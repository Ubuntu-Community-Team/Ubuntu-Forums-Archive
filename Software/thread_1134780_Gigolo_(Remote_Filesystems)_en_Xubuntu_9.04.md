---
title: "Gigolo (Remote Filesystems) en Xubuntu 9.04"
date: 2009-04-23
forum: Software
---

### Post by DrKenobi on 2009-04-23
Recien termino de reinstalar el nuevo Xubuntu, y una de las aplicaciones nuevas que viene instalada es el Gigolo (Applications--> System--> Remote Filesystems). Ya que el FileZilla no me lo deja instalar el "Add/Remove" voy a usar este programa para conectarme via ssh/sftp a otro ordenador.

Logre configurar todo bien (es muy simple, nada del otro mundo) y me reconoce el otro ordenador y el usuario en ese ordenador (con MacOS X 10.5). Le doy a conectar y me pide la clave, me la acepta, me muestra un icono que es el usuario de la otra pc y cuando lo quiero abrir no me da ni bola. Hago doble-click, le doy "open", etc y nada. Ni siquiera error. Nada!

Alguno lo conoce a este programa? Alguna idea?

Gracias!!

---

### Post by clasificado on 2009-04-24
Aqui por kde, el konqueror nos resuelve todos los problemas de conectividad ftp :P

¿La otra pc está en la misma red local o tenés que salir a buscarla? (firewall)

¿Probaste ejecutando el programa desde la consola? Hay veces que los errores y timeouts te los devuelve por ahi, y ejecutandolo directamente gráfico uno se lo pierde

clasificado

---

### Post by DrKenobi on 2009-04-24
Mirando el sitio del programa en cuestion, encontre lo siguiente. Si bien no es el error exacto, puede que ayude. Pero me llama la atencion que pongan este programa en el nuevo Xubuntu cuando este tiene problemas con el Thunar y xFce 4.6 que son parte de Xubuntu.

Despues pruebo cuando tenga un poco mas de tiempo y les cuento.

> [Open resources in Thunar on Xfce 4.4 and 4.6]("http://www.uvena.de/gigolo/help.html#open-resources-in-thunar-on-xfce-4-4-and-4-6")

By default, Gigolo uses gvfs-open to open the connected remote resources. On some systems this will either result in an error or open the wrong file manager because gvfs-open uses the mime types to determine which application it should launch and those mime types are often not configured properly.

First, you need to install the gvfs-fuse backend for GVFS and fuse-utils so that GVfs mounts the remote resources in ~/.gvfs. Make sure that your user is in the fuse group or this will not work. The easiest way to do add your user to the fuse group is to run the following command as root:

gpasswd -a username fuse

or as user using sudo:

sudo gpasswd -a username fuse

Obviously, you should replace username by your actual used username.

Then, you may need to add the following lines to your ~/.local/share/applications/defaults.list so that Thunar is used to open folders by gvfs-open:

x-directory/gnome-default-handler=Thunar.desktop
inode/directory=Thunar.desktop
x-directory/normal=Thunar.desktop

Note

It may be necessary to relaunch your session after those modifications especially when you added your user to the fuse group.

Now, double clicking on a connected bookmark in Gigolo should launch Thunar with the correct folder. Changing Thunar.desktop to the name of the desktop file of any other file manager will of course open the connected bookmarks in this file manager.

(Thanks to Jérôme Guelfucci for these information.)

---

### Post by DrKenobi on 2009-04-24
ya esta, lo del post anterior anda perfecto, solo que una palabrita en ingles me confundio y al principio no me anduvo, pero encontre un post en español que ahi lo dice todo muy clarito (igual al post en ingles pero en español) y ya esta funcionando.

Es muy comodo, es lo que siempre quise y no habia podido encontrar en linux!!!

> [Problema al conectar fuentes remotas con Gigolo en XUBUNTU, Xfce (SOLUCIÓN)]("http://notasconfiguracion.blogspot.com/2009/04/problema-al-conectar-fuentes-remotas.html")

Habia configurado bien el programa Gigolo para conectarme a Windows pero no podia ver el contenido de las carpetas compartidas por el mismo.

Asi solucioné la situación:

En una terminal instalar, si ya no se tiene instalado:

sudo aptitude install gvfs-fuse fuse-utils

Asegurarse de que nuestro usuario esté en el grupo fuse de esta forma:

sudo gpasswd -a username fuse

En donde username es nuestro nombre de usuario.

Y por último abrir este archivo localizado en nuestra carpeta personal y que esta oculto:

~/.local/share/applications/defaults.list

Y agregarle estas líneas:

x-directory/gnome-default-handler=Thunar.desktop
inode/directory=Thunar.desktop
x-directory/normal=Thunar.desktop

Guardar y reiniciar nuestra sesión.

Basado en la ayuda en linea de Gigolo

---

### Post by alewandro on 2009-09-07
Genial!! Estuve horas intentando hasta que probe esto y anda de 10
Gracias

---

