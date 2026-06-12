---
title: "Evolution envia pero no recibe mensaje.."
date: 2009-09-19
forum: Software
---

### Post by akiestudio on 2009-09-19
Pues eso que si consigo enviar ,pero no recibo mensajes en Evolution con gmail.
La version es Evolution 2.26.1.

Y mi configuracion de entrada es:

Tipo de servidor:POP
Servidor:pop.gmail.com:995
usuario:Aqui he puesto mi nombre -.... no se si se refiere a eso.

Usar conexion segura:Cifrado ssl

Y he marcado  Recordar Contraseña

Gracias

---

### Post by santiagoward2000 on 2009-09-19
> **akiestudio said:**
> Pues eso que si consigo enviar ,pero no recibo mensajes en Evolution con gmail.
La version es Evolution 2.26.1.

Y mi configuracion de entrada es:

Tipo de servidor:POP
Servidor:pop.gmail.com:995
usuario:Aqui he puesto mi nombre -.... no se si se refiere a eso.

Usar conexion segura:Cifrado ssl

Y he marcado  Recordar Contraseña

Gracias

Hola!
Lo único que se me ocurre que pueda ser es el usuario. Ahí hay que poner la dirección completa de gmail, incluyendo el "@gmail.com".
El resto me suena que está bien, aunque hace un tiempo que no uso Evolution, y cuando lo usé siempre lo hice por imap en vez de pop.
Saludos!

---

### Post by akiestudio on 2009-09-19
Pues ya cambie el usuario y no es eso...sigo sin recibir emails...
EL problema parece ser de la cuenta de gmail que no me guarda la configuacion de Reenvio y correo POP

---

### Post by guillermolisi on 2009-09-19
> **akiestudio said:**
> Pues ya cambie el usuario y no es eso...sigo sin recibir emails...
Y como esta configurada tu cuenta de correo en Gmail ?
Esta como POP3 o esta como IMAP ?

---

### Post by Hei Ku on 2009-09-19
Activaste el pop3 en Google?

---

### Post by akiestudio on 2009-09-20
No me deja , cuando hago click y guardar configuracion , no la guarda la configuracion, sera ese el problema....

---

### Post by guillermolisi on 2009-09-20
> **akiestudio said:**
> No me deja , cuando hago click y guardar configuracion , no la guarda la configuracion, sera ese el problema....
Me parece sumamente extraño que en la pagina de configuracion de tu cuenta de Gmail, via web, no te deje cambiar de protocolo salvando la configuracion.

---

### Post by akiestudio on 2009-09-21
Parece que si que esta habilitado ,pero sigo sin recibir los mail de gmail ...?
Alguna ayuda....

---

### Post by santiagoward2000 on 2009-09-21
Para estar seguros, en la configuración de Gmail, bajo **Reenvío y correo POP/IMAP**, la segunda categoría (Descarga correo POP) debería decir: **Estado: [COLOR="Green"]POP está habilitado[/COLOR]** (para todos los mensajes recibidos de alguna fecha dependiendo de si elegiste todos los mensajes o a partir de ahora) ¿Dice eso?

---

### Post by akiestudio on 2009-09-21
Si dice eso.... lo raro es que puedo enviar pero no recibir.

---

### Post by santiagoward2000 on 2009-09-21
> **akiestudio said:**
> Si dice eso.... lo raro es que puedo enviar pero no recibir.

No es tan raro, ya que son dos protocolos diferentes, recibís por POP3 y enviás por SMTP.
Sé que no es exactamente lo que preguntabas, ¿pero si lo configurás por IMAP? A mí siempre me anduvo sin problemas.
Para hacerlo tenés que habilitarlo en Gmail (está abajo de donde habilitaste POP). Después en Evolution poné:

Tipo de servidor: IMAP
Servidor: imap.gmail.com:993

Usar conexion segura: Cifrado ssl

---

### Post by akiestudio on 2009-09-21
Solo tengo que cambiar la configuracion en recibidos ,sigo dejando en enviado como pop,porque solo la he cambiado en recibidos y nada de nada..y como si puedo enviar el resto lo deje asi

---

### Post by santiagoward2000 on 2009-09-21
> **akiestudio said:**
> Solo tengo que cambiar la configuracion en recibidos ,sigo dejando en enviado como pop,porque solo la he cambiado en recibidos y nada de nada..y como si puedo enviar el resto lo deje asi

¿Tenés el enviado como POP? Tendría que ser SMTP.
Igual lo que hay que cambiar es solo lo de enviado.
Pregunta abierta, para que alguien conteste porque no estoy seguro de esto: ¿puede ser que haya que abrir el puerto 995 o 993 para que pueda recibir?
Saludos!

---

### Post by guillermolisi on 2009-09-21
> **santiagoward2000 said:**
> ¿Tenés el enviado como POP? Tendría que ser SMTP.
Igual lo que hay que cambiar es solo lo de enviado.
Pregunta abierta, para que alguien conteste porque no estoy seguro de esto: ¿puede ser que haya que abrir el puerto 995 o 993 para que pueda recibir?
Saludos!
Si la conexion es directa a Internet y no hay otro firewall externo al propio de Linux, no haria falta ya que ese port lo deberia abrir Evolution.

---

### Post by akiestudio on 2009-09-21
Perdon el enviado lo tengo como SMTP, Como puedo saber si tengo el puerto abierto...no vaya ser que este cerrado y no pueda recibir por eso...

---

### Post by mama21mama on 2009-09-21
Yo lo que aria seria purgarlo luego meto de nuevo la config de correo. Si no funca esto pues instalo la ultima versión :D

Saludos

---

### Post by mama21mama on 2009-09-21
Yo lo que aria seria purgarlo luego meto de nuevo la config de correo. Si no funca esto pues instalo la ultima versión :D


PD: también esta la posibilidad $ rm -rf ~/.evolution 

Saludos

---

### Post by Hei Ku on 2009-09-21
> **mama21mama said:**
> 

PD: también esta la posibilidad $ rm -rf ~/.evolution 

Saludos

Este comando borra la configuración  y potencialmente cualquier dato almacenado por Evolution incluyendo correos si tenes configurada la carpeta ahí. Valga la aclaracion.

Es mejor explicar bien antes de dar comandos para borrar cosas.

Lo mejor es algo como:

mv ~/.evolution ~/.evolution.old

Que solo le cambie el nombre a la carpeta.

---

### Post by santiagoward2000 on 2009-09-21
> **guillermolisi said:**
> Si la conexion es directa a Internet y no hay otro firewall externo al propio de Linux, no haria falta ya que ese port lo deberia abrir Evolution.

Por las dudas, akiestudio, ¿cómo es la conexión? ¿Directa o mediante un router?

---

### Post by Mauro22 on 2009-09-22
Hola!


Podes chekear con Thunderbird que Gmail se configura solo. Si éste envia y recibe es un problema propio de Configuracion de evolution. Si tampoco anda, es un problema de red/servidor.

---

### Post by akiestudio on 2009-09-22
Pues con Thunderbird funciona perfectamente asi que si alguien sabe que puede ser, por curiosida... estoy en casa con un router wifi normal y corriente...
Seguire usando Thunderbird,Se puede usar con hotmail y yahoo tambien?
Gracias

---

### Post by guillermolisi on 2009-09-22
> **akiestudio said:**
> Pues con Thunderbird funciona perfectamente asi que si alguien sabe que puede ser, por curiosida... estoy en casa con un router wifi normal y corriente...
Seguire usando Thunderbird,Se puede usar con hotmail y yahoo tambien?
Gracias
Con Yahoo entiendo que si, con Hotmail creo que no hasta no hace mucho. Tal vez Hotmail haya cambiado su postura al respecto.

---

### Post by santiagoward2000 on 2009-09-22
> **guillermolisi said:**
> Con Yahoo entiendo que si, con Hotmail creo que no hasta no hace mucho. Tal vez Hotmail haya cambiado su postura al respecto.

Si, cambió hace poco. A los 2 se puede acceder por POP.

---

