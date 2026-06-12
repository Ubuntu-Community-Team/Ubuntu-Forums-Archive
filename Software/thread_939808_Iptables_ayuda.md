---
title: "Iptables ayuda"
date: 2008-10-06
forum: Software
---

### Post by ramiro_md on 2008-10-06
Bueno gente, hoy me dieron ganas de desarrollar un script para el firewall.
Anduve leyendo un pocquitín sobre el tema, y tengo entendido que hay dos maneras de programar el script:
1)Bloquear todas las conexiones como política principal. Y luego ir creando excepciones.
2)Aceptar todas las conexiones como política principal y luego ir creando excepciones.
Yo opté por la opción 1, basandome en que cuanto menos puertos abiertos haya mejor :). Entonces cerré todos los puertos:

iptables -A INPUT -p TCP -j DROP

Bien, luego comencé a crear excepciones quedandome algo así:

iptables -A INPUT -p TCP -j DROP
iptables -A INPUT -s xx.xxx.xxx.xxx -p TCP --dport xxx -j ACCEPT 
[...]

Lo que hice en esa útlima línea, creo que algunos ya se habrán dado cuenta igual, es aceptar toda conexión entrante  del source xxx.xxx.xxx.xxx al puerto xxx.

Mis dudas son las siguientes, si eso que propongo en ese script es correcto. O hay alguna falla. Porque lo noto algo contradictorio xD.
Y por otro lado, para permitir navegar por internet sería OUTPUT?.
Bueno espero que me den una mano y me orienten un poco más con respecto a esto. Un saludo.

---

