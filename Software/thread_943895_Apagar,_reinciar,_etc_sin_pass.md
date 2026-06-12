---
title: "Apagar, reinciar, etc sin pass"
date: 2008-10-10
forum: Software
---

### Post by Mauro22 on 2008-10-10
Buenas!!


Necesito que prueben algo que encontré y me llamó la atencion.


A traves de la consola hay un .sh que permite apagar, suspender, reiniciar o hibernar la pc sin ser sudo (en Gnome).


Al menos ahi no me lo pide, y era lo que me faltaba para incluir en los scripts sin tocar el sudoers.

En la terminal pongan: 

```
gnome-power-cmd.sh
```

Y les sale esto:

```
command required: suspend, shutdown, hibernate or reboot
```

Entonces, para apagar seria:

```
gnome-power-cmd.sh shutdown
```



Si les pide pass, haganmelo saber porque a mi no...

---

### Post by faktorqm on 2008-10-12
Si anda, sos un grosso. Salu2!

---

### Post by santiagoward2000 on 2008-10-12
No sabés cuánto estuve buscando eso! Sos un grande!

---

### Post by victor_nesta on 2008-10-12
Me viene barbaro quiero poner un media center en la casa de un amigo, y si bien aun no probé las herramientas lo que me volvía loco era como entrar sin pass, esto ya es un avance ya que un teclado al lado del televisor es un bajón.

Si llego hacerlo les cuento que onda!

---

### Post by anarhell on 2008-10-26
gracias el comando es una nota

---

### Post by c4d0rn4 on 2008-10-27
=S... creo que me perdí de algo.

A mi para apagarla no me pide pass ni nada.

(si dije alguna ganzada inserten risas en el post de abajo ajaj xD)

---

### Post by Mauro22 on 2008-10-27
Este codigo reemplazaria a sudo shutdown el cual si pide pass.


Este codigo es util para usarlo en scripts o con cron para automatizar el apagado sin tener que ingresar el pass.



Es obvio que de la forma ""grafica"" para apagar, no pide contraseña pero por consola si.

---

### Post by gearangelus on 2009-07-07
Muchisimas gracias, mire un par de foros mas, pero rapidamente me encontre con esta respuesta, justo lo que se necesita, para tirar un cron o similares con usuarios a quienes no sean sudoers.

Gracias.

--By GEAR

---

