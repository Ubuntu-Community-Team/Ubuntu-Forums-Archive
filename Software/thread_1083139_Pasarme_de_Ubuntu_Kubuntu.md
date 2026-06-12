---
title: "Pasarme de Ubuntu Kubuntu"
date: 2009-02-28
forum: Software
---

### Post by victor_nesta on 2009-02-28
La cosa es que después de usar un tiempo ubuntu quiero formatear la maquina para aprovechar mejor los espacios de las particiones, ordenar un poco todo y usar solo lo necesario y/o que me gusto.

Lo que me gustaría al instalar el Kubuntu es poder instalar de manera fácil algunas aplicaciones que ya tengo, sin tener que estar dando tanta vuelta buscando como se llamaba, que necesitaba, ect. Y asi no perder tanto tiempo.

¿Hay alguna manera fácil de guardar lo que necesito en 1 o mas .deb? O algo por el estilo FACIL

Gracias

---

### Post by NickCis on 2009-02-28
Que son, aplicaciones que vienen con Ubuntu?, que compilaste? o que conseguiste los debs x ahi y los instalaste?.

Si estan en los repositorios de ubuntu, creo que podes bajarte los debs de ahi, aptitude tiene una opcion para solo bajarlos y despues instalarlos. Pero es mucho mas facil que te anotes los nombres y despues con el comando "sudo apt-get install [nombre de aplicacion1] [nombre de aplicacion2] [nombre de aplicacion3] [etc]" y te lo instala y configura todo.

Igual tene en cuenta, que esas aplicaciones capas son especificas para Gnome, y probablemente hay una parecida que sea nativa KDE y ande mejor.

Si los compilaste, meparece que hay forma de crearte los debs, en este momento desconozco, ya que tuve poca experiencia compilando.

La forma mas facil es la de instalar via repositorios, ya que con un comando podes instalar todo de una, sin nececidad de hacer un backup de debs (que son uno por cada programa). Ademas, se resolveria el problema de las dependencias, ya que aptitude te las instala :P.

Saludos.

---

### Post by staar on 2009-02-28
para no tener que bajarte tooodo de nuevo, instalate APTonCD ```
sudo aptitude install aptoncd
``` que te permite guardar la caché de apt en un cd y copiarla a otro sistema, en la caché (si no la limpiaste) va a estar todo lo que instalaste a traves de repositorios, lo que compilaste o instalaste con debs vas a tener que conseguirlo de vuelta

saludos

---

### Post by victor_nesta on 2009-03-01
NickCis: De todo un poco. por eso!!

staar: Vi esta opcion en algunas webs. El tema es que si limpie la Cache.

Creo que reinstalare todo, y ahi si tiro un aptoncd, para no hacerlo mas.

Gracias!

---

