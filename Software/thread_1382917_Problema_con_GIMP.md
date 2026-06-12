---
title: "Problema con GIMP"
date: 2010-01-16
forum: Software
---

### Post by magicdrums on 2010-01-16
Hola,
hace mucho que no escribo en el foro, bueno mi problema es que imp no incia esto ocurrio despues de desinstalarlo y volver a instalarlo, la version que estoy utilizando es ubuntu 9.10, al ejecutar imp desde la consola aparece esto

```
(gimp:4576): GLib-GObject-WARNING **: specified class size for type `GimpOperationPointFilter' is smaller than the parent type's `GeglOperationPointFilter' class size

(gimp:4576): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gimp:4576): GLib-GObject-CRITICAL **: g_type_register_static: assertion `parent_type > 0' failed

(gimp:4576): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gimp:4576): GLib-GObject-WARNING **: cannot retrieve class for invalid (unclassed) type `<invalid>'
```

 si aluien pudiera ayudarme a solucionarlo. :(

---

### Post by moreback on 2010-01-16
¿Probaste a borrar el directorio **~/.gimp-2.6**? Puede ser un problema con alguna configuración personal.

Saludos.

---

