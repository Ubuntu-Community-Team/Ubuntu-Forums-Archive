---
title: "Stopmotion"
date: 2008-10-04
forum: Software
---

### Post by jajajavi on 2008-10-04
Hace un tiempo instalé el Stopmotion, un programita que está en los repositorios y sirve para hacer animaciones [[COLOR="SeaGreen"]stopmotion[/COLOR]]("http://es.wikipedia.org/wiki/Stop-motion"), es decir secuencias animadas hechas con imágenes concatenadas, el principio básico del cine. Pero cuando cargo varias imágenes (fotogramas) e intento exportar la animación el programa se cierra y tira estos errores:

```
Fallo de segmentación

Unsupported call to FAMSuspendMonitor()
Unsupported call to FAMResumeMonitor()

```

La frustración me llevó a experimentar con [MEncoder]("http://www.mplayerhq.hu/") que por lo que entendí Stopmotion viene a ser como una interfaz gráfica que utiliza MEncoder. Para hacer una película a partir de imágenes jpg (640x480), abro una terminal y voy a la carpeta donde están guardadas y pongo:

```
mencoder mf://*.jpg -mf type=jpg:fps=25 -o PELICULA.avi -ovc lavc -lavcopts vcodec=mpeg4
```
que quiere decir convertir todos los jpg (*.jpg) de la carpeta en una película avi a 25 cuadros por segundo (fps) codificado en mpeg4, ponele...

Hay más opciones para crear animaciones a partir de imágenes estáticas en [el manual de MEncoder]("http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-images.html") (la versión [en español]("http://www.mplayerhq.hu/DOCS/HTML/es/menc-feat-enc-images.html") está desactualizada). El avi se puede editar en avidemux u otros para agregar sonido, efectos, etc. 

Ejemplos:
[http://vimeo.com/1859792](http://vimeo.com/1859792)
[http://www.youtube.com/watch?v=NTtlvlGm5kY](http://www.youtube.com/watch?v=NTtlvlGm5kY)

También es posible hacer una stopmotion con el [Gimp]("http://www.gimp.org/"), y el proceso es el siguiente: abrir el primer fotograma y abrir el resto como capas, pasar a color indexado y guardar como gif (opción "guardar como animación"). Hay un tutorial más completo [acá]("http://www.linuxquestions.org/questions/linuxquestions.org-member-success-stories-23/stop-motion-tutorial-613757/").

Podemos pasar el gif a avi:
```
mencoder ANIMACION.gif -ovc lavc -fps XX -o PELICULA.avi
```

XX = cuadros por segundo

---

### Post by leo_rockway on 2008-10-05
> **jajajavi said:**
> El avi se puede editar en avidemux u otros para agregar sonido, efectos, etc. 

Y el Avidemux es también, en realidad, un frontend para el Mencoder.

Una lástima lo del Stopmotion, yo lo había probado hace un año y tenía ese problema. Aparentemente no avanzó mucho desde entonces.

---

