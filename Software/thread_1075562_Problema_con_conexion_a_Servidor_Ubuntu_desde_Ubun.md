---
title: "Problema con conexion a Servidor Ubuntu desde Ubuntu Desktop"
date: 2009-02-20
forum: Software
---

### Post by ferarg on 2009-02-20
Hola, hace tiempo que vengo instalando servidores ubuntu, pero es la primera vez que me pasa lo siguiente:

Cuando quiero conectar al servidor que tengo instalado en un cliente, desde internet, usando yo Ubuntu (Server o Desktop, de 32 o 64 Bits), y usando SSH, Putty o usando Firefox para conectarme con el apache remoto, o conectado por SSH ejecuto el "mc" o hago un "ls" desde el cual me tiene que enviar muchas lineas, la conexión se congela, pero si hago lo mismo desde MS Windows, usando Putty o Firefox, el equipo responde sin problemas.

Lo probé desde varios PC con Ubuntu, desde varias conexiones de Internet diferentes, y lo mismo, el problema es cuando te conectás al server desde Ubuntu, pero no da ningún error si te conectas desde Windows.

Que puedo hacer?

no es el primer server que armo, pero si el primero que me da este error tan raro.

Si alguien puede darme una idea se lo agradezco, por que no puedo encontrar la solución ni imaginar por donde viene el problema.

Muchas Gracias!!!

FErArg

---

### Post by guillermolisi on 2009-02-20
> **ferarg said:**
> Hola, hace tiempo que vengo instalando servidores ubuntu, pero es la primera vez que me pasa lo siguiente:

Cuando quiero conectar al servidor que tengo instalado en un cliente, desde internet, usando yo Ubuntu (Server o Desktop, de 32 o 64 Bits), y usando SSH, Putty o usando Firefox para conectarme con el apache remoto, o conectado por SSH ejecuto el "mc" o hago un "ls" desde el cual me tiene que enviar muchas lineas, la conexión se congela, pero si hago lo mismo desde MS Windows, usando Putty o Firefox, el equipo responde sin problemas.

Lo probé desde varios PC con Ubuntu, desde varias conexiones de Internet diferentes, y lo mismo, el problema es cuando te conectás al server desde Ubuntu, pero no da ningún error si te conectas desde Windows.

Que puedo hacer?

no es el primer server que armo, pero si el primero que me da este error tan raro.

Si alguien puede darme una idea se lo agradezco, por que no puedo encontrar la solución ni imaginar por donde viene el problema.

Muchas Gracias!!!

FErArg
Cuando probas con Win, es en la misma maquina que probaste con Ubuntu o es otra ?

Ese Ubuntu que usas para conectarte al server, tiene reglas de iptables o esta "como viene de fabrica", sin tocar ?

Tanto Win como Ubuntu, estan identificados en la red con los mismos valores de IP, mascara de red, ruteos, etc. o existen diferencias ?

---

### Post by ferarg on 2009-02-24
Hola, gracias por la respuesta, te cuento:

Hice pruebas desde la misma red, con PC con WinXP y con Ubuntu, hice pruebas desde maquinas virtuales WinXP en PC's con Ubuntu como OS host, y realicé las mismas pruebas desde ordenadores en otras redes, y siempre el mismo error

---

### Post by guillermolisi on 2009-02-24
> **ferarg said:**
> Hola, gracias por la respuesta, te cuento:

Hice pruebas desde la misma red, con PC con WinXP y con Ubuntu, hice pruebas desde maquinas virtuales WinXP en PC's con Ubuntu como OS host, y realicé las mismas pruebas desde ordenadores en otras redes, y siempre el mismo error
Disculpame pero no termino de comprender bien tu ultima respuesta y tampoco si las pruebas las haces con distintos SOs ero en la misma PC con el mismo hardware (como para descartar este factor).

Por otra parte, estaba pensando que podria ser alguna diferencia en la configuracion de la placa de red en esa maquina con Ubuntu, que hace que llegar al otro lado y recibir la respuesta sea tan lenta que parece que se cuelga la comunicacion, respecto de la PC con WinXP (ruteos, DNS, /etc/hosts - \system32\drivers\etc\hosts, etc.).

---

### Post by hictio on 2009-02-24
guillermolisi,

A mi me pasó eso en algunas ocasiones, siempre con SSH, y no exclusivamente con Ubuntu, con otros Linux y con Os X.
Mi sugerencia, fijate que no tenés problemas de DNS; de última, y sólo por testearlo, agregá a mano en el '/etc/hosts' de cada una de las máquinas (servidor Uubntu y cliente Ubuntu) ua entrada para c/u de esas máquinas.

---

### Post by ferarg on 2009-03-06
Hola, el problema fueron los MTU de mi eth local, desde Windows se ve que los mtu rondan los 1400, y en mi eth local estaban en 1500, al poner mtu 1400, funciona todo de maravillas!

Gracias por sus Respuestas

FErArg

[www.FErArg.com](www.FErArg.com)
[www.SerInformaticos.es](www.SerInformaticos.es)
[www.OSXServicios.com](www.OSXServicios.com)

---

### Post by guillermolisi on 2009-03-06
> **ferarg said:**
> Hola, el problema fueron los MTU de mi eth local, desde Windows se ve que los mtu rondan los 1400, y en mi eth local estaban en 1500, al poner mtu 1400, funciona todo de maravillas!

Gracias por sus Respuestas

FErArg

[www.FErArg.com](www.FErArg.com)
[www.SerInformaticos.es](www.SerInformaticos.es)
[www.OSXServicios.com](www.OSXServicios.com)

Y como fue que llegaste a pensar que podia estar por ese lado el problema ?

---

