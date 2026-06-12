---
title: "Como deslogueo una TTY?"
date: 2009-09-03
forum: Software
---

### Post by KaKuS on 2009-09-03
Gente, les comento, tengo en un servidor que no puedo reiniciar la consola colgada, lo que iba a hacer es desde otra consola o por SSH levantar el PID del bash de esa TTY y matarlo con un kill -9. 

El tema es que la consola se colgó con el usuario root logueado y no puedo por ningún motivo permitir que se reinicie o se cuelgue el equipo, que sigue realizando sus funciones automáticas.

¿Si mato esa TTY que pasa con los procesos que se están ejecutando? ¿Vuelve a la vida esa consola o queda muerta?

¿Como harían? =P

¿Hay alguna forma más "correcta" de desloguear a un usuario de otra consola?

Como siempre perdón por la ignorannnnncia :D

---

### Post by pablo.s on 2009-09-03
> **KaKuS said:**
> Gente, les comento, tengo en un servidor que no puedo reiniciar la consola colgada, lo que iba a hacer es desde otra consola o por SSH levantar el PID del bash de esa TTY y matarlo con un kill -9. 

El tema es que la consola se colgó con el usuario root logueado y no puedo por ningún motivo permitir que se reinicie o se cuelgue el equipo, que sigue realizando sus funciones automáticas.

Con cuál programa se colgó?


> **KaKuS said:**
> ¿Si mato esa TTY que pasa con los procesos que se están ejecutando? ¿Vuelve a la vida esa consola o queda muerta?

Si está colgada como decis vos
no importa mucho. Si son servicios
que está ejecutando, se siguen
ejecutando en segundo plano.
Matar la consola, no creo que puedas,
se reinicia o reloguea, pero es solo
esa consola y no es todo el sistema.

> **KaKuS said:**
> ¿Como harían? =P

Probaría de la manera más sencilla,
presionando CTRL+C y luego tipeando
```
exit
```
aunque si es un programa que está 
colgado podés probar haciendo

```
ps axf
```

ver que proceso está sin actividad
y ver si es el que está colgado para
mandarle kill.

---

### Post by KaKuS on 2009-09-04
Estas son las sesiones logueadas ahora:

```
 07:36:15 up 57 days, 20:04,  4 users,  load average: 0.00, 0.00, 0.00
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
_so       tty1     -                21Jul09 47:34m  0.04s  0.00s login -- _so   
so       tty2     -                Wed09   22:26m  0.04s  0.00s login -- so   
so       ttyS0    -                08Jul09 18.00s  2:51   0.00s login -- so   
so       pts/0    192.168.0.152    07:36    0.00s  0.03s  0.02s sshd: so [priv]

```

La TTY1 es la que se colgo, CTRL+D no lo toma y no puedo tipear nada pero CTRL+F2 para pasar de consola si.
No estaba dentro de ningún programa, solo logueada con el bash esperando.

---

