---
title: "Problemas configurando la red"
date: 2010-10-01
forum: Software
---

### Post by Sukoa on 2010-10-01
Buenas, soy nuevo en esto del ubuntu, y realmente no entiendo nada. XD
Lo instale, anda todo muy lindo, pero tengo el problema de que no logro configurar la red de wifi de mi casa.
Tengo internet, pero no puedo ver o acceder a la otra computadora de la res.
Si alguien me puede explicar de cero como hacer, seria de mucha ayuda.
ya probe con varios post, y no consegui que nada me funcione,
antes al menos podia ver la pc de abajo, ahora no, y nunca logre ver los archivos de la otra pc (tiene windows 7), me daba error en la lista de compartición. De la otra pc si se podian ver los archivos compartidos que yo tenia.
Desde ya muchas gracias. =D

---

### Post by juancarlospaco on 2010-10-01
**Lugares--->Conectar con el Servidor...**

en la ventanita elejir arriba de todo "**Compartido de Windows**"

donde dice "**Server:** " pone **la IP de la otra PC**

todo lo otro, que dice "Informacion Opcional", no pongas nada.

dale click en el boton "**Conectar**"

---

### Post by Sukoa on 2010-10-05
Lo hice, pero me aparece el cartel que dice:

 
"No se pudo montar el lugar
Falló al obtener la lista de compartición del servidor"


Asi que no se que hacer :S

---

### Post by guillermolisi on 2010-10-05
De que version de Ubuntu estamos hablando ?
Que version de Windows usan las otras PCs ?
Entre ellas (las que usan Windows) se ven ?
Y desde la que usan Windows podes ver la que corre Ubuntu ?
Usas IP estaticas o dinamicas en esa red ?

---

### Post by sys.adm.og on 2010-10-05
Prueba si las windows se ven entre si!
en ejecutar pon lo siguiente: **\\192.168.1.2** (en este caso la ip de la otra pc con windows)
si usas ip estaticas te va ser facil sino en ejecutar escribe cmd (en la otra pc)y en la ventana dos: **ipconfig** y traera la ip que esta utilizando.
Si llega a aparecerte las carpetas compartidas trata de acceder.

Luego imagino que a internet la pc que tiene ubuntu accede? si es asi abre una terminal:
Alt+F2, y en la ventana emergente escribe:**gnome-terminal** luego alli ingresa: **ifconfig** y donde diga wlan0 esa alli aparecera la ip que tiene.

Luego comparte una carpeta y trata de acceder desde una windows a la ubuntu, ejecutar: \\192.168.1.3 ip de tu ubuntu. Si ve las carpeta y accede vamos por buen camino.

Luego y por ultimo prueba desde el ubuntu acceder a tus carpetas compartidas de las maquinas con windows de esta forma:
Da un clic en el escritorio y presiona luego: **Ctrl+L** y te aparecera una ventanita donde pondras **smb://192.168.1.2** la ip de algun windows, y si te aparece las carpetas compartidas y te accede al menos ya sabremos que el problema es otro.

Si te parece complicado solo pregunta!

---

