---
title: "[UTIL] como limpiar la memoria de GNU/Linux"
date: 2009-06-25
forum: Software
---

### Post by mhoyos on 2009-06-25
En los sitemas que utlizan el Kernel de Linux existe una forma de limpiar la memoria cacheada en RAM, que es información que está ahí por si hace falta, pero que no tiene por qué necesariamente estar ahí, es totalmente prescindible.

Apache es una aplicación que utiliza mucho ese tipo de memoria, y claro, en un servidor web puede provocar que se utilice más RAM de la cuenta y puede provocar problemas no deseados como el empezar a paginar, que no es otra cosa que empezar a utilizar el disco duro con información que debería estar en RAM y como la velocidad de acceso a disco es muy inferior al acceso a RAM pues el equipo puede parecer que se ha quedado “colgado”, de forma que ni siquiera podamos llegar a logarnos en el mismo.

Otro ejemplo es el navegador web Firefox, el cual consume muchoa memoria, sin que tengamos una pagina abierta con muchos contenidos.

Pero en el kernel 2.6.16 se introdujeron cambios y gracias a estos cambios la solución es muy sencilla, en el directorio /proc/sys/vm/ tenemos un fichero llamado drop_caches que es el encargado de decirle al kernel qué hacer con esa información que está en memoria, por defecto se permite el utilizar este tipo de memoria, pero para reducir RAM nos puede interesar que el kernel actúe de otra manera, modificando el valor del fichero con los siguientes valores:

    * 0: No libera nada.
    * 1: Libera la pagecache.
    * 2: Libera inodos y dentries.
    * 3: Libera pagecache, inodos y dentries.

La pagecache es la memoria la caché de páginas, un inodo es la representación de ficheros y directorios en memoria y las dentries son las entradas de directorio, componentes de un path, todos estos valores en RAM.

Para liberar podemos ejecutar estos comandos como root o con un sudo delante:

```
echo 1 > /proc/sys/vm/drop_caches 
```: Libera la pagecache.


```
echo 2 > /proc/sys/vm/drop_caches
``` : Libera inodos y dentries.


```
echo 3 > /proc/sys/vm/drop_caches
``` : Libera pagecache, inodos y dentries.

Y por supuesto no es mala idea hacer esto de vez en cuando vía una entrada en el cron de root con un crontab -e con lo siguiente:

```
#Entrada para limpiar la cache en memoria
3,18,33,48 * * * * sync; echo 3 > /proc/sys/vm/drop_caches
```

**El sync que se pone antes es para asegurarnos que todos los objetos cacheados son liberados y es muy recomendable ponerlo siempre.**

---

### Post by clasificado on 2009-06-25
creia que el control del caché era automático.

osea: no tengo idea de como funciona :P

clasificado

---

### Post by anarko on 2009-06-30
La verdad que no la sabia esta, que tan util es en servidores apache de uso muy frecuente, onda miles de clicks por minuto. Acelera liberarle el cache o lo estoy volviendo loco haciendolo reconstruir el cache cada x time.

---

### Post by fedetxf on 2010-05-17
> **anarko said:**
> o lo estoy volviendo loco haciendolo reconstruir el cache cada x time?

Exacto, liberar las cachés es malo. Queda en caché lo más frecuentemente leído y al borrarlo fuerzas a que se relea. La memoria usada como cache, es memoria disponible para programas. Si tenés poca memoria, compra más. Más datos: [http://wp.me/p50WQ-dp](http://wp.me/p50WQ-dp)

---

