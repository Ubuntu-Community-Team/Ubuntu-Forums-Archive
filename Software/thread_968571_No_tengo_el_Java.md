---
title: "No tengo el Java"
date: 2008-11-02
forum: Software
---

### Post by PeTTi on 2008-11-02
No tengo Java, y lo quiero instalar y no entiendo nada.. y hago lo que dice las instrucciones y cuando entro a la terminal y pongo su y pongo la pass me dice fallo de autenticacion :S

El link para instalarlo es [este]("http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80").
Gracias.

---

### Post by pol666 on 2008-11-02
el java viene en el restricted.

sudo apt-get install ubuntu-restricted-extras

---

### Post by Joeb454 on 2008-11-02
Se puede instalar con ```
sudo apt-get install sun-java6-bin
```

---

### Post by PeTTi on 2008-11-02
> **pol666 said:**
> el java viene en el restricted.

sudo apt-get install ubuntu-restricted-extras

> **Joeb454 said:**
> Se puede instalar con ```
sudo apt-get install sun-java6-bin
```
Hice las dos cosas y sigue igual :S
Y no es error de la página porque con la otra pc que tenía Ubuntu funcionaba bien.

---

### Post by c4d0rn4 on 2008-11-02
> **PeTTi said:**
> No tengo Java, y lo quiero instalar y no entiendo nada.. y hago lo que dice las instrucciones y cuando entro a la terminal y_ pongo su y pongo la pass me dice **fallo de autenticacion**_:S


Quien te dice fallo de autenticación? la terminal después del sudo? todo tu quilmobo me parece viene por acá.

su es la pass del root
sudo es la pass de tu usuario

ejecutá los comandos que te dan con sudo, ahí si te va a aceptar tu pass. Tenés un problema con la pass del su, no se como se rescata.

---

### Post by PeTTi on 2008-11-03
> **c4d0rn4 said:**
> Quien te dice fallo de autenticación? la terminal después del sudo? todo tu quilmobo me parece viene por acá.

su es la pass del root
sudo es la pass de tu usuario

ejecutá los comandos que te dan con sudo, ahí si te va a aceptar tu pass. Tenés un problema con la pass del su, no se como se rescata.
En Usuarios y grupos le puse una contraseña, asi que después intento, ahora me voy a dormir porque mañana tengo que ir al colegio :S

Gracias.

---

### Post by PeTTi on 2008-11-03
nah@lore-laptop:~$ su
Contraseña: 
root@lore-laptop:/home/nah# cd
root@lore-laptop:~# cd/usr/java
bash: cd/usr/java: No existe el fichero ó directorio
root@lore-laptop:~# cd/nah/java
bash: cd/nah/java: No existe el fichero ó directorio


:S

---

### Post by c4d0rn4 on 2008-11-03
> **PeTTi said:**
> nah@lore-laptop:~$ su
Contraseña: 
root@lore-laptop:/home/nah# cd
root@lore-laptop:~# cd/usr/java
bash: cd/usr/java: No existe el fichero ó directorio
root@lore-laptop:~# cd/nah/java
bash: cd/nah/java: No existe el fichero ó directorio


:S
Güat de foc?! jajaj xD

Lo que pensé que era la contraseña no es, te podés loguear como root.

La verdad no se que es lo que querés hacer con 
*cd/nah/java*, pero te aviso que debés dejar un espacio después del cd para cambiar de carpeta.

```
cd /nah/java 
```

contá que querés hacer, la verdad no se a que viene ese intento de buscar esa carpeta.

---

### Post by PeTTi on 2008-11-04
> **c4d0rn4 said:**
> Güat de foc?! jajaj xD

Lo que pensé que era la contraseña no es, te podés loguear como root.

La verdad no se que es lo que querés hacer con 
*cd/nah/java*, pero te aviso que debés dejar un espacio después del cd para cambiar de carpeta.

```
cd /nah/java 
```contá que querés hacer, la verdad no se a que viene ese intento de buscar esa carpeta.
root@Nah-Ubuntu:~# cd /nah/java
bash: cd: /nah/java: No existe el fichero ó directorio


Lo que quiero hacer es jugar al truco en una página y cuando voy a jugar me dice eso de que tengo qeu isntalar Java y me manda a un link de Java, y en las intrucciones del Java dice eso es usr/java..

---

### Post by PeTTi on 2008-11-05
Entonces no hay forma? :(

---

### Post by pol666 on 2008-11-05
que raro, te referis al truco Taringa.

Yo lo usé y me anda genial

---

### Post by c4d0rn4 on 2008-11-06
petti, por curiosidad, abrí la consola y poné

```
java
```

dale enter y decí que resultado te da.

---

### Post by PeTTi on 2008-11-06
> **c4d0rn4 said:**
> petti, por curiosidad, abrí la consola y poné

```
java
```dale enter y decí que resultado te da.

nah@lore-laptop:~$ java
Usage: java [-options] class [args...]
           (to execute a class)
   or  java [-options] -jar jarfile [args...]
           (to execute a jar file)

where options include:
    -d32          use a 32-bit data model if available

    -d64          use a 64-bit data model if available
    -client      to select the "client" VM
    -server      to select the "server" VM
    -hotspot      is a synonym for the "client" VM  [deprecated]
                  The default VM is client.
                  
    -cp <class search path of directories and zip/jar files>
    -classpath <class search path of directories and zip/jar files>
                  A : separated list of directories, JAR archives,
                  and ZIP archives to search for class files.
    -D<name>=<value>
                  set a system property
    -verbose[:class|gc|jni]
                  enable verbose output
    -version      print product version and exit
    -version:<value>
                  require the specified version to run
    -showversion  print product version and continue
    -jre-restrict-search | -jre-no-restrict-search
                  include/exclude user private JREs in the version search
    -? -help      print this help message
    -X            print help on non-standard options
    -ea[:<packagename>...|:<classname>]
    -enableassertions[:<packagename>...|:<classname>]
                  enable assertions
    -da[:<packagename>...|:<classname>]
    -disableassertions[:<packagename>...|:<classname>]
                  disable assertions
    -esa | -enablesystemassertions
                  enable system assertions
    -dsa | -disablesystemassertions
                  disable system assertions
    -agentlib:<libname>[=<options>]
                  load native agent library <libname>, e.g. -agentlib:hprof
                    see also, -agentlib:jdwp=help and -agentlib:hprof=help
    -agentpath:<pathname>[=<options>]
                  load native agent library by full pathname
    -javaagent:<jarpath>[=<options>]
                  load Java programming language agent, see java.lang.instrument
    -splash:<imagepath>
                  show splash screen with specified image

[QUOTE=pol66]que raro, te referis al truco Taringa.

Yo lo usé y me anda genial 	[/QUOTE]
En otra pc con Ubuntu 8.04 andaba re bien..

---

### Post by c4d0rn4 on 2008-11-06
la verdad pensé que no tenías instalado java.
Fijate si tenés el plugin de java para firefox, es lo unico que faltaría. A lo que querés acceder es a un java en internet en una página, no?

[[IMG]http://img47.imageshack.us/img47/5607/javacl8.th.png[/IMG]](http://img47.imageshack.us/my.php?image=javacl8.png)[[IMG]http://img47.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

fijate si tenés esos paquetes instalados en el synaptic, y si firefox reconoce el plug-in (tools->add-ons->sección plug-ins)

---

### Post by PeTTi on 2008-11-07
> **c4d0rn4 said:**
> la verdad pensé que no tenías instalado java.
Fijate si tenés el plugin de java para firefox, es lo unico que faltaría. A lo que querés acceder es a un java en internet en una página, no?

[[IMG]http://img47.imageshack.us/img47/5607/javacl8.th.png[/IMG]]("http://img47.imageshack.us/my.php?image=javacl8.png")[[IMG]http://img47.imageshack.us/images/thpix.gif[/IMG]]("http://g.imageshack.us/thpix.php")

fijate si tenés esos paquetes instalados en el synaptic, y si firefox reconoce el plug-in (tools->add-ons->sección plug-ins)
Instale los que se ven en el screenshot que tenés ahi y no paso nada, pero despues instale todo lo que comenzaba con Java (Casi 1 GB Instalé) y funciona.
Gracias a todos :D

---

### Post by vampichoke on 2008-11-07
yo tengo un problema parecido con los juegos de yahoo. (imagen 1)


busque seguir los mismos pasos a ver si se solucionaba.. por q parece ser el mismo problema... pero no tengo esa opcion sun-java6-plugin en synaptic (imagen2)


=/

---

### Post by PeTTi on 2008-11-13
> **vampichoke said:**
> yo tengo un problema parecido con los juegos de yahoo. (imagen 1)


busque seguir los mismos pasos a ver si se solucionaba.. por q parece ser el mismo problema... pero no tengo esa opcion sun-java6-plugin en synaptic (imagen2)


=/

Fijate abriendo [esto]("apt:/sun-java6-plugin") si podés.

---

### Post by vampichoke on 2008-11-14
> **PeTTi said:**
> Fijate abriendo [esto]("apt:/sun-java6-plugin") si podés.

[B]No se encuantra <<sun-java6-plugin>>
[/B]
y ahora...?
[B]
mi terminal por las dudas.[/B]

> mariano@mariano-desktop:~$ java
Usage: java [-options] class [args...]
           (to execute a class)
   or  java [-options] -jar jarfile [args...]
           (to execute a jar file)
where options include:
    -d32	  use a 32-bit data model if available
    -d64	  use a 64-bit data model if available
    -server	  to select the "server" VM
                  The default VM is server.

    -cp <class search path of directories and zip/jar files>
    -classpath <class search path of directories and zip/jar files>
                  A : separated list of directories, JAR archives,
                  and ZIP archives to search for class files.
    -D<name>=<value>
                  set a system property
    -verbose[:class|gc|jni]
                  enable verbose output
    -version      print product version and exit
    -version:<value>
                  require the specified version to run
    -showversion  print product version and continue
    -jre-restrict-search | -jre-no-restrict-search
                  include/exclude user private JREs in the version search
    -? -help      print this help message
    -X            print help on non-standard options
    -ea[:<packagename>...|:<classname>]
    -enableassertions[:<packagename>...|:<classname>]
                  enable assertions with specified granularity
    -da[:<packagename>...|:<classname>]
    -disableassertions[:<packagename>...|:<classname>]
                  disable assertions with specified granularity
    -esa | -enablesystemassertions
                  enable system assertions
    -dsa | -disablesystemassertions
                  disable system assertions
    -agentlib:<libname>[=<options>]
                  load native agent library <libname>, e.g. -agentlib:hprof
                  see also, -agentlib:jdwp=help and -agentlib:hprof=help
    -agentpath:<pathname>[=<options>]
                  load native agent library by full pathname
    -javaagent:<jarpath>[=<options>]
                  load Java programming language agent, see java.lang.instrument
    -splash:<imagepath>
                  show splash screen with specified image
See [http://java.sun.com/javase/reference](http://java.sun.com/javase/reference) for more details.


---

### Post by fmsismo on 2008-11-14
En ubuntu 64 bit no esta el plugin de java.

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=sun-java6-plugin](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=sun-java6-plugin)

No busque, pero seguro hay alguna alternativa para salvar esto.

---

### Post by vampichoke on 2008-11-14
aaaahhhhhh

era por mi 64bits ubuntu hardy maximun power version 


u.u) gueno... 



a jugar otra cosa ^^)

---

### Post by vampichoke on 2008-11-14
ahi estoy leyendo q el plugin de java para 64 recien empezarian a probarlo el año q viene...

q mientras se puede usar **icedtea6-plugin** (?)

alguien lo usa o me explica q onda.

(estoy actualizando a intrepid justo y no puedo entrar a synatic =)

---

