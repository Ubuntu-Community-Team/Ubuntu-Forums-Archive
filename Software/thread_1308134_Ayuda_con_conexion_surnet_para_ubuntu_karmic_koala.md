---
title: "Ayuda con conexion surnet para ubuntu karmic koala 9.10"
date: 2009-10-31
forum: Software
---

### Post by maXchelo on 2009-10-31
Hola soy nuevo en esto de linux....habia instalado ubuntu 9.04 y habia logrado conectarme a internet despues de mucho atao...hoy actualizé a la ultima version y ahora no logro de ninguna forma conectarme a internet...he intentado varias cosas desde ese comando PPPOECONF y varios ensayo y error..
si alguien por favor pudiera enseñarme como conectarme a internet con alguna guia o tutorial se lo agradeceria mucho o mandarme un correo a [email]maxchelo@gmail.com[/email] 
...de antemano gracias..

PD:
tengo una cuenta de telefonica del sur (telsur)
con el plan witv con 3 teles mi router es un zhone 6212

---

### Post by moreback on 2009-10-31
Hola, bienvenido, primero que todo, en este foro tenemos[** algunas reglas para mantener el orden**]("http://ubuntuforums.org/showthread.php?t=1162750"). Te rogaría que las leyeras, ya que una de ellas es escribir en el foro que corresponde al tema que preguntas.

Se supone que esas conexiones son con PPPoE, pero desconozco cómo se puede hacer con el Network-Manager (Nunca he configurado una).

Supongo que tienes que configurar una conexión DSL, agregar la MAC de tu tarjeta de red (con la que tienes acceso al router) y darle a conectar.

Juega por ahí.

---

### Post by Patriciologico on 2009-11-02
Movido.

Con el Network-Manager no he necesitado poner la MAC, pero si poner "adsl" donde dice tipo.

Lo que me pasa y no se por que es que si uso pppoeconf, luego pierdo la configuracion de network manager y no puedo volver a conectarme por el y dado algunos problemas mas, mejor lo saque y solo uso pppoeconf (Todo esto en Intrepid)

Saludos

---

### Post by AlexDDR on 2009-11-02
lo que pasa es que hay que borrar la configuracion de interface que creo el pppoeconf y ahi vuelve a funcionar el network manager para crear o usar la pestaña de adsl para conectar.


yo ahora no lo necesito  porque me compre un router jejeje

saludos

---

### Post by donmatas on 2009-12-30
holanda ubunteros:

¿alguien podría explicar un "paso a paso" como hacerlo para gente que no cacha chino?

gracias y aguante linux para humanos

salud
DM

---

### Post by themasterdark on 2009-12-30
Hola buenas... 
Revisa este link 

[http://ubuntuforums.org/showthread.php?t=1340962](http://ubuntuforums.org/showthread.php?t=1340962)

En el deje escrito una solución a los problemas de coneccion PPPoe
para realizarlo sin problemas en NetworkManager.

Espero te funcione como a mi.

Saludos

---

### Post by Masrealque_Dios on 2010-01-05
surnet y linux es una mala combinación, telefónica del sur no da soporte linux
pero lo que si pueden hacer es que marquen la conexión pppoe desde el router.

para los mas novatos solo llamen a soporte técnico y le explican la situación, y si la operadora te sale con el cuento que no dan soporte linux, insiste que estas pagando por un servicio y no te funciona, derechos del consumidor y bla bla bla. en un par de dias tendrás un tecnico configurándote el router y dile adiós a las engorrosas conexiones pppoe por wifi

saludos

---

