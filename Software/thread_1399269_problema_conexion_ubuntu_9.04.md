---
title: "problema conexion ubuntu 9.04"
date: 2010-02-05
forum: Software
---

### Post by luchorojo on 2010-02-05
hola a todos acabo de instalar ubuntu 9.04 y todo bien menos internet, solo puedo ver los resultados de busqueda de google pero no ingresar a ninguna web, en el IRC me recomendaron hacer varias pruebas, entre ellas fijarme de no estar con un proxy y eso quedo ok, hacer ping a las web q no puedo ingresar como por ejemplo powers.cl y me dio ping de 38 ms, verificar la ip con ifconfig etc.
otro datos son: 

[LIST]
[*]tengo banda ancha movistar de 1 MB con modem ZTE zxdsl 831II
[/LIST]

[LIST]
[*]el programa de mensajeria pidgin me funciona sin ningun problema al conectarme a mi cuenta msn
[*]no puedo descargar paquetes ni actualizar ubuntu se queda pegado con este mensaje [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) jaunty-updates/main Packages
98% [Esperando las cabeceras], antes de eso me salen varios errores 404 y dice fallo de conexion
[/LIST]

[LIST]
[*]navego con firefox y no he podido actualizarlo, tampoco puedo instalar otros navegadores, pq no se descargan los paquetes
[*]no se si el problema sea solo ubuntu ya que tengo otra version: MUSIX y en esta no se conectaba nada de nada internet tanto en version live como instalada en el disco duro.
[*]lei en algun lugar q posiblemente el modem tuviese un firewall pero es imposible acceder a el con 192.168.1.1 ni con 192.168.1.0, ni 192.168.0.1 etc, he probado montones, si alguien sabe si se puede hacer esto y conoce la ip para hacerlo seria de gra ayuda para mi ya que en movistar no me dicen nada.
[/LIST]
en definitiva solo puedo ver los resultados de google, ver gmail, usar pidgin, y acceder con mucha suerte a alguna web como por ejemplo [http://www.mono-project.com/Main_Page](http://www.mono-project.com/Main_Page) todas las demas webs no puedo verlas, ni actualizar nada, ya no se que hacer, he buscado en google a traves de windows alguna solucion pero no he dado con clavo en 3 dias, bueno eso, saludos

---

### Post by luchorojo on 2010-02-06
porfa alguna ayuda, alguien q tenga este modem zte zxdsl 831II y q le funcione bien con ubuntu q me de alguna luz, realmente quiero usar ubuntu y no quiero volver a windows, porfa, no me entra en la cabeza que solo google, gmail y pidgin funcionen y el resto no, es realmente frustrante probar posibles soluciones y no dar con la correcta, ni siquiera las paginas de ubuntu me funcionan, saludos

---

### Post by Carlos C on 2010-02-07
Puede ser que tengas un problema de dns. Intenta cambiar los dns que usas por los de opendns:

[http://ubuntuforums.org/showpost.php?p=7316309&postcount=3](http://ubuntuforums.org/showpost.php?p=7316309&postcount=3)

No pierdes nada con probar.

Saludos.

---

### Post by luchorojo on 2010-02-12
definitivamente no son las dns, lleve el laptop a otra conexion con router y funciona bien... al parecer es el put* modem que me dejo telefonica esta completamente bloqueado, es imposible ingresar a su configuracion, por lo menos para mi, ya probe de todo, y al abrirlo, ya que el sello de garantia estaba roto, note q hay una especie de puerto libre donde deberia ir un chip o algo, supongo q telefonica lo dejo inhabilitado y configurado a su pinta para asi bloquear los puertos q usan los p2p y otras tonteras, pero al parecer tambien bloquea ubuntu, para que  hablar de la distro musix que es la que realmente quiero usar y que no se conecta a nada de nada, bueno les recuerdo que el modem es el ZTE zxdsl 831II, una basura, es super desalentador, recuerdo cuanto me esforce la primera vez q use ubuntu y tenia un modem speedtouch y tambien fue un leseo conectarlo, pero por lo menos esa vez lo resolvi con ayuda de algun foro linux ya no recuerdo cual, y ahora estoy entre comprarme un router nuevo, o dejarme de cabecear y quedarme en windows, una lastima, siempre encontrar los mismos problemas de compatibilidad con todo.

---

### Post by Carlos C on 2010-02-13
> **luchorojo said:**
> es super desalentador, recuerdo cuanto me esforce la primera vez q use ubuntu y tenia un modem speedtouch y tambien fue un leseo conectarlo, pero por lo menos esa vez lo resolvi con ayuda de algun foro linux ya no recuerdo cual, y ahora estoy entre comprarme un router nuevo, o dejarme de cabecear y quedarme en windows, una lastima, siempre encontrar los mismos problemas de compatibilidad con todo.
Creo que has tenido mala suerte, en general no es tanto problema conectarse, salvo cuando tienes un hardware poco común.

Mira si este enlace te sirve de algo:

[http://tecnicoenlaplata.blogspot.com/2008/08/un-mnimo-apunte-cmo-configurar-el-modem.html](http://tecnicoenlaplata.blogspot.com/2008/08/un-mnimo-apunte-cmo-configurar-el-modem.html)

---

