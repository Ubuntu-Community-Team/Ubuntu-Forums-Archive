---
title: "computadora como despertador"
date: 2011-03-02
forum: Software
---

### Post by marianocossio on 2011-03-02
buenas! hace unos días se me ocurrió usar mi compu como despertador, pero sin dejarla prendida toda la noche...
esto es fácil de hacer en windows, programando una tarea y suspendiendo la maquina...

ahora, en ubuntu se me complico mas... pude hacer que la maquina salga sola del estado de "Suspender", con un script...
el tema es que cuando vuelve, me pide la contraseña, y la idea es que yo este dormido cuando eso pase...

mi pregunta es: como puedo hacer para hacer que un programa (por ejemplo de musica, o el firefox con alguna pagina de radios) empiece a correr automáticamente sin tener que poner la contraseña manualmente??

---

### Post by maxibanez77 on 2011-03-02
Hola ante todo, Si no me equivoco Ubuntu tiene la facilidad de ser configurado para que al volver de la suspension o de la actividad del salvapantallas pida o no la contraseña, asi que solo se trataria de configurar correctamente el sistema. de todas maneras no te quedes solo con mi humilde opinion pues todos podemos equivocarnos no?

Por lo otro, tendrias que buscar y seguramente existe un programador de tareas y listo

Suerte y saludos. [SIZE=2][COLOR=Red]_**[COLOR=Blue]si funciona pasa el Script y/o la data[/COLOR].**_[/COLOR][/SIZE]:popcorn:

---

### Post by hectorivand on 2011-03-02
Hola, podes usar Alarm Clock

```
sudo apt-get install alarm-clock-applet
```

Saludos
Nacho

---

### Post by marianocossio on 2011-03-02
> **maxibanez77 said:**
> Hola ante todo, Si no me equivoco Ubuntu tiene la facilidad de ser configurado para que al volver de la suspension o de la actividad del salvapantallas pida o no la contraseña, asi que solo se trataria de configurar correctamente el sistema. de todas maneras no te quedes solo con mi humilde opinion pues todos podemos equivocarnos no?

Por lo otro, tendrias que buscar y seguramente existe un programador de tareas y listo

Suerte y saludos. [SIZE=2][COLOR=Red]_**[COLOR=Blue]si funciona pasa el Script y/o la data[/COLOR].**_[/COLOR][/SIZE]:popcorn:
si, probé con eso, pero no tuve resultados... logre que no me pida la contraseña ni bien prendo la compu, o cuando vuelve del salvapantallas... pero me la sigue pidiendo cuando vuelve de la suspensión :S

mira, acá va el script... a lo sumo tendrás el wakealarm en otra carpeta, pero es poco probable, debería funcionar...
lo guardas en /bin como archivo.sh, y después le das permiso de ejecución poniendo en una terminal chmod -x archivo.sh (primero te posicionas en la carpeta /bin desde la terminal)


#!/bin/bash

echo ""
echo "Ingrese hora y fecha para prender automaticamente su computadora"
echo ""

bandera= true 

while $bandera ;do

#se ingresa el año
echo "Ingrese año: "
read ANIO

#se ingresa la hora
echo "Ingrese Hora:"
read HORA

#estructura de control para la hora
while [ $HORA -ge 24 ];do
echo ""
echo "HORA INCORRECTA!"
echo "Formato Hora: HH"
echo "Ingrese Hora:"
read HORA
done

#se ingresan minutos
echo ""
echo "Ingrese Minutos:"
read MINUTOS

#estructura de control para los minutos
while [ $MINUTOS -ge 60 ];do
echo ""
echo "MINNUTOS INCORRECTOS!"
echo "Formato Minutos: MM"
echo "Ingrese Minutos:"
read MINUTOS
done

#se ingresa mes
echo ""
echo "Ingrese Mes:"
read MES

#estructura de control para el mes
while [ $MES -gt 12 ];do
echo ""
echo "MES INCORRECTO!"
echo "Formato Mes: MM"
echo "Ingrese Mes:"
read MES
done

#se ingresa dia
echo ""
echo "Ingrese Dia:"
read DIA

#primera estructura de control para el dia
while [ $DIA -gt 31 ];do
echo ""
echo "DIA INCORRECTO!"
echo "Formato Dia: DD"
echo "Ingrese Dia:"
read DIA
done

#segundda estructura de control para el dia (de compatibilidad entre dia y mes)
control=true
while $control ;do

if [ $MES -eq "1" ] && [ $DIA -le "31" ];then
 mes="Enero"
 break
fi

if [ $MES -eq "2" ] && [ $DIA -le "29" ];then
 mes="Febrero"
 break
fi

if [ $MES -eq "3" ] && [ $DIA -le "31" ];then
 mes="Marzo"
 break
fi

if [ $MES -eq "4" ] && [ $DIA -le "30" ];then
 mes="Abril"
 break
fi

if [ $MES -eq "5" ] && [ $DIA -le "31" ];then
 mes="Mayo"
 break
fi

if [ $MES -eq "6" ] && [ $DIA -le "30" ];then
 mes="Junio"
 break
fi

if [ $MES -eq "7" ] && [ $DIA -le "31" ];then
 mes="Julio"
 break
fi

if [ $MES -eq "8" ] && [ $DIA -le "31" ];then
 mes="Agosto"
 break
fi

if [ $MES -eq "9" ] && [ $DIA -le "30" ];then
 mes="Septiembre"
 break
fi

if [ $MES -eq "10" ] && [ $DIA -le "31" ];then
 mes="Octubre"
 break
fi

if [ $MES -eq "11" ] && [ $DIA -le "30" ];then
 mes="Noviembre"
 break
fi

if [ $MES -eq "12" ] && [ $DIA -le "31" ];then
 mes="Diciembre"
 break
fi

echo "FECHA INCORRECTA! Verifique la fecha."

done

#estructura de control final
echo ""
echo "Su computadora se encendera automaticamente el dia $DIA de $mes de $ANIO a las $HORA:$MINUTOS:00"
echo ""
echo "¿Esta conforme? s/n"
read opcion


if [ $opcion = "s" ] || [ $opcion = "S" ];then
# bandera= false
 break
fi


echo "Por favor reingrese los datos."
echo ""

done


DESPERTADOR=`date -u --date "$ANIO-$MES-$DIA $HORA:$MINUTOS:00" +%s`

sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"
sudo sh -c "echo $DESPERTADOR > /sys/class/rtc/rtc0/wakealarm"



es bastante simple en realidad... lo raro son las ultimas 3 lineas, lo otro es todo estructuras de control... lo complicado por ahi es que tenes q aprender a programar en bash para hacerlo, pero si tenes una base en otro lenguaje, es re simple

para usarlo pones un una terminal 'archivo.sh' y listo... no hace falta q te posiciones en ningún directorio en particular (para eso es que lo guardas en /bin)

contame si te anduvo!

---

### Post by marianocossio on 2011-03-02
> **hectorivand said:**
> Hola, podes usar Alarm Clock

```
sudo apt-get install alarm-clock-applet
```Saludos
Nacho


ahi anduvo! buenisimo, gracias por el aporte!

---

### Post by z37a on 2011-03-02
También podes apagar la PC y que a determinada hora se prenda! Eso se hace desde la BIOS, en una época con una PC vieja un tanto mas lenta, la había configurado en la BIOS para que 10 minutos después de despertarme se encienda, así me daba tiempo de preparar el desayuno, sentarme y ponerme a leer las noticias y demás! je

---

### Post by marianocossio on 2011-03-02
> **z37a said:**
> También podes apagar la PC y que a determinada hora se prenda! Eso se hace desde la BIOS, en una época con una PC vieja un tanto mas lenta, la había configurado en la BIOS para que 10 minutos después de despertarme se encienda, así me daba tiempo de preparar el desayuno, sentarme y ponerme a leer las noticias y demás! je



si, sabia de eso... pero no estoy seguro de como se hace, y la verdad no me animo mucho a meterle mano a la BIOS... si tenes bien idea de como hacerlo, estaría bueno que lo compartas, como para tenerlo en cuenta!

gracias...

---

### Post by z37a on 2011-03-03
> **marianocossio said:**
> si, sabia de eso... pero no estoy seguro de como se hace, y la verdad no me animo mucho a meterle mano a la BIOS... si tenes bien idea de como hacerlo, estaría bueno que lo compartas, como para tenerlo en cuenta!

gracias...

Cada BIOS tiene su manera, pero lo que te voy a comentar es lo mas importante, toqueteala mal, si la arruinas (estaba por escribir otra palabra pero el CoD me lo prohíbe! jajajaj) existe una opción que es "load default values" y te va a encender de una la maquina! Igualmente la función creo que era RTC o algo así, esta justo donde esta siempre la opción de WoL o Wake on LAN, o power on PCI event. Es muy util por si no queres dejarla toda la noche prendida, lo que si fijala para 10 minutos antes del despertador por que si justo corre un fsck te va a tardar 3 o 4 minutos mas encender la pc!

---

### Post by marianocossio on 2011-03-04
> **z37a said:**
> Cada BIOS tiene su manera, pero lo que te voy a comentar es lo mas importante, toqueteala mal, si la arruinas (estaba por escribir otra palabra pero el CoD me lo prohíbe! jajajaj) existe una opción que es "load default values" y te va a encender de una la maquina! Igualmente la función creo que era RTC o algo así, esta justo donde esta siempre la opción de WoL o Wake on LAN, o power on PCI event. Es muy util por si no queres dejarla toda la noche prendida, lo que si fijala para 10 minutos antes del despertador por que si justo corre un fsck te va a tardar 3 o 4 minutos mas encender la pc!


ok gracias! lo probare y después te cuento...

---

