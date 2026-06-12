---
title: "[SOLVED] emesene ¿que hiciste con mis contactos?"
date: 2008-04-08
forum: Software
---

### Post by vk-cdg on 2008-04-08
Bueno, abro este post para comentarles un problema que me tiene un tanto desconcertado. 
Hace ya un tiempo que uso emesene, pero justamente anteayer hablando por teléfono con un amigo que vive en MDP le pregunto que pasó que no está mas conectado, me dice, si que lo estoy, de hecho te veo y me manda un mensaje. 
El mensaje llega, pero a el no lo tengo en la lista. Cuando lo quiero agregar, me dice que no puede porque el contacto ya existe. 

En resumen, investigando, descubro que tengo contactos que no aparecen en mi lista (viendo todos los contactos, aún los desconectados) de emesene.
La comparación la hice anotando todos los contactos del emesene y luego abriendo el XP que tengo virtualizado y mirando los contactos del MSN de Winbox (windows + virtualbox). Ahí descubro que tengo muchos mas contactos (y grupos) que los que me muestra el emesene.  WTF???

Alguien tiene idea si emesene guarda alguna lista de contactos local que pueda voletear para que se regenere o que es lo que puede estar pasando?

En /home/miperfil/.config/emesene1.0 no hay nada, ya que moví la carpeta esa al desktop y solo pierde la configuración, pero el tongo con los contactos queda igual.

:confused:

---

### Post by niko_3100 on 2008-04-08
A mi tambien me tira errores con lso contactos, cuando quiero agregar uno me tira un error, cuando lo quiero borrar tambien, no maneja bien los contactos... abri el amsn y ahi te aparecen los contactos posta, de a poco despues te van a ir apareciendo en el emesene.

---

### Post by vk-cdg on 2008-04-08
Es rarísimo!
Voy a ver en la web de emesene si hay algún lugar para reportar esto. La jod*a es que mi inglés no es tan bueno como para redactar algo.

---

### Post by marianom on 2008-04-08
Pero si a ese programa lo hizo un argentino. No tienen un lugar donde escribir algunas palabrillas en español?

---

### Post by SLA_leandrin on 2008-04-08
Plop!

Pensé que era algo raro que me había pasado a mi, pero a mi vieja que vive en España no la puedo ver en el emesene, no me fijé con otros como el amsn o pidgin... el tema es que ella a mi tampoco me ve, es rarísimo.

Demos gracias al Cielo por Skype.

---

### Post by vk-cdg on 2008-04-08
No, no, a mi si me ven esos contactos, pero yo no los veo a ellos. 
Es re loco!

No probé configurar el emesene en otra PC o en otro perfil para ver que pasa.

---

### Post by scloneh on 2008-08-07
a mi me funciono esto!!:
solo pega y ejecuta en un terminal!! 

sudo sed -i.bak 's/09607671-1C32-421F-A6A6-CBFAA51AB5F4/CFE80F9D-180F-4399-82AB-413F33A1FA11/g' /usr/share/emesene/emesenelib/XmlTemplates.py

ya podras ver a tus kontaktos, agegar nuevos, eliminarlos, kambiar tu nick etc!! bueno a mi no me hacia nada de eso despues de una aktualizacion de phyton!! kuando lo ejekutes no te debe de salir nada!! bueno si salio bn!! obvio debes de tenerlo cerrado kuando lo ejekutes!! suerte!!

---

### Post by pol666 on 2008-08-07
a bue, escribis como dios manda ^^


esto ya se arreglo era problema de la version 1.0

---

### Post by vk-cdg on 2008-08-07
En mi caso la manoseada de los contactos la hizo pidgim, por eso dejé de usarlo. Los que me tenían en el gtalk... lo siento mucho!

---

