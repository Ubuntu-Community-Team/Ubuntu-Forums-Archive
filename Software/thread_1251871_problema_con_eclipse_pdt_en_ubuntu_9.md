---
title: "problema con eclipse pdt en ubuntu 9"
date: 2009-08-28
forum: Software
---

### Post by jrodriguezc on 2009-08-28
Hola, instale el eclipse pdt en la ruta /opt/eclipse
tengo instalado apache2, php5, mysql, corriendo en /var/www
luego defino un workspace /var/www/jona (con permisos 777 y editado en /etc/apache2/sites-available/default)
...pero cuando trato de generar un nuevo proyecto en php, al pinchar el boton finalizar,
 me sale el siguiente error:

[http://img142.imageshack.us/img142/900/pantallazocei.png](http://img142.imageshack.us/img142/900/pantallazocei.png)



[IMG]http://img220.imageshack.us/img220/5088/pantallazowft.png[/IMG]

Ojala alguien me pueda orientar:


Saludos!

---

### Post by guillermolisi on 2009-08-28
> **jrodriguezc said:**
> Hola, instale el eclipse pdt en la ruta /opt/eclipse
tengo instalado apache2, php5, mysql, corriendo en /var/www
luego defino un workspace /var/www/jona (con permisos 777 y editado en /etc/apache2/sites-available/default)
...pero cuando trato de generar un nuevo proyecto en php, al pinchar el boton finalizar,
 me sale el siguiente error:

[http://img220.imageshack.us/img220/5088/pantallazowft.png](http://img220.imageshack.us/img220/5088/pantallazowft.png)

[IMG]http://img220.imageshack.us/img220/5088/pantallazowft.png[/IMG]

Ojala alguien me pueda orientar:


Saludos!
No se porque no puedo entrar a ver el screenshot en el que tenes el error, pero me llama la atencion que no menciones haber realizado el link a /etc/apache2/sites-enabled para dejar debidamente configurado el site. Sera que te olvidaste de ese detalle ?

---

### Post by jrodriguezc on 2009-08-28
gracias por tu interes [[COLOR=#339900]**guillermolisi**[/COLOR]]("http://ubuntuforums.org/member.php?u=299461"), adjunte la captura de pantalla y subi nuevamente el archivo al servidor de imagenes, podrias ser mas explicito con tu sugerencia, es primera vez que trato de usar eclipse en linux.

Saludos

---

### Post by guillermolisi on 2009-08-28
> **jrodriguezc said:**
> gracias por tu interes [[COLOR=#339900]**guillermolisi**[/COLOR]]("http://ubuntuforums.org/member.php?u=299461"), adjunte la captura de pantalla y subi nuevamente el archivo al servidor de imagenes, podrias ser mas explicito con tu sugerencia, es primera vez que trato de usar eclipse en linux.

Saludos
Ahi vi el error pero me parece que lo que comente no tiene nada que ver con el problema.

Para habilitar un website, ademas de generar la entrada de configuracion en /etc/apache2/sites-available hay que generar un link (ln) a /etc/apache2/sites-enabled. De esa forma Apache "sabe" que hay un site habilitado para atender y lee sus directivas y configuracion.

El mensaje de error que estas recibiendo me parece que habla de una doble declaracion en un path donde se referencia mas de una vez el mismo directorio (el que contiene los plugins).

Aclaro que no use Eclipse.

---

### Post by jrodriguezc on 2009-08-28
> **guillermolisi said:**
> Ahi vi el error pero me parece que lo que comente no tiene nada que ver con el problema.

Para habilitar un website, ademas de generar la entrada de configuracion en /etc/apache2/sites-available hay que generar un link (ln) a /etc/apache2/sites-enabled. De esa forma Apache "sabe" que hay un site habilitado para atender y lee sus directivas y configuracion.

El mensaje de error que estas recibiendo me parece que habla de una doble declaracion en un path donde se referencia mas de una vez el mismo directorio (el que contiene los plugins).

Aclaro que no use Eclipse.


Estimado, como genero el link que me comentas? y ¿tendra alguna solucion eso de la doble declaracion de los plugin? ¿tendra algo que ver con el eclipse oficial tambien instalado?

Saliudos!

---

### Post by guillermolisi on 2009-08-28
> **jrodriguezc said:**
> Estimado, como genero el link que me comentas? y ¿tendra alguna solucion eso de la doble declaracion de los plugin? ¿tendra algo que ver con el eclipse oficial tambien instalado?

Saliudos!
Si tenes dos versiones concurrentes y hay directorios en comun, es posible que se presenten conflictos. Habria que indagar algo mas sobre como instalaste la segunda instancia del IDE.

Respecto del link, tenes dos formas, via escritoro grafico, click derecho sobre /etc/apache2/sites-available/<nombre_del_site> y elegis "Make Link". Esto te crea un archivo con el vinculo que tenes que mover al directorio /etc/apache2/sites-enabled/. Una vez ahi podes renombrarlo para que su nombre sea el mismo que el original (el que esta en sites-available).

Sino, por consola/terminal, creo que tenes que poner ```
ln /etc/apache2/sites-available/<nombre_del_site> /etc/apache2/sites-enabled/<nombre_del_site>
```

Para mas info sobre la ultima alternativa, mada mejor que "man ln" en consola.

---

