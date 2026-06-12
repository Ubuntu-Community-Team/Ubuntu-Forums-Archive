---
title: "Quien la tiene clara con SSH?"
date: 2009-02-23
forum: Software
---

### Post by Mauro22 on 2009-02-23
Hola!!


La consulta es rapida pero es problema es grande.


Como tengo el dia libre, me puse a investigar esto del ssh y la administracion remota.


Hecho. Consegui Putty y Xming, los puse en el win XP. Instale ssh en ubuntu y me conecte de 10, modo consola, modo grafico :D.


Ahora, esto es en intranet y no tiene sentido (para mi) que sea asi nomas. Necesito que pueda entrar por la ip publica.


+ Hice una cuenta en No-ip. Estoy medio perdido aca. Nunca me pidio que puertos ni nada de eso.

+ Cambie el puerto standar del ssh de 22 a 1988.



Si en Putty pongo mi ip publica no conecta.

+ El modem: Es un zyxel 600, abri todos los puertos y los dirigi al router.
+ El router: Dlink dir300. Sigo haciendo forward de los puertos 22 hasta el 2000 hacia mi ip de intranet (192.168.0.100) y nada




Alguna idea salvadora?




Gracias!!

---

### Post by fmsismo on 2009-02-23
1ro, la información que tiene el host tuyo en no-ip, onda misuperservidor.no-ip.com (o como sea el dominio) es coincidente con la ip que te asigno tu isp?

Para esto tenes que ejecutar 
              nsloolup misuperservidor.no-ip.com
Y desde la máquina de tu casa entrar a 
              [http://www.ip-adress.com/](http://www.ip-adress.com/) 
y verificar que los resultados sean coincidentes.

Si no son coincidentes tenes que poner un script o algo que te refresque la información de tu ip externa.

Saludos

---

### Post by euzkoarima on 2009-02-23
> **Mauro22 said:**
> 
+ Hice una cuenta en No-ip. Estoy medio perdido aca. Nunca me pidio que puertos ni nada de eso.
Gracias!!

Esta bien, los servicios tipo no-ip solo sirven para que puedas poner algo.no-ip y te lo manden al ip que tu pc tenga en ese momento, después con el router tenes que ocuparte de los puertos.

Todo lo que contás a mi parece bien, repasaría lo siguiente por las dudas:

1. que el no-ip este apuntando bien a tu ip pública
2. creo que con redireccionar los tcp alcanza, pero proba con los udp también
3. Pregunta: estás probando de entrar desde afuera de tu intranet o desde adentro ??.
La pregunta es porque se que a veces esa "vuelta" no anda de una y hay que configurar algo en los routers.
No se como para ayudarte en como solucionarlo, pero vi ese problema varias veces (sobre todo relacionado con voip).

Saludos,
Eduardo

---

### Post by Mauro22 on 2009-02-23
Gracias y Gracias!


Les comento, avance no hay ninguno salvo que si pongo la direccion que me da no-ip en el navegador me dirije a la "pagina web" del modem. (zyxel) que se parece a esto:

> **fmsismo said:**
> 1ro, la información que tiene el host tuyo en no-ip, onda misuperservidor.no-ip.com (o como sea el dominio) es coincidente con la ip que te asigno tu isp?

Para esto tenes que ejecutar 
              nsloolup misuperservidor.no-ip.com
Y desde la máquina de tu casa entrar a 
              [http://www.ip-adress.com/](http://www.ip-adress.com/) 
y verificar que los resultados sean coincidentes.

Si no son coincidentes tenes que poner un script o algo que te refresque la información de tu ip externa.

Saludos

El resultado del nslookup es:

```

nmauro@ubuntu:~$ nslookup darkfiressh.homeip.net
Server:		192.168.0.1
Address:	192.168.0.1#53

Non-authoritative answer:
Name:	darkfiressh.homeip.net
Address: 192.168.1.33


```

Asi que efectivamente se detiene en 1.33 que es el router. De ahi no pasa.

No lo probe de afuera todavia, lo probe desde la intranet saliendo con la ip publica.

---

### Post by guillermolisi on 2009-02-23
> **Mauro22 said:**
> Gracias y Gracias!


Les comento, avance no hay ninguno salvo que si pongo la direccion que me da no-ip en el navegador me dirije a la "pagina web" del modem. (zyxel) que se parece a esto:



El resultado del nslookup es:

```

nmauro@ubuntu:~$ nslookup darkfiressh.homeip.net
Server:        192.168.0.1
Address:    192.168.0.1#53

Non-authoritative answer:
Name:    darkfiressh.homeip.net
Address: 192.168.1.33


```Asi que efectivamente se detiene en 1.33 que es el router. De ahi no pasa.

No lo probe de afuera todavia, lo probe desde la intranet saliendo con la ip publica.
Supongo que en la web de no-ip debe haber documentacion sobre que hacer en estos casos, en forma similar a como lo han documentado los de DynDNS.

Se me ocurre que para que no te quedes en el modem deberias rutear los accesos SSH recibidos en la IP publica a la PC que tiene IP privada. Es decir, con la publica llegas al modem, luego, ruteo de por medio, llegas a tu PC para accesos SSH (si el punto externo es conocido podrias mejorar el ruteo con un dominio o IP) (salvo que el modem solo sea eso y no tenga posibilidad de ruteos).

La IP publica la tiene el modem, asi que el servicio de no-ip parece estar funcionando bien.

Porque cambiarle el port de un servicio seguro como SSH ?

---

### Post by Mauro22 on 2009-02-23
> **guillermolisi said:**
> 
Porque cambiarle el port de un servicio seguro como SSH ?

Vos lo dijiste! Por que? porque asi estaba en un guia que encontre... que lo mas seguro era cambiar el puerto. Y claro nunca andubo.

Probe con un amigo y nada. Volvi al puerto 22 y andubo lo mas bien.




Lo que me faltaria es algun script o comando para actualizar la ip con dyndns.com !!


Estaria solved, salvo por lo del script o comando.






Sigo buscando. Gracias!


EDIT:
PD:

A los admin y moderadores: Que pasa que no volvieron a poner la opcion de Mark As Solved y ahora tampoco esta la Medallita para darle a la gente que me ayudo-

---

### Post by hictio on 2009-02-23
> **Mauro22 said:**
> 
Lo que me faltaria es algun script o comando para actualizar la ip con dyndns.com !!


Mauro,

Viste los clientes de DynDNS para actualizar el cambio de los IPs dinámicos?
Hay para todos los gustos y OSes:

[https://www.dyndns.com/support/clients/](https://www.dyndns.com/support/clients/)

No se como es tu red, pero hoy en día casi todos los routers hogareños tienen la opción para agregar que se actualize el cambio de IP de forma automática con varios de estos servicios, asi no tendrías que instalar nada de nada, en el router hacés todo.

---

### Post by hictio on 2009-02-23
Una cosa más, este acceso lo vas a dejar abierto por un tiempo? O es algo que testeaste y volvés a apagar?

Si lo vas a dejar abierto, es decir, con acceso desde internet, lo mejor que podés hacer es activar el firewall interno del Ubuntu para bloquear qué direcciones se pueden conectar al SSH en tu máquina.

Si no podés con el firewall, por lo menos, bloqueá el acceso al sshd con TCP Wrappers, es instáneo, y sólo tenés que editar /etc/hosts.allow & /etc/hosts.deny via sudo.

Otra cosa importante es que settees en el /etc/ssh/sshd_config la directiva 'AllowUsers', y le agregues el nombre de tu usuario.

Asi:

```

AllowUsers  tu.username.aca

```

Después re-iniciá o dale reload al sshd.

Después de un rato con el puerto de sshd abierto, mira los zombies que tratan de entrar:

```

tail -f /var/log/auth.log

```

---

### Post by sergiom99 on 2009-02-23
pregunta, ya que viene al caso:
En la oficina hay un viejo RHEL que era el antiguo firewall y ahora sigue activo con otras cosas, y lo armaron para que cuando te logueas por SSH, la primera vez te rechaza la contraseña y te hace ponerla 2 veces, para patear los ataques desde afuera.
Como se configura eso?

Salu2- Sergio

---

### Post by Mauro22 on 2009-02-24
Digo otra pregunta para algun otro master!


Con windows conectado a mi laptop por ssh: 

Uso putty y Xming para iniciar un servidor X. 


Pregunta:

Lo grafico lo puede ver en mi pc con windows (ej. emesene) pero el audio sale por la laptop.

Otro ejemplo: Abro banshee, lo veo, interactuo, etc pero el audio sale en la otra pc.


Es algo de tuneles o algo asi? Mientras sigo buscando!


Gracias!! ):P

---

