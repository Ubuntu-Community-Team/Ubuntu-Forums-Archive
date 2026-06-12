---
title: "Ayuda con script para monitorear screen, y si cae levantarla"
date: 2010-08-07
forum: Software
---

### Post by Jorgee! on 2010-08-07
Hola muchachos, les agradeceria si me ayudan con esto, porque la verdad 0 linux.....

Tengo un script, que lo que hace es levantar un server de BF2:

```
#!/bin/sh

echo "Starting Project Reality Server"

sleep 1

cd /home/reality/serverbf/bf2/

sleep 1

screen -A -m -d -S serverPR ./start.sh +modPath mods/pr
```Bien, ese script funciona a la perfeccion....... el problema es cuando intente hacer un chequeo basado en las siguientes paginas: 

[http://bf2tech.org/index.php/Scripts:RestartScript](http://bf2tech.org/index.php/Scripts:RestartScript)

En la 1ra parte de esa pagina, donde hay que poner un script titulado /path/to/bf2/servermonitor, no dice como ponerle de nombre al script, es decir en el startit.sh hace referencia al path servermonitor, pero como hace para encontrar un script ahi sin un nombre especifico? Hay algun tipo index.sh? Jaja es media boluda la pregunta, pero la verdad no le encontre la vuelta....

En fin, la mayoria recomienda este script de la misma web:

```
#!/bin/bash
#
# Press Ctrl+C to stop the restarting
echo "##########################"
echo "# Bf2 Server Starting #"
echo "##########################"
echo To stop the restarting press Ctrl+C when the server is being restarted
echo
trap 'echo; echo $SRV Server Restarter has been STOPPED!; exit 1' _**2**_
C1=0
while true
do
C1=$((C1+=1))
cd /home/bf2srv/bf2
# Modify the line bellow to match your server execution command line
./start.sh
echo "Bf2 server restarted $C1 time(s)!"
sleep 10
done

```El problema es que el ubuntu me da errores, primero con el 2 que marque en negrita, me dice "No es un comando valido", y despues me dice que no encuentra start.sh, lo que me parece muy raro porque en el script que yo uso actualmente dice lo mismo, cd home/path y despues ./start.sh, y funciona igual......

Lo que estoy tratando de hacer es un monitor, para que si el server de BF2 se cae, se levante solo, al parecer es simple, pero no logro mas que darme la cabeza contra la pared.... es que nunca habia tocado linux hasta hace unos dias....

Les agradeceria cualquier ayuda.... saludo

---

### Post by alfplayer on 2010-08-07
> NOTE: Make sure to change /path/to/bf2 to your bf2 install dir!!!

Eso quiere decir que hay que reemplazar */path/to/bf2* por el directorio de BF2.

Si el directorio es */home/reality/serverbf/bf2/*, según las instrucciones de esa página el archivo/script servermonitor tiene que estar en ese directorio. Se puede usar cualquier nombre de archivo (por ejemplo *servermonitor*).

En el segundo script también habría que reemplazar */home/bf2srv/bf2* por el directorio de BF2.

---

