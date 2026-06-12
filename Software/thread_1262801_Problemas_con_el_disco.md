---
title: "Problemas con el disco"
date: 2009-09-10
forum: Software
---

### Post by ropb on 2009-09-10
Buen dia a todos....He intentado en varias oportunidades pasarma a Linux y debi desistir por falta de tiempo. Ahora me decidí a migrar dado que Windows colmo mi *BEEP*.
Mi motherboard es una Asrock P4I45GV que, creo, no es la mejor opcion para comenzar con Linux.
He instalado Ububtu 9.04. Remando solucione los problemas con una placa Nvidia y logre hacer andar al Compiz. Ahora estoy luchano con la placa de TV y la sicronizacion entre Evolution y mi Ipaq.
Perdon por la chachara. Mi consulta es la siguiente: me parece que esto no ocurre desde el principio, porque noto desde hace unos dias la PC mas lenta.
He descubierto que la luz del disco duro titila constantemente sin haber razon, aun sin tener ningun programa abierto. Ademas el uso de la CPU esta entre el 50 y 70% y viendo los procesos activos no han nada que produzca ese nivel de actividad.
¿Pueden darme alguna sugerencia?
Saludos

---

### Post by alfplayer on 2009-09-10
Te recomiendo hacer lo expresado en el primer párrafo del segundo mensaje de este tema: [http://ubuntuforums.org/showthread.php?t=1221186](http://ubuntuforums.org/showthread.php?t=1221186)

Esto es para saber qué proceso/s usan el CPU.

---

### Post by ropb on 2009-09-11
Gracias Alfplayer por tu respuesta.

Ya habia hecho lo que tu comentaste y tengo, segun el monitor, un 20 a 25% de uso de CPU y si lo miras en el tab de recursos el uso es de un 60 a 70%. No encuentro razon a esto.
Ademas no hay activo ningun proceso que justifique ese uso del disco.
Saludos

---

### Post by staar on 2009-09-11
por casualidad tenés alguna partición NTFS en uso? porque me ocurría algo similar, y era porque dicha partición estaba muy fragmentada, y cada vez que el sistema escribía algo ahí el uso de CPU y disco se iba por las nubes, la solución fue desfragmentar la partición...

saludos

---

### Post by ropb on 2009-09-11
Staar gracias por tu respuesta. tengo particiones fat y ntfs pero lo que me llama la atencion es que no abriendo ningun programa y no existiendo razon aparente alguna para que se use el disco igual puede pasarse horas titilando. Nunca he visto que deje de hacerlo.
Salu2

---

### Post by staar on 2009-09-11
una cosa, la luz titila porque realmente se usa el disco? a lo que voy, no podría ser que ande mal la luz (por problema de software o de hardware)? escuchás el ruido del disco cuando pasa?

saludos

---

### Post by alfplayer on 2009-09-12
> **ropb said:**
> Ya habia hecho lo que tu comentaste y tengo, segun el monitor, un 20 a 25% de uso de CPU y si lo miras en el tab de recursos el uso es de un 60 a 70%. No encuentro razon a esto.
Ademas no hay activo ningun proceso que justifique ese uso del disco.

Está faltando un porcentaje, que probablemente sea de otro usuario, que puede ser root. Se pueden ver los procesos de root ejecutando en un terminal:

```
sudo gnome-system-monitor
```

**Edit**: También se pueden mostrar los procesos de root con el menú Ver del Monitor de sistema, cliqueando *Todos los procesos*. Cliqueando *Procesos activos* se podría ver lo que estás buscando (solo se muestran los procesos activos de todos los usuarios)

---

