---
title: "ares en ubuntu"
date: 2008-05-20
forum: Software
---

### Post by ramiro_md on 2008-05-20
Hola gente del foro..escribia este thread..ya que mi cliente p2p preferido es ares, puesto a que m vielocidad de internet no es de la mas rapidas y con el ares aprovecho al maximo el ancho de banda. La cuestion es que probe con varias opciones q lei en internet como usar el wine (pero jamas conecta) e instalando otros servicos p2p como gift y otras cosas asi..pero no he obtenido resultados. Queria saber si alguien esta corriendo ares en su ubuntu y de que forma lo hizo. Desde ya muchas gracias.

---

### Post by Thalskarth on 2008-05-20
> **ramiro_md said:**
> Hola gente del foro..escribia este thread..ya que mi cliente p2p preferido es ares, puesto a que m vielocidad de internet no es de la mas rapidas y con el ares aprovecho al maximo el ancho de banda. La cuestion es que probe con varias opciones q lei en internet como usar el wine (pero jamas conecta) 
esto me passaba a mi.

La salucion, la encontre desistalando wine completo (borra el .wine) einstale la ultima version desde la pagina de wine.
instale Ares y la primera vez tardo unos 15 minutos ...pero despues siempre se meconecta al toque sin esperas

---

### Post by sartrejp on 2008-05-20
Que version de ubuntu usas? porque a mi en 7.10 me pasaba, pero desde que instalé hardy (que viene wine instalado) anda de maravilla (lastima que ya me acostumbré a usar otro programas (amule, nicotine, frostwire).

---

### Post by ramiro_md on 2008-05-20
El ares sigue sin conectar de todos modos..y el nicotinwe no me funca..o no lo se hacer andar...me dice el siguiente error No se puede entrar en el sistema, razón: INVALIDPASS..si laguien me puede guuiar:confused:

---

### Post by guisheca on 2008-05-21
El problema está en que tenes cerrado el puerto que usa para compartir archivos, eso lo ves en Panel de control>descargas. Ahí ves cual es el puerto y lo abris en tu router, o lo cambias por uno que sepas que lo tenes abierto.
Yo uso ares y tenia ese problema, con esto que te digo funciona de 10.
Saludos.

---

### Post by ramiro_md on 2008-05-21
uso  un modem motorola sb 5101...

---

### Post by rapper97 on 2008-06-25
Si lees inglés, [este hilo]("http://ubuntuforums.org/showthread.php?t=198945") tiene mucha información, pero resulta que giFT está bastante viejo y parece que no se actualice ya. [Este post]("http://www.tuxinga.com.ar/2007/11/11/ares-en-ubuntukubuntu-sin-wine/") les ayudó a muchos, pero funcione para unos y para otros no, aunque siguieron los mismos pasos.

¡Suerte!

---

### Post by ramiro_md on 2008-06-27
> **rapper97 said:**
> Si lees inglés, [este hilo]("http://ubuntuforums.org/showthread.php?t=198945") tiene mucha información, pero resulta que giFT está bastante viejo y parece que no se actualice ya. [Este post]("http://www.tuxinga.com.ar/2007/11/11/ares-en-ubuntukubuntu-sin-wine/") les ayudó a muchos, pero funcione para unos y para otros no, aunque siguieron los mismos pasos.

¡Suerte!

Nunca me anduvo gift ! :confused: igual ahora con hardy heron me anduvo ares bajo wine a la perfeccion :)

---

### Post by ramiro_md on 2008-09-14
Gente reabroel thread con urgencia jejeje, necesito ayuda con el iptables, la cuestión es que emulé el ares en mi hardy heron (porque jamas me salio hacerlo andar de otra manera, y el amule nunca me convencio al igual que emule en win$).
La cuestion, es que; abro el puerto en el router, configuro el ares tildando la opcion "mi pc esta detras de un cortafuegos". 
En fin, a la hora de abrir el peurto del ares en iptables, hago lo siguente x consola:

iptables -A INPUT -p TCP --dport xxxx -j ACCEPT
iptables -A OUTPUT -p TCP --dport xxxx -j ACCEPT
iptables -A FORWARD -p TCP --dport xxxx -j ACCEPT

No se si hice bien los pasos del iptables, pero el ares no conecta =(, si alguien le me da una mano, agradecido de por vida xD. Un saludo.

Nota: en anteriores instalaciones de hardy solia andar de una =S

---

