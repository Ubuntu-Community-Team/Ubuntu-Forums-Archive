---
title: "Autentificacion en una red Windows"
date: 2007-06-18
forum: Software
---

### Post by inakios on 2007-06-18
Buenas a todos, mi consulta es si alguien pudo autentificarse en una red Windows. Ingreso la IP asignada. DNS, GW, mascara y no puedo acceder a internet.
Puedo ver otras PC con win entrar, hacer ping a otra IP (las veo a todas) pero no puedo acceder a Internet, me pide ID/PASS, el cual lo tengo, pero aun no me deja salir a Internet. Que estare haciendo mal.
Tengo una pc al lado que esta en red, funcionando perfectamente y copie absolutamente todos los parametros que tiene (salvo la ip) y no hay forma. Me da la sensacion que no puede autentificarse(en NT tengo que poder el nombre del dominio para poder loguearme) en Ubunt 6.01 no me dice.
Es como que la red la ve bien, pero no me permite ver mas nada.
Si alguien entiende mi problema y puede darme una mano, se lo voy a agradecer mucho. 
Saludos!!!

---

### Post by guillermolisi on 2007-06-19
Inakios

Me resulta un poco confuso el contexto en el cual tenes el inconveniente.

Entiendo que tenes una red Windows con un controlador de dominio con WinNT y al que todas las PCs, tambien con Win, acceden para iniciar sesion en el dominio.
Tambien tenes una PC con Ubuntu 6.01 (o 6.10 ?) y que queres que tenga salida a Internet.

Luego, no hace falta que Ubuntu se autentique en el dominio para acceder a Internet (si esto es lo uico que necesitas hacer). Con que tenga "vista" del Firewall/Proxy (si es que hay alguno) y que no exista en Windows (la que oficie de salida a Internet) algun impedimento y tanto el bloque de IP, mascara, gateway y port de salida (si el firewall/proxy exige uno en particular) de Ubuntu sean los correctos, deberia funcionar.

Si contas con algo mas de detalle creo que podriamos dar con una solucion mas concreta.

Saludos

---

### Post by ariel on 2007-06-20
por lo que entiendo (es un poco confuso) hay dos posibilidades:

  - Hay un proxy en tu red. Facil de chequear, en alguna de las maquinas windows, abri el explorer y fijate en el setup si hay un proxy configurado. Si lo hay, copia la data en la configuracion de proxy de firefox en linux, y listo. 

  - Hay un windows NT domain controller y un FW que deja salir solo a las maquinas autenticadas contra el dominio. Aca ya no se. Nunca supe como hacer que un linux sea parte de un dominio nt. En una de esas se puede. Igual, que esten filtrando la salida a inet asi seria muy raro. 



> **inakios said:**
> Buenas a todos, mi consulta es si alguien pudo autentificarse en una red Windows. Ingreso la IP asignada. DNS, GW, mascara y no puedo acceder a internet.
Puedo ver otras PC con win entrar, hacer ping a otra IP (las veo a todas) pero no puedo acceder a Internet, me pide ID/PASS, el cual lo tengo, pero aun no me deja salir a Internet. Que estare haciendo mal.
Tengo una pc al lado que esta en red, funcionando perfectamente y copie absolutamente todos los parametros que tiene (salvo la ip) y no hay forma. Me da la sensacion que no puede autentificarse(en NT tengo que poder el nombre del dominio para poder loguearme) en Ubunt 6.01 no me dice.
Es como que la red la ve bien, pero no me permite ver mas nada.
Si alguien entiende mi problema y puede darme una mano, se lo voy a agradecer mucho. 
Saludos!!!

---

### Post by jpmorelli on 2007-06-23
Si yo no me acuerdo mal, una vez hicimos para un laburo una red con un controlador de dominio Windows NT que a la vez era la puerta de entrada de internet, o sea, el cable se conectaba a ese "server" y desde ahí daba el servicio a las otras máquinas ( odavía los routers no eran muy baratos en ese momento ). Si no me equivoco lo único que hacíamos en los clientes era ponerle como dirección proxy la IP del controlador de dominio ( la máquina que valida los usuarios ).
Suerte !

---

### Post by inakios on 2008-11-03
Estimados, el inconveniente era que el dominio se tiene que ingresar antes del nombre de usuario o ID, ej.: DOMINIOC\usuario.

Lamento responder tan tarde, pero no me olvide.

Saludos y muchisimas gracias por su ayuda.

---

