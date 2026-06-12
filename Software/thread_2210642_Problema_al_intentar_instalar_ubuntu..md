---
title: "Problema al intentar instalar ubuntu."
date: 2014-03-11
forum: Software
---

### Post by martinx2 on 2014-03-11
B[COLOR=#000000]uenas! tras intentar todo el día de instalar la versión 13.10 64 bits buscando soluciones y fallar me decidí en postear mi problema.[/COLOR]

[COLOR=#000000]El problema es que al poner en instalar o probar sin instalar, o se queda la pantalla en negro o me tira una pantalla de todos colores,[/COLOR]
[COLOR=#000000]leí por ahí que podía ser un problema por los drivers de la targeta gráfica (NVidia), probé iniciarlo con el parametro nomodeset y sigue con la pantalla negra.[/COLOR]

[COLOR=#000000]Sé que es un foro de ubuntu, pero vale decir que también intenté con linux mint 64 bits y tengo el mismo problema de la pantalla negra, O con este OS tambien me pasa[/COLOR]
[COLOR=#000000]que cuelga ahí nomás, (en la pantalla de linux mint).[/COLOR]

[COLOR=#000000]Alguna solución?[/COLOR]

[COLOR=#000000]Tengo una ASUS M5A78L-M[/COLOR]
[COLOR=#000000]Una NVidia Geforce gtx 650 ti[/COLOR]
[COLOR=#000000]Un AMD FX(tm) 6100 six core 3.30 GHz.[/COLOR]
[COLOR=#000000]8 GB de RAM.[/COLOR]

[COLOR=#000000]y por si sirve la información, tengo un lcd 32" que uso de monitor, y mi OS actual es W7.[/COLOR]
[COLOR=#000000]Estoy desesperado por introducirme en linux xD. [/COLOR]
[COLOR=#000000]Desde ya muchas gracias![/COLOR]

---

### Post by gmunioz on 2014-03-13
Para instalar en ordenadores con problemas de gráficas, se puede realizarse el siguiente procedimiento:

a- Descargar la imagen mini.iso de 32 ó 64 bits, según más convenga:
Para 32 bits
[http://archive.ubuntu.com/ubuntu/dists/raring/main/installer-i386/curren](http://archive.ubuntu.com/ubuntu/dists/raring/main/installer-i386/curren)...
Para 64 bits
[http://archive.ubuntu.com/ubuntu/dists/raring/main/installer-amd64/curre](http://archive.ubuntu.com/ubuntu/dists/raring/main/installer-amd64/curre)...
Y luego grabarla en un:
cd
Con
Grabador de cd preferido (opción grabar imagen, no grabar cd)
Usb
Con unetbootin
Para Windows
[http://unetbootin.sourceforge.net/unetbootin-windows-latest.exe](http://unetbootin.sourceforge.net/unetbootin-windows-latest.exe)
Para Gnu/Linux
[http://unetbootin.sourceforge.net/unetbootin-linux-latest](http://unetbootin.sourceforge.net/unetbootin-linux-latest)

b- Iniciar el ordenador, conectado por cable, a modem con dhcp activado.
Iniciar la instalación
Completar todos los datos requeridos
Elegir particionamiento manual e instalar en tres (3) particiones dos ext4 (para / y /home) una de intercambio para swap
En la pantalla de selección de paquetes solo marcar servidor.
Dejar desmarcadas todas las opciones restantes y presionar Enter.
El sistema completara la instalación sin entorno gráfico.

c- Al reiniciar en la pantalla negra con cursor, escribir primero el nombre de usuario, dar enter y después la contraseña
(no se muestra nada, y dar enter)
Este es el verdadero Ubuntu, solo texto, sin fallas, ahora a instalar lo necesario, ejecutando
> 
sudo su
(contraseña de usuario)
apt-get update
apt-get install xubuntu-desktop --no-install-recommends synaptic gedit jockey-text ubuntu-restricted-extras file-roller rar unrar system-config-printer cups smplayer brasero p7zip devede libreoffice libreoffice-l10n-es gimp gdebi firefox firefox-locale-es thunderbird thunderbird-locale-es

Terminada la instalación ejecutar, en la misma terminal
> 
apt-get install -f
dpkg --configure -a
jockey-text -l
(aparecerá el driver privativo de la tarjeta de video, selo hablita con)
jockey-text -e driver
(donde driver es lo que informó el comando)
apt-get clean
reboot

Al reiniciar iniciará con entorno gráfico liviano
Queda configurar a gusto y synaptic ó gdebi mediante, instalar con paciencia y criterio
de selección adecuado los paquetes que nos hagan falta.
PD:
Para otros entornos gráficos, posteriormente instalar unity-desktop, gnome-desktop, kubuntu-desktop, lubuntu-desktop. etc.

---

### Post by martinx2 on 2014-03-13
Ante todo, muchas gracias por la respuesta. Intenté lo que dijiste pero nisiquiera inicia con la instalación. Me aparece el menú de unetbootin y cualquier opción que ponga se pone un cursor abajo a la izquierda(en el que no se puede escribir nada) y cuelga ahí nomás. Alguna otra solución?

---

### Post by guillermolisi on 2014-03-15
> **martinx2 said:**
> Ante todo, muchas gracias por la respuesta. Intenté lo que dijiste pero nisiquiera inicia con la instalación. Me aparece el menú de unetbootin y cualquier opción que ponga se pone un cursor abajo a la izquierda(en el que no se puede escribir nada) y cuelga ahí nomás. Alguna otra solución?

Proba con la version beta de la 14.04, por lo menos para saber si con el nuevo stack de hardware del kernel Linux que trae esa version de Ubuntu mejora el reconocimiento de hardware de tu maquina.

Me parece que el origen del problema excede cuestiones de drivers de video porque la recomendacion que te hicieron deberia haber funcioando.

---

