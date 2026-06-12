---
title: "Botones minimizar, maximizar"
date: 2010-08-06
forum: Software
---

### Post by Cholon on 2010-08-06
como cambio el boton minimizar a maximizar y viceversa ?  tengo ubuntu 10.04

---

### Post by bichopro on 2010-08-07
Aplicaciones>accesorios>terminal

Te va a pedir la contraseña...

> $ gconftool-2 --type string --set /apps/metacity/general/button_layout "menu:maximize,minimize,close"

Volver a dejar como estaba (por defecto):

> $ gconftool-2 --type string --set /apps/metacity/general/button_layout "maximize,minimize,close:menu"

---

### Post by Cholon on 2010-08-10
lo escribo en la terminal y no pasa nada, no me pide contraseña tampoco ¿:(?

---

### Post by Patriciologico on 2010-08-10
Esto debes ingresar

```
gconftool-2 --type string --set /apps/metacity/general/button_layout "menu:maximize,minimize,close"
```

Tal vez copiaste el primer simbolo "$" que indica que estas en modo de usuario sin privilegios de administrador. No te pedirá contraseña, no es necesario pues es un cambio que afecta solo a tu usuario.

---

### Post by Cholon on 2010-08-21
no, lo habia escrito ya sin el  "$" y no pasa nada de nada

---

### Post by themasterdark on 2010-08-22
Mas facil aún escribe en un terminal 

gconf-editor

dentro de este ve a:

apps->metacity->general

y busca button_layout

ahí lo editas y le das el orden que quieras ejemplo:

close,minimize,maximize:menu

luego simplemente sales 

Saludos =)

---

### Post by Cholon on 2010-09-02
ok muchas gracias, ahi si me funciono, gracias :)

---

