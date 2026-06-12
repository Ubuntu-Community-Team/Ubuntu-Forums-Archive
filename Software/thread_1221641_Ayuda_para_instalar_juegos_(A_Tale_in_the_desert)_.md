---
title: "Ayuda para instalar juegos (A Tale in the desert) (O a.d.)"
date: 2009-07-24
forum: Software
---

### Post by matias_tati on 2009-07-24
Hola que tal encontre este juego navegando por la red (O a.d.) y me baje incluso el archivo de un post pero luego lei que hay que compilar para poder probarlo y la verdad que este juego vale la pena el intento. Si alguien sabe como hacerlo me haria un gran favor. Y el otro (A tale in the desert) Entro a la pag oficial y cuando le doy download me salen en el navegador una serie de textos que no se que son y qisiera saber si solo se puede jugar on line Gracias.

---

### Post by guillermolisi on 2009-07-24
Links, please ?

---

### Post by matias_tati on 2009-07-24
[http://www.atitd.com/linuxc.html](http://www.atitd.com/linuxc.html)

[http://www.vivalinux.com.ar/soft/0-a.d](http://www.vivalinux.com.ar/soft/0-a.d).

---

### Post by staar on 2009-07-24
para instalar el 'A tale in the desert' hacé click derecho donde dice 'Click here to download' y seleccioná 'Guardar contenido enlazado como' (en opera es esa la opción, ni idea en firefox, pero supongo que será similar) guardalo en tu home, después abrí una terminal y corré ```
chmod 777 eClient-linux-i686.run
``` para darle permisos de ejecución, y después ```
./eClient-linux-i686.run
``` para correr el instalador, que te va a guiar para bajar todo...

de 0 AD tené en cuenta que no está terminado, y como dijeron en otro post, todavía le falta la IA, por lo que solo se puede jugar en LAN y no contra la pc...

saludos

---

### Post by kornykyano on 2009-07-24
0 A.D. esta en fase alfa. y creo que no es jugable, si se puede armar edificios solados y toda la bolud**z. Es muy interesante, por tener gráficos muy buenos. En ubuntu 9.04 parece que corre, yo lo quise probar en HH y falta algunas librerías o algo así :confused:```
`GLIBCXX_3.4.10' not found
```

---

### Post by matias_tati on 2009-07-24
Que lastima pq busco juegos de este tipo y estos dos me parecen fantasticos mas el 0 a.d. esperando ansiosamente entonces. Bueno probare para instalar A Tale in the desert. Gracias!

---

### Post by juancarlospaco on 2009-07-24
> **matias_tati said:**
> Que lastima pq busco juegos de este tipo

[Click aca.]("apt:/glest")

---

### Post by guillermolisi on 2009-07-24
> **juancarlospaco said:**
> [Click aca.]("apt:/glest")

Juanca, revisa el hipervinculo que me parece apunta a cualquier lado.

---

### Post by matias_tati on 2009-07-24
> **guillermolisi said:**
> Juanca, revisa el hipervinculo que me parece apunta a cualquier lado.
Si si. No se te escapa una.

---

### Post by staar on 2009-07-24
el link está bien, glest es un juego de ese tipo y el protocolo apt:/ permite instalar el paquete con un click (desde el firefox de ubuntu) mediante el uso de apt-url

saludos

---

### Post by matias_tati on 2009-07-24
Buenisimo entonces espero que sea algo bueno pq tengo un gusto muy especial para los juegos. Gracias desp les cuento.

---

### Post by matias_tati on 2009-07-24
Me tira esto:

---

### Post by staar on 2009-07-25
posteá la salida de ```
ls -la eClient-linux-i686.run
``` para ver como son los permisos de ese archivo...

saludos

---

### Post by matias_tati on 2009-07-26
Aqui esta

---

### Post by staar on 2009-07-26
debería poder instalarse como usuario normal, en la página no dice nada de que debe hacerse como root (en realidad no dice mucho de nada), pero bueh, corré ```
sudo sh ./eClient-linux-i686.run
``` a ver si así lo instala...

saludos

---

### Post by Mauro22 on 2009-07-26
te falta darle permiso de ejecuccion

```
chmod +x eClient-linux-i686.run
```

Fijate que en la salida de ls -l tenes -rw- te falta la x, o se rwx


No lo instalas como sudo, sino te queda como propietario 'root'

---

### Post by staar on 2009-07-26
> **Mauro22 said:**
> te falta darle permiso de ejecuccion

```
chmod +x eClient-linux-i686.run
```

Fijate que en la salida de ls -l tenes -rw- te falta la x, o se rwx


No lo instalas como sudo, sino te queda como propietario 'root'
uh, tenés razón, lei cualquier cosa antes :-D :-P, perdón...

EDIT: y ahora que me fijo, yo le había pasado mal el chmod :-P le pifié en el número...

saludos

---

### Post by matias_tati on 2009-07-26
Tanto lio para jugar un jueguito? Me siento descolocado mal.

---

### Post by staar on 2009-07-26
eeemmh, es bastante claro eso, te pide que hagas ```
cd ./eClient
``` para moverte al directorio (el comando cd hace eso) del juego, y después te pide que pongas ```
./elaunch
``` para bajar el cliente y después jugar...

saludos

---

### Post by matias_tati on 2009-07-26
Es claro? Entonces soy un cuadrado. Ja ja ja ja!! saludos a ver que pasa

---

### Post by matias_tati on 2009-07-26
No hay caso.

---

### Post by matias_tati on 2009-07-26
Me falto una

---

### Post by staar on 2009-07-26
ahí me mataste, ni idea, parece un bug, fijate en la página del juego...

saludos

---

### Post by Mauro22 on 2009-07-27
Si no te deja escribir son dos:

O no tenes permisos de ejecuccion (como antes) o el juego intenta escribir en / por lo tanto tenes que iniciarlo con sudo.

---

### Post by matias_tati on 2009-07-27
No funciono seguire resignado a no encontrar ningun buen juego para linux y a quedarme callado cada vez que los ventaneros me toquen ese tema. Que va ser. Gracias de todos modos. Saludos!!!!

---

### Post by Mauro22 on 2009-07-27
Ahi lo estoy bajando a ver que onda...


Un juego no nos puede ganar jeje

---

### Post by matias_tati on 2009-07-27
Y la verdad que no pero que se yo en realidad no juego casi en la PC pero queria demostrar que no hay nada que envidiar. Contame despues...

---

### Post by Mauro22 on 2009-07-27
Salió todo joya, che!! 


Estos son los pasos:

```
mauro@mauro-laptop:~/Descargas$ ./eClient-linux-i686.run 
Creating directory eClient
Verifying archive integrity... All good.
Uncompressing ATITD linux i686 client install.................................. (mucho de eso)

To download client and play: cd ./eClient then hit the enter key, then type: ./elaunch and hit the enter key
mauro@mauro-laptop:~/Descargas$ cd eClient/ && ./elaunch

```

Y nada más...

---

### Post by matias_tati on 2009-07-27
Estoy orinado por un elefante. Ahora intento de nuevo. Saludos. Se puede instalar en español?

---

### Post by matias_tati on 2009-07-27
Me sigue poniendo lo mismo de las capturas de arriba. Lomio es grabe creo desde que tengo Ubuntu me costo todo el doble.

---

### Post by matias_tati on 2009-10-13
ja ja ja ja ja ja m Rio de Janeiro

[[img]http://h.imagehost.org/t/0967/Pantallazo.jpg[/img]](http://h.imagehost.org/view/0967/Pantallazo)

---

