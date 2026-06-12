---
title: "AMULE  3 preguntas"
date: 2008-09-23
forum: Software
---

### Post by katon on 2008-09-23
queria saber si a todos les pasa que el AMULE resulta "pesado": 

consume muchos recursos cuantos mas archivos se esten bajando y subiendo? 
Alguien de ustedes usa AMULE con alguna maquina potente (Dual core - quad core) como resulta ?

por otro lado como hacer para mantener los creditos ( no los archivos a medio bajar )  de mi usuario que tenia en una maquina con EMULE (windows) y pasarlos ahora a AMULE en Ubuntu?

gracias desde ya

---

### Post by sartrejp on 2008-09-23
Yo uso el amule y no resulta pesado, para nada. tengo una amd athlon 64 con 2 gb de ram.
Para mantener los créditos deberías copiarte los archivos, aunque no se cuales sirven.
Yo tengo instalado windows en una partición, Ubuntu en otra y una más para guardar archivos, y el directorio de descargas y el de temporales son los mismos para el emule y el amule, entonces si pongo a bajar un archivo en linux, y mi novia va a usar la computadora en windows, la reinicia, y sigue descargando el archivo desde donde iba.
No contesta tu pregunta, pero por ahi te sirve.
Suerte

---

### Post by faktorqm on 2008-09-23
yo tengo un athlon xp 2600 con 512mb de ram y va re bien amule, ni un drama, he dejado mas de 20 archivos bajando y no paso nada. Salu2!

---

### Post by User21 on 2008-09-23
Por el titulo del hilo, pensé que Amule habia sacado una version llamada "Amule 3" :P

---

### Post by katon on 2008-09-23
> **faktorqm said:**
> yo tengo un athlon xp 2600 con 512mb de ram y va re bien amule, ni un drama, he dejado mas de 20 archivos bajando y no paso nada. Salu2!

gracias, entiendo que es la maquina que usas aparte del AMULE ? osea no es dedicada para bajadas.

---

### Post by katon on 2008-09-23
> **User21 said:**
> Por el titulo del hilo, pensé que Amule habia sacado una version llamada "Amule 3" :P


si, ahora que lo pienso parece algo asi :)

---

### Post by faktorqm on 2008-09-24
si si es la pc que uso todos los dias... para todas las cosas, lo que pasa es que a veces me satura la conexion, tonces le tengo ke poner pausa, pero sino necesito internet amule rulea :P

---

### Post by ramiro_md on 2008-09-25
CHe, ahora que pude sacar andando el amule, tengo una duda, en las  flechas que tiene el mundito (que deberían estár verdes para un óptimo funcionamiento), tengo una verde y otra amarilla y me marca "kad(firewalled)". Es algo referido al firewall no ?...disculpen si es algo obvia la preg., pero como lo soluciono ?. Un saludo.

---

### Post by WanderingKnight on 2008-09-25
Tenés que habilitar el puerto que estás usando para TCP y UDP con iptables.

```
sudo iptables -A INPUT -p tcp --dport <puerto> -j ACCEPT
sudo iptables -A INPUT -p udp --dport <puerto> -j ACCEPT
```

Fijate que vas a tener que agregarlo al script default de iptables para que te lo agarre cada vez que arranca (/etc/iptables). También podés agregar un script a /etc/init.d con esas líneas (agregando #!/bin/bash como primera línea y haciéndolo ejecutable con chmod +x nombre_del_script) y correr:

```
sudo update-rc.d nombre_del_script defaults
```

para agregarlo a los runlevels por defecto (3 y 5 creo).

---

### Post by ramiro_md on 2008-09-25
Bien, cree mi propio "script" ¿sería?...agregue estas líneas:

[COLOR="Red"]iptables -A INPUT -p tcp --dport 4662 -j ACCEPT
iptables -A INPUT -p udp --dport 4672 -j ACCEPT[/COLOR]

Le dí permisos al script y ejecuté:

[COLOR="Red"]sudo cp firewall.sh /etc/init.d/
sudo update-rc.d firewall.sh defaults
[/COLOR]
Pero sigue la flecha amarilla y el "kad:firewalled".:confused:

Nota: la salida de "iptables -L" me está diciendo que los puertos están abiertos o estoy equivocadisimo ?

[COLOR="Red"]Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:4662 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:4672 

[/COLOR]
PD: me base en esta guía [http://www.guia-ubuntu.org/index.php?title=Cortafuegos](http://www.guia-ubuntu.org/index.php?title=Cortafuegos)

---

### Post by faktorqm on 2008-09-26
Es un bug del amule eso. Yo tengo los puertos bien y a veces me tira los dos verdes, y a veces me tira verde y amarillo. Apreta conectar desde clientes conocidos (o algo asi) en Kad y vas a ver que "renicias" la conexion solo con Kad, tonces capaz te pasa a verde solo. Digo capaz por que tambien me pasa que conecta en amarillo el kad, y cuando me levanto al otro dia esta en verde.... y asi. Salu2!!

---

### Post by ramiro_md on 2008-09-26
Bueno, okey, igualmente me anda óptimo amule, pero tenía incorporado que las dos flechas tenían que estar en verde jejeje.
Otra cosa, desde que configuré el script del firewall para que cargue desde el inicio del sistema, Gnom,e tarda más en iniciar (es decir en cargar el escritorio) y me inicia con un cartelaso de error diciendo algo de que no se pueden cargar ciertas preferencias :confused:.
Un saluudo.


PD: Cómo hacen cuando postean comandos les apaarezca en un "recuadro" y la palabra "code" ?? :)

---

### Post by katon on 2008-09-27
perdon pero nunca entendi lo del KAD , es otro protocolo ? yo siempre use AMULE pero KAD no me conecte nunca, se supone que ayuda a tener mas fuentes para bajar o algo asi??  (que ignorancia la mio!)

---

### Post by sartrejp on 2008-09-27
Ed2k se conecta a un servidor, donde tu conexión va al servidor, de ahí a otro usuario, vuelve al servidor y te la devuelven a vos.
En la red kademlia (KAD) la conexión es de nodo a nodo, de persona a persona, te conectas directamente a las otras personas eliminando los servidores que actúan como intermediarios.
A grandes rasgos y en forma vulgar, esa es la diferencia.

---

### Post by katon on 2008-09-27
gracielaaa

---

### Post by WanderingKnight on 2008-09-27
> 
Bueno, okey, igualmente me anda óptimo amule, pero tenía incorporado que las dos flechas tenían que estar en verde jejeje.

Fijate que tengas forwardeados los puertos que usás si tenés un router, y también de usar puertos que estén por arriba del 10000... muchas veces los ISPs bloquean los defaults (no sé cuales son en aMule, pero en Bittorrent son 6881-6889 y generalmente están bloqueados).

> 
PD: Cómo hacen cuando postean comandos les apaarezca en un "recuadro" y la palabra "code" ?? 

[code]código[/code*] sin el * (vBulletin tags que le dicen).

---

