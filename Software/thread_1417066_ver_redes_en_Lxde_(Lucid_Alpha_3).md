---
title: "ver redes en Lxde (Lucid Alpha 3)"
date: 2010-02-26
forum: Software
---

### Post by joseluis on 2010-02-26
Hola, el título es extraño, pero no sabía que poner o mejor dicho como resumir.
El tema es el siguiente:
En Ubuntu, al hacer Click en Lugares / Red , puedo ver, entrar y trabajar con carpetas de una red win o una red de cualquier tipo. Es más, no necesité instalar samba para eso.
Por lo que pude rescatar de preguntar por otro lado, es un tema de nautilus, que puede explorar eso.

Ahora, Puse en una notebook el entonrno LXDE, que convive entonces con Gnome, y no pude hacer lo mismo. 
Entnoces, para ver la red cuando estoy en sesión con LXDE ,lo que hago es abrir nautilus en lxde y ahi si la veo.

El problema viene acá ahora. Estuve probando LUBUNTU en su versión alpha 3 y me parece sencillamente maravilloso. Nada mejor para mi notebook. Sin embargo, tengo ese problema descrito anteriormente. Si lo instalo de "cero", que es lo que quisiera hacer, pierdo el nautilus y pierdo ese acceso a ver la red.

Acá va la pregunta:[B] ¿cómo hacer para ver la red sin necesidad de nautilus desde lxde?
[/B]
Espero haber sido claro en el planteo y agradezco lo que puedan ayudarme.

---

### Post by NickCis on 2010-02-27
Fijate si esto te sirve:
[http://wiki.gleducar.org.ar/index.php/Navegar_redes_SMB_con_Thunar](http://wiki.gleducar.org.ar/index.php/Navegar_redes_SMB_con_Thunar)

Esta para el Thunar, pero para el PCmanfm tmb debe servir =P

Saludos.

---

### Post by alfplayer on 2010-02-28
En Karmic se pueden usar comandos del paquete gvfs-bin:

Ejemplos:

Listar archivos:
*gvfs-ls smb://pc_remota/recurso_compartido*
Montar:
*gvfs-mount smb://pc_remota/recurso_compartido*

Los puntos de montaje quedan con la forma:
*~/.gvfs/recurso_compartido on pc_remota*

Otros protocolos que se pueden usar con GVFS son SFTP y FTP.

---

### Post by juancarlospaco on 2010-02-28
*Vale aclarar que si no anda, esta bien, pues esta en pruebas aun... Alpha*

---

### Post by joseluis on 2010-02-28
GRACIAS! voy a probar en la notebook en donde tengo el lxde, y ver si entonces instalo el Lubuntu. Lo recomiendo de verdad me está volando la cabeza para equipos de bajos recursos

---

### Post by joseluis on 2010-02-28
> **NickCis said:**
> Fijate si esto te sirve:
[http://wiki.gleducar.org.ar/index.php/Navegar_redes_SMB_con_Thunar](http://wiki.gleducar.org.ar/index.php/Navegar_redes_SMB_con_Thunar)

Esta para el Thunar, pero para el PCmanfm tmb debe servir =P

Saludos.

no puedo. no encuentro los mismos o semejantes comandos a seguir

---

### Post by alfplayer on 2010-02-28
Si el objectivo es tener una distribución de Ubuntu y LXDE estable y actualizada recomiendo Masonux. Tiene bugs pero es la única distribución liviana que pude encontrar con LXDE y con paquetes estables de la versión final 9.10. La imagen es de 356 MB.

Hay otras populares con la combinación Ubuntu y LXDE pero con defectos: U-lite que solo tiene versiones anteriores a la versión final 9.10 y Lubuntu que no tiene una versión estable (solo ofrece versiones con paquetes anteriores a la versión final 9.10 o la versión alpha de Lucid).

---

### Post by joseluis on 2010-03-02
GRACIAS!
estoy bajando Masonux a ver qué onda. Hay dos versiones, una basada en ubuntu 9.04 y otra en 9.10. La estable es la 9-04. 
Ahora, de todos modos, creo que está piola ver el desarrollo de lubuntu que saldrá junto ubuntu 10.04.

Vuelvo con mi planteo inicial y doy un paso más a mi pregunta.: si con Gnome puedo ver la red de casa (la maquina que tiene linux y otra que tiene win), me pregunto si instalando nautilus en LXDE se puede lograr ese beneficio. ¿se puede instalar nautilus en lxde? ¿perderá la ligereza lxde?

---

### Post by alfplayer on 2010-03-02
> **joseluis said:**
> GRACIAS!
estoy bajando Masonux a ver qué onda. Hay dos versiones, una basada en ubuntu 9.04 y otra en 9.10. La estable es la 9-04. 
Ahora, de todos modos, creo que está piola ver el desarrollo de lubuntu que saldrá junto ubuntu 10.04.

Vuelvo con mi planteo inicial y doy un paso más a mi pregunta.: si con Gnome puedo ver la red de casa (la maquina que tiene linux y otra que tiene win), me pregunto si instalando nautilus en LXDE se puede lograr ese beneficio. ¿se puede instalar nautilus en lxde? ¿perderá la ligereza lxde?

El iso de Masonux basado en 9.10 también es estable porque tiene los paquetes de la versión final de Ubuntu 9.10, pero al parecer tiene algunos bugs más que el iso basado en 9.04.

Se puede instalar y usar nautilus con LXDE, no hay problema con eso. Se pierde un poco de la ligereza en cuanto al espacio en el disco y la cantidad de paquetes instalados ("aptitude install" informa el espacio en disco que se ocupará antes de continuar la instalación, si se instala y no gusta la sobrecarga es posible desinstalarlo, también sin inconvenientes). En cuanto al consumo de memoria y CPU probablemente sean mayores que los de pcmanfm.

No sé si es posible reemplazar pcmanfm (el file manager de LXDE) con nautilus, pero es aconsejable para disminuir la utilización de recursos usar normalmente pcmanfm y opcionalmente usar nautilus solo si se quiere usar una característica que no tiene pcmanfm como conectarse a redes. Nautilus no es necesario para navegar los archivos de las redes, se puede hacer con pacmanfm desde ~/.gvfs después de conectarse a la red.

---

### Post by joseluis on 2010-03-03
> **alfplayer said:**
> El iso de Masonux basado en 9.10 también es estable porque tiene los paquetes de la versión final de Ubuntu 9.10, pero al parecer tiene algunos bugs más que el iso basado en 9.04.

Se puede instalar y usar nautilus con LXDE, no hay problema con eso. Se pierde un poco de la ligereza en cuanto al espacio en el disco y la cantidad de paquetes instalados ("aptitude install" informa el espacio en disco que se ocupará antes de continuar la instalación, si se instala y no gusta la sobrecarga es posible desinstalarlo, también sin inconvenientes). En cuanto al consumo de memoria y CPU probablemente sean mayores que los de pcmanfm.

No sé si es posible reemplazar pcmanfm (el file manager de LXDE) con nautilus, pero es aconsejable para disminuir la utilización de recursos usar normalmente pcmanfm y opcionalmente usar nautilus solo si se quiere usar una característica que no tiene pcmanfm como conectarse a redes. Nautilus no es necesario para navegar los archivos de las redes, se puede hacer con pacmanfm desde ~/.gvfs después de conectarse a la red.

Gracias, me vienen muy bien las aclaraciones y notas. No se bien cómo hacer esto de "~/.gvfs" si bien está explicado más arriba. Intentaré nuevamente a ver qué pasa, pero no puedo hacerlo.

---

### Post by alfplayer on 2010-03-03
> **joseluis said:**
> Gracias, me vienen muy bien las aclaraciones y notas. No se bien cómo hacer esto de "~/.gvfs" si bien está explicado más arriba. Intentaré nuevamente a ver qué pasa, pero no puedo hacerlo.

Hago la aclaración que ~ es el directorio home del usuario, por ejemplo: /home/*usuario* (hay que reemplazar *usuario* por el nombre de usuario de Ubuntu, por defecto Ubuntu usa el primer nombre de la persona).

Reemplazando, ~/.gvfs es el directorio: /home/*usuario*/.gvfs

---

### Post by alfplayer on 2010-03-03
Una advertencia para los usuarios de LXDE de Karmic como los de Masonux 9.10 r1:

pcmanfm de Karmic tiene un bug muy molesto que hace que pcmanfm no muestre los íconos de archivos y no sabe con qué programas abrir los diferentes tipos de archivos. Esto se puede resolver instalando el paquete de pcmanfm de Lucid: [http://packages.ubuntu.com/lucid/i386/pcmanfm/download]("http://packages.ubuntu.com/lucid/i386/pcmanfm/download")

---

### Post by juancarlospaco on 2010-03-03
Si, no se ven los iconos, 
se soluciona despues de instalar, antes de ejecutar PCManFM, ejecutar en la Terminal:
[B]
echo gtk-icon-theme-name="Tango" > $HOME/.gtkrc-2.0[/B]

---

### Post by alfplayer on 2010-03-03
> **juancarlospaco said:**
> Si, no se ven los iconos, 
se soluciona despues de instalar, antes de ejecutar PCManFM, ejecutar en la Terminal:
[B]
echo gtk-icon-theme-name="Tango" > $HOME/.gtkrc-2.0[/B]

Esto sería solo para resolver lo de los íconos, pero además casi siempre aparece la ventana para elegir el programa que abre el archivo, o sea, no abre la aplicación correspondiente según el tipo de contenido. Bug report: [https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/455344]("https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/455344")

---

### Post by joseluis on 2010-03-12
> **alfplayer said:**
> Esto sería solo para resolver lo de los íconos, pero además casi siempre aparece la ventana para elegir el programa que abre el archivo, o sea, no abre la aplicación correspondiente según el tipo de contenido. Bug report: [https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/455344]("https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/455344")

¿Quizás me convenga esperar que salga Lubuntu, confiando en que ese bug pueda ser resuelto?

---

### Post by alfplayer on 2010-03-12
Si se publica una versión final de Lubuntu 10.04 es casi seguro que el bug no va a estar.

---

