---
title: "Problema de instalacion de Ubuntu Gutsy dentro de una maquina virtual en Virtual Box"
date: 2008-11-25
forum: Software
---

### Post by pablerque on 2008-11-25
Buenas,

Mi sistema host es Ubuntu Intrepid y tengo la ultima version de Virtual Box (la 2.0.6)

Estoy hace dias intentando instalar el Ubuntu Gutsy dentro de una maquina virtual y al 82% de la instalacion se congela y no avanza mas.

En esta imagen se puede observar como el proceso de instalacion avanza sin problemas (el cartel dice que queda solo un minuto...)

[IMG]http://www.warriorsdeath.com.ar/pantallazo1.png[/IMG]


y luego cuando configura el APT ahi se queda congelado con el ste cartel:

[IMG]http://www.warriorsdeath.com.ar/pantallazo2.png[/IMG]

Ya verifique el disco en busca de errores, probe con una imagen ISO montada, probe con el XUBUNTU y el UBUNTU ULTIMATE EDITION (todos Gutsy) y en todos los casos se queda congelada la instalacion en el mismo punto.

Como ultimo comentario, les comento que el archivo de imagen que prepare para el virtual box, lo tengo en una particion NTFS porque no me queda mas espacio en /home.

Aguardo sus comentarios.

Saludos.

---

### Post by Hei Ku on 2008-11-25
No te encuentra la conexion a internet para conectarse y bajar actualizaciones. O por lo menos a mi me paso algo similar en una PC que estaba detras de un proxy. Lo solucione bajando a consola y configurandolo ahí.

---

### Post by pablerque on 2008-11-25
> **Hei Ku said:**
> No te encuentra la conexion a internet para conectarse y bajar actualizaciones. O por lo menos a mi me paso algo similar en una PC que estaba detras de un proxy. Lo solucione bajando a consola y configurandolo ahí.
Perdon por mi ignorancia pero a que te referis con "...lo solucione bajando a consola y configurandolo ahí..."

---

### Post by Hei Ku on 2008-11-25
Ctrl+Alt+F1 y configure el apt-get para el proxy.

Es este tu caso? No tenes configurada la red en esa maquina?

---

### Post by pablerque on 2008-11-25
En realidad en esa pc no tengo ninguna conexion a internet (es en mi casa).

Igual me diste una pista y voy a probar. A la maquina virtual le voy a sacar el adaptador de red y ver que sucede.

---

### Post by guisheca on 2008-11-26
> **pablerque said:**
> En realidad en esa pc no tengo ninguna conexion a internet (es en mi casa).

Igual me diste una pista y voy a probar. A la maquina virtual le voy a sacar el adaptador de red y ver que sucede.

Sip yo creo que con eso tiene que andar. El problema es justamente que se queda esperando conexión, capás con eso se soluciona.

---

### Post by pablerque on 2008-11-26
Bueno finalmente lo pude solucionar de esa manera, es decir, a la maquina virtual le desactive el adaptador de red y la instalacion continuo normalmente. Luego una vez instalada la volvi a poner el adaptador de red y ahi se configuro.

Muchas gracias.

---

