---
title: "un consejo sobre formateo"
date: 2009-06-24
forum: Software
---

### Post by joseluis on 2009-06-24
quiero pedir un consejo sobre el sistema para formatear mi disco.
tengo en mi notebook win y ubuntu. desde ubuntu puedo trabajar con los documentos que tengo en mi particion win.
pero ahora quiero sacar definitivamente win y quedarme con linux y formatear todo el disco.
¿que me aconsejan?
que deje una particion ntfs para los documentos con los que trbajo y asi poder leerlos si voy, por ejemplo a una red y poder tener acceso a los documentos?
O que mande directamente formato ext4? tendría problemas en que otros vean mis archivos o yo mismo, si estoy desde una red, con una maquina win, para trabajar con dichos archivos

¿se entiende?

---

### Post by staar on 2009-06-25
se entiende, no te hagas problema, compartiendo alguna carpeta o archivo (mediante samba, para que windos pueda verlas), las máquinas con ese SO no van a tener problemas para manejarlos, independientemente del filesystem en que estén...

saludos

---

### Post by Mister X on 2009-06-25
si no vas a tener windows en la maquina local, no tiene sentido ntfs...

sacalo y te ahorras el problema de la fragmentacion

---

### Post by joseluis on 2009-06-25
no voy a tener win en la maquina local, la cuestión es el problema de que si estoy en una red windows otros no podrían leer los archivos de mi pc..ese es el inconveniente. Es una duda existencial. y estoy de acuerdo con que me salvo de la fragmentación, ademas, si no tuviera win y una particion ntfs, NO TENDRIA MODO DE DEFRAMENTARLO NUNCA!!!

---

### Post by EnriqueK on 2009-06-25
No tengo experiencia en redes, pero el compartir documentos entre diferentes usuarios de un mismo equipo es complejo, la solución que emplee para este caso fue el de tener una partición ntfs para que todos los usuarios puedan acceder a esos archivos, supongo que al tratarse de una red, el asunto es mas complejo.

---

### Post by staar on 2009-06-25
a ver, NO vas a tener problemas, si compartis tus archivos, otras pc con windos SI los van a poder leer y modificar, el sistema de archivos no importa en este caso...

saludos

---

### Post by Mister X on 2009-06-25
> **joseluis said:**
> no voy a tener win en la maquina local, la cuestión es el problema de que si estoy en una red windows otros no podrían leer los archivos de mi pc..ese es el inconveniente. Es una duda existencial. y estoy de acuerdo con que me salvo de la fragmentación, ademas, si no tuviera win y una particion ntfs, NO TENDRIA MODO DE DEFRAMENTARLO NUNCA!!!

la unica forma de que las maquinas remotas accedan a tu disco (y a todo tu hardware) es a traves del sistema operativo de la maquina local, a lo que voy es que cualquier maquina remota le tiene que "pedir" a tu Ubuntu mediante algun procolo, por ejemplo samba, que lea o escriba en disco y por lo tanto el unico que importa que sepa usar el disco local es el SO local

en definitiva: poné ext3 (o ext4 si querés)

---

### Post by juancarlospaco on 2009-06-25
**EXT4 y Swap**

Desde ubuntu podes trabajar con los documentos que tenes en la particion window

[I]Yo lo uso para trabajar todos los dias, 
tambien tengo una netbook con Ubuntu, 
que anda mejor que una Notebook HP de 10lucas de un amiga con Window Vista.[/I]

---

### Post by joseluis on 2009-06-25
bien..voy tamando ideas y obviamente me sirven mucho.Voy a hacer la prueba de poner archivos en la partición que tengo hasta ahora en ubuntu y ver cómo lo maneja la red de mi trabajo.
gracias!! después les cuento.,

---

### Post by joseluis on 2009-06-26
bueno..les cuento. Es así, puedo ver perfectamente mis archivos en ubuntu desde cualquier computador de la red de mi trabajo. 
Lo que hice (a ver si está bien) fue poner un archivo en Documenos, dentro de la home, y compartirlo con SAMBA. 
Ahora bien, abro un archivo .doc, por ejemplo, desde otra maquina, y no me permite modificarlo. Es decir, se abre como solo lectura. Supongo que debe tener que ver con los permisos.
¿como se los cambio?
En samba le puse en Propiedades que pueda ser visto, leido y escribrir por todos. Use el mc y le cambie los permisos a lectura y escritura por dueño y por grupo y por todos.
¿Como hago entonces?
gracas

---

