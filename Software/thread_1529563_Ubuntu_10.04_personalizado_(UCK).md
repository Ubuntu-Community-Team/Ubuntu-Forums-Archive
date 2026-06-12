---
title: "Ubuntu 10.04 personalizado (UCK)"
date: 2010-07-12
forum: Software
---

### Post by W31RD on 2010-07-12
Hola nuevamente a todos!

Estoy con un proyecto en el trabajo en  el cual la idea es migrar bastantes equipos (3 hardwares distintos) a  Ubuntu 10.04 Lucid Lynx, y me pidieron que genere una imagen del mismo  personalizada para que sea instalada sin problemas en los equipos  necesarios.

Como es la primera vez que hago esto, me puse a  investigar, y así dí con el software UCK.

Procedí a instalarlo,  ya que leí que es el más "configurable". Realicé una imagen ISO de mi  Ubuntu 10.04 Lucid Lynx y procedía a "buildear" la imagen personalizada.

Al  principio, el UCK solamente da la opción de seleccionar los idiomas y  si durante el "buildeo" de la imagen uno quiere personalizarla o no.  Luego de esas opciones, comienza en una terminal a ejecutarse el build,  montando y desmontando y configurando lo necesario para el programa.

Pero  me surge un error.

El UCK quiere descargar de internet los  paquetes de idioma que necesita para realizar lo nombrado anteriormente,  pero en la empresa no se permite la salida directa a los repositorios  de Ubuntu por internet, si no que se direcciona a un servidor que hace  de "puente" entre internet y los equipos.

El proxy siempre  rechaza las conexiones directas, por lo que todo lo que quiera utilizar  de manera directa a internet es rechazado. Todo va por intranet.

El  problema es que busqué por toda la imagen del Live CD buscando una  especie de archivo "sources.list", me metí en los .conf con mi amigo cat  y grep buscando coincidencias de las palabras "update", "apt", etc., y  terminé mirando los archivos de configuración del UCK.

Uno de  estos es "/usr/lib/uck/customization-profiles/localized_cd/customize", y  al hacer un "cat customize | grep apt" me devolvió resultados, por lo  que entré.

El archivo contiene lo siguiente por default:

```
#!/bin/bash

###################################################################################
#  UCK - Ubuntu Customization  Kit                                                  #
# Copyright  (C) 2006-2010 UCK Team                                                #
#                                                                                  #
# UCK is free software: you can redistribute it and/or  modify                     #
# it under the terms of the GNU General  Public License as published by            #
# the Free Software  Foundation, either version 3 of the License, or               #
# (at  your option) any later  version.                                             #
#                                                                                  #
# UCK is distributed in the hope that it will be  useful,                          #
# but WITHOUT ANY WARRANTY;  without even the implied warranty of                  #
#  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See  the                   #
# GNU General Public License for more  details.                                    #
#                                                                                  #
# You should have received a copy of the GNU General Public  License               #
# along with UCK.  If not, see  <http://www.gnu.org/licenses/>.                    #
###################################################################################

function  failure()
{
    echo "$@"
    exit 1
}

function  prepare_install()
{
    #try 2 times to avoid slow proxies  failures
    apt-get update || apt-get update || failure "apt-get  update failed, error=$?"
}

function install_packages()
{
     apt-get install --assume-yes --force-yes "$@" || failure "apt-get  install $@ failed, error=$?"
}

function remove_packages()
{
     apt-get --purge remove --assume-yes --force-yes "$@" || failure  "apt-get remove $@ failed, error=$?"
}

function  run_package_manager()
{
    echo "Starting package application..."
     
    PACKAGE_APP=`which adept`
    PACKAGE_APP_OPTIONS=(--caption  "UCK Package Manager")
    if [ "$PACKAGE_APP" = "" ]; then
         PACKAGE_APP=`which adept_manager`
    fi
    if [  "$PACKAGE_APP" = "" ]; then
        PACKAGE_APP=`which synaptic`
         PACKAGE_APP_OPTIONS=(-t "UCK Package manager")
    fi
    
     if [ "$PACKAGE_APP" = "" ]; then
        dialog_msgbox "Failure"  "Unable to find any package manager application"
    else
         $PACKAGE_APP "${PACKAGE_APP_OPTIONS[@]}"
        RESULT=$?
    
         if [ $RESULT -ne 0 ]; then
            dialog_msgbox "Failure"  "Running package application $PACKAGE_APP failed, error=$RESULT"
         fi
    fi
}

function run_console()
{
    echo  "Starting console application..."
    
    CONSOLE_APP=`which  konsole`
    CONSOLE_APP_OPTIONS=(--caption "UCK customization  console" -e /bin/bash)
    if [ "$CONSOLE_APP" = "" ]; then
         CONSOLE_APP=`which gnome-terminal`
         CONSOLE_APP_OPTIONS=(-t "UCK customization console" -e /bin/bash)
     fi
    if [ "$CONSOLE_APP" = "" ]; then
         CONSOLE_APP=`which xfce4-terminal`
        CONSOLE_APP_OPTIONS=(-t  "UCK customization console" -e /bin/bash)
    fi
    if [  "$CONSOLE_APP" = "" ]; then
        CONSOLE_APP=`which xterm`
         CONSOLE_APP_OPTIONS=(-title "UCK customization console" -e  /bin/bash)
    fi
    
    if [ "$CONSOLE_APP" = "" ]; then
         dialog_msgbox "Failure" "Unable to find any console application"
     else
        eval `dbus-launch --sh-syntax --exit-with-session  2>/dev/null`
        $CONSOLE_APP "${CONSOLE_APP_OPTIONS[@]}"
         RESULT=$?
    
        if [ $RESULT -ne 0 ]; then
             echo "Running console application $CONSOLE_APP failed, trying the  fallback xterm"
            xterm -title "UCK customization console"  -e /bin/bash
            RESULT=$?
            if [ $RESULT -ne 0  ]; then
                dialog_msgbox "Failure" "Running console  application $CONSOLE_APP failed, error=$RESULT"
            fi
         fi
    fi
}

SCRIPT_DIR=`dirname "$0"`
.  "$SCRIPT_DIR/gui.sh"

LIVECD_LANGS=`cat  "$SCRIPT_DIR/language_packs"`
RUN_MANUAL_CUSTOMIZATIONS=`cat  "$SCRIPT_DIR/run_manual_customizations"`
DESKTOP_TYPE=`cat  "$SCRIPT_DIR/desktop_type"`

DESKTOP_FLAVOURS=`cat  "$SCRIPT_DIR/desktop_types"`

prepare_install || failure  "Preparing installation failed, error=$?"

echo "Installing  language packs ($LIVECD_LANGS)..."

PACKAGES_TO_INSTALL=""
LANGPACKS_CONCATENATED=""

if  [ -n "$LIVECD_LANGS" ]; then
    for LANGPACK in $LIVECD_LANGS; do
         PACKAGES_TO_INSTALL="$PACKAGES_TO_INSTALL language-pack-$LANGPACK  language-support-$LANGPACK"
    
        if [ "$DESKTOP_FLAVOURS"  ]; then
            for FLAVOUR in $DESKTOP_FLAVOURS; do
                 if [ $FLAVOUR == "gnome" ] || [ $FLAVOUR == "kde" ]; then
                     PACKAGES_TO_INSTALL="$PACKAGES_TO_INSTALL  language-pack-$FLAVOUR-$LANGPACK"
                fi
             done
        fi
    
        if [ -z "$LANGPACKS_CONCATENATED"  ]; then
            LANGPACKS_CONCATENATED="$LANGPACK"
         else
             LANGPACKS_CONCATENATED="$LANGPACKS_CONCATENATED|$LANGPACK"
        fi
     done
    
    install_packages $PACKAGES_TO_INSTALL || failure  "Installing language packs failed, error=$?"
    
    #NOTE: we  first install language pack, then remove others as installing language  pack might pull packages
    #which were not previously present
     echo "Removing unnecessary language packages..."
     REMOVED_PACKAGES=`dpkg-query --show | cut -f1 | grep -E  '^(language-pack|language-support)' | grep -v -E  "[-]($LANGPACKS_CONCATENATED)\>"`
    remove_packages  $REMOVED_PACKAGES || failure "Removing packages failed, error=$?"
fi

if  [ "$RUN_MANUAL_CUSTOMIZATIONS" = "yes" ] ; then
    while true ; do
         CHOICE_PACKAGE_MANAGER="Run package manager"
         CHOICE_CONSOLE="Run console application"
         CHOICE_EXIT="Continue building"
        CHOICE=`dialog_menu "Please  choose customization action" "$CHOICE_PACKAGE_MANAGER" "$CHOICE_CONSOLE"  "$CHOICE_EXIT"`
        RESULT=$?

        if [ $RESULT -ne 0 ]  ; then
            failure "Script cancelled by user"
        fi
         #workaround for KDE bug  (https://bugs.kde.org/show_bug.cgi?id=139025)
        CHOICE=`echo  "$CHOICE" | grep -v -i kwrited | tail -n1`

        echo  "CHOICE='$CHOICE'"

        if [ "$CHOICE" = "$CHOICE_EXIT" ] ;  then
            break
        elif [ "$CHOICE" =  "$CHOICE_PACKAGE_MANAGER" ] ; then
            run_package_manager
         elif [ "$CHOICE" = "$CHOICE_CONSOLE" ] ; then
             run_console
        fi
    done
fi

echo "Done"

```Yo  intenté comentar los lugares donde figuraba la función que incluía el  uso de "apt-get update", pero al volver a ejecutarlo recibo esto en  lugar del típico "proxy connection rejected":

```

dt@computer:~$  uck-gui
Preparing build enviroment...
Creating X authentication  cookie...
Running build process...
[sudo] password for dt:
Ubuntu  Customization Kit 2.2.0
Starting CD remastering on lun jul 12  11:08:10 ART 2010
Customization  dir=/home/dt/tmp/customization-scripts
Removing remastering root  dir...
Removing ISO remastering dir...
Mounting ISO image...
Unpacking  ISO image...
Unmounting ISO image...
Mounting SquashFS image...
Unpacking  SquashFS image...
Unmounting SquashFS image...
Removing win32  files... #(yo elegí que quite todos los archivos en relación con win)
Mounting  /proc
Mounting /sys
Mounting /dev/pts
Mounting /var/run
Mounting  /tmp
Mounting /home/dt/tmp/remaster-root-home
Mounting  /home/dt/tmp/remaster-apt-cache
Copying resolv.conf
Creating DBUS  uuid...
/tmp/customization-scripts/customize: line 31: syntax error  near unexpected token `}'
/tmp/customization-scripts/customize: line  31: `}'
Removing generated machine uuid...
Removing generated  resolv.conf
Unmounting  /home/dt/tmp/remaster-root/tmp/customization-scripts...
Unmounting  /home/dt/tmp/remaster-root/var/cache/apt...
Unmounting  /home/dt/tmp/remaster-root/root...
Unmounting  /home/dt/tmp/remaster-root/tmp...
Unmounting  /home/dt/tmp/remaster-root/var/run...
Unmounting  /home/dt/tmp/remaster-root/dev/pts...
Unmounting  /home/dt/tmp/remaster-root/sys...
Unmounting  /home/dt/tmp/remaster-root/proc...
Cleaning up temporary  directories...

```Realmente creo que con saber en que  parte del Live CD de Ubuntu 10.04 Lucid Lynx que estoy utilizando se  encuentra el sources.list default que se utiliza con los repositorios  base de Ubuntu 10.04 bastaría, ya que tal vez cambiando eso en la iso  calculo que el programa al solicitarlos haría el update por intranet y  me dejaría continuar configurándolo (recuerdo nuevamente que es la  primera vez que lo utilizo el UCK), para poder realizar mi imagen  personalizada de Ubuntu para los equipos.

A su vez, si alguno  tiene idea de si se puede realizar la misma para que sea compatible con  distintos drivers según el hardware donde instale éste Live CD, será  realmente bienvenida y agradecida.



Nuevamente, MUCHISIMAS  GRACIAS DE ANTEMANO.

Slds!

---

### Post by guillermolisi on 2010-07-12
Cuando estaba en situaciones similares y con versiones anteriores a la que mencionas, utilizaba el archivo /etc/apt/apt.conf con el siguiente contenido:
```
Acquire::http::Proxy "http://MYDOMAIN\MYNAME:MYPASS@MY.PROXY.COM:MYPORT"
```En caso que el proxy no requiera autenticacion, la linea se resume a:
```
Acquire::http::Proxy "http://MYDOMAIN:MYPORT"
```
En 10.04 no existe ese archivo pero nada impide que lo crees con el contenido indicado.

---

### Post by W31RD on 2010-07-12
> **guillermolisi said:**
> Cuando estaba en situaciones similares y con versiones anteriores a la que mencionas, utilizaba el archivo /etc/apt/apt.conf con el siguiente contenido:
```
Acquire::http::Proxy "http://MYDOMAIN\MYNAME:MYPASS@MY.PROXY.COM:MYPORT"
```En caso que el proxy no requiera autenticacion, la linea se resume a:
```
Acquire::http::Proxy "http://MYDOMAIN:MYPORT"
```En 10.04 no existe ese archivo pero nada impide que lo crees con el contenido indicado.

Guillermo, gracias por responder!

Ese archivo que vos me decis, es el que utilizan las versiones anteriores de Ubuntu 10.04 en los live cd? Porque éste software utiliza la imagen del Live CD de Ubuntu 10.04 para realizar el build de la nueva imagen personalizada, por lo que en realidad necesitaría modificar el archivo del Live CD que indique que el APT vaya a buscar a los repositorios de internet, para modificarlo por los de la intranet y así poder realizar la instalación de los paquetes de idioma, ya que los equipos Linux no tienen permitida la salida a internet para realizar los updates.

Por lo tanto, si yo genero ese archivo, lo tomaría por default, pudiendo indicar ahí mismo los repositorios?

De nuevo, muchas gracias!

Saludos!

---

### Post by juancarlospaco on 2010-07-12
Clonezilla   *(?)*

---

### Post by guillermolisi on 2010-07-12
Conoci las propiedades funcionales de ese archivo cuando instale por primera vez Debian Sarge, asi que tiene sus años. Hasta la 8.04 estaba vigente asi que no veo razon (y si alguien sabe que el metodo es obsoleto, que avise) para que no funcione, aun usando LiveCD.

Cuando apt encuentra este archivo usa las definiciones de su contenido, por defecto. Este archivo sirve para que apt sepa como debe conectarse a Internet, NO indicas ningun respositorio en el. Los repositorios se declaran en otro archivo.

---

### Post by W31RD on 2010-07-12
> **juancarlospaco said:**
> Clonezilla   *(?)*

Juan Carlos, gracias por responder. Acá utilizamos el Clonezilla, pero me gustaría poder utilizar UCk o algún software que realice algo similar a éste, ya que me interesa la utilidad del Live CD generado además de la instalación misma, ya que podrían utilizarse los paquetes instalados en ésta "distribución personalizada".

> **guillermolisi said:**
> Conoci las propiedades funcionales de ese archivo cuando instale por primera vez Debian Sarge, asi que tiene sus años. Hasta la 8.04 estaba vigente asi que no veo razon (y si alguien sabe que el metodo es obsoleto, que avise) para que no funcione, aun usando LiveCD.

Cuando apt encuentra este archivo usa las definiciones de su contenido, por defecto. Este archivo sirve para que apt sepa como debe conectarse a Internet, NO indicas ningun respositorio en el. Los repositorios se declaran en otro archivo.

Guillermo, gracias nuevamente. Entendí lo de la configuración mediante ese archivo para editar la manera de conectarse a internet, pero éste equipo no tiene acceso a internet, por lo que necesitaría que el Live CD tome los repositorios que yo le indique, no necesitando indicar un proxy en ningún momento, ya que los repositorios a utilizar pertenecen a la intranet y no solicitan un proxy ni autenticación.

Muchas gracias a ambos por la ayuda, seguiré investigando.

Slds!

---

### Post by guillermolisi on 2010-07-12
> **W31RD said:**
> Guillermo, gracias nuevamente. Entendí lo de la configuración mediante ese archivo para editar la manera de conectarse a internet, pero éste equipo no tiene acceso a internet, por lo que necesitaría que el Live CD tome los repositorios que yo le indique, no necesitando indicar un proxy en ningún momento, ya que los repositorios a utilizar pertenecen a la intranet y no solicitan un proxy ni autenticación.

Slds!
Podrias explayarte un poco mas y con mas detalle sobre el tema repositoros y esa intranet (que en realidad no se porque llamas asi, de ahi mi pedido).

Si en la red poseen un servidor que oficia de mirror de repositorios, es decir que aloja copias de los repos de Ubuntu, la solucion es una.

Si lo que llamas intranet es un proxy que regula que y quienes tienen acceso a Internet desde dentro de la LAN, la solucion es la que sugeri.

Vos podes indicarle que tome los repositorios que necesites, pero en algun lado, en alguna parte tienen que estar, fisicamente hablando, y con posibilidad de ser accedidos.

Hay una maquina con la estructura y contenido de repositorios en esa LAN ?
Si no la hay, de donde surgen los repositorios que necesitas el utilitario considere en la personalizacion ?

---

### Post by W31RD on 2010-07-12
> **guillermolisi said:**
> Podrias explayarte un poco mas y con mas detalle sobre el tema repositoros y esa intranet (que en realidad no se porque llamas asi, de ahi mi pedido).

Si en la red poseen un servidor que oficia de mirror de repositorios, es decir que aloja copias de los repos de Ubuntu, la solucion es una.

Si lo que llamas intranet es un proxy que regula que y quienes tienen acceso a Internet desde dentro de la LAN, la solucion es la que sugeri.

Vos podes indicarle que tome los repositorios que necesites, pero en algun lado, en alguna parte tienen que estar, fisicamente hablando, y con posibilidad de ser accedidos.

Hay una maquina con la estructura y contenido de repositorios en esa LAN ?
Si no la hay, de donde surgen los repositorios que necesitas el utilitario considere en la personalizacion ?

Guillermo, mil disculpas si no supe expresarme correctamente, lo que quise decir es exactamente a que en la red hay un servidor de mirror de repositorios, al cual quiero apuntar en ésta imagen.

Muchas gracias nuevamente,

Saludos!

---

### Post by guillermolisi on 2010-07-12
> **W31RD said:**
> Guillermo, mil disculpas si no supe expresarme correctamente, lo que quise decir es exactamente a que en la red hay un servidor de mirror de repositorios, al cual quiero apuntar en ésta imagen.

Muchas gracias nuevamente,

Saludos!
Sugiero hacer cambios en el archivo /etc/apt/sources.list, que originalmente podria verse segun el siguiente ejemplo:```

deb http://mirror.globo.com/ubuntu/archive/ lucid-updates main restricted
deb-src http://mirror.globo.com/ubuntu/archive/ lucid-updates main restricted
```y deberia figurar mas o menos asi:```

deb http://<URL/IP/path_del_server>/ lucid-updates main restricted
deb-src http://<URL/IP/path_del_server>/ lucid-updates main restricted
```donde <URL/IP/path_del_server> es el nombre o IP del webserver/maquina que publica los repositorios.

Indique un solo repo a modo de ejemplo.
Tambien podes cambiar el protocolo http por ftp si resulta mas comodo este ultimo para la configuracion/estructura que posean.

Si entras a la pagina de mirrors en el sitio de Ubuntu, podras ver el arbol que resulta tanto para los casos http como para ftp. Ejemplo [http://ftp.caliu.cat/pub/distribucions/ubuntu/releases/](http://ftp.caliu.cat/pub/distribucions/ubuntu/releases/)

[Aqui]("http://ubuntuforums.org/archive/index.php/t-599479.html") tenes una nota tecnica (de las varias que hay en Internet) que habla sobre como montar un mirror de repos local y que cambios introducir para poder consumir su servicio.

---

### Post by W31RD on 2010-07-13
> **guillermolisi said:**
> Sugiero hacer cambios en el archivo /etc/apt/sources.list, que originalmente podria verse segun el siguiente ejemplo:```

deb http://mirror.globo.com/ubuntu/archive/ lucid-updates main restricted
deb-src http://mirror.globo.com/ubuntu/archive/ lucid-updates main restricted
```y deberia figurar mas o menos asi:```

deb http://<URL/IP/path_del_server>/ lucid-updates main restricted
deb-src http://<URL/IP/path_del_server>/ lucid-updates main restricted
```donde <URL/IP/path_del_server> es el nombre o IP del webserver/maquina que publica los repositorios.

Indique un solo repo a modo de ejemplo.
Tambien podes cambiar el protocolo http por ftp si resulta mas comodo este ultimo para la configuracion/estructura que posean.

Si entras a la pagina de mirrors en el sitio de Ubuntu, podras ver el arbol que resulta tanto para los casos http como para ftp. Ejemplo [http://ftp.caliu.cat/pub/distribucions/ubuntu/releases/](http://ftp.caliu.cat/pub/distribucions/ubuntu/releases/)

[Aqui]("http://ubuntuforums.org/archive/index.php/t-599479.html") tenes una nota tecnica (de las varias que hay en Internet) que habla sobre como montar un mirror de repos local y que cambios introducir para poder consumir su servicio.

Guillermo, muchas gracias por la info! Te cuento que los repositorios ya los estoy utilizando en la actualidad como así también varios equipos con Ubuntu y otras distros (hay repositorios para distintas distribuciones como Ubuntu Lucid, Debian Lenny, etc), y los tengo configurados en el sources.list del equipo en el cual estoy ejecutando el UCK, pero no se porque el soft busca en los repositorios "standard" que trae Ubuntu Lucid y no en los que yo tengo configurado, por eso yo pensaba que era algún archivo dentro del Live CD que estoy utilizando como imagen base el que trae ésta configuración de algún lado o algo así.

Igualmente, me recomendaron probar SystemImager, así que si encuentro como solucionar lo del UCK genial, pero a la vez voy a probar éste otro a ver si cumple las funcionalidades del otro o similares.

Saludos!

---

### Post by EnriqueK on 2010-07-13
Te recomiendo usar "Remastersys", primero haces una instalación completa en un equipo con todos los programas , luego usas Remastersys con la opción "distribuible", esto  te va a genarar una ISO que al grabarla será un Live CD o Live DVD instalable que podrás usarlo en otros equipos.
En el siguiente enlace lo puedes descargar y allí tienes mucha información e inclusive tiene un foro para evacuar todas las dudas
[http://geekconnection.org/remastersys/](http://geekconnection.org/remastersys/)

---

### Post by leviatanx on 2010-10-06
Se que el post es viejo pero pongo la manera en que lo solucionamos en mi trabajo asi tienen otra posible solucion.
Lo que hicimos es un scrip que descarga desde nuestros repositorios locales nuestra source.list y la filtramos. este es el script
```
#!/bin/bash
wget -q direccion del repositorio/sources.list -O - | grep  `cat /etc/lsb-release | grep CODENAME | cut -d= -f2` | cut -d# -f2 >> /etc/apt/sources.list 

```

---

