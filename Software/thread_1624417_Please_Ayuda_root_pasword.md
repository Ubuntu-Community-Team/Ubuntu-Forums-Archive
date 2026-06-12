---
title: "Please Ayuda root pasword"
date: 2010-11-17
forum: Software
---

### Post by Mashara on 2010-11-17
Hola: 
1ra vez en el foro, tenia instalado Ubuntu  9.04 desde marzo pasado, nos fuimos adaptando mutuamente, iba bastante bien, a veces no tanto.
Hace 15 días decidí aceptar las actualizaciones propuestas por el gestor de actualizaciones, ahora tengo Ubuntu 9.10.
Todo bien excepto que no me reconoce como administrador, no me permite hacer casi nada, **no tengo la contraseña de root ** ni ninguna otra, puedo entrar con limitaciones al escritorio y mis carpetas personales, no logro acceder a los archivos de Windows.
Espero puedan ayudarme por favor en español.
Gracias

---

### Post by marcelo_bur on 2010-11-17
Hola, ¿no tenés ninguna contraseña??? ¿como entras a tu escritorio, no te la pide para iniciar sesión?

---

### Post by Mashara on 2010-11-18
Hola Marcelo
Si tengo mi contraseña personal, me permita acceder y modificar mi contraseña y trabajar con mis carpetas.
No me reconoce como administrador, no me deja modificar nada del sistema, ni actualizar o eliminar actualizaciones, algo que si podía hacer antes de la ultima actualización.
Aclaro que con anterioridad hice 2 actualizaciones  de la version 9.04 y si bien me trajo algunos inconvenientes seguí trabajando sin graves consecuencias.
Ahora solo puedo trabajar yo, mi hija tiene otra cuenta de usuario, abre con contraseña y se bloquea, ella no puede entrar.
Si puede ver sus carpetas y documentos desde mi cuenta pero le abre solo para lectura no puede modificar nada.

---

### Post by marcelo_bur on 2010-11-18
Hola. Fijate si podes hacer algo usando esto:

Abris una terminal, escribis "sudo -i", sin comillas por supuesto. Te va a pedir tu contraseña personal y luego das enter y tendrías que estar accesando al sistema como root, luego podrías, desde la terminal, intentar arreglar el tema de las demas contraseñas y otras cosas que estes necesitando.
Espero que esto te sirva, de lo contrario vas a tener que esperar que miembros del foro que saben mucho más que yo te den otras soluciones.
Te dejo una captura de pantalla de la terminal.
Saludos

---

### Post by Wiredfixer on 2010-11-18
Me gusta tu terminal marcelo :3

Mashara, dices que despues de las actualizaciones te empezo a dar problemas?

Si no te funciona entrar como root en terminal, vas a tener que hacer un pequeño truco con un LiveCD, consiste en editar /etc/shadow en donde esta el password de root y el de tu usuario, la idea es limpiarlos y volverlos a asignar...

[http://bootlog.org/blog/linux/como-cambiar-la-clave-de-root-en-linux](http://bootlog.org/blog/linux/como-cambiar-la-clave-de-root-en-linux)

Aqui puedes hayar algo de luz.. :D

---

