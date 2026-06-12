---
title: "Problema con los efectos visuales"
date: 2009-07-14
forum: Software
---

### Post by Suraku on 2009-07-14
No se si este thread deba ir en esta seccion, si no va en esta seccion pido disculpas y que por favor lo muevan a la seccion correspondiente

El problema es que no puedo activar los efectos visuales en **Sistema>Apariencia>Efectos**, ya que al tratar de colocarlos en normal o en extra empieza a cargar los efectos y despues sale un mensaje de error. Ahi va la imagen con el mensaje de error:

_[[IMG]http://img441.imageshack.us/img441/2863/pantallazoa.th.png[/IMG]]("http://img441.imageshack.us/i/pantallazoa.png/")_

Tengo instalado Ubuntu 9.04 y mi tarjeta de video es una **S3 **VT8375 [ProSavage8 KM266/KL266], leyendo la ayuda que trae el Ubuntu me dice que debo usar un controlador de video privativo o algo asi, el problema es que he tratado de buscar un controlador privativo para esa tarjeta y no lo he encontrado. No se como solucionar este problema asi que por favor les pido ayuda.

De antemano gracias

PD: Soy un usuario bastante nuevo en Ubuntu, llevo cerca de 2 o 3 dias usando Ubuntu asi que por favor traten de explicarme la solucion al problema de la manera mas sencilla posible ya que aun hay varias cosas que no comprendo de este sistema

---

### Post by Carlos C on 2009-07-15
Hola. Por favor escribe en el terminal:
```
lspci |grep VGA
```
También anda al panel supoerior y entra en Sistema-->Administración-->Controladores de Hardware y dinos si aparece algo.

Saludos.

---

### Post by kamus on 2009-07-18
chu.. suerte con el controlador tu tarjeta! 

De todas maneras en el foro hay algunos dementes que han logrado activar la aceleracion y los efectos 3d con esa tarjeta, pero tranquilo que al parecer ya hay ruido al respecto... 

[1]http://brainstorm.ubuntu.com/idea/4005/
[2]http://foros.ubuntu-cl.org/viewtopic.php?p=31052

---

