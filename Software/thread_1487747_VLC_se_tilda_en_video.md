---
title: "VLC se tilda en video"
date: 2010-05-19
forum: Software
---

### Post by Criminel on 2010-05-19
Hola,
Con ubuntu 10.04 el VLC se tilda repetidamente deteniendo la reproducci{on de video (se congela un par de minutos) mientras el audio sigue corriendo.
Sospecho una cuesti{on de caché, memorias o algo así pero la verdad no doy con la solución.

¿Alguna idea?

---

### Post by juancarlospaco on 2010-05-19
*Deshabilitar compiz...?*

---

### Post by Criminel on 2010-05-20
Deshabilitar compiz no me ha solucionado el tema. Gracias  igual.

---

### Post by alfplayer on 2010-05-20
Hardware insuficiente?

---

### Post by Criminel on 2010-05-20
> **alfplayer said:**
> Hardware insuficiente?

No entiendo a qué te referís exactamente. Con 8.04 LTS no tenía ningún inconveniente.

---

### Post by alfplayer on 2010-05-20
> **Criminel said:**
> No entiendo a qué te referís exactamente. Con 8.04 LTS no tenía ningún inconveniente.

Por ejemplo, CPU lento, o procesador gráfico (en tarjeta de video o integrado en el motherboard o CPU) lento.

---

### Post by demuxer on 2010-05-20
hey Criminel, podrias indicar si estas haciendolo con un disco DVD, con  archivos de algun codec específico? estas seguro que con cualquier tipo  de archivo te da ese problema?

de no ser asi, me temo que sea el cambio de kernel también, con cual trabajabas antes?

---

### Post by Criminel on 2010-05-20
> **demuxer said:**
> hey Criminel, podrias indicar si estas haciendolo con un disco DVD, con  archivos de algun codec específico? estas seguro que con cualquier tipo  de archivo te da ese problema?

de no ser asi, me temo que sea el cambio de kernel también, con cual trabajabas antes?

Sucede con discos de DVD, con archivos de video en todos los formatos grabados en un data DVD e incluso con archivos de video que están en el rígido. Ignoro cuál era el kernel (no soy ducho en esas cosas) pero usaba el ubuntu 8.04 LTS antes.

Gracias a todos los que responden.

---

### Post by alfplayer on 2010-05-20
Si nos das información de qué hardware estás usando (como procesador o placa de video) y del tipo de videos que tienen problemas tal vez podemos saber mejor qué está sucediendo.

Se puede probar por ejemplo con videos de baja resolución, que deberían reproducir correctamente en casi cualquier computadora moderna.

---

### Post by guillermolisi on 2010-05-20
> **Criminel said:**
> Sucede con discos de DVD, con archivos de video en todos los formatos grabados en un data DVD e incluso con archivos de video que están en el rígido. Ignoro cuál era el kernel (no soy ducho en esas cosas) pero usaba el ubuntu 8.04 LTS antes.

Gracias a todos los que responden.
Para saber que version de kernel estas usando, ingresa ```
uname -a
```en una consola/terminal.

Si queres saber que version de Ubuntu estas usando, ingresa ```
lsb_release -a
```en una consola/terminal.

Entre los dos sabras bastante bien que estas usando.

---

### Post by Criminel on 2010-05-21
> **alfplayer said:**
> Si nos das información de qué hardware estás usando (como procesador o placa de video) y del tipo de videos que tienen problemas tal vez podemos saber mejor qué está sucediendo.

Se puede probar por ejemplo con videos de baja resolución, que deberían reproducir correctamente en casi cualquier computadora moderna.

Es un AMD Sempron de 1.6 con 1GB de RAM y  placa de video Nvidia GEforce 6150SE nForce 430 (sea lo que sea lo que eso signifique...) de 512MB de memoria

---

### Post by Criminel on 2010-05-21
En cuanto al kernel (si seguí bien sus instrucciones):
Linux drutus-desktop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

¿Existen procesos que se puedan detener como en Windows para aligerar el uso de memoria o eso no afecta nada en Linux?

---

### Post by alfplayer on 2010-05-21
Ese hardware puede tener problemas para muchos videos.

Además, Ubuntu 10.04 se instala con un driver de video llamado Nouveau que no aprovecha toda la capacidad del hardware.

Es posible deshabilitar servicios, por ejemplo con un programa llamado "bum" (el paquete se llama igual). Eso puede ayudar.

---

### Post by Criminel on 2010-05-21
Buscando conla utilidad de controles de hardware me da como resultado la posibilidad de activar los siguientes controladores privativos:
aparecen así:

Controlador para Nvidia versión 173 (este controlador no está activado)
Controlador para Nvidia versión 96 (este controlador no está activado)
Controlador para Nvidia (versión current) (recomendado) (Se está usando una versión diferente de este controlador)

¿Debería activar alguno de ellos en particular?

---

### Post by Criminel on 2010-05-21
Adicionalmente quisiera comentar que llevo dos años reproduciendo videos con VLC bajo Ubuntu 8.04 ( razón de un par de pleículas por día) sin haber jamás encontrado antes problemas de este tipo.
Agradeceré  si alguien tiene idea de porqué sucede esto ahora con 10.04 y también cualquier seteo que pueda ayudarme a minimizar el problema.

---

### Post by alfplayer on 2010-05-21
Los versiones de Ubuntu vienen más y más "pesadas". Lo primero que podés probar es, como mencioné antes, deshabilitar servicios con *bum*.

Instalar el controlador de video de Nvidia también puede mejorar el video, aunque no se qué opción hay que elegir para el 6150 SE (se puede buscar ayuda *googleando*).

---

### Post by Criminel on 2010-05-23
Luego de actualizar el driver de nVidia llegué a una solución de compromiso que es deshabilitar todos los efectos visuales para poder ver un video sin problemas.
Gracias a todos los que se tomaron la molestia de leer y contestar.

---

