---
title: "Problema con Gnome classic en lugar de Shell"
date: 2012-09-10
forum: Software
---

### Post by daggaz on 2012-09-10
Hola,
Tengo una nueva computadora Asus K53S Series, con una tarjeta de video NVidia GForce 610M con 2 Gb dedicados.
Instalé Ubuntu y todo aparentemente bien, hasta el punto en el que  instalé Gnome Shell y traté de pasarme ahí, pues al momento de logear en  lugar de ver Shell veo el escritorio clásico de Gnome.
Unity funciona muy bien, incluido el 3D...
He buscado en internet sin mucho éxito, salvo una pista de que quizás se  trate de un problema con la aceleración 3D y Gnome Shell y no sé que  hacer.
El post más similar al problema que tengo es este:
[http://askubuntu.com/questions/132860/ubuntu-12-04-gnome-shell-problem](http://askubuntu.com/questions/132860/ubuntu-12-04-gnome-shell-problem)
Al momento de escribir en la terminal
```
gnome-shell --replace
```Me da lo siguiente:
```
Xlib: extension "GLX" missing on diaplay ":0".
Violación de segmento ('core' generado)
```No he instalado controladores privativos por que al momento de ingresar a  la sección de hardware, no muestra los de la tarjeta NVidia, pero al momento de la instalación activé la opción de Software de Terceros...  ¿Será ese el problema? en caso de ser así ¿conocen algún buen tutorial  para forzar esta instalación si Ubuntu no la sugiere?
 Gracias.

---

### Post by EnriqueK on 2012-09-11
Puedes seguir estas instrucciones para instalar el controlador descargado desde el sitio oficial
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

1.- pone el archivo .run en tu carpeta personal

2.- Ejecuta por única vez estos comandos
sudo su
apt-get install build-essential
apt-get install linux-headers-$(uname -r)
echo 'blacklist nouveau' > /etc/modprobe.d/nvidia-installer-disable-nouveau.conf
echo 'options nouveau modeset=0' >> /etc/modprobe.d/nvidia-installer-disable-nouveau.conf
update-initramfs -u
init 6

3.- Cuando reinicie, entras a tty1 mediante Ctrl+Alt+F1 y ejecuta estos comandos
sudo su
service lightdm stop
nvidia-uninstall
apt-get --purge remove nvidia*
bash NV
pulsas Tab para que se complete el nombre del controlador
pulsas Enter y acepta todo
service lightdm start
Eso sería todo, solo agrego que los comandos del punto 3.- deberás repetirlos cada vez que haya cambios en el kernel, el xorg , por lo que a estos comando conviene tenerlos en un Script
Si quieres desinstalarlo ejecuta
sudo rm /etc/modprobe.d/nvidia-installer-disable-nouveau.conf
sudo rm /etc/X11/xorg.conf
sudo update-initramfs -u
sudo init 6
Cuando reinicio , ejecuta
sudo nvidia-uninstall

---

### Post by daggaz on 2012-09-11
Funcionó perfectamente :)
Muchas gracias.

---

