---
title: "La papelera cambio de lugar en Hardy"
date: 2008-07-11
forum: Software
---

### Post by Hernán-Amaya on 2008-07-11
hola gente, no se si dieron cuenta pero en HH cambiaron la papelera de lugar
antes estaba en ~/.Trash y ahora la pusieron acá ~/.local/share/Trash/files

yo lo que hice fue hacer un enlace simbólico para no acordarme todo el path 

de la siguiente manera 
```

ln -s ~/.local/share/Trash/files ~/.Trash

```
no se si es lo mas correcto o es mejor hacer esto

```

rmdir ~/.Trash
ln -s ~/.local/share/Trash/files ~/.Trash

```

---

### Post by niko_3100 on 2008-07-11
Lo correcto seria acordarte el nuevo path, supongo que lo van a mantener asi por un par de nuevas salidas de ubuntu, cuando pones ~/ que significa? la home?

---

### Post by Hernán-Amaya on 2008-07-11
exactamente ~ es la home, también hay programas que vienen con la trash con el path viejo como awn

---

### Post by santiagoward2000 on 2008-08-21
Hola!
Revivo este thread porque tengo una duda sobre este tema. Cuando entro como root y borro algo, se mueve a la carpeta /root/.local/share/Trash/files
Pero el icono de la papelera figura como vacia, y si quiero entrar, en Nautilus me aparece este error: > The folder contents could not be displayed.
Sorry, couldn't display all the contents of "trash": Operation not supported
Como queria vaciar la papelera, probe con:
```
sudo rm -rf /root/.local/share/Trash/files/*
```
pero no me borro los archivos. ¿Alguien sabe como puedo hacer?
Saludos!

_EDIT:_
Bue, lo solucione de una forma medio rustica. Lo que hice fue mover como root todos los archivos estos a una carpeta en /home, le cambie los permisos, y despues, como yo (no root) borre esta carpeta.
Igual, si alguien conoce una forma mas simple y elegante que lo explique por favor.

---

