---
title: "Servidor http en Ubuntu. Enlace de archivo"
date: 2009-07-24
forum: Software
---

### Post by Daisaku on 2009-07-24
Hola...
Soy nuevo en el foro. De modo que si me equivoco en algo ruego lo sepan disimular.
Acabo de instalar mi servidor experimental HTTP mediante Apache2, y ahora quisiera que las personas que lo visiten no tengan sólo una página de inicio, sino que puedan enlazarse otras con diferentes contenidos.
De momento lo que más me urge, es saber cómo generar un enlace a un archivo de audio que guardé en la carpeta /var/www
Al ser también nuevo en Linux Ubuntu, son millones las dudas que me van surgiendo y no quiero apabullarlos con miles de ellas; pero ésta me resulta realmente importante.
Si alguien me puede explicar con palabras simples cómo generar ese hipervínculo mucho lo agradeceré.
Desde ya, muchas gracias.
 
Daisaku

---

### Post by juancarlospaco on 2009-07-25
En realidad el enlace es igual a la ruta/nombre de archivo luego de **/var/www/**
o sea, si pones un archivo que se llame " **faisbook.php** " 
el enlace desde internet seria, **[www.nombredehost.com/faisbuc.php](www.nombredehost.com/faisbuc.php)**
si creas una carpeta llamada **misupercarpeta** y adentro le metes **faisbuc.php**,
el enlace seria **[www.nombredehost.com/misupercarpeta/faisbuc.php](www.nombredehost.com/misupercarpeta/faisbuc.php)**

:)

---

### Post by sergiom99 on 2009-07-26
@Daisaku: Bienvenido al foro.
Fijate que aca tenes un muy buen tutorial que te va a servir para empezar con Apache y demases> [http://ubuntu-ar.org/node/206](http://ubuntu-ar.org/node/206)

Suerte!

---

