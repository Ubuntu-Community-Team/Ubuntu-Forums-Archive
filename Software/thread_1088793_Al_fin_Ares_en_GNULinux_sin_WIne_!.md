---
title: "Al fin Ares en GNU/Linux sin WIne !"
date: 2009-03-06
forum: Software
---

### Post by ramiro_md on 2009-03-06
Bueno, de nuevo aparezco yo por estos lados,hace mucho no posteaba y menos aportando alguna solución jeje. Esta vez traigo la solución que muchos usuarios nuevos (acostumbradisimos a window$) estaban esperando. 
Uno de los "bajonasos" que sufre todo nuevo usuario de GNU/Linux (sea cual fuere la distro) es no poder encontrar un p2p tan efectivo como el Ares que usaban en su Window$. Por eso, en esta "guía" voy a mostrar los pasos para poder pillar la red de Ares en nuestro GNU/Linux.
Nota: me funcionó tanto en DEbian Lenny como en Ubuntu INtrepid =).

Lo primero es instalar giFT, que es un porgrama p2p al cual, más tarde, le agregaremos el plugin para que se conecte a la red Ares. Para instalar:
```
aptitude install gift giftcurs giftd giftui libgift0 libgiftproto0 libgnutella-gift libopenft-gift
```

Lo siguiente es instalar el plugin de Ares desde el archivo deb de este enlace: [http://www.esnips.com/nsdoc/e6f8233f-d36c-45fa-a4f6-44bf305ed8ee/?action=forceDL](http://www.esnips.com/nsdoc/e6f8233f-d36c-45fa-a4f6-44bf305ed8ee/?action=forceDL)

Listo, una vez instalado tenemos el programa p2p, el plugin para que enganche la red de Ares, pero nos falta la interfaz gráfica para giFT, es ahora cuando instalamos giftoxic:
```
aptitude install giftoxic
```

Una vez instalado, ejecuten gift-setup para responder algunas preguntas básicas de la configuración del p2p. Te debería quedar algo así:
> setup = 1
hosts_allow = ALL
client_port = 1213
follow_symlinks = 1
plugins = Ares
incoming = ~/.giFT/incoming
completed = 
max_peruser_uploads = 3
hide_dot_files = 1
root = 
max_uploads = 5
shares_hidden = 0
auto_resync_interval = 86400
share_completed = 1
ignore_incoming = 1
downstream = 0
upstream = 0
host [127.0.0.1] =
port [1213] = 
class [1] = 
port [1443] =
http_port [2301] = 
# Aqui empieza la configuración de Gnutella
alias [] = Ingresa algun alias
max_active [-1] = 
lan_mode [0] = 
hosts_allow [LOCAL] = 
port [3677] = 
proxy [] = 
port [59049] = 
# Aqui comienza la configuración de Ares
username [] = Ingresa algún alias
sessions [4] = 15
timeout [300] = 


EXcelente si han llegado aquí sin problemas porque ya estamos terminando :). Lo que hay que hacer ahora es pegar el archivo (que contiene los nodos actualizados de Ares) en la carpeta /home/usuario/.giFT/Ares, en caso de que el arrchivo ya exista reemplazenlo. Lo descargamos de acá [http://www.esnips.com/nsdoc/83653639-c1c4-49c9-818d-04b5280a16e9/?action=forceDL](http://www.esnips.com/nsdoc/83653639-c1c4-49c9-818d-04b5280a16e9/?action=forceDL)

Ahora para poder conectarnos ejecuten en una consola giftd -v esperen a que aparezco algo parecido a esto:
> Ares: as_session.c:227(session_connected): Connected to xxx.xx.xx.xxx : xxxxx

Esto es señal de que ya estamos conectados a la red de Ares desde giFT. Para comenzar a descargar inicien giFToxic SIN CERRAR LA CONSOLA, sino se desconecta (pequeño detalle xD). Bueno espero que les haya servido, acá dejo unos screens de como me anda a mi para que no crean que les doy falsas esperanzas jeje.

Screens:
[http://pixelea.com/ver.php?imagen=762969c17f.png](http://pixelea.com/ver.php?imagen=762969c17f.png)
[http://pixelea.com/ver.php?imagen=f799fd2824.png](http://pixelea.com/ver.php?imagen=f799fd2824.png)
[http://pixelea.com/ver.php?imagen=a4b11defe2.png](http://pixelea.com/ver.php?imagen=a4b11defe2.png)

NOTA: Para descargar el plugin de Ares y el archivo de los nodos, es necesario registrarse en la página que aloja el archivo y luego intentar descargarlo.
NOTA 2: El artículo lo armé conbinando toda la información que hay dando vueltas por internet sobre el tema.

---

### Post by juancarlospaco on 2009-03-07
Lo mismo pero **Auto-Instalable** con GUI creado por quien postea :


Name:	ares-autoinstall-ubuntu.sh
Size:	452.3K (463174 bytes)
Created:	2009-01-14 10:23:03
Shared:	Publicly Shared
URL:	
[http://www.adrive.com/public/0085c0e7525b8dc34fa2123d3ae95bc2019769116484c18b76b4957e7427c53f.html](http://www.adrive.com/public/0085c0e7525b8dc34fa2123d3ae95bc2019769116484c18b76b4957e7427c53f.html)

Downloads:	13

---

### Post by rubioo on 2009-03-07
Parece muy bueno, hoy a la tarde lo pruebo y comento como fue

  
     Gracias y saludos !

---

### Post by eldenico on 2009-03-07
Hola, el problema para cerrar la ventana se soluciona facil, simplemente escribe giftd -v &
Esto hara que corra en segundo plano.

Aun no he logrado que me conecte, sabes que puede ser?

[21:21:51] giftd 0.11.8.1 (Aug  5 2008 14:35:39) started
[21:21:51] Plugin Ares (0.3.0) successfully loaded and initialized
[21:21:51] Ares: asp_plugin.c:230(asp_giftcb_start): Starting up.
[21:21:51] Ares: as_ares.c:88(as_init): Initializing Ares library...
[21:21:51] Ares: as_node_man.c:492(as_nodeman_load): Loaded 400 nodes from node file
[21:21:51] *** GIFT-WARNING: Ares: Requested number of sessions (15) above hard limit. Reducingto 10.
[21:21:51] Ares: as_session_man.c:97(as_sessman_connect): Requested: 15, connected: 0, connecting: 0
[21:21:51] giFT: giftd.c:744(init_transfer): recovered 0 state transfers
[21:21:51] *** GIFT-WARNING: updating index...
[21:21:51] giFT: share_cache.c:855(share_write_index): entered
[21:21:51] giFT: share_cache.c:562(share_build_index): entered
[21:21:51] giFT: share_cache.c:893(share_write_index): descending root: /home/nicolas/.giFT/completed...
[21:21:51] giFT: share_cache.c:465(path_traverse): descending /home/nicolas/.giFT/completed...
[21:21:51] giFT: share_cache.c:1141(share_read_index): entered
[21:21:51] giFT: share_cache.c:562(share_build_index): entered
[21:21:51] giFT: share_cache.c:1157(share_read_index): total shares: 0 (0.00MB)
[21:21:51] reaped child process 8212

---

### Post by ramiro_md on 2009-03-07
> **eldenico said:**
> Aun no he logrado que me conecte, sabes que puede ser?

Mirá a mi me conectó de toque, pero puede ser que se tome unos minutos (no sé hace cuánto esperas..) de todas maneras, fijate si tenés los puertos abiertos en el router (en caso de que tengas) yen el firewall (en caso de que tengas).
Sino yo uso el 1213 (el que viene por defecto), probá configurando ese puerto. También, si es que usas window$ probá con el puerto que usa Ares en window$.
Un saludo y suerte.

---

### Post by rubioo on 2009-03-08
Yo tampoco logro que se conecte

> 
cristian@cristian-desktop:~$ giftd -v
[14:22:36] giftd 0.11.8.1 (Aug  5 2008 14:35:39) started
[14:22:36] Plugin Ares (0.3.0) successfully loaded and initialized
[14:22:36] Ares: asp_plugin.c:230(asp_giftcb_start): Starting up.
[14:22:36] Ares: as_ares.c:88(as_init): Initializing Ares library...
[14:22:36] Ares: as_node_man.c:492(as_nodeman_load): Loaded 400 nodes from node file
[14:22:36] *** GIFT-WARNING: Ares: Requested number of sessions (15) above hard limit. Reducing to 10.
[14:22:36] Ares: as_session_man.c:97(as_sessman_connect): Requested: 15, connected: 0, connecting: 0
[14:22:36] giFT: giftd.c:744(init_transfer): recovered 0 state transfers
[14:22:36] *** GIFT-WARNING: updating index...
[14:22:36] giFT: share_cache.c:855(share_write_index): entered
[14:22:36] giFT: share_cache.c:562(share_build_index): entered
[14:22:36] giFT: share_cache.c:893(share_write_index): descending root: /home/cristian/.giFT/incoming...
[14:22:36] *** GIFT-WARNING: Ignoring path below incoming dir: /home/cristian/.giFT/incoming
[14:22:36] giFT: share_cache.c:1141(share_read_index): entered
[14:22:36] giFT: share_cache.c:562(share_build_index): entered
[14:22:36] giFT: share_cache.c:1157(share_read_index): total shares: 0 (0.00MB)
[14:22:36] reaped child process 7526


---

### Post by uvazquez on 2009-03-08
¿Los nodos están actualizados?
Porque todos mis conocidos (usuarios tanto de linux como de window$) tienen el problema de tener los nodos desactualizados y no poder encontrarlos...

Saludos.

---

### Post by luks911 on 2009-03-08
Es muy probable que sean los nodos. Acá[0] hay unos que están funcionando.

[0] [http://update.kceasy.com/update/ares/nodes](http://update.kceasy.com/update/ares/nodes)

---

### Post by juancarlospaco on 2009-03-08
En mi script estan actualizados...

---

### Post by ramiro_md on 2009-03-09
Yo uso excatamente los nodos que deje en la guía y me anda :confused:

---

### Post by rubioo on 2009-03-09
A mi como no me funcionaba con los pasos que dejo ramiro_md, probe el script pero tampoco funciona :confused:


Edit: Usando los nodos que dejo luks911 me funciona :D

---

### Post by eldenico on 2009-03-09
OK gracias, 

probaré los nodos en cuanto llegue a mi casa.

---

### Post by ramiro_md on 2009-03-09
> **rubioo said:**
> A mi como no me funcionaba con los pasos que dejo ramiro_md, probe el script pero tampoco funciona :confused:


Edit: Usando los nodos que dejo luks911 me funciona :D

Te funcionó con mi manera o con el script ?

---

### Post by eldenico on 2009-03-09
> **eldenico said:**
> OK gracias, 

probaré los nodos en cuanto llegue a mi casa.

Gracias Luks, Funcionó a la perfección, eran los nodos.

---

### Post by rubioo on 2009-03-09
> **ramiro_md said:**
> Te funcionó con mi manera o con el script ?

 Primero probe con tu manera, pero como no funcionaba probe el script. Y finalmente los nodos que dejo lucas.

---

### Post by kiefer on 2009-03-27
> **juancarlospaco said:**
> Lo mismo pero **Auto-Instalable** con GUI creado por quien postea :


Name:	ares-autoinstall-ubuntu.sh
Size:	452.3K (463174 bytes)
Created:	2009-01-14 10:23:03
Shared:	Publicly Shared
URL:	
[http://www.adrive.com/public/0085c0e7525b8dc34fa2123d3ae95bc2019769116484c18b76b4957e7427c53f.html](http://www.adrive.com/public/0085c0e7525b8dc34fa2123d3ae95bc2019769116484c18b76b4957e7427c53f.html)

Downloads:	13

juancarlospaco ya no esta disponible el script en esa dirección, te agradecería que lo subieras a otra. Gracias de antemano

---

### Post by lotvx on 2009-03-27
> **kiefer said:**
> juancarlospaco ya no esta disponible el script en esa dirección, te agradecería que lo subieras a otra. Gracias de antemano

si, por favor, upload

---

### Post by lotvx on 2009-03-27
si, eran los nodos, coloque los ultimos y esta funcionando bien

---

### Post by GGsalas on 2009-03-30
> **lotvx said:**
> si, por favor, upload

Adhiero

---

### Post by leo_liet on 2009-05-23
Perdón por revivir el thread, pero desde que instale desde cero ubuntu 9.04 no puedo hacer que funcione.
Hice lo que dice la guia (usando los nodos y el plugin que usabada en ubuntu 8.10), pero me sale esto:
> 
leo@leo-desktop:~$ giftd -v
[13:23:32] giftd 0.11.8.1 (Aug  5 2008 17:23:32) started
[13:23:32] *** GIFT-ERROR: couldn't load protocol in file /usr/lib/giFT/libAres.la: file not found
[13:23:32] giFT: giftd.c:744(init_transfer): recovered 0 state transfers
[13:23:32] *** GIFT-WARNING: updating index...
[13:23:32] giFT: share_cache.c:855(share_write_index): entered
[13:23:32] giFT: share_cache.c:562(share_build_index): entered
[13:23:32] giFT: share_cache.c:893(share_write_index): descending root: /home/leo/.giFT/completed...
[13:23:32] giFT: share_cache.c:465(path_traverse): descending /home/leo/.giFT/completed...
[13:23:32] giFT: share_cache.c:1141(share_read_index): entered
[13:23:32] giFT: share_cache.c:562(share_build_index): entered
[13:23:32] giFT: share_cache.c:1157(share_read_index): total shares: 0 (0.00MB)
[13:23:32] reaped child process 4450


Si necesitan que ponga otra cosa, avisenme, ya que soy bastante nuevo.

     Chau

---

### Post by luks911 on 2009-05-23
Lo que te dice es que te falta el archivo /usr/lib/giFT/libAres.la que lo instala el plugin para poder usar la red Ares. Decís que lo tenés, pero probá reinstalándolo. Lo bajás de este link[0], es un deb y lo instalás con doble click.
Recién lo probé y funcionó. Cualquier cosa avisá.


[0] [http://www.esnips.com/nsdoc/e6f8233f-d36c-45fa-a4f6-44bf305ed8ee/?action=forceDL](http://www.esnips.com/nsdoc/e6f8233f-d36c-45fa-a4f6-44bf305ed8ee/?action=forceDL)

---

### Post by leo_liet on 2009-05-23
Pero tengo la version de 64 bits, como hago para ponerlo?

---

### Post by guillermon on 2009-08-04
> **luks911 said:**
> Lo que te dice es que te falta el archivo /usr/lib/giFT/libAres.la que lo instala el plugin para poder usar la red Ares. Decís que lo tenés, pero probá reinstalándolo. Lo bajás de este link[0], es un deb y lo instalás con doble click.
Recién lo probé y funcionó. Cualquier cosa avisá.


[0] [http://www.esnips.com/nsdoc/e6f8233f-d36c-45fa-a4f6-44bf305ed8ee/?action=forceDL](http://www.esnips.com/nsdoc/e6f8233f-d36c-45fa-a4f6-44bf305ed8ee/?action=forceDL)
Hola, voy a ese link, me suscribí (lamentablemente) y no pasa nada... cómo es para descargarlo? Funcionará todavía?
Gracias!

---

### Post by mama21mama on 2009-08-05
:D a mi me anda joya ares con giFToxic

de esta manera [me funco]("http://mamalibre.eshost.com.ar/?q=node/220")

Saludos


PD: uso ares como ultimo recurso si no encuentro lo que busco

---

### Post by santiagoward2000 on 2009-08-05
> **guillermon said:**
> Hola, voy a ese link, me suscribí (lamentablemente) y no pasa nada... cómo es para descargarlo? Funcionará todavía?
Gracias!

Hola,
Buscando en Google (porque soy paranoico y no me quería registrar en páginas raras) encontré este link:
[http://www.esnips.com/doc/e6f8233f-d36c-45fa-a4f6-44bf305ed8ee/gift-ares_0.4.0-1_i386]("http://www.esnips.com/doc/e6f8233f-d36c-45fa-a4f6-44bf305ed8ee/gift-ares_0.4.0-1_i386")
Es de la misma página (y si no me equivoco hasta es el mismo archivo), pero con este no tuve que registrarme.
Espero que te sirva.
Saludos!

---

