---
title: "Problema en el escritorio y paneles cuando uso Writer"
date: 2009-07-19
forum: Software
---

### Post by anagramagia on 2009-07-19
Al tener una ventana de Writer o Draw (pero sobre todo con Writer) abierta y activa y pasar el mouse por el panel inferior o por el escritorio, desaparecen íconos, el reloj, cambian los colores, los menúes emergentes no se entienden porque quedan imagenes superpuestas.

Si minimizo la ventana de Writer o clickeo en otra ventana con lo cual la de Writer deja de estar activa, entonces se vuelve a la normalidad.

Las versiones de Writer que probé y con las que sucede el problema que comento son las que vienen en: OpenOffice.org 2.4 y 3 para Linux y la 3.01 portátil para windows.

No pasa con otros programas que usé hasta el momento.

El sistema es Kubuntu 8.10 32bits en una pc AMD Athlon 64 X2 Dual Core Processor 5200+, 2GB RAM.

Placa de video:                                      
description: VGA compatible controller
product: GeForce 7050 PV / nForce 630a
vendor: nVidia Corporation                     
physical id: 12
bus info: pci@0000:00:12.0
version: a2    
width: 64 bits   
clock: 66MHz      
capabilities: bus_master cap_list
configuration: driver=nvidia latency=0 module=nvidia 

La pantalla está configurada a 1024x768 y 50.0Hz

El monitor es Samsung SyncMaster 510s

Están instalados los drivers nvidia-177-kernel-source (177.80-0ubuntu2), nvidia-common (0.2.4), nvidia-kernel-common (20080825+1ubuntu2), nvidia-glx-177 (177.80-0ubuntu2), nvidia-settings (177-78-0ubuntu2).

---

### Post by staar on 2009-07-19
ese es un problema entre las aplicaciones java y KDE, especialmente con placas nvidia, es un bug viejo y reportado, que ocurría en varias distros, en teoría ya solucionado, decís que aún usas intrepid, te recomendaría que actualizes, por lo menos la versión de KDE...

una solución temporal es desactivando los efectos de escritorio al usar el OOo (Alt + Shift + F12) o cambiar el motor de estos a XRender (mucho más lento que OpenGl)

saludos

---

### Post by anagramagia on 2009-07-22
Gracias por la respuesta!
Voy a probar lo que me sugerís. Para eso antes de abrir writer o después ¿presiono Alt+Shift+F12 y se desactivan los efectos de escritorio?

¿Cómo cambio el motor de los efectos a XRender?

---

### Post by staar on 2009-07-22
el motor lo cambiás en Preferencias del Sistema > Escritorio > Avanzado > Tipo de composición, la combinación esa sirve en cualquier momento mientras KDE esté en funcionamiento...

saludos

---

### Post by anagramagia on 2009-07-24
Ok. Gracias.

---

