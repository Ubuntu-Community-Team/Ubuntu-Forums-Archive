---
title: "FreeNX Hardy"
date: 2008-09-16
forum: Software
---

### Post by ramiro_md on 2008-09-16
Gente necesito el freenx para hardy, encontre muchas paginas donde decia de agregar fuentes a los repositorios pero es hasta feisty. Un saludo.

---

### Post by llove on 2008-09-18
1. Editamos el sources.list:

    sudo gedit /etc/apt/sources.list

También puedes usar nano si no tienes interfaz gráfica..

    sudo nano /etc/apt/sources.list

2. Con sources.list abierto, añadimos estas dos líneas al final del todo:

    deb [http://ppa.launchpad.net/marceloshima/ubuntu](http://ppa.launchpad.net/marceloshima/ubuntu) hardy main
    deb-src [http://ppa.launchpad.net/marceloshima/ubuntu](http://ppa.launchpad.net/marceloshima/ubuntu) hardy main

3. Le damos a guardar, y ejecutamos los siguientes comandos:

    sudo apt-get update

    sudo apt-get upgrade

4. Si todo a ido bien, continuamos. Ejecutamos el siguiente comando en la consola:

    sudo apt-get install expect openssh-server nxlibs nxagent nxproxy freenx-server

5. Lo siguiente sería crear el usuario en Ubuntu, en Sistema -> Administración -> Usuarios y Grupos.

Con esto ya tendríamos el server funcionando a la perfección. Ahora para la instalación del cliente haríamos lo siguiente..:

1. Descargamos el paquete:

    wget [http://64.34.161.181/download/3.2.0/Linux/nxclient_3.2.0-9_i386.deb](http://64.34.161.181/download/3.2.0/Linux/nxclient_3.2.0-9_i386.deb)

2. Y lo instalamos:

    sudo dpkg -i nxclient_3.2.0-9_i386.deb


la info la saque de este link. [http://inf-o.no-ip.org/2008/05/18/instalar-freenx-en-ubuntu-804-hardy-heron/](http://inf-o.no-ip.org/2008/05/18/instalar-freenx-en-ubuntu-804-hardy-heron/)

ps: google no muerde amigo,jajajjaja saludos. espero te sirva

---

### Post by ramiro_md on 2008-09-18
Llove ese tuto que me indicas vos creo que aparece en la primer hoja de google si buscas "FreeNX hady", antes de postear siempre googleo ;). Remarco que no me sirve porque cuando voy a instalar los paquetes me corta en este punto:
openssh-server ya está en su versión más reciente.
fijado openssh-server como instalado manualmente.
E: No se pudo encontrar el paquete nxlibs
Gracias capo y un saludo.

---

### Post by txitxo on 2008-09-18
A mi me pasa lo mismo, lo has podido solucionar?

He estado buscando en ubuntu packages y no he encontrado nxlibs ni nxagent. Pero he encontrado otro repositorio que si los tiene. He utilizado este enlace 

[http://s230070429.mialojamiento.es/freexn-serverclient-escritorio-remoto-en-ubuntu-hardy-heron-64bits/](http://s230070429.mialojamiento.es/freexn-serverclient-escritorio-remoto-en-ubuntu-hardy-heron-64bits/)

de momento se me ha instalado todo. Ahora a probar si funciona.

---

### Post by sajnox on 2008-09-18
> **ramiro_md said:**
> Llove ese tuto que me indicas vos creo que aparece en la primer hoja de google si buscas "FreeNX hady", antes de postear siempre googleo ;).

Ramiro, no somos adivinos. Si ya probaste con algo lo recomendable es que lo comentes y cuentes en que paso te quedaste, y desde ahi el resto puede ver cual es tu problema. 

(Si bien no es para seguir al pie de la letra nunca esta de mas leer esto (1))

(1) [http://www.sindominio.net/ayuda/preguntas-inteligentes.html](http://www.sindominio.net/ayuda/preguntas-inteligentes.html)

---

### Post by ramiro_md on 2008-09-18
> **ramiro_md said:**
> encontre muchas paginas donde decia de agregar fuentes a los repositorios pero es hasta feisty. Un saludo.

Eeh ultimamente me estan dando con un caño :( xD yo dije que ya habia buscado en varias fuentes, la proxima especifico con el termino "googleando".
Por otro lado, txitxo al parecer se instalo todo ok, pero no se como ejecutar el server. Probe poner "freenx-server" en alt+F2 y de mismo modo en la consola pero nada che. Nose si le estoy errando en algo. UN saludo gente =)

PD: [http://www.sindominio.net/ayuda/preg...eligentes.html](http://www.sindominio.net/ayuda/preg...eligentes.html) excelente pagina.

---

### Post by ramiro_md on 2008-09-18
> **ramiro_md said:**
> pero no se como ejecutar el server.
Ya lo solucione =)
APlicaciones > Internet > NX CLient for Linux > NX Session Admin.
Un saludo

---

### Post by llove on 2008-09-18
amigo fue con la mejor mi comentario, sin animo de bardear,,,me alegro que lo hayas solucionado, saludos.

---

### Post by ramiro_md on 2008-09-18
> **llove said:**
> amigo fue con la mejor mi comentario, sin animo de bardear,,,me alegro que lo hayas solucionado, saludos.

Todo copado con vos amiguito jajaja re cabeza. Un saludo man =)

---

