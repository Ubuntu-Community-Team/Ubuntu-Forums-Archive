---
title: "comando whois!"
date: 2008-07-16
forum: Software
---

### Post by excaliburs on 2008-07-16
que tal gente? usando el comando de consola "whois" me da este resultado para algunas búsquedas
No se conoce ningún servidor whois para esa clase de objeto.
alguien me podría decir si es que tengo que configurar una lista de servidores para tales búsquedas? 
por ejemplo: instale el xwhois para ver otra alternativa al comando y veo que tiene una lista de servidores de búsqueda de dominio a la derecha de la pantalla....alguien me confirma esto?

gracias!

---

### Post by sergiom99 on 2008-07-17
proba con el dig

```
sergio@kubuntu:~$ dig google.com 
```

el nslookup esta obsoleto, pero en algunas distros aun funciona:
(en ubuntu sí, en CentOs te avisa)
> $ nslookup google.com
Note:  nslookup is deprecated and may be removed from future releases.
Consider using the `dig' or `host' programs instead.  Run nslookup with
the `-sil[ent]' option to prevent this message from appearing.
Server:         200.49.130.25
Address:        200.49.130.25#53

Non-authoritative answer:
Name:   google.com
Address: 64.233.187.99
Name:   google.com
Address: 64.233.167.99
Name:   google.com
Address: 72.14.207.99


sino postea como pones el comando a ver si te falta algo.

---

### Post by excaliburs on 2008-07-18
perdon sergio! tenes razon, faltaron datos en el post.
te pongo este ejemplo.
# whois "telefonica"@arin.net
No se conoce ningún servidor whois para esa clase de objeto.

tengo entendido que para usar el comando no solo hay que poner la url tal cual es sino que se pueden hacer busquedas mas genericas como esa.....corregime por favor si estoy cometiendo un error.

gracias!

---

### Post by sergiom99 on 2008-07-19
instale el whois para probarlo:
vos queres preguntarle al "arin.net" por el usuario "telefonica"?


```
sergio@kubuntu:~$ whois telefonica -h arin.net
connect: Conexión rechazada

```

---

### Post by excaliburs on 2008-07-19
gracias por responder sergio....
en realidad yo quiero preguntar por dominios, pero en general....
o sea, hacer una consulta de este tipo:

# whois "telefonica"

y obtener un resultado como este:

TELEFONICA.ORG
TELEFONICA.NET
TELEFONICA.COM

o hacer una consulta de este tipo:

# whois "Ciudad"@arin.net

y obtener algun resultado, por ejemplo:

Ciudad Internet Node (25 de Mayo City) (NETBLK-PRIMA-BLK-184) PRIMA-BLK-184
                                                 200.42.12.208 - 200.42.12.223
Ciudad Internet Node (25 de Mayo City) (NETBLK-PRIMA-BLK-172) PRIMA-BLK-172
                                                    200.42.11.8 - 200.42.11.15
Ciudad Internet Node (Concepcion del Uruguay City) (NETBLK-PRIMA-BLK-244) PRIMA-
BLK-244
                                                 200.42.31.192 - 200.42.31.223
Ciudad Internet Node (Cordoba City) (NETBLK-PRIMA-BLK-146) PRIMA-BLK-146
                                                      200.42.9.0 - 200.42.9.31
Ciudad Internet Node (Corrientes City) (NETBLK-PRIMA-BLK-147) PRIMA-BLK-147
                                                     200.42.9.32 - 200.42.9.63
Ciudad Internet Node (La Plata City) (NETBLK-PRIMA-BLK-150) PRIMA-BLK-150
                                                   200.42.9.128 - 200.42.9.159
Ciudad Internet Node (Mendoza City) (NETBLK-PRIMA-BLK-144) PRIMA-BLK-144
                                                   200.42.8.128 - 200.42.8.143

en fin, quiero hacer consultas como en los ejemplos y ver algun resultado mas alla del:
No se conoce ningún servidor whois para esa clase de objeto.

gracias!!!
y perdon por andar jodiendo con estas cosas....por ahi es una pabada....pero no encuentro nada por la red que me saque de la duda...

---

### Post by excaliburs on 2008-07-19
acabo de hacer otra prueba....aca te pongo lo que me tiro.

# whois ciudad -h whois.arin.net
Ciudad CIUDAD (NET-64-60-69-192-1) 64.60.69.192 - 64.60.69.199
Ciudad CIUDAD (NET-64-60-69-192-1) 64.60.69.192 - 64.60.69.199
Ciudad Tecnopolis RSPC-1210868767625211 (NET-67-192-157-120-1) 67.192.157.120 - 67.192.157.127

toy contento....logre algun resultado
fijate donde dice: 
# whois ciudad -h **whois**.arin.net

---

### Post by sergiom99 on 2008-07-19
mira estos links:
[http://www.arin.net/whois/](http://www.arin.net/whois/)

[http://en.wikipedia.org/wiki/Whois](http://en.wikipedia.org/wiki/Whois)

con esto va a andar bien.

(que estas tratando de hacer? curiosidad nomas)

---

### Post by excaliburs on 2008-07-19
como va Sergio!!...solo quiero saber lo que pocos saben...prometo que solo voy a preguntar lo justo y necesario y cosas muy especificas....
pasa que para aprender ciertas cosas no queda otra mas que la practica...solo asi se aprende...es uno de los motivos por los que me divorcie de M$....uno usa el S.O. que mejor se adapta a sus espectativas..
si solo se usa la máquina para el msn, emule y juegos; con win basta y sobra.....para los que aspiramos a mas (cualidad que a mi entender se repite en la inmensa mayoría de los usuarios de GNU/Linux), se necesita otra herramienta...o mejor dicho, una herramienta!

saludos Sergio!
y muchas gracias por tu atención!

---

### Post by excaliburs on 2008-07-19
PD: cualquier descubrimiento que haga, voy a compartirlo aca.

---

