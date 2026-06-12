---
title: "Problema con repositorios auxilio !"
date: 2009-05-08
forum: Software
---

### Post by zoroastro444 on 2009-05-08
Hoy estube tocando la lista de repositorios y sin querer los borre pero quedo algo trabado creo porque cuando voy al gestor de paquetes Synaptic me da este error:

E: Tipo 'hhj' desconocido en la línea 3 de lista de fuentes /etc/apt/sources.list.d/dropbox.list
E: No se pudo leer la lista de fuentes.
Vaya al diálogo del repositorio para corregir el problema.
E: _cache->open() failed, please report.

 
creo que tengo que poner una nueva lista de repositorios, pero no tengo idea como, busque varias y las fui poniendo en 
sudo gedit /etc/apt/sources.list 

pero siempre sale algun error quiza es porque estaban mal las listas, no se que onda
necesito arreglar esto por favor ayuda!!!

---

### Post by pablo.s on 2009-05-08
Que versión usás? (8.04 / 8.10 / 9.04)

---

### Post by zoroastro444 on 2009-05-08
9.04

---

### Post by Hei Ku on 2009-05-08
Primero que nada, copia lo que tengas ahora a otro archivo, y dejar el sources.list vacio.
Despues, pone en una terminal:

sudo apt-get update

Si te anda ok, entonces postea lo que tenias en el sources.list y lo vamos arreglando.

---

### Post by pablo.s on 2009-05-08
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-proposed restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-backports restricted main multiverse universe

---

### Post by zoroastro444 on 2009-05-08
E: Tipo 'hhj' desconocido en la línea 3 de lista de fuentes /etc/apt/sources.list.d/dropbox.list

este error me sale con la lista vacia.



y esta es la lista que tenia :

## sources.list
  ## General comments about the sources.list file
  deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted
  deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted

  ## Comment about the 'Update' repositories
  ## Comments about the role of the updates
  deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted
  deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty -updates main restricted

  ## Comment on the 'Universe' repositories
  ## Comment about the support limitations of Universe & Multiverse
  ## repositories as well as licence restrictions and update policies.
  ## Please satisfy yourself as to your rights to use the software.
  # deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse
  # deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse

  ## Comment on the 'Backports' repository
  ## N.B. software from this repository may not have been tested as
  ## extensively as that contained in the main release, although it includes
  ## newer versions of some applications which may provide useful features.
  ## Comment about update and security update limitations
  # deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty -backports main restricted universe multiverse
  # deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty -backports main restricted universe multiverse 
  # deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty -security main restricted
  # deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty -security main restricted

---

### Post by zoroastro444 on 2009-05-08
Pablo, me sigue saliendo el mismo error con esta lista.

---

### Post by pablo.s on 2009-05-08
Feisty? 7.04 tenés entonces...

---

### Post by pablo.s on 2009-05-08
Te aconsejo bajar la ISO de
9.04 y actualizar.

---

### Post by zoroastro444 on 2009-05-08
ya tengo la ultima version  (Jaunty) 9.04

---

### Post by pablo.s on 2009-05-08
Y de donde salió este sources.list
con referencias a Feisty?

---

### Post by Hei Ku on 2009-05-08
Tenes algun archivo en la carpeta /etc/apt/sources.list.d/?

Si es así, copialos a otro lado, que la carpeta quede vacía.

---

### Post by zoroastro444 on 2009-05-08
[B]Y de donde salió este sources.list
con referencias a Feisty?
[/B]
La saque de una pag , me confundi. 



[B]Tenes algun archivo en la carpeta /etc/apt/sources.list.d/?

Si es así, copialos a otro lado, que la carpeta quede vacía. 	

[/B]Tengo un par de archivos pero como hago para eliminarlos desde la consola? ya los copie pero desde la consola como se borran? ,, si los borro se supone que tiene que funcionar? ,, como decia arriba, es el problema de la lista que esta mal?, el error que aparece de "hhJ" de que es?

---

### Post by rubioo on 2009-05-08
Para borrar archivos tenes que usar el comando **rm**

  > rm [archivo]

 Si tenes alguna duda, man rm.
 
 PD: si no los podes borrar asi, pone "sudo rm [archivo]"
 
          Saludos

---

### Post by pablo.s on 2009-05-08
> **rubioo said:**
> si no los podes borrar asi, pone "sudo rm [archivo]" 

Cuidado lo que posteas, papi:
un par de parametros más y te
pueden banear de por vida en
este foro. Leete la advertencia
que dice: [B]Attention All Users
Malicious Commands[/B]

---

### Post by Hei Ku on 2009-05-08
El comando correcto seria:

```

sudo rm /etc/apt/sources.list.d/*

```

Y las advertencias las hacemos los moderadores. rubioo solo respondio la pregunta, sin ningun parametro "complicado".

---

### Post by pablo.s on 2009-05-08
No es una advertencia de moderador
la mia, es una advertencia de usuario.
Por supuesto que no soy moderador,
¿está mal si le aconsejo algo?

---

### Post by rubioo on 2009-05-08
Todo bien, con el consejo. Por ahi tenes razon, en que tendria que haber puesto todo el comando, para que no se confunda.
 Pero me pueden banear por mostrarle como borrar un archivo?

---

### Post by pablo.s on 2009-05-08
No, hasta ahi era normal, pero hay
una famosa combinación que empieza
con erreeme guion erreefe y como
sos un buen muchacho cumplo con
contarte que estaba por ahi la cosa.
Hei Ku hace lo que tiene que hacer,
pero yo solo aconsejé algo, eh...

---

### Post by rubioo on 2009-05-08
Por eso puse > Si tenes alguna duda, man rm. ;)
 Pero igual ya fue, no vamos a discutir por esto.
 Gracias por el consejo
 

    Saludos

---

### Post by EnriqueK on 2009-05-08
Has cometido un grave error en pretender usuar un repositorio diferente a tu versión instalada, pero has tenido suerte por que los repositorios de feisty hace rato que dejaron de estar activos, así que no creo que hayan causado daños al sistema , si hubieras usado otra lista de orígenes de software mas actual y que se encuentre activa, seguro que se te habría armado un safarrancho que te hubiera obligado a reinstalar todo.
Poné en terminal **sudo gedit /etc/apt/sources.list**  borrá todo el contenido y poné el que te pusieron antes.
Luego poné **sudo nautilus /etc/apt/sources.list.d** manteniendo pulsada la tecla mayúsculas (Shift) marcá todas los archivos que aparecen y los borrás.
Lo que queda es perfeccionar tu lista de fuenstes  y para ello puedes entrar a uno de los muchos tutoriales que hay en la red, pero asegurate que sean para jaunty, recomiendo empezar por habilitqr los repositorios de Medibuntu **[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)** , mas adelante podrás agregar mas repositorios, aunque estimo que con esto sería suficiente, no es bueno llenarse de repositorios de orígen desconocido .

---

### Post by infernus92 on 2009-05-08
pero con un "sudo apt-get update" no alcanzaria despues de borrar las fuentes que tiene?

Saludos

---

### Post by EnriqueK on 2009-05-09
> **infernus92 said:**
> pero con un "sudo apt-get update" no alcanzaria despues de borrar las fuentes que tiene?



No, esa sentencia lo que hace es actualizar los archivos índices o índices de repositorios, paso presio a instalar paquetes o actualizaciones, estos índices de repositorios se alojan en /var/lib/apt/lists , estos archivos no deben editarse manualmente, pero puedes por ejemplo copiarlos a otro equipo que no tenga internet y así este podrá generar una lista de paquetes para descargar en otra PC

---

### Post by zoroastro444 on 2009-05-09
Ya borre los archivos y me arme la lista de repositorios ahora me funca de 10, gracias !

disculpen mi ignorancia, soy medio nuevo XD

---

### Post by rubioo on 2009-05-09
> disculpen mi ignorancia, soy medio nuevo XD 

 Nadie nacio sabiendo :)

---

### Post by sajnox on 2009-05-10
Bien que arreglaste el problema, pero me parece que tenes otro

Vos tenias dropbox instalado en tu maquina?? Si es asi, como lo instalaste? Me parece que borraste los repositorios del programa y no se te va actualizar mas

---

### Post by zoroastro444 on 2009-05-13
no , no lo tuve nunca instalado que yo sepa

---

