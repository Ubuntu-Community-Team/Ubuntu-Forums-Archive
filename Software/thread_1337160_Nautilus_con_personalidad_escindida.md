---
title: "Nautilus con personalidad escindida"
date: 2009-11-25
forum: Software
---

### Post by aledruetta on 2009-11-25
La pucha con Karmic!!!

Ahora resulta que si voy al menú lugares y hago click en cualquier lugar, en lugar (perdón por tanto "lugar") de abrir Nautilus abre EasyTag. ¿Qué tendrá que ver Julio Verne con Shakira?

Cuando ejecuto Nautilus por terminal (sin sudo), aparece lo siguiente:
```
karmic@karmic-laptop:~$ nautilus

(nautilus:3337): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

```

Con sudo:
```
karmic@karmic-laptop:~$ sudo nautilus

(nautilus:3368): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

** (nautilus:3368): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:3368): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:3368): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: La «red compartida» devolvió el error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No existe el fichero ó directorio
Please ask your system administrator to enable user sharing.

```

En los dos casos anteriores, abre Nautilus, no EasyTag.

¿Alguna idea?

---

### Post by enzomatrix on 2009-11-25
Da toda la impresión que es un problema de asocación. Parece que EasyTag quedó como programa por defecto.

Para empezar podemos probar abriendo gconf-editor
Ahí hay que ir a desktop/gnome/applications/component_viewer y en la clave "exec" el valor tiene que ser "nautilus %s" sin las comillas.

---

### Post by aledruetta on 2009-11-26
> **enzomatrix said:**
> Da toda la impresión que es un problema de asocación. Parece que EasyTag quedó como programa por defecto.

Para empezar podemos probar abriendo gconf-editor
Ahí hay que ir a desktop/gnome/applications/component_viewer y en la clave "exec" el valor tiene que ser "nautilus %s" sin las comillas.

Sí, Enzo, el valor es "nautilus %s"

¿Se te ocurre otra cosa?

---

