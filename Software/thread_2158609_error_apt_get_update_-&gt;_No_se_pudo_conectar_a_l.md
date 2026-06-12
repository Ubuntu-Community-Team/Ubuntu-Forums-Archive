---
title: "error apt get update -&gt; No se pudo conectar a localhost:9090:"
date: 2013-06-29
forum: Software
---

### Post by danin on 2013-06-29
buenas foreros, nunca he tenido mayores problemas con Ubuntu, pero esto me supera.

hace un tiempo no instalo aplicaciones pero ahora debo y al momento de querer instalar o hacer un update, me salen los errores siguientes:

```

danin@tanya-lnx:~$ sudo apt-get update
Err http://archive.ubuntu.com oneiric InRelease
  
Err http://archive.ubuntu.com oneiric-updates InRelease
  
Err http://archive.ubuntu.com oneiric-backports InRelease
  
Err http://archive.ubuntu.com oneiric-security InRelease
  
Err http://extras.ubuntu.com oneiric InRelease
  
Err http://linux.dropbox.com oneiric InRelease
  
Err http://dl.google.com stable InRelease
  
Err http://dl.google.com stable InRelease
  
Err http://archive.canonical.com oneiric InRelease
  
Err http://ppa.launchpad.net oneiric InRelease
  
Err http://archive.ubuntu.com oneiric Release.gpg
  No se pudo conectar a localhost:9090:
Err http://archive.ubuntu.com oneiric-updates Release.gpg
  No se pudo conectar a localhost:9090:
Err http://archive.ubuntu.com oneiric-backports Release.gpg
  No se pudo conectar a localhost:9090:
Err http://extras.ubuntu.com oneiric Release.gpg
  No se pudo conectar a localhost:9090:
Err http://dl.google.com stable Release.gpg
  No se pudo conectar a localhost:9090:
Err http://archive.canonical.com oneiric Release.gpg
  No se pudo conectar a localhost:9090:
Err http://ppa.launchpad.net oneiric Release.gpg
  No se pudo conectar a localhost:9090:
Err http://archive.ubuntu.com oneiric-security Release.gpg
  No se pudo conectar a localhost:9090:
Err http://dl.google.com stable Release.gpg
  No se pudo conectar a localhost:9090:
Err http://linux.dropbox.com oneiric Release.gpg
  No se pudo conectar a localhost:9090:
Leyendo listas de paquetes... Hecho
W: Imposible obtener http://archive.ubuntu.com/ubuntu/dists/oneiric/InRelease  

W: Imposible obtener http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/InRelease  

W: Imposible obtener http://archive.ubuntu.com/ubuntu/dists/oneiric-backports/InRelease  

W: Imposible obtener http://archive.ubuntu.com/ubuntu/dists/oneiric-security/InRelease  

W: Imposible obtener http://extras.ubuntu.com/ubuntu/dists/oneiric/InRelease  

W: Imposible obtener http://linux.dropbox.com/ubuntu/dists/oneiric/InRelease  

W: Imposible obtener http://dl.google.com/linux/chrome/deb/dists/stable/InRelease  

W: Imposible obtener http://dl.google.com/linux/talkplugin/deb/dists/stable/InRelease  

W: Imposible obtener http://archive.canonical.com/ubuntu/dists/oneiric/InRelease  

W: Imposible obtener http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/InRelease  

W: Imposible obtener http://archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg  No se pudo conectar a localhost:9090:

W: Imposible obtener http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg  No se pudo conectar a localhost:9090:

W: Imposible obtener http://archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release.gpg  No se pudo conectar a localhost:9090:

W: Imposible obtener http://archive.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg  No se pudo conectar a localhost:9090:

W: Imposible obtener http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg  No se pudo conectar a localhost:9090:

W: Imposible obtener http://linux.dropbox.com/ubuntu/dists/oneiric/Release.gpg  No se pudo conectar a localhost:9090:

W: Imposible obtener http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg  No se pudo conectar a localhost:9090:

W: Imposible obtener http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg  No se pudo conectar a localhost:9090:

W: Imposible obtener http://archive.canonical.com/ubuntu/dists/oneiric/Release.gpg  No se pudo conectar a localhost:9090:

W: Imposible obtener http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/Release.gpg  No se pudo conectar a localhost:9090:

W: Algunos archivos de índice fallaron al descargar. Se han ignorado, o se han utilizado unos antiguos en su lugar



```

Principalmente veo que el sistema quiere conectarse mediante Localhost:9090. 
Me fijé en las propiedades y no tengo Proxy configurado.
La navegacion mediante browsers funciona bien. (estoy usando ahora)

Agradezco sus ideas.

Gracias!

---

### Post by danin on 2013-06-29
Edit: Perdon, pensé que estaba en el subForo Software, quizas el Admin podrá moverlo hacia ese SubForo. Disculpas!

---

### Post by guillermolisi on 2013-07-06
Eso pasa porque esa version que queres actualizar ya ha dejado de recibir soporte/actualizaciones.

> 
[TABLE]
[TR]
[TD="bgcolor: #dd4814, align: center"]**Version**
[/TD]
   [TD="bgcolor: #dd4814, align: center"]**Code name**
[/TD]
   [TD="bgcolor: #dd4814, align: center"]**Docs**
[/TD]
   [TD="bgcolor: #dd4814, align: center"]**Release date**
[/TD]
   [TD="bgcolor: #dd4814, align: center"]**End of life date**
[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="bgcolor: #762852"]Ubuntu 11.10 

[/TD]
   [TD="bgcolor: #f1f1dd"][Oneiric Ocelot]("https://wiki.ubuntu.com/OneiricOcelot")
[/TD]
   [TD="bgcolor: #f1f1dd"] [Tech]("https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview") / [Rel]("https://wiki.ubuntu.com/OneiricOcelot/ReleaseNotes") 
[/TD]
   [TD="bgcolor: #f1f1dd"] [October 13, 2011]("https://lists.ubuntu.com/archives/ubuntu-announce/2011-October/000153.html") 
[/TD]
   [TD="bgcolor: #f1f1dd"] [May 9, 2013]("https://lists.ubuntu.com/archives/ubuntu-announce/2013-March/000167.html")
[/TD]
[/TR]
[/TABLE]
para confirmar esto, podes ingresar en una terminal/consola ```
ubuntu-support-status
```Hay varias formas, mas o menos parecidas, de lograr una actualizacion (upgrade) a un version soportada. Aqui hay una de tantas explicaciones (en Ingles): [http://askubuntu.com/questions/110477/how-do-i-upgrade-from-10-04-or-11-10-to-12-04](http://askubuntu.com/questions/110477/how-do-i-upgrade-from-10-04-or-11-10-to-12-04)

---

