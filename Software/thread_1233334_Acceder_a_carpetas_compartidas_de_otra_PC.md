---
title: "Acceder a carpetas compartidas de otra PC"
date: 2009-08-06
forum: Software
---

### Post by LolaMora on 2009-08-06
Hola a todos.:)
Tengo el siguiente problema:
Tenemos 2 PCs con Ubuntu 9.04. La que tiene placa de red cableada esta conectada a un router y el router al modem de la banda ancha de telefonica.
La otra PC tiene placa inalambrica y se conecta perfectamente a Internet a traves del router que esta a seis metros.
El problema radica en que no tengo idea (soy aprendiz) como comunicar las dos PCs. Quisiera poder acceder  a una carpeta compartida de la otra PC.:confused:
Instale el samba4 y le di propiedades de compartida a una carpeta que cree en mi /home/usuario. Pero llego hasta aca. 

Agradeceré al que pueda darme una mano.

---

### Post by sergiom99 on 2009-08-06
Hola.
Aca tenes un excelente y sencillo tutorial que hizo Faktorqm para Compartir carpetas.
[http://ubuntu-ar.org/tutoriales/samba](http://ubuntu-ar.org/tutoriales/samba)

Suerte!
Sergio

---

### Post by jjgomera on 2009-08-06
es que si son dos ubuntu no necesitas samba, se hace con nfs:
-instalas nfs-user-server en el ordenador que va a recibir
-instalas nfs-kernel-server en el ordenador que va a servir los archivos
-defines los directorios a compartir editando el archivo /etc/exports, indicando también la ip del ordenador que podrá acceder a ellospor ejemplo para compartir todo el sistema de archivos con permisos de lectura y escritura:
```
/	192.168.0.129(rw)
```
-reinicias nfs
-montas la partición en el otro ordenador:
```
sudo mount -t nfs 192.168.0.129:/ /media/otro_ordenador
```

---

### Post by guillermolisi on 2009-08-06
Totalmente de acuerdo con JJGomera. Es muchisimo mas rapido y facil NFS que Samba, asi que teniendo maquinas solamente con Linux, no tiene sentido Samba.

---

### Post by sergiom99 on 2009-08-06
> **guillermolisi said:**
> Totalmente de acuerdo con JJGomera. Es muchisimo mas rapido y facil NFS que Samba, asi que teniendo maquinas solamente con Linux, no tiene sentido Samba.

Entonces Lola la guía que necesitas es [http://ubuntu-ar.org/node/208](http://ubuntu-ar.org/node/208) , escrita por Sismo.

---

### Post by sergiom99 on 2009-08-06
Estaba leyendo la guía de Sismo y lo explicado por jjgomera, y en ambos veo que la carpeta compartida hay que agregarla al fstab y/o montarla.
Usando Samba, en el cliente yo agrego a la barra de Dolphin un acceso directo con, por ejemplo, "smb://desktop/shared" y solo se monta cuando trato de acceder.

Acá se puede hacer lo mismo? O ir buscando por la red la carpeta compartida?
Cómo sería la ruta?

---

### Post by Hei Ku on 2009-08-06
Konqueror al rescate:

En la barra pones nfs://<host>

Y ahi debiera aparecerte.

---

### Post by LolaMora on 2009-08-07
Muchas gracias a todos.
Me sorprendieron al contestar tan rápido.

Esta tarde trabajo con el tutorial que me pasaron.

Nuevamente gracias. ;-)

---

### Post by Kalma on 2010-04-20
> **Hei Ku said:**
> Konqueror al rescate:

En la barra pones nfs://<host>

Y ahi debiera aparecerte.

Hola,

a mí no me ha funcionado ni desde Firefox ni desde Nautilus (me dice que no reconoce el protocolo en ambos casos). Lo que sí me ha funcionado es:

```
showmount <host> --exports
```

desde la consola. Donde <host> es el nombre o dirección IP de la máquina de la que queramos saber lo que tiene compartido con NFS.

Saludos.

---

