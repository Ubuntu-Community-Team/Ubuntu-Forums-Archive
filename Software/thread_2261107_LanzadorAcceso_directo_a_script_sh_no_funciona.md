---
title: "Lanzador/Acceso directo a script sh no funciona"
date: 2015-01-16
forum: Software
---

### Post by Simbiosys on 2015-01-16
Hola a todos! 

Tengo un archivo .sh que inicia Kosmo.
Si lanzo el programa desde consola funciona perfectamente pero cuando creo un lanzador/acceso directo a ese archivo no funciona, se queda un ratito pensando (simbolito de ubuntu girando) y luego se termina todo sin hacer nada.

Si voy a la consola y ejecuto directamente, me da el siguiente error:
```
xxx@xxx-desktop:~$ /home/xxx/Kosmo-3.0/bin/Kosmo.sh
/home/xxx/Kosmo-3.0/bin/Kosmo.sh: 11: /home/xxx/Kosmo-3.0/bin/Kosmo.sh: ./jre/bin/java: not found
```

Si en la consola navego hasta el directorio donde está el SH y ejecuto, abre perfecto:
```
xxx@xxx-desktop:~$ cd Kosmo-3.0/
xxx@xxx-desktop:~/Kosmo-3.0$ cd bin
xxx@xxx-desktop:~/Kosmo-3.0/bin$ ./Kosmo.sh

```

CONTENIDO DE Kosmo.sh:
```
#!/bin/sh
# Kosmo.sh
KOSMO_LIBS_PATH="../libs"
export PROJ_LIB="./crs/data"

if [ -n "$LD_LIBRARY_PATH" ]; then
	export LD_LIBRARY_PATH=$KOSMO_LIBS_PATH:$LD_LIBRARY_PATH
else
	export LD_LIBRARY_PATH=$KOSMO_LIBS_PATH
fi
./jre/bin/java -Djava.library.path=/usr/lib:"../libs" -Dsun.java2d.d3d=false -cp .:./kosmo_desktop.jar -Xmx800M com.vividsolutions.jump.workbench.JUMPWorkbench -plug-in-directory ./ext
```

En el lanzador, no sucede nada (asumo que es el mismo error de ./jre/bin/java: not found)

¿Podrían darme una mano para ver que me está faltando?

Un abrazo y mil gracias de antemano.

Saludos,
Nahuel.

---

### Post by enriquek2 on 2015-01-16
Estos problemas se dan cuando un script debe ejecutarse dentro de una determinada carpeta, veo  dos soluciones
1.- crear otro script que tome en cuenta esta situación 
2.- modifica el script poniendo al comienzo la ruta de la carpeta en donde debe ejecutarse
o sea
#!/bin/sh
cd /home/tu_usuario/Kosmo-3.0$/ bin
# Kosmo.sh
"
etc
etc

---

### Post by Simbiosys on 2015-01-19
Enriquek2, gracias por tu respuesta.

Eso lo había probado pero no funcionó, te dejo pegado el script modificado que no funcionó a ver si le estoy errando en algo. Gracias!!!

```
#!/bin/sh
cd /home/xxx/Kosmo-3.0$/bin/
# Kosmo.sh
KOSMO_LIBS_PATH="../libs"
export PROJ_LIB="./crs/data"

if [ -n "$LD_LIBRARY_PATH" ]; then
	export LD_LIBRARY_PATH=$KOSMO_LIBS_PATH:$LD_LIBRARY_PATH
else
	export LD_LIBRARY_PATH=$KOSMO_LIBS_PATH
fi
./jre/bin/java -Djava.library.path=/usr/lib:"../libs" -Dsun.java2d.d3d=false -cp .:./kosmo_desktop.jar -Xmx800M com.vividsolutions.jump.workbench.JUMPWorkbench -plug-in-directory ./ext

```

---

### Post by enriquek2 on 2015-01-19
Para salir de dudas respecto a la ruta del  Script,  abre un terminal y arrastra a este el script , muestra lo que te sale

---

### Post by Simbiosys on 2015-02-08
```
xxx@xxx-desktop:~$ '/home/xxx/Kosmo-3.0/bin/Kosmo.sh' 
/home/xxx/Kosmo-3.0/bin/Kosmo.sh: 2: cd: can't cd to /home/xxx/Kosmo-3.0$/bin/
/home/xxx/Kosmo-3.0/bin/Kosmo.sh: 12: /home/xxx/Kosmo-3.0/bin/Kosmo.sh: ./jre/bin/java: not found
```

---

### Post by Simbiosys on 2015-07-02
Disculpen, aún no pude solucionar esto... por si a alguien se le ocurre algo... muchas gracias.

---

### Post by enriquek2 on 2015-07-02
Ejecuta

 sudo gedit /usr/local/bin/kosmo 
pega el siguiente contenido

  #!/bin/sh 
 cd /home/xxx/Kosmo-3.0/bin
 ./Kosmo.sh

  Guarda y sales luego ejecuta para  darle permisos de ejecución
 sudo chmod +x /usr/local/bin/kosmo 

para hacerte propietario del script ejecutor
 sudo chown xxx.xxx /usr/local/bin/kosmo  

Ya estaría listo , para ejecutar el programa solo debes poner en terminal, en un lanzador o en Alt+F2 la expresión
 kosmo

---

### Post by Simbiosys on 2015-07-10
Hola Enriquek2!

Te cuento que probé con eso y:

1- Si ejecuto desde "ejecutar programa" ALT+F2 kosmo, todo bien abre sin problemas.
2- Si abro una terminal y pongo kosmo, todo bien abre sin problemas.
3- Si hago un lanzador que contenga kosmo:
3.1- si ejecuto desde el escritorio con doble clic ese lanzador, no abre... no pasa naranja.
3.2- si ejecuto desde una terminal el lanzador, abre todo bien sin problemas.

Que raro, está empecinada en no dejarme tener un hermoso acceso directo en el escritorio, jaja.
Bueno, no te hagas mas drama doy esto por solucionado ya que me cansó y me imagino que a usted también. Muchas gracias por la ayuda...

---

### Post by papibe on 2015-07-10
Hola Simbiosys.
> **Simbiosys said:**
> 3.1- si ejecuto desde el escritorio con doble clic ese lanzador, no abre... no pasa naranja.
Usa este formato para el lanzador del escritorio:
```
[Desktop Entry]
Version=1.0
Name=Lanzador_Personal_de_Kosmo
Comment=No mas naranjas
Exec=/usr/local/bin/kosmo
Icon=/home/usuario/Pictures/pic.png
**[COLOR="#B22222"]Terminal=true[/COLOR]**
Type=Application
Categories=Utility;Application;

```
El archivo debe tener extension .desktop y tener permiso de ejecución. Por ejemplo, si se llama kosmo.desktop:
```
mv kosmo.desktop ~/Desktop
chmod a+x ~/Desktop/kosmo.desktop
```
(cambia Desktop por Escritorio si tienes el sistema en español).

Espero que sirva. Cuéntanos como te va con eso.
Saludos.

P.D.: el ícono "/home/usuario/Pictures/pic.png" es opcional, pero se ve bastante bien si consigues uno ;)

---

### Post by Simbiosys on 2015-07-20
Hola ! gracias por tu respuesta papibe. Ahora efectivamente funciona, aunque con un detalle y es que me deja abierta una terminal, pero bueno ! A caballo regalado no se le miran los dientes... muchas gracias por tu ayuda y al resto también, doy por concluído ya que demasiado los he molestado... le coloqué el ícono de la aplicación, quedó pipíqq

Un abrazo.

---

### Post by enriquek2 on 2015-07-21
Ejecuta el siguiente Script

#!/bin/bash 
mkdir $HOME/Lanzadores
cd $HOME/Lanzadores
echo -e " #!/bin/bash \nNM1=\$((RANDOM%8000)) \nNM2=\$((RANDOM%7999)) \ngnome-desktop-item-edit --create-new \$NM1\$NM2.desktop " > Crear
 chmod +x Crear

Se va a crear en tu carpeta de usuario la carpeta Lanzadores entra a ella y doble click sobre Crear  y te aparecerá un cuadro de diálogo para crear lanzadores, se van a crear  en esa carpeta, pero luego lo mueves a donde quieras

---

