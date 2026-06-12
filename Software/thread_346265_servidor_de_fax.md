---
title: "servidor de fax"
date: 2007-01-25
forum: Software
---

### Post by waj on 2007-01-25
Buenas,
alguien tiene alguna experiencia con ubuntu como servidor de fax?, la idea es instalarlo para como servidro para 30 usuarios con windor., que me tire una idea, mientras estoy mirando hylafax, e-fax, y lo que encuentro, hay mucho pero todo suelto....y encima viejo.
Saludos y gracias

---

### Post by felipelerena on 2007-01-26
asterisk no hace eso???

---

### Post by waj on 2007-01-27
pues. no...Asterisk es una aplicación de código abierto de una central telefónica 
y yo busco solo Fax.  Gracias igual.

[http://es.wikipedia.org/wiki/Asterisk](http://es.wikipedia.org/wiki/Asterisk)

---

### Post by cintiaarosales on 2012-05-31
Ah! Pero este asunto es bien viejito! Me llamó la atención porque también he estado revisando el tema de funcionamiento de un servidor de fax  con Ubuntu u otros sistemas operativos de tipo-Linux.
Es cierto que Asterisk no tienen esta capacidad, pero si todavía estás interesado en encontrar la manera de hacer esto con hylafax, encontré un procedimiento simple en los foros en inglés que puede ser útil:
Teclee:

```
# sudo apt-get install hylafax-server
```

Después de lo cual tendrías que configurar hylafax con el guión de faxsetup.

```
# sudo faxsetup 
```

faxsetup solicitará que ejecutes faxaddmodem y te conducirá a través de la instalación. Si no se ejecuta faxaddmodem de la línea de comandos, te ayudará a configurarlo. Una vez completado reinicia hylafax y deberías ser capaz de enviar y recibir faxes.

```
# sudo / etc / init.d / hylafax parada
# sudo / etc / init.d / hylafax inicio
```

Tengo entendido que también estabas chequeando servicios de fax online como efax (a pesar de que se trata de una dirección diferente). Yo también he leído acerca del [reemplazo de servidor de fax]("http://www.interfax.net/es/solutions/servidor_de_fax"), que es un tipo de la misma calidad de servicios online y no tiene mucho para configurar, pero cuesta dinero. Otro "sustituto del servidor de fax" del que oído hablar es [MyFax]("http://www.myfax.com"), tampoco es gratis, pero creo que tiene una version de prueba gratuita.
Dudo que esto siga siendo relevante, pero me imaginé que podría ayudar a alguien como yo, que se encuentra este asunto y está investigando el tema ... :)
Cintia

---

