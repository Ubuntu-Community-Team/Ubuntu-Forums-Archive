---
title: "Ubuntu 8.04 LTS (actualizaciones)"
date: 2008-10-04
forum: Software
---

### Post by rokimoki on 2008-10-04
Cuando intento actualizar me sale esto:

```
alejandro@Al3X:~$ sudo apt-get update
Obj http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-es
Ign http://security.ubuntu.com hardy-security/restricted Translation-es
Ign http://security.ubuntu.com hardy-security/universe Translation-es
Ign http://security.ubuntu.com hardy-security/multiverse Translation-es
Obj http://security.ubuntu.com hardy-security Release   
Obj http://security.ubuntu.com hardy-security/main Packages                  
Obj http://security.ubuntu.com hardy-security/restricted Packages
Obj http://security.ubuntu.com hardy-security/main Sources
Obj http://security.ubuntu.com hardy-security/restricted Sources
Obj http://security.ubuntu.com hardy-security/universe Packages
Obj http://security.ubuntu.com hardy-security/universe Sources
Obj http://security.ubuntu.com hardy-security/multiverse Packages              
Obj http://security.ubuntu.com hardy-security/multiverse Sources               
Err http://es.archive.ubuntu.com hardy Release.gpg                             
  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)
Err http://es.archive.ubuntu.com hardy/main Translation-es
  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)
Err http://es.archive.ubuntu.com hardy/restricted Translation-es
  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)
Err http://es.archive.ubuntu.com hardy/universe Translation-es
  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)
Err http://es.archive.ubuntu.com hardy/multiverse Translation-es
  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)
Err http://es.archive.ubuntu.com hardy-updates Release.gpg
  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)
Err http://es.archive.ubuntu.com hardy-updates/main Translation-es
  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)
Err http://es.archive.ubuntu.com hardy-updates/restricted Translation-es
  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)
Err http://es.archive.ubuntu.com hardy-updates/universe Translation-es
  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)
Err http://es.archive.ubuntu.com hardy-updates/multiverse Translation-es
  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)
Leyendo lista de paquetes... Hecho
W: Imposible obtener http://es.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)

W: Imposible obtener http://es.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-es.bz2  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)

W: Imposible obtener http://es.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-es.bz2  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)

W: Imposible obtener http://es.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-es.bz2  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)

W: Imposible obtener http://es.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-es.bz2  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)

W: Imposible obtener http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)

W: Imposible obtener http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-es.bz2  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)

W: Imposible obtener http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-es.bz2  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)

W: Imposible obtener http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-es.bz2  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)

W: Imposible obtener http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-es.bz2  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)

W: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas

```

---

### Post by Hei Ku on 2008-10-04
Proba de cambiar a los repositorios "en" en vez usar los "es".

---

### Post by WanderingKnight on 2008-10-04
Debe ser un problema temporal con los repositorios de España porque tampoco los puedo accesar por http, si estás acá en Argentina probá con los repositorios de Brasil que son rapidísimos, sino probá con algún otro que esté por tu zona. Para cambiar eso fijate de editar el archivo /etc/apt/sources.list:

```
sudo gedit /etc/apt/sources.list
```

...y cambiá en cada línea el "es" por el código del país de donde querés los repositorios (br para Brasil, ar para Argentina, etc).

---

### Post by sajnox on 2008-10-05
Perdon wandering, pero como ya dije las soluciones graficas no matan a nadie. Es mas te diria que para este caso por esta via es mas facil.

Para cambiar a otro repositorio podes hacer lo siguiente:

Sistema > Administracion > Origenes del Software

Elegis la opcion "Descargar Desde" Seleccionas otro y le das a "Seleccionar el mejor servidor" 

Con esa opcion pinguea a todos los servidores de Ubuntu y te elige el que tenga la conexion mas rapida en ese momento.

Igual como te dice WanderingKnight el de Brasil es el que mejor anda para Argentina.

---

### Post by WanderingKnight on 2008-10-07
Jaja, perdón, es que estoy tan acostumbrado a hacerlo así (y como honestamente me parece la manera más rápida) que ni sé cómo funciona la interfaz gráfica de selección de repositorios.

De todas formas Kubuntu por lo que puedo ver no tiene algo similar así que :/

---

### Post by Vera_ on 2008-10-09
A mi también me pasaba el mismo error al actualizar / instalar alguna aplicación. Soy de España. ¿Sabéis si ya está bien el servidor?

Por cierto, ¡hola a todos! Soy nueva por aquí, intentaré ayudar en lo que pueda. Me encanta usar Ubuntu :) . Estaba buscando un post para las presentaciones aquí y en el foro general (en inglés), y no encontré ningún post...
En fin, nos vemos por aquí. ;)

Un saludo,
Vera.

---

