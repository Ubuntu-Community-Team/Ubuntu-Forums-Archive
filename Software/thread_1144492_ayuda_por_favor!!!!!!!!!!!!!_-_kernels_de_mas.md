---
title: "ayuda por favor!!!!!!!!!!!!! - kernels de mas"
date: 2009-04-30
forum: Software
---

### Post by ambystoma_19 on 2009-04-30
hola linuxeros:

antes de empezar les cuento que me cambie a ubuntu hace dos meses y quede maravillado es realmente increible.
bueno mi consulta es por una estupidez que hice, antes que nada mi maquina es una PIV, 2 gb de ram y disco de 80 gb, tengo ubuntu 8.04 y microsoft xp, bueno ayer no fijandome lo que hacia marque para instalar muchos kernels en synaptic (esa fue mi etupidez) ahora e el grub de inicio me marca el kernel 386 y server, inicio caulquiera de ellos y la pantalla de ve totalmente distorsionada (lo cual hace imnposible hacer cualquier operacion, al tener startupmanager, saque del grub las opciones de recovery mode, por suerte puedo acceder a la maquina de comandos con ctrl+alt+f1.
segun lo que pude reflexionar tengo que restablecer el kernel generic de ubuntu, entonces ese es el proposito de este mensaje, alguien de ustedes me podria guiar como hacer esto, o encontrar de solucion con los recursos que poseo (maquina de comandos)
si alguno de ustedes me podria brindar su ayuda estaria muy agradecido.

pd: actualmente estoy usando windows; por favor no lo soporto mas, necesito ayuda.

---

### Post by clasificado on 2009-04-30
Buenas buenas!

dos cositas:
1) el kernel que yo estoy usando ahora es el "linux-image-2.6.28-11-generic". podrías instalarlo desde la consola tipeando 
```
sudo apt-get install linux-image-2.6.28-11-generic
```

Despues de eso, al reiniciar, te tendria que aparecer en el grub la opción "Ubuntu 9.04, kernel 2.6.28-11-generic"

2) No hace falta insistir con el título :lolflag: los que entramos a este foro lo hacemos de puro gusto, y leemos casi todos los posts. Algunos, de hecho, les ha molestado (en otras ocasiones) que los anden picando con la vara para que los ayuden. Posta, no hace falta

probalo y contanos como te fue

clasificado

---

### Post by sherwoodinc on 2009-05-01
Te recomiendo instalarte el paquete virtual "linux-generic" que te va a instalar automáticamente el último kernel "generic" disponible. Además se te van a ir ninstalando los nuevos kernels actualizados a medida que salgan.
```
sudo apt-get install linux-generic
```
Una vez que lo hayas instalado, reiniciá la máquina y usá ese kernel y después podés desinstalar todos los paquetes  linux-...  que no sean de esa versión del kernel.
NOTA: No es recomendable desinstalar los paquetes del kernel con el que iniciaste la máquina.

Si en algún momento necesitás saber qué versión de kernel estás corriendo, una manera rápida es hacer en una Terminal
```
uname -a
```
lo que te va a devolver algo como
```
Linux swinc 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux
```
En mi ejemplo puede verse que estoy corriendo con la 2.5.27-9-generic.

Una joda del "linux-generic" es que con el correr del tiempo tu lista de kernels instalados se irá alargando a medida que vayan saliendo actualizaciones.

---

### Post by ambystoma_19 on 2009-05-01
hola gracias por sus respuestas. pero lamentablemente ninguna resolvio el problema

la preimera que era ecribir en la consola de comandos:

sudo apt-get install linux-image-2.6.28-11-generic
me decia que no era un paquete valido.
la otra respuesta quera de [sherwoodinc]("http://ubuntuforums.org/member.php?u=648586") 
sudo apt-get install linux-generic al hacerlo me dice que ya tengo el la ultima version del kernel instalado.

intente ponerlo como defecto, editando el menu.lst del grub, pero me dice que no se puede hacer de modo grafico.
lo que estaba pensando es borrar en grub con la consola de recuperacion del xp a traves del comando fixmbr, para despues recuperar el grub con el live cd, usando ubuntu sin instalarlo, accediendo asi a la consola de comandos.
ustedes que opinan?

---

### Post by Mauro22 on 2009-05-01
para editar archivos desde consola no podes usar programas que trabajen en X.


Para textos podes usar:

vi

nano

vim

y otros


Todos trabajan en consola.

---

### Post by ambystoma_19 on 2009-05-01
hola gracias por sus repuestas, pero lamentablemente ninguna dio resultado.

la primera era de clasificado, decia:

sudo apt-get install linux-image-2.6.28-11-generic
al intentarlo me devolvio que no era un paquete valido.

luego intente hacer lo que decia sherwoodinc :

sudo apt-get install linux-generic

me devolvio que ya tenia la ultima version del kernel instalado.
entonces intente editar el menu.lst del grub, pero la consola no me deja hecerlo de modo grafico.
lo que quiero intentar es iniciar ubuntu sin instalarlo con el live cd, para asi editar el menu.lst del grub y poner el kernel generic como defoult.
ustedes que opinan

---

### Post by josecuervo86 on 2009-05-01
Pero y si editas el menu.lst del grub, comentando los kernels nuevos y dejando sin comentar unicamente el kernel que te interesa a vos? Eso deberia funcionar. Por lo menos asi fue como resolvi un kernel panic, debido a una mala compilacion del kernel.

Edit: no lei que no podias editar el grub en modo gráfico.

---

### Post by ambystoma_19 on 2009-05-01
me enteresaria como hacer eso, me podrias guiar como.

---

### Post by josecuervo86 on 2009-05-01
> **ambystoma_19 said:**
> me enteresaria como hacer eso, me podrias guiar como.

Mira, abris el menu.lst del grub

```
sudo gedit /boot/grub/menu.lst
```

Te vas a donde figuran los kernels que instalaste y los comentas (le pones un "#" adelante, o simplemente los cortas (siempre haciendo un backup), dejando primero el kernel con el que queres que bootee

Edit: tambien podes cambiarlos de orden, dejando primero el que queres que bootee

Edit2: si no podes hacerlo con gedit, hacelo con nano:

```
sudo nano /boot/grub/menu.lst
```

---

### Post by ambystoma_19 on 2009-05-01
hola sigo sin resolver el problema, tome la desicon de reinstalar el sistema, antes voy a usar el live cd para hacer un backup.
graqcias a todos por la ayuda, si neesitan ayuda no duden en chiflar. gracias

---

