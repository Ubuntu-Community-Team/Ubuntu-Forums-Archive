---
title: "Necesito ayuda urgente!"
date: 2009-07-11
forum: Software
---

### Post by sliiver on 2009-07-11
Hola, ayer compré una pc y apenas la prendo me aparece ubuntu
No se qe contraseña poner!!
Alguien me ayuda?
 
 
Mandenme un e-mail, por favor
 
Muchas  gracias!

---

### Post by Hei Ku on 2009-07-11
A quien se la compraste? No le podes preguntar?

Hmmm, esto puede ser un pedido de ayuda genuino o alguien tratando de encontrar la forma facil de entrar a una pc "prestada".

Ademas, los temas no se contestan por email. Todo se hace en el foro, a la vista de todos. Especialmente en estos casos.

---

### Post by sliiver on 2009-07-11
La PC la compré en una casa de electrodomésticos (Pardo S.A.)
Y en el manual de instrucciones no me dice ninguna contraseña ni nada..
No se qe hacer

Por favor, una ayuda..

---

### Post by guillermolisi on 2009-07-11
Sliiver

Varias observaciones para tu ayuda:

No te desesperes y no abras mas de un hilo/thread por el mismo tema. No es una lista de e-mails, es un foro y tiene una dinamica, reglas y uso totalmente distitna a las listas.

Luego, cuando quieras ayuda rapida, pone en el asunto del thread algo que permita intuir (aunque mas no sea) el contenido del mismo, el tema sobre el cual se tratara.

Tercero, este foro es comunitario, voluntario, internacional, queda todo registrado y algunos detalles mas que ahora no vienen al caso. Asi que te pido que leas las reglas de uso y comportamiento vigentes en la primer pagina del foro argentino (sticky threads).

Nadie tiene obligacion de responder y menos si no saben o conocen del tema que se trate.

Si tenes dudas sobre como proceder, podes contactar a los moderadores via PM (Private Message) para aclararlas.

Bienvenido.

---

### Post by Hei Ku on 2009-07-11
Probá la contraseña igual al nombre de usuario. Y si no, llamá a los que te la vendieron y preguntales. 

El resto de las posibilidades implica que tengas un CD con Ubuntu y editar archivos, etc., asi que el llamado por telefono me parece que es lo más fácil.

---

### Post by gmunioz on 2009-07-11
Hola sli....:

En principio te sugiero que leas con tranquilidad la documentación y los

posts del foro.

Luego, te informo que para todos los problemas que puedan presentarse

las distribuciones Linux tienen una opción para iniciar en consola, modo

solo texto, como administrador sin contraseña.

Para ello al iniciar el ordenador debes pulsar escape, aparecrá el menu 

del Grub, en el debes elegir la opción recovery mode o single user, según

la distribución que sea, aparecerá un nuevo menu en el que deberás elegir

netroot, con esta opción iniciaras como administrador sin contraseña en

consola

ejecutando (escribiendo y dando enter) las ordenes

cd /home

ls

Tendrás el nombre de usuario, ya que el usuario tiene su directorio de

trabajo con su nombre dentro de /home

Si ejecutas

man passwd

sabrás como cambiar la contraseña.

---

### Post by aledruetta on 2009-07-13
> **gmunioz said:**
> Hola sli....:

En principio te sugiero que leas con tranquilidad la documentación y los

posts del foro.

Luego, te informo que para todos los problemas que puedan presentarse

las distribuciones Linux tienen una opción para iniciar en consola, modo

solo texto, como administrador sin contraseña.

Para ello al iniciar el ordenador debes pulsar escape, aparecrá el menu 

del Grub, en el debes elegir la opción recovery mode o single user, según

la distribución que sea, aparecerá un nuevo menu en el que deberás elegir

netroot, con esta opción iniciaras como administrador sin contraseña en

consola

ejecutando (escribiendo y dando enter) las ordenes

cd /home

ls

Tendrás el nombre de usuario, ya que el usuario tiene su directorio de

trabajo con su nombre dentro de /home

Si ejecutas

man passwd

sabrás como cambiar la contraseña.


¿Che, así de fácil puede entrar alguien a mi PC?

---

### Post by pablo.s on 2009-07-13
> **aledruetta said:**
> ¿Che, así de fácil puede entrar alguien a mi PC?

Las contraseñas se guardan
en un archivo que se llama
shadow, donde están cifradas
con un [hash]("http://es.wikipedia.org/wiki/Hash"). Para poder
cambiar la contraseña es
necesario saber cual es, para
empezar.
Ahi lo que Gabriel señaló es
un indicio para saber como
cambiar la contraseña, pero 
no hay que confundirse con
que dice cómo averiguar cuál
es.

---

### Post by gmunioz on 2009-07-15
Hola ale....:

```
¿Che, así de fácil puede entrar alguien a mi PC?
```

Si.

Si no quieres que utilicen esa entrada opta por:

Editar /boot/grub/menu.lst y dos caminos:

1- Borras ese menu de recuperación o único usuario.

2- Comentas con almohadilla (#) sus líneas.

¿Esto impide el ingreso?

No.

Cualquiera que pulse escape al iniciar el ordenador y 

edite el menu del Grub, agrege las líneas o las descomente

puede ingresar en forma similar.

¿Qué se puede hacer para impedirlo?

Ponerle una contraseña al Grub.

¿Esto impide el ingreso?

No.

Cualquiera con un live-cd o un pendrive booteable

puede acceder a las particiones y a los datos.

¿Qué se puede hacer para impedirlo?

Deshabilitar desde el setup el inicio desde cdrom y usb

y ponerle una contraseña a la bios.

¿Esto impide el ingreso?

No.

Cualquiera que acceda a la motherboard puede borrar la 

contraseña, modificar el setup e iniciar del cdrom o usb

¿Qué se puede hacer para impedirlo?

Cifrar las particiones

Las particiones cifradas son inaccesibles para los intrusos y 

para el usuario que se olvidó la contraseña.

---

### Post by aledruetta on 2009-07-15
jajaja!!! Qué entren entonces!!! Como dice la sabiduría popular: "relájate y goza".

Gracias gmunioz

---

