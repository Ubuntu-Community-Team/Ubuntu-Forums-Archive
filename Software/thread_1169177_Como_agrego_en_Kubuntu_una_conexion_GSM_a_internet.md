---
title: "Como agrego en Kubuntu una conexion GSM a internet? (Hei Ku al rescate!)"
date: 2009-05-24
forum: Software
---

### Post by atari130xe on 2009-05-24
Foro, estoy probando Kubuntu 9.04 para ver como funciona y que cosas nuevas trae, y resulta que quiero configurar una conexion con mi telefono celular (wap no banda ancha movil), como la que hago en Ubuntu (inclusive con la jaunty es una maravilla de facil hacerlo) pero probando con Kubuntu y su applet para confugurar redes, muero en el intento porque no le encuentro la vuelta.

Caso Ubuntu Intrepid o Jaunty: conecto el cable USB, conecto el celular, (lo pongo en modo "modem") y sale el asitente de configuracion de NetManager y listo elijo: Argentina, proveedor: Movistar y listo, click en conectar y listo navegando Wap!

Caso Kubuntu: hago lo mismo pero no sale ningún asistente, solo reconoce que hay 2 puertos nuevos de comunicaciones y listo, le doy a configurar conexiones de banda ancha movil y me pide usuario contraseña numero, etc. no logro dar pie con bola, alguna sugerencia? Hei ku yo se que ud puede! :lolflag:

PD: o sea quiero configurar una conexion WAP a internet.

---

### Post by Hei Ku on 2009-05-25
Hmmm, los verdaderos hombres editan a mano el archivo /etc/network/interfaces. 

Yo uso WiCD. :lolflag:

Y nunca configure una conexión GSM en linux.

---

### Post by staar on 2009-05-25
sugerencia: anotar los datos relevantes (usuario, contraseña, apn, dns, etc) de la conexión en gnome, y luego configurar una nueva conexión con dichos datos en kde...

las GSM (y las 3g) son conexiones ppp, el /etc/network/interfaces no va para ellas, en todo caso se editarían los diferentes archivos de /etc/ppp/ y ESO es de hombres...

yo uso wvdial :lolflag::lolflag:

saludos

---

### Post by Hei Ku on 2009-05-25
En ese caso, en KDE tenes kppp. :D

---

### Post by atari130xe on 2009-05-25
Jajaja y después me preguntan porqué me gusta tanto esta comunidad y porque uso Ubuntu, Hei Ku me hiciste reir mucho, entrar a darle a gedit/kate... modificar, guardar, etc jajaja gracias.... sos unos seres humanos de 10 :D

PD: en Ubuntu al menos en la maquina de mi amigo que fué la última en la que le instalé la 9.04 Wicd no funcionó muy bien (se pasaba una eternidad buscando la conexion DSL y moría) pero me gusta ese programa, asi que probaré con Wicd.

---

### Post by atari130xe on 2009-05-25
> **staar said:**
> sugerencia: anotar los datos relevantes (usuario, contraseña, apn, dns, etc) de la conexión en gnome, y luego configurar una nueva conexión con dichos datos en kde...

las GSM (y las 3g) son conexiones ppp, el /etc/network/interfaces no va para ellas, en todo caso se editarían los diferentes archivos de /etc/ppp/ y ESO es de hombres...

yo uso wvdial :lolflag::lolflag:

saludos

jajaja ok, y la verdad que es de hombres tmb ejecutar el comando que tenés ahi para escuchar el laburo del rígido si te lo bancas 2 minutos son un Macho Mexicano con sombrero de ala ancha y pistolas... :lolflag:

---

