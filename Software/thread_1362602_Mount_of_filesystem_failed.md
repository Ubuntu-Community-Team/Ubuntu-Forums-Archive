---
title: "Mount of filesystem failed"
date: 2009-12-23
forum: Software
---

### Post by ketzelleshelle on 2009-12-23
Hoy despuès de un tiempo de no usar ubuntu, al encender el equipo (en el cual comparto 9.10 y Windows 7) me salió esto:

[I]Mount of filesystem failed
A maintenance shell will now restarted
Control-D will terminate this shell and retry
[/I]

Al hacer Control-D, les dejo un screenshot de lo que apareció.


Alguna idea?
Muchas Gracias.

---

### Post by gmunioz on 2009-12-23
Si.

Inicia desde un live-cd
Desmonta la partición si se hubiere montado
en consola ejecuta

```
sudo su
umount /dev/sda7
```

Repárala

```
fsck -a /dev/sda7
```

Reinicia del disco rígido

```
reboot
```

---

### Post by ketzelleshelle on 2009-12-23
El comando

sudo su
umount /dev/sda7

pareciera no causar nada.
Te dejo un nuevo screenshot de lo sucedido.

Gracias por la pronta respuesta.

---

### Post by gmunioz on 2009-12-23
Hola ket....:

1- sudo su
No hace nada porque ya estas trabajando como root
y es para loguearte como root desde un usuario normal


2- umount /dev/sda7
Si no informa nada, es que desmontó correctamente.

3- El siguiente comando es:
fsck *(espacio)* -a *(espacio)* /dev/sda7

---

### Post by ketzelleshelle on 2009-12-24
Bien. Esto es lo que me devuelve.
Gracias por la respuesta.

---

### Post by guillermolisi on 2009-12-24
> **ketzelleshelle said:**
> Bien. Esto es lo que me devuelve.
Gracias por la respuesta.
Ahi te dice lo que tenes que hacer: Repetir la corrida de fsck pero sin las opciones -a o -p.

Proba y comenta que resulto.

---

### Post by ketzelleshelle on 2009-12-24
Bueno. Actualmente escribo esto ya desde Ubuntu.
Dejo los dos pantallazos finales.
Básicamente me arriesgué a ir diciendo a todo que sí, y el resultado (al menos de momento, ya que estoy adentro) fué positivo.

De todos modos me gustaría saber que fué lo que sucedió.

Muchísimas gracias.

---

### Post by guillermolisi on 2009-12-24
Por lo que interpreto de la informacion que se ve en el monitor, la maquina no cerro correctamente los archivos que tenia abiertos antes de apagarse (shutdown).
Las causas para esto son varias y van desde un problema en el disco hasta un corte de energia imprevisto, abrupto, pasando por un microcorte.

En la primer fotografia se ve que hay una apreciable cantidad de bloques que dependian de un mismo i-node y que, a raiz de alguna de las causas mencionadas, no termino de actualizar todo el sistema de archivos de esa particion.

De hecho la informacion que estaba almacenada en esos bloques ya no existe (en su forma logica, si lo estan fisicamente) porque fueron marcados como espacio libre para todo el file system.

---

### Post by ketzelleshelle on 2009-12-24
Excelente. Me quedo investigando lo que posteaste, Guillermo.
Doy el tema por solucionado.

---

### Post by guillermolisi on 2009-12-24
> **ketzelleshelle said:**
> Excelente. Me quedo investigando lo que posteaste, Guillermo.
Doy el tema por solucionado.
Si tenes alguna duda respecto de la salud de ese disco, instala Smartmon tools asi podes monitorearlo y hasta configurar ese paquete para que te avise via e-mail si algo anda fuera de los parametros aceptables, como por ejemplo la cantidad de reintentos de lectura y escritura.

Otra cosa que no me parece menor es configurar el BIOS de la maquina para que ante un corte de energia permanezca apagada (algunas tienen la opcion de volver al estado original o reinicio) y lo mejor ante estas circunstancias es estar delante del monitor cuando la volves a encender para evitar usarla en condiciones irregulares (por falta de una adecuada revision de consistencia del file system).

---

### Post by lean-mini on 2009-12-27
> **guillermolisi said:**
> Por lo que interpreto de la informacion que se ve en el monitor, la maquina no cerro correctamente los archivos que tenia abiertos antes de apagarse (shutdown).
Las causas para esto son varias y van desde un problema en el disco hasta un corte de energia imprevisto, abrupto, pasando por un microcorte.

Guillermo: a mi me suele pasar lo mismo en mi Hp2133 cuando la estoy utilizando sin la batería. Con la batería puesta nunca me sucedió. Lo de la batería lo hago para no agotarla. No se si sirve el dato, o que te parece. Saludos y felices fiestas.

---

### Post by tombino34 on 2010-09-11
excelente explicacion de como recuperar este error , me fue muy util .
GRACIAS!  esto si quiero que suene como grito.

Saludos

---

### Post by adelchi on 2011-02-22
Yo tengo el mismo problema! pero con la particularidad de que no me deja escribir nada, es igual al primer pantallazo

---

### Post by putxi on 2013-01-10
Gracias por postear el problema, y por las soluciones aportadas.
He tenido el mismo problema, y ya está resuelto (fsck + yes, yes, yes, ... + reboot)!  ;-)
En mi caso fue por apagón inesperado por error en instalación cableado eléctrico, también solucionado.

Saludos!
Jordi

---

