---
title: "Pidgin y MSN"
date: 2009-06-30
forum: Software
---

### Post by Iced_R on 2009-06-30
Tengo un problema con Pidgin. Intento conectarme a la red en MSN, pero no me quiere dejar. Y al parecer es sólo problema de la red MSN, xq tengo el plugin para que me conecte a la red de Facebook y lo hace sin problemas.

La red en la que estoy se rige por un proxy HTTP, el cual obviamente está añadido a las opciones de Pidgin. Y además, estaba trabajando con el método HTTP, con las opciones por defecto de la red MSN...


Saludos.

---

### Post by bichopro on 2009-06-30
Justamente hoy he tenido problemas con pidgin, por eso por hoy he usado emesene, intentalo mañana por que al parecer es solo temporal

---

### Post by nopersona on 2009-07-01
Para usar las cuentas msn en pidgin yo uso [msn-pecan]("http://code.google.com/p/msn-pecan/downloads/list"), está en los repositorios. Es mejor usar el de launchpad para siempre tenerlo actualizado. Después agregan su cuenta con WLM y todo funciona ok.

Repositorio para jaunty

```
#Msn Pecan
deb http://ppa.launchpad.net/msn-pecan/ppa/ubuntu jaunty main
```
Saludos!

---

### Post by Iced_R on 2009-07-02
Al parecer mi problema no es de Pidgin. Me parece que me bloquearon por proxy cualquier tipo de acceso a la red MSN, así que este tema quedará en el aire.

De todas maneras, gracias por las respuestas.

Saludos.

---

### Post by nopersona on 2009-07-03
> **Iced_R said:**
> Al parecer mi problema no es de Pidgin. Me parece que me bloquearon por proxy cualquier tipo de acceso a la red MSN, así que este tema quedará en el aire.

De todas maneras, gracias por las respuestas.

Saludos.

Algún sustento para afirmar eso? qué tira iptables?

---

### Post by aledruetta on 2009-07-03
> **Iced_R said:**
> ... Y al parecer es sólo problema de la red MSN, xq tengo el plugin para que me conecte a la red de Facebook y lo hace sin problemas.

¿Cómo es eso del plugin para Facebook? En herramientas --> complementos no lo encontré.

---

### Post by aledruetta on 2009-07-03
Perdón, lo encontré. Synaptic --> pidgin-facebookchat

---

### Post by Iced_R on 2009-07-06
Por lo visto no es problema de una conexión Proxy. No sé cómo ocupar el comando iptables, así que no pego ningún screenshot ni documentación xD, pero por lo menos en GUIndous si puedo entrar a la red MSN. 

Estoy atento a sugerencias, y así de paso aprendo un poco más XD.

Saludos.

---

### Post by adux on 2009-07-07
Si dices que estas en una red con proxy es factible que tengan ciertos puertos bloqueados msn messenger usa 
 
TCP port 1863 
TCP port 6901 
TCP ports 6891 to 6900. 
UDP on ports 1503, 3389 
 
(hay varios mas)
 
Ahora otra cosa que puede pasar que no entiendo bien porque, pero me pasaba en la u, es que se tomaba la red como no segura (supongo que por el proxy?) 
 
asique yo lo que yo hice es usar el magico boton de HTTP mode :) y asi (supongo tambirn) usaba el puerto 80 que casi nunca tiene filtro y listoco tenemos msn.
 
 
Ahora para todo lo que es pluins por synaptic, busca "pidgin" y te aparecen varios, el resto es buscar entre la lista.
 
Aun asi hay otros que no te aparecen, que puedes buscar aqui algunos: [http://ubuntuforums.org/showthread.php?t=865424](http://ubuntuforums.org/showthread.php?t=865424)
 
eso, espero haber aportado un granito de arena 
 
adiosh

---

### Post by Iced_R on 2009-07-07
Toy comenzando las pruebas con el los protocolos recomendados en el post de adux. Lo del método HTTP, es la primera cosa que probé, pero sin resultado, y además como puse anteriormente, Windows Live Messenger sí permite conexión a la red MSN. Y a todo eso, ¿cómo utilizo iptables?

---

### Post by aledruetta on 2009-07-07
> **Iced_R said:**
> Toy comenzando las pruebas con el los protocolos recomendados en el post de adux. Lo del método HTTP, es la primera cosa que probé, pero sin resultado, y además como puse anteriormente, Windows Live Messenger sí permite conexión a la red MSN. Y a todo eso, ¿cómo utilizo iptables?

Iptables, no sé. Pero hay mucha información dando vueltas. Yo uso gufw. Es un firewall de Ubuntu y ahí podés abrir o cerrar puertos graficamente. Es lo más sencillo, creo.

Saludos,
Alejandro.

---

### Post by nopersona on 2009-07-07
Par mi iptables es lo más cómodo a la hora de realizar estas labores, si aprendes a usarlo, aunque sea como usuario común, verás que es una utilidad fabulosa!

[http://www.seguridad.unam.mx/red-seguridad/documentos/descarga.dsc?arch=12&damedoc=doc-iptables-firewall.pdf](http://www.seguridad.unam.mx/red-seguridad/documentos/descarga.dsc?arch=12&damedoc=doc-iptables-firewall.pdf)

[http://www.linuca.org/body.phtml?nIdNoticia=99](http://www.linuca.org/body.phtml?nIdNoticia=99)


También podrías usar un sniffer como [Wireshark]("http://www.wireshark.org/") para comprobar el puerto de la conexión, y que realmente la señal intente salir por dicho puerto. A todo esto, probaste msn-pecan?


P.S.: Se me olvidaba, no viene mucho al tema, pero, alguien ha probado jabber? me parece una red muy estable y funcional, además pidgin tiene un soporte muy completo, hasta se pueden usar pasarelas para mantener los contactos msn, dependiendo del servidor, claro está. Cof cof cof, [le remuevo el polvo a un how-to que hice. ]("http://nopersona.wordpress.com/2008/03/30/habilitando-jabber/")

---

