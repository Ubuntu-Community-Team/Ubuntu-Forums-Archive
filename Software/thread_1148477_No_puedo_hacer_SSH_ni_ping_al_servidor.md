---
title: "No puedo hacer SSH ni ping al servidor"
date: 2009-05-04
forum: Software
---

### Post by jacc90220 on 2009-05-04
Hola, soy nuevo en ubuntu.

Instale ubuntu server 8.1. El servicio de internet lo tengo con un modem adsl y mi ISP ya me dijo que todos los puertos estan abiertos. Tengo 5 IP públiccas para administrar.

Una la puse a este servidor. Levante apache, actualicé, etc.

Otra la puse en una red interna que se conecta mediante el Smoothwall 3.0.

Desde esa red pude conectrame con el putty, puedo ver la pagina que tengo en el servidor y demás.

Pero si me voy a micasa, la oficina de una migo, no puedo ni hacer ping (menos conectrame por SSH)... llame al ISP y el tampoco puede...

Quizas sea un firewall q me esta restringiendo al servidor, pero en la instalación no recuerdo haber habilitado ningino...

Si alguien me puede dar una mano. Gracias

---

### Post by guillermolisi on 2009-05-04
> **jacc90220 said:**
> Hola, soy nuevo en ubuntu.

Instale ubuntu server 8.1. El servicio de internet lo tengo con un modem adsl y mi ISP ya me dijo que todos los puertos estan abiertos. Tengo 5 IP públiccas para administrar.

Una la puse a este servidor. Levante apache, actualicé, etc.

Otra la puse en una red interna que se conecta mediante el Smoothwall 3.0.

Desde esa red pude conectrame con el putty, puedo ver la pagina que tengo en el servidor y demás.

Pero si me voy a micasa, la oficina de una migo, no puedo ni hacer ping (menos conectrame por SSH)... llame al ISP y el tampoco puede...

Quizas sea un firewall q me esta restringiendo al servidor, pero en la instalación no recuerdo haber habilitado ningino...

Si alguien me puede dar una mano. Gracias

Proba con un tracert: ```
sudo tracert <ip-publica_a_alcanzar>
```
La salida te va a decir cuantos saltos hay entree donde estas y la maquina a la cual queres llegar. Si no esta visible, en algun momento te dara asteriscos como salida sin darte la ultima linea con los datos del server de destino.

Si el modem esta como router y bloquea ping nunca vas a poder llegar con ese comando.

Por otra parte y tambien si el modem/router posee firewall activado, habilitale el port 22 para que deje entrar ssh. Una vez que lo hagas funcionar podes afinar la configuracion para darle un poco mas de seguridad.

---

### Post by Hei Ku on 2009-05-04
Probablemente tengas que hacer un port forwarding al servidor.

---

### Post by jacc90220 on 2009-05-04
Gracias por tu pronta respuesta,

tracert me aparece como un comando desconocido en ubuntu.

Pero hice la prueba desde windows y si me salen los asteriscos.

Pero como comenté mi ISP tampoco puede hacer ping y ya me confirmó q el modem q nos pusieron tiene todos los puertos abiertos.

Slds

---

### Post by Hei Ku on 2009-05-04
Le haces ping a la ip publica del servidor y aun asi no te responde?

Estas seguro que el modem esta en router? Tiene bien configuradas las tablas de ruteo?

---

### Post by jacc90220 on 2009-05-04
Gracias Hei Ku por tu respuesta.

Le hago ping y no me responde. Axcabo de consultar con el ISP nuevamente y me confirman que el modem está con los puertos abiertos.

Pero me observan que posiblemente sea el firewal u otro programa que me esté bloqueando.

Tiene el ubuntu server 8.1 algún firewall instalado y activado por defecto??

Gracias por su ayuda.
Slds

---

### Post by hictio on 2009-05-04
> 
Tiene el ubuntu server 8.1 algún firewall instalado y activado por defecto??


Hasta donde se, no, lo tiene deshabilitado por defecto, pero no perdés nada con probarlo.
Conectate o logeate al servidor, y tipeá:

```

sudo ufw status ENTER

```

---

### Post by sebastianabate on 2009-05-04
Ubuntu no instala ningún firewall si no lo especificás vos durante la instalación.
Igual tengo un par de dudas con respecto a la topología de tu instalación. Decís que administrás 5 IP's públicas y que te conectás por un modem/router que tiene todos los puertos abiertos. Ahora las preguntas son:
1) ¿cómo tenés distribuídas esas IP's públicas que te dieron? usá xxx para la parte común (tipo xxx.xxx.xxx.100) por seguridad
2) ¿el módem/router tiene una IP pública propia o te conectás con usuario y contraseña desde uno de tus equipos?
3) ¿cómo es la conexión física de todos los equipos? tratá de ser lo más exacto posible

---

### Post by hictio on 2009-05-04
> 
tracert me aparece como un comando desconocido en ubuntu.


Tenés que instalarlo, son unos 200 KB.

```

sudo aptitude install traceroute

```

> 
Ubuntu no instala ningún firewall si no lo especificás vos durante la instalación.


Si instala, no lo habilita, pero instala ufw, que es un wrapper para administrar iptables.

---

### Post by Hei Ku on 2009-05-04
Lo ultimo que te respondieron esta mal, salvo por la instalacion del traceroute. Por favor, no respondan si no saben.

Ubuntu trae un firewall, activado por defecto, con todos los puertos de entrada cerrados, salvo el ping. Si estuviera pasando el router, deberia responderte.

Cuando haces el trace desde afuera, en que punto muere? Llega hasta el modem o antes?

---

### Post by jacc90220 on 2009-05-04
Gracias a todos por responder.

Hictio instale el traceroute y me funciona full (por lo menos hasta lo q probé).

Verifique el status de ufw y me da: not loaded. Entonces interpreto que no está habilitado.

sebastianbate, tengo lo siguiente:


[LIST=1]
[*]Son 8 IP pùblicas:1 es el inicio de red, otra el broadcast y otra el gateway (q utiliza el modem). Me quedan 5 para hacer lo q quiera. Como les comente una la puse en el servidor y otra a otra red mediante el Smothwall 3.o (un firewal, proxy en Linux, no me acuerdo la distro, q me funciona sin novedad)
[*]El modem no lo puedo configurar porq el ISP no me da los privilegios (user/passw). Pero ya confirmé q no tiene ningún puerto cerrado.
[*]Fisicamente: nube, modem, switch. Del switch uno va al smooth (y de aqui en cascada con otros switch) y otro al servidor.
[/LIST]
Desde esa red (la que esta con el smooth) puedo hacer SSH con putty, winscp sin novedad. El problema es en forma remota desde casa, oficina, etc.

Slds

---

### Post by jacc90220 on 2009-05-04
Gracias hictio,

Estuve probando con tracert desde ubuntu (mediante vmware) y desde windows.

En el primero se me corta apenas sale de mi red (que es remota).

Desde windows sale hasta el modem pero ahi muere.

Volvere a molestar al ISP para que haga  las pruebas necesarias.

Slds

---

### Post by hictio on 2009-05-04
> **Hei Ku said:**
> 
Ubuntu trae un firewall, activado por defecto, con todos los puertos de entrada cerrados, salvo el ping. Si estuviera pasando el router, deberia responderte.


Estás seguro? Yo no lo vi habilitado por defecto nunca, es decir, el ufw; y las reglas de iptables permiten tráfico de todo en todas las direcciones, es decir, no tienen ninguna regla cargada.
El algo propio de la versión Server? No tengo a mano ninguno acá para verlo.

---

### Post by guillermolisi on 2009-05-04
> **Hei Ku said:**
> Lo ultimo que te respondieron esta mal, salvo por la instalacion del traceroute. Por favor, no respondan si no saben.

Ubuntu trae un firewall, activado por defecto, con todos los puertos de entrada cerrados, salvo el ping. Si estuviera pasando el router, deberia responderte.

Cuando haces el trace desde afuera, en que punto muere? Llega hasta el modem o antes?

Aclaro algo mas, UFW es una interface simple para generar las reglas de filtrado para el firewall de Linux (iptables).

Este activo UFW o no nada dice respecto del firewall en si.

Hay otros productos similares, mas elaborados o no, generalmente graficos, pero siguen siendo herramientas de configuracion para no tener que registrar las reglas usando las primitivas de iptables (en consola).

Ejemplos Firestarter, FirewallBuilder, etc.

---

### Post by hictio on 2009-05-04
> **guillermolisi said:**
> Aclaro algo mas, UFW es una interface simple para generar las reglas de filtrado para el firewall de Linux (iptables).

Este activo UFW o no nada dice respecto del firewall en si.

Hay otros productos similares, mas elaborados o no, generalmente graficos, pero siguen siendo herramientas de configuracion para no tener que registrar las reglas usando las primitivas de iptables (en consola).

Ejemplos Firestarter, FirewallBuilder, etc.

Entonces, podés revisar las reglas en los iptables así:

```

sudo /sbin/iptables -nvL | less ENTER

```

y salís de la pantalla de las reglas tipeando 'q'.

---

### Post by jacc90220 on 2009-05-04
Nuevamente gracias.

Hei Ku , estuve leyendo el tema del ping e indican q no utliza ningùn puerto, asì q nada tendrìa q ver si estan abiertos o no... pero que si se puede bloquear el q te hagan un ping.

hictio, probe la linea

sudo /sbin/iptables -nvL | less ENTER
y me mostro q si hay trafico  de output, forward e input.

Aún sigo sin poder conectarme en forma remota al servidor.

Slds

---

### Post by Hei Ku on 2009-05-04
El ping es trafico ICMP, no TCP o UDP, que son los que utilizan puertos. Y como decis, se puede bloquear igual que el resto. Pero si no llega un ping, menos vas a entrar con cualquier otro tipo de protocolo.

Podes postear la salida de hacer un trace desde una direccion externa al servidor?
Copia todo enterito acá.

---

### Post by jacc90220 on 2009-05-04
Ahi te pongo lo q saque desde windows,

Traza a xxx.xxx.xxx.155 sobre caminos de 30 saltos como m ximo.
  1    <1 ms    <1 ms    <1 ms  192.168.1.100 

  2     1 ms     1 ms     1 ms  xxx.xxx.xxx.201 

  3    13 ms    14 ms     9 ms  172.16.40.97 

  4    68 ms    69 ms    62 ms  172.16.27.234 

  5     *        *        *     Tiempo de espera agotado para esta solicitud.

  6     *        *        *     Tiempo de espera agotado para esta solicitud.

  7     *        *        *     Tiempo de espera agotado para esta solicitud.

  8     *        *        *     Tiempo de espera agotado para esta solicitud.

  9     *        *        *     Tiempo de espera agotado para esta solicitud.

 10     *        * 

Slds

---

### Post by Hei Ku on 2009-05-04
La ultima IP, 172.16.27.234, es la ip del router? Me parece que son muy pocos saltos, salvo que estes dentro del mismo ISP.

---

### Post by jacc90220 on 2009-05-04
Pues si tenemos el mismo ISP.

Ahora no encuentro a nadie en sus oficinas pero mañana te confirmo si es que el modem tiene algún problema.

Gracias nuevamente. Slds

---

### Post by Hei Ku on 2009-05-04
A que corresponde la IP 172.16.27.234? Esa es la IP del router o no?

---

### Post by guillermolisi on 2009-05-04
> **Hei Ku said:**
> A que corresponde la IP 172.16.27.234? Esa es la IP del router o no?
Ambas IPs en el bloque 172.16 son privadas con lo cual si o si tiene que haber algun firewall/proxy que pasar.

Me llama muchisimo la atencion el lag que se ve entre la primera IP y la segunda, ambas del bloque 172.16 pero en distintas subredes.

Esta claro que la 172.16.40.97 rutea a la que le sigue, asi que ahi hay un router (por hardware o por software, o sea que tambien podria ser una maquina).

Ademas es muy probable que exista NATting para que se vean todas esas maquinas con la misma IP publica.

Para mi se han olvidado de configurar algo en los equipos ... posiblemente hayan configurado en un sentido y se olvidaron o lo hicieron mal en el contrario.
Si nunca llega o nunca se recibe confirmacion produce el mismo efecto.

---

### Post by jacc90220 on 2009-05-05
Muchas gracias a otdos por sus aportes.

Hoy me encontre con un amigo que trabaja en el ISP y me confirmo que las 172.16 son dos redes internas q manejan ellos y me hizo check del modem y todo estaba normal.

Hice el ping y tracert y ahora si llego haste el servidor...sinceramente hasta ayer en la noche no se podía pero ahora si... asunto resuelto (eso espero)

Nuevamente gracias por su tiempo y seguramente los estaré molestando nuevamente para aprender un poco más...

Slds

---

