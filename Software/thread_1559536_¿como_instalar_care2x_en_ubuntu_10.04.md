---
title: "¿como instalar care2x en ubuntu 10.04?"
date: 2010-08-23
forum: Software
---

### Post by kahn$ on 2010-08-23
hola a todos! primera visita y consulta al for y usuario novel de ubuntu 10.04.

 Les comento mi drama: estoy tratando de hacer correr el prog. **care2x**, que está enfocado al sector salud, como una alternativa para el manejo de una farmacia intrahospitalaria, de la cual la municipalidad de mi comuna se ha hecho cargo, y de la cual no hay ningun medio automatizado para su control, pues actualmente solo se registran en planillas "a mano". El problema es el siguiente: he instalado el servidor LAMP, otorgado los permisos en el localhost como se ve en la salida del comando **ls -l**:

kahn@genghis:/var$ ls -l
total 48
drwxrwxrwx  2 root     root     4096 2010-08-23 10:38 backups
drwxrwxrwx 19 root     root     4096 2010-08-23 14:43 cache
drwxrwxrwx  2 root     root     4096 2010-04-13 16:52 crash
drwxrwxrwx  2 root     root     4096 2010-04-29 08:26 games
drwxrwxrwx 64 root     root     4096 2010-08-23 14:43 lib
drwxrwsrwx  2 root     staff    4096 2010-04-23 06:11 local
drwxrwxrwt  3 root     root       60 2010-08-23 16:28 lock
drwxrwxrwx 17 root     root     4096 2010-08-23 16:28 log
drwxrwsrwx  2 root     mail     4096 2010-04-29 08:17 mail
drwxrwxrwx  2 root     root     4096 2010-04-29 08:17 opt
drwxr-xr-x 16 root     root      600 2010-08-23 16:28 run
drwxrwxrwx  7 root     root     4096 2010-04-29 08:22 spool
drwxrwxrwx  2 root     root     4096 2010-08-23 16:37 tmp
**[COLOR=Red]drwxrwxrwx  4 www-data www-data 4096 2010-08-23 16:24 www[/COLOR]**
kahn@genghis:/var$ 
 
He seguido un tutorial que he encontrado en la pag: [http://blog.mogaal.com/?p=80](http://blog.mogaal.com/?p=80) y las recomendaciones que ahi se especifican salvo por las versiones del php, apache y mysql, ya que no estaban disponibles en los repos de ubuntu Haciendo todo esto, lo unico que he logrado es este mensajito :[http://a.imageshack.us/img716/4697/errorcare2x.png](http://a.imageshack.us/img716/4697/errorcare2x.png)

algun consejo?

pd:no me crucifiquen por el theme, asi es mas facil que se adapten al software libre ;)

---

### Post by elgaelo on 2011-01-16
Sigues con el problema?

Saludos

---

