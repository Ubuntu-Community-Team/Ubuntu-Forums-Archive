---
title: "Preguntas antes de instalar 12.04"
date: 2012-05-10
forum: Software
---

### Post by guillermon on 2012-05-10
Hola a todos:
      Desde que dejé ubuntu 10.04, por actualizar y luego instalar de forma limpia 11.10, comencé a tener muchos problemas, de los cuales casi todos se fueron solucionando; salvo que en mi sesión (no pasa en la de mi mujer), no se apaga! Tengo que hacerlo mediante la terminal. No es gran cosa, pero me resulta molesto.
     La pregunta 1 es: ¿cuáles son las carpetas que estaría bien (no no estaría mal) borrar, para que funcione todo bien?

     Pregunta 2: ¿hay forma de conservar el diccionario de libreoffice (que uno va agregando)?

      Algún otro consejo?
Desde ya gracias

Guillermo

---

### Post by El Potro on 2012-05-12
Hola Guillermo,

Yo la verdad que en este momento usando Ubuntu 10.04 porque estoy podrido de tener que actualizar cada 6 meses o cada 2 años.

En otras computadoras instalé el 11.10, como el que vos estás usando ahora. Hasta donde yo, sé, la diferencia principal es su entorno gráfico, Unity. Ubuntu 12.04 trae este mismo entorno gráfico, Unity, así que ahí no vas a notar grandes cambios. Supongo que debe andar bastante parecido a la 11.10 la 12.04.

Vos por qué necesitás actualizar el sistema? Algo no te funciona?

[QUOTE="guillermon"]La pregunta 1 es: ¿cuáles son las carpetas que estaría bien (no no estaría mal) borrar, para que funcione todo bien?[/QUOTE]
Esta pregunta es difícil, a qué te referís con que "funcione todo bien"?

Vos querés guardar las configuraciones personales que hiciste de cada programa? La clave para eso está en la carpeta /home/$USUARIO o ~/ o sea la llamada "carpeta personal" en el panel de gnome. Allí los programas que usás diariamente guardan archivos de configuración (generalmente en carpetas con su mismo nombre o en archivos que comienzan con un punto) 

Por ejemplo, el diccionario de LibreOffice está en:

/home/$USUARIO/.config/libreoffice/3/user/wordbook/standard.dic

o sino en

/home/$USUARIO/.libreoffice/3/user/wordbook/standard.dic

No creo que todavía uses OpenOffice. Pero si usás openoffice reemplazá libreoffice por openoffice en las rutas anteriores.

Si vas a andar actualizando todo el tiempo (como impone Ubuntu) te recomiendo que particiones tu disco de modo que la carpeta /home/ tenga una partición aparte, así cuando alteres la partición / no pierdas tus configuraciones personales.

Espero que mis humildes consejos te sirvan. Un saludo y suerte!

---

### Post by guillermolisi on 2012-05-12
Unity enla 12.04 funciona mucho mejor (y en algunas casos hasta diria que funciona, directamente) que en sus versiones anteriores.

Por otra parte, el kernel que se utiliza en la 11.10 posee una regersion importante en lo referente al reconocimiento ACPI y que impacta negativamente en todo lo relacionado a la administracion de consumo de energia del sistema.

Si bien el kernel que se incluye y luego actualiza (al la fecha) en la 12.04 no tiene totalmente resuelto este asunto, se nota que hubo avances y el rendimiento de la maquina mejora en forma perceptible, sobre todo si se usa en portatiles.

Es cierto que no es requisito actualizar la version de Ubuntu para utilizar un kernel mas nuevo, pero con el tiempo y la llegada de nuevas versiones de kernel en algun momento algun resorte puede saltar (por el lado de drivers instalados como modulos, por ejemplo).

Creo que para resolver acabadamente el problema del perfil de usuario que es uno de los temas de este thread, primero deberiamos saber que escritorio/entorno grafico se esta usando.

Si un usuario tiene problemas y en la misma maquina otro funciona bien, claramente es una cuestion de archivos de configuracion del primero y la gran mayoria de las veces se soluciona borrando esos archivos para que en la proxima sesion se generen corerctamente.

---

