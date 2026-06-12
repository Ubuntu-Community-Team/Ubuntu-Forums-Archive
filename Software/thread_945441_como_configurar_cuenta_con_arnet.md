---
title: "como configurar cuenta con arnet"
date: 2008-10-12
forum: Software
---

### Post by patoruzuold on 2008-10-12
Hola a todos; para los mas viejos usuarios de UBUNTU, yo tengo una copia de la version 8.xx la ultima me podrian decir como configuro la cuenta que poseo en arnet.
Ahora estoy conectado con arnet pero con windows; hay muchos comentarios de ubuntu que es uno de lo mejores pero espero que no se como el redhat que ni siquiera reconocio la mather que tengo.
La mather es un MSI K8TNEO(1). envienme la respuesta a [email]esteban_quito_dellapiazza@yahoo.com.ar[/email]
Desde ya muchas gracias
8-):-\"

---

### Post by Hei Ku on 2008-10-12
El mother te lo va a reconocer sin problemas, es el mismo que usaba yo hasta ayer.

En cuanto a la cuenta de Arnet, no hay problema tampoco, pero nos tenes que decir cuál es el modem que tenés. A partir de ahí, nuestro amigo Faktor te puede dar una mano. También podés buscar en el foro por ese modelo y fijar las guias que hay, porque es algo bastante común.

---

### Post by majatu on 2008-10-13
Si tenes el tipico modem de ahora (el Pirelli rojo) no vas a tener problemas:

Cuendo entres en Ubuntu,metete en firefox y en la barra de direcciones pone [COLOR="black"]**10.0.0.2**[/COLOR] y dale enter.
Despues de que te abra el menu web del modem vas a tener que poner en donde dice usuario la direccion de e-mail que te creo arnet cuando te suscribiste (completa, con @... y todo) y en contraseña la pass que deberias tener escrita por ahi en la cajita del modem o en el contrato de servicio o entre todo lo que te dieron o dijeron de arnet.
Le das a conectar y en un momento deberias de estar online y conectado a internet.

Espero sea tu modem el que te mencione, mi novia tiene ese y asi es la forma mas facil de entrar a internet, porque el cd de instalacion del dialer de arnet (el programa para conectarse que te pone una A de arnet en la barra de tareas de windows no anda en linux, no se si emulandolo en Wine pueda tirar, mas facil intemtar como te dije arriba.

Salutes y espero te ande si tenes el modem Pirelli ;)

---

### Post by patoruzuold on 2008-10-14
Gracias,

---

### Post by EcoMarcus on 2009-04-16
Hola chicos. Soy nuevo en Linux. Tardé en dar el salto, pero lo hice. ¿El detonante? Me harté de hacer click en "recordármelo más tarde" cuando, al iniciar el Word, me decía que mi Office era trucho, lo cual es MUY cierto, aunque eso fue solo la gota que colmó el vaso, uno a punto de llenarse desde hace más de 15 años. Es por eso que hace unos días instalé en mi máquina el Ubuntu 8.04 para compartir el rígido, al menos por el momento, con un WinXP por medio del dual-boot. 
  
   Les escribo para contarles que tengo el mismo problema que tenía **Patoruzuold**, si es que lo pudo resolver: no logro conectarme a Internet a través de Arnet. Es una conexión ADSL a través de un modem **Amigo CA85UR** (es el blanquito, rectangular). El modem está conectado a un puerto USB, es decir, no estoy usando Ethernet. Probé lo que propuso **Majatu** pero no funcionó; Firefox me pone que no encuentra la dirección, como si la buscara en Internet. Bajo Windows, al hacer click en el acceso directo del soft del modem, "USB Endpoint Login", el navegador busca la dirección [http://10.0.0.2/doc/pppacct1.htm](http://10.0.0.2/doc/pppacct1.htm), la cual no me es desconocida, pero bajo Ubuntu no funciona. Probé escribiendo solamente "10.0.0.2" pero obtengo el mismo resultado. ¿Alguna sugerencia, gente?

   Saludos y gracias de antemano.;)

---

### Post by juancarlospaco on 2009-04-18
Conseguir un Modem Router Ethernet, 120 mangos en Mercadoliebre

---

### Post by faktorqm on 2009-04-18
pero tiene entrada ethernet alguno de los dos modems?

@juancarlospaco: ya todos sabemos eso, la onda es no gastar plata ¬¬ hola?

---

### Post by EcoMarcus on 2009-04-19
> **juancarlospaco said:**
> Conseguir un Modem Router Ethernet, 120 mangos en Mercadoliebre

Hola. Agradezco tu sugerencia, Juancarlospaco, pero entiendo que debe existir la forma de configurar un acceso ADSL a Internet en Ubuntu sin tener que recurrir a gastar dinero. En definitiva, de eso se trata en Linux en general, no? Gracias igualmente.

> **faktorqm said:**
> pero tiene entrada ethernet alguno de los dos modems?

@juancarlospaco: ya todos sabemos eso, la onda es no gastar plata ¬¬ hola?

Hola Faktor. Estuve leyendo el thread entre Vero1 y vos en busca de alguna equivalencia con mi problema para sacar ideas. Realmente le pusieron mucha garra, y me alegró pensar que estaba entrando en una comunidad donde se ayudan entre todos. =) He probado algunas cosas que allí se dijeron pero no me funcionaron o, quizás, no las supe aplicar correctamente. Es un solo modem y solo tiene entrada USB. Gracias por responder.

---

### Post by EcoMarcus on 2009-04-22
Chicos:

        Sigo sin poder conectarme a Internet a través de Ubuntu. Les comento lo que hice hasta ahora:

  1) Fui hasta **Sistema > Administración > Red**, y allí, luego de desbloquear las opciones, seleccioné las propiedades para **Conexión Punto a Punto** (sepan disculpar si cometí una burrada pero entiendo bastante poco de telecomunicaciones). Allí, en la solapa "General", elegí un tipo de conexión "PPPoE" y donde me pedía los "Datos de Cuenta", especifiqué mi usuario de Arnet y su respectiva contraseña. En la solapa "Ajustes del modem", seleccioné (era la única posibilidad) "eth0", mientras que en "Configuración" tildé la 1º y la 3º opción (*Establecer el modem  como ruta predeterminada a Internet* y *Reintentar si se corta la conexión...*, respectivamente). Una vez que seleccioné el casillerito que está junto a "Conexión Punto a Punto", pareció que estaba cargando algo, pensé que podía llegar a conectarse incluso, pero luego nada ocurrió.

  2)También en **Sistema > Administración > Red**, probé con **Conexión Cableada** (esto me sonó más a ADSL). Una vez desbloqueada la cuestión, en Propiedades, desactivé el "modo itinerante" (ni idea que es; busqué en la ayuda de Ubuntu pero nada encontré) y seleccioné **Configuración automática (DHCP)**, pensando que esta podía ser la opción adecuada para una conexión cuya IP es dinámica, lo cual es mi caso. Es por esta misma razón que no elegí **Dirección IP estática**. Nuevamente, al aceptar todos estos cambios y clickear en el casillerito junto a Conexión Cableada, pareció que estuviera cargando las modificaciones que hice, y a continuación la nada absoluta.

  3)Por último, probé con lo conocido: me metí en el site de Arnet, busqué si había algún driver del modem Amigo CA85UR para Linux... y lo encontré! Sin embargo, como soy demasiado novato, no sé que hacer con ellos. No vale decirme "instalalo". Por supuesto que lo haría... si supiera como. =P

  Por favor, denme una mano con esto. Realmente tengo muchas ganas de empezar a usar Linux, y con esto de no poder acceder a Internet tengo las gambas cortadas. Ni siquiera puedo escuchar mis mp3 porque me dice que tienen que bajarse unos codecs adecuados para reproducir tal tipo de formato... Un bajón.

   Saludos.

PD: Ah! Olvidé decirles que llamé a Arnet pidiendo ayuda con la instalación de los drivers del modem para Linux. Me dijeron que debía consultar a un técnico particular. Les dije que si ellos ponían el driver en su página, sin importar para que SO era, entonces debían ocuparse de guiar en la instalación al usuario. Agregué *"¿Qué pasaría si en lugar de ser Linux, fuera un driver para Windows y la persona que llama tiene 70 años y no entiende nada de computadoras? Ustedes tendrían que brindarle soporte de todos modos. Esto es exactamente igual: si ustedes ponen un driver para un SO cualquiera, deben hacerse entonces cargo de guiar en la instalación de ese software en caso de que el usuario, por ignorancia, lo requiera. ¿Me explico?"* A lo que el empleado me respondió *"Señor, derivaremos el caso a una persona especializada en Linux para que lo llame entre mañana sábado y el domingo, y lo asesore en la instalación del driver"*. Lo malo de esta historia es el final: esta conversación telefónica tuvo lugar el viernes a la noche; estamos a martes a la noche y aún no recibí ninguna llamada de Arnet.

---

### Post by Hei Ku on 2009-04-22
Podes poner el link al driver en la pagina de Arnet? Al verlo, podemos darnos una idea de como instalarlo. Generalmente tienen un archivo README o INSTALL que dice que hay que hacer.

---

### Post by EcoMarcus on 2009-04-22
Gracias por responder a mi pedido de auxilio, Hei Ku.

No puedo postear el link porque para acceder a esa parte de la página de Arnet, me pide que ingrese mi usuario y mi contraseña, es decir, sí puedo postearlo pero de nada serviría. De todos modos, a continuación listo los archivos contenidos en el archivo .zip:

 cxacru.c
 Kbuild
 Kconfig
 usbatm.c
 usbatm.h

Acabo de bajarme de la misma página el manual del modem donde dice que *"Los sistemas operativos soportados son Windows 98, Windows 98se, Windows 2000, Windows ME y Windows XP, opcionalmente también son soportados los sistemas operativos MAC OS 9.X, MAC OS 10.X, Linux Redhat 7.1/7.2, Linux Mandrake."* ¿Debo entender por esto que no voy a poder usarlo en Ubuntu y, por ende, no podré conectarme a Internet mientras no cambie de modem/proveedor? No sé cual es el alcance de la compatibilidad, si es que existe, entre el software para Mandrake y Redhat, de aquel para Ubuntu.

Además, en el manual dice: *El dispositivo ADSL USB EndPoint Router se independiza del procesamiento disponible en las computadoras actuales, ejecutándose en el dispositivo ADSL USB EndPoint Router todas las tareas que consumen recursos de procesamiento en como ser las funciones de segmentación y reensamble del ATM (SAR)(...) Adicionalmente, incorpora las funcionalidades estándares de la industria como PPP sobre ATM (PPPoA) por la RFC 2364, PPP sobre Ethernet (PPPoE) por la RFC 2516, Routed Ethernet por la RFC 2684/1483, e IP Clásico sobre ATM por la RFC 2225/1577, ruteo estático y dinámico (RIPv2), NAT, NAPT, Dynamic NAPT, DNS Proxy, DHCP Server & Client y soporte de ALGs. (...) El concepto del CA-85UR ADSL USB EndPoint Router es combinar los beneficios del bajo costo de un dispositivo USB con la riqueza funcional e independencia de la PC del usuario de un dispositivo Ethernet. Esto es posible dado que el single-chip de Conexant contiene un poderoso procesador de red capaz de implementar las funciones y facilidades de un router ADSL Ethernet con funciones integrales. (...) Sin embargo, en lugar de hacer que sea la PC la que realice todo el trabajo de procesamiento de  celdas ATM, el firmware que corre en el CA-85UR tiene el stack completo de un router y, simplemente, transmite frames Ethernet a través de la interfaz USB. De esta manera, el CA-85UR funciona como un router completo y el único driver requerido en la PC es el que hace aparecer la interfaz USB como un puerto Ethernet.  La dependencia en la PC y el consumo del poder de procesamiento de la misma se minimiza mientras se mantienen todos los beneficios de un dispositivo USB.* Todo este "choclo" ¿significa que, si bien el modem se conecta a la PC por medio de un puerto USB, debido a su funcionamiento como router es como si fuera Ethernet?

Un detalle que supongo aporta es que al tirar un "ipconfig /all", la dirección IP es **igual** a la puerta de enlace predeterminada. Por lo que leí en un thread, esto significa que mi conexión es Ethernet, ¿no es cierto?

---

### Post by Hei Ku on 2009-04-22
No trae las instrucciones para instalarlo en Red Hat, a partir de eso se puede usar alien para convertirlo a Ubuntu.

---

### Post by EcoMarcus on 2009-04-22
No, no las trae; solo las instrucciones para instalarlo en Windows. No sé que es "alien", Hei Ku. Perdón.

Estuve probando con ```
 sudo pppoeconf
``` Encontró el dispositivo Ethernet llamado eth0. Cuando seleccioné "sí", al preguntarme el programa si estaban todas las interfaces, empezó a buscar un concentrador de acceso PPPoE en eth0. Al final, obtuve el sig. mensaje: *"No respondió el concentrador. Verifique los cables de red y del módem. Otra razón puede ser que se esté ejecutando otro proceso PPPoE y que éste esté controlando el módem."*

En un post previo, sugerí la posibilidad de que mi conexión fuera Ethernet a pesar de estar usando un puerto USB debido a la arquitectura del modem (ver #11). Mi IP cambia todos los días, es decir, es dinámica. ¿No supone una conexión Ethernet una IP fija?

---

### Post by faktorqm on 2009-04-24
Hola, tocaste demasiadas cosas. Borra las conexiones punto a punto que hiciste y todo, y la placa ethernet dejala en DHCP. (no se por que tocaste esto si el modem se conecta por usb...)

Yo creo que esto te va a ayudar, [http://www.ubudsl.com/es/inicio.php](http://www.ubudsl.com/es/inicio.php)

Si no te anda eso, postea. Yo habia generado un script igual que para el smart ax 810 uno para este tipo de modems, pero no lo encuentro. (tenia menos cosas que este que te pase).

Ojala el proximo post lo hagas de gnu/linux, salu2!

---

### Post by EcoMarcus on 2009-04-24
Yo ya dije que la tenés muy clara en cuanto a conexión a Internet se refiere, Faktor... :) 

¡Señoras y señores, les estoy escribiendo desde un sistema GNU/Linux, más precisamente desde mi Ubuntu personal! ;)

Hice exactamente lo que me dijiste: borré las conexiones 'punto a punto' que había hecho y dejé a la Ethernet en DHCP. Luego bajé (desde Windows) el UbuDSL y lo instalé. Tal como dice la página de este programita, es muy sencilla su configuración.

MUCHÍSIMAS GRACIAS, FAKTOR.
Te debo una.

---

