---
title: "Repositorio con Apt-Mirror da error"
date: 2011-04-25
forum: Software
---

### Post by javierlinux1 on 2011-04-25
Leyendo la lista hace pocos días vi un hilo sobre repositorios locales y refloté la idea.

Tengo una maquina que uso de server, con Ubuntu Server 10.04.2 y quise armar el repo ahi, segui un par de tutoriales, hasta que me quedo todo configurado, el problema surge cuando corro "apt-mirror", me da el siguiente error:

Downloading 16 index files using 16 threads...
Begin time: Sun Apr 24 23:42:15 2011
[16].[15].[14].[13].[12].[11].[10]...... [2]... [1]... [0]...
End time: Sun Apr 24 23:42:16 2011

Proceed indexes: [Psh: cannot open archive.ubuntu.com/ubuntu//dists/lucid-updates/main/binary-: No such file
apt-mirror: can't open index in proceed_index_gz at /usr/bin/apt-mirror line 449.

No puedo encontrar cual es el error, veo ahí dos "/" juntas, antes de "dists", que no se si está bien o no, pero otra cosa no encuentro, si alguno me pueda dar una idea, se los agradezco.

Javier

PD: Publique la consultaayer en la lista, pero no recibi ninguna respuesta, por eso lo publico acá tambien. Saludos

---

### Post by javierlinux1 on 2011-04-27
Nadie vio esta consulta? Si alguno me puede dar una mano, agradecido.
Saludos y perdon por el mail, pero no encuentro otra solucion despues de haber intentado varias veces

Saludos y gracias a todos
jawifi01

---

### Post by javierlinux1 on 2011-04-29
Hago un intento más...si alguien me ayuda, agradecido.

Javier

---

### Post by javierlinux1 on 2011-05-01
Sigo tratando de hacerlo funcionar, algo baja, pero da este error ahora:


gzip: stdin: not in gzip format
Psh: cannot open ubuntu.innova-red.net/ubuntu///dists/maverick/main/binary-i386/Packages.gz: No such file
apt-mirror: can't open index in proceed_index_gz at /usr/bin/apt-mirror line 449.

Y no encuentro cual es el problema. Alguien tiene alguna idea?
Gracias

---

### Post by guillermolisi on 2011-05-01
Javi, proba desde otro mirror. Yo usaria los oficiales (Main servers) hasta que estes seguro que no tenes problemas de intalacion y configuracion.

---

