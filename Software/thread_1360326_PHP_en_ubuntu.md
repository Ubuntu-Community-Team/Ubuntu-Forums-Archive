---
title: "PHP en ubuntu"
date: 2009-12-20
forum: Software
---

### Post by leonardo83 on 2009-12-20
Buenas, tengo una consulta bastante tonta...pero consulta al fin.  Tengo ubuntu Jaunty y me baje un libro de programacion php para aprender, ya que me intereso bastante. Pero quiero instalar el programa en ubuntu para practicar y demas, me podrian ayudar a decir como se instala? :confused:

Por ahi lei que habia un programa llamado php5 pero que tenia problemas con las licencias o algo similar y que no funcionaba bien, si alguien usa php en ubuntu o sabe como instalar le pediria que me ayude porque no tengo idea ni como se llama el programa, estoy tocando de oido :lolflag:

Saludos, espero respuestas!

---

### Post by Fistandantilus on 2009-12-20
Wenas!.

```

sudo apt-get install apache2 php5

```y si necesitas MySQL:

```

sudo apt-get install mysql-server mysql-client

```Si mal no recuerdo al instalar php automaticamente te configura el apache. Para chequearlo crea el archivo "/var/www/test.php" con lo siguiente:
[php]
<? phpinfo() ?>
[/php]Luego desde cualquier browse ingresa: "127.0.0.1/test.php". Si todo esta bien deberia mostrarte un monton de información sobre la configuración de PHP.

Saludos!.

---

### Post by leonardo83 on 2009-12-20
> **Fistandantilus said:**
> Wenas!.

```

sudo apt-get install apache2 php5

```y si necesitas MySQL:

```

sudo apt-get install mysql-server mysql-client

```Si mal no recuerdo al instalar php automaticamente te configura el apache. Para chequearlo crea el archivo "/var/www/test.php" con lo siguiente:
[php]
<? phpinfo() ?>
[/php]Luego desde cualquier browse ingresa: "127.0.0.1/test.php". Si todo esta bien deberia mostrarte un monton de información sobre la configuración de PHP.

Saludos!.


Gracias man! voy a ver que onda, justo me estaba bajando un programa llamado XAMPP de aca, parecia sencillo:

[http://www.apachefriends.org/en/xampp-linux.html#372](http://www.apachefriends.org/en/xampp-linux.html#372)

voy a ver que onda sigueindo lo que vos decis tambien, gracias.
Cualquier otra ayuda es bienvenida :)

---

### Post by z37a on 2009-12-21
> **leonardo83 said:**
> Gracias man! voy a ver que onda, justo me estaba bajando un programa llamado XAMPP de aca, parecia sencillo:

[http://www.apachefriends.org/en/xampp-linux.html#372](http://www.apachefriends.org/en/xampp-linux.html#372)

voy a ver que onda sigueindo lo que vos decis tambien, gracias.
Cualquier otra ayuda es bienvenida :)

XAMPP es esactamente lo mismo que logras con lo que te pasaron antes, solo que XAMPP es un paquetes fuera de la distribucion, y lo otro es usar los paquetes propios de la distribucion, los cuales estan mas testeados y seguramente son mas estables, te recomiendo no usar XAMPP si no ir a Sistema->Administración->Synaptic, alli Editar->Marcar paquetes pro tareas... y selecciona LAMP server, es lo mismo que XAMPP pero como te dije usando los paquetes propios de Ubuntu, no de otros.

---

### Post by leonardo83 on 2009-12-21
> **z37a said:**
> XAMPP es esactamente lo mismo que logras con lo que te pasaron antes, solo que XAMPP es un paquetes fuera de la distribucion, y lo otro es usar los paquetes propios de la distribucion, los cuales estan mas testeados y seguramente son mas estables, te recomiendo no usar XAMPP si no ir a Sistema->Administración->Synaptic, alli Editar->Marcar paquetes pro tareas... y selecciona LAMP server, es lo mismo que XAMPP pero como te dije usando los paquetes propios de Ubuntu, no de otros.

ok man, estoy instalando lo que me dijeron antes desde el synaptic, pero antes para probar instale xampp, eso no me va a traer erorres no? como puedo desinstalarlo ahora? porque en synaptic no esta y borrando solo la carpeta opt y demas crean que sea suficiente?
Saludos y muchas gracias

UPDATE: ya lo inastale..ahora como lo ejecuto? que escribo en consola??? :confused:

---

### Post by facundocorradini on 2009-12-22
Qué ganas de complicarse innecesariamente!. 

Para instalar PHP (y apache, y mysql) basta con ir en synaptic a " marcar paquetes por tarea" y elegir "LAMP Server". 


Como lo instalaste, lo más probable es que ya esté funcionando apache y php, para probar basta con ir a [http://localhost](http://localhost) .Eso te va a mostrar tu servidor local. 

Para ejecutar archivos PHP debes ponerlos en el directorio /var/www/ (recomendable usar otro subdirectorio) y los miras desde localhost. 

saludos!

---

### Post by z37a on 2009-12-22
> **leonardo83 said:**
> ok man, estoy instalando lo que me dijeron antes desde el synaptic, pero antes para probar instale xampp, eso no me va a traer erorres no? como puedo desinstalarlo ahora? porque en synaptic no esta y borrando solo la carpeta opt y demas crean que sea suficiente?
Saludos y muchas gracias

UPDATE: ya lo inastale..ahora como lo ejecuto? que escribo en consola??? :confused:

Si ya instalaste XAMP puede generarte un conflicto ya que tendrías instalado ambos apaches a la vez y al iniciar uno atrás del otro el puerto 80 ya esta en uso. La verdad no se como quitarlo al XAMPP, fijate en su web seguro hay algún item!!!

---

### Post by leonardo83 on 2009-12-27
ok manes, gracias, al final borre todo lo de xampp o lamp (como quieran llamarlo) y estoy usandolo con lo que instale desde el synaptic, es un poco mas raro porque el otro me parecia mas amigable graficamente pero buen, cuando quiero ver como va quedando lo pruebo desde localhost jeje.

Saludos gente y gracias! :P

-- THREAD CLOSED --

---

