---
title: "Agregar ppa/repositorio no funciona con proxy?"
date: 2010-09-16
forum: Software
---

### Post by kabeza on 2010-09-16
Buenas
En un hilo anterior fui aconsejado de instalar los ppa de cierta forma, 

[URL="http://ubuntuforums.org/showthread.php?t=1575139"]http:
//ubuntuforums.org/showthread.php?t=1575139[/URL]

...y resulta que he probado agregar un ppa desde la terminal, pero me esta dando problemas. Tengo un proxy asignado en preferencias, pero no se porque en la terminal no funciona... alguna idea? Sera el **HTTPS**?

[[IMG]http://img20.imageshack.us/img20/1096/screenshot007ne.th.jpg[/IMG]](http://img20.imageshack.us/i/screenshot007ne.jpg/)

Gracias

---

### Post by guillermolisi on 2010-09-16
Decididamente tenes algun problema de ruteo/bloqueo ya que pude acceder y ver el contenido del repositorio sin ningun tipo de error.

Cuando hablas de proxy, sabes como esta configurado ?

Si no es un proxy transparente (como creo que esta en tu caso), que ports utiliza para acceder e intercambiar con Internet ?

Requiere de usuario y clave para accederlo/usarlo ?

Ademas de proxy, filtra sitios/IPs publicas (como lo que se hace con Squid, por ejemplo) ?

Podes acceder a Launchpad con el navegador web sin problemas ?

Segun sean las respuestas sera la solucion del caso.

---

### Post by kabeza on 2010-09-16
Hola Guille

1. ni idea como esta configurado el proxy. Son alrededor de 800 clientes divididos en 5 pisos

2. el proxy esta como figura a continuacion

[[IMG]http://img186.imageshack.us/img186/8256/screenshot008kh.th.jpg[/IMG]](http://img186.imageshack.us/i/screenshot008kh.jpg/)

[[IMG]http://img534.imageshack.us/img534/4493/screenshot009x.th.jpg[/IMG]](http://img534.imageshack.us/i/screenshot009x.jpg/)

3. No requiere de user/pass para usarlo

4. Si, esta todo bloqueado: taringa, twitter, facebook, p0rn, etc

5. Si, puedo entrar a launchpad.net sin problemas

---

### Post by guillermolisi on 2010-09-16
> **kabeza said:**
> 
5. Si, puedo entrar a launchpad.net sin problemas

Bien, entonces proba de ir a la URL del repo, la completa que te devuelve el error (no la direccion condensada) con el navegador.
Deberias ver lo siguiente:
> commercial
False
dependencies_collection_link
[https://launchpad.net/api/1.0/~nilarimogard/+archive/webupd8/dependencies](https://launchpad.net/api/1.0/~nilarimogard/+archive/webupd8/dependencies)
description
PPA maintained by Web Upd8: [http://www.webupd8.org/](http://www.webupd8.org/) To add this PPA, simply paste this in a terminal (Ubuntu Karmic +): sudo add-apt-repository ppa:nilarimogard/webupd8
displayname
WebUpd8
distribution_link
[https://launchpad.net/api/1.0/ubuntu](https://launchpad.net/api/1.0/ubuntu)
http_etag
"da39a3ee5e6b4b0d3255bfef95601890afd80709-107aee6462e6a6e85b8b0d48dd431ce618872b35"
name
webupd8
owner_link
[https://launchpad.net/api/1.0/~nilarimogard](https://launchpad.net/api/1.0/~nilarimogard)
private
False
require_virtualized
True
resource_type_link
[https://launchpad.net/api/1.0/#archive](https://launchpad.net/api/1.0/#archive)
self_link
[https://launchpad.net/api/1.0/~nilarimogard/+archive/webupd8](https://launchpad.net/api/1.0/~nilarimogard/+archive/webupd8)
signing_key_fingerprint
1DB29AFFF6C70907B57AA31F531EE72F4C9D234C

Si verificas que podes acceder a este contenido, entonces solo tenes que revisar si Synaptic esta utilizando el proxy que tenes configurado en esa maquina.

Conta como resulta.

---

### Post by kabeza on 2010-09-17
Hola Guille
Perdon por la tardanza en la rta. pero solo estoy por las mañanas aca

Si, confirmo lo que pusiste en tu ultimo mensaje. Al ingresar la url en el browser veo toda la info:

[[IMG]http://img697.imageshack.us/img697/3855/screenshot010i.th.jpg[/IMG]](http://img697.imageshack.us/i/screenshot010i.jpg/)

Esto quiere decir que debo configurar algo mas? O como lo puedo solucionar?

Gracias nuevamente

---

### Post by guillermolisi on 2010-09-17
Quiere decir que no habria impedimento alguno para que accedas al repositorio.

En funcion de lo que comentaste en el thread anterior, sobre como aplicaste repositorios y sus claves, sugiero que reveas esto aplicando los repositorios adicionales con el metodo sugerido, asi tambien ingresan correctamente sus certificados digitales, y despues volver a probar.

Es todo un retrabajo pero es una sola vez y te aseguras que cuando actualices a la nueva version no tengas mas problemas como estos.

Si aun asi continuas con problemas, seria importante ver el contenido de los archivos que forman parte de la estructura de datos para apt.

---

### Post by kabeza on 2010-09-17
> **guillermolisi said:**
> Quiere decir que no habria impedimento alguno para que accedas al repositorio.

pero debo configurar algo aparte para que no me de el error en la terminal? no tengo ni la menor idea de como hacerlo funcar

> **guillermolisi said:**
> 
En funcion de lo que comentaste en el thread anterior, sobre como aplicaste repositorios y sus claves, sugiero que reveas esto aplicando los repositorios adicionales con el metodo sugerido, asi tambien ingresan correctamente sus certificados digitales, y despues volver a probar.


buscando y buscando, encontre un .sh llamado DebCleaner, que supuestamente te limpia todas esas cosas, pero bue, creo que sigue igual
[http://ubuntulife.wordpress.com/2010/09/11/debcleaner-script-para-limpiar-el-sistema/](http://ubuntulife.wordpress.com/2010/09/11/debcleaner-script-para-limpiar-el-sistema/)

> **guillermolisi said:**
> 
Si aun asi continuas con problemas, seria importante ver el contenido de los archivos que forman parte de la estructura de datos para apt.

Esos 3 paquetes (del hilo anterior) que me siguen dando k*****o y que hacen que me salga lo de "Actualizacion parcial", etc. tengo que removerlos de synaptic y volverlos a instalar una vez que solucione lo del k*****o de la terminal y https?

Gracias

---

### Post by guillermolisi on 2010-09-17
Yo los removeria a mano con Synaptics, simple y controlable, anotando que borras de los repos para luego reincorporarlos correctamente.

Hasta aqui no veo razon para configurar algo en especial ni problemas con https o la terminal.

---

### Post by kabeza on 2010-09-17
> **guillermolisi said:**
> Hasta aqui no veo razon para configurar algo en especial ni problemas con https o la terminal.

perdona que insista, entonces porque me tira ese error en la terminal y por el browser puedo verlo correctamente?

Gracias por la paciencia/ayuda

---

### Post by guillermolisi on 2010-09-18
Puede ser que en tu lista de repositorios algo este "molestando" a raiz de como los incorporaste y cuando quiere agregar ese salta con un error.

No se me ocurre otra cosa porque sino no podrias llegar a verlo con el navegador.

Por las dudas probe en una de mis maquinas y el resultado fue exitoso:

> guille@guillermo:~$ sudo add-apt-repository ppa:nilarimogard/webupd8
[sudo] password for guille: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 1DB29AFFF6C70907B57AA31F531EE72F4C9D234C
gpg: requesting key 4C9D234C from hkp server keyserver.ubuntu.com
gpg: key 4C9D234C: public key "Launchpad webupd8" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
guille@guillermo:~$ 


---

