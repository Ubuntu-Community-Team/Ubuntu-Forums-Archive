---
title: "[OT] PHP y MySQL"
date: 2011-06-24
forum: Software
---

### Post by mrchelo2002 on 2011-06-24
Hola a Todos. Estoy haciendo unos ejercicios de prueba, luego de haber instalado apache, mysql y php, y tengo un error que no sé cómo salvarlo. Es que no logro conectar la base de datos de mysql a la página de php. El servidor mysql funciona, he creado y llenado tablas, y el php por si solo el apache funciona, con páginas que no usan acceso a datos.
para testear, hice este script:
[COLOR="DarkRed"]<?php
echo "conectando <br>";
$conn=mysql_connect("localhost","pepe","pepito") or die ("error al abrir conexion");
echo "seleccionando db <br>";
$db=mysql_select_db("prueba",$conn) or die("error al elegir base");
echo "select <br>";
$tabla=mysql_query("select * from tabla_prueba",$conn) or die("error al select");
echo "while... <br>";
while ($fila=mysql_fetch_array($tabla)) {
	echo "Esto es $fila[1] <br>";
}
?>[/COLOR]

y el resultado fue que solo imprime el primer echo, y nada más.

Qué me está faltando configurar?
Desde ya muchas gracias.
Saludos.

Marcelo

---

### Post by alfplayer on 2011-06-24
Con respeto, esto parece muy básico. Del tipo de información que se encuentra repetida mil veces en la web.

---

### Post by mrchelo2002 on 2011-06-29
Bueno, si alguien tiene el mismo problema que yo, que instale todas los paquetes desde el centro de software, hay que instalar desde consola los siguientes paquetes:

sudo aptitude install libapache2-mod-auth-mysq
sudo aptitude install php5-mysql

Estos no se instalan al seleccionar php, apache2 y mysql desde el centro de software.

Saludos

---

