---
title: "Problemas con la papelera en Ubuntu"
date: 2010-01-10
forum: Software
---

### Post by zaladquiel on 2010-01-10
Tengo problemas con la papelera de reciclaje en mi Ubuntu, los archivos que llegan ahí no se eliminan cuando le doy a "vaciar papelera" y ya acumulan como 2 gigas de espacio. 
Cuando hago click en vaciar papelera simula como si eliminara los archivos, pero estos siguen estando ahí. Si intento eliminarlos uno a uno me dice "Error al eliminar el archivo: Permiso denegado".
¿Cómo puedo eliminar efectivamente estos archivos?

Mi Ubuntu es 8.04 y el escritorio es Gnome.

---

### Post by Carlos C on 2010-01-10
La papelera de tu usuario se encuentra en una carpeta oculta en tu home, su ruta es "~/.local/share/Trash/files". Puedes intentar borrar esos archivos escribiendo:
```
sudo rm -rf ~/.local/share/Trash/files/*
```
Cuidado con escribir ese comando, si te equivocas puedes terminar borrando algo que no quieres.

Otra opción es iniciar nautilus con permisos de administrador. En el terminal escribes:
```
sudo nautilus
```
Luego te diriges a esa misma carpeta (~/.local/share/Trash/files) y borras los archivos.

Saludos.

---

### Post by zaladquiel on 2010-01-10
> **Carlos C said:**
> La papelera de tu usuario se encuentra en una carpeta oculta en tu home, su ruta es "~/.local/share/Trash/files". Puedes intentar borrar esos archivos escribiendo:
```
sudo rm -rf ~/.local/share/Trash/files/*
```Cuidado con escribir ese comando, si te equivocas puedes terminar borrando algo que no quieres.

Otra opción es iniciar nautilus con permisos de administrador. En el terminal escribes:
```
sudo nautilus
```Luego te diriges a esa misma carpeta (~/.local/share/Trash/files) y borras los archivos.

Saludos.

Gracias, he podido vaciar la papelera, pero no se ha liberado espacio en el disco. ¿Cómo puedo verificar esto?

---

### Post by CdK1 on 2010-01-10
has un df -H antes de borrar algo, fíjate en tu partición /home/, luego borra algo y has nuevamente un df -H, ve si te libera espacio...

---

