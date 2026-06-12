---
title: "Mail a traves de Squid"
date: 2010-02-05
forum: Software
---

### Post by sebacastro21 on 2010-02-05
Buenas
Necesito configurar el mail a traves del squid proxy, es decir lo que nesecito en realidad es que el squid ignore el trafico pop3, smtp e imap ya que estos protocolos no son soportados por el squid. Por lo que pude averiguar la mayor parte de las veces se soluciona configurando un iptables pero el tema es que en esta instalacion no esta instalado.
Espero que me puedan dar una mano.
Saludos

---

### Post by guillermolisi on 2010-02-05
> **sebacastro21 said:**
> Buenas
Necesito configurar el mail a traves del squid proxy, es decir lo que nesecito en realidad es que el squid ignore el trafico pop3, smtp e imap ya que estos protocolos no son soportados por el squid. Por lo que pude averiguar la mayor parte de las veces se soluciona configurando un iptables pero el tema es que en esta instalacion no esta instalado.
Espero que me puedan dar una mano.
Saludos
iptables esta siempre, solo tenes que agregar las reglas que direccionan los paquetes de esos protocolos para los ports que estes usando en cada caso, si queres ser muy especifico, o solamente para los protocolos si queres ser mas general en los forwardings.

---

### Post by sebacastro21 on 2010-02-05
Pero desde donde lo configuro y como?? osea desde el conf del squid??
En cuanto a lo que decis de que siempre esta el iptable, la verdad te digo que lo busque y no esta insalado
Disculpa mi ignorancia pero soy bastante nuevo en esto
Muchas gracias
Saludos

---

### Post by guillermolisi on 2010-02-05
> **sebacastro21 said:**
> Pero desde donde lo configuro y como?? osea desde el conf del squid??
En cuanto a lo que decis de que siempre esta el iptable, la verdad te digo que lo busque y no esta insalado
Disculpa mi ignorancia pero soy bastante nuevo en esto
Muchas gracias
Saludos
Para conocer sintenticamente sus opciones y sintaxis, a modo de aproximacion al uso de iptables ```
man iptables
``` en una consola/terminal. Si te muestra el contenido de sus paginas, esta "instalado" y funcionando.
Para saber que reglas tenes activas ```
sudo iptables -L
```

Edit: Te paso dos links que se publicaron en la lista de e-mail sobre iptables que podrian ampliarte el panorama:

[http://www.ibiblio.org/pub/Linux/docs/LuCaS/Manuales-LuCAS/doc-iptables-firewall/doc-iptables-firewall-html/](http://www.ibiblio.org/pub/Linux/docs/LuCaS/Manuales-LuCAS/doc-iptables-firewall/doc-iptables-firewall-html/)

[http://www.pello.info/filez/IPTABLES_en_21_segundos.html](http://www.pello.info/filez/IPTABLES_en_21_segundos.html)

---

### Post by sebacastro21 on 2010-02-05
Esta bien, el tema insisto es que iptable no esta instalado solo el squid, igualmente me parece que voy a terminar instalando es iptable y enmascarando el trafico de mail
Saludos

---

### Post by juancarlospaco on 2010-02-06
IPtables es parte del Kernel Linux.

Una manera amigable y recomendable de manejarlo es UFW: **ufw --help**

Squid por defecto forwardea todo trafico que no soporta cachear, 
asi que seria muy raro que Squid NO ignore el trafico pop3, smtp e imap.
Asi que seguro no necesitas hacer nada que ya esta andando, si es que Squid anda.

---

### Post by alfplayer on 2010-02-06
> **sebacastro21 said:**
> Esta bien, el tema insisto es que iptable no esta instalado solo el squid, igualmente me parece que voy a terminar instalando es iptable y enmascarando el trafico de mail
Saludos

Es iptable**s **(termina con s).

---

