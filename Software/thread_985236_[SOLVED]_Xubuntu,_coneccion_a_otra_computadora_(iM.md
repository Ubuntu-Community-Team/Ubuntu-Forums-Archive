---
title: "[SOLVED] Xubuntu, coneccion a otra computadora (iMac)"
date: 2008-11-17
forum: Software
---

### Post by DrKenobi on 2008-11-17
Hola! Recien termino de instalar Xubuntu 8.10 con el Wubi en mi PC. La verdad, muy contento!!

Pero se me presento un pequeño problema. En mi casa tengo una red WiFi y dentro de esa red varias computadoras, todas iMac. ¿Como hago para conectarme a ellas y poder acceder al disco y usuario? (como la mac de mi hna tiene un disco mas grande, lo uso como disco externo, es lento, pero util)

Lo principal es que no encuentro nada que diga Network o similar....je

Muchas gracias!

---

### Post by hictio on 2008-11-17
Que sistema operativo tienen esas iMacs? Tiger? Leopard?

---

### Post by DrKenobi on 2008-11-17
Mac OS 10.4.11 "Tiger"

---

### Post by hictio on 2008-11-17
Excelente, en la maquina Apple, anda a Manzanita, "System Preferences", "Internet & Network", "Sharing".
En "Services", habilita "Remote Login".

Desde tu maquina Linux te podes conectar al Tiger abriendo un Terminal, y tipeando:

```

ssh direccion.ip.maq.tiger (ENTER)

```

Si el usuario con el cual estas conectado a la maquina Linux es diferente que el que te loggeas a Tiger, tenes que pasarle el parametro asi:
```

ssh -l nombre.de.usuario.aca direccion.ip.maq.tiger (ENTER)

```

Sino te gusta la linea de comando, o necesitas otra cosa. en Ubuntu (no estoy seguro en Xubuntu) en el Menu de "Places" casi al final hay una opcion "Connect to Server", abrila, y selecciona "SSH", completa los datos (con direccion IP & username es suficiente).
Con eso podes acceder en forma grafica al Os X.
Lo importante es que habilites en el Os X la opcion para poder loggearse via SSH.

---

### Post by DrKenobi on 2008-11-17
hictio: muchas gracias, todo lo que dijiste anduvo y me pude conectar por ssh. Pero ahora lo que no se es como hacer para una vez conectado poder pasar archivos con el mouse (soy un usuario Mac de toda la vida ja).

Lamentablemente en Xubuntu no hay en el Menu "Places" la opcion "Connect to Server".

Otra consultita: habilitando el ssh en la iMac, cualquiera se puede conectar a la iMac, pero solo si esta dentro de la red casera? o tambien via internet?

Gracias!!

---

### Post by hictio on 2008-11-17
El firewall por default de Tiger, una vez abierto el servicio, permite conexion desde cualquier lugar HACIA ese servicio.
Eso me parece una soberana c*g*d*.
Pero, si vos tenes un router WiFi, por ejmplo, en el borde de tu red interna y entre internet, a menos que en el router hayas permitido el acceso (ya sea a tu Os X en gral, o a ese servicio en particular), no se van a poder conectar a tu Os X.

Si te interesa, en mi blog puse un posts con scripts para poner el firewall interno de Tiger mucho mas restrictivo, [link](http://oesediez.blogspot.com/search/label/ipfw%20firewall)

Otra cosa, demas esta decir que podes hacer el camino inverso, acceder desde Os X a Linux, si en la maq. Ubuntu le instalas el paquete 'openssh-server'.

```

sudo aptitude install openssh-server (ENTER)

```

Tambien, por default, el acceso va a ser irrestricto al servicio.
Desde Os X, hay un cliente grafico para SSH, gratuito, [Fugu](http://rsug.itd.umich.edu/software/fugu/).

---

### Post by hictio on 2008-11-17
Nunca use Xubuntu, pero al parecer, no vas a poder montar tu directorio de la iMac por SSH, porque no tiene soporte nativo para eso, aunque quizas alguno usuario te pueda confirmar si en la version mas nueva eso no cambio.

[equivalent to connect to server(ssh) program in xubuntu?](http://ubuntuforums.org/showthread.php?t=322907)
[Connect to SSH Server in Xubuntu](http://ubuntuforums.org/showthread.php?t=465596)
[HOWTO: Mount SSH Shares](http://ubuntuforums.org/showthread.php?t=103860)

Otra opcion, es que en la maq con Xubuntu, te instales el [Filezilla](http://filezilla-project.org/), que tiene soporte para SSH.

En el Xubuntu, abri un terminal, y tipea para instalarlo:

```

sudo aptitude install filezilla (ENTER)

```

---

### Post by DrKenobi on 2008-11-17
Al final, como me dijistes, instale el FileZilla y ya estoy pasando archivos de aca para alla con sftp.

Estuve viendo tu blog y esta muy interesante lo del firewall, voy a ver de ponerlo en practica en los proximos dias.

Muchas gracas!!!

---

### Post by faktorqm on 2008-11-17
Tambien podes instalar samba en ambos SO's y tambien te deberian funcionar todas las cosas. No es la mejor opcion pero capaz algun dia te saca del paso. Salu2!

---

