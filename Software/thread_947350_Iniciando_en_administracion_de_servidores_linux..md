---
title: "Iniciando en administracion de servidores linux."
date: 2008-10-14
forum: Software
---

### Post by zeroadrenaline on 2008-10-14
Bueno, la idea es la siguiente, mi intencion es montar un servidor Linux, ya sea Ubuntu o algun otro, en mi Notebook, y que el mismo administre el trafico web, y funcione como file server, para maquinas virtuales instaladas dentro de mi misma notebook.
La idea es poder empesar a aprender como administrar de la mejor manera estas cuestiones, permisos a carpeas, archivos, usuarios windows via smb, y demases.
La pregunta es si alguien uso esta modalidad, funciona bien, es comparable a administrar una red clasica, o las maquinas virtuales tiene caracteristicas que van a hacer la daministracion muy diferente.
El principal, y evidente, motivo por el que intento hacer esto con maquinas virtuales es porque no dispongo de suficientes maquinas, ni una familia dispuesta a que por mis ganas de aprender, se les caiga internet por haber configurado mal IPTABLES jejeje.
Asique en fin, si alguno me puede recomendar algo, desde que tipo de maquina virtual usar (Qemu, Vbox ...) hasa que tipo de servidor, lo que quieran, sera bienvenido.

---

### Post by Hernán-Amaya on 2008-10-14
No te puedo recomendar mucho solo, que tenes unos lindos manuales 

[http://es.tldp.org/htmls/manuales.html](http://es.tldp.org/htmls/manuales.html) 

saludos

---

### Post by sergiom99 on 2008-10-14
fijate aca que el amigo faktorqm puso dos links para unos manuales de servidores:
[http://ubuntuforums.org/showthread.php?t=902278&page=4](http://ubuntuforums.org/showthread.php?t=902278&page=4)

---

### Post by zeroadrenaline on 2008-10-14
> **sergiom99 said:**
> fijate aca que el amigo faktorqm puso dos links para unos manuales de servidores:
[http://ubuntuforums.org/showthread.php?t=902278&page=4](http://ubuntuforums.org/showthread.php?t=902278&page=4)

Dale buenisimo, ya me los baje. Voy a leerlos de apoquito para ver que nececito y poder darle manija.
Que onda CentOS o Ubuntu LTS ? Que Opinana los que saben?

---

### Post by marianom on 2008-10-14
> **zeroadrenaline said:**
> Que onda CentOS o Ubuntu LTS ? Que Opinana los que saben?

Con CentOS vas a aprender a administrar un servidor que te va a servir mucho en el ámbito de una empresa (si un día vas a buscar trabajo por ese lado): esto se debe a que CentOS es un clon de Red Hat y Red Hat es una de las distros linux más extendida en los servidores corporativos (junto a SuSe): saber manejar rpms, SeLinux y gracias similares son importantes si algún día te sientan frente a una distro así y te ponen a trabajar en esos menesteres.
Ubuntu te hace la administración de un server bastante sencilla por la comodidad para instalar paquetes y resolver dependencias (gracias esto a Debian) aunque por defecto solo viene la consola y no hay entorno de escritorio. Un Debian o un Arch también son opciones saludables para aprender mucho.

Más allá de la distro que selecciones mi recomendación es una: arreglatelas sin entorno de escritorio: con la consola tenés el poder para hacer todo lo que necesites y siempre es mejor aprender como se configuran las cosas con las herramientas mínimas para obtener un conocimiento cabal sobre como se tiene que administrar un server.
Algunos hitos para cumplir en el proceso de aprendizaje:
1- instala y configura un apache (con virtual hosts, soporte para ssl, toda la gracia).
2- aprendé a manejar iptables
3- instala y configurá un cliente de correo (exim, postfix o sendmail solo si sos loco).
4- aprendé a automatizar todo lo que puedas con scripts bash.
5- aprendé a hacer backups (por ejemplo con Bacula).
6- poné a correr algunos procesos pesados y desconectá el cable de electricidad y divertite como loco corriendo un fsck! :)

---

### Post by victor_nesta on 2008-10-14
Quiero felicitar a todo ser humano que sea capaz de hacer lo que cito marianom mas arriba.
Es fantástico!!

---

### Post by WanderingKnight on 2008-10-14
De todas formas por favor tené en cuenta que administrar un servidor en tu casa es muy distinto que administrar uno en una situación empresarial. Hay muchas decisiones en este último ámbito que no dependen de vos y a la larga terminan haciéndote la vida más complicada (helllooo dependency hell--sí, SUSE, te estoy mirando a vos y tu extraño concepto de lo que representa un administrador de paquetes).

En tu casa de por sí ya es algo bastante sencillo, setear samba es algo que sale en menos de media hora leyendo la documentación; hay varios scripts de automatización de una instalación de Apache; para un fileserver probablemente lo único que necesitás es un túnel de SSH, mucho espacio y un cronjob si querés backupear archivos; mailserver nunca levanté pero no debe ser muy complicado que digamos (aunque tenés que tener en cuenta que muchos ISPs bloquean el puerto default de SMTP, así que tenés que salir por donde sale Gmail con SMTP, creo que es el puerto 924). Como estás vos solo no tenés limitaciones en cuanto al acceso a internet, reglas complejas de firewall ni falta de acceso físico a los servidores, que son cosas que siempre te complican a la hora de administrar un servidor en una empresa.

De todas formas me parece que lo de las máquinas virtuales te va a complicar la vida (a menos que tengas un maquinón), pero es perfectamente viable. De hecho en el laburo estamos corriend un Debian que con VMware virtualiza 8 servidores distintos.

PD: Y sí, vas a necesitar usar la consola. Mucho. A menos que quieras instalarte Windows 2003 Server :p

PD 2: Obviamente deberías tener un conocimiento básico de:

1) Redes
2) Qué es un puerto
3) Qué es un servicio
4) Cómo funciona un firewall
5) iptables
6) iptables
7) iptables (:p)

---

### Post by sergiom99 on 2008-10-14
> **marianom said:**
> 
3- instala y configurá un cliente de correo (exim, postfix o sendmail solo si sos loco).


si sos guapo y queres hacer las cosas bien, instala un Servidor de correo! (qmail es la eleccion para distros basadas en rpms) [1] 

:lolflag:
saludos/ Sergio

[1] [www.qmailtoaster.org](www.qmailtoaster.org)

---

### Post by marianom on 2008-10-14
> **sergiom99 said:**
> si sos guapo y queres hacer las cosas bien, instala un Servidor de correo! (qmail es la eleccion para distros basadas en rpms) [1] 

:lolflag:
saludos/ Sergio

[1] [www.qmailtoaster.org](www.qmailtoaster.org)

Cliente de correo... en que estaba pensando :) También quise decir servidor de correo y el desafío de campeones sigue siendo un sendmail (el manual de administrador tiene 1300 páginas).

---

### Post by zeroadrenaline on 2008-10-14
Bueno, la verdad, me alegro que haya algunos interesados en el tema, hoy puse a bajar el live dvd de CentOS, me pareció la herramienta mas adecuada para lo que quiero gestionar.
Hoy por hoy, las limitaciones de hard me obligan a tener que testear mi trabajo sobre una maquina virtual, para que quede claro, instalar el servidor, y bajo el servidor correr una VM con por ejemplo un WIN XP, y ver como aplica CentOS los cambios, o ...agadas que haga con el , al Win XP virtualizado.
Tomo como base las indicaciones de marianom y profundizare sobre los 4 o 5 puntos que resalto, sin dejar de lado lo que mencionó otra persona respecto a redes, servicio, firewall, y por supuesto iptables.
Tratare de mantener este thread actualizado, la intención tmb es que desde el hilo, se haga una especie de mini wiki de administrador de servidor, en este caso CentOS, con consultas, consejos y dudas, se ira aportando de apoco, y prometo leer detenidamente cada uno de los comentarios que se hagan, y aplicarlos de ser posible en mi busqueda de la sabiduría servidora.
Un abrazo para todos, sean felices, quiérance mucho, PAZ!.
PD: todo esto despues de rendir mi parcial de Teoría de Números de este sábado para el cual ya estoy bastante paranoico!.

---

### Post by Hei Ku on 2008-10-15
Podés probar con Debian también, aunque CentOS te va a dar la vision del mundo RPM. Debian es usado por un montón de empresas grandes acá en Argentina, y te va a ser más familiar ya que Ubuntu está basado en la versión testing de Debian.

---

### Post by faktorqm on 2008-10-15
estoy de acuerdo con marianom salvo por que se olvido de dovecot...

1- instala y configura un apache (con virtual hosts, soporte para ssl, toda la gracia).
2- aprendé a manejar iptables
3- instala y configurá un cliente de correo (exim, postfix o sendmail solo si sos loco).
4- aprendé a automatizar todo lo que puedas con scripts bash.
5- aprendé a hacer backups (por ejemplo con Bacula).

lo que agregaria como punto 6, no se si por experiencia propia o por que, pero clonar un dominio win 2003, siempre es una buena idea. salvo parte del 1 y todo el 5, se hacer el resto, y aca hay mucha gente que tambien sabe, asi que te vamos a poder ayudar cuando empiecen con 150000 preguntas/segundo.
con el punto 2 difiero un poco, y por lo general si tenes una sola pc oficiando de firewall, te conviene instalarte un openBSD y usar pf (packet filter), tambien es una buena idea.
y con lo del debian y el red hat, o sea, es mas o menos lo mismo, lo unico que cambian son algunas ubicaciones de los archivos y como instalas paquetes, el resto es mas de lo mismo. yo uso Debian, pero para levantar el Asterisk use CentOS.
Guias para servidores tengo 1500 que obviamente no lei todas, pero siempre ayudan.

---

### Post by zeroadrenaline on 2008-10-15
Bueno, como ya dije antes, la intencion es usar CentOS, no lo tomen a mal, pero les pido que centremos los sucesivos posts en este sitema, sino el thread se centra en que sitema es mejor, y no es la idea.
De ultima abrimos otros thread para esa discucion.
Faqtor, ya te pongo una medallita por los manuales, y por tus comentarios, al igual que a marianom.
Gracias y seguiremos leyendo!.
Hoy posiblemente me gestione un disco rigido de 120 y compraré un case bonito, para migrar el home de mi notebook y dejar el de 80 interno para Ubuntu 8.10 (el 30 jejeje) y para CentOS.

---

### Post by sergiom99 on 2008-10-15
> **sergiom99 said:**
> si sos guapo y queres hacer las cosas bien, instala un Servidor de correo! (qmail es la eleccion para distros basadas en rpms)

hoy me mandé una de nabo y tuve a todo el dominio sin recibir mails durante toda la mañana hasta que me dí cuenta la línea de más que había metido donde no debía :mad:

pero no me lo olvido mas!
salu2

---

### Post by sergiom99 on 2008-10-15
peguense un rulo por aca a ver que me cuentan ;-) 
[http://ubuntuforums.org/showthread.php?p=5973955](http://ubuntuforums.org/showthread.php?p=5973955)

---

### Post by zeroadrenaline on 2008-10-16
Bueno, primer chasco, solo por probar, intente correr en qemu el dvd de centos para ver como me trataba, no pude bootear, me tiro un kernel panic - not syncing: Fatal exeption.
El hard es una notebook, una dell inspiron 6400, 1 gb de ram, le di a centos en qemu 128 de ram.
En fin, buscare en google para ver que me dice, si alguno tiene una sujerencia, la probare con gusto, mientrastanto , mi servidor sigue a la espera.

---

### Post by zeroadrenaline on 2008-10-17
Bien, ayer a la noche intente bootear el dvd, y funciona, pero en la notebook tubo problemas con la interfaz, cuando intenta abrir anaconda, la pantalla se pone blanca y empieza a cambiar de colores en una forma muyyyyyyyyyyyyyyyyyyyyyyy lenta e irritante.
Testeado en otro hard anda barbaro.
Mi notebook tiene plaquita ati, la reconocio, cuando arrancó anaconda, me identifica la placa, pero asi todo, no entro, habra que seguir buscando, mientras vere la posibilidad de instalar CentOS en el gabinete de la desktop.

---

### Post by sergiom99 on 2008-10-17
yo personalmente, no haria eso en mi laptop. ni la mula corro para no dejarla prendida mas de lo que la necesito. mucho menos correr un server.
sere medio paranoico, pero prefiero "desgastar" una desktop que tiene repuestos mas baratos.
imaginate que se planche el HDD?

---

### Post by zeroadrenaline on 2008-10-17
Jajajaja, re rata el tipo, na igual no pienso montar un servidor en la notebook, simplemente que la desktop es familiar, entonces para poder jugar con centos, no quiero ponerme a toquetear y dejar a toda una familia sin coneccion durante 2 dias, entendes.
La onda es esa, y mientras me junto unos pesitos para montar un serveer pero desktop, pero bueno, hay que comprar una maquinita para eso, y no hay mucha plata.
Igual gracias por el concejo.
Centos y ati evidentemente no se llevan muy bien, pero le voy a buscar la vuelta, y menos centos con qemu, tengo que ver bien como laburarlo.

---

### Post by marianom on 2008-10-17
Si te sobran $60 por mes podés alquilarte un server en slicehost (buscalo por ahí ya que no quiero hacer publicidad de más): te dan el linux que quieras, root completo y podés hacer y deshacer a tu antojo. Yo tengo un Ubuntu 8.04 server ahí y no me puedo quejar (podés poner centos si queres).

---

### Post by zeroadrenaline on 2008-10-25
Bueno, por cuestiones de hard, momentaneamente tube que instalar Debian, Ubuntu Server 7.10 para ser mas exactos, y yensima en qemu, malisimo, pero bueno, peor es nada. Lo primero que voy a ver es si tengo internet, y si tengo red con el Big Brother (el kubuntu donde corre qemu).
Asique eso sera lo primero, mover bien las cosas hasta que se vean las dos maquinas, y de ahi en adelante, a laburar, lo primero, y supongo que es nativo, ver si puedo administrar la maquinita de qemu desde el BB (Big Brother) via ssh.
Si es así, esta sera mi modalidad de trabajo para cuando tenga montado mi server desktop propiamente dicho, cosa que en unas horas estara listo si todo sale bien!.
Un abrazo y que siguan bien, los mantendre informado.

Para los que les interece, qemu no me permitio bootear con 2 cpu, tube que ponerle 1 sola, y le di un poco mas de ram para compenzar.
Si saben como hacer para habilitar las 2 cpu, escucho atentamente.

---

### Post by hictio on 2008-10-25
Una pregunta, porque lo haces en una maquina virtual?
Es por un problema de espacio fisico en tu casa, o por un tema de ahorro economico?

En mi opinon, si va a ser "servidor", tiene que estar prendido todo el tiempo, y ademas, "sirviendo" algo, o a alguien.

Ademas, de vuelta, en mi opinion :D, en un servidor una de las cosas mas lindas es ver como "respira", como responde al paso del tiempo, a la carga, etc, etc; y lo mejor para eso, es instarle algo como, por ejemplo, [MRTG](http://en.wikipedia.org/wiki/MRTG) o [Zabbix](http://en.wikipedia.org/wiki/Zabbix), y dejar la maquina funcionando un par de semanas (en lo posible haciendo algo de verdad)

No se como sera tu setup, pero hoy en dia cuando es mas o menos comun que haya mas de una maq en una casa, un servidor Linux, empieza a tener sentido, y mas si queres aprender a administrar uno!
Podes ponerlo como firewall, servidor de backups, como NTP server, como DNS (aunque sea caching only), etc, etc, etc.

Yo trataria de conseguir hardware de descarte, esta lleno, ponele dos tarjetas de red, y empeza a jugar, un servidor de verdad, sin GUI, con 64/ 128 MB de RAM estas mas que hecho, el CPU cualquier cosa de 200 MHz sirve, el HDD, de 100 MB para arriba esta mas que bien (excepto para un servidor de backups :p)

Lo ultimo, fijate otras alternativas ademas de Ubuntu Server, CentOS esta bien, especialmente porque es lo que mas se usa; pero no dejes de probar OpenBSD, para servidores, especialmente "los fato en casa con piezas de la calle", anda de mil maravillas.

---

### Post by WanderingKnight on 2008-10-28
> 
Una pregunta, porque lo haces en una maquina virtual?
Es por un problema de espacio fisico en tu casa, o por un tema de ahorro economico?

En mi opinon, si va a ser "servidor", tiene que estar prendido todo el tiempo, y ademas, "sirviendo" algo, o a alguien.


En muchos ambientes empresariales se utiliza un solo servidor que virtualiza muchos otros. Nosotros en el laburo tenemos al menos uno que virtualiza más de 8, y en uno de nuestros clientes hay un servidor Blade que virtualiza alrededor de 16, incluído un Linux.

Que sea una maquina virtual no significa que no vaya a estar prendido todo el tiempo...

---

### Post by hictio on 2008-10-28
> **WanderingKnight said:**
> En muchos ambientes empresariales se utiliza un solo servidor que virtualiza muchos otros. Nosotros en el laburo tenemos al menos uno que virtualiza más de 8, y en uno de nuestros clientes hay un servidor Blade que virtualiza alrededor de 16, incluído un Linux.

Que sea una maquina virtual no significa que no vaya a estar prendido todo el tiempo...

Claro, hombre, pero estas llevando el caso al otro extremo; dudo seriamente que sea en el caso del OP sea mas rentable dejar prendida su workstation 24x7, que poner un Pentium II con 2 tarjetas a trabajar como firewall (y que haga otras cosas ademas, NTP, DNS, file server)
El escenario que vos decis es mas bien para green computing o data centers que para abaratar sus costos (y el de sus clientes :D ) virtualizan la cantidad de OSs en la misma maquina.

---

### Post by WanderingKnight on 2008-10-30
> El escenario que vos decis es mas bien para green computing o data centers que para abaratar sus costos (y el de sus clientes  ) virtualizan la cantidad de OSs en la misma maquina.

Jaja, no creas eh. Aca somos una empresa sumamente chiquita (20~30 personas), pero tenemos varios Terminal Servers de Windows y otra cantidad de servidores especializados, todo virtualizado bajo VMware. Algunos son servidores de desarrollo, otros son servidores de VPNs para conectarse a clientes, etc... y nuestro laburo esta lejos de ser el de un data center.

Simplemente *es efectivo*. De todas formas, si usase otra máquina como servidor exclusivamente, también debería estar prendida 24/7. Ahí no entiendo la diferencia, honestamente.

(Obviamente su máquina sentiría el impacto al estar virtualizando algo todo el día).

---

### Post by hictio on 2008-10-30
Hey,

Me parece que no nos entendemos.
En el escenario de una computadora hogarena, toma una con un disco o dos de 250 GB, 1 GB de RAM o mas, una buena tarjeta de video; por supuesto que podes instalar tu virtualizador favorito y usarlo.

Ahora, si la idea es aprender a administrar un servidor, me parece que lo mejor es, especialmente en una red hogarena:

- asignarle una funcion real (DNS, file server, firewall, NTP server, headless Torrents, etc)
- aprender a medida que el servidor cumple esa funcion

Entonces, a menos que estes dispuesto a dejar tu maq. prendida 24x7, con lo que conlleva de gastos de electricidad., ruido, problemas con hardware si se te rompe algo, lo que vos decis del performance de tener el OS virtualizado activo, etc.
Creo yo que es mas conveniente agarrar una maq con un Pentium de 233 Mhz, con 128 MB de RAM. un par de tarjetas de red, y algun disco, una maquina asi gasta menos electricidad que una moderna, la podes dejar prendida 24x7 (especialmente si cumple alguna funcion), no necesita teclado ni monitor, la administras todo por SSH, y ademas, te deja tu workstation libre para seguir usandola como la venias usando hasta el momento. :D

---

### Post by zeroadrenaline on 2008-10-30
Bueno, para los interesados:
Al fin instale CentOS 5 en una Pen II 700 mHz aprox, con 256 ram, un disco de 80, y hoy mismo le compre la lecto-grabadora de DVD, asique esta a full.
Tiene 2 plaquitas de red, pero no funciona como firewall de nada actualmente.
Tube inconvenientes devido a que quiero ponerla atras de uan coneccion speedy, modem zyxel, y se me esta complicando configurarle como router, se que puedo tenerlo como pppoe sin tenerlo como router, pero me interesa que este configurado de esa forma, asique lucharemos para eso, si alguno lo tiene asi y me quiere ayudar, le agradeceria.
Yo adopte la modalidad mensionada anteriormente por uno de los lectores, el gabinete esta en mi abitacion, y tengo mi notebook y otro gabinete mas tmb ahi adentro, asique soy el unico damnificado por los ruidos, hoy por hoy no esta encendido 24/7 pero en cuanto lo pueda poner de firewall seguramente lo voy a poner delante de la notebook, para probar cosas como ssh a la notebook desde el trabajo, pasando por el server, cerrar el apso, abrirlo, esas cosas, y bueno, seguiremos jugando.
Por ahora intentare hacer que funcione como firewall.
Graias por los aportes, y seguimos en contacto.
PD: Vamos a ver a stallman?, yo llevo la camarita. Saben donde anda el GNU que le quieren entregar, al menos una fotito, asi se lo puede llevar a la casa. Si no saben de lo que estoy hablando busque en los ultimos treath que esta la data sobre TUX por el mundo.

---

### Post by clasificado on 2008-10-30
> **zeroadrenaline said:**
> Tube inconvenientes devido a que quiero ponerla atras de uan coneccion speedy, modem zyxel, y se me esta complicando configurarle como router, se que puedo tenerlo como pppoe sin tenerlo como router, pero me interesa que este configurado de esa forma, asique lucharemos para eso, si alguno lo tiene asi y me quiere ayudar, le agradeceria.


"Telefónica | Speedy" tiene un tutorial que muestra como hacer esto mismo que funciona de maravillas

[http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=197&root=132](http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=197&root=132)

---

### Post by zeroadrenaline on 2008-10-31
Si gracias, pasaba que no me podia conectar bien a la pagina para ver el soporte, ya concegui el tuto y de hecho lo pase a pdf y lo subi a un treath.
Te agradezco, no lo probe pero segurisimo que funsiona.

---

### Post by zeroadrenaline on 2008-11-06
Bueno, migre a ubuntu server 7.10 por cuestiones de velocidad, y repositorios, actualise y ahora tengo un problemonsote, al cargar *Loading event manager ahi hay un error que desconosco, pero el sistema desde aca empieza a tirar una serie de errores, y desde ahi, imposible bootear, no tengo idea que es lo que paso.
El asunto es que, increiblemente, estos errores se solucionaron, puede ser que el error venga de haber reseteado sin dar reboot, o sudo shutdown -r now? no lo se, pero mis pasos fueron, reiniciar en modo recovery, NADA, tire un memtest, lo deje 2 minutitos pero me canse y puse un live cd, booteo todo perfecto, y ahi la reinicie, tmb desde el botoncito maligno, sin esperar, ni nada, pero arranco el servidor, corrio un check de disco, y listo.
No se si alguien tiene idea de por que puede haber pasado esto, me vendria bien, si alguno sabe, que me comenten el porque para no reencontrarme con este problemita again.
Bueno los dejo.
Hoy compre el cablecito cruzado para conectarle la notebook al server, editare unas lineas de iptables, y veremos si podemos poner en dhcp al server para que le de a la notebook una ip.
Escucho ofertas.
Un abrazo para todos.
Busquen los audios de stallman hablando en argentino en la charla en diputados, se pueden descargar, no tienen desperdicio, ese tpo es increible!!.
Cuidence PAZ!.

---

### Post by faktorqm on 2008-11-07
hola, empeza por dejar los links, donde estan disponibles?

otra: por que server ubuntu 7.10? te doy 3 opciones, o debian 4, o cent os 5, o ubuntu server 8.04 que es lts, pero elegir eso le pifiaste feo feo para mi.

De iptables hay posteado bastante en el foro, sino pregunta. Salu2!

---

### Post by zeroadrenaline on 2008-11-07
Para Martin (?) no me acuerdo el nombre, jejeje, faqtor, aca tenes los links para la charla de stallman.
[http://www.criticadigital.com/index.php?secc=nota&nid=13602&pagina=1](http://www.criticadigital.com/index.php?secc=nota&nid=13602&pagina=1)

Aclaro que estaban en el treath de la charla de stallman, pero bueno, los pongo aca tmb.

Instale Ubuntu Server 7.10 por los requerimientos de hard, 8.04 pide mas ram del que puedo disponer, centos 5 idem, no se debian 4, y ya con 256  7.10 anda bastaaaaaaaaaaaaaaante lenteja, bootea en aprox 2 min, quisas es normal en servidores, no lo se.
Bueno, les dejo un abrazo, y vere si puedo configurarle el modo dhcp al server para que la notebook tenga internet filtrada por el server.
uscare info por ahi, vi que hay mucho!.
PAZ!

---

### Post by hictio on 2008-11-07
Pero, como 7.10 lento? Estas usando la version Server, que no tiene interfaz grafica? O instalaste el normal, que tiene Gnome, etc?

256 MB de RAM esta mas que bien para un servidor "caserito", hombre. CentOS necesita 128 minimo, asi que estas bien; pero claro *sin* interfaz grafica.
Aca estan los requerimientos minimos para CentOS (busca 'Recommend minimums' en la pag):

[http://www.centos.org/product.html](http://www.centos.org/product.html)

---

### Post by zeroadrenaline on 2008-11-09
Ubuntu 7.10 sin interfaz rafica. Pero yo creo que el asunto viene de haber instalado todos los modulos de mySQL por ejemplo, o de Mail Server, FTP server etc etc, que bienen opcionales en la instalacion del sistema, y que evidentemente me lo hacen mas pesado.
Sigo lidiando con el dhcp del server.
Les tendre mas noticias, y por supouesto, si funciona, los links utilizados para el trabajo.

---

### Post by faktorqm on 2008-11-10
gracias por los links!

yo en mi laburo instale debian 4 (etch) con 64mb de ram!!!! (era un p2 celeron 333mhz en un pc-chips feo) y tenia todo eso que vos pones. Aclaro que al igual que vos era "para probar". Capaz si se te conectan 30 monos te cuelgan el server, pero bueno. Si queres aprender, esta mas que bien.
No instales interfaz grafica, los servidores "reales" por lo general no llevan interfaz grafica. Suelen tener o interfaz web o nada.

Con respecto a que tarda, te diria que esa parte la dejes para el final. Para que "no tarde", tenes que ver exactamente que modulos cargas en el inicio uno por uno, mirar que servicios estas cargando uno por uno, y por supuesto, compilar tu propio kernel para ese server, te ahorra por lo general un 50% del tiempo en el booteo. Despues tambien podes inventar de instalar algo del estilo del read ahead o el preload para acelerar todavia un cachito mas, pero bueno, primero aprende lo basico ;)

Salu2!!!

---

### Post by zeroadrenaline on 2008-11-11
Agradezco los concejos Martin, lo voy a tener en cuenta, ultimamente por examenes no le estoy dedicando mucho tiempo al trabajo en el servidor, cuando termine la cursada supongo que me pondre a leer mas a fondo y a ponerlo a punto.
Me queda el asunto del dhcp, pero la verdad es que lei poco y nada, asique primero leer, probar, putear, y preguntar, en ese orden.

---

### Post by zeroadrenaline on 2008-11-13
Bueno me dispuse en la dificil tarea de configurar el servidor dhcp con dnsmasq, el hecho de que desconosco algunos aspectos tecnicos del trabajo sobre redes hace la tarea un tanto mas pesada que de costumbre.
Mas aya de esto, con un tuto que segui, [http://tecnoloxiaxa.blogspot.com/2008/10/instalar-y-configurar-un-servidor-dns.html](http://tecnoloxiaxa.blogspot.com/2008/10/instalar-y-configurar-un-servidor-dns.html) llegue a hacer alguos avances (supongo) pero al bootear la maquina observo para mi desason que al tirar STARTING DNS FORWARDER AND DHCP SERVER? dnsmasqdnsmasq:no se pudo crear un socket escuchador: Address already in use.
Sin animo de actuar como parasito, me interesaria saber si alguno tiene idea de que me esta faltando, o que me esta sobrando.
Adjunto algunos aspectos de la config del servidor:

/etc/dnsmasq.conf:

interfaces=eth1 (la placa a la cual esta conectada la notebook que quiere recibir IP)

listen-address=127.0.0.1 (no entiendo realmente por que ese numero)

dhcp-range=192.168.0.2,192.168.0.99,12h (aclaro que el server esta atras de un router que tiene ips del 0.100 a, 0.199, no se si puede afectar la configuracion del dhcp, ip del router es 0.1,ip del server 0.51)

dhcp-host=MAC-ADRRESS-de-la-notebook,ip-que-quiero-que-tenga-la-notebook (192.168.0.50)

dhcp-option=3,192.168.0.51
dhcp-option=6,192.168.0.51 (esa es la ip del servidor, la que le brinda el router, no se por que puse eso ahi, pero lei por algun lado que a un loco le funciono, y dije, bueno yo pruebo)

/etc/resolv.conf

search cpe.telecentro.net.ar
nameserver 127.0.0.1
nameserver xxx.xxx.xxx.29
nameserver xxx.xxx.xxx.30 (estos son los de telecentro, que los saque de mi router, en status me dio estos dos numeritos).

/etc/dhcp3/dhclient.conf

prepend domain-name-server 127.0.0.1;
request sunet-mask, broadcast-address, time-offset, routers, domain-name, domain-name-servers, host-name, netbios-name-servers, netbios-scope;
timeout 30;


Puse solo esos tres archivos porque son los que yo modifique, si hace falta algo ams pidan y veo que les puedo pasar, la verdad es que deje de usar mi notebook porque me niego a desconctarla del server hasta que no tenga dhcp, no puede ser que esta mier... me gane tan facil.
Por las dudas, para no estar haciendo bolude.... el cable que va del server a la notebook tiene que ser cruzado? tiene uno cruzado, mi logica me dice que si, pero ya estoy tan caliente que quiero empesar a descartar errores infantiles.
Disculpen la longitud del post, pero no se me ocurrio una forma mejor de preguntar, espero sepan vaalorar el tiempo que me tomo hacer las transcripciones de los archivos, asi meto presion viste.
Lo que pido solamente, es que si saben cual es la solucion, sean lo mas completos, no dejen nada sobreentendido, porque yo de redes estoy aprendiendo y quisas hay cosas qu eno aclaran por ser muy obvias pero para mi no lo son tanto.
Un abrazo para todos, y si llegaste hasta el final del post, te agradezco el doble.
PAZ!.

---

### Post by ArgentinoGuy on 2008-11-14
Hola hermosa comunidad ubuntu jeje

como siempre acudo a ustedes! bue resulta que en la desktop instale centos para dejarla de una vez por todas como servidor pero como tiene que seguir cumpliendo un cierto papel de desktop para otras personas es que instale virtualbox y pienso instalarle un xp.
La cuestion es que cuando intento prender la maquina virtual me saltan una serie de errores y que llegue a dterminar que no tengo instalado el source code del kernel cosa que tendria que hacer manualmente.

La version de kernel que tengo es **2.6.18-92.1.18.el5 #1 SMP Wed Nov 12 09:30:27 EST 2008 i686 i686 i386 GNU/Linux** y los kernel source que veo en esta pagina son [http://www.gz.us.kernel.org/pub/linux/kernel/v2.2/](http://www.gz.us.kernel.org/pub/linux/kernel/v2.2/) estoy siguiendo los pasos de aca [http://www.linuxheadquarters.com/howto/tuning/kernelsources.shtml](http://www.linuxheadquarters.com/howto/tuning/kernelsources.shtml) 

Bue la pregunta es si tengo que instalar si o si los que coincida con mi version de kernel (cosa que no encuentro) o puedo instalarle cualquiera (el mas nuevo en ese caso).

Espero que alguien me pueda dar una mano, saludos!!!!

---

### Post by sergiom99 on 2008-11-14
y si haces:
```

yum -y install gcc gcc-c++ kernel-devel
yum update
reboot

```

---

### Post by ArgentinoGuy on 2008-11-14
Muchisimas gracias Sergio!!! virtualbox está andando!

gracias en serio muy buena onda.

saludos!

---

### Post by faktorqm on 2008-11-14
> **zeroadrenaline said:**
> Bueno me dispuse en la dificil tarea de configurar el servidor dhcp con dnsmasq, el hecho de que desconosco algunos aspectos tecnicos del trabajo sobre redes hace la tarea un tanto mas pesada que de costumbre.
Mas aya de esto, con un tuto que segui, [http://tecnoloxiaxa.blogspot.com/2008/10/instalar-y-configurar-un-servidor-dns.html](http://tecnoloxiaxa.blogspot.com/2008/10/instalar-y-configurar-un-servidor-dns.html) llegue a hacer alguos avances (supongo) pero al bootear la maquina observo para mi desason que al tirar STARTING DNS FORWARDER AND DHCP SERVER? dnsmasqdnsmasq:no se pudo crear un socket escuchador: Address already in use.
Sin animo de actuar como parasito, me interesaria saber si alguno tiene idea de que me esta faltando, o que me esta sobrando.
Adjunto algunos aspectos de la config del servidor:

/etc/dnsmasq.conf:

interfaces=eth1 (la placa a la cual esta conectada la notebook que quiere recibir IP)

listen-address=127.0.0.1 (no entiendo realmente por que ese numero)

dhcp-range=192.168.0.2,192.168.0.99,12h (aclaro que el server esta atras de un router que tiene ips del 0.100 a, 0.199, no se si puede afectar la configuracion del dhcp, ip del router es 0.1,ip del server 0.51)

dhcp-host=MAC-ADRRESS-de-la-notebook,ip-que-quiero-que-tenga-la-notebook (192.168.0.50)

dhcp-option=3,192.168.0.51
dhcp-option=6,192.168.0.51 (esa es la ip del servidor, la que le brinda el router, no se por que puse eso ahi, pero lei por algun lado que a un loco le funciono, y dije, bueno yo pruebo)

/etc/resolv.conf

search cpe.telecentro.net.ar
nameserver 127.0.0.1
nameserver xxx.xxx.xxx.29
nameserver xxx.xxx.xxx.30 (estos son los de telecentro, que los saque de mi router, en status me dio estos dos numeritos).

/etc/dhcp3/dhclient.conf

prepend domain-name-server 127.0.0.1;
request sunet-mask, broadcast-address, time-offset, routers, domain-name, domain-name-servers, host-name, netbios-name-servers, netbios-scope;
timeout 30;


Puse solo esos tres archivos porque son los que yo modifique, si hace falta algo ams pidan y veo que les puedo pasar, la verdad es que deje de usar mi notebook porque me niego a desconctarla del server hasta que no tenga dhcp, no puede ser que esta mier... me gane tan facil.
Por las dudas, para no estar haciendo bolude.... el cable que va del server a la notebook tiene que ser cruzado? tiene uno cruzado, mi logica me dice que si, pero ya estoy tan caliente que quiero empesar a descartar errores infantiles.
Disculpen la longitud del post, pero no se me ocurrio una forma mejor de preguntar, espero sepan vaalorar el tiempo que me tomo hacer las transcripciones de los archivos, asi meto presion viste.
Lo que pido solamente, es que si saben cual es la solucion, sean lo mas completos, no dejen nada sobreentendido, porque yo de redes estoy aprendiendo y quisas hay cosas qu eno aclaran por ser muy obvias pero para mi no lo son tanto.
Un abrazo para todos, y si llegaste hasta el final del post, te agradezco el doble.
PAZ!.

bue... no se por donde empezar! 

127.0.0.1 es una direccion reservada para una interfaz de red virtual que existe en todas las placas de red del mundo, y se llama loopback. Tiene multiples usos, pero para lo que vos queres hacer esta bien. Ahora me llega la duda, cuando leo que tenes un router, pero mas abajo pones que tenes un cruzado directamente a la notebook... o sea, tenes un router o un cable directo? si tenes un cable directo, esta bien que sea cruzado, me gustaria saber el router a donde esta....

Para no complicarte mas la vida de lo que ya la tenes, te recomiendo enfaticamente que leas esta pagina [http://wiki.xtech.com.ar/index.php/Portada](http://wiki.xtech.com.ar/index.php/Portada) y tambien leas el manual que postie antes, el largo que dice como levantar todos los servicios. Si necesitas mas ayuda, avisame y te subo a rapidshare kilos y litros y pascales de pdf's sobre eso. Salu2!!

---

### Post by zeroadrenaline on 2008-11-15
Ok algunas aclaraciones importantes:
Luego de uan charla interesante con un compañero y amigo de la facu, me avive de las siguientes fallas obvias para un conocedor, pero inadvertidas para un novato:
```
 
Diagrama de la red: 

                    Internet _____ Roter ______PC_Familiar
                                    |_________ Servidor _ _ _ _Notebook

Las lineas continuas son cable recto,las lineas punteadas son cable cruzado.

Servidor: eth2 recto a router ; eth1 cruzado a eth0 notebook.

    Ifconfig eth2 : ip 192.168.0.51 ; eth1 : ip 10.0.0.1
    
    Route : Destination      GW             GM          Flags  Metric   Ifaces
            192.168.0.0      *          255.255.255.0     U      0      eth2
            10.0.0.0         *          255.0.0.0         U      0      eth1
            default      192.168.0.1    0.0.0.0           UG     0      eth2

Notebook: eth0 cruzado a eth1 servidor.

    Ifconfig eth0 : ip 10.0.0.2

    Route : Destination      GW           GM          Flags  Metric   Ifaces
            10.0.0.0         *        255.255.255.0     U      1      eth0
            link-local       *        255.255.0.0       U      1000   eth0
            default        10.0.0.1   0.0.0.0           UG     0      eth0


```
Bueno eso es lo que creo importante para el problema que estoy teniendo.
La situacion es asi: ping responde perfectamente en la red 10.0.0.0 y el servidor tiene salida a internet en 192.168.0.0 , hasta ahi todo barbaro
pero la notebook no tiene salida a internet, se me ocurrio agregar una regla de routeo default con gateway 192.168.0.1 (el router) pero si el eth0 de la note no esta conectado directamente al router no se si tiene mucho sentido.
El asunto es que tengo que ver como darle salida a internet a la notebook.
Si a alguno se le ocurre como lo puedo hacer, me vendria barbaro.
Por otro lado si alguno lee esto y no entiende alguno de los valores o para que sirve cada uno, sientase en la livertad de preguntar, traten de no preguntar cosas fuera de lo que va tratando el hilo asi puedo mantener el hilo ordenado por "progreso de trabajo".
No se si este pedido "restrictivo" viola las reglas del foro, si es asi "hacedmelo saber o grandes dioses administradores del foro!!!".

P.D.: Use muchos puntos en la tabla de route porque sino el sistema de post me amuchaba la info, si ya se, es re cabeza, pero no se me ocurrio un sistema mejor, si alguno conoce la forma amable de hacer esto, le agradeceria que me la diga.
Abrazo para todos, cuidence mucho, PAZ!.

---

### Post by hictio on 2008-11-15
> **zeroadrenaline said:**
> 
P.D.: Use muchos puntos en la tabla de route porque sino el sistema de post me amuchaba la info, si ya se, es re cabeza, pero no se me ocurrio un sistema mejor, si alguno conoce la forma amable de hacer esto, le agradeceria que me la diga.
Abrazo para todos, cuidence mucho, PAZ!.

Porque no pegas la data/ esquema de red de vuelta (seguramente sin los puntos para el espacio) pero dentro de los tags de ['code']['/code']?

(Sacale esas comillas simples que le puse, es solo para que el tag en si se escriba en pantalla.)

---

### Post by zeroadrenaline on 2008-11-15
Buenisimo, es exactamente lo que queria, prolijito como tiene que ser, asi se entiende perfectirijillo!!!

---

### Post by sergiom99 on 2008-11-15
> **ArgentinoGuy said:**
> Muchisimas gracias Sergio!!! virtualbox está andando!

gracias en serio muy buena onda.

saludos!

de nada. sabes las vueltas que di cuando instalé VMware Server la 1ra vez hasta que encontré que con esos 3 paquetes arreglaba todo?? Desde entonces lo tengo en un artículo del KB de la empresa, para poder consultarlo siempre :lolflag:

---

### Post by sergiom99 on 2008-11-15
si bajas el firewall del server, podes salir desde la laptop?
era CentOS, no?
```
service iptables stop
``` (como root)

o sino con el comando setup podes ver la lista de servicios que carga al arrancar, entre otras cosas.
y si queres agregar/borrar alguno por CLI:
```
chkconfig {servicio} on|off
```

suerte!

---

### Post by zeroadrenaline on 2008-11-17
Estoy en un Ubuntu 7.10.
En el iptables no tengo ninguna regla asignada asique esta por defecto, si no me equivoco, deja pasar todo.
Por otro lado otro problea que s eme presento fue el hecho de que la placa que conecta el servidor a la notebook, esa plaquita, si reinicio el servidor, no guarda os valores de ip netmask y broadcast que yo le habia asignado. Hay forma de que los guarde?.

---

### Post by hictio on 2008-11-17
> 
En el iptables no tengo ninguna regla asignada asique esta por defecto, si no me equivoco, deja pasar todo.


Para asegurarte, en consola, o a traves de un Terminal con SSH, tipea:
```

sudo ufw status (ENTER)

```

---

### Post by sergiom99 on 2008-11-17
> **zeroadrenaline said:**
> 
Por otro lado otro problea que s eme presento fue el hecho de que la placa que conecta el servidor a la notebook, esa plaquita, si reinicio el servidor, no guarda os valores de ip netmask y broadcast que yo le habia asignado. Hay forma de que los guarde?.

postea el contenido del archivo de configuracion de eth2 (o sea de la placa q va a la laptop)

---

### Post by zeroadrenaline on 2008-11-17
> **hictio said:**
> Para asegurarte, en consola, o a traves de un Terminal con SSH, tipea:
```

sudo ufw status (ENTER)

```

Status: Not Loaded

Tire el comando en la notebook, en el servidor no tengo el comando, me llama la atencion.

---

### Post by faktorqm on 2008-11-18
> **zeroadrenaline said:**
> Ok algunas aclaraciones importantes:
Luego de uan charla interesante con un compañero y amigo de la facu, me avive de las siguientes fallas obvias para un conocedor, pero inadvertidas para un novato:
```
 
Diagrama de la red: 

                    Internet _____ Roter ______PC_Familiar
                                    |_________ Servidor _ _ _ _Notebook

Las lineas continuas son cable recto,las lineas punteadas son cable cruzado.

Servidor: eth2 recto a router ; eth1 cruzado a eth0 notebook.

    Ifconfig eth2 : ip 192.168.0.51 ; eth1 : ip 10.0.0.1
    
    Route : Destination      GW             GM          Flags  Metric   Ifaces
            192.168.0.0      *          255.255.255.0     U      0      eth2
            10.0.0.0         *          255.0.0.0         U      0      eth1
            default      192.168.0.1    0.0.0.0           UG     0      eth2

Notebook: eth0 cruzado a eth1 servidor.

    Ifconfig eth0 : ip 10.0.0.2

    Route : Destination      GW           GM          Flags  Metric   Ifaces
            10.0.0.0         *        255.255.255.0     U      1      eth0
            link-local       *        255.255.0.0       U      1000   eth0
            default        10.0.0.1   0.0.0.0           UG     0      eth0


```
Bueno eso es lo que creo importante para el problema que estoy teniendo.
La situacion es asi: ping responde perfectamente en la red 10.0.0.0 y el servidor tiene salida a internet en 192.168.0.0 , hasta ahi todo barbaro
pero la notebook no tiene salida a internet, se me ocurrio agregar una regla de routeo default con gateway 192.168.0.1 (el router) pero si el eth0 de la note no esta conectado directamente al router no se si tiene mucho sentido.
El asunto es que tengo que ver como darle salida a internet a la notebook.
Si a alguno se le ocurre como lo puedo hacer, me vendria barbaro.
Por otro lado si alguno lee esto y no entiende alguno de los valores o para que sirve cada uno, sientase en la livertad de preguntar, traten de no preguntar cosas fuera de lo que va tratando el hilo asi puedo mantener el hilo ordenado por "progreso de trabajo".
No se si este pedido "restrictivo" viola las reglas del foro, si es asi "hacedmelo saber o grandes dioses administradores del foro!!!".

P.D.: Use muchos puntos en la tabla de route porque sino el sistema de post me amuchaba la info, si ya se, es re cabeza, pero no se me ocurrio un sistema mejor, si alguno conoce la forma amable de hacer esto, le agradeceria que me la diga.
Abrazo para todos, cuidence mucho, PAZ!.

Hola, el error me parece que esta en la notebook, en la mascara de subred, pusiste 255.255.255.0 y en el servidor pusiste 255.0.0.0, o sea estas haciendo cualquier cosa ahi. O pones todo /8 o todo /24. Voy a asumir que la configuracion del iptables esta bien hecha, y ahi te deberia funcionar, sino postea y te posteo todas las configuraciones.

Con lo del ruteo le pegaste en la tecla: no tiene sentido lo que hiciste.... O sea, vos siempre que pedis un paquete, suponete la ip que devuelva [www.google.com](www.google.com), primero se fija si esta en la misma red (la 10.0.0.0) si no lo encuentra, lo manda al default gateway, 10.0.0.1 y este si no lo encuentra en la red 192.168.0.0 lo manda al default gateway de tu proveedor de internet (no nombro el proceso de averiguacion de DNS, ojo!), y asi sucesivamente hasta que llega. Si vos le pones una ruta por defecto a esa direccion, no pasa nada por que no va a llegar nunca, o siempre va a llegar mediante el default gateway. 

Arregla lo de las mascaras y sino volve a postear. Salu2!

---

### Post by zeroadrenaline on 2008-11-18
```

 Servidor: eth2 recto a router ; eth1 cruzado a eth0 notebook.

    Ifconfig eth2 : ip 192.168.0.51 ; eth1 : ip 10.0.0.1
    
    Route : Destination      GW             GM          Flags  Metric   Ifaces
            192.168.0.0      *          255.255.255.0     U      0      eth2
            10.0.0.0         *          255.0.0.0         U      0      eth1
            default      192.168.0.1    0.0.0.0           UG     0      eth2

```

Para mi el drama esta en el asuntito que en las reglas de Route de los paquetes que vienen desde 10.0.0.0 y quiero que salgan a internet, deverian de tener como GW la ip del eth2 de servidor, 192.168.0.51, asi los paquetes que van a internet pasan por ahi, o me equivoco?.

Lo que me preguntabas acerca de la eth1 del servidor, tiene el netmask que corresponde, pero estan mal declaradas las regras de routeo, voy a ver como declararlas como corresponde.
En un rato te subo las reglas bien puestas, y te digo si funciona.

---

### Post by faktorqm on 2008-11-18
Si eso tambien te iba a decir, te estas rompiendo demasiado el coco con el ip route, creo que hay otras maneras de hacer lo mismo con iptables, y que de paso lo aprendes y es mas facil. Espero tu post y te contesto mas tarde. Abrazo!

---

### Post by zeroadrenaline on 2008-11-18
Bueno, esta es la configuracion actual de la red:

```
 
 
Diagrama de la red: 

                    Internet _____ Roter ______PC_Familiar
                                    |_________ Servidor _ _ _ _Notebook

Las lineas continuas son cable recto,las lineas punteadas son cable cruzado.

Servidor: eth2 recto a router ; eth1 cruzado a eth0 notebook.

    Ifconfig eth2 : ip 192.168.0.51 netmask 255.255.255.0 
             eth1 : ip 10.0.0.1 netmask 255.255.255.0
    
    Route : Destination      GW             GM        Flags  Metric Ifaces
            192.168.0.0      *        255.255.255.0     U      0      eth2
            10.0.0.0         *        255.255.255.0     U      0      eth1
            default      192.168.0.1  0.0.0.0           UG     0      eth2

Notebook: eth0 cruzado a eth1 servidor.

    Ifconfig eth0 : ip 10.0.0.2 netmask 255.255.255.0

    Route : Destination      GW           GM          Flags  Metric Ifaces
            10.0.0.0         *        255.255.255.0     U      1      eth0
            link-local       *        255.255.0.0       U      1000   eth0
            default        10.0.0.1   0.0.0.0           UG     0      eth0
```
Para agregar las reglas en la notebook se utilizaron los siguientes comandos:
```
route add -net 10.0.0.0 netmask 255.255.255.0 dev eth0
route add -net default gw 10.0.0.1 netmask 0.0.0.0 dev eth0
```

Tube que agregar en /etc/network/interfaces mi placa en la notebook y en el servidor, editando el archivo y agregando las siguientes lineas:

```

Servidor: 
auto eth1
iface eth1 inet static
address 10.0.0.1
netmask 255.255.255.0
broadcast 10.0.0.255

Notebook:
auto eth0
iface eth0 inet static
address 10.0.0.2
netmask 255.255.255.0
broadcast 10.0.0.255
gateway 10.0.0.1

```

Este es el script que arme para asignarle a iptables :

```


#Borra todas las reglas anteriores, si existiesen.

iptables -F

#Borra todas las reglas de nat anteriores, si existiesen.

iptables -t nat -F

#Permite forward dentro del servidor, esto es importatnte, un 0 o un 1 significan, tenes o no tenes salida a internet.

echo 1 > /proc/sys/net/ipv4/ip_forward

#Reglas de forward y nat para las dos redes.

iptables -t nat -A POSTROUTING -j MASQUERADE
iptables -A FORWARD -i eth2 -o eth1 -j ACCEPT
iptables -A FORWARD -i eth1 -o eth2 -j ACCEPT
```

Importante al finalizar el script darle permiso de ejecusión:

```


sudo chmod +x /hubicacion_del_script/nombre_del_script
```

Y por ultimo, agregar el script en el archivo /etc/rc.local , así estas reglas son incorporadas cuando se reinicie el servidor, y no las tengo qeu cargar a mano siempre:

```


echo >> /hubicacion_del_script/nombre_del_script


```

Eso fue todo, mi notebook ya tiene salida a internet, y puede ver maquinas de mi otra red, 192.168.0.0 .
Espero les sirva de ayuda, la idea de este extenso thread es ir haciendo un ayuda memoria de cosas utiles. Data, codigo, links, y adjuntos interesantes relacionados al tema servidores.
Si alguno ve algun error, o algo que se podria optimizar, comentelo, y lo testeamos a ver como labura.
Gracias a Martin que estubo firme (faqtor) ayudandome para que pudiese salir al mundo.
Cuidence y los mantendre al tanto de los cambios.
Disculpen la horrible ortografia, PAZ!.

---

### Post by hictio on 2008-11-18
Ahora tenes que convertir el script en un firewall, de momento, esta funcionando solo como una especie de "router".
Tenes que empezar a agregarle reglas para filtrar trafico, fundamentalmente, entrante.

Hay uno bastante bueno, como muchos comentarios, para ver que es lo que hace, y usar como template, buscalo en Google: 

Technion + iptables

---

### Post by faktorqm on 2008-11-19
Bueno, ahora que te anduvo, como te dijo hictio, podes armarte un script de iptables un poco mas elaborado, y no confundir (como suelen hacer) los parametros de red del kernel con el firewall.

PARAMETROS: Cuando vos haces "echo 1 > /proc/sys/net/ipv4/ip_forward" lo que estas haciendo es escribir un uno (entiendase por habilitado o deshabilitado si fuera cero) en un parametro del kernel que te deja redireccionar. Ahora, esto es "al vuelo" (on the fly) y quiere decir que si reinicias se va todo, y ojo, no me parece mal, podes probar mil cosas y mandarte mil y una kga**s que cuando reinicias todo vuelve a estar bien. 

Esos parametros del kernel o de sus modulos se alojan el archivo /etc/sysctl.conf y la linea que va es:

```
net.ipv4.ip_forward=1
```

igual creo que esta comentada en el archivo default de instalacion. Luego, para tomar la configuracion sin reiniciar el comando es 

```
sudo sysctl -p /etc/sysctl.conf
```

Sino cuando reinicias te toma la configuracion que le pusiste ahi. Por defecto el kernel no reenvia ("forwardea") paquetes.

Éstos no son los unicos parametros que existen como te habras imaginado, hay varios muchos y dependiendo de lo que necesites tenes que ir agregando o sacando pero (por cuestiones de seguridad) aca te paso los que uso yo:

tarea para el hogar: averiguar para que sirven y encontrar la clave en sysctl.conf ;)

echo "1" > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts
echo "0" > /proc/sys/net/ipv4/conf/all/accept_source_route
echo "1" > /proc/sys/net/ipv4/tcp_syncookies
echo "1" > /proc/sys/net/ipv4/conf/default/rp_filter
echo "1" > /proc/sys/net/ipv4/conf/all/rp_filter
echo "1" > /proc/sys/net/ipv4/icmp_ignore_bogus_error_responses 

# Saco la redirección ICMP
echo "0" > /proc/sys/net/ipv4/conf/default/accept_redirects
echo "0" > /proc/sys/net/ipv4/conf/all/accept_redirects

# Freno las peticiones ARP
echo "1" > /proc/sys/net/ipv4/conf/1/arp_filter


IPTABLES:

Secuencia que elimina toda posible regla anterior:

```

iptables -F
iptables -X
iptables -Z
iptables -F -t nat
iptables -X -t nat
iptables -Z -t nat
iptables -F -t mangle
iptables -X -t mangle
iptables -Z -t mangle
iptables -F -t filter
iptables -X -t filter
iptables -Z -t filter

```

Algunas protecciones de seguridad:

```

# Rechazo todo para las reglas input, output y forward
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

# Protecciones contra inundaciones SYN
iptables -N syn-flood
iptables -A INPUT -i $DISPOSITIVO_EXTERNO -p tcp --syn -j syn-flood
iptables -A syn-flood -m limit --limit 1/s --limit-burst 4 -j RETURN
iptables -A syn-flood -j DROP

# Me aseguro de que las conexiones tcp nuevas sean paquetes SYN con estado NEW
iptables -A INPUT -i $DISPOSITIVO_EXTERNO -p tcp ! --syn -m state --state NEW -j DROP

# Mantener el estado y/o abrir para conexiones salientes
iptables -A FORWARD -m state --state NEW -i $DISPOSITIVO_INTERNO -j ACCEPT
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -m state --state NEW,INVALID -i $DISPOSITIVO_EXTERNO -j DROP

# Acepto para poder pedir nombres
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

# Acepto paquetes ICMP (ping y amigos) a ambos lados
iptables -A OUTPUT -p icmp -j ACCEPT
iptables -A INPUT  -p icmp -j ACCEPT

```

Capaz este te queda un poquiiiiiito mas claro por que especifica -s (source, o sea fuente) y -d (destiny, o sea destino)

```
# Habilito el enmascaramiento
iptables -t nat -A POSTROUTING -s $RED_INTERNA/$MASCARA_INTERNA -o $DISPOSITIVO_EXTERNO -j MASQUERADE
```

y bueno esto ya es cualquiera pero como no se que queres hacer tampoco te puedo recomendar el comando que va, aca estas mandando todo lo que entra a la otra interfaz y viceversa, o sea, seguridad, cero. No disitngue protocolo, no distingue nada. Se puede mejorar! (y mucho! ;))

```
iptables -A FORWARD -i eth2 -o eth1 -j ACCEPT
iptables -A FORWARD -i eth1 -o eth2 -j ACCEPT
```

Algo un toque mas prolijo capaz es esto:

```
iptables -A INPUT -i $DISPOSITIVO_INTERNO -j ACCEPT
iptables -t nat -A POSTROUTING -s $DISPOSITIVO_INTERNO -o $DISPOSITIVO_EXTERNO -j MASQUERADE
iptables -A FORWARD -i $DISPOSITIVO_EXTERNO -j ACCEPT
```

Despues guardas el script que hayas hecho en /etc/init.d/ con el nombre firewall (o uno mas original todavia jajaja)

Ejecutas todo esto:
```

sudo chmod +x /etc/init.d/firewall
sudo ln -s /etc/init.d/firewall /etc/rc2.d/S99firewall
sudo ln -s /etc/init.d/firewall /etc/rc3.d/S99firewall
sudo ln -s /etc/init.d/firewall /etc/rc4.d/S99firewall
sudo ln -s /etc/init.d/firewall /etc/rc5.d/S99firewall
```

Eso que ves ahi como 2, 3, 4, 5 son los niveles de ejecucion, sino sabes que es, googlea ;) y esos comandos sirven para agregar el script a esos niveles y no te quedes sin firewall cuando arrancas en otro momento del sistema.

Bueno cualquier cosa chiflá. Salu2!!!

---

### Post by zeroadrenaline on 2008-11-19
Cabe la aclaracion ya hecha por mis colegas hackers, las reglas de iptables que yo subi de ninguna manera funcionan como herramienta de seguridad, simplemente redireccionan el trafico web, no tomen esas reglas como una forma de salvaguardar su sistema bajo ningun punto de vista.
Por lo pronto solo tengo esas reglas, ire incorporando algunas nuevas, pero es medio dificil poder hacer tests cuando solo hay un terminar subordinado a ese firewall, con mas maquinas seria mas divertido, ya veremos, cualquier cosa, levantaremos un cyber en casa, un par de racks, y listo, jeejeje, vecinos contentos!!! familiares tmb!!!, novias ni hablar!!!.
Cuidence mucho, PAZ!.

---

### Post by zeroadrenaline on 2009-01-25
Bueno, despues de mucho timepo de difrutar del servidor, habiendo hecho algunos cambios drasticos, como por ejemplo haber migrado a slackware en vez de mantener el Ubuntu Server 7.10, y haber migrado de Ubuntu 8.10 a Debian 4 (etch) en la notebook, volvi para poder tener internet de la misma forma que lo habia hehco anteriormente y para mi felicidad, todo funsiono como antes, con los logicos contratiempos de no saber donde aloja cada distro sus archivos, vuelvo a la red de redes, esta vez con mas sabiduria, y me pone feliz ver que algo que hice hace mucho tiempo, le haya servido a alguien, en este caso, a mi, de modelo para pdoer solucionar un problema serio como ser no tener internet.
Un abrazo para todos, y a seguir llenando de hilos con informacion de configuraciones el foro que siempre le pueden servir a su creador!.
Jeje!.
Abrazo!.

---

