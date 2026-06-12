---
title: "sacar windows"
date: 2009-06-28
forum: Software
---

### Post by joseluis on 2009-06-28
amigos, he sustituído mi modo de trabajar en forma definitiva y ahora quiero sacar windows de mi notebook-
tengo dos opciones cre, 
1. formatear la partición ntfs de win y dejarla para datos, con el trabajo agregado de hacer copia de datos para no perderlos,
2. borrar win de esa particion para no estar haciendo copia de los datos, y listo

¿qué opción es la más recomendable?

Y otra pregunta: ¿cómo sacaría el selector de buteo en ambos casos?

gracias desde ya

---

### Post by grutta on 2009-06-28
Hola. No soy experto, te aclaro, pero funcionó perfecto. Yo hice lo siguiente:

1. Copia de datos.

2. Formato de la partición a ext3 (mejor que ntfs) con gparted. Sino está instalado gparted: 

```
sudo apt-get install gparted
```

3. Sacar windows del selector de buteo:

3.1 Abrir para editar el archivo menu.lst:

```
sudo gedit /boot/grub/menu.lst
```

3.2 Borrar las siguientes líneas de ese archivo. (O parecidas según el caso):

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

```


Espero te sirva...

---

### Post by juancarlospaco on 2009-06-28
Hola, solo vengo a recomendar **EXT4**

---

### Post by joseluis on 2009-06-28
ok...SE AGRADECEEEEEEEEEEEEE

---

### Post by joseluis on 2009-06-28
pero me queda un tema que plantee en otro post por el tema del formateo. Si pongo en ext4, puedo ver los archivos desde otras maquinas en red, pero no puedo modificarlos. Y eso para mi es importante. Si los pongo en ntfs puedo modificarlos. si alguien tiene la respuesta agradezco

---

### Post by Hei Ku on 2009-06-28
desde otras maquinas en red? No hay diferencia. Verifica los permisos con que estas compartiendo esos archivos, pero no tiene que ver con el formato de la particion.

---

### Post by ramiro_md on 2009-06-28
El tema con ext4 es que si vas a compartir con pc que tengan Wintendo, estas últimas no van a reconocer tu partición ext4 por más compartida que esté, solo aclaro eso...saludos

---

### Post by Hei Ku on 2009-06-28
> **ramiro_md said:**
> El tema con ext4 es que si vas a compartir con pc que tengan Wintendo, estas últimas no van a reconocer tu partición ext4 por más compartida que esté, solo aclaro eso...saludos

Esto no es así. El problema podrías tenerlo con un dual boot, pero a través de la red las maquinas windows no tienen problema.

---

### Post by juancarlospaco on 2009-06-29
> **ramiro_md said:**
> El tema con ext4 es que si vas a compartir con pc que tengan Wintendo, estas últimas no van a reconocer tu partición ext4 por más compartida que esté, solo aclaro eso...saludos

**[SIZE="3"]No.[/SIZE]**

---

### Post by joseluis on 2009-06-29
no se.
de hechohe podido ver los archivos, pero no pude modificar. y desde mc puse los permisos para que se pueda leer y escribir por cualquier usuario

---

### Post by joseluis on 2009-06-29
no se.
de hechohe podido ver los archivos, pero no pude modificar. y desde mc puse los permisos para que se pueda leer y escribir por cualquier usuario, pero no graba las modificaciones, solo abre los archivos

---

