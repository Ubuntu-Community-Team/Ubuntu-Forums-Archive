---
title: "Auxilio - Destroce Ubuntu - Ayuda para backupear files"
date: 2009-10-31
forum: Software
---

### Post by sitiomatic on 2009-10-31
Hola, yo estaba muy contento con mi jaunty y andaba super.
Ayer actualice algo y compiz dejo de andar, toque aqui y alla y como no puede arreglarlo, decidi hacer el updgrade a karmic.
Bue, la actualizacion aborto por demasiados errores asi que me queda format e instalar de cero. Ahora Ubuntu no arranca.
Usando el live cd, quiero copiar archivos de mi /home a un disco usb pero no me deja copiar algunas carpetas porque dice que no tengo permisos.
Alquien me diria como hacer?
Gracias, y prometo no volver a decir que no voy a actualizar [-X
Edit: ya le encontre la vuelta con gksudo nautilus .... grazzie mile

---

### Post by granjero on 2009-10-31
creo que para que no te moleste con los permisos deberías hacer desde una terminal en el live cd

```
sudo nautilus
```así te abre nautilus como superusuario y no te molesta con los permisos....

eso sí después que instales KK vas a tener que arreglar los permisos de tus archivos con *chmod* y *chown* comandos que no termino de entender...

si estoy diciendo gansadas avisen por favor!

salud!

---

### Post by guillermolisi on 2009-10-31
> **granjero said:**
> creo que para que no te moleste con los permisos deberías hacer desde una terminal en el live cd

```
sudo nautilus
```así te abre nautilus como superusuario y no te molesta con los permisos....

eso sí después que instales KK vas a tener que arreglar los permisos de tus archivos con *chmod* y *chown* comandos que no termino de entender...

si estoy diciendo gansadas avisen por favor!

salud!
Es que para acceder al disco rigido debera montarlo y posiblemente deba echar mano a chroot para evitar que el esquema de permisos de acceso a los archivos resulte perjudicial para lo que se quiere hacer (tener una copia fiel y completa de todos los archivos).

---

### Post by anarko on 2009-10-31
Por si no insalaste todabia es 100% recomendable un minimo de 2 particiones "/" y "/home" porque en estos casos se hace muchisimo muy facil no perder nada, ya que levantas con un live CD montas el /home renombras la carpeta de tu usuario y haces una instalacion limpia, luego recuperas lo que te plazca y borras lo que sobre.

---

### Post by sitiomatic on 2009-10-31
Gracias por los consejos.
No se que paso ayer, solo instale la nueva version de ubuntu-tweak y al final decia que si ya lo tenia instalado hiciera apt-get upgrade y eso hice........pero sin leer lo que decia, creo que metio otras cosas y ahi sono gnome.
Bue, salve todo, las bases de mysql, los sitios que tenia en apache, el windows que tenia en Vbox y los programas que corrian con wine ....perdi todo el sabado instalando y configurando pero ya esta, solo me queda pelear un rato con conky para dejarlo como estaba. (me olvide de copiar eso y los bookmarks de FFox)
Al tipo que invento el Live CD hay que darle un nobel al menos :)

---

### Post by pablo.s on 2009-10-31
> **sitiomatic said:**
> Al tipo que invento el Live CD hay que darle un nobel al menos :)

Mandale un correo electrónico
a [email]info@knopper.net[/email].
En inglès o en alemàn.
Lo va a apreciar mucho.

---

### Post by sitiomatic on 2009-11-01
Ahhhhhhhh....es el tipo que hizo knoppix!!.Ese fue el primer Live CD que tuve y me salvo la vida montones de veces, no sabia el origen.
Gracias por el dato, ya le escribi.

---

### Post by anarko on 2009-11-01
Un groxo el knoppix.
Pa la proxima, proba el plugin de FF que se llama FoxMarks o algo asi ter guarda los bookmarks en una base de datos de ellos y los podes recuperar desde cualquier FF con el plugin instalado, es una cosa menos para preocuparse de backupear.

---

