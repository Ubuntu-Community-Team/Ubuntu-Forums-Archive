---
title: "problema por modificar la seguridad en mi ubuntu"
date: 2009-09-21
forum: Software
---

### Post by descargado on 2009-09-21
hola a todos.
tengo un problema que no puedo solucionar y no he tenido quien me ayude.
El mes pasado decidi seguir las recomendaciones del IT-security (file:///home/jacome/Escritorio/The%20Big%20Ol%27%20Ubuntu%20Security%20Resource%20-%20IT%20Security.html). solo segui las tres primeras instrucciones y desde ese momento no he podido conectar con mi huawei gsm de telefonica chile. cuando conecta el modem 3g automaticamente se detecta pero antes de conectar me sale el siguiente mensaje: {la aplicacion "miniaplicacion gestor de red" (/usr/bin/nm-applet) quiere acceder al anillo de claves predetrminado pero esta bloqueado}. lo he intentado todo pero no logro cambiar la configuracion para que me reconozca automaticamente el huawei y que puedo  decir... ahora no puedo navegar. incluso he pensado que tengo que cambiar de distro o reinstalar ubuntu.
Les agradezco la ayuda que me puedan aportar 
[email]descargado2005@yahoo.com[/email]
saludos.

---

### Post by Carlos C on 2009-09-21
Hola. He movido tu pregunta al subforo "Software". Por favor recuerdoa publicar en el subforo adecuado. En cada uno de ellos hay un [sticky]("http://ubuntuforums.org/showthread.php?t=1162708") que te dice lo que puedes publicar.

Pedir ayuda mediante mensajes personales o a tu correo va contra las normas de Ubuntuforums. En caso de dudas te recomiendo mirar [aquí]("http://ubuntuforums.org/showthread.php?t=1162750").

El enlace que pusiste no sirve, es la dirección de un archivo en tu equipo y no es posible saber qué fue lo que hiciste.

Saludos.

---

### Post by moreback on 2009-09-21
> **descargado said:**
> pero antes de conectar me sale el siguiente mensaje: {la aplicacion "miniaplicacion gestor de red" (/usr/bin/nm-applet) quiere acceder al anillo de claves predetrminado pero esta bloqueado}. 

Que te aparezca ese mensaje significa que el NM está intentando acceder a tu depósito de claves para obtener la clave de tu conexión 3G. Tienes que autorizar la aplicación** ingresando la contraseña del usuario con que estás trabajando** (la misma que usas para instalar software o hacer labores administrativas) y activar la casilla que te permite recordar la autorización.

Saludos.

---

