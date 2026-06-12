---
title: "Dale a Xfce4 la apariencia de KDE4"
date: 2008-06-02
forum: Software
---

### Post by andy_91 on 2008-06-02
[Dale a Xfce4 la apariencia de KDE4]("http://softwarelibre-propietario.blogspot.com/2008/06/dale-la-apariencia-de-kde4-xgce4.html")


Bueno siguiendo la linea de los tutoriales para conseguir la apariencia de Vista y Leopard acá les traigo un tutorial para conseguir la apariencia de KDE4 en Xfce

lo primero son los materiales a utilizar:

*Xfce4-menu-plugin

*Xfce4-mixer-plugin

*Xfce4-clipman-plugin

*orangeclock

*otros plugins (lanzadores, mostrar escitorio, caja de iconos, paginador, bandeja de sistema, etc)

*para poner los iconos como en kde usa los de [crystal project]("http://www.4shared.com/file/22498213/54e3283c/CrystalProjecttar.html")

* [Temas (GTK y Xfwm) y fondo de panel]("http://www.sendspace.com/file/brhyyr")

1-bueno como primer paso nos quedamos con un solo panel inferior
2-descomprimimos el paquete con los temas en nuestro home
3-ahora tecleamos alt+f2 y escribimos $sudo Thunar y marcamos la casilla que dice ejecutar en un terminal
se abre el terminal y en ella colocamos nuestra contraseña de superusuario
4-una vez hecho lo anterior se habre el explorador de archivos, y en el seleccionamos las carpetas murrinestormcloudsilver y murrine
Las movemos a la carpeta /usr/share/themes, luego descomprimimos el tema de iconos y lo movemos a /usr/share/icons
Solo Para Linux Mint

copia la siguiente [imagen]("http://imagenes.pro/out.php/i371876_mintkde.png") en /usr/share/pixmaps
luego hacemos clic secundario en el menú propiedades y elegimos la imagen como botón de icono

5-vamos a menú-configuración- configuracion de la interfas de usuario

en la parte de tema elegimos murrine stormcloudsilver y en iconos crystal projet

6- en el menú-configuración-windows manager settings, elegimos murrine

7-cambiamos el fondo de pantalla y el botón de icono del menú por el siguiente(Distribuciones No Mint) /usr/share/icons/CrystalProject/128x128/apps/kde-icon.png

Para Mint

descarga los siguientes [fondos]("http://www.kde-look.org/content/show.php/Unofficial+Linux+Mint+5+Wallpapers.?content=78517"), y coloca el que mas te guste

8-cerramos sesión y volvemos a entrar

9-ahora reemplazamos el reloj común por el orangeclock y lo personalizamos como queremos

10-le quitamos el cuadro tanto a la bandeja de sistema como al orangeclock

11- como final disponemos de los plugins del panel como queramos


les dejo unos [fondos de pantalla]("http://www.sendspace.com/file/siydka") de kde

y por supuesto algunos pantallazos

[http://img212.imageshack.us/my.php?image=pantallazourli7mj5.jpg](http://img212.imageshack.us/my.php?image=pantallazourli7mj5.jpg)

[http://img293.imageshack.us/my.php?image=pantallazodarynaov0.jpg](http://img293.imageshack.us/my.php?image=pantallazodarynaov0.jpg)

Ahora Hablemos de Detalles Que solo Linux Puede ofrecer

Demos una apariencia completa con amarok

$ sudo apt-get install language-pack-kde-es-base language-pack-kde-es amarok

Si no queremos amarok por que instala servicios de KDE que preferimos no instalar entonces probemos Exaile

$ sudo apt-get install exaile

Y que hay de Super Karamba.....

$ sudo apt-get install adesklets

los [adesklets]("http://adesklets.sourceforge.net/") podrian reemplazar a los super karamba

[Pantallazo adesklets en KDE]("http://adesklets.sourceforge.net/images/screenshots/jimbob_0.jpg")
[URL="http://adesklets.sourceforge.net/images/screenshots/thibault_0.jpg"]
Pantallazo adesklets en Gnome[/URL]

[Pantallazo adesklets Xfce]("http://adesklets.sourceforge.net/images/screenshots/darkliquid_0.jpg")

---

