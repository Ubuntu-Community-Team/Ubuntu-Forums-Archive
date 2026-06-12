---
title: "Problema Ubuntu One"
date: 2009-11-05
forum: Software
---

### Post by juancho_777 on 2009-11-05
Hola! que tal!

les comento mi problema, yo tengo Kubuntu 9.10, "Ubuntu One" no viene por defecto, asi que lo instale desde el "Software Center" (el cual tampoco viene por defecto, pero previamente lo habia instalado por terminal)... mi problema es el siguiente, cuando ejecuto el cliente de Ubuntu One, se abre, todo normal supuestamente, hasta que uno intenta conectarse... click izquierdo sobre el ícono da la opción para conectarse, pero al hacer click sobre "conectar" no pasa nada... absolutamente nada.
tampoco tengo la opcion en los menus contextuales, para compartir archivo en Ubuntu One al hacer click derecho sobre un archivo o carpeta.

alguien tiene alguna idea? o le paso lo mismo?

Gracias!!!

---

### Post by santiagoward2000 on 2009-11-05
> **juancho_777 said:**
> Hola! que tal!

les comento mi problema, yo tengo Kubuntu 9.10, "Ubuntu One" no viene por defecto, asi que lo instale desde el "Software Center" (el cual tampoco viene por defecto, pero previamente lo habia instalado por terminal)... mi problema es el siguiente, cuando ejecuto el cliente de Ubuntu One, se abre, todo normal supuestamente, hasta que uno intenta conectarse... click izquierdo sobre el ícono da la opción para conectarse, pero al hacer click sobre "conectar" no pasa nada... absolutamente nada.
tampoco tengo la opcion en los menus contextuales, para compartir archivo en Ubuntu One al hacer click derecho sobre un archivo o carpeta.

alguien tiene alguna idea? o le paso lo mismo?

Gracias!!!

Hola!
Para conectarte tenés que autorizar tu máquina. Para eso, podés instalar **ubuntuone-client-tools** y después en una terminal ponés:
```
u1sync --authorize
```
Esto tendría que abrir tu navegador por defecto en la página de Ubuntu One y te pediría loguearte con tu cuenta de Launchpad.
Igual tengo que avisar que tengo una duda con esto en KDE. Para autentificarte la máquina, tu contraseña se guarda en gnome-keyring. No sé si te lo instala como una dependencia o tenés que instalarlo manualmente.
Saludos y suerte!

---

### Post by juancho_777 on 2009-11-05
Hola! gracias por la respuesta....
el paquete ubuntuone-client-tools lo tengo instalado, el gnome-keyring lo instale manualmente y cuando intento autorizar mi maquina por terminal como me indicastes, me muestra esto y no hace nada mas... y tampoco me deja conectarme con Ubuntu One.

```
juancho_777@juancho777:~$ u1sync --authorize
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/main.py", line 462, in main
    do_main(argv=argv)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/main.py", line 454, in do_main
    reactor.run(installSignalHandlers=False)
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 185, in run
    self.__run()
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 225, in simulate
    self.runUntilCurrent()
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/internet/base.py", line 729, in runUntilCurrent
    f(*a, **kw)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/client.py", line 73, in wrapper
    ent = func(*arg, **kwargs)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/client.py", line 295, in _obtain_token
    oauth_client.clear_token()
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 166, in clear_token
    items = self._get_keyring_items()
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 138, in _get_keyring_items
    self.consumer.key})
gnomekeyring.NoKeyringDaemonError:

```

Aclaro que entrando en la pagina de Ubuntu One, y logeandome con mis datos de launchpad puedo cargar archivos, pero desde el navegador... lo que no me funciona es el cliente de Ubuntu One.


Gracias de todas maneras!

---

### Post by Mauro22 on 2009-11-05
```

gnomekeyring.NoKeyringDaemonError:

```


Eso es lo unico que me llama la atencion, si bien instalaste el keyring de Gnome, éste no está corriendo como demonio.

---

### Post by juancarlospaco on 2009-11-05
Creo que vas a necesitar instalar aunque sea lo basico del desktop gnome,
tal vez con gnome-core y dependencias.

---

### Post by santiagoward2000 on 2009-11-05
¿No hará falta que inicie **gnome-keyring?** ¿Con ```
gnome-keyring-daemon --start
``` tal vez?
Saludos!

_EDIT:_
Estoy acá probando en un LiveCD de Kubuntu. Instalé:
[LIST]
[*]ubuntuone-client
[*]ubuntuone-client-tools
[*]ubuntuone-client-gnome
[*]gnome-keyring
[*]y todas las dependencias
[/LIST]

Abrí **Ubuntu One** desde el menú. Ahí se abrió el Konqueror para que lo autentique y automáticamente saltó el **gnome-keyring**. Le agregué una contraseña y se conectó sin ningún problema. Ni siquiera tuve que cargar gnome-keyring, lo hizo solo. Raro...

---

### Post by juancho_777 on 2009-11-06
acabo de encender la notebook, y me aparecio el keyring pidiendome la contraseña, la puse, y el Ubuntu One intentó conectarse y al instante apareció la crucecita roja indicando que esta desconectado...
se me acaban las ideas... entrando desde el navegador al sitio de Ubuntu One, me puedo logear perfectamente.

---

### Post by santiagoward2000 on 2009-11-06
> **juancho_777 said:**
> acabo de encender la notebook, y me aparecio el keyring pidiendome la contraseña, la puse, y el Ubuntu One intentó conectarse y al instante apareció la crucecita roja indicando que esta desconectado...
se me acaban las ideas... entrando desde el navegador al sitio de Ubuntu One, me puedo logear perfectamente.

¿Podés probar correr de nuevo **u1sync --authorize** a ver si te tira algún error?
Saludos!

---

### Post by juancho_777 on 2009-11-06
Santiago, cuando corrí denuevo **u1sync --authorize **me saltó una ventanita pidiendome que permita el acceso al keyring, lo permití y me abrió firefox con la pagina de Ubuntu One confirmando asociar mi maquina a la cuenta, le di ok, y esta todo bien, desde el navegador.
pero al ejecutar el applet desde el menu, me aparece la misma ventanita que antes pidiendome permiso para acceder a keyring, le doy permiso, y no pasa naranja hago click sobre el icono en la barra de sistema y pongo "connect" e intenta conectarse y al instante vuelve a aparecer la cruz indicando que está desconectado =(

---

### Post by guillermolisi on 2009-11-06
En una epoca Ubuntu One funcionaba con el Network Manager de Ubuntu pero no con la implementacion del mismo en Kubuntu. Si las cosas no cambiaron, seria una de las razones de por que U1 viene con Ubuntu y no con Kubuntu (que hasta ahora no logra que el NM funcione igual que en Ubuntu).

---

### Post by juancho_777 on 2009-11-06
bueno gente, muchas gracias igual por la ayuda, creo qe por ahora lo usare solamente mediante navegador, subiendo y bajando los archivos.

---

### Post by santiagoward2000 on 2009-11-06
> **guillermolisi said:**
> En una epoca Ubuntu One funcionaba con el Network Manager de Ubuntu pero no con la implementacion del miso en Kubuntu. Si las cosas no cambiaron, seria una de las razones de por que U1 viene con Ubuntu y no con Kubuntu (que hasta ahora no logra que el NM funcione igual que en Ubuntu).

Me parece que eso sí cambió. Yo por lo menos lo pude usar bien en el LiveCD de Kubuntu.

---

### Post by dox_drum on 2009-11-06
Hola, no se si esto te ayude, pero cuando instale Karmic me decia que U1 tenia un problema de coneccion, ademas una actualizacion de u1-core, etc... no funcionaban.

Lo que hice fue cambiar el repository to main (y no el local), y todo funciono perfecto. Ojo, estoy en Gnome.

Saludos.

---

### Post by carlosli on 2009-11-18
Bueno yo también tengo problemas con el Ubuntu One, lo llego a instalar sin problemas, conecta si problemas pero no acutaliza automaticamente los archivos de la máquina al sitio en la web, pese a que he instalado y desintalado dos veces. Seriamente estoy considerando regresar al Dropbox ¿alguna sugerencia?

---

### Post by santiagoward2000 on 2009-11-28
Hola gente!
Anoche estuve dando vueltas y encontré esto: [https://launchpad.net/~apachelogger/+archive/ubuntuone-kde]("https://launchpad.net/~apachelogger/+archive/ubuntuone-kde")
Parece que alguien empezó a trabajar en una versión de Ubuntu One Client para KDE.
Lo estoy probando ahora en el LiveCD y hasta ahora anda bien. Sigue dependiendo de muchas cosas de GNOME, pero cuando lo instalás resuelve las dependencias que el otro no (como gnome-keyring).
Se corre con:
```
ubuntuone-client-kde
``` (no aparece en el menú, el que está es la versión GTK).
Tal vez tengan más suerte con este.
Saludos!

---

