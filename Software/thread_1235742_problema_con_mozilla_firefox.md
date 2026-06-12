---
title: "problema con mozilla firefox ???"
date: 2009-08-09
forum: Software
---

### Post by pelaolinux on 2009-08-09
Hola a todos !!! 
Bueno explico el problema, lo que sucede es que mi navegador mozilla firefox no esta funcionando correctamente, los flash de las paginas se pegan o se ven demasiados cortado, los vídeos de youtube o paginas a si se ven muy cortado y aparte en algunas paginas se queda congelado el mozilla con una pantalla griss que cubre todo el navegador .... 

como puedo solucionar todos esos problemas??? 

Saludos!!!

---

### Post by nopersona on 2009-08-09
Acabo de recibir una actualización por lo mismo, yo uso 3.0.13.  De todas formas, [prueba firefox 3.5. ]("http://ubuntupatagonia.blogspot.com/2009/08/como-instalar-firefox-35-en-ubuntu.html")

---

### Post by EnriqueK on 2009-08-09
Instala **flashplugin-installer** , como indica su nombre, es un imstalador de flash que lo que hace es conectar al sitio de Adobe y procede a descargar y luego a instalar el plugin flash , sería recomendable que antes desinstales el flash que tengas.
Otra forma es instalar el metapaquete "**ubuntu-restricted-extras**" , que además trae varios otros prohtamas co ser Java, fuentes de Microsoft, codecs, etc, etc.

---

### Post by pelaolinux on 2009-08-09
> **EnriqueK said:**
> Instala **flashplugin-installer** , como indica su nombre, es un imstalador de flash que lo que hace es conectar al sitio de Adobe y procede a descargar y luego a instalar el plugin flash , sería recomendable que antes desinstales el flash que tengas.
Otra forma es instalar el metapaquete "**ubuntu-restricted-extras**" , que además trae varios otros prohtamas co ser Java, fuentes de Microsoft, codecs, etc, etc.

hola!! 
mira tu me estas diciendo que aga esto : 
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash
sudo apt-get install flashplugin-installer

y eso yo ya lo ise y me funciono bien ahora el problema es que me esta funcionando mal de nuevo, pero probare con el mata paquete para ver que tan eficaz sera....

---

