---
title: "Internet - Resolucion de pantalla y demas"
date: 2009-05-27
forum: Software
---

### Post by Ciudadela on 2009-05-27
Me instale el 9.04 ya hace unos dias, estuve releyendo los post y siguiendo los links pero yo solo no pude resolver las siguientes cosas
 
_Conexion de internet:_
Los controladores del modem (Zykel 600 proporcionado x Telefonica) quiero saber si funcionan los del CD de Zykel, y tambien estuve leyendo que ingresan comandos x teclado (menciona SUDO),es una aplicacion o una ventana??, revise en sistema y no lo encontre, si me lo xplican podre resolver los problemas que siguen
 
_resolucion de patalla max 800 x 600:_
Se que debo instalar controladores de video tengo una Asus con video onboard y en la paginas de Nvidia solo ofrece soporte para funcionar en linux para las tarjetas GeForce, descargue unos paquetes de esa pagina pero mi instalacion no responden para abrirse con ninguna de las aplicaciones instaladas.
 
_Inicio:_
Instale Ubuntu en una unidad fisica distinta donde teni mi sist. WXP.
Al iniciar me da la alternativa de elegir Windows Xp, pero no sucede nada, si lo dejo solito el equipo se inicia en ubuntu, pero como no puedo resolver los problemas anteriores, para volver a la criatura de Bill G. tengo que reiniciar y en el setup cambiar de HD de inicio.
 
Gracias a todos los que puedan responderme y sean compasivos conmigo!!!!

---

### Post by luks911 on 2009-05-27
> **Ciudadela said:**
> _Conexion de internet:_
Los controladores del modem (Zykel 600 proporcionado x Telefonica) quiero saber si funcionan los del CD de Zykel, y tambien estuve leyendo que ingresan comandos x teclado (menciona SUDO),es una aplicacion o una ventana??, revise en sistema y no lo encontre, si me lo xplican podre resolver los problemas que siguen

Lo que te recomiendo para ese modem es que lo configures como router. De ese modo, es el modem el que marca la conexión y te olvidás. Así va a funcionar con sólo conectarlo a una máquina mediante el cable de red sin importar el sistema operativo que use. 
Para hacerlo, acá[0] hay un pdf que explica cómo mediante telnet, seguilo paso a paso que funciona. En lugar de usar el cmd de Windows lo hacés en una Terminal (Aplicaciones > Accesorios > Terminal) El mismo tuto debería estar acá[1] pero la página no carga lo que debería, por eso el pdf.

sudo es lo que se usa en Ubuntu antes de un comando para ejecutarlo como root o super usuario. Por ejemplo, para instalar o desinstalar un aplicación. En concreto podrías ser:

```
sudo aptitude install amule
```

para instalar aMule

> **Ciudadela said:**
>  
_resolucion de patalla max 800 x 600:_
Se que debo instalar controladores de video tengo una Asus con video onboard y en la paginas de Nvidia solo ofrece soporte para funcionar en linux para las tarjetas GeForce, descargue unos paquetes de esa pagina pero mi instalacion no responden para abrirse con ninguna de las aplicaciones instaladas.

¿El vieo on-board es Nvidia? En una terminal ejecutá 
```
lspci
``` y pegá el resultado acá así vemos que placa de video tenés. Si es Nvidia, en Sistema > Aministración > Controladores de Hardware, debería darte la opción de instalar los drivers. No es necesario que bajes nada de la página de Nvidia. 

> **Ciudadela said:**
> _Inicio:_
Instale Ubuntu en una unidad fisica distinta donde teni mi sist. WXP.
Al iniciar me da la alternativa de elegir Windows Xp, pero no sucede nada, si lo dejo solito el equipo se inicia en ubuntu, pero como no puedo resolver los problemas anteriores, para volver a la criatura de Bill G. tengo que reiniciar y en el setup cambiar de HD de inicio.
 
Gracias a todos los que puedan responderme y sean compasivos conmigo!!!!

De esto, ni idea.

[0] [http://rapidshare.com/files/129251750/INSTRUCTIVO_ZYXEL660.pdf.html](http://rapidshare.com/files/129251750/INSTRUCTIVO_ZYXEL660.pdf.html)
[1] [http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=197&root=132](http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=197&root=132)

---

### Post by staar on 2009-05-27
los comandos se ingresan en la terminal (Aplicaciones > Accesorios > Terminal), sudo es un comando que se usa para obtener permisos de root, con los que es posible realizar tareas de administración del sistema...

respecto al tema de los drivers de video, necesitaríamos saber el modelo exacto de tu mother Asus, para poder saber la marca del chip de video que integra, si sabés que dicho chip es Nvidia, instalá los controladores desde Sistema > Administración > Controladores de Hardware, que el sistema va a detectar los correctos (OJO, antes tenés que tener disponible internet, resolvé eso primero)...

para el problema de acceder al windos, necesitaríamos que nos muestres el contenido del archivo /boot/grub/menu.lst así también como la salida de poner ```
sudo fdisk -l
``` en una terminal...

AVISO: cuando en la Terminal ponés un comando que comienze con sudo, al apretar enter, te va a solicitar tu contraseña, al escribirla, no van a a aparecer caracteres, no te asustes, es el comportamiento normal, se oculta lo que escribís por seguridad...

saludos

---

### Post by Ciudadela on 2009-05-28
> **luks911 said:**
> Lo que te recomiendo para ese modem es que lo configures como router. De ese modo, es el modem el que marca la conexión y te olvidás. Así va a funcionar con sólo conectarlo a una máquina mediante el cable de red sin importar el sistema operativo que use. 
Para hacerlo, acá[0] hay un pdf que explica cómo mediante telnet, seguilo paso a paso que funciona. En lugar de usar el cmd de Windows lo hacés en una Terminal (Aplicaciones > Accesorios > Terminal) El mismo tuto debería estar acá[1] pero la página no carga lo que debería, por eso el pdf.
 
sudo es lo que se usa en Ubuntu antes de un comando para ejecutarlo como root o super usuario. Por ejemplo, para instalar o desinstalar un aplicación. En concreto podrías ser:
 
```
sudo aptitude install amule
```
 
para instalar aMule
 
 
 
¿El vieo on-board es Nvidia? En una terminal ejecutá 
```
lspci
``` y pegá el resultado acá así vemos que placa de video tenés. Si es Nvidia, en Sistema > Aministración > Controladores de Hardware, debería darte la opción de instalar los drivers. No es necesario que bajes nada de la página de Nvidia. 
 
 
 
De esto, ni idea.
 
[0] [http://rapidshare.com/files/129251750/INSTRUCTIVO_ZYXEL660.pdf.html](http://rapidshare.com/files/129251750/INSTRUCTIVO_ZYXEL660.pdf.html)
[1] [http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=197&root=132](http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=197&root=132)
 
Hola ya voy comprendiendo, aunque todavia no hice nada agradezco las 2 respuestas, mi mother es una Asus M2N68-SE y viene con la Nforce630a/Geforce7025
 
de la pagina de Nvidia baje el siguiente paquete
[http://la.nvidia.com/object/linux_display_ia32_180.51.html](http://la.nvidia.com/object/linux_display_ia32_180.51.html)
 
como para tener algo e ir resolviendo aun cuando en el sitio especificaba que no era exactamente para mi tarjeta de video, se pone muy dificultoso esto ya que para estar al no poder entrar a internet desde mi ubuntu, tengo que iniciar en xp leer y anotar volver a iniciar y despues el intento de solucionar, espero que con los datos de mi equipo me proporcionen las ayudas mas favorables, ah!! mi monitor es un CRT Samsung 753.
):PSaludos a todos!!!

---

### Post by luks911 on 2009-05-28
Ok. Bajate el pdf que te pasé y tratá de llevarlo a cabo. Podés hacerlo desde XP, es lo mismo. Una vez que tengas internet, el tema de la placa de video lo solucionás con dos clicks.
Si te surge alguna duda con lo del modem avisá.

---

### Post by Ciudadela on 2009-05-28
Gracias!!!! ** Luks911**, ...ya mañana lo llevo a cabo ahora estoy con un par de escarbadientes en los parpados!!!

---

