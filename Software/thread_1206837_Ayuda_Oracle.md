---
title: "Ayuda Oracle"
date: 2009-07-07
forum: Software
---

### Post by Pottian on 2009-07-07
Tengo un archivo.sql que esta ok ejecutandose correctamente etc etc ..
el problema es que tengo spool nuevoarchivo.txt y este sql se ejecuta por lo menos durante 2 horas por ende el spool soreescribe el nuevoarchivo.txt lo que necesito hacer es 
dejar ese nuevoarchivo.txt en otro archivo.txt para que me valla añadiendo linea tras linea 
esper que se entienda.
hice esto en el cron

* * * * * usuario /ruta/archivo.sh >> /ruta/archivo.txt
dentro de esa SH esta la llamada del archivo sql q se conecta y tiene los selects.

despues lo intenete sin usuario es decir
* * * * * /ruta/archivo.sh >> /ruta/archivo.txt

y por ultimo cree una SH que decia

tome el archivo que crea el SPOOL dentro del sql 

nuevoarchivo.txt >> nuevoarchivo2.txt

y me da unos errores como de espacio cuando intenta pasar de uno al otro ...

gracias de antemano

---

### Post by Pottian on 2009-07-07
Tengo un archivo.sql que esta ok ejecutandose correctamente etc etc ..
el problema es que tengo spool nuevoarchivo.txt y este sql se ejecuta por lo menos durante 2 horas por ende el spool soreescribe el nuevoarchivo.txt lo que necesito hacer es 
dejar ese nuevoarchivo.txt en otro archivo.txt para que me valla añadiendo linea tras linea 
esper que se entienda.
hice esto en el cron

* * * * * usuario /ruta/archivo.sh >> /ruta/archivo.txt
dentro de esa SH esta la llamada del archivo sql q se conecta y tiene los selects.

despues lo intenete sin usuario es decir
* * * * * /ruta/archivo.sh >> /ruta/archivo.txt

y por ultimo cree una SH que decia

tome el archivo que crea el SPOOL dentro del sql 

nuevoarchivo.txt >> nuevoarchivo2.txt

y me da unos errores como de espacio cuando intenta pasar de uno al otro ...

gracias de antemano

---

### Post by Sef on 2009-07-07
merged.

---

### Post by Pottian on 2009-07-08
> **Sef said:**
> merged.
sorry.

ya encontre la solucion gracias a los que leyeron e intentaron ayudar de todas formas.

Close pliss

---

### Post by moreback on 2009-07-08
¿Serías tan amable de compartir la solución para que si nos toca pasar por algo similar sepamos donde buscar?

Gracias.

Saludos.

---

