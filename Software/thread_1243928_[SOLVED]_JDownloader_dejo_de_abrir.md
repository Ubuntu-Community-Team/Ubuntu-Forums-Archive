---
title: "[SOLVED] JDownloader dejo de abrir"
date: 2009-08-18
forum: Software
---

### Post by losoollenos on 2009-08-18
Hola cómo andan tod@s?
Bueno la cuestión es que jdownloader no abrió más de buenas a primeras......andaba bien. La única forma es desde el archivo jdupdate.jar que está dentro de la carpeta del jd, primero actualiza (que dicho sea de paso me re llama la atención que hace rato no descarga ninguna, cuando normalmente eran varias por semana) y después abre el programa.
Si intento desde terminal me da este error:

ubuntu@ubuntu-desktop:~$ cd /home/ubuntu/JDownloader
ubuntu@ubuntu-desktop:~/JDownloader$ java -jar JDownloader.jar
18/08/2009 23:19:39 - INFO [jd.Main(main)] -> Start JDownloader
18/08/2009 23:19:40 - ADVERTENCIA [jd.Main(heapCheck)] -> Heapcheck: Not enough heap. use: java -Xmx512m -jar JDownloader.jar
JAR
18/08/2009 23:19:40 - LA MÁS FINA [jd.utils.JDUtilities(getJDClassLoader)] -> Create Classloader: for: /home/ubuntu/JDownloader
18/08/2009 23:19:40 - LA MÁS FINA [jd.JDClassLoader(<init>)] -> rootDir:/home/ubuntu/JDownloader
/home/ubuntu/JDownloader
 file:/home/ubuntu/JDownloader/jd
18/08/2009 23:19:40 - MÁS FINA [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/ubuntu/JDownloader/plugins/JDChat.jar
18/08/2009 23:19:40 - MÁS FINA [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/ubuntu/JDownloader/plugins/JDShutdown.jar
18/08/2009 23:19:40 - MÁS FINA [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/ubuntu/JDownloader/plugins/JDTray.jar
18/08/2009 23:19:40 - MÁS FINA [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/ubuntu/JDownloader/plugins/JDHJMerge.jar
18/08/2009 23:19:40 - MÁS FINA [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/ubuntu/JDownloader/plugins/JDUnrar.jar
18/08/2009 23:19:40 - MÁS FINA [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/ubuntu/JDownloader/JDownloader.jar
18/08/2009 23:19:40 - INFO [jd.Main(main)] -> init Eventmanager
18/08/2009 23:19:40 - MÁS FINA [jd.config.DatabaseConnector(<init>)] -> Loading database
18/08/2009 23:19:40 - MÁS FINA [jd.config.DatabaseConnector(checkDatabaseHeader)] -> Checking database
Loaded language: english
18/08/2009 23:19:41 - INFO [jd.Main(main)] -> init Localisation
Exception in thread "main" java.lang.NullPointerException
	at jd.Main.increaseSplashStatus(Unknown Source)
	at jd.Main.main(Unknown Source)
ubuntu@ubuntu-desktop:~/JDownloader$ 

Que puede ser???

Muchas gracias

---

### Post by josecuervo86 on 2009-08-18
Parece que es un error bastante común. Aca [0] proponen una solución que funciono para alguien que tenia el mismo problema

[0] [http://blogdrake.net/consulta/jdownloader-no-se-ejecuta](http://blogdrake.net/consulta/jdownloader-no-se-ejecuta)

---

### Post by losoollenos on 2009-08-18
Gracias josecuervo86, mirá que anduve buscando ehhh.........
Y qué es lo que cambió que ahora hay que agregar este -Xmx512m ?

Saludos y muchas gracias

---

### Post by josecuervo86 on 2009-08-18
Mira, toco de oido nomas pero segun lo que lei es debido a las actualizaciones (?) Que bueno que te haya resultado!

---

### Post by losoollenos on 2009-08-19
Es rarísimo lo de la falta de actualizaciones, los de JD eran superactivos en ese sentido, por suerte sigue funcionando muy bien.
Nuevamente muchas gracias y hasta la próxima!!!
claudio

---

