---
title: "xinit no such file ubuntu 10.10"
date: 2011-01-31
forum: Software
---

### Post by guaji on 2011-01-31
buenas, hace poco instale ubuntu 10.10 intale compiz y los driver nvidia tengo una tarjeta gforce 8400 gs todo de maravilla hasta que reinicie el pc y me sale este mensaje de error nunca me he topado con este error antes y estoy en blanco agradeceria mucho una ayuda,
 lo unico que puede hacer con ubuntu es iniciar en consola y funciona a la perfeccion excepto por que no puedo iniciar el entorno grafico y reinstalar el driver tampoco me funciono.

---

### Post by asterix77 on 2011-01-31
Parece ser un problema con el controlador de tu tarjeta gráfica

Ejecuta lo siguiente en la terminal para ver mas detalle, y postea la salida

$lspci | grep VGA

Registra la salida del siguiente comando:

$startx

Ese comando inicia el entorno gráfico, si tienes problemas te arrojará el tipo de error.

Si tienes acceso a internet por consola, puedes también intentar lo siguiente:

**$sudo apt-get update && sudo apt-get upgrade**

Te dejo un link que a lo mejor te puede ayudar

[http://www.ubuntu-es.org/node/145123](http://www.ubuntu-es.org/node/145123)

Saludos

---

