---
title: "Ayuda para instalar conky new playing"
date: 2009-12-10
forum: Software
---

### Post by leonardomdq on 2009-12-10
Hola a todos, necesito si me pueden dar una mano para instalar conky new playing en Karmic, trate de hacerlo andar pero no hubo caso.
Es este: [http://izobalax.deviantart.com/art/DSTRY-Conky-Config-138317160](http://izobalax.deviantart.com/art/DSTRY-Conky-Config-138317160)

este es el archivo de ayuda:
> 
STEP 1: copy the "monitor" and "NowPlaying" files into your home directory and rename them to something like ".conkyrc1" and ".conkyrc2"

STEP 2: Edit .conkyrc1 (your monitor conky setup), scroll to the bottom of the file, you'll see an image directory. Be sure to point this to where you've saved my conky image "mail-and-other.png". This conky also uses the 'cure' font, part of the artwiz fonts package; make sure you have them installed or use a different font (if you use a different font, you'll need to edit the x and y offsets so it all fits nicely).

STEP 3: Edit .conkyrc2 (your NowPlaying conky setup), scroll to the bottom of the file, you'll see an image directory. Be sure to point this to where you've saved my conky image "music.png". This conky also uses the 'cure' font, part of the artwiz fonts package; make sure you have them installed or use a different font (if you use a different font, you'll need to edit the x and y offsets so it all fits nicely).

NOTE1: the monitor conky setup uses a gmail python script (included). Place this script in "/home/<your username>/.scripts/" and be sure to edit it as required. 

NOTE2: the NowPlaying conky setup is designed to work with Banshee (script included). Place this script in "/home/<your username>/.scripts/".

STEP 4: ensure that, if you use Compiz, it doesn't draw shadows around conky. Go to CompizConfig Settings Manager>Window Decorations and in the "Shadow Windows" field change the line to "(any) & !(class=Conky)", obviously minus the speech marks. 

STEP 4a: See this thread her: [http://ubuntuforums.org/showthread.php?p=8009406](http://ubuntuforums.org/showthread.php?p=8009406) to install the conkybanshee scripting for your OS.

STEP 5: Everything should all be set. You can execute your monitor conky now, just Alt+F2 then enter "conky -c .conkyrc1" then the NowPlaying with "conky -c .conkyrc2". If you want to boot these automatically on startup, you can add them into Startup Applications; create new entries with commands used above. 

STEP 6: ?????

STEP 7: PROFIT!

README courtesy of Izobalax 2009 [http://izobalax.deviantart.com](http://izobalax.deviantart.com)



Les agradesco si me pueden guiar.
Saludos y gracias de antemano.

---

### Post by matias_tati on 2009-12-10
Pero como no
Primero tenes que tener instalado conky 1.7.2 que soporta imagenes.
Buscalo en Synaptic el paquete se llama conky-all
Intentalo de nuevo ahora.

O no tenes ni idea?ja ja ja ja ja.
Contame...

---

### Post by leonardomdq on 2009-12-10
> **matias_tati said:**
> Pero como no
Primero tenes que tener instalado conky 1.7.2 que soporta imagenes.
Buscalo en Synaptic el paquete se llama conky-all
Intentalo de nuevo ahora.

O no tenes ni idea?ja ja ja ja ja.
Contame...
:D No tengo idea para que te voy a mentir jaja

Ahora si instale conky 1.7.2

Sigo segun la ayuda que trae, cualquier duda consulto...gracias

---

### Post by leonardomdq on 2009-12-10
El new Playing esta funcionando, el user panel no pude hacer andarlo todavia...que podra ser?

---

### Post by matias_tati on 2009-12-10
```
conky -c .conkyrc2
```

---

### Post by leonardomdq on 2009-12-10
> **matias_tati said:**
> ```
conky -c .conkyrc2
```

Habia seguido los pasos bien, lo que me falto lo mas importante era istalar conky 1.7.2 :p ese era el problema, una ves instalado salio andando.

Ahora me queda una sola cosa, cuando reinicio la pc no lo carga, lo agregue a aplicaciones de inicio y tampoco, que podra ser?

Slds

---

### Post by matias_tati on 2009-12-10
Mostrame exactamente que agregaste en aplicaciones al inicio.
Y decime: Usas Compiz o Composite?

---

### Post by leonardomdq on 2009-12-10
la ruta para el userpanel que le agregue en aplicaciones de inicio es:
```
/home/leonardo/.conkyrc1
```

No uso ni Compiz ni Composite

---

### Post by matias_tati on 2009-12-10
Podes poner dos aplicaciones al inicio con estos comandos:

```
conky -c .conkyrc1
```

Y otro


```
conky -c .conkyrc2
```

Esto lo pones donde dice orden en nombre y comentario lo que vos quieras

Acordate añadi dos aplicaciones al inicio y en cada una pones eso en "orden" una en cada una.

Asumo que los archivos en tu home se llaman .conkyrc1 y .conkyrc2

---

### Post by leonardomdq on 2009-12-11
Solucionado, muchas gracias.;)

SOLVED

---

### Post by matias_tati on 2009-12-11
> **leonardomdq said:**
> asi los tengo pero no inicia automaticamente, si lo hace si lo ejecuto manualmente con Alt+F2

Y la ruta que me mostraste antes donde la pusiste? No entiendo.

---

### Post by leonardomdq on 2009-12-11
la ruta esa la cambie por lo que me pasaste pero no arranco automaticamente cuando inicia ubuntu, si arranca si lo ejecuto manualmente...nose que sera

---

### Post by matias_tati on 2009-12-13
Y con un script?
Yo lo tengo asi...

---

