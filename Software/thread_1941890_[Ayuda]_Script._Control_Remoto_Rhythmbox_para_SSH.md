---
title: "[Ayuda] Script. Control Remoto Rhythmbox para SSH"
date: 2012-03-16
forum: Software
---

### Post by granjero on 2012-03-16
Hola ubuntueros. Ando con ganas de hacer un script para poder controlar rhytmbox desde el ipod, ya que tengo la pc en un lugar y muchas veces me encuentro en otro lado y de repente suenan unos hits de mi chica, in-bancables. 

Hasta ahora escribí esto: Pero como no se mucho de scripting y no estoy entendiendo lo que leo por la web recurro a uds. No termino de entender como sería la sintaxis para que el valor ingresado por el usuario sea usado en un if o en otro. cuando el if es uno solo no hay problema pero quiero que el valor lo use en 5 casos diferentes.

El script se llama CR.sh

```
#!/bin/bash
clear
echo "P. Play / Pausa"
echo "N. Siguiente"
echo "A. Anterior"
echo "0. Salir"
echo ""
echo "ingrese valor:"
read valor
#PLAY / PAUSA
if [ $valor = "P" -o "p" ]
	then
	clear
	DISPLAY=:0 rhythmbox-client --play-pause --print-playing
	sleep 3
	clear
fi
./CR.sh
#PROXIMA
if [ $valor = "N" -o "n" ]
	then
	clear
	DISPLAY=:0 rhythmbox-client --next --print-playing
	sleep 2
	clear
fi
./CR.sh
#ANTERIOR
if [ $valor = "A" -o "a" ]
	then
	clear
	DISPLAY=:0 rhythmbox-client --previous --print-playing
	sleep 2
	clear
#SALIR
	if [ $valor = 0 ]
	then
	exit 0
	clear
	else
	echo "valor incorrecto"
	fi

```

Muchas gracias por su tiempo!

salud!

---

### Post by granjero on 2012-03-16
En el chat me tiraron data que tenía que usar "case"
Autosolucioné!

Quedó así! Y funciona!

```
#!/bin/bash
clear
echo P. Play / Pausa
echo N. Siguiente
echo A. Anterior
echo 0. Salir
echo 
echo ingrese valor:

read valor

case "$valor" in

"P" | "p" )
	clear
	echo "play/pause"
	echo "Ahora suena:"
	DISPLAY=:0 rhythmbox-client --play-pause --print-playing
	sleep 2
	clear
	./CR.sh
;;

"N" | "n" )
	clear
	echo "next"
	echo "Ahora suena:"
	DISPLAY=:0 rhythmbox-client --next --print-playing
	sleep 2
	clear
	./CR.sh
;;

"A" | "a" )
	clear
	echo "anterior"
	echo "Estaba sonado:"
	DISPLAY=:0 rhythmbox-client --previous --print-playing
	echo "Ahora suena:"
	DISPLAY=:0 rhythmbox-client --previous --print-playing
	sleep 2
	clear
	./CR.sh
;;

"0" )
	exit 0
;;

* )
	clear 
	echo "entrada incorrecta, vuelva a intentar"
	sleep 2
	./CR.sh
;;

esac
```

---

### Post by granjero on 2012-03-16
Listísimo!
Ahora si.
el script se llama cr.sh
lo copie a /bin :KS
le puse unos espacios para que pueda verlo bien en iPod!
les dejo unas capturas...

```
#!/bin/bash
clear
echo ""
echo ""
echo ""
echo ""
echo P. Play / Pausa
echo N. Siguiente
echo A. Anterior
echo 0. Salir
echo 
echo ingrese valor:

read valor

case "$valor" in

"P" | "p" )
	clear
	echo ""
	echo ""
	echo ""
	echo ""
	echo "PLAY / PAUSE"
	echo "Ahora suena:"
	DISPLAY=:0 rhythmbox-client --play-pause --print-playing
	sleep 3
	clear
	cr.sh
;;

"N" | "n" )
	clear
	echo ""
	echo ""
	echo ""
	echo ""
	echo "PROXIMA"
	echo "Ahora suena:"
	DISPLAY=:0 rhythmbox-client --next --print-playing
	sleep 2
	clear
	cr.sh
;;

"A" | "a" )
	clear
	echo ""
	echo ""
	echo ""
	echo ""
	echo "ANTERIOR"
	echo "Estaba sonado:"
	DISPLAY=:0 rhythmbox-client --previous --print-playing
	echo "Ahora suena:"
	DISPLAY=:0 rhythmbox-client --previous --print-playing
	sleep 2
	clear
	cr.sh
;;

"0" )
	echo "Gracias por usar este script"
	exit 0
;;

* )
	clear 
	echo ""
	echo ""
	echo ""
	echo ""
	echo "Entrada incorrecta, vuelva a intentar"
	echo "Ingresó '$valor' las posibles opciones son:"
	echo "p / n / a / 0"
	sleep 2
	cr.sh
;;

esac
```

---

