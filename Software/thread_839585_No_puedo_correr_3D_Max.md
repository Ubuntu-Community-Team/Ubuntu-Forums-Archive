---
title: "No puedo correr 3D Max"
date: 2008-06-24
forum: Software
---

### Post by Gpafundi on 2008-06-24
Buenas a todos. La verdad es que esto de la buena onda que hay entre usuarios de Ubuntu nunca lo había visto. Soy novato en esto así que todo lo que me quieran explicar, haganlo (por favor) de manera sencilla y simple.

Bueno, les explico. Acabo de instalar todos los drivers y realmente comienzo a dominar un poco el tema del sistema operativo. Me quedo mil veces con Ubuntu que con windows. Mi cuestión es la siguiente. Quisiera reemplazar Windows por mi Ubuntu 8.04 pero digamos que por cuestiones universitarias estoy atado a Windows. Tengo que usar programas como el 3D max y que no puedo instalar en Ubuntu. Probé con el Wine y no anda. Lo instale dentro de un disco virtual del VirtualBox y se instala pero, al andar el programa no puedo visualizar nada que sea en 3D. He buscado en foros y encontré que decía que hay una versión paga de VirtualBox que permite utilizar la placa de video y que la versión gratuita no lo hace. Calculo yo que ese es mi problema.

1. Alguien sabe si ese es mi problema?
2. De ser ese mi problema, existe otro programa similar al VirtualBox pero gratuito?

Desde ya muchas gracias

---

### Post by guisheca on 2008-06-24
Amigo te comento, en primer lugar, no existe hasta la fecha una maquina virtual capas de emular una aceleradora de video, no existe, ni de pago, ni gratis ni nada, eso por ahora no es posible. Es decir, virtualizando jamas vas a poder visualizar objetos en 3D (esto incluye juegos, lamentablemente).
Mediante wine podés hacer funcionar programas que utilicen aceleración gráfica, por ejemplo juegos, pero tenés que instalar las librerías del directx y, no es por tirarte mala onda, jamás pude hacerlo, aunque existen muchos tutoriales al respecto en internet.
Lamento no poder ayudar demasiado, quizás te interese, por lo menos probar, blender que es el software de modelado y animación 3D por excelencia en sistemas linux.
Saludos

---

### Post by pablo.s on 2008-06-24
Software profesional para modelado en 3D:

-[Alias Maya]("http://usa.autodesk.com/adsk/servlet/item?siteID=123112&id=7635770") 
-[SideFX Houdini]("http://www.sidefx.com/index.php?option=com_content&task=view&id=1277&Itemid=66")
-[Softimage XSI]("http://www.softimage.com/products/xsi/evaluation.aspx")

Software semiprofesional para modelado en 3D:

-[Blender]("http://www.blender.org/download/get-blender/")
-[Wings 3D]("http://www.wings3d.com/")

Todos estos funcionan de forma nativa en cualquier distribucion de Linux.

---

### Post by jonafischer on 2008-06-26
usa kvm si tu procesador te deja, es una version modificada de qemu que virtualiza con soporte de hardware, actualmente tengo instalado de esta forma win XP UE, opensuse 11.0 y xubuntu y todo funciona que es un violin! eso si tengo un AMD Turion 64x2 TL-60 mobile... Yo virtualizo win y uso mis programas asi!

---

### Post by osensei on 2008-07-03
> **guisheca said:**
> Amigo te comento, en primer lugar, no existe hasta la fecha una maquina virtual capas de emular una aceleradora de video, no existe, ni de pago, ni gratis ni nada, eso por ahora no es posible. Es decir, virtualizando jamas vas a poder visualizar objetos en 3D (esto incluye juegos, lamentablemente).
Mediante wine podés hacer funcionar programas que utilicen aceleración gráfica, por ejemplo juegos, pero tenés que instalar las librerías del directx y, no es por tirarte mala onda, jamás pude hacerlo, aunque existen muchos tutoriales al respecto en internet.
Lamento no poder ayudar demasiado, quizás te interese, por lo menos probar, blender que es el software de modelado y animación 3D por excelencia en sistemas linux.
Saludos

Sí existen máquinas virtuales con soporte para DirectX, VMWare Fusion (para Mac) y VMware Workstation 6.5 beta soportan DirectX 9.0 con pixel shader hasta la versión 2.0 

Por otro lado, acá hay una guía (en inglés) para instalar DirectX 9.0c en Wine que a mí me funcionó.

[http://www.wine-reviews.net/microsoft/directx-90c-march-2008-redistributable-on-linux-with-wine.html](http://www.wine-reviews.net/microsoft/directx-90c-march-2008-redistributable-on-linux-with-wine.html)

Saludos!

---

### Post by leo_rockway on 2008-07-04
> **pablo.s said:**
> 

Software semiprofesional para modelado en 3D:

-[Blender]("http://www.blender.org/download/get-blender/")


Usado en Spider-Man 2, Elephants Dream, Big Buck Bunny, Plumiferos... ¿semi?

---

