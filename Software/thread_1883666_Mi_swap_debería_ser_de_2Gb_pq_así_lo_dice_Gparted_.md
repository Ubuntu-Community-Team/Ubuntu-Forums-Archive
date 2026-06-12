---
title: "Mi swap debería ser de 2Gb pq así lo dice Gparted pero en realidad es de 3Gb"
date: 2011-11-19
forum: Software
---

### Post by esbrinartot on 2011-11-19
El problema que tengo si miro el espacio asignado a SWAP mediante Gparted veo que son 2Gb tal y como configure en la instalación: (ver link adjunto)

[http://img411.imageshack.us/img411/7834/201111192033121680x1050.png](http://img411.imageshack.us/img411/7834/201111192033121680x1050.png)

Si mediante la terminal escribo el comando free son 3 GB (ver resultado):

total used free shared buffers cached
Mem: 1017540 902348 115192 0 25480 577188
-/+ buffers/cache: 299680 717860
Swap: 3072700 18108 3054592

Es muy raro... Pq me pasa esto?
También noto que a pesar de tener el valor de swappiness a 10 la memoria de intercambio se activa demasiado. Creo que da igual el valor que le ponga que el ordenador usa el valor que quiere

Tengo que comentar que recien instalado lubuntu 11.10 me dio el siguiente error:

/dev/mapper/cryptswap1 no esta listo o presente.

"según me informe este error ocurre siempre que cifres tu partición home"

Para solucionar este problema hice lo siguiente: (No se si esto puede causar el problema?)

sudo swapoff - a
sudo cryptsetup remove /dev/mapper/cryptswap1
sudo gedit /etc/crypttab
dentro de este archivo comenté/borré la siguiente linea:
# cryptswap1 /dev/sda8 /dev/urandom swap,cipher=aes-cbc-essiv:sha256
después en la terminal:
sudo /sbin/mkswap /dev/sda9
sudo swapon /dev/sda9
sudo gedit /etc/fstab
y dentro del archivo cambié esta linea:
/dev/maer/cryptswap1 none swap sw 0 0
por esta otra:
/dev/sda9 none swap sw 0 0

Reinicié y después habilité la partición cifrada mediante:
sudo ecryptfs-setup-swap

A ver si alguien me ayuda a saber si miro la swap que tengo mediante gptared o free me da valores diferentes

---

### Post by esbrinartot on 2011-12-03
Encontré la respuesta ya hace tiempo pero hago el post.

Todo lo que pasaba era porqué instalé Zram. Zram es quien crea las particiones que en teoria yo no habia creado conscientemente.

Ahora Lubuntu funciona de maravilla

---

