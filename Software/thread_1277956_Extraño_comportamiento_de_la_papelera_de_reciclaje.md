---
title: "Extraño comportamiento de la papelera de reciclaje"
date: 2009-09-28
forum: Software
---

### Post by nahuel_89p on 2009-09-28
Buenas foro, les paso a contar:
Si borro algo, y va a parar a la papelera de reciclaje, y luego intento abrir la papelera de reciclaje, la ventana no abre y desaparecen todos los iconos del escritorio.
Bueno, recien lo intento enviando un txt, y bastó con el solo hecho de enviarlo para que desaparezcan los iconos... muy raro, si...
La situacion vuelve a la normalidad cuando, graciosamente, hago muchos clicks seguidos rapidos (si, a lo bobo, y los bordes de la pantalla parpadean, como que la ventana "intenta" aparecer) en el icono de la papelera... llega un momento que se abren varias ventanas de la papelera, y los iconos del escritorio reaparecen. Ah, y solamente funciona si vacío a la papelera con boton derecho-->vaciar papelera. (en el icono inferior derecho d la papelera), porque si la papelera tiene algo, no hay forma de que funcione.
Ah, y el nautilus funciona para explorar otras ubicaciones cuando los iconos desaparecen y la papelera no abre.

Gracias por cualquier sugerencia

---

### Post by pablo.s on 2009-09-29
Contanos que versión de
Ubuntu estás usando y
qué versión de Nautilus.

---

### Post by nahuel_89p on 2009-09-29
> **pablo.s said:**
> Contanos que versión de
Ubuntu estás usando y
qué versión de Nautilus.

9.04
nautilus 2.26.2

Tampoco tiene nada que ver si el compiz esta o no activado

Para resumir, solamente puedo abrir la papelera si está vacía.

Saludos

---

### Post by juancarlospaco on 2009-09-29
*Se esta muriendo el Nautilus...*
Tenes todos los Updates?

---

### Post by pablo.s on 2009-09-29
> **nahuel_89p said:**
> Ah, y solamente funciona si vacío a la papelera con boton derecho-->vaciar papelera. (en el icono inferior derecho d la papelera), porque si la papelera tiene algo, no hay forma de que funcione.
Ah, y el nautilus funciona para explorar otras ubicaciones cuando los iconos desaparecen y la papelera no abre.

Ahí veo (perdón por no haber
leído el mensaje en profundidad
antes) que lo que te puede estar
dando errores no es Nautilus sino
el paquete gnome-applets, que es
el que coloca la papelera abajo a 
la derecha. Fijate si hace el mismo
comportamiento al desinstalar el
paquete y usás la papelera pero
directamente desde Nautilus.
PD: Si te pide desinstalar también 
al paquete ubuntu-desktop no tengas
miedo, porque es un metapaquete.

---

### Post by nahuel_89p on 2009-09-29
> **pablo.s said:**
> Ahí veo (perdón por no haber
leído el mensaje en profundidad
antes) que lo que te puede estar
dando errores no es Nautilus sino
el paquete gnome-applets, que es
el que coloca la papelera abajo a 
la derecha. Fijate si hace el mismo
comportamiento al desinstalar el
paquete y usás la papelera pero
directamente desde Nautilus.
PD: Si te pide desinstalar también 
al paquete ubuntu-desktop no tengas
miedo, porque es un metapaquete.

Me da cosa desinstalar. no querras decir reinstalar?. De todos modos el problema no es del icono de la papelera. Si entro a la papelera desde el nautilus, se cierra la ventana y desaparecen los iconos. Es lo mismo. El problema está en la papelera.

---

### Post by pablo.s on 2009-09-29
Ahá. Y tenés alguna 
actualización de Nautilus
o gnome-applets esperando
ser instalada? ¿Que formato
tiene tu /home?

---

### Post by juancarlospaco on 2009-09-29
Fijate si tenes Updates, si tenes Scripts agregados al Nautilus, 
Limpia la papelera desde la Terminal con sudo, 
*se pone caprichoso el cefalópodo ese a veces...*

---

### Post by nahuel_89p on 2009-09-30
> **pablo.s said:**
> Ahá. Y tenés alguna 
actualización de Nautilus
o gnome-applets esperando
ser instalada? ¿Que formato
tiene tu /home?
No hay actualizaciones de nautilus ni gnome applets.
Y a q te referis con mi formato de /home?? En ese directorio está la carpeta de usuario con mi nombre nada mas.

> **juancarlospaco said:**
> Fijate si tenes Updates, si tenes Scripts agregados al Nautilus, 
Limpia la papelera desde la Terminal con sudo, 
*se pone caprichoso el cefalópodo ese a veces...*


Miren lo que me acaba de pasar. Por aca va el problema creo:
Si hago sudo nautilus se abre una ventana de nautilus con permisos root, pero en la consola me tiran un par de errores

[HTML]"Nautilus-Share-Message: Called "net usershare info" but it failed: La «red compartida» devolvió el error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No existe el fichero ó directorio
Please ask your system administrator to enable user sharing.


** (nautilus:5211): WARNING **: Unable to add monitor: Operación no soportada"[/HTML]

Y si con esa ventana de nautilus, intento entrar a la papelera, salta un mensaje q dice:

[HTML]No se pudo mostrar todo el contenido de «trash»: Operación no soportada[/HTML]

---

### Post by aledruetta on 2009-09-30
Probablemente no tenga nada que ver, pero yo tuve muchos problemas con la papelera cuando instalé Jaunty usando el formato ext4. Tuve que volver al ext3 para tener un sistema estable. Claro que los síntomas no eran los mismos, a mí se me tildaba el sistema y solo podía salir reiniciando a lo bruto.

---

### Post by nahuel_89p on 2009-09-30
Si entro a /home/nahuel/.local/share/Trash/files puedo ver los archivos que borro, por lo tanto me quedo tranquilo xq se que si borré algo que no debia borrar, lo puedo recuperar. Y si quiero borrar, hago boton derecho en el icono para vaciar la papelera (no puedo borrar desde /home/nahuel/.local/share/Trash/files porque de esa manera no hago más que mandar a la papelera lo que ya estaba en la papelera). Osea, la funcionalidad está... pero tambien la anomalía...

Voy a seguir investigando... pero mientras tanto no encuentro solución. Alguna otra sugerencia?

---

### Post by TatonCba on 2009-10-08
Nahuel, soy nuevo en el foro, entre por el mismo problema, lo soulcioné por un tiempo borrando recursivamente desde la consola el contenido de las carpetas /home/*/.local/share/Trash/ y /root/.local/share/Trash/, es decir las papeleras de todos los usuarios del sistema. Lamentablemente el problema volvió a surgir despues de un tiempo y me di cuenta de que no solo es con la papelera, al ir a lugares<equipo sucede lo mismo, fondo de pantalla negro y no se abre nautilus... alguna novedad???

---

### Post by mama21mama on 2010-02-01
](*,) me pasa lo mismo.
Al intentar borrar o abrir desde el panel inferior (icono de papelera) se me borran los iconos del escritorio.

La idea es recuperar la funcion original.
Saludos

PD: Aqui dejo el [bug reportado]("https://bugs.launchpad.net/awn-extras/+bug/327970")

---

### Post by santiago79 on 2010-02-02
probaste con forzar a vaciar la papelera desde terminal?
```
cd .Trash
sudo rm -rf *
```
y la de root

```
sudo rm -fR /root/.Trash
```y si tenes varias particiones en el disco por ejemplo el home en una partición distinta que el sistema cada uno tiene su papelera

---

### Post by guillermolisi on 2010-02-02
> **santiago79 said:**
> probaste con forzar a vaciar la papelera desde terminal?

y la de root

y si tenes varias particiones en el disco por ejemplo el home en una partición distinta que el sistema cada uno tiene su papelera
Importante: NO olvidar el primer paso !
```
cd .Trash
```

---

### Post by mama21mama on 2010-02-02
No me funca.
Luego de borrar sigue el mismo comportamiento.
Luego que desaparecen los iconos si acciono...

> gksudo nautilus
Veo en el escritorio los iconos de root, wallpaper, (theme). :s

La única que puedo hacer es reiniciar sesión.

---

### Post by santiago79 on 2010-02-03
proba con los 2 que te dije antes y tambien con este
> sudo rm -rf ~/.local/share/Trash/files/*

---

