---
title: "Loguearse como su"
date: 2009-09-07
forum: Software
---

### Post by Applelnx on 2009-09-07
Hola, necesitaba loguearme con su.
En la consola pongo

```
su
```

me pide contraseña, y pongo la de mi usuario (es la unica que defini desde que instale Kubuntu 9.04). Que contraseña se usa o de donde se cambia en el Kubuntu?

Saludos

---

### Post by Mauro22 on 2009-09-07
Con 

```
sudo su

```

deberia alacanzarte, si le queres poner contraseña (no recomendado)

```
sudo passwd root
```

---

### Post by guisheca on 2009-09-07
El usuario root viene desactivado por defecto en ubuntu, por cuestiones de seguridad. En su lugar es conveniente usar sudo.

Que es lo que necesitas hacer?

Si de todas formas queres activar el usuario root [acá hay una guía]("http://maximoperez.com/blog/archivos/336/activar-cuenta-root-en-ubuntu/").

Mucho cuidado nomás.

Saludos.

---

### Post by Applelnx on 2009-09-07
Para desinstalar el America's Army ([http://ubuntuforums.org/showthread.php?t=235395&page=2](http://ubuntuforums.org/showthread.php?t=235395&page=2)), necesitaba si o si loguearme como su, porque si no, me decia que no tenia permisos. Me funciono el "sudo su". Muchas gracias a todos ;)

---

### Post by z37a on 2009-09-07
> **Applelnx said:**
> Para desinstalar el America's Army ([http://ubuntuforums.org/showthread.php?t=235395&page=2](http://ubuntuforums.org/showthread.php?t=235395&page=2)), necesitaba si o si loguearme como su, porque si no, me decia que no tenia permisos. Me funciono el "sudo su". Muchas gracias a todos ;)

tambien podes hacer sudo -s para poder abrir una instancia de bash como root(lo que haria el su)

---

