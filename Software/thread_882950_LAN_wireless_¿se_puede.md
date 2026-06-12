---
title: "LAN wireless: ¿se puede?"
date: 2008-08-07
forum: Software
---

### Post by brunovecchi on 2008-08-07
Hola! Les hago una pregunta desde la más absoluta y completa ignorancia.

Tengo una compu de escritorio y una portátil; la de escritorio conectada a internet con banda ancha (flash). La notebook tiene placa Wifi funcionando, y ambos equipos tienen un dispositivo bluetooth-usb también funcionando (puedo pasar archivos entre ellas con el applet de gnome-bluetooth).
La cosa es, ¿puedo armar una mini-red inalámbrica? Estuve tratando de buscar algún HOWTO por internet pero como no conozco NADA de la terminología, debo estar poniendo palabras claves que no corresponden y termino en páginas de cómo sincronizar una palm o como hacer andar el wifi.

La pregunta principal es, ¿se puede hacer de esa manera? ¿cómo?

---

### Post by luchardi on 2008-08-07
No estoy del todo seguro que se pueda, en tal caso busca algun help que te diga como conectar una palm o algun celular via BT y una de las pc las tendrias que usar via BT.

Lo mejor seria un router WiFi en el desktop y ademas compartis internet, con BT vas a andar no lento, muuuuuuuy lento 50k como max.

---

### Post by brunovecchi on 2008-08-07
Si, me parece que voy a dejar de dar vueltas y me tendré que conseguir uno de esos... Porque en internet no encontré lo que busco, debe ser que no existe o que no tiene sentido hacerlo.

---

### Post by luchardi on 2008-08-07
Hoy en dia que la norma G es el Standard y la nueva N va en vias de comvertirse en STD, si no te preocupa la velocidad un lindo Router Linksys norma B (11Mbps) te viene barbaro y me imagino que debe estar algo de 200 300 pesos, o menos quizas este sobrevaluandolo en ML DR tenes muchos para elegir.

Suerte!!

---

### Post by brunovecchi on 2008-08-07
> **luchardi said:**
> Hoy en dia que la norma G es el Standard y la nueva N va en vias de comvertirse en STD, si no te preocupa la velocidad un lindo Router Linksys norma B (11Mbps) te viene barbaro y me imagino que debe estar algo de 200 300 pesos, o menos quizas este sobrevaluandolo en ML DR tenes muchos para elegir.

Suerte!!

Mirá, no entiendo mucho eso de las normas (como dijo en el primer post, no sé NADA de redes), pero los precios que estuve chusmeando son parecidos a los que vos ponés, incluso creo haber visto esos linksys...
Una preguntita, ¿funcionan con Linux, no? ¡Muchas gracias por la sugerencia y el consejo!

---

### Post by luchardi on 2008-08-07
Las normas son como si fueran los protocolos que existen dentro de WiFi.

Te paso un link que tiene mucha información, igualmente en internet vas a encontrar mucha más seguramente:

[http://en.wikipedia.org/wiki/Wifi]("http://en.wikipedia.org/wiki/Wifi")

No se que conexión tenes si ADSL o Cable aunque mucho no importa, la idea es que conectes de la forma siguiente para que la conexión (el simulador de discado en ADSL) se haga por parte del Router y la PC quede como si fuera una RED de una empresa cableada e independiente. Con esto te olvidas sea cual sea el sistema operativo que uses pones la placa de red en DHCP automatica y listo, se encarga el router de todo.

Hoy seguramente tenes conectado así:

PC <----------> Modem (adsl / cable)

Y deberias conectar de esta forma (no te preocupes si te compras un linksys que el tutorial que arranca te indica paso por paso que tenes que ir haciendo)

PC < --------> Router WiFi <----------> Modem (adsl / cable)

Lo unico que vas a tener que pasar de la configuracion de tu PC al modem es los puertos del emule/amule y torrent u otras apps. que uses porque por defecto vienen cerrados.

Te recomiendo leer bien sobre WEP y WPA que son los algoritmos de encriptación de la red inalambrica asi podes segurizar tu red.

Cualquier duda preguntá, seguro muchos podamos responderte, yo ya pase por todo lo que te puedas imaginar con WiFi en mi casa así que algo de experiencia con los linksys tengo.

Saludos.

---

### Post by marianom on 2008-08-08
Yo me compré uno ayer, $340 pesos creo (¿se nota mucho que no lo pago yo?): no te preocupes por el sistema operativo ya que es independiente del modem, solo necesitas tener un navegador web para configurarlo (ponele MAC filtering y WPA2 para dejarlos a los okupas del wireless ajeno con las ganas) y eso si: cambiale la pass del admin lo más rápido que puedas.

Es medio lenteja eso si, el netgear que reventé la semana pasada me duró 4 años y era una máquina, lastima que no pude encontrar esa marca (el mercado parece inundado de linksys, están en todos lados): pero la velocidad deja un poco que desear, es notorio (por lo menos para mi que le doy con todo). Por lo demas buen alcance: lo tengo en el segundo piso de casa y alcanza todos los lugares a donde voy con la notebook.

---

### Post by faktorqm on 2008-08-08
Hola, tenes que poder tranquilamente, siempre y cuando aceptes el ancho de banda del bluetooth ([http://es.wikipedia.org/wiki/Bluetooth](http://es.wikipedia.org/wiki/Bluetooth)).
este no aporta mucho que digamos pero bueno, t lo puse = ; [http://answers.yahoo.com/question/index?qid=20071011033740AAwMqyb](http://answers.yahoo.com/question/index?qid=20071011033740AAwMqyb)
este dice algo mas tecnico [http://wiki.xda-developers.com/index.php?pagename=InternetOverBluetoothNetwork](http://wiki.xda-developers.com/index.php?pagename=InternetOverBluetoothNetwork)
aca en vez de hacerlo en la ipaq, hacelo en la pc (es lo mismo) y ya: [http://www.tweaks2k2.com/How_to/bluetooth_network.htm](http://www.tweaks2k2.com/How_to/bluetooth_network.htm)

Salu2!

---

### Post by brunovecchi on 2008-08-08
Muchas gracias a los tres, me vino muy bien la información. Cuando mi bolsillo se reponga de las trompadas que le estuve dando, me compro el router (seguramente uno como el que te compraste, marianom) y lo voy a intentar conectar como dicen.
Mientras tanto, voy a seguir las guías que me pasó faktorqm, pareciera que es factible de hacer.

Cualquier cosa les comento el desenlace, seguro que con alguna otra pregunta los voy a molestar! :)

Saludos muchachos!

---

### Post by faktorqm on 2008-08-08
Claro, es que la onda es que uses los cosos bluetooth como si fueran placas de red normales, o sea, una especie de punto a punto, (el equivalente cableado seria un cruzado entre dos placas de red, el equivalente wi-fi seria "conexion directa", NO AP).
en el ultimo tuto, ahi estas usando lo que te digo yo, o sea, le decis al SO que sea, que comparta la conexion por esa placa(o sea, que haga lo que se conoce como "forwarding" (reenvio) de la conexion por esa placa) y en la otra la configuras como """cliente""" digamos y listo el pollo. si tenes dudas pregunta. salu2!

---

### Post by clasificado on 2008-08-13
Yo lo tengo así :D

Y funciona eh! Nomás que mis adaptadores bluetooth son algo viejos y no transmiten muy lejos, además es lento para transferencia de archivos

Pero para compartir web, anda que es una massa

Clasificado

---

