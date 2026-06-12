---
title: "¿Como apagar la PC desde consola sin ser root ni sudo?"
date: 2008-05-06
forum: Software
---

### Post by anarko on 2008-05-06
Hola, formulo esta pregunta porque todabia no encontre una forma de hacerlo ( vi un par en las que cambian permisos y grupo a /sbin/halt pero no me kabe ni un poquitito ) 

Buscando y leyendo un poco en google, a lo mas cerca que llegue es a usar gnome-session-save --kill --silent pero eso reinicia la PC, no la apaga. y no me sirve, si no le pongo el --silent aparece como si hubiera apretado el boton de power( terminar session, reiniciar y todas esas cosas ).

EL porque de todo esto es para usar irexec para lanzar un comando para apagar la PC despues del zapping nocturno antes de ir a dormir y no tener que levantarme. Creo que me lo merezco despues de haber buscado, patcheado ( a mano porque el patch que encontre no concordaba ) y recompilado el modulo bttv para que ande el bendito control remoto. La placa es una Leadtek TV2000FM/XP si alguien la tiene y quiere el modulo bttv precompilado para el kernel default de Hardy, pidamelo, tambien tengo el source del .c patcheado.

Tambien acepto sugerencias sobre como asignarle teclas a los botones del control remoto con el manejador de control remoto de gnome ( con la forma nueva el control remoto es un input tipo teclado ). Sin ejecutar irexec alguno botones del control remoto responden como por ej. volumen +/- del control remoto hace lo mismo que volumen +/- del teclado multimedia que tengo, tambien responden los numeros como si los apretara del teclado, como asi la tecla power del control remoto hace lo mismo que la tecla power de la pc.

Espero no haber sido muy extenso, Saludos.

---

### Post by croto on 2008-05-06
Amigazo, con todo respeto, no, pero no entiendo por que no quiere darle SUID permissions a /sbin/shutdown. Veo que es un hack medio feito, quizas introduzca alguna vulnerabilidad pero el peligro parece casi nulo.  Otra cosa, el irexec, habla con un deamon, no es cierto? Con que usuario corren esos programas? Si corren bajo el usuario root, entonces no habria mas que llamar a shutdown (o halt, por supuesto). Pero si corren bajo un usuario regular, se podria agregar ese usuario a la lista de sudoers y hacer que no necesite password para correr solo el programa "shutdown" (estoy casi seguro que eso es posible). Mas que eso no lo puedo ayudar, pero si se me ocurre algo, le aviso.

---

### Post by faktorqm on 2008-05-06
Bueno, he aqui la solución luego de una hora y media de busqueda y pruebas. A todo esto me parece que rompi algo en mi sistema jajajaj ahora no puedo hacer mas sudo con ningun comando y encima me agregue en el grupo gdm y no me puedo sacar. y peor aun, cada vez que apreto "desbloquear" en algun lugar me dice que hubo un error inesperado. todo mal. ajajajaj

Abri una consola y escribi:

```
sudo visudo
```

El editor es horrible, lo sé. Busca la linea que dice root blabla y abajo pone (tenes que apretar insert para escribir):

```
<nombre de usuario> boulder = (root) /sbin/shutdown
```

en mi caso fue:

```
faktorqm boulder = (root) /sbin/shutdown
```

luego, apretas ESC y despues ":wq" y te lo guarda.

entonces escribis feliz "sudo shutdown -h now" y listo! no te pide contraseña. (ojo! es solo para ese comando)

Espero que te haya servido. Salu2!!

---

### Post by anarko on 2008-05-06
Gracias por el intento, pero no, eso del visudo ya lo habia probado y no funciona pide el password.

---

### Post by niko_3100 on 2008-05-06
Es que esta bien que sea el root quien apague la pc. Si no fuera el root y cualquiera pudiera apagarla cualquier gil puede venir y apagar tu computadora sin tener ninguna restriccion.

---

### Post by faktorqm on 2008-05-06
a mi no me pidio, proba eso. Salu2!

---

### Post by anarko on 2008-05-06
> **niko_3100 said:**
> Es que esta bien que sea el root quien apague la pc. Si no fuera el root y cualquiera pudiera apagarla cualquier gil puede venir y apagar tu computadora sin tener ninguna restriccion.

Estas equivocado, te cuento porque, porque si viene un "cualquiera" y aprieta en el boton de cerrar session y despues aprieta en "apagar la PC" la maquina se apaga y jamas pregunto la contraseña. SI un cualquera llega tan cerca de mi pc como para apretar el boton de apagar, no me importaria si lo hace desde el control remoto de la plaka de tele ( que tiene un alcanze de 5/6 mts ) en una abitacion de 4x3 tendria que verlo venir :p

---

### Post by Mister X on 2008-05-06
> **anarko said:**
> Estas equivocado, te cuento porque, porque si viene un "cualquiera" y aprieta en el boton de cerrar session y despues aprieta en "apagar la PC" la maquina se apaga y jamas pregunto la contraseña. SI un cualquera llega tan cerca de mi pc como para apretar el boton de apagar, no me importaria si lo hace desde el control remoto de la plaka de tele ( que tiene un alcanze de 5/6 mts ) en una abitacion de 4x3 tendria que verlo venir :p

prefiero que el "cualquiera" tenga la gentileza de apagarla con un comando y no desenchufando el cable de alimentacion;)

---

### Post by anarko on 2008-05-06
ufa nadie sabe?

---

### Post by leo_rockway on 2008-05-06
Edita los sudoers. Eso tiene que funcionar, tal como dijo factorqm

---

### Post by LordKafi on 2012-02-20
Hola, hace algún tiempo yo buscaba lo mismo, escribe me a mi correo davisport_eros@hot... pero se trata de un comando, pero yo me hice un script donde copias el comando de apagar de root y lo reemplazas por el usuario de tu computador linux, lo he probado con 9.10-11.04 y todas las versiones que estan incluidas donde te indico funcionan imaginate trabajo en un aula virtual donde hay mas de 200 computadoras en diferentes laboratorios y tengo q ir apagando de una en una, pero eso ya no es problema lo hago con 1 clic jeje miralo si gustas a partir del minuto para que no te aburras, eso lo ejecuto sin ser usuario root y mira cuantas computadoras apago con 1 clic:
[https://www.youtube.com/watch?v=QDmtFtlZKLg](https://www.youtube.com/watch?v=QDmtFtlZKLg)

---

