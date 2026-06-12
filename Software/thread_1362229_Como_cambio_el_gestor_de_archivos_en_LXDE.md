---
title: "Como cambio el gestor de archivos en LXDE?"
date: 2009-12-22
forum: Software
---

### Post by Kai-Eiji on 2009-12-22
Buenas a todos,
Miren, mi problemas es el siguiente, yo estoy usando el LXDE con Ubuntu 09.10 y quería cambiar el gestor de archivos que viene por defecto, el PCman FileManager por el nautilus, que aunque el PCman sea más rápido, me gusta más el otro, pero no se como hacerlo. Uso Nautilus 2.28.1 y el PCMan File Manager 0.5.1. 
Busqué en google, pero sólo aparece cómo hacer el proceso inverso...
Gracias y espero que me puedan ayudar. 

Ahh y perdón si hice el thread en un lugar equivocado, pero no encontraba donde. Si lo cree mal, perdonen y me dicen para la próxima donde crearlo ^^ Gracias

---

### Post by gmunioz on 2009-12-23
Hola kai....:

a- Navega hasta /usr/share/applications/
Verifica si existe el archivo nautilus-folder-hanlder.desktop
Si existe ve que su contenido sea este:

```
[Desktop Entry]
Encoding=UTF-8
Name=Open Folder
TryExec=nautilus
Exec=nautilus --no-desktop %U
NoDisplay=true
Terminal=false
Icon=folder-open
StartupNotify=true
Type=Application
MimeType=x-directory/gnome-default-handler;x-directory/normal;inode/directory;ap
plication/x-gnome-saved-search;
OnlyShowIn=GNOME;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.28.1
X-Ubuntu-Gettext-Domain=nautilus

```
Si no existe créalo.

b- En ese mismo directorio  /usr/share/applications/
Examina el archivo defaults.list 
Verifica que existan estas dos líneas, si no existen
o no coinciden las agregas o modificas:

```
inode/directory=nautilus-folder-handler.desktop
x-directory/normal=nautilus-folder-handler.desktop
```

Un procedimiento rápido de verificación es ejecutar

```
cat /usr/share/applications/defaults.list | grep x-directory
cat /usr/share/applications/defaults.list | grep inode
 
```

c- Una vez cambiadas en estas dos líneas 
pcmanfm-folder-handler.desktop por nautilus-folder-handler.desktop
al reiniciar el sistema nautilus tendría que ser el administrador
de archivos por defecto

---

### Post by Kai-Eiji on 2009-12-25
Hola gmunioz ^^
Desde ya gracias por la respuesta, pero me estuve fijando y en todo lo que me dijiste, lo tengo igual :S
No tuve que cambiar nada... no se que onda. Por supuesto, el pcmanfm sigue estando como predeterminado. La verdad ni idea...

Yo de estas cosas no tengo idea, pero tendrá algo que ver el 
"OnlyShowIn=GNOME;" ?

Sólo por tirar algo

---

### Post by Kai-Eiji on 2010-03-09
Bueno, verdaderamente no pude solucionar ESTE problema, pero buscando en el foro encontré una solución mucho mas fácil: resolvieron el bug del pcman que me molestaba y ahora lo actualicé. El bug te impedía ejecutar cualquier tipo de archivo automáticamente desde pcman. Había que seleccionar siempre la aplicación con qué abrirlo manualmente. [Post Original](http://ubuntuforums.org/showthread.php?t=1396222&highlight=Lxde)

No se si dejarlo abierto por si a otro le viene la duda o no. El problema en sí no lo pude resolver, pero lo hice por otro método. Lo dejo a criterio de los mods. Disculpen las molestias. Gracias

---

### Post by juancarlospaco on 2010-03-10
Yo instale el de Lucid, que es una version superior en Karmic, 
va de una, ok con las dependencias.

---

### Post by geronime on 2011-10-01
A mí me paso lo mismo y acabé "solucionándolo" mediante un apaño. El gestor que abría las carpetas de lugares era el xfe, así que lo desinstalé y creé un link llamado xfe que apuntaba al nautilus. Lo digo por si alguien anda buscando (si no se puede desinstalar que gestor de archivos que usa porque forma parte de un paquete mayor que no quieres desinstalar, borra (o cambia el nombre de) el ejecutable). Se que no es una solución, pero no falla.

ln -s /usr/bin/xfe /usr/bin/nautilus

---

