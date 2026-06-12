---
title: "Error al ejecutar sudo apt-get..."
date: 2008-07-01
forum: Software
---

### Post by PeTTi on 2008-07-01
Cuando quiero descargar algo en la Terminal me aparece esto: 
 
petti@petti-desktop:~$ sudo apt-get update 
sudo: unable to resolve host petti-desktop

---

### Post by anka on 2008-07-01
Se debe a [este]("https://bugs.launchpad.net/ubuntu/+bug/203593") bug.

Edita /etc/hosts

```
sudo gedit /etc/hosts
```

Fijate en las 2 primeras lineas y comproba que sea mas o menos asi:

127.0.0.1 localhost petti-desktop
127.0.1.1 petti-desktop

En la primer linea puede ser que no te aparezca "petti-desktop", en ese caso, ahi ta el error, agregalo.

Suerte!

---

### Post by PeTTi on 2008-07-01
> **anka said:**
> Se debe a [este]("https://bugs.launchpad.net/ubuntu/+bug/203593") bug.

Edita /etc/hosts

```
sudo gedit /etc/hosts
```Fijate en las 2 primeras lineas y comproba que sea mas o menos asi:

127.0.0.1 localhost petti-desktop
127.0.1.1 petti-desktop

En la primer linea puede ser que no te aparezca "petti-desktop", en ese caso, ahi ta el error, agregalo.

Suerte!
exacto,  en otro foro me dijieron lo mismo pero no puedo editarlo.. 

para editarlo entro a nano /etc/hosts y lo edito y todo pero no encuentro al forma de guardarlo.

---

### Post by marianom on 2008-07-01
¿Te estará faltando el sudo antes de nano? (Fijate que anka lo puso pero vos no lo mencionás) No tengo idea como se graba con nano.

---

### Post by anka on 2008-07-01
para guardar en nano es: ctrl+o (de ornitorrinco :P)

Suerte!

---

### Post by PeTTi on 2008-07-01
> **marianom said:**
> ¿Te estará faltando el sudo antes de nano? (Fijate que anka lo puso pero vos no lo mencionás) No tengo idea como se graba con nano.
es que son sudo tengo error, y lo guardo con ctrl + O y con que nombre lo guardo?
Lo quiero guardar con el mismo y me dice que no tengo permiso (y jamas me pide la pass)

---

### Post by Hei Ku on 2008-07-01
que error te da con sudo? copia aca lo que pones en la consola y el error que te da. Exacto, no como te lo acordas.

Una cosa importante, para que recuerdes y tengas en cuenta, es que en Linux los errores sí tienen significado. Para darte ayuda mas rapida, lo mejor es que copies siempre el error que te da, no decir que te dio error y nada mas.

---

### Post by PeTTi on 2008-07-01
> **Hei Ku said:**
> que error te da con sudo? copia aca lo que pones en la consola y el error que te da. Exacto, no como te lo acordas.

Una cosa importante, para que recuerdes y tengas en cuenta, es que en Linux los errores sí tienen significado. Para darte ayuda mas rapida, lo mejor es que copies siempre el error que te da, no decir que te dio error y nada mas.
petti@petti-desktop:~$ sudo apt-get update 
sudo: unable to resolve host petti-desktop

ese error me da.. y bueno cuando pongo
petti@petti-desktop:~$ sudo gedit /etc/hosts
sudo: unable to resolve host petti-desktop

---

### Post by dgcampos on 2008-07-01
> **PeTTi said:**
> petti@petti-desktop:~$ sudo apt-get update 
sudo: unable to resolve host petti-desktop

ese error me da.. y bueno cuando pongo
petti@petti-desktop:~$ sudo gedit /etc/hosts
sudo: unable to resolve host petti-desktop

probaste con su? no se digo...

su gedit /etc/hosts

---

### Post by Hei Ku on 2008-07-01
el problema es tu archivo /etc/hosts
Dentro de ese archivo deberia figurarte petti-desktop
Despues de eso vas a poder utilizar la consola normalmente. Esto no tiene nada que ver con un problema del apt-get

---

### Post by anka on 2008-07-01
Sujerencia .., y si le mandas un live cd de algo y probas de montar el disco y editar el susodicho archivo?

---

### Post by PeTTi on 2008-07-02
Yo entro con nano /etc/hosts y puedo entrar pero cuando lo guardo me dice
[ Error guardando '/etc/hosts': Permiso denegado ]

Y con y con su me dice que no existe algo asi..
Cuando encuentre el cd Live lo pongo e intento.

---

### Post by Hei Ku on 2008-07-02
Apreta Alt+F2 y pone: gksudo gedit /etc/hosts

---

### Post by PeTTi on 2008-07-03
> **Hei Ku said:**
> Apreta Alt+F2 y pone: gksudo gedit /etc/hosts
lo hicey  se estaba por inicia runa aplicacion pero no se inicio xD.

Cuando encuentre el Live cd me fijo eso que me dijieron, yo no lo encuentro asi que ya se lo pedi a un amigo.

---

### Post by PeTTi on 2008-07-06
Ya entre como root, modifique el /etc/hosts y asi quedo


  GNU nano 2.0.7            Fichero: /etc/hosts                                 

127.0.0.1 localhost petti-desktop.DATALAN
127.0.1.1 petti-desktop.DATALAN

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
127.0.1.1 localhost


pero sigo teniendo el mismo error con el 'sudo'.

---

### Post by Hei Ku on 2008-07-06
pone petti-desktop a secas

---

### Post by PeTTi on 2008-07-07
Ya esta, hice ese cambio de sacar el Datalan y ya funciona
Gracias a todos :D

---

### Post by PeTTi on 2008-08-31
[FONT=Century Gothic]Solucionado otra vez        :D[/FONT][FONT=Century Gothic]
[/FONT]

---

