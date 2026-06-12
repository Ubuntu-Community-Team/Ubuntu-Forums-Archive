---
title: "Problema con WordPress"
date: 2012-04-24
forum: Software
---

### Post by dam1977 on 2012-04-24
Instalé WordPress en mi Notebook Samsung RV511. Seguí todos los pasos para configurarlo de modo local así puedo experimentar temas y plugins sin arruinar mi sitio en Internet. Anda todo bien, excepto cuando quiero actualizar plugins. Me pide los datos de mi servidor FTP. Le doy los datos de localhost y mi usuario y contraseña, pero luego de intentar instalar las actualizaciones me tira un mensaje de error:

Ha ocurrido un error cuando se actualizaba Akismet: No ha sido posible crear el directorio /var/www/wordpress/wp-content/upgrade/akismet.tmp.

Me da la impresión que tiene alguna incompatibilidad con los permisos de escritura en la carpeta /var/www/wordpress pero no se donde puede estar el error.....

Gracias

---

### Post by marcelo_bur on 2012-04-24
Sugerencia simple.
Instala un Wordpress de prueba en tu servidor y experimentas sin tocar la parte pública de tu sitio, con la ventaja de que vas a ver todo como realmente quedaría en tu sitio.
Saludos

---

### Post by dam1977 on 2012-04-25
Hola Marcelo! Gracias por contestarme. El problema es que tengo instalado todo en el servidor local. Y el sitio se ve perfecto en el navegador. Pero el problema es cuando quiero actualizar los plugins. Ahi se pudre todo porque me pide Datos de Conexión (¿?) o sea, los del FTP. Por qué será? La actualización de los plugins tiene que ser a traves de FTP? Es un problema de configuración del servidor FTP (Filezilla)? Lo borré todo, incluso la base de datos, y reinstalé todo de nuevo y otra vez. Pero en el @@##&&!!! Windows anda todo joya. Pero es justo lo que no quiero.....

---

### Post by marcelo_bur on 2012-04-25
Hola. La verdad es que no se lo suficiente para aconsejarte. Yo nunca armé un sitio en mi máquina, salvo las páginas comunes html. Contrato servicios de hosting desde hace muchos años y siempre hago mis pruebas directamente en servidores remotos. Para ello uso generalmente directorios que luego protejo, para que no puedan ser visitados, y en esa forma nunca tuve inconvenientes. Wordpress lo actualizo sin inconveniente, justamente acabo de actualizar. Pero con otro foro que tengo, que es de un formato muy antiguo en PERL, y del cual he ido modificando el código a través de los años para dejarlo a mi gusto, uso invariablemente el sistema de tener uno para ver como quedan las modificaciones.
Creo que vas a tener que esperar a que alguien con más sabio que yo te tire una mano.
Saludos

---

