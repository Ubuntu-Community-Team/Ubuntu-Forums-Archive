---
title: "problema con eclipse pdt en ubuntu 9"
date: 2009-08-28
forum: Software
---

### Post by jrodriguezc on 2009-08-28
Hola, instale el eclipse pdt en la ruta /opt/eclipse
tengo instalado apache2, php5, mysql, corriendo en /var/www
luego defino un workspace /var/www/jona (con permisos 777 y editado en /etc/apache2/sites-available/default)
...pero cuando trato de generar un nuevo proyecto en php, al pinchar el boton
finalizar, me sale el siguiente error:

[http://img220.imageshack.us/img220/5088/pantallazowft.png](http://img220.imageshack.us/img220/5088/pantallazowft.png)

[IMG]http://img220.imageshack.us/img220/5088/pantallazowft.png[/IMG]


Ojala alguien me pueda orientar:


Saludos!

---

### Post by maxmoraga on 2009-08-28
no puedo ver la imagen. al parecer imageshack esta teniendo algunos problemas.

---

### Post by Carlos C on 2009-08-28
Se puede adjuntar la imagen al foro si es que su tamaño no es excesivo ;)

---

### Post by jrodriguezc on 2009-08-28
> **maxmoraga said:**
> no puedo ver la imagen. al parecer imageshack esta teniendo algunos problemas.

Estimado, ya adjunte la imagen al foro, muchas gracias por tu interes.

---

### Post by moreback on 2009-08-29
No se por qué instalas en /opt siendo que Eclipse ya está empaquetado para Ubuntu y lo puedes encontrar en **Aplicaciones -> Añadir y quitar...**

Sld.s

---

### Post by maxmoraga on 2009-08-31
Porque no intentas remover el plugin de PHP y reinstalarlo. Para eso ve a Help->Software Updates eso abrira una ventana 
y en la pestaña Installed software  busca el plugin del problema y desinstalalo(Creo que es "Dynamic Languages Toolkit - Core Frameworks or Dynamic Languages Toolkit - Core Frameworks SDK"). Luego ve a la pestaña available software y en la url corresponiente que ya debiera estar agregada reinstala el plugin(si la url no aparece creo que debiera ser esta [http://download.eclipse.org/tools/pdt/updates/2.0/](http://download.eclipse.org/tools/pdt/updates/2.0/)).

Saludos.

---

