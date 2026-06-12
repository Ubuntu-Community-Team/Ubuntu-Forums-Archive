---
title: "Configurar Escritorio Remoto desde consola"
date: 2012-05-08
forum: Software
---

### Post by javierlinux1 on 2012-05-08
Buenas noches, escribo porque stoy tratando de instalar el escritorio remoto en un server casero que tengo para pruebas.

El equipo está ya funcionando con ubuntu server 10.04.4 LTS y le quiero agregar la posibilidad de acceder a el con escritorio remoto, para algunas que quiero probar. Tengo instalado Fluxbox, pero como la maquina no tiene monitor ni teclado no puedo entrar directamente y lo quiero hacer desde mi equipo principal. 

Busque bastante y no encuendtro nada que me indique como hacer esto por consola, en todos lados esta explicado para hacerlo desde el entorno grafico, pero yo quiero hacerlo por consola, ¿se puede? alguien tiene alguna pagina donde se pueda leer como ahcerlo?
Gracis de antemano

Javier

---

### Post by papibe on 2012-05-08
Hola javierlinux1.

¿Te refieres a acceso remoto usando el terminal? o sea, ¿a una connexión ssh?

Saludos.

---

### Post by marohds on 2012-05-10
Hola,
 
Si lo que necesitás es acceder cada tanto al servidor en forma remota, deberías configurarlo para que se inicie automáticamente cada vez que lo reiniciás.
Sin embargo, creo que sólo es posible acceder al VNC de una si el usuario que inicia sesión automática no tiene contraseña, ya que, si el usuario tiene contraseña, el gnome-keyring te pide la pide cuando se carga el servicio VNC (o sea que tenés que caminar hasta el server, enchufar monitor, escribir la contraseña y ahi recién conectar vía VNC).
 
Otra opción es utilizar [XDMCP]("http://tldp.org/HOWTO/Remote-X-Apps.html")
 
Una que prefiero yo es utilizar usar redireccionamiento del servidor X para cargar el programa que quieras (siempre corriendo en el servidor) en la pc remota. La forma más sencilla es iniciar sesión SSH con el parámetro -X, y luego ejecutar cualquier programa con un & al final para que se ejecute en segundo plano.
Si querés probarlo, te dejo un ejemplo:
 
1 -  Iniciás sesión con #ssh -X <ip-server> 
2 - ejecutás cualquier programa, ejemplo: #gedit &
 
 Y otra opción más completa es "redireccionar" la salida completa del servidor X. De esta manera estarías reemplazando el servicio VNC. Te recomiendo buscar el término "X11 forwarding". ([te dejo una referencia]("http://cosi.clarkson.edu/knowledge/faq/xforwarding.html"))
 
 
Espero te sirva, saludos!

---

