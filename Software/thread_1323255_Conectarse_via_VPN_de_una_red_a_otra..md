---
title: "Conectarse via VPN de una red a otra."
date: 2009-11-11
forum: Software
---

### Post by _ZeTa on 2009-11-11
Hola que tal?
mi duda es la siguiente...
es posible conectar 2 maquinas de redes totalmente distintas via VPN?
[obvio que se puede... pero aquí va la dificultad...]
la maquina a la que me quiero conectar, se encuentra dentro de una red muy grande
[la de mi trabajo]
y el asunto es que existen 4 cortafuegos
entonces, para poder conectarme necesito una maquina que me haga las veces de puente...
tengo una maquina
pero hasta ahi llego...
x ejemplo, a esa maquina, puedo conectarme desde cualquier parte via ssh
y desde esa maquina a la mia, pero necesito poder controlar mi maquina de forma gráfica... ¿puedo usar la maquina a la que si tengo acceso como puente entre la maquina desde la que me quiero conectar hacia la otra? si es así... ¿Como?
Alguien sabe como podría hacerlo?

-----

Edito por que lo solucione.

Era tan simple como colocar ssh -X cuenta@ipmaquina

Al colocar "-X", ssh asume que vas a ejecutar los comandos visuales desde la maquina que estas conectado.

sería para que quede mas claro... lo que quería hacer asi:

desde mi maquina
ssh -X cuenta@maquinaacceso

una vez conectado, colocas lo que quieres hacer en la maquina a la que te quieres conectar...
en mi caso vncviewer

vncviewer ipmaquina.

Con eso ya puedo ver mi máquina, usando otra como puente.

Ojala le sirva a alguien.

Saludos!

Nota: para usar vncviewer tiene que estar instalado en las maquinas que usas... Cliente, puente y maquina final.

---

### Post by _ZeTa on 2009-12-14
Ojala le sirva a alguien... xD!

---

