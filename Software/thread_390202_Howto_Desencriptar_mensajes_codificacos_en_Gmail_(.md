---
title: "Howto: Desencriptar mensajes codificacos en Gmail (y otros webmails)"
date: 2007-03-21
forum: Software
---

### Post by strugart on 2007-03-21
Bueno no se bien si ya fue publicado, en ese caso sepan disculpar.  

Bueno como yo tengo un webmail y no puedo desencruptar desde un programa de correo (como Thunderbird) ya que la unica extension que lo maneja es, digamos, dificil de obtener (esto es para firefox), hice esto Howto. 

Lo primero que deberiamos tener es GnuPG, de donde se baja? Bueno esta enpaquetado en nuestra forma de distrubucion (.deb) asi que es realmente facil. Vamos aca:
[http://packages.debian.org/stable/utils/gnupg](http://packages.debian.org/stable/utils/gnupg) y lo descargamos.
Acto seguido completamos las distintas dependencias (cualquier problema de dependencia vuelvan a la pagina y desde alli descargen los paquetes que no se les descargan). Hecha la instalacion continuamos.
Seria bueno que tambien instalemos una version grafica, la que yo utilizo es para KDE pero me ha funcionado bien. Se llama KGpg que se puede descargar desde aca: [http://developer.kde.org/~kgpg/download.html](http://developer.kde.org/~kgpg/download.html). 
Hecho todo esto hacemos la guia de launchpad para crear y firmar las claves:
1) Aseguremonos que tenemos una clave:
gpg --list-keys [email]tu@direccionde.mail[/email]
2) Si no tenemos nos creamos una:
gpg --gen-key (seguimos todo el asistente que nos guia por el proceso).
3) Nos aseguramos que lo hemos subido a un servidor de claves:
gpg --send-key id-llave
4) Introducimos nuestras huellas:
gpg --fingerprint id-llave
Dsp de todo esto introducimos un codgo parecido a este: 27E0 7815 B47C 0397 90D5  8589 27D9 A27B F3F9 6058 ne la seccion de de claves GnuPG de nuestro usuario (para llegar aca nos autoclikeamos y vamos al panel de la derecha y click en OpenPG keys) Al final de los pasos que ya traduci y liste hay una palabra que dice Fingerprint y un cuadro de texto,  alli introducimos nuestros numeros. Debemos esperar, talvez, un rato para que los distintos servidores se sincronizen. Esto puede llegar a durar una hora (pero es raro)
Posteriormente de esperar aburridos el mail que nos llega le vamos a dar vida al GUI de GnuPG:
Vamos a Aplicaciones, Accesorios, KGpg y alli cuando finzalizamos el asistente (en estos momentos solo es necesario clickear en siguiente todo el tiempo).
Despues vamos a File,  Open Editor y alli pegamos TODO el mail que nos ha llegado a nuestra casilla. Estos es (para que quede claro) desde nos dice Begin...hasta End PGP Message.
Y clickeamos en Decrypt. Y Voila! De esa traduccion nos importa solo la direccion que aparece mas abajo. La seleccionamos y, despues de clikear en boton derecho, y seleccionar copiar lo pegamos en el navegador. Y Voila hemos registrado nuestra clave.
Pero falta lo mas importante que es firmar el codigo de conducta:
Lo descargamos y seleccionamos todo y lo pegamos en el editor y clickeamos en sign/verify. Nos va aparecer nuestras claves, seleccionamos la que nos interesa o la unica que tenemos,  clikeamos en ok ponemos nuestra contrasena y nos va aparecer el mismo texto pero abajo firmado por nosotros. Copiamos todo el texto y lo pegamos en el link del tercer paso (despues clickeamos en continue) Y listo.
Tambien podemos encriptar mensajes solo haciendolo, pegandolo y despues clickenaod en encript (cualquier que tenga algun problema avise que hago un howto)

---

### Post by clasificado on 2007-03-22
Aver si entendí: 

1) Alguien me manda un **correo encriptado**. por ej: GMail, con opción de encriptacion ¿Existe eso en GMail?)

2) Yo tengo cualquier cadorcha, me llega en mi webmail y me quiero matar porque **me muestra cualquier cosa porque no puede desencriptar**.

3) Me armo de valor (y paciencia, y tiempo, y ganas, y me anoto buscar un webmail que lo haga por mi) y me instalo el **GnuPG + KGpg**, y bailo un ratito entre las opciones como explicas vos

4) Listo el pollo, Open editor, me aparece un cuadro de texto **Copio y Pego** (no cualquier cosa, eso que decís vos), Le doy al **Decrypt** ese y ¡Voilà!

5) **Ya está: Todo desencriptado**. No lo veré en formato web ni muy lindo pero está ahi.

¿Puede ser?. La verdad nunca me pasó, pero si me pasa: ¿Entendí bien?

Clasificado

---

### Post by strugart on 2007-03-22
A ver la idea del howto es que si te suscribis a launchpad y queres firmar el codigo de conducta no vas a poder con webmail ya que no existe o mas bien es dificil de obtener una extension que te lo desencripta solo (esto si pasa y es facil por ejemplo con una cuenta pop3 o Imap en Thunderbird que existen extensiones y traducciones).  Entonces como yo tuve el problema y logre una solucion mas rapida que cambiar de provedor lo comparto para que cualquiera que tenga el mismo problema pueda solucionarlo.
Otra cosa si vos queres tener un fludio trafico de correo entre tus cercanos con mensajes encriptados bueno esta bien, pero la idea es para un solo mail no 50 (anque ovbio es totalmente aplicable si lo modificas un poco).

---

### Post by fetova on 2007-03-22
> **strugart said:**
> A ver la idea del howto es que si te suscribis a launchpad y queres firmar el codigo de conducta no vas a poder con webmail ya que no existe o mas bien es dificil de obtener una extension que te lo desencripta solo (esto si pasa y es facil por ejemplo con una cuenta pop3 o Imap en Thunderbird que existen extensiones y traducciones).  Entonces como yo tuve el problema y logre una solucion mas rapida que cambiar de provedor lo comparto para que cualquiera que tenga el mismo problema pueda solucionarlo.
Otra cosa si vos queres tener un fludio trafico de correo entre tus cercanos con mensajes encriptados bueno esta bien, pero la idea es para un solo mail no 50 (anque ovbio es totalmente aplicable si lo modificas un poco).

Pues yo tengo problemas exactamente con eso ;) gracias

---

### Post by fetova on 2007-03-29
> **fetova said:**
> Pues yo tengo problemas exactamente con eso ;) gracias

\\:D/ \\:D/ \\:D/ \\:D/ 

Ya pude firmar el codigo!!!!!

Todo por tragarme cachos del texto:-\" 


#-o #-o Pero por fin esta

Gracias

---

### Post by Thalskarth on 2009-01-25
> **clasificado said:**
> 1) Alguien me manda un **correo encriptado**. por ej: GMail, con opción de encriptacion ¿Existe eso en GMail?)

Eso lo podes hacer directamente con Firepgp ([https://addons.mozilla.org/es-ES/firefox/addon/4645](https://addons.mozilla.org/es-ES/firefox/addon/4645))

Es una extensión para firefox, que te permite encriptar y decencriptar y firmas mails desde el webmail de Gmail de la misma forma a que si estuvieras usando un cliente como thunderbird+enigmail

---

### Post by almufadado on 2009-12-01
Use gpa - Gnu Privacy assistante ... works nice!

---

