---
title: "Instalar algo en Karmic"
date: 2010-11-04
forum: Software
---

### Post by ajdlcf on 2010-11-04
Hola!

¿Puede alguien enseñarme algo por favor?

Desde esta página hay varias instalaciones que tengo que probar pero no tengo ni la menor idea de por dónde empezar :confused:. Soy usuario de windows desde hace décadas pero con Linux desde hace unos 3 días. :mrgreen:

Quisiera empezar con una de las aplicaciones que viene COMPRIMIDA (tar.bz2) para empezar a entender. Después seguiría con otras. La página de la aplicación es esta: 

[http://openpyme.osl.ull.es/GF/applications/GNUCash](http://openpyme.osl.ull.es/GF/applications/GNUCash)

Y el link directo para bajar la aplicación es éste: 

[http://openpyme.osl.ull.es/attached/installers/333/installers/gnucash-2.2.9.tar.bz2](http://openpyme.osl.ull.es/attached/installers/333/installers/gnucash-2.2.9.tar.bz2)

Otra opción sería que me digan dónde encontrar un manual paso a paso para instalaciones en Linux.

Gracias por cualquier ayuda :mrgreen:

---

### Post by hectorivand on 2010-11-04
> **ajdlcf said:**
> Hola!

¿Puede alguien enseñarme algo por favor?

Desde esta página hay varias instalaciones que tengo que probar pero no tengo ni la menor idea de por dónde empezar :confused:. Soy usuario de windows desde hace décadas pero con Linux desde hace unos 3 días. :mrgreen:

Quisiera empezar con una de las aplicaciones que viene COMPRIMIDA (tar.bz2) para empezar a entender. Después seguiría con otras. La página de la aplicación es esta: 

[http://openpyme.osl.ull.es/GF/applications/GNUCash](http://openpyme.osl.ull.es/GF/applications/GNUCash)

Y el link directo para bajar la aplicación es éste: 

[http://openpyme.osl.ull.es/attached/installers/333/installers/gnucash-2.2.9.tar.bz2](http://openpyme.osl.ull.es/attached/installers/333/installers/gnucash-2.2.9.tar.bz2)

Otra opción sería que me digan dónde encontrar un manual paso a paso para instalaciones en Linux.

Gracias por cualquier ayuda :mrgreen:

Hola, bienvenido, en todos los archivos para instalar, una vez descomprimidos, por lo general hay un archivo con las instrucciones para instalar.

En el caso de Gnu Cash está en los repositorios, con lo cual, solo tenes que ir a la consola y poner lo siguiente.:

```
sudo apt-get install gnucash
```

Cuando te pida un password, pone el que seteaste en la instalación, no te va a mostrar nada y es correcto, una vez ingresado, les das Enter y después de ahi "Y", te va a empezar a descargar e instalar los paquetes necesarios.

En Karmic Koala ya estaba la tienda de aplicaciones... que se llama Software Center o Centro de Software de Ubuntu, desde ahí podes buscar aplicaciones e instalarlas sin mayores complicaciones ;)

Cualquier consulta que tengas por acá ando.

Saludos
Nacho

---

