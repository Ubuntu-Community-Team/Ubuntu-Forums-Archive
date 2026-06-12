---
title: "Como instalar Java Gui para R"
date: 2010-09-21
forum: Software
---

### Post by guillejcopello on 2010-09-21
Buenas, quiero instalar la interface gráfica Java Gui para R (JGR) para poder usar el programa de estadísticas R ya que no tengo idea como hacerlo correr en la terminal.
Estoy siguiendo los pasos  que aparecen en: [http://www.rforge.net/JGR/linux.html](http://www.rforge.net/JGR/linux.html)
El problema es el siguiente, me dan las siguientes indiaciones:
 In general installing JGR on any unix system is simple, you need 

[LIST]
[*]R with shared library (libR.so) and developer files
[*]JDK 1.4 or higher (>=1.5 recommended)
[/LIST]
 Then simply run as root: R CMD javareconf R    install.packages('JGR')
library(JGR)
JGR()

La cuestion es que no se si tengo R con libreria compartida (tampoco se como hacerlo) y no se si tengo developer files.
Por otra parte llego hasta install.packages y pasa lo siguiente:
>install.packages('JGR')
Aviso en install.packages("JGR") :
 argument 'lib' is missing: using '/home/guille/R/i486-pc-linux-gnu-library/2.10'

A lo que me pide que elija un mirror (elijo Chile o Brasil) y al final de todo el texto dice lo siguiente:

Error : package 'rJava' required by 'JGR' could not be found
ERROR: lazy loading failed for package ‘JGR’
* removing ‘/home/guille/R/i486-pc-linux-gnu-library/2.10/JGR’

The downloaded packages are in
    ‘/tmp/RtmpTSuG6Z/downloaded_packages’
Mensajes de aviso perdidos
1: In install.packages("JGR") :
  installation of package 'rJava' had non-zero exit status
2: In install.packages("JGR") :
  installation of package 'JavaGD' had non-zero exit status
3: In install.packages("JGR") :
  installation of package 'iplots' had non-zero exit status
4: In install.packages("JGR") :
  installation of package 'JGR' had non-zero exit status

¿Alguien tiene idea de como hacer para instalar la interface gráfica?

Gracias

Guille

---

### Post by lkjoel on 2010-09-21
> **guillejcopello said:**
> Buenas, quiero instalar la interface gráfica Java Gui para R (JGR) para poder usar el programa de estadísticas R ya que no tengo idea como hacerlo correr en la terminal.
Estoy siguiendo los pasos  que aparecen en: [http://www.rforge.net/JGR/linux.html](http://www.rforge.net/JGR/linux.html)
El problema es el siguiente, me dan las siguientes indiaciones:
 In general installing JGR on any unix system is simple, you need 

[LIST]
[*]R with shared library (libR.so) and developer files
[*]JDK 1.4 or higher (>=1.5 recommended)
[/LIST]
 Then simply run as root: R CMD javareconf R    install.packages('JGR')
library(JGR)
JGR()

La cuestion es que no se si tengo R con libreria compartida (tampoco se como hacerlo) y no se si tengo developer files.
Por otra parte llego hasta install.packages y pasa lo siguiente:
>install.packages('JGR')
Aviso en install.packages("JGR") :
 argument 'lib' is missing: using '/home/guille/R/i486-pc-linux-gnu-library/2.10'

A lo que me pide que elija un mirror (elijo Chile o Brasil) y al final de todo el texto dice lo siguiente:

Error : package 'rJava' required by 'JGR' could not be found
ERROR: lazy loading failed for package ‘JGR’
* removing ‘/home/guille/R/i486-pc-linux-gnu-library/2.10/JGR’

The downloaded packages are in
    ‘/tmp/RtmpTSuG6Z/downloaded_packages’
Mensajes de aviso perdidos
1: In install.packages("JGR") :
  installation of package 'rJava' had non-zero exit status
2: In install.packages("JGR") :
  installation of package 'JavaGD' had non-zero exit status
3: In install.packages("JGR") :
  installation of package 'iplots' had non-zero exit status
4: In install.packages("JGR") :
  installation of package 'JGR' had non-zero exit status

¿Alguien tiene idea de como hacer para instalar la interface gráfica?

Gracias

Guille
I think that for your own sake, you should translate that into english.

---

### Post by Jesus_Valdez on 2010-09-21
Hola, mira, las instrucciones que debieras de estar siguiendo son las que aparecen mas abajo de la pantalla.

Primero agregar una fuente a tu repositorio:


To obtain the latest R packages, add an entry like

   deb http://<my.favorite.cran.mirror>/bin/linux/ubuntu lucid/

in your /etc/apt/sources.list file, replacing <my.favorite.cran.mirror> by the actual URL of your favorite CRAN mirror. See [http://cran.r-project.org/mirrors.html](http://cran.r-project.org/mirrors.html) for the list of CRAN mirrors. To install the complete R system, use

   sudo apt-get update
   sudo apt-get install r-base

__________
En otra parte recomeinda instalar estos paquetes tambien:


sudo apt-get install r-base-dev r-recommended


Despues instalas lo demas:

Install Java Development Kit
Make sure you have enabled the multiverse above (run sudo apt-get update if necessary) and run:
sudo apt-get install sun-java6-jdk

If you have more than one Java version installed, set the Sun version as default, e.g.:
sudo update-java-alternatives -s java-1.6.0-sun

Enable Java support in R
Run:
sudo R CMD javareconf
Install JGR
Run R as root via sudo R and type:
install.packages('JGR')
library(JGR)
JGR()

---

### Post by s.fox on 2010-09-22
Thread moved after PM exchange with OP.

---

### Post by guillejcopello on 2010-09-22
Gracias Jesus,
El problema es que uso este sistema operativo por primera vez en mi vida y mis dudas son muuuyyy básicas.
Por ejemplo no se como agregar la entrada deb http...... como indican abajo.
To obtain the latest R packages, add an entry like
deb http://<my.favorite.cran.mirror>/bin/linux/ubuntu lucid/
in your /etc/apt/sources.list file, replacing  <my.favorite.cran.mirror> by the actual URL of your favorite CRAN  mirror. See [http://cran.r-project.org/mirrors.html](http://cran.r-project.org/mirrors.html) for the list of CRAN mirrors. 

Por otro lado instale todo lo que en el gestor de paquetes Synaptic aparece como JDK (Java Development Kit).
Pero no se como abilitar el "multiverse" que indican acá:
Make sure you have enabled the multiverse above (run sudo apt-get update if necessary) and run:
sudo apt-get install sun-java6-jdk
Luego de correr esto me dice que esta actualizado en su versión más reciente.
Por último:
If you have more than one Java version installed, set the Sun version as default, e.g.:
sudo update-java-alternatives -s java-1.6.0-sun
A lo que la terminal responde:
update-java-alternatives: directory does not exist: /usr/lib/jvm/java-1.6.0-sun

Seguramente sea una pavada pero ignoro como resolverla.
Gracias

Guille

---

### Post by Morpholinux on 2010-10-11
Text in english
> texto en español

Hi i am also have some problems installing JGR...
>Hola yo también tengo problemas intalando JGR...
I was doing that to install Deducer...which looks very nice..
>Estaba haciendo eso para instalar Deducer...que se ve bastante bien


anyway I knew that Ubuntu wasn't using sun's JDK... so the instructions here ..[http://rforge.net/JGR/linux.html](http://rforge.net/JGR/linux.html) I think were a bit outdated... finally I found this
[http://www.seancsb.net/statistical/installing-jgr-and-deducer](http://www.seancsb.net/statistical/installing-jgr-and-deducer)
 
>de cualquier manera..Sabía que Ubuntu no estaba usando el JDK de sun... >así que las instrucciones de aquí [http://rforge.net/JGR/linux.html](http://rforge.net/JGR/linux.html) yo >pienso, están algo viejas
>finalmente encontré esta página
>[http://www.seancsb.net/statistical/installing-jgr-and-deducer](http://www.seancsb.net/statistical/installing-jgr-and-deducer)

As you can see, step number 3 makes the installation of openjdk 6
sudo apt-get install openjdk-6-jdk ## Ubuntu no longer uses Sun's JDK

>como se ve en el paso número 3.
>se instala openJDK 
>sudo apt-get install openjdk-6-jdk ## Ubuntu no longer uses Sun's JDK

the problem is that I cannot pass thru step number 6
>El problema es que  no puedo avanzar más allá del paso número 6
ERROR: configuration failed for package ‘JavaGD’
* removing ‘/usr/local/lib/R/site-library/JavaGD’
ERROR: dependencies ‘rJava’ are not available for package ‘iplots’
* removing ‘/usr/local/lib/R/site-library/iplots’
ERROR: dependencies ‘rJava’, ‘JavaGD’, ‘iplots’ are not available for package ‘JGR’
* removing ‘/usr/local/lib/R/site-library/JGR’

The downloaded packages are in
	‘/tmp/RtmpStnjqa/downloaded_packages’
Mensajes de aviso perdidos
1: In install.packages("JGR", dep = T) :
  installation of package 'rJava' had non-zero exit status
2: In install.packages("JGR", dep = T) :
  installation of package 'JavaGD' had non-zero exit status
3: In install.packages("JGR", dep = T) :
  installation of package 'iplots' had non-zero exit status
4: In install.packages("JGR", dep = T) :
  installation of package 'JGR' had non-zero exit status
> q()
Save workspace image? [y/n/c]: n


I have ..almost the same as [http://www.seancsb.net/statistical/installing-jgr-and-deducer](http://www.seancsb.net/statistical/installing-jgr-and-deducer)
>tengo básicamente lo mismo que [http://www.seancsb.net/statistical/installing-jgr-and-deducer](http://www.seancsb.net/statistical/installing-jgr-and-deducer)
murpholinox@eva00:~$  cat /etc/issue.net
Ubuntu 10.04.1 LTS
murpholinox@eva00:~$ uname -srvm
Linux 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010 i686

 
murpholinox@eva00:~$ cat /etc/apt/sources.list
bunchoflines......
>montóndelíneas......
#R
deb [http://cran.r-project.org/bin/linux/ubuntu/](http://cran.r-project.org/bin/linux/ubuntu/) lucid/



And also I think I have the multiverse stuff enabled
>Y creo que lo del multiverse lo tengo puesto
murpholinox@eva00:~$ cat /etc/apt/sources.list |grep multiverse
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) lucid multiverse universe #Added by software-properties
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) lucid-updates restricted main multiverse universe #Added by software-properties
## multiverse WILL NOT receive any review or updates from the Ubuntu
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
# deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) lucid-security restricted main multiverse universe #Added by software-properties
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) lucid-security multiverse


so...why it doesn't work?

>entonces por qué no funciona?

sorry if this is too long
>perdón si esto es demasiado largo

---

