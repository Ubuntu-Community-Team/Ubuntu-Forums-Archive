---
title: "Problemas al actualizar el Gestor de Actualizaciones"
date: 2008-06-09
forum: Software
---

### Post by Vulcano on 2008-06-09
Estimados:

Tengo el siguiente problema. Cuando quiero actualizar los paquetes del gestor de actualizaciones me tira el siguiente error:

W: Ha ocurrido un error durante la verificación de la firma. El repositorio no se ha actualizado y se usarán los archivos de índice anteriores. Error de GPG: [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates Release Las siguientes firms fueron inválidas: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://ar.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  

W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/hardy-proposed/universe/binary-i386/Packages.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/hardy-proposed/universe/binary-i386/Packages.bz2)  La suma MD5 difiere

W: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.

Alguien me podrà ayudar?

Desde ya, muchas gracias a todos!

Leo

---

### Post by majatu on 2008-06-09
Justo entro para preguntar lo mismo. Recien instale Ubuntu en un disco limpio y cuendo me puse a querer instalar las actualizaciones, los controladores restringidos y demás, se me abre la ventana de "Descargando Información de Paquetes" y ahi queda, no descarga ni verifica ningun source :confused:, yo pensé que era inet pero anda de 10 y sin problemas.


**** ACA LES DEJO LO ULTIMO QUE ME APARECIO EN PANTALLA ***

W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://ar.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  No pude conectarme a ar.archive.ubuntu.com:80 (91.189.88.45), expiró tiempo para conexión [IP: 91.189.88.45 80]

W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-es.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-es.bz2)  No pude conectarme a ar.archive.ubuntu.com http: [IP: 91.189.88.45 80]

W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-es.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-es.bz2)  No pude conectarme a ar.archive.ubuntu.com http: [IP: 91.189.88.45 80]

W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-es.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-es.bz2)  No pude conectarme a ar.archive.ubuntu.com http: [IP: 91.189.88.45 80]

W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-es.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-es.bz2)  No pude conectarme a ar.archive.ubuntu.com http: [IP: 91.189.88.45 80]

W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://ar.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  No pude conectarme a ar.archive.ubuntu.com http: [IP: 91.189.88.45 80]

W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-es.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-es.bz2)  No pude conectarme a ar.archive.ubuntu.com http: [IP: 91.189.88.45 80]

W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-es.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-es.bz2)  No pude conectarme a ar.archive.ubuntu.com http: [IP: 91.189.88.45 80]

W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-es.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-es.bz2)  No pude conectarme a ar.archive.ubuntu.com http: [IP: 91.189.88.45 80]

W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-es.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-es.bz2)  No pude conectarme a ar.archive.ubuntu.com http: [IP: 91.189.88.45 80]

W: Imposible obtener [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  No pude conectarme a security.ubuntu.com:80 (91.189.88.37), expiró tiempo para conexión

W: Imposible obtener [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-es.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-es.bz2)  No pude conectarme a security.ubuntu.com http:

W: Imposible obtener [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-es.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-es.bz2)  No pude conectarme a security.ubuntu.com http:

W: Imposible obtener [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-es.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-es.bz2)  No pude conectarme a security.ubuntu.com http:

W: Imposible obtener [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-es.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-es.bz2)  No pude conectarme a security.ubuntu.com http:

W: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.




Entones creo suponer que hay un problema con el server, alguien puede intentar y contarnos si tampoco le anda?

Tienen idea de que pasa o si puedo solucionarlo de alguna forma?



Muchas gracias!

---

### Post by Flechagorda on 2008-06-09
Majatu, probaste cambiando desde Origenes de Software?

Donde dice "DESCARGAR DESDE" cambia "Servidor Para Argentina" por "Servidor Principal"

Recarga y probalo.......

---

### Post by majatu on 2008-06-10
> **Flechagorda said:**
> Majatu, probaste cambiando desde Origenes de Software?

Donde dice "DESCARGAR DESDE" cambia "Servidor Para Argentina" por "Servidor Principal"

Recarga y probalo.......

Ahora esta andando con normalidad, había pensado en eso pero no encontraba en donde cambiar el server. A tener en cuenta si me pasa nuevamente. Gracias! ;)

---

