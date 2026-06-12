---
title: "instalar gnome basico en ubuntu 8.04"
date: 2008-09-30
forum: Software
---

### Post by bhm160583 on 2008-09-30
hola gente tengo un problema al intentar instalar gnome básico en ubuntu Server 8.04, en realidad como soy novato no tengo en claro muchas cosas como por ejemplo: 
* el paquete que contiene gnome en esta distribución ¿como se llama?
*si es que se encuentra en el cd, como lo leí de otros foros, tengo que montar la unidad de cd o bien la reconoce por defecto cuando le ejecuto sudo install
*en caso de de tenga que bajar los paquetes de que pagina lo hago
*que conviene usar apt-get ó aptitude
 Una vez que sean tan amables de aclararme estar cosas por favor indíquenme como lo han instalado en sus maquinas, si es la versión 8.04 server mucho mejor

---

### Post by ramiro_md on 2008-09-30
Lindo user name te elegiste flaco xD. Ahora si, bienvenido.
Con respecto a instalar gnome leete esta guía [http://www.guia-ubuntu.org/index.php?title=GNOME](http://www.guia-ubuntu.org/index.php?title=GNOME). Por otro lado qué entorno de escritorio estás usando (xfce,kde) ?.
Con el tema del cd, vos metelo en la lectora que te lo monta solo el sistema. Lo mismo con un dvd.
Con lo de aptitude o apt-get, a mi me l oenseñaron con aptitude y me dijeron que es mejor. En fin, podés usar los dos si querés.
Y paera terminar, si vas a usar tu computadora como servidor está bien que le hayas puesto server, pero si la usas para navegar por internet, escuchar música, chatear, ver pelis y demás cosas de usuario común...deberías haber instalado la desktop. 
Un saludo y espero que te haya ayudado en algo.

---

### Post by faktorqm on 2008-10-01
Hola, lindo username, si, jajaj

Yo lo que te recomiendo son varias cosas, la primera, si estas instalando ubuntu server en un servidor, en un servidor posta, sólo vale la pena instalarlo por el tema del reconocimiento de hardware, sino es lo mismo instalarte Debian (no hago flame con esto, yo en mi laburo instale debian y va como piña). Segundo, por lo general, esta muy mal visto instalar entornos de escritorio en servidores, por que estas levantando mil cosas que "alentan" el servidor, cuando bien podrias hacerlo por consola. Aclaro algo, yo entiendo que sos nuevo en esto, pero si sos nuevo no te conviene tirarte a instalar un servidor por que te vas a volver loco, primero te convendria instalartelo en tu casa la version "home" y estudiarlo un poquito antes de saltar a un server.
Tercero, no es un paquete, es un metapaquete, y si no me falla la memoria se llama ubuntu-desktop. 
Cuarto, sudo install no existe, o es sudo apt-get install <paquete>, o sudo aptitude install <paquete>, pero esta ese paquete en el cd (creo, nunca instale ubuntu server, pero en la instalacion no te pregunto si le querias agregar interfaz grafica???)
Quinto, apt-get y aptitude son lo mismo. apt-get "solo" tiene un aptitude configurado, por ejemplo si pones aptitude install paquete te instala paquete con todas sus dependencias mas los paquetes recomendados, apt-get instala igual sin los paquetes recomendados.
En mi pc tengo ubuntu 8.04, y lo instale con el alternate cd, tambien lo podes hacer con el desktop cd. En el laburo para servidores instale Debian Etch net-install, pero me comentaron que ubuntu server es muy bueno con el tema del reconocimiento del hardware, asi que ... vos elegis. Salu2!

---

