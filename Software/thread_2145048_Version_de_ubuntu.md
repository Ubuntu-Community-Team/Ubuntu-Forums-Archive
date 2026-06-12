---
title: "Version de ubuntu"
date: 2013-05-14
forum: Software
---

### Post by sitodonosti on 2013-05-14
Hola,

hace mucho que no posteo nada, el caso es que tengo un ordenador de hace como 6 años y he probado instalando las 2 ultimas versiones pero siempre he tenido problemas con los drivers nvidia, y no me funcionaba bien ubuntu(por lo que me desespere un poco). 


Tengo un intel core dos duo con 2 gigas de ram y una grafica nvida gforce 8600m gt, que versión de ubuntu puedo utlizar y que me vaya livianamente?
gracias de antemano

---

### Post by guillermolisi on 2013-05-14
Xubuntu y/o Lubuntu son las mas livianas al momento.

---

### Post by MeduZa on 2013-05-15
te debería funcionar bien el ultimo Ubuntu en ese hard, el único problema que veo es que esa nvidia es una versión medio recortada (y customizada), calculo que el binario debería funcionar, y en su defecto el opensorce.
Saludos

---

### Post by sitodonosti on 2013-05-23
> **MeduZa said:**
> te debería funcionar bien el ultimo Ubuntu en ese hard, el único problema que veo es que esa nvidia es una versión medio recortada (y customizada), calculo que el binario debería funcionar, y en su defecto el opensorce.
Saludos

acabo de instalarlo y no me aparece "configuracion de hardware" he instalado mediante el centro de instalacion la version 173 y he reinciado y pantalla en negro...ademas que me iba muy muy lento. Llevo teniendo este problema desde hace 2 años :$

---

### Post by gmunioz on 2013-05-23
Instala el driver descargado de aqui:
[http://www.nvidia.es/object/linux-display-ia32-319.17-driver-es.html](http://www.nvidia.es/object/linux-display-ia32-319.17-driver-es.html)

---

### Post by MeduZa on 2013-05-24
pantalla negra = choque entre el driver open y el binario, me paso, tenes que quitar el opensource para usar el binario, no pueden cohexistir por aguna razon.

---

### Post by sitodonosti on 2013-05-25
> **MeduZa said:**
> pantalla negra = choque entre el driver open y el binario, me paso, tenes que quitar el opensource para usar el binario, no pueden cohexistir por aguna razon.

Cierto es, no me acordaba de ese "pequeño" detalle, lo unico malo es que me va tan sumamente lento el ordenador... no se porqué..

voy a probar descargandome los drivers de la pagina y quitar los driver open

---

### Post by sitodonosti on 2013-05-25
Bueno he vuelto reinstalar ubuntu e instaldo  repositorios, instalado synaptic. Ahora como hago para instalar el archivo .run¿ tengo que salir del modo grafico?

Aparte de esto he mirado a ver que es lo que me consumia tanto y hacia que fuera el pc tan lento, el xorg me consume como casi un 50% de la cpu... :$ sera por los drivers¿

---

### Post by gmunioz on 2013-05-25
Debes iniciar en modo recuperación, subopción root.

---

