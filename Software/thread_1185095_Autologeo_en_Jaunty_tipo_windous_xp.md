---
title: "Autologeo en Jaunty tipo windous xp"
date: 2009-06-11
forum: Software
---

### Post by nopersona on 2009-06-11
Bueno, mi primer tema en la casa nueva :p La cosa es que desde feisty vengo usando esta modificación (gracias a Denis!), ya que mantengo una sesión de invitado para que mi madre pueda realizar sus actividades. Pero la cosa es que como uso face browser en el GDM (simplemente porque me parece más bonito!) la idea de tener que escribir nombre de usuario y contraseña cada vez que se quiere usar el pc, para mi madre, es algo medieval. 

Lo que haremos será modificar unos parámetros para que el o los usuarios que definamos simplemente pinchen su nombre o su foto en el GDM para logearse, muy al estilo windous xp. 

Primero creamos el usuario, en este caso invitado, le asignamos una contraseña manualmente y le otorgamos los permisos que creamos necesarios. En el nombre de usuario y en el nombre real conviene usar el mismo para no confundir los items. 

[ATTACH]117283[/ATTACH] [ATTACH]117284[/ATTACH]


Ahra editamos el archivo que permite hacer este autologeo:

```
sudo gedit /etc/pam.d/gdm
``` Borramos su contenido y lo dejamos así:

```

#%PAM-1.0
auth requisite pam_nologin.so
auth required pam_env.so

# La siguiente linea permite tener una lista de usuarios sin contrasena en GDM:
auth sufficient pam_listfile.so item=user sense=allow file=/etc/gdm/nopassusers.txt onerr=fail

@include common-auth
@include common-account
session required pam_limits.so
@include common-session
@include common-password
```La antigua ruta para guardar el archivo nopassusers.txt  era  /etc/X11/gdm ya que allí se alojaba la configuración del GDM. Desde gutsy o hardy, no recuerdo bien, esta ruta cambió a /etc/gdm/, detalle importante a la hora de realizar esta configuración. 

Finalmente agregamos el nombre de usuario al archivo, uno por linea.

```
sudo gedit /etc/gdm/nopassusers.txt
```[ATTACH]117285[/ATTACH]

Los usuarios que no aparezcan en esta lista sí deberan escribir su contraseña para logearse. Espero que les sirva tanto como a mí. Si alguien conoce otro método más "moderno" para realizar la misma función, bienvenido sea ;) 

Saludos a todos!

---

### Post by Patriciologico on 2009-06-14
Muy bueno, se agradece. Hace un tiempo trate de hacerlo y no di como.

Saludos

---

### Post by nopersona on 2009-06-14
Sí, estos pequeños ajustes son los que a veces marcan la diferencia definitiva entre usar o no usar un sistema distinto :p

---

### Post by Patriciologico on 2009-07-14
[**Post de la Semana**]("http://ubuntuforums.org/showthread.php?t=1176055"): [14 de julio]("http://ubuntucl.wordpress.com/2009/07/14/autologueo-en-jaunty-tipo-windows-xp/") de 2009

---

### Post by rubioo on 2009-08-09
No entiendo como hacerlo :S

 Mi gdm
 > #%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session required        pam_limits.so
@include common-session
session optional        pam_gnome_keyring.so auto_start
@include common-password

 Y no tengo el archivo nopassusers.txt, lo creo y pongo los usuarios?

         Saludos

---

### Post by nopersona on 2009-08-10
> **rubioo said:**
> No entiendo como hacerlo :S

 Mi gdm
 

 Y no tengo el archivo nopassusers.txt, lo creo y pongo los usuarios?

         Saludos

Por seguridad hace un backup del archivo, luego lo borras y copias el contenido que sale en el post. El archivo nopassusers.txt efectivamente no existe, ya que es dónde se almacena el nombre de usuario que le estamos indicando al gdm, podría tener el nombre que quisieras.

Alguna otra duda? :P

---

### Post by rubioo on 2009-08-11
Ahora lo pruebo, cualquier cosa pregunto nuevamente :)

 Gracias

---

### Post by rubioo on 2009-08-12
Funciona :D
 Aunque tengo que escribir el nombre de usuario.

---

### Post by nopersona on 2009-08-12
> **rubioo said:**
> Funciona :D
 Aunque tengo que escribir el nombre de usuario.

Estás usando GDM con user list? si es así, basta con pinchar el nombre de usuario.

---

### Post by rubioo on 2009-08-13
Estoy usando el tema GDM [New Wave]("http://www.gnome-look.org/content/show.php/New+Wave+GDM?content=87370")

---

### Post by nopersona on 2009-08-13
> **rubioo said:**
> Estoy usando el tema GDM [New Wave]("http://www.gnome-look.org/content/show.php/New+Wave+GDM?content=87370")

Por ello necesitas un GDM con user list, [te dejo uno de los que diseñé]("http://www.gnome-look.org/content/show.php/Paranoid+GDM?content=87826"), hay muchos más :P

---

### Post by rubioo on 2009-08-13
Gracias!!

 PD: como se si el tema GDM es con user list?

---

### Post by nopersona on 2009-08-13
> **rubioo said:**
> PD: como se si el tema GDM es con user list?

Como su nombre lo dice, tiene una lista de usuarios visible, mejor conocida como face browser, que los GDM comúnes no tienen.

---

### Post by rubioo on 2009-08-14
Gracias por la ayuda nopersona :)

---

### Post by ManiacMagee on 2009-11-23
Gracias nopersona! Las instrucciones estan super claras.  Me salio al tiro.

---

