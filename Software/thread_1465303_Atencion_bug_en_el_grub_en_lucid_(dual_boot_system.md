---
title: "Atencion: bug en el grub en lucid (dual boot systems)"
date: 2010-04-29
forum: Software
---

### Post by guillermolisi on 2010-04-29
Marco Antonio (mhoyos) publico recien lo siguiente en la lista de soporte de Ubuntu-ar:

> Para los que instalen ubuntu lucid en equipos con doble booteo, se a
detectado un error en el grub:

El error causa que aquellos con más de un Sistema Operarivo (dual boot
environment)  no veamos sus entradas en el Grub para elegirlos como
alternativo para trabajar.

La solución ya está disponible en updates y hasta manualmente se puede
corregir con

sudo grub-install --recheck /dev/sda

De todas maneras, se ha decidido demorar la salida de la versión
final, hasta que la solución sea integrada a la misma, sin necesidad
de hacer nada extraño para solucionar el error. Algo que me parece
estupendo ya que me costó trastear ante un error similar con el Koala
y el Seven.

Para más información y seguir el reporte del error, pueden seguir su wiki:

[https://wiki.ubuntu.com/IncidentReports/2010-04-29-Late-respin-for-bug-570765](https://wiki.ubuntu.com/IncidentReports/2010-04-29-Late-respin-for-bug-570765)


---

### Post by harryscode on 2010-04-29
Que raro... yo instalé Lucid (el RC) y no tuve problemas, tengo dual boot y grub anduvo sin inconvenientes.

---

### Post by alfplayer on 2010-04-29
> **harryscode said:**
> Que raro... yo instalé Lucid (el RC) y no tuve problemas, tengo dual boot y grub anduvo sin inconvenientes.

El bug pudo haber sido introducido después del iso del RC.

---

