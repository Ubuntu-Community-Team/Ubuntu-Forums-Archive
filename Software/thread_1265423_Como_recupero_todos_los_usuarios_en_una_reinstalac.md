---
title: "Como recupero todos los usuarios en una reinstalación del sistema?"
date: 2009-09-13
forum: Software
---

### Post by atari130xe on 2009-09-13
Gente, hice una reinstalación del sistema y no puedo recuparar los usuarios que tenia en un principio en la particion /home
Cuando voy a administrador de usuarios e ingreso los que ya estaban creados en la partición /home sale esta advertencia:

> [COLOR="Black"][SIZE="5"]El directorio personal ya existe[/SIZE][/COLOR]
Por favor seleccione una ruta para el directorio personal diferente

Siempre hice instalaciones "limpias" y esta es la primera vez que hago un formateo de "/" dejando "/home" intacta para no perder todos los datos y configuraciones (no quise hacer backups en otros soportes), alguna sugerencia?

Nota: Mi usuario (Administrador) se creo perfecto y recuperé los datos de la partición /home dentro de la misma hay 2 usuarios más que tenia creados, al intentar agregarlos es cuando me sale esa advertencia.

---

### Post by pablo.s on 2009-09-13
> **atari130xe said:**
> Gente, hice una reinstalación del sistema y no puedo recuparar los usuarios que tenia en un principio en la particion /home
Cuando voy a administrador de usuarios e ingreso los que ya estaban creados en la partición /home sale esta advertencia

A ver, es un tema sencillo y
complicado a la vez. Por una parte
es bueno conservar en el backup
dos archivos esenciales (como son
/etc/passwd y /etc/shadow) que
conservan la configuración de
claves de usuario. Por otra parte,
esto que te digo no se me hubiera
ocurrido a mi tampoco. Veamos:
Los usuarios los podés crear con
el comando 
```
sudo adduser
```
y luego con el gestor de Usuarios ver
si le podés cambiar la ruta donde se
guardan los archivos.

---

### Post by EnriqueK on 2009-09-13
Seguramente debe haber comandos de terminal que resurlven este problema , pero tamnién se puede de una forma menos elegante y para eso 
1. Abrí un terminal y ponés 
 sudo nautilus /home
con esto vas a abrir como adminstrador la carpeta /home y seguidamente renombrás todas las carpetas de los otros usuarios de una forma simple, por ejemplo si una fuera carlos, le pones carlos1 , luego de terminar de renombrar. cierras terminal.
 
2.- Ahora crea todas las cuentas de usuario , ya no vas a tener problemas por que has renombrado las carpetas, pero se van a crear nuevas carpetas de usuario que deberás eliminar y luego de esto vuelve a renombrar todas las carpetas de los otros usuarios al nombre original.

---

### Post by atari130xe on 2009-09-13
> **EnriqueK said:**
> Seguramente debe haber comandos de terminal que resurlven este problema , pero tamnién se puede de una forma menos elegante y para eso 
1. Abrí un terminal y ponés 
 sudo nautilus /home
con esto vas a abrir como adminstrador la carpeta /home y seguidamente renombrás todas las carpetas de los otros usuarios de una forma simple, por ejemplo si una fuera carlos, le pones carlos1 , luego de terminar de renombrar. cierras terminal.
 
2.- Ahora crea todas las cuentas de usuario , ya no vas a tener problemas por que has renombrado las carpetas, pero se van a crear nuevas carpetas de usuario que deberás eliminar y luego de esto vuelve a renombrar todas las carpetas de los otros usuarios al nombre original.

Solucionado, utilicé la "menos elegante" jejeje suelo modificar con sudo nautilus las cosas que pueden o no ver los otros usuarios, así qeu solucionado. gracias!

---

### Post by atari130xe on 2009-09-13
> **EnriqueK said:**
> Seguramente debe haber comandos de terminal que resurlven este problema , pero tamnién se puede de una forma menos elegante y para eso 
1. Abrí un terminal y ponés 
 sudo nautilus /home
con esto vas a abrir como adminstrador la carpeta /home y seguidamente renombrás todas las carpetas de los otros usuarios de una forma simple, por ejemplo si una fuera carlos, le pones carlos1 , luego de terminar de renombrar. cierras terminal.
 
2.- Ahora crea todas las cuentas de usuario , ya no vas a tener problemas por que has renombrado las carpetas, pero se van a crear nuevas carpetas de usuario que deberás eliminar y luego de esto vuelve a renombrar todas las carpetas de los otros usuarios al nombre original.

Solucionado, utilicé la "menos elegante" jejeje suelo modificar con sudo nautilus las cosas que pueden o no ver los otros usuarios, así que solucionado. gracias!

---

