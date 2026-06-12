---
title: "CUPS via internet"
date: 2009-12-23
forum: Software
---

### Post by z37a on 2009-12-23
Gente, una pequeña consulta, se que se puede y de echo lo probe y funciona, utilizar cups via internet, ahora viene el tema de seguridad. Intente de varias maneras permitirle solo acceso a determinadas ips de internet mediante dyndns y no logre que funcione, es posible permitirle acceso a un nombre de un ddns en vez de a una ip? Otra cosa que queria consultarles es si hay alguna forma para que al imprimir mediante internet(si se puede, si no en forma normal) solicite usuario y password?

PD: Yo siempre con mis preguntas alocadas.....

---

### Post by juancarlospaco on 2009-12-23
En la web del CUPS hay una opcion que dice:

(*)Permitir imprimir a todos los usuarios excepto:
( )Denegar imprimir a todos los usuarios excepto:
-
-

tendrias que ponerlo asi:

( )Permitir imprimir a todos los usuarios excepto:
(*)Denegar imprimir a todos los usuarios excepto:

-usuarioqueimprimedesdeinternet
-ChuckNorris

y con eso los usuarios autenticados de la lista podrian imprimir.

---

### Post by z37a on 2009-12-24
> **juancarlospaco said:**
> En la web del CUPS hay una opcion que dice:

(*)Permitir imprimir a todos los usuarios excepto:
( )Denegar imprimir a todos los usuarios excepto:
-
-

tendrias que ponerlo asi:

( )Permitir imprimir a todos los usuarios excepto:
(*)Denegar imprimir a todos los usuarios excepto:

-usuarioqueimprimedesdeinternet
-ChuckNorris

y con eso los usuarios autenticados de la lista podrian imprimir.

Habilite esa opcion pero le dio permiso a TODOS, asi que cualquiera podia, mi idea es que solo la ip del dom inio "x.x.net" pueda imprimir.

---

### Post by juancarlospaco on 2009-12-24
nonononono, la opcion DENEGAR a todos excepto...
:)

---

### Post by faktorqm on 2009-12-24
y si pones una regla de iptables para el puerto 631?

deberia ser algo asi (te tiro un cable, no se si funciona este comando)

```
iptables -A INPUT -s NOMBRE_PC_Q_IMPRIME -p tcp -dport 631 -j ACCEPT
```


Lo del user y pass no me acuerdo como era, pero es re contra molesto por que cada X tiempo te pide la contraseña. Decime a ver como avanzaste. Saludos.

---

### Post by z37a on 2009-12-25
> **faktorqm said:**
> y si pones una regla de iptables para el puerto 631?

deberia ser algo asi (te tiro un cable, no se si funciona este comando)

```
iptables -A INPUT -s NOMBRE_PC_Q_IMPRIME -p tcp -dport 631 -j ACCEPT
```


Lo del user y pass no me acuerdo como era, pero es re contra molesto por que cada X tiempo te pide la contraseña. Decime a ver como avanzaste. Saludos.

Es que llegar lego justo el print server tiene ip publica(es un router Linux), pero me da el 404, a menos que active el imprimir desde internet, pero en ese caso si bien puedo imprimir bien, le dejo imprimir a TODOS!!! y solo quiero que puedan ciertos dominios dinámicos.

---

### Post by gmunioz on 2009-12-25
Hola z37....:

Prueba en cups.conf, dejar las autorizaciones
denegadas por defecto y habilitadas una a una:

```
<Location />
    AuthType None
    Order Deny,Allow
    Deny From All
    Allow From @LOCAL
    Allow From 10.0.1.0/8
    Allow From 172.19.0.0/12
    Allow From 192.168.1.0/16
    </Location>
    
    <Location /jobs>
    AuthType None
    Order Deny,Allow
    Deny From All
    Allow From @LOCAL
    Allow From 10.0.1.0/8
    Allow From 172.19.0.0/12
    Allow From 192.168.1.0/16
    </Location>

```

---

### Post by z37a on 2009-12-25
> **gmunioz said:**
> Hola z37....:

Prueba en cups.conf, dejar las autorizaciones
denegadas por defecto y habilitadas una a una:

```
<Location />
    AuthType None
    Order Deny,Allow
    Deny From All
    Allow From @LOCAL
    Allow From 10.0.1.0/8
    Allow From 172.19.0.0/12
    Allow From 192.168.1.0/16
    </Location>
    
    <Location /jobs>
    AuthType None
    Order Deny,Allow
    Deny From All
    Allow From @LOCAL
    Allow From 10.0.1.0/8
    Allow From 172.19.0.0/12
    Allow From 192.168.1.0/16
    </Location>

```

Es esactamente lo que estoy intentando hacer, pero justamente si yo en vez de ip coloco un dominio esto no funciona, pero al probar el dominio con un simple ping el dns resuelve correctamente el nombre.

---

### Post by Mauro22 on 2009-12-25
Aca [0] lo escribe (si no me equivoco, como pensas vos)

<Location />                   # this location is the main screen
Order Deny, Allow
Deny From All
Allow From 127.0.0.1           # allow configuration from local host
Allow From 192.168.1.*         # allow configuration from any machine
                               # on the 192.168.1.0/24 subnet
Allow From mybox.mydomain      # this is my desktop on another segment
</Location>

[0] [http://www.linuxjournal.com/article/8618](http://www.linuxjournal.com/article/8618)


Hay algo interesante de Listen tambien.

---

### Post by z37a on 2009-12-26
Lo que yo hize es lo siguiente:

```
<Location />
  Allow 192.168.1.0/255.255.255.0
  Allow from 192.168.1.0/255.255.255.0
  Allow XXXXXXXX.dynalias.net
  Order allow,deny
  Allow @LOCAL
</Location>

```

Pero con eso al entrar desde XXXXXXX.dynalias.net me da 404, si le pongo Allow from all me anda de 10, pero entra cualquiera.

No entiendo bien si el Allow @LOCAL tendra algo que ver!!!

Gente les agrego, probe de modificar tal cual [http://www.linuxjournal.com/article/8618](http://www.linuxjournal.com/article/8618) pero me dio un error 403 al ingresar desde afuera, les paso el conf como me quedo, lo unico tapando la info de los dominios(Pa evitar problemas vio)!!

```
<Location />
  # Allow shared printing and remote administration...
  Order Deny, Allow
  Deny From All
  Allow From 127.0.0.1
  Allow From 192.168.1.*
  Allow From XXXXX.xxxxx.com
  Allow From xxxxx.dynalias.net
</Location>

```

Desde mi LAN entro bien, pero desde afuera no logro entrar, ahora si agrego el Allow From All como linea desde afuera entro de 10!!!!

---

### Post by guillermolisi on 2009-12-26
> **z37a said:**
> ```
<Location />
  # Allow shared printing and remote administration...
  Order Deny, Allow
  Deny From All
  Allow From 127.0.0.1
  Allow From 192.168.1.*
  Allow From XXXXX.xxxxx.com
  Allow From xxxxx.dynalias.net
</Location>

```Desde mi LAN entro bien, pero desde afuera no logro entrar, ahora si agrego el Allow From All como linea desde afuera entro de 10!!!!
La linea que menciona Deny From All no deberia ser la ultima, luego del bloque de Allow ?
De esa forma le doy permiso a las redes que me interesan, locales o no, y al final cierro para todo el resto (el mismo criterio de aplicacion para un Firewall).

---

### Post by z37a on 2009-12-26
> **guillermolisi said:**
> La linea que menciona Deny From All no deberia ser la ultima, luego del bloque de Allow ?
De esa forma le doy permiso a las redes que me interesan, locales o no, y al final cierro para todo el resto (el mismo criterio de aplicacion para un Firewall).


No creo, por que localmente ingreso perfecto, y si te fijas el Deny esta antes que el local, igualmente probé de cambiar el orden pero nada sigue dando el mismo problema da un 403 en el lado remoto y en el local ingresa perfecto.

---

