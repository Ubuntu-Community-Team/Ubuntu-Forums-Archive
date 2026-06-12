---
title: "¿Porqué no se me instala el firewall?"
date: 2008-08-31
forum: Software
---

### Post by Arcoiris on 2008-08-31
Hola a todos. Soy nuevo aquí.
Acabo de instalar el Ubuntu Ultimate Edition 1.8. Es mi primera experiencia con Linux y traté de iniciarme con algo aparentemente sencillo y completito. 
Lo cierto es que me manejo con un router y traté de utilizar un firewall para mi seguridad, acostumbrado como estoy a Windows. 
El asistente para la configuración del Firestarter, no importa la combinación de las opciones de configuración que elija, siempre me contesta: "No se puede arrancar el cortafuegos. El dispositivo etho no está preparado (...)"
Preguntas (descartando benevolentemente que sea bobo de baba): ¿Creéis que puedo haber cometido algún error en el proceso? ¿Acaso todo se resuma en que no se precise esa protección operando con un router?
Espero vuestras opiniones y consejos. Gracias.

---

### Post by kornykyano on 2008-08-31
Chequeaste las preferencias de Firestarter? creo que el problema pueda ser eso.

---

### Post by Hei Ku on 2008-08-31
Por defecto los puertos de Ubuntu estan cerrados. Te vas a dar cuenta cuando quieras usar BitTorrent, por ejemplo.

Pero me parece que la versión de Firestarter de Hardy tiene un problema, porque a mi me sucede lo mismo si intento correrlo manualmente. Luego me fijo si hay un bug reportado por ese tema.

En principio, el firewall está andando de por sí, asi que no te preocupes. Firestarter sólo te da una forma de configurarlo.

---

### Post by Arcoiris on 2008-08-31
Las preferencias de Firestarter no me resuelven el problema, si no me equivoco. De otra parte, si el sistema ya me protege, según entiendo, esté o no bien configurado el firewall, pues que le den. Gracias por la prontitud de vuestras respuestas.

---

### Post by faktorqm on 2008-08-31
y como tenes configurado el router? si lo habilitas desde ahi es suficiente. salu2!

---

### Post by Arcoiris on 2008-09-01
> **faktorqm said:**
> y como tenes configurado el router? si lo habilitas desde ahi es suficiente. salu2!

Es éste un enfoque que no había contemplado. Pero ni puñetera idea de cómo abordar el asunto. ¿Te importaría describirme el acceso? Gracias.

---

### Post by luks911 on 2008-09-01
> **Arcoiris said:**
> Es éste un enfoque que no había contemplado. Pero ni puñetera idea de cómo abordar el asunto. ¿Te importaría describirme el acceso? Gracias.

Para acceder a la configuración del router vas a tener que poner su IP en el navegador web que uses (Firefox, por ejemplo), y la IP depende del modelo y la marca del router. Podés bsucarla en el manual (si lo tenés), en google o en sitios como [adslzone]("http://www.adslzone.net") y [adslayuda]("http://www.adslayuda.com"). La interfaz para configurarlo también depende del modelo.
Por ejemplo, yo uso un Zyxel al que accedo entrando a [http://192.168.1.1](http://192.168.1.1)

Saludos

---

### Post by faktorqm on 2008-09-01
Para entrar al router, por lo general alcanza con poner la direccion IP que figura como tu puerta de enlace en el navegador. Ahora, si vos te conectas en lo que se llama modo bridge (utilizando pppoeconf o similar) no podes entrar, pues estas usando el router como si fuera un modem exclusivamente. Postea marca y modelo y cualquier cosa lo vemos. Salu2!

---

### Post by Arcoiris on 2008-09-08
No toméis mi silencio como una muestra de descortesía: simplemente me era imposible establecer conexión ya que no me eran reconocidos el nombre ni la contraseña.
En definitiva, como decía ***Hei Ku***, a pesar de que me aparece una ventana, cuando activo esa herramienta, que dice que no ha sido posible cargar el cortafuegos, el Firestarter, sin embargo, vira a "activo" y se queda residente en el "sistray".
La configuración desde el router la ensayaré, con tiempo, una vez que lea cuatro elementos de teoría.
Gracias a todos.

---

### Post by pablo atheist on 2008-09-09
no se si ya te lo dijieron pero el firestarter no se conecta por un bug o algo asi, para solucionarlo:
 abrí una terminal y escribi

```
 sudo gedit /etc/firestarter/firestarter.sh
```

después tenes que cambiar la linea

```
MASK=`/sbin/ifconfig $IF | grep Mas | cut -d : -f 4`
```

le tenes que agregar el tilde al mas o sea que quede

```
MASK=`/sbin/ifconfig $IF | grep Más | cut -d : -f 4`
```
aca tenes la explicacion completa(yo la solución la saque de ahí ): 
[http://lagneuronal.wordpress.com/2007/12/14/problemas-con-el-cortafuegos-firestarter-por-jlob/](http://lagneuronal.wordpress.com/2007/12/14/problemas-con-el-cortafuegos-firestarter-por-jlob/)

además el firewall ya viene instalado con el sistema operativo (viene integrado al kernel creo) el firestarter es simplemente una forma gráfica para manejar al iptables (creo)

saludos

---

### Post by Arcoiris on 2008-09-12
En [http://doc.ubuntu-es.org/Aplicaciones_y_equivalencias](http://doc.ubuntu-es.org/Aplicaciones_y_equivalencias) podemos leer:
“Cortafuegos. No es necesario instalar ninguno adicional: Ubuntu trae un cortafuegos intregrado en el núcleo del sistema llamado Iptables. La instalación por defecto de Ubuntu trae todos los puertos cerrados, por lo que si necesitas abrir puertos adicionales (p2p, mensajería, servidor, juegos, etc.) puedes usar una interfaz gráfica para configurar y administrar el funcionamiento de Iptables". 
Y punto pelota.

---

