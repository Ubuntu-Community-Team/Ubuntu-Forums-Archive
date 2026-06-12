---
title: "Problema con el gestor de actualizaciones y lentitud de la red"
date: 2008-09-17
forum: Software
---

### Post by santiagofrias on 2008-09-17
Amigos: Estoy teniendo un problema con el gestor de actualizaciones y la red. Cuando me aparece el icono de que hay nuevas actualizaciones para descargar, le digo que comience y se ve que intenta descargar, pero pasa una eternidad, aunque la conexión para navegar por internet es rápida, lo que me lleva a suspender el gestor, pero reiniciando el equipo.
 A todo esto es una máquina del trabajo basada en Windows y estoy tratando de imponer Linux aqui. Volviendo a mi pregunta: ¿puede ser problema de "Firewall"?, ¿el gestor de act. necesita algún permiso especial?, ¿la lentitud de este se debe a algo distinto?
Gracias desde ya

---

### Post by fmsismo on 2008-09-17
Puede ser que el servidor que estas usando para bajar los paquetes no sea del todo feliz.  Probaste cambiando el servidor del repositorio?

Yo estoy usando [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)

Saludos

---

### Post by santiagofrias on 2008-09-17
> **fmsismo said:**
> Puede ser que el servidor que estas usando para bajar los paquetes no sea del todo feliz.  Probaste cambiando el servidor del repositorio?

Yo estoy usando [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)

Saludos
Como agrego este repositorio? (no te olvides que recién comienzo con el lenguaje linux)

---------------------------------------------------------------------------------------------
[COLOR="Red"]No leí la ayuda de la Guia Ubuntu - Favor de borrar esta última pregunta por el Moderador[/COLOR]

---

### Post by fmsismo on 2008-09-17
Desde el synaptic, settings, en la pestaña ubuntu software, tenes un desplegable descargar de...

Avisame si te complicas.

Saludos

---

### Post by leo_rockway on 2008-09-17
Probá de ir a una terminal y poner "sudo apt-get update". Si se queda trabado es que los servidores que estás usando tienen algún problema. Si el problema es otro el mensaje de error que te tire nos va a ayudar a darte una solución.

Por cierto, yo recomiendo los servidores de Brasil (cambiá el 'us' por 'br' en la dirección que te pasó fmsismo). Y por las dudas, vale la pena aclarar: __No__ conviene usar los de Argentina porque por alguna extraña razón se encuentran en el Reino Unido, así que van bastante lentos.

---

### Post by santiagofrias on 2008-09-17
Ok, gracias leo y fmsismo, mañana a primera hora hago los cambios y les comento; pasa que la máquina está en la oficina y solo voy por las mañanas.
Pero me parece que es problema con el firewall del trabajo, (ya antes con windows no podíamos salir con el Messenger, ni usar Emule, ni ningún prog. P2P) así que vamos a probar...

---

### Post by santiagofrias on 2008-09-18
Bueno, agregue los repositorio de brasil pero al ir a la terminal me tira el siguiente error

Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy Release.gpg                          
  No pude resolver 'br.archive.ubuntu.com'
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/main Translation-es                  
  No pude resolver 'br.archive.ubuntu.com'
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/restricted Translation-es            
  No pude resolver 'br.archive.ubuntu.com'
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/universe Translation-es              
  No pude resolver 'br.archive.ubuntu.com'
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/multiverse Translation-es            
  No pude resolver 'br.archive.ubuntu.com'
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates Release.gpg                  
  No pude resolver 'br.archive.ubuntu.com'
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/main Translation-es          
  No pude resolver 'br.archive.ubuntu.com'
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/restricted Translation-es    
  No pude resolver 'br.archive.ubuntu.com'
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/universe Translation-es      
  No pude resolver 'br.archive.ubuntu.com'
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/multiverse Translation-es    
  No pude resolver 'br.archive.ubuntu.com'
Err [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                          
  No pude resolver 'archive.canonical.com'
Err [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-es               
  No pude resolver 'archive.canonical.com'
Leyendo lista de paquetes... Hecho                                          
W: Imposible obtener [http://br.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://br.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  No pude resolver 'br.archive.ubuntu.com'

W: Imposible obtener [http://br.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-es.bz2](http://br.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-es.bz2)  No pude resolver 'br.archive.ubuntu.com'

W: Imposible obtener [http://br.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-es.bz2](http://br.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-es.bz2)  No pude resolver 'br.archive.ubuntu.com'

W: Imposible obtener [http://br.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-es.bz2](http://br.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-es.bz2)  No pude resolver 'br.archive.ubuntu.com'

W: Imposible obtener [http://br.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-es.bz2](http://br.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-es.bz2)  No pude resolver 'br.archive.ubuntu.com'

W: Imposible obtener [http://br.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://br.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  No pude resolver 'br.archive.ubuntu.com'

W: Imposible obtener [http://br.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-es.bz2](http://br.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-es.bz2)  No pude resolver 'br.archive.ubuntu.com'

W: Imposible obtener [http://br.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-es.bz2](http://br.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-es.bz2)  No pude resolver 'br.archive.ubuntu.com'

W: Imposible obtener [http://br.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-es.bz2](http://br.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-es.bz2)  No pude resolver 'br.archive.ubuntu.com'

W: Imposible obtener [http://br.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-es.bz2](http://br.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-es.bz2)  No pude resolver 'br.archive.ubuntu.com'

W: Imposible obtener [http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg](http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg)  No pude resolver 'archive.canonical.com'

W: Imposible obtener [http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-es.bz2](http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-es.bz2)  No pude resolver 'archive.canonical.com'

W: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas


Espero que se pueda resolver, gracias desde ya.

---

### Post by faktorqm on 2008-09-18
que pasa si desde una terminal pones este comando? postea la salida.

```
ping -c 4 www.google.com
```

si anda, te tiene que mostrar algo como me muestra a mi:

```
faktorqm@the-edge:~$ ping -c 4 www.google.com
PING www.l.google.com (64.233.169.147) 56(84) bytes of data.
64 bytes from yo-in-f147.google.com (64.233.169.147): icmp_seq=1 ttl=244 time=149 ms
64 bytes from yo-in-f147.google.com (64.233.169.147): icmp_seq=2 ttl=244 time=149 ms
64 bytes from yo-in-f147.google.com (64.233.169.147): icmp_seq=3 ttl=244 time=149 ms
64 bytes from yo-in-f147.google.com (64.233.169.147): icmp_seq=4 ttl=244 time=149 ms

--- www.l.google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3001ms
rtt min/avg/max/mdev = 149.195/149.333/149.464/0.301 ms
faktorqm@the-edge:~$ 

```

si no te llega a andar, tambien postea el comando:

```
cat /etc/resolv.conf
```

a ver que tenes. Salu2!!

---

