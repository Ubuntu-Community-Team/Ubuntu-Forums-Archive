---
title: "Virtual Box"
date: 2010-02-24
forum: Software
---

### Post by sp33d3rs on 2010-02-24
Instale Windows en una laptop con ubuntu por medio de Virtual Box.
El problema comenzo cuando Corel Word Perfect no funcionaba con wine.
Asi que instale Virtual Box y un windows que inicie con el programa andando en primera instancia, sin drivers, ni sonido ni nada para mas velocidad.
 
Ahora quiero si alguien me puede ayudar a configurar mi escritorio..
 
Quiero saber si se puede configurar que el Virtual Box inicie windows con un acceso en el escritorio, (ya que la notebook no la oy a usar yo y quiero que resulte todo lo mas sencillo posible), pero no que arranque el soft, sino que arranque directamente el windows cargando, y que inicie en lo posible en el escritorio 2. Asi se puede trabajar en un escritorio con ubuntu (9.10 mi caso) y en otro escritorio, winchows maximizado.
 
Espero haber sido claro.
 
Muchas gracias de antemano

---

### Post by rubioo on 2010-02-24
Hola, por ahi te sirve esto [http://ubuntuforums.org/showthread.php?t=875284]("http://ubuntuforums.org/showthread.php?t=875284")

---

### Post by sp33d3rs on 2010-02-24
> **rubioo said:**
> Hola, por ahi te sirve esto [http://ubuntuforums.org/showthread.php?t=875284](http://ubuntuforums.org/showthread.php?t=875284)
 
WFT is GMD Session...
Che, no lo entendi bien, cazo algo de ingles pero no entendi que es lo que hace..

---

### Post by guillermolisi on 2010-02-24
> **sp33d3rs said:**
> WFT is GMD Session...
Che, no lo entendi bien, cazo algo de ingles pero no entendi que es lo que hace..
GDM es el acronimo de Gnome Display Manager o sea lo que comunmente se llama escritorio grafico Gnome.

En ese thread se explica como generar un acceso en el escritorio grafico y que contenido debe tener ese archivo para que invoque a VirtualBox e inicie una maquina virtual determinada dentro del inventario de VMs de VBox.

El nombre de la maquina virtual, mencionado en la linea que comienza por el comando "exec" debe coincidir con el que le diste dentro de VirtualBox.

En la linea que comienza con "name" podes poner lo que quieras ya que es informativo pero relacionado con el tipo de VM que se iniciara.

---

### Post by Mister X on 2010-03-03
tenes que crear un archivo en el escritorio y ponerle la extension .desktop con el siguiente contenido:
```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Windows 2003 server
Type=Application
Comment=Maquina virtual
Terminal=false
Exec=VirtualBox -startvm <nombre de la vm a iniciar>
Icon=/usr/share/pixmaps/VBox.png
Categories=System;
GenericName=

```

---

