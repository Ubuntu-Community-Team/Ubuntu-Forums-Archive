---
title: "ubuntuiES"
date: 2009-03-28
forum: Software
---

### Post by chaos-legion on 2009-03-28
no sabia donde preguntar asi que aka lo dejo... miren, yo quiero instalar en mi pendrive el ubuntuiES, tengo 2 problemas. en la web oficial de ubuntu la mayoria de los mirror no andan, consegui un torrent que luego copie en el pen, al butearlo me dice que falta el kernel :S
la vercion que consegui es la 8.03.31 si alguien me puede auxiliar XD muchisimas grasias.

P.D: ya se que hay muchas otras distroas linux para instalar en pen, pero yo soy usuario novato de linux y ubuntu es la distro con la que me siento mas comodo y me gustaria poder llevarla en mi pen para trabajar en la facu y el trabajo.

desde ya muchas grasias.

---

### Post by guillermolisi on 2009-03-28
> **chaos-legion said:**
> no sabia donde preguntar asi que aka lo dejo... miren, yo quiero instalar en mi pendrive el ubuntuiES, tengo 2 problemas. en la web oficial de ubuntu la mayoria de los mirror no andan, consegui un torrent que luego copie en el pen, al butearlo me dice que falta el kernel :S
la vercion que consegui es la 8.03.31 si alguien me puede auxiliar XD muchisimas grasias.

P.D: ya se que hay muchas otras distroas linux para instalar en pen, pero yo soy usuario novato de linux y ubuntu es la distro con la que me siento mas comodo y me gustaria poder llevarla en mi pen para trabajar en la facu y el trabajo.

desde ya muchas grasias.
No me tome el trabajo de verificar si oficialmente hay mirrors para esta distribucion de Ubuntu, pero lejos de no funcionar, cada vez andan mejor.

Cuando decis que copiaste el torrent al pendrive, copiaste literalmente ese archivo o llevaste a cabo un proceso de instalacion propiamente dicho ?

---

### Post by chaos-legion on 2009-03-28
el torrent tenia era un iso. lo descomprimi y tenia estos archivos:

directorio - BOOT
directorio - CASPER
directorio - LIB
y un archivo - BOOT

las carpetas y el archivo los meti en el pen, suponiendo que con estos bootearia normalmente.

---

### Post by pablo.s on 2009-03-28
Si todavia tenés la ISO, probá instalando **unetbootin**. Desde 
ese programa se graba la iso al pendrive haciendo arrancable.

sudo apt-get install unetbootin

Saludos

---

### Post by guillermolisi on 2009-03-28
> **chaos-legion said:**
> el torrent tenia era un iso. lo descomprimi y tenia estos archivos:

directorio - BOOT
directorio - CASPER
directorio - LIB
y un archivo - BOOT

las carpetas y el archivo los meti en el pen, suponiendo que con estos bootearia normalmente.
Es que con solo descomprimir no alcanza para que el pendrive sea booteable.
Hace falta grabar, entre otras cosas, informacion en el Master Boot Record (MBR) para que el BIOS de la maquina sepa que en ese pendrive hay un SO para iniciar la maquina.

Por lo que contas y como lo contas, solo copiaste archivos.

Adhiero a la recomendacion de pablo.s

---

### Post by chaos-legion on 2009-04-01
Muchisimas gracias. use el programa que menciono pablo.s para instalar la imagen en el pen y anduvo genial.

---

