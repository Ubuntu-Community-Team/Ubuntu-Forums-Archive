---
title: "SESSION no funcionan bien en mi localhost"
date: 2009-11-12
forum: Software
---

### Post by Fabiantronc on 2009-11-12
Estimados.

Hace semanas que tengo problemas con las SESSION, antes use xampp, wampp y phptriad en Windows, ahora estoy usando Ubuntu 9.04 y sigo con el mismo problema.

En mi index.html tengo un formulario para el login, si el usuario y la contraseña es correcta, entonces muestra un mensaje de que me he logueado y luego hago click para que me redireccione al index.html, como ya estoy logueado, no deberia de mostrar el formulario de login, si no que, un mensaje de bienvenida.
El aproblema es que siempre me muestra el formulario. Hasta el momento solo me ha funcionado al subir los archivos al hosting de 000webhost, en miarroba, lycos no me ha funcionado al igual que en mi servidor local.
Leyendo en internet decia que este problema podia ser por el Zone Alarm que bloqueaba las peticiones, pero en Ubuntu no tengo ningun firewall instalado, unos antivirus no mas pero son para escanear archivos de windows.

Tengo instalado Ubuntu 9.04, apache 2.2.11, php 5.2.6-3 y mysql 5.0.75

Aqui esta el codigo del index.html y el validar_usuario.php, el archivo de conexion no creo que sea necesario ya que funciona.

index.html
[http://pastebin.com/f4a0d68ec](http://pastebin.com/f4a0d68ec) 

validar_usuario.php
[http://pastebin.com/f64f24cca](http://pastebin.com/f64f24cca)    

user : usuario
pass : 123456

Aqui pueden probar que el codigo funciona
[http://fabiantronc.hostei.com/test](http://fabiantronc.hostei.com/test)

Aqui pueden probar que el codigo NO funciona
[http://fabiantronc.webcindario.com](http://fabiantronc.webcindario.com)

Chau, saludos :)

---

### Post by Lutho on 2009-11-12
me funciona a la pefeccion ... tal como dices tu 
ingreso el usuario y password

> Has sido logueado correctamente usuariopruebatest 
se supone que debo de pinchar en index

> Bienvenidousuario        
ese resultado me mostro..
por lo que explicas esta bien .. a mi me funciono.

> Ha terminado la session 

---

### Post by Fabiantronc on 2009-11-12
Cual de los 2 links probaste ?
El de hostei o el de webcindario?

Por que el de hostei funciona bien, el de webcindario funciona mal como en mi localhost.

Estoy pensando que tiene que ser algo de la configuracion del servidor, pero todavia no se exactamente que es.

---

### Post by MDK2000 on 2009-11-13
Si tienes razón, en el de hostei funciona bien; en el de webcindario no

Debe ser una configuracion en el servidor tal como dices tu, pero no se cual podría ser

---

### Post by nopersona on 2009-11-13
localhost:popcorn:

---

### Post by Fabiantronc on 2009-11-13
Que raro.

Me podrias dar una copia de tu php.ini ?

---

