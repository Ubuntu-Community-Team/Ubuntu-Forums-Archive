---
title: "Como ver el inicio en modo texto ?"
date: 2010-04-30
forum: Software
---

### Post by majatu on 2010-04-30
como hacer para que el sistema bootee en modo texto hasta llegar a la ventana de selecion de usuario?

Un saludo y muchas gracias!

---

### Post by guillermolisi on 2010-04-30
> **majatu said:**
> como hacer para que el sistema bootee en modo texto hasta llegar a la ventana de selecion de usuario?

Un saludo y muchas gracias!
Queres ver el avance del inicio en pantalla hasta llegar al Login ?
Si es asi hay que modificar en el Grub la linea que carga el boot para el kernel en uso y remover el string "quiet". Ejemplo:

```
kernel          /boot/vmlinuz-2.6.31-20-generic root=UUID=72c5d05e-b996-4634-9
cd3-130716ed6404 ro pci=nomsi,noaer quiet splash
```Ahora habria que verificar si estas usando Grub 1 o Grub 2 ya que en funcion de esto cambia como hacer la modificacion en forma permanente.

Suponiendo que estas usando Grub 2, una forma es habilitar para que te muestre el menu de Grub, seleccionas la entrada desde a cual queres inciar la maquina y presionas la tecla "e" para entrar al editor. Te moves con las flechas de direccion hasta que llegas al string a remover, lo borras, luego "Enter" e inicias el sistema.

Con el sistema funcionando abris una consola/terminal e ingresas ```
update grub
```con esto deberias hacer permanente el cambio para esa opcion de inicio del Grub.

---

### Post by juancarlospaco on 2010-04-30
No.

El parametro "quiet" cambia entre el modo normal y el modo Debug,
pero si no se remueve el parametro "splash", 
ambos modos son tapados graficamente por xsplash.

Igualmente esto no es necesario, con apretar ALT + F1 cuando inicia la pantalla de carga grafica, 
la misma termina, dejando la carga de texto.

Si se usa Grub2 se debe apretar SHIFT para que se muestre el menu de Grub2,
Si se usa Grub se debe apretar ESC para que se muestre el menu de Grub.

Usarlo en modo Debug siempre ralentiza el booteo.

---

### Post by guillermolisi on 2010-04-30
Gracias por la muy buena aclaracion, Juan Carlos.

---

