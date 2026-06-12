---
title: "problema shockwave flash 10.2 r152 en firefox"
date: 2011-03-13
forum: Software
---

### Post by Brath-ga on 2011-03-13
Hola a tod@s.
Tengo un problema con shockwave flash 10.2 r152 en firefox 3.6.15.
El problema consiste en que aveces no carga el plugin de flash y da un error.
Si recargo la página varias veces, se suele solucionar, pero al cambiar de página, vuelve a salir el error.
Tengo también instalado chromium y aquí no sucede este error.
Le pasa a alguien más?
Tenéis alguna solución?

---

### Post by Liv~ on 2011-03-13
A mi me pasa lo mismo desde la actualización 3.6.14
A veces tira error que se "crashea" y a veces cargan los videos pero se ven en blanco y negro. Por ahí no pasa nada y anda todo bien. Con la actualización 3.6.15 parecía haberse arreglado pero ayer justamente volvió a pasar, con la diferencia que esta vez había audio pero el video se veía negro, o sea, no había imagen. Después se arregló. 
No pasa todo el tiempo, constantemente, pero sería bueno saber a qué puede deberse. No tuve problemas con el flash hasta la actualización 3.6.14

---

### Post by mama21mama on 2011-03-14
tienen que usar este: Flash 10.3 d180
ese trae un bug

```
wget http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer10-3/flashplayer10-3_b1_lin_030811.tar.gz
```
```
tar zxvf flashplayer10-3_b1_lin_030811.tar.gz
```
```
sudo mv /usr/lib/flashplugin-installer/libflashplayer.so /usr/lib/flashplugin-installer/libflashplayer.so.bak
```
```
sudo mv /flashplayer10-3_b1_lin_030811/libflashplayer.so /usr/lib/flashplugin-installer/
```

[URL="http://ubuntulife.wordpress.com/2011/03/08/%c2%bfproblemas-con-flash-10-2-instalate-flash-10-3-beta/"]
Fuente[/URL]

---

### Post by Brath-ga on 2011-03-20
Gracias mama21mama, pero al efectuar el ultimo comando, me aparece este error:

sudo mv /flashplayer10-3_b1_lin_030811/libflashplayer.so /usr/lib/flashplugin-installer/
mv: no se puede efectuar «stat» sobre «/flashplayer10-3_b1_lin_030811/libflashplayer.so»: No existe el fichero o el directorio

busqué el directorio /flashplayer10-3_b1_lin_030811 y no me aparece por ningún lado.

---

### Post by mama21mama on 2011-03-20
```
sudo mv libflashplayer.so /usr/lib/flashplugin-installer/
```

):P

---

### Post by EnriqueK on 2011-03-20
Otra forma de hacerlo


Usa synaptic, pones flash en el buscador y eliminas todos los flash que tengas instalado como ser flashplugin-installer  y todo lo que sea flash, lo mismo haces para elininar todo lo que tengas de gnash,
seguidanmente si usas 32 bits, ejecuta los siguientes comandos en el ordem indicado
```
wget [http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer10-3/flashplayer10-3_b1_lin_030811.tar.gz](http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer10-3/flashplayer10-3_b1_lin_030811.tar.gz)
sudo tar -zxvf flashplayer10-3_b1_lin_030811.tar.gz --directory /usr/lib/mozilla/plugins
rm flashplayer10-3_b1_lin_030811.tar.gz
```
si usas 64 bits ejecuta estos otros comandos
```
wget -c [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p2_64bit_linux_092710.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p2_64bit_linux_092710.tar.gz)
sudo tar -zxvf flashplayer_square_p2_64bit_linux_092710.tar.gz --directory /usr/lib/mozilla/plugins
rm flashplayer_square_p2_64bit_linux_092710.tar.gz
```

el priner comando realiza la descarga del plugin, por lo que tendrá algo de demora
el segundo descomprime el archivo en el directorio apropiado
el tercero borra el archivo descargado[QUOTE][QUOTE]

---

### Post by Liv~ on 2011-03-23
Al final actualicé el flash y aparentemente todo bien... Ahora estoy viendo si actualizo el zorrito.

Gracias por la ayuda.

---

