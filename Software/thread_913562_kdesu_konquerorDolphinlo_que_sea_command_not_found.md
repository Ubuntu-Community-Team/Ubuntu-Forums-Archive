---
title: "kdesu konqueror/Dolphin/lo que sea: command not found"
date: 2008-09-07
forum: Software
---

### Post by valucha on 2008-09-07
[COLOR="DarkOrchid"]Hola!!
Vengo con algo que según creo que un bug o algo que me anda funcionando mal en la máquina.

En resumidas cuentas: no puedo o no sé abrir nada con permisos de root. Está bien que recién empiezo con KDE, pero vamos! no puede ser tan complicado... BUsqué por internet y descubrí que, a diferencia de gnome, hay que usar sudo para la shell y kdesu para los programas graficos. Ponga lo que ponga me salta una ventanita externa a la temrinal y me dice "command not found".

¿Se hace de otra forma o es algún error?.

Si de algo sirve tengo Kubuntu con KDE 4.1 recien recien instaladito hoy sin tocarle nada.


Gracias desde ya :)[/COLOR]

---

### Post by sergiom99 on 2008-09-07
que comando estas tratando de correr despues del sudo?
porque si es un alias a veces no lo reconoce como alias de root.

tambien tenes 'kdesudo'

---

### Post by Hei Ku on 2008-09-07
kdesu es mejor que kdesudo.

si pones en la terminal konqueror anda ok?

---

### Post by valucha on 2008-09-07
[COLOR="DarkOrchid"]COn KDESUDO tampoco hay caso...
LO que principalmente quiero hacer es abrir algun gestor de archivos con sudo, Porque tengo cosas que eliminar y que pegar en lugares donde requiere privilegios de root.[/COLOR]

---

### Post by Hei Ku on 2008-09-07
Desconozco si cambio el nombre de konqueror en KDE4, aunque por algunas cosas que estuve viendo, puede que sí.

Que pasa si tratas de arrancar konqueror desde la consola? arranca normalmente?

---

### Post by valucha on 2008-09-07
[COLOR="DarkOrchid"]SI pongo Konqueror o DOlphin solo en la terminal aparecen sin problemas[/COLOR]

---

### Post by sergiom99 on 2008-09-07
recien probé 'sudo dolphin' y lo abrió sin problemas.

---

### Post by valucha on 2008-09-07
[COLOR="DarkOrchid"]Sudo Dolphin me sigue diciendo "command not found"...
NO me faltara instalar algo?...
sudo apt-get instal command? jajaja[/COLOR]

---

### Post by sergiom99 on 2008-09-07
dolphin con minuscula no?

---

### Post by WanderingKnight on 2008-09-08
Tenés mal seteadas las variables de bash. De alguna forma el usuario root no está yendo a buscar los ejecutables a /usr/bin.

Probá haciendo sudo /usr/bin/konqueror a ver qué pasa.

---

### Post by fgl82 on 2008-09-08
> **valucha said:**
> [COLOR=DarkOrchid]Hola!!
Vengo con algo que según creo que un bug o algo que me anda funcionando mal en la máquina.

En resumidas cuentas: no puedo o no sé abrir nada con permisos de root. Está bien que recién empiezo con KDE, pero vamos! no puede ser tan complicado... BUsqué por internet y descubrí que, a diferencia de gnome, hay que usar sudo para la shell y kdesu para los programas graficos. Ponga lo que ponga me salta una ventanita externa a la temrinal y me dice "command not found".

¿Se hace de otra forma o es algún error?.

Si de algo sirve tengo Kubuntu con KDE 4.1 recien recien instaladito hoy sin tocarle nada.


Gracias desde ya :)[/COLOR]

sugerencia quizá descarriada pero bueh: ¿No será que tu usuario no está en el grupo necesario para poder ejecutar los comandos del directorio bin?

---

### Post by valucha on 2008-09-08
> **WanderingKnight said:**
> Tenés mal seteadas las variables de bash. De alguna forma el usuario root no está yendo a buscar los ejecutables a /usr/bin.

Probá haciendo sudo /usr/bin/konqueror a ver qué pasa.

[COLOR="DarkOrchid"]Tampoco, me sigue diciendo sudo: /usr/bin/konqueror: command not found

Probé Konqueror, konqueror, Dolphin, dolphin, todas las variables...Pero he notado que si abro algun programa, por ejemplo sudo firefox, si me lo toma.

El usuario mio es el único,y el predeterminado que te pone Kubuntu con la instalación gráfica. Solo llené mis datos, el nombre de usuario y la contraseña cuando pertinentemente me lo pidio en la instalación.
[/COLOR]

---

### Post by fgl82 on 2008-09-08
Estoy leyendo varias páginas que nombran problemas con sudo y KDE 4 (yo uso el 3 todavía...)

edit: postee boludeces!!!!

igual sigo buscando, me intriga mucho el problema y tengo tiempo al dope!

update: encontré esto [https://bugs.launchpad.net/ubuntu/+bug/208054](https://bugs.launchpad.net/ubuntu/+bug/208054),

---

### Post by WanderingKnight on 2008-09-08
De todas formas parece ser un tema de permisos segun lo que veo. Al parecer no están seteados como ejecutables? El tema de permisos de ejecución es por usuario?

En el reporte de bug ese te dicen que con un chmod +x archivo se soluciona... es raro eso. Cualquier otro comando con sudo anda?

---

### Post by valucha on 2008-09-08
> **fgl82 said:**
> Estoy leyendo varias páginas que nombran problemas con sudo y KDE 4 (yo uso el 3 todavía...)

edit: postee boludeces!!!!

igual sigo buscando, me intriga mucho el problema y tengo tiempo al dope!

update: encontré esto [https://bugs.launchpad.net/ubuntu/+bug/208054](https://bugs.launchpad.net/ubuntu/+bug/208054),

[COLOR="DarkOrchid"]Bueno, inicialmente puedo iniciar Konqueror con permisos de root mediante el siguiente comando 
sudo /usr/lib/kde4/bin/konqueror

Le doy un casi solved?[/COLOR]

---

### Post by Hei Ku on 2008-09-08
entonces es un tema de path del usuario root

Alguien sabe como editar el path del bash?

---

### Post by WanderingKnight on 2008-09-09
Pero es raro... el archivo /usr/bin/konqueror, al menos en KDE 3, existe, y si con sudo no lo deja usar...

Fijate haciendo un ls /usr/bin | grep konqueror a ver si en KDE 4 esta ahi.

---

### Post by fgl82 on 2008-09-09
> **WanderingKnight said:**
> Pero es raro... el archivo /usr/bin/konqueror, al menos en KDE 3, existe, y si con sudo no lo deja usar...

Fijate haciendo un ls /usr/bin | grep konqueror a ver si en KDE 4 esta ahi.

[COLOR=Black]pero ella lo encontró en [/COLOR][COLOR=Black]/usr/lib/kde4/bin/konqueror según lo que puso arriba... :S[/COLOR]

---

### Post by valucha on 2008-09-09
[COLOR="DarkOrchid"]ABrirlo ya lo puedo abrir de esa forma... Eventualmente quedará así, es un bug reportado, ya se corregirá.[/COLOR]

---

### Post by pablo atheist on 2008-09-09
a mi me pasa exactamente lo mismo, en un kubuntu con kde 4.1 que tengo en el virtualbox, todavía parece tener muchos bugs el kde 4.1

---

### Post by leo_rockway on 2008-09-09
> **pablo atheist said:**
> a mi me pasa exactamente lo mismo, en un kubuntu con kde 4.1 que tengo en el virtualbox, todavía parece tener muchos bugs el kde 4.1

Más allá de que KDE4 todavía no esté completo, este bug suena a problema de Kubuntu y no de KDE.

---

