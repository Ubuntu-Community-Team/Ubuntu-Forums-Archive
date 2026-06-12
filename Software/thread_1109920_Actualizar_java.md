---
title: "Actualizar java"
date: 2009-03-29
forum: Software
---

### Post by losoollenos on 2009-03-29
Hola cómo andan?
Quisiera saber cómo se podría actualizar java desde repositores en Ubuntu 8.04. Yo lo instalé con el paquete ubuntu-restricted-extras que trae el java update 7 y en la página oficial se puede bajar el update 13. No es que me funcione algo mal (que yo sepa), sólo me gustaría saber hacerlo......
Lo que pude encontrar buscando por google es cómo instalarlo descargándolo de java, pero nada de si es posible "actualizarlo" desde repositores.  

Muchas gracias y saludos para tod@s !!!!

---

### Post by Hei Ku on 2009-03-29
Los repositorios de Ubuntu 8.04 solo se actualizan por razones de seguridad. Así que, excepto que encuentren un bug de seguridad en la versión que esta en los repositorios, se va a quedar esa version mientras dure el soporte del 8.04.

---

### Post by losoollenos on 2009-03-29
Muchas gracias; y repositores no oficiales?

---

### Post by Hei Ku on 2009-03-29
Puede ser que haya, pero en ese caso por que no actualizas directo a Intrepid?

---

### Post by losoollenos on 2009-03-29
Porque me anda mejor la 8.04......a vos no?

---

### Post by Hei Ku on 2009-03-29
Si anda, no lo toques! ;)

En mi caso, yo uso la 8.04 porque desarrollo en KDE3. Pero en cuanto empecemos a migrar a KDE4 me cambio a una versión actualizada.

---

### Post by pablo.s on 2009-03-30
Yo sufro de [versionitis]("http://www.medialifemagazine.com/cgi-bin/artman/exec/view.cgi?archive=226&num=5439"). No tiene cura al parecer.

---

### Post by losoollenos on 2009-03-30
Ok...

Saludos y hasta ponto

---

### Post by losoollenos on 2009-03-30
Pablo, lamento no poder comprender las explicaciones de tu problema en inglés, pero para solucionar cualquier problema, ante todo, uno debe planteárselo de forma integral y no tratar de simplificarlo monocausalmente, fijate bien......de onda !!!!

---

### Post by pablo.s on 2009-03-30
A ver, voy a plantearlo de forma integral:

En la página de Sun está el binario de la versión 6 update 13 como vos dijiste.
En el repositorio multiverse de Jaunty está la [versión 6 update 12]("http://packages.ubuntu.com/jaunty/sun-java6-bin"). Si tenés
la necesidad de bajarlo ya ya ya mismo, dale, pero tiene dependencias con
otros paquetes complementarios de Java. Esto puede hacer que no te funcione
al final, dado que vos estás con Hardy.
La versionitis es (supuestamente) una enfermedad consistente en la dependencia
del enfermo por todo lo último que salió, o las ultimas versiones de cada
programa. Yo lo comentaba mitad en serio mitad en broma. No lo entendiste.
Equivocación mia. Todo bien. Saludos.

---

### Post by losoollenos on 2009-03-30
Como hablaste de sufrir de "un" problema te sugerí que no seas monocausalmente simplista.....no importa.
Y si fuera como te apresuraste en juzgarme enfermo de tener lo "último" no estaría con hardy, usaría intrepid o la beta 9.04 no?
Pero no tuviste en cuenta mis últimos post dónde consulté sobre algunos problemas con programas que usan java, concretamente el JDownloader, y como no soy ni me creo más que un novato consulto, pruebo, busco así solucionar mis problemas.
Si la actitud que tuviste te sirve, dale para adelante......pero claro que no aporta nada.

Y perdón por salir del hilo del post, pero no fue culpa mía.

saludos

---

### Post by pablo.s on 2009-03-30
Probaste con [FreeRapid]("http://wordrider.net/freerapid")? Para mi es mejor que JDownloader.
Haya paz, haya paz...

---

### Post by losoollenos on 2009-03-30
No lo conozco, lo voy a tener en cuenta.......gracias.
Todo bien.....

---

### Post by NickCis on 2009-03-30
Igual el FreeRapid sigue siendo java.
Intente probarlo pero al ejecutar "java -jar frd.jar" en la carpeta donde esta me devuelve este error:
```
newpc@ubuntu-newpc:~/jdownloader/FreeRapid-0.81$ java -jar frd.jar
Exception in thread "main" java.lang.UnsupportedClassVersionError: Bad version number in .class file
	at java.lang.ClassLoader.defineClass2(Native Method)
	at java.lang.ClassLoader.defineClass(Unknown Source)
	at java.security.SecureClassLoader.defineClass(Unknown Source)
	at java.net.URLClassLoader.defineClass(Unknown Source)
	at java.net.URLClassLoader.access$100(Unknown Source)
	at java.net.URLClassLoader$1.run(Unknown Source)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(Unknown Source)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at sun.misc.Launcher$AppClassLoader.loadClass(Unknown Source)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at java.lang.ClassLoader.loadClassInternal(Unknown Source)
newpc@ubuntu-newpc:~/jdownloader/FreeRapid-0.81$ 

```

Alguna idea?.

Offtopic: Alguien sabe como hacer andar el Trayicon plugin para el jdownloader?.

Saludos.

---

### Post by pablo.s on 2009-03-30
Escribi en una terminal

     sudo update-alternatives --config java

y probalo.

---

### Post by NickCis on 2009-03-30
Sigue pasando lo mismo, (no entendi bienq ue tengo que hacer despues de poner ese comando en terminal), adjunto la salida:
```
newpc@ubuntu-newpc:~/jdownloader/FreeRapid-0.81$ sudo update-alternatives --config java

Hay 2 alternativas que proveen `java'.

  Selección     Alternativa
-----------------------------------------------
          1    /usr/lib/jvm/java-6-sun/jre/bin/java
*+        2    /usr/lib/j2re1.5-sun/bin/java

Pulse <Intro> para mantener el valor por omisión [*] o pulse un número de selección: 
newpc@ubuntu-newpc:~/jdownloader/FreeRapid-0.81$ java -jar frd.jarException in thread "main" java.lang.UnsupportedClassVersionError: Bad version number in .class file
	at java.lang.ClassLoader.defineClass2(Native Method)
	at java.lang.ClassLoader.defineClass(Unknown Source)
	at java.security.SecureClassLoader.defineClass(Unknown Source)
	at java.net.URLClassLoader.defineClass(Unknown Source)
	at java.net.URLClassLoader.access$100(Unknown Source)
	at java.net.URLClassLoader$1.run(Unknown Source)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(Unknown Source)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at sun.misc.Launcher$AppClassLoader.loadClass(Unknown Source)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at java.lang.ClassLoader.loadClassInternal(Unknown Source)
newpc@ubuntu-newpc:~/jdownloader/FreeRapid-0.81$ 

```

Edit: Al poner el numero 1 (cuando te pedi ese numero o pulse intro) se soluciono el problema.

---

### Post by pablo.s on 2009-03-30
Bueno, quise ver si estabas atento a ver que te daba
a elegir las dos versiones... Vos ya estas bastante
curtido papá...
Saludos.

---

### Post by |Porsche on 2009-03-30
Porque no instalas la ultima versión de Java sin depender de los supositorios de ubunut?

Lo único que no me gusta de Ubuntu es que se tardan tanto en sacar nuevos programas. A veces hasta los que tienen bichos no los actualizan.

---

### Post by pablo.s on 2009-03-30
> **|Porsche said:**
> Porque no instalas la ultima versión de Java sin depender de los supositorios de ubunut?

Uh, yo me salgo de esta cosa, hay que usar supositorios y nadie
me avisó nada!

> Lo único que no me gusta de Ubuntu es que se tardan tanto en sacar nuevos programas. A veces hasta los que tienen bichos no los actualizan.

No te creas que tardan en sacar nuevos programas. ¡Al dia siguiente 
que fué lanzado GNOME 2.26 ya estaba para ser instalado!

---

### Post by NickCis on 2009-03-31
Los REpositorios de Ubuntu no es que estan atrasados, si no que cuando no es necesaria una actualizacion (mas para las verciones mas viejas), no la sacan, por que todo funciona como esta. Actualizar todos los paquetes, constantemente, ademas de consumir mucho tiempo, es algo que puede generar problemas, por que tambien va haber que actualizar las dependencias etc/etc...

Ontopic: el problema que me paso a mi, segun entiendo ahora, es por que el freerapid requiere java 1.6. No entiendo por que yo tenia instalado tambien el 1.5, y tenia configurado para usar ese :S. Algo raro, pero bueh,,,

Saludos.

---

### Post by losoollenos on 2009-04-01
Bueno, comento que estoy sorprendido con este FreeRapid, es muy rápido, sencillo (si bien carece de algunos chiches del JDownloader, como la reconexión automática, la descompresión de archivos y otros) y si no hace boludeces puede tranquilamente reemplazar al jdownloader.
Lo voy a seguir probando......

saludos

---

