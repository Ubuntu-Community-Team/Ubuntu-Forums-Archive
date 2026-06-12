---
title: "Java Plugin 64 bits"
date: 2008-12-18
forum: Software
---

### Post by z37a on 2008-12-18
Hola gente, antes que nada les quería comentar parece ser que los muchachos de SUN se pusieron a laburar!! Salio el Java Plugin de 64 bits!!!!!

[Java Plugin 64 bits](http://www.tecnoayuda.com.ar/viewtopic.php?f=3&p=106#p106)[(Noticia Original)](http://www.theinquirer.es/2008/12/18/primero-flash-luego-wine-y-ahora-java-64bits-en-linux.html)

[Descarga del JRE 6 - 12](https://jdk6.dev.java.net/6uNea.html)

PD: Al parecer salio el 12 pero recién hoy me entero!

Ahora es donde vengo a pedir una consulta, no logro configurar el plugin en mi firefox!!! Descargue el bin, los desenpaquete y movi la carpeta al /urs/lib/jvm Pero no logro configurar el plugin, alguna idea de como pueda hacerlo????

Edito:

Bueno, segui luchando y encontre la solucion a mi problema, aca les dejo el paso a paso que hice para poder utilizar el plugin de java

1º Descargar el .bin
2º ir a un terminal y ejecutar
```
sudo ./jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin
```
3º Mover la carpeta
```
sudo mv jre1.6.0_12/ /usr/lib/jvm
```
4º Crear un link para el plugin de java
```
cd /usr/lib64/firefox-addons/plugins
sudo ln -s /usr/lib/jvm/jre1.6.0_12/lib/amd64/libnpjp2.so
```
5º Reiniciar firefox e ir a [about:plugins](about:plugins) y verificar al final que este el plugin java
6º Para mayor seguridad a ver si funciona vayan a [Test de java](http://www.java.com/en/download/help/testvm.xml)

Listo son 6 pasos(descontando las pruebas son 4)

---

### Post by kulight on 2008-12-18
can u please do that again 
in English

thank u very much

---

### Post by santiagoward2000 on 2008-12-18
Muy bueno! Tal vez la próxima vez instale Ubuntu 64bits.
Gracias!

---

### Post by z37a on 2008-12-18
> **kulight said:**
> can u please do that again 
in English

thank u very much

I regret it but is not very good English, and might write anything. Perhaps one can translate this guide, anything using the tools of the language of google, so I wrote this message.

[Link to Google translate](http://translate.google.com)

---

### Post by c4d0rn4 on 2008-12-18
existe alguna mejoria de rendimiento entre 32 y 64 bits sin tener más de 4 gigas de ram?

Sí, totalmente colgado! jaja xD, pero tenía entendido que ese plugin era una de las pocas cositas que le faltaba a linux en 64 bits.

________________________

Edit: 

te lo traduzco z37a =P (le borre un paso jaja xD)
> 
[Java Plugin 64 bits]("http://www.tecnoayuda.com.ar/viewtopic.php?f=3&p=106#p106")[(Noticia Original)]("http://www.theinquirer.es/2008/12/18/primero-flash-luego-wine-y-ahora-java-64bits-en-linux.html")

[**DOWNLOAD JRE 6 - 12**]("https://jdk6.dev.java.net/6uNea.html")

1º Download the .bin file
2º In the terminal execute
```
sudo ./jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin 
```
3º Move the folder
```
sudo mv jre1.6.0_12/ /usr/lib/jvm 
```
4º Create a link for the java's plugin
```
cd /usr/lib64/firefox-addons/plugins
sudo ln -s /usr/lib/jvm/jre1.6.0_12/lib/amd64/libnpjp2.so 
```
5º Restart Firefox and type in your address bar **about:plugins** and verify that java's plugin is there.
6ºAnd finally check out if it's working: [Test de java]("http://www.java.com/en/download/help/testvm.xml")


---

### Post by z37a on 2008-12-18
> **c4d0rn4 said:**
> existe alguna mejoria de rendimiento entre 32 y 64 bits sin tener más de 4 gigas de ram?

Sí, totalmente colgado! jaja xD, pero tenía entendido que ese plugin era una de las pocas cositas que le faltaba a linux en 64 bits.

En mi caso particular era lo único que me faltaba nada mas!!! Ya puedo utilizar tranquilo los 64 bits en todas mis pcs(bue 1 sola, tengo la laptop y otra mas que no tienen 64 bits, bue la laptop si, peor el em64t anda muy mal en los celeron!!!)

---

### Post by kulight on 2008-12-18
> **c4d0rn4 said:**
> existe alguna mejoria de rendimiento entre 32 y 64 bits sin tener más de 4 gigas de ram?

Sí, totalmente colgado! jaja xD, pero tenía entendido que ese plugin era una de las pocas cositas que le faltaba a linux en 64 bits.

________________________

Edit: 

te lo traduzco z37a =P (le borre un paso jaja xD)

thank you for the english
that worked for me

---

