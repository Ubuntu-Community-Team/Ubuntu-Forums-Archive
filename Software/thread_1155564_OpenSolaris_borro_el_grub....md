---
title: "OpenSolaris borro el grub..."
date: 2009-05-10
forum: Software
---

### Post by Just64 on 2009-05-10
Tenia el Ubu 9.04, instalo OpenSolaris en un sector libre del disco y me piso el grub por lo q veo, y el cd del SuperGrub no me lo puede recuperar, me tira un error. Como recupero el Grub de ubuntu 9.04?

---

### Post by pablo.s on 2009-05-10
Editá el grub de OpenSolaris
para que lea a Jaunty, mas facil.

---

### Post by Just64 on 2009-05-10
Como? Aparte no se cual es el archivo del grub de solaris...


```
pato@PatoLaptop:/boot/grub$ ls
bin	       install_menu	 reiserfs_stage1_5  ufs2_stage1_5
capability     iso9660_stage1_5  splash.xpm.gz	    vstafs_stage1_5
default        jfs_stage1_5	 stage1		    xfs_stage1_5
e2fs_stage1_5  minix_stage1_5	 stage2		    zfs_stage1_5
fat_stage1_5   nbgrub		 stage2_eltorito
ffs_stage1_5   pxegrub		 ufs_stage1_5

```

---

### Post by pablo.s on 2009-05-10
En [este articulo]("http://blogs.sun.com/abhi/entry/installing_opensolaris_and_opensuse_10") se explica
bastante bien.

---

### Post by Just64 on 2009-05-10
Claro el problema es q no puedo ver/modificar el menu.lst !
Aparte q no me puedo logear como root...

Aparte cada vez q quiero ejecutar el sudo desde la terminal me aparece esto:

```
pato@PatoLaptop:~$ sudo gedit

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

Password: 
pato is not in the sudoers file.  This incident will be reported.

```

---

### Post by pablo.s on 2009-05-10
pfexec gedit

---

### Post by Just64 on 2009-05-10
Pero no tengo el menu.lst , no me aparece el archivo en /boot/grub/ 
No se cual es el derivado de ese archivo en OpenSolris...

```
pato@PatoLaptop:/boot/grub$ ls -la
total 1208
drwxr-xr-x 3 root sys     24 2009-05-10 23:45 .
drwxr-xr-x 5 root sys      6 2009-05-10 23:45 ..
drwxr-xr-x 2 root sys      3 2009-05-10 23:44 bin
-r--r--r-- 1 root sys   1867 2008-11-19 22:34 capability
-r--r--r-- 1 root sys     10 2008-11-19 22:34 default
-rw-r--r-- 1 root sys   8532 2008-11-19 22:34 e2fs_stage1_5
-rw-r--r-- 1 root sys   8228 2008-11-19 22:34 fat_stage1_5
-rw-r--r-- 1 root sys   7540 2008-11-19 22:34 ffs_stage1_5
-rw-r--r-- 1 root sys   1447 2008-11-19 22:34 install_menu
-rw-r--r-- 1 root sys   7640 2008-11-19 22:34 iso9660_stage1_5
-rw-r--r-- 1 root sys   9028 2008-11-19 22:34 jfs_stage1_5
-rw-r--r-- 1 root sys   7732 2008-11-19 22:34 minix_stage1_5
-rw-r--r-- 1 root sys 136048 2008-11-19 22:34 nbgrub
-rw-r--r-- 1 root sys 137072 2008-11-19 22:34 pxegrub
-rw-r--r-- 1 root sys   9972 2008-11-19 22:34 reiserfs_stage1_5
-rw-r--r-- 1 root sys  47330 2008-11-19 22:34 splash.xpm.gz
-rw-r--r-- 1 root sys    512 2008-11-19 22:34 stage1
-rw-r--r-- 1 root sys 136688 2008-11-19 22:34 stage2
-rw-r--r-- 1 root sys 136688 2008-11-19 22:34 stage2_eltorito
-rw-r--r-- 1 root sys   7412 2008-11-19 22:34 ufs_stage1_5
-rw-r--r-- 1 root sys   7816 2008-11-19 22:34 ufs2_stage1_5
-rw-r--r-- 1 root sys   7220 2008-11-19 22:34 vstafs_stage1_5
-rw-r--r-- 1 root sys   9852 2008-11-19 22:34 xfs_stage1_5
-rw-r--r-- 1 root sys  17804 2008-11-19 22:34 zfs_stage1_5


```

---

### Post by pablo.s on 2009-05-11
No te enrosqués con el OpenSolaris
por ahora, te metiste en un mambo,
podés probar el [método de recuperación]("http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB")
de Grub desde LiveCD. Sabés como es?


PD: Necesitás OpenSolaris por
algo en especial? Perdoná si la
pregunta es tonta.

---

### Post by pablo.s on 2009-05-11
Estás desarrollando en Java?
Te recomiendo que leas la [URL="http://es.opensolaris.org/gesce/"]Guia
del Estudiante[/URL], está muy bien
redactada, a mi me sirvió para
aclarar las diferencias que hay
de un sistema al otro.

Perdoná lo de la explicación,
pero OpenSolaris lo tengo
instalado en otra máquina que
no es esta y tampoco la tengo
acá en mi casa.

---

### Post by Just64 on 2009-05-11
Voy a ver si puedo recuperar el grub como vos decis.

La verdad no lo necesito para nada, lo baje por y lo instale xq netbeans me tira un par de errores con Ubu. Espero no haber perdido nada por q tenia unas cosas de la facu q me van a atrasar bastante si no las recupero. Encima estoy escuchando los head_park q esta haciendo y el ruido q hace es tremendo, me esta fumando el disco como nunca.

---

### Post by Just64 on 2009-05-11
Che lo arregle siguiendo el tuto del livecd , gracias!!!

---

