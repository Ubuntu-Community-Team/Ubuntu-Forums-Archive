---
title: "Como subo mi pagina web a Ubuntu??"
date: 2010-01-13
forum: Software
---

### Post by Arian_Tux on 2010-01-13
Tengo una pagina web y me gustaria saber si puedo hacer mi pc que aloje la pagina para hosting o algo asi xD

Tendria que conseguir el dominio algo asi [www.midominio.ar](www.midominio.ar) luego guardar mi pagina en mi pc y que los demas puedan leer mi pagina.

Como hago eso en Ubuntu????
 

Muchas gracias.

---

### Post by FB91 on 2010-01-13
ya estarías hablando (si no me equivoco) de Ubuntu 9.10 Server Edition

---

### Post by guillermolisi on 2010-01-14
> **Arian_Tux said:**
> Tengo una pagina web y me gustaria saber si puedo hacer mi pc que aloje la pagina para hosting o algo asi xD

Tendria que conseguir el dominio algo asi [www.midominio.ar]("http://www.midominio.ar") luego guardar mi pagina en mi pc y que los demas puedan leer mi pagina.

Como hago eso en Ubuntu????
 

Muchas gracias.
Tendrias que usar algun servicio de DNS publico para que tu dominio web sea conocido y alcanzable por los demas. Para ello uso ZoneEdit, por ejemplo.

Si tu conexion a Internet es con IP publica dinamica tendrias que utilizar algun servicio que mantenga actualizada la relacion IP-PC, tal como DynDNS o equivalentes, cada vez que tu ISP cambia la IP que te asigna.

Luego, instalar y configurar Apache para poner en marcha el servidor web en tu maquina. Prestar especial atencion a las mejores practicas sobre seguridad cuando lo configuras.

Si tu conexion no es simetrica (igual ancho de banda para upload que para download) la navegacion del sitio alojado en la PC sera modesta, funcionara pero no esperes accesos instantaneos como puede percibirse con sitios que usan IP estatica.

---

### Post by z37a on 2010-01-14
> **guillermolisi said:**
> Si tu conexion no es simetrica (igual ancho de banda para upload que para download) la navegacion del sitio alojado en la PC sera modesta, funcionara pero no esperes accesos instantaneos como puede percibirse con sitios que usan IP estatica.

Justo estaba a punto de comentar esto. Suelo armar webs para aprender un poco de programación PHP, HTML, etc... y uso un servidor casero, pero también llegue en ciertas épocas a tener un hosting para esas pruebas. Aca en Argentina, a menos que cuentes con iPlan(o un enlace dedicado de Clarin, por Fibertel y demas empresas lo digo), todas las conexión son asimétricas con un máximo de 512Kbps, las que superan esta subida salen fortuna!!! Por lo cual tu web andaría extremadamente lenta dependiendo de la cantidad de visitas, pero por ejemplo transferir un vídeo, solo 1 a la vez podría verlo y tiene que ser de baja calidad. Un hosting te puede ofrecer 100Mbps de upstream, por lo cual andaría muchísimo mas rápido, y hay alguno baratos(tenes desde 4$ por mes).

Mi consejo, si solo vos usas el sitio alojalo en tu maquina, si lo usan varios alojarlo en un hosting y deja una copia en tu maquina alojada para testeos.

---

### Post by juancarlospaco on 2010-01-14
**sudo apt-get update ; sudo apt-get install ddclient ; sudo tasksel ; sudo apt-get autoclean ; xdg-open [http://www.dyndns.com/](http://www.dyndns.com/)**

:)
Necesitas cuenta en DynDNS para el ddclient, en el TaskSel elegir LAMP, todo es gratis

---

### Post by Arian_Tux on 2010-01-14
Muchas gracias por los consejos. Pues la pagina sera visitada creo que por 10 o 20 personas al dia del exterior. 

La conexion de internet que poseo es de 512 Kbps por lo que me quitaria ancho de banda si lo visitan mas de 10 personas al dia si me equivoco???

Pues claro que tambien tendria que contratar un dominio un suponer como [www.miwebenubuntu.ar](www.miwebenubuntu.ar) o com la que me salga mas barata ;) o los dominios edu.ar o asi xD

Pues ya tengo la pagina web lista y solo se que va en el directorio /var/www/ xD

Mucgas gracias y sigan comentando.

---

### Post by guillermolisi on 2010-01-14
> **Arian_Tux said:**
> Muchas gracias por los consejos. Pues la pagina sera visitada creo que por 10 o 20 personas al dia del exterior. 

La conexion de internet que poseo es de 512 Kbps por lo que me quitaria ancho de banda si lo visitan mas de 10 personas al dia si me equivoco???

Pues claro que tambien tendria que contratar un dominio un suponer como [www.miwebenubuntu.ar]("http://www.miwebenubuntu.ar") o com la que me salga mas barata ;) o los dominios edu.ar o asi xD

Pues ya tengo la pagina web lista y solo se que va en el directorio /var/www/ xD

Mucgas gracias y sigan comentando.
512Kbps simetricos ? De upload ? De download ?
A priori no me parece un ancho de banda razonable para dar servicio web.

Mi blog, que no tiene muchas visitas, esta montado sobre un enlace asimetrico de 2Mb y como es un blog personal no importa pero para algo mas serio ni siquiera me animaria a montarlo sobre lo que tengo como enlace.

Como saber de antemano que la cantidad de visitas sera esa ? Que pasara cuando comience a estar indexada por Google y comiencen a entrar personas que no sabian que el site existia ? Que pasara con las referencias de otros sitios (que llevaran mas interesados) ?

Los dominios edu.ar solo se pueden gestionar si acreditas ser una institucion de enseñanza debidamente inscripta (en la juridisccion que corresponda segun el nivel y zona de influencia).

Por un dominio .com.ar no hace falta pagar un solo peso, ni para registrarlo ni para operarlo ya que servicios como los que brinda ZoneEdit son gratuitos. Solo tenes que gestionarlo en NIC.ar y luego delegarlo.

Tambien podes pagar absolutamente todo y cada parte de lo que queres hacer.

---

### Post by Arian_Tux on 2010-01-14
Muchas gracias por la ayuda el upload de la pagina es como de 128 a 384 xD y el download es de 484 Kbps segun un test abeltronica. 

Pero ya me habia informado sobre el ancho de banda. Lo mejor sera pagar hosting ya que creo que no deben ser muy caros segun se manejo todo hoy xD.

Pero hacer el intento no me costaria nada xD o mejor se los dejo a los expertos???? :popcorn:

---

### Post by Arian_Tux on 2010-01-18
Alguien me puede ayudar???? :D

---

### Post by z37a on 2010-01-19
> **Arian_Tux said:**
> Alguien me puede ayudar???? :D

Estas usando Ubuntu Server o Desktop?

---

### Post by NickCis on 2010-01-21
Mmm,,, yo lo unico qe tengo experiencia es usando servers gratuitos, ([www.000webhost.com](www.000webhost.com)), con dominio propio ( .com.ar), y depaso lo manege con zone edit, para usar el mail qe te proporciona google para el dominio propio (para hacer todo eso del manejo de los servers de correo, no me acuerdo bien como se llamaba).

Zone Edit ([http://www.zoneedit.com/](http://www.zoneedit.com/)), te proporciona el manejo de 5 dominios de manera gratuita.
Para tener dominio propio .com.ar, son gratuitos, entras a [http://www.nic.ar/](http://www.nic.ar/) , (tenes qe ser ciudadano argentino). Seguis las instrucciones de la pagina, y listo, no es nada dificil.
Y si no tenes ip fija, me imagino que vas a poder usar el servicio de no-ip ( [http://www.no-ip.com/](http://www.no-ip.com/) ), para tener una "ip fija" (lo que hace es darte un dominio que se relaciona con tu ip). Me parece que habia una forma de que el servidor actualice tu ip de manera automatica usando un programa, bien no me acuerdo =P...

Saludos.

---

### Post by mama21mama on 2010-01-21
Asi monte mi [lamp con ubuntu ]("http://mamalibre.eshost.com.ar/?q=content/lamp-linux-apache-mysql-php-y-drupal").
De maravilla anduvo.

Si luego te viene mucho gasto de electricidad puedes optar por un [hosting gratuito]("http://www.taringa.net/posts/info/2534005/Hosting-Gratuito-ublicidad.htm") como este que uso yo.

Para usar [tudominio.com.ar ]("http://foro.eshost.com.ar/index.php/topic,255.0.html")

Saludos

---

