---
title: "Sin Internet en Terminal?"
date: 2010-08-15
forum: Software
---

### Post by jpoeta on 2010-08-15
Queridos amigos de Loco Team Argentina!

Ayer trate de ayuda a un amigo a pasarse al mejor de los sistemas operativos del mundo ubuntu. Pero lamentablemente surgieron muchos inesperados problemas el primera de ellos fue Firefox que no conectaba la solucion fue "about:Config" "ipv6" y cambiar de false a True. Gracias a ello puedo bajar skype y amsn normalmente(sin terminal) debido a que yo lo ayudo online pues vivo en Alemania y mi amigo en Perú. Luego y fue aquí que no supe que hacer fue cuando al tratar de bajar los codecs de medibuntu en terminal la conección se reiniciaba y reiniciaba sin parar. Para ver si era un problema de el link lo hice yo mismo y no me presento ningun problema, luego cambie el servidor de los origenes de software a principal pero aún así la conección se reiniciaba y no lograba descargar nada.
Espero alguien me pueda ayudar pues no quiero que alguien deje ubuntu con una muy mala impresión de nuestro querido software libre.

Muchas Gracias de Antemano:P

Jpoeta

Ps. Mi amigo veia partidos de futbol completo por justin.tv cuando tenia windows xp, creo que cambiaba su ip por uno aericano usando aol. Sabe alguien cual es la solucion en ubuntu =)

---

### Post by jpoeta on 2010-08-15
Queridos amigos de Loco Team Chile!

Ayer trate de ayuda a un amigo a pasarse al mejor de los sistemas operativos del mundo ubuntu. Pero lamentablemente surgieron muchos inesperados problemas el primera de ellos fue Firefox que no conectaba la solucion fue "about:Config" "ipv6" y cambiar de false a True. Gracias a ello puedo bajar skype y amsn normalmente(sin terminal) debido a que yo lo ayudo online pues vivo en Alemania y mi amigo en Perú. Luego y fue aquí que no supe que hacer fue cuando al tratar de bajar los codecs de medibuntu en terminal la conección se reiniciaba y reiniciaba sin parar. Para ver si era un problema de el link lo hice yo mismo y no me presento ningun problema, luego cambie el servidor de los origenes de software a principal pero aún así la conección se reiniciaba y no lograba descargar nada.
Espero alguien me pueda ayudar pues no quiero que alguien deje ubuntu con una muy mala impresión de nuestro querido software libre.

Muchas Gracias de Antemano

Jpoeta

Ps. Mi amigo veia partidos de futbol completo por justin.tv cuando tenia windows xp, creo que cambiaba su ip por uno americano USA usando aol. Sabe alguien cual es la solucion en ubuntu =)

---

### Post by biale on 2010-08-15
El cambio que hiciste afecta solamente a Firefox. Suponiendo que la solución sea anular IPv6 (¿será así?), para Lucid se puede anular para todo modificando a /etc/sysctl.conf de acuerdo con:

[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)

Un saludo

---

### Post by Carlos C on 2010-08-15
Yo habilito medibuntu mediante el comando:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
¿Qué comando utilizas tú?

---

### Post by jpoeta on 2010-08-15
Lo Intenté pense que resulataria pero no se que hacer ayudenme amigos.

eric@eric-desktop:~$ cat /proc/sys/net/ipv6/conf/all/disable_ipv6
1
eric@eric-desktop:~$ ./postlucid.sh
Aplicando Radiance Theme...
[sudo] password for eric: 
--2010-08-15 11:29:04--  [http://www.medibuntu.org/sources.list.d/lucid.list](http://www.medibuntu.org/sources.list.d/lucid.list)
Resolviendo [www.medibuntu.org](www.medibuntu.org)... 1.0.0.0
Conectando a [www.medibuntu.org|1.0.0.0|:80](www.medibuntu.org|1.0.0.0|:80)... falló: Expiró el tiempo de conexión.
Reintentando.

--2010-08-15 11:29:26--  (intento: 2)  [http://www.medibuntu.org/sources.list.d/lucid.list](http://www.medibuntu.org/sources.list.d/lucid.list)
Conectando a [www.medibuntu.org|1.0.0.0|:80](www.medibuntu.org|1.0.0.0|:80)... falló: Expiró el tiempo de conexión.
Reintentando.

--2010-08-15 11:29:49--  (intento: 3)  [http://www.medibuntu.org/sources.list.d/lucid.list](http://www.medibuntu.org/sources.list.d/lucid.list)
Conectando a [www.medibuntu.org|1.0.0.0|:80](www.medibuntu.org|1.0.0.0|:80)...

---

### Post by lisati on 2010-08-15
Threads merged

---

### Post by jpoeta on 2010-08-15
Probé también así como vos lo haces pero no funciona y lo mas raro aun es que es solo medibuntu y un par de otros repositorios pero tras cosas funcionan normal gracia de antemano

---

### Post by jpoeta on 2010-08-17
Me han dicho que mis DNS funcionan mal y que el encargado de eso seria Telefonica mi ISP. Me pregunto si puedo configurar manualmente mis DNS y asi se solucione el problema si alguien tiene experiencia le agradeceria un Consejo.

Saludos 

Jpoeta;)

---

