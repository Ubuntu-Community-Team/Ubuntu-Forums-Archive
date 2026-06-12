---
title: "Placa de sonido arranca con volumen bajo"
date: 2009-07-03
forum: Software
---

### Post by Einfachlacm on 2009-07-03
Hola,

En una pc con Xubuntu cada vez que la arranco el volumen aparece al minimo, por mas que cada vez que la apago ya lo he subido al maximo.

Como puedo hacer para que al encender este con el mismo volumen que la dejé antes de apagarla?

Gracias de antemano.

---

### Post by staar on 2009-07-03
podés hacer lo siguiente, en una Terminal corré ```
alsamixer
``` y seteá el volumen como desees, despues salí (con Alt + Q) y poné ```
sudo alsactl store
``` y después agregá a las aplicaciones de inicio una entrada con el comando ```
alsactl restore
``` es una solución algo rudimentaria, y medio fea, pero funciona :-D

saludos

---

### Post by santiagoward2000 on 2009-07-03
Otra solución rústica, pero un poco más simple, es usar aumix (que desde Xubuntu 9.04 viene preinstalado). Habría que agregar a los programas que se cargan al inicio:
```
aumix -v 100
```
Saludos!

---

### Post by aledruetta on 2009-07-03
> **santiagoward2000 said:**
> Otra solución rústica, pero un poco más simple, es usar aumix (que desde Xubuntu 9.04 viene preinstalado). Habría que agregar a los programas que se cargan al inicio:
```
aumix -v 100
```Saludos!

Y si quiero que suceda lo contrario, es decir, que inicie con un volumen bajo ¿hago así?

```
aumix -v 30
```

---

### Post by santiagoward2000 on 2009-07-03
> **aledruetta said:**
> Y si quiero que suceda lo contrario, es decir, que inicie con un volumen bajo ¿hago así?

```
aumix -v 30
```

Si, el número es el nivel de sonido de 0 a 100. **aumix -v** es para setear el valor del volumen principal. Se puede poner un número fijo (tipo 30 o 100) o se puede usar con un incremento o descenso (tipo +5 o -10, yo usé esto para hacer andar los botones de volumen de mi laptop). Hay más opciones para cambiar el volumen de otros controles.
Saludos!

---

### Post by aledruetta on 2009-07-04
Buenísimo, así no despierto a nadie cuando reinicio la portatil ¡Esto es Linux para seres humanos!!!

---

