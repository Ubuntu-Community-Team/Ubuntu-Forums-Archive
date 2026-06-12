---
title: "Consulta sobre iptables"
date: 2010-09-17
forum: Software
---

### Post by asterix77 on 2010-09-17
Al realizar lo siguiente vía consola, me aparece el siguiente resultado

$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination     


Esto me indica si no me equivoco, que todo es aceptado.
Ahora si yo escribo una orden por consola para iptables como por ejemplo:

iptables -A INPUT -s 195.65.34.234 -j ACCEPT

me imagino que se debe almacenar en algún fichero ¿pero cual es ese fichero?¿existe ese fichero de configuración "original"?
En internet se dan ejemplos de uso de iptables, en la cual se debe crear un script, darle permiso de ejecución, y ejecutarlo al inicio, pero si ya viene en el kernel, significa que ya viene preconfigurado por defecto.

Mi idea es aprender sobre el uso de iptables por consola, y no depender de programas gráficos como por ejemplo firestarter, pero tengo esa duda.

Saludos

---

### Post by miguelwill on 2010-09-17
cuando se aplican las reglas al filtro de red (iptables), estas quedan almacenadas en memoria (puede que algun archivo dentro de /proc/sys ), por lo que si creas alguna regla y la cargas, esta queda funcionando solo hasta que reinicias el sistema, por lo que deben ser cargadas en cada arranque (para eso estan los script que cargan tus reglas en cada arranque)

una ves cargadas, pueden ser eliminadas o le puedes agregar mas reglas, y si no las agregas al script que carga tus reglas, solo cargara las que ya tenia :D

saludos

---

### Post by asterix77 on 2010-09-17
Ok.

Gracias por la aclaración.

Saludos

---

