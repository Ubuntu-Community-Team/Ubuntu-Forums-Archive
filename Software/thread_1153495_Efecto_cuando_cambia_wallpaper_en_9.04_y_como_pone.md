---
title: "Efecto cuando cambia wallpaper en 9.04 y como poner Amarok 1.4 en 9.04"
date: 2009-05-08
forum: Software
---

### Post by emiliano_raso on 2009-05-08
Hola gente de la comunidad. Primero que nada queria preguntar si alguien sabe como quitar ese efecto de difuminado que hace Ubuntu 9.04 cuando cambiamos de wallpaper. Realmente me morfa la placa de video y es una maquina medio pobre la mia.

Y en agradecimiento a sus respuestas (y para aportar algo) explico como poner Amarok 1.4 en Ubuntu 9.04 para quienes no les guste el Amarok 2 (ya que este es el que viene por defecto en las repos de la ultima version)

----- X -----

Abrimos el sources.list:
> sudo gedit /etc/apt/sources.list

Agregamos los siguientes repositorios:
> #Amarok1.4
deb [http://ppa.launchpad.net/bogdanb/ppa/ubuntu](http://ppa.launchpad.net/bogdanb/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/bogdanb/ppa/ubuntu](http://ppa.launchpad.net/bogdanb/ppa/ubuntu) jaunty main

Agregamos la clave:
> sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \
0x1d7e9dd033e89ba781e32a24b9f1c432ae74ae63

Actualizamos las sources e instalar Amarok 1.4:
> sudo apt-get update
> sudo apt-get install amarok14

Espero que les sirva. Suerte.
Y ayudenmé con mi duda que no encuentro la opcion para sacarlo y es muy molesto xD

---

### Post by juancarlospaco on 2009-05-09
En el Gconf-editor hay una opcion que dice *"Reduced Resources"* tildala y reinicia sesion.

---

### Post by emiliano_raso on 2009-05-09
En que parte? No lo encuentro -__-

---

### Post by Mauro22 on 2009-05-10
Esta en:


/apps/metacity/general/


Saludos!

---

### Post by emiliano_raso on 2009-05-10
Listo. Muchisimas gracias a ambos.

EDIT: Acabo de probar y no funcionó :-S

---

### Post by Mauro22 on 2009-05-10
Encontre esto aca [0]

```

Unfortunately the only way to disable the nautilus wallpaper fade effect is to disable all GTK+ animations.

Add 
Code:
gtk-enable-animations = 0
to ~/.gtkrc-2.0 (create if it doesn't exist). For all users it would be /etc/gtk-2.0/gtkrc IIRC.

And then logout or pkill nautilus.

```


En español:

```
Desafortunadamente la unica forma de desactivar el efecto fundido del wallpaper es deshabilitar todos las animaciones GTK+


Agregá:

gtk-enable-animations = 0

al archivo ~/.gtkrc-2.0 (crealo si no existe). Para todos los usuarios seria /etc/gtk-2.0/gtkrc IIRC.

Y luego salí de la sesion o mata nautilus.
```


Saludos!


[0] [http://ubuntuforums.org/showpost.php?p=6900489&postcount=16](http://ubuntuforums.org/showpost.php?p=6900489&postcount=16)

---

### Post by Mauro22 on 2009-07-03
Bump y revivo post para volverlo a matar.


Comprobado por **mi y por emiliano_raso**, detallo la solución al "fundido" **** que tiene JJ que junto (otra vez) a la Intel Graphics resulta en un dolor de hueso.

[solucion]---->

El otro dia solucioné lo del "fundido" del escritorio que empieza a andar todo lento por 15 segundos hasta que cambia...


Busque y busque porque me acordaba de haber leido algo aca.

Pasos:

1) sudo gedit /etc/X11/xorg.conf

2) dentro de la seccion "Device" agregar:

Option "MigrationHeuristic" "greedy"

3) Reinicia la pc y listo, se soluciona...



PD. Esto generalmente solo pasa con las Intel Graphics... si tenes otra placa que tiene el mismo problema, postealo!!

<----[/solucion]

Saludos!!


PD: El crédito no es mío. Solo busque un tiempo por internet y en un foro extranjero encontre un link a una pagina wiki con los 'ubuntu known issues' ... 

Si encuentro el link, lo pongo pero de la felicidad no lo anoté.
):P

---

