<!-- El primer caracter determina si el archivo es:
• - archivo
• d directorio
• l enlace
• c dispositivo de caracteres (como un puerto serial)
• b dispositivo de bloques (como un disco duro)
• s socket (conexión a red)


Los caracteres 2,3,4 determinan los permisos de usuario
para lectura +r, escritura +w y ejecución +x
Los caracteres 5,6,7 determinan los permisos del grupo
para lectura +r, escritura +w y ejecución +x
Los caracteres 8,9,10 determinan los permisos del resto
para lectura +r, escritura +w y ejecución +x
Si en la lista aparece - entonces no tiene el permiso


-->

1) Identifica los siguientes permisos

	d = directory; r = read; w = write; x = eXecute;
	1) drwxr-xr-x
		d = directory, es un directorio.
		rwx = permisos de usuario, puede leer, ejecutar, y escribir;
		r-x = permisos de grupo, puede leer y ejecutar pero no escribir;
		r-x = permisos de otros, osea cualqier persona que tenga accesso. Puede leer y ejecutar pero no escribir;
	2) -rwxr-xr-x
		- = file, es un archivo de tipo file.
		rwx = Permisos de usuario, tiene acceso a todas las acciones.
		r-x = Permisos de grupo, solo lectura y ejecucion.
		r-x = Permisos de otros, solo lectura y ejecucion.
	3) dr-xrwx-wx
		d = directory, es un directorio.
		r-w = permisos de usuario, solo lectura y ejecucion;
		rwx = permisos de grupo, tiene todos los permisos;
		-wx = permisos de otros, solo escritura y ejecucion;
	4) -rw-rw-rw-
		- = file, es un archivo de tipo file.
		rw- = permisos de usuario, solo lectura y escritura.
		rw- = permisos de grupo, solo lectura y escritura.
		rw- =permisos de otros, solo lectura y escritura.
	5) -rw-r--r--
		- = file, es un archivo de tipo file.
		rw- = permisos de usuario, solo lectura y escritura.
		r-- = permisos de grupo, solo lectura.
		r-- = permisos de otros, solo lectura.
	6) d-w-rwx-w-
		d = directory, es un directorio.
		-w- = permisos de usuario, solo escritura
		rwx = permisos de grupo, tiene todos los permisos
		-w- = permisos de otros, solo escritura.

		// Los voy a probar en el terminal
	7) 414
		4 = r va primero, por lo que como r vale 4, el usuario solo puede leer.
		1 = r vale 4, 4 no cabe en 1, por lo que pruebo el siguiente. w vale 2, 2 no cabe en 4, por lo que paso al siguiente. x vale uno asi que EL GRUPO SOLO PUEDE EJECUTAR.
		4 = r va primero, por lo que como r vale 4, otros usuarios solo pueden leer.
		Traducido en Terminal: -r----xr--
		Respuesta completa: Usuario: Solo lectura; Grupo: Solo ejecucion; Otros: Solo lectura;
	8) 422
		4 = r va primero, por lo que como r vale 4, el usuario solo puede leer.
		2 = r vale 4, y 4 no cabe en 2, w vale 2, 2 + 0 = 2, el grupo solo puede escribir.
		2 = r vale 4, y 4 no cabe en 2, w vale 2, 2 + 0 = 2, otros usuarios solo pueden escribir.
		Traducido en Terminal: -r---w--w-
	9) 303
		3 = r vale 4, 4 no cabe en 3, continuo el proceso. w = vale 2, 2 si cabe en 3, ahora es un 1. x vale 1,  solo nos queda 1, por lo que si puede ejecutar. El usuario solo puede leer y escribir.
		0 = El grupo no tiene ningun permiso-0 no es mayor a ningun valor.
		3 = r vale 4, 4 no cabe en 3, continuo el proceso. w = vale 2, 2 si cabe en 3, ahora es un 1. x vale 1,  solo nos queda 1, por lo que si puede ejecutar. Otros solo pueden leer y escribir.
		Traducido en Terminal: --wx----wx
		Respuesta completa: El usuario puede escribir y ejecutar; El grupo no tiene permisos sobre el archivo; Otros pueden escribir y ejecutar;
	10) 404
		4 = r va primero, por lo que como r vale 4, el usuario solo puede leer.
		0 = El grupo no tiene ningun permiso-0 no es mayor a ningun valor.
		4 = r va primero, por lo que como r vale 4, el usuario solo puede leer.
		Traducido en Terminal: -r-----r--
		Respuesta completa: El usuario solo puede leer; El grupo no tiene permisos sobre el archivo; Otras personas solo pueden leer;
	11) 755
		7 = El usuario tiene acceso a todos los permisos
		5 = r = 4, cuatro si cabe en 5 por lo que se transforma en un 1(se resta). w vale 2 y no cabe en el 1. x vale 1. Así que el grupo solo puede leer y ejecutar.
		5 = r = 4, cuatro si cabe en 5 por lo que se transforma en un 1(se resta). w vale dos y no cabe en el 1. x vale 1. Así que otras personas solo pueden leer y ejecutar.
		Traducido en Terminal: -rwxr-xr-x
		Respuesta completa: El usuario tiene acceso completo a todos los permisos; El grupo solo a leer y ejecutar, y otras personas tambien pueden leer y ejecutar.
	12) 766
		7 = El usuario tiene todos los permisos.
		6 = r = 4, 4 cabe en 6, 6 se convierte a 2. w = 2, quedan 2, por lo que el grupo puede leer y escribir.
		6 = r = 4, 4 cabe en 6, 6 se convierte a 2. w = 2, quedan 2, por lo que otras personas pueden leer y escribir.
		Traducido en Terminal: -rwxrw-rw-
		Respuesta completa: El usuario tiene todos los permisos, el grupo solo puede leer y escribir y otros solo pueden leer y escribir.
	13) 711
		7 = El usuario tiene todos los permisos.
		1 = x es el valor menor(x = 1), asi que el grupo solo puede ejecutar.
		1 = x es el valor menor(x = 1), asi que otros solo pueden ejecutar.
	14) 070
		0 = El usuario no tiene nigun permiso.
		7 = El grupo tienetodos los permisos.
		0 = Otras personas no tienen ningun permiso.
		Traducido en Terminal: ----rwx---
	//fin ejercicio 1)



15. Crear un archivo

touch file.txt
ls -la | grep 'file.txt'

Respuesta:

-rw-rw-r--  1 sofia sofia       0 ago 18 15:43 file.txt

16. Asignar los permisos a usuario tal que éste pueda leer y escribir y que no tengan privilegios ni grupo ni otros

chmod 600 file.txt
ls -la | grep 'file.txt'

Respuesta:

-rw-------  1 sofia sofia       0 ago 18 15:43 file.txt

17. Al mismo archivo asignarle permisos de lectura y escritura a grupo

chmod 660 file.txt
ls -la | grep 'file.txt'

Respuesta:

-rw-rw----  1 sofia sofia       0 ago 18 15:43 file.txt

18. Al archivo, cambiar el permiso del usuario para que se pueda ejecutar

chmod 760 file.txt
ls -la | grep 'file.txt'

Respuesta:

-rwxrw----  1 sofia sofia       0 ago 18 15:43 file.txt

19. A ese mismo archivo asignarle permiso de lectura a otros

chmod 764 file.txt
ls -la | grep 'file.txt'

Respuesta:

-rwxrw-r--  1 sofia sofia       0 ago 18 15:43 file.txt

20. Crear un archivo

touch filenew.txtxt
ls -la | grep 'filenew.txtxt'

Respuesta:

-rw-rw-r--  1 sofia sofia       0 oct 28 13:47 filenew.txtxt

21. Quitarle todos los permisos

chmod 000 filenew.txtxt
ls -la | grep 'filenew.txtxt'

Respuesta:

----------  1 sofia sofia       0 oct 28 13:47 filenew.txtxt

22. Abrirlo con sublime

subl filenew.txtxt

23. ¿Qué error aparece?

Respuesta:

Unable to save ~/Escritorio/Escritorio/Escritorio/Desafios/filenew.txtxt
Error: /home/sofia/Escritorio/Escritorio/Escritorio/Desafios/filenew.txtxt is readonly

24. Dar permisos de lectura al dueño

chmod 400 filenew.txtxt
ls -la | grep 'filenew.txtxt'

Respuesta:

-r--------  1 sofia sofia       0 oct 28 13:47 filenew.txtxt

25. Abrirlo con sublime, modificarlo y guardarlo.

subl filenew.txtxt

Respuesta:

Unable to save ~/Escritorio/Escritorio/Escritorio/Desafios/filenew.txtxt
Error: /home/sofia/Escritorio/Escritorio/Escritorio/Desafios/filenew.txtxt is readonly

26. Dar permisos de escritura

chmod 500 filenew.txtxt
ls -la | grep 'filenew.txtxt'

Respuesta:

-r-x------  1 sofia sofia       0 oct 28 13:47 filenew.txtxt

27. Crea un archivo .txt utilizando sudo

sudo touch txt.txt

28. ¿Qué usuario queda al hacer ls -la ?

ls -la | grep 'txt.txt'

Respuesta:

-rw-r--r--  1 root  root        0 oct 28 14:18 txt.txt

29. Cambia los permisos para que todos puedan escribir en él sin sudo

chmod 333 txt.txt

30. ¿Permitido?

No

Respuesta:

chmod: changing permissions of 'txt.txt': Operation not permitted

31. Cambia el owner a tu usuario (chown)

sudo chown sofia txt.txt

Respuesta:

sudo: unable to resolve host sofia-castillo: Connection timed out

32. Confirma el cambio con ls -la

ls -la txt.txt

Respuesta:

-rw-r--r-- 1 sofia root 0 oct 28 14:18 txt.txt

33. Cambia los permisos para que sólo el usuario pueda leer y escribir

chmod 600 txt.txt

34. ¿Permitido?

Si

Respuesta:

-rw------- 1 sofia root 0 oct 28 14:18 txt.txt
