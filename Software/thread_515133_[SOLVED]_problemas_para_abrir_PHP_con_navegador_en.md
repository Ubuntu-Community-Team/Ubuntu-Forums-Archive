---
title: "[SOLVED] problemas para abrir PHP con navegador en Apache2 Ubuntu Festy"
date: 2007-08-01
forum: Software
---

### Post by ccp on 2007-08-01
Hola a todos.
Estoy muy contento con esta primera experiencia que estoy haciendo en Ubuntu. Nunca antes use Linux ni nada parecido, aunque soy un viejo usuario de PC de antes de la XP, en la época de los monitores ámbar o verdes. ;-(
Tenía una pc en desuso y se me ocurrió reciclarla, tal como dice en una Guia de Ubuntu, haciéndola servir.
Como no había nada allí de importancia, instalé Ubuntu borrando todo lo que había a su paso. Tuve algunos problemas hasta que opté por usar el CD Alternate (esta pc tiene 256 de ram pero usa video onboard) (esa sería una advertencia que de existir en alguna parte me hubiera hecho perder algunas horas menos).
Sigo.
Ubuntu funcionó y pasé a mi arriesgada segunda etapa que fue transformarla en un Servidor.
Instalé Apache2, PHP5, Mysql-server y phpmyadmin.
Al parecer anduvo todo ok. Registré mi IP en Dyndns, y ok.
Avancé a Instalar Joomla, para que todo lo anterior tuviera sentido. También, después de un par de intentos, lo logré.
Y finalmente me puse a adecuar Joomla a mi gusto. Trabajé varias horas y todo marchaba bien.
Cambié de pc, a una más moderna y probé entrar a Joomla como ADMIN desde allí. Esa PC corre con Vista.
Entré y trabajé a mucha meyor velocidad remozando mi web.
Se hizo muy tarde y apagué todo y me fui a dormir....
y a la mañana, mi explorador no podía ingresar de nuevo al ADMIN de Joomla. Me corrí a la vieja pc y traté desde ahí. Y ME APARECE EL MISMO PROBLEMA,
Me da la opción de guardar archivo, en vez de abrir en Firefox.
Husmeando en la web entendí que era un problema de Apache, desinstalé, volví a instalar, y así varias veces, desinstalando todo lo que había instalado para correr el servidor, y nada, el mismo problema sigue sin resolverse. Instalé lo que recomendaban por ahí (vean esto: ese problema se soluciona instalando estos paquetes libapache2-mod-auth-mysql y php5-mysql si ya los instalaste proba reinstalando.)
Pero sigue igual.
Me pueden ayudar???
Abrazos y gracias por estar ahí.
Saludos
Claudio

---

### Post by marianom on 2007-08-01
Puede ser que el apache no haya iniciado o puede ser que no esté reconociendo el php.

¿Si pones solo la direccion IP interna de tu red de la máquina -tipo 10.23.1.4-, aparece el mensaje de bienvenida de apache?

---

### Post by ccp on 2007-08-01
Gracias Mariano!!
Pensaba que todo el mundo estaba de vacaciones de invierno!!!
Creo que la ip privada de mi pc es
127.0.1.1
si coloco esa dirección en el firefox lo que aparece es

Index of /
[ICO]	Name	Last modified	Size	Description
[DIR]	apache2-default/	20-Nov-2004 17:16 	-
[DIR]	joomla/	08-Jun-2007 16:28 	-
[DIR]	phpmyadmin/	24-Mar-2007 20:47 	-
Apache/2.2.3 (Ubuntu) Server at 127.0.1.1 Port 80

Gracias de nuevo
CCP

---

### Post by beuno on 2007-08-01
Es muy posible que no este especificado el MIME type para los archivos .php, para que sean procesador por PHP.

No tengo a mano algun link para configurarlo, pero seguramente se deba a como instalaste PHP (quizas antes que Apache).

---

### Post by marianom on 2007-08-01
Bueno, el apache parece funcionar asi que lo que supongo que pasa es que el php no está en funcionamiento.
Vamos a hacer una última prueba con el viejo y querido phpinfo.

Creá un documento nuevo llamada test.php y pone esto dentro:

```
<?php

phpinfo();

?>

```

Grabalo dentro del raíz de documentes de apache (aca voy a ciegas porque yo tengo mi apache configurado a mano así que no es como lo hacen los empaquetadores, es posible que tu raiz sea /var/www/html. Sea donde sea, es el mismo lugar donde tenes los mismos documentos que nos mostrás en tu post anterior) y luego llamalo desde el navegador

[http://127.0.1.1/test.php](http://127.0.1.1/test.php)

Veamos si sale o no. Si no sale, hay que configurarlo.

---

### Post by ccp on 2007-08-01
Gracias Mariano y Beuno,

Mariano, hice la prueba que me dijiste y, efectivamente, no sale.
Es decir, me aparece esa ventana en la que me pregunta por el script en PHP, y qué hacer, si abrirlo o guardarlo (si le digo abrirlo con Firefox, abre otra ventana y aprece de nuevo la misma pregunta, y así hasta abrir infinitas ventanas .... )
Bueno, ahora sigo acà a la espera de instrucciones.
Abrazo y gracias
CCP

---

### Post by marianom on 2007-08-01
¡A configurar se ha dicho! 
Voy a usar mi server para ubicar donde la instalación de apache pone los archivos de configuración y vamos a ver si es lo mismo que en tu server.
Fijate si tenes el archivo httpd.conf dentro de /etc/httpd/conf
(si no está, buscalo en la máquina para ver donde anda) y una vez lo hayas encontrado, dentro de ese archivo busca la palabra php. Si no aparece buscá
"Load config files from the config directory"
y ahí (abajo) vas a tener una opción
Include ...
que te dice donde se guardan los conf del apache para módulos especificos.
Si encontrás algo, contamos que es y seguimos viendo.

pd: tengo tarea familiar asi que no podré ver tus mensajes por un rato. Es posible que alguien te ayude meanwhile y si no, esperame.

---

### Post by ccp on 2007-08-01
THKS Mariano,
Esto es lo que encontré con el buscador:

/etc/apache-ssl/httpd.conf
/etc/apache2/httpd.conf
/etc/apache-perl/httpd.conf
/usr/share/doc/apache2.2-common/examples/apache2/original/httpd.conf.gz

Curiosamente el archivo que está en "/etc/apache2/httpd.conf"
tiene un tamaño de.... 0 b. y, viéndolo con el editor de texto... está vacío en su interior.
Crash!!
Como decía el enfermero de un viejo chiste, todo ensangrentado... "me parece que tocamos una venita".

Bueno sigo acá al pie del cañon a ver si logro recuperar esto.
Mil thks.

CCP

---

### Post by marianom on 2007-08-01
Si yo me tengo que tirar por uno, sería por ese. De todos modos si el archivo de configuración está vacio no debería tomar ni el directorio raiz del server. Raro...
¿Tenés algún apache.conf?

---

### Post by facundocorradini on 2007-08-01
Hola Claudio.

No se cual es tu nivel en desarrollo web, pero por lo que escribís parece que no tenes muchos conocimientos de servidores. (si me equivoco te pido disculpas...)
---------------------------------------------------------------------------------
Generalmente este "problema" se da con los principiantes en desarrollo web.

Lo que suele pasar es que tratan de abrir el script (mediante "abrir con") en firefox, por lo que las cuestiones de php no pasan por apache y por lo tanto no son interpretadas.
(todos pasamos alguna vez por este "problema")


Comunmente deberías tener el sitio en una carpeta dentro de /var/www/ , e ingresar al mismo escribiendo en la barra de direccion de tu explorador 

[http://localhost/nombre_del_sitio/](http://localhost/nombre_del_sitio/)

----------------------------------------------------------------------

Lo raro es que digas que te había andado en un momento...

---

### Post by ccp on 2007-08-01
justo estaba por postear esto y vi tu mensaje. Si, hay un file apache2.conf
tambien en la carpeta
/etc/apache2/

Lo copio a pesar de que es largo. Ahi va:


```

#
# Based upon the NCSA server configuration files originally by Rob McCool.
#
# This is the main Apache server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See <URL:http://httpd.apache.org/docs-2.1/> for detailed information about
# the directives.
#
# Do NOT simply read the instructions in here without understanding
# what they do.  They're here only as hints or reminders.  If you are unsure
# consult the online docs. You have been warned.  
#
# The configuration directives are grouped into three basic sections:
#  1. Directives that control the operation of the Apache server process as a
#     whole (the 'global environment').
#  2. Directives that define the parameters of the 'main' or 'default' server,
#     which responds to requests that aren't handled by a virtual host.
#     These directives also provide default values for the settings
#     of all virtual hosts.
#  3. Settings for virtual hosts, which allow Web requests to be sent to
#     different IP addresses or hostnames and have them handled by the
#     same Apache server process.
#
# Configuration and logfile names: If the filenames you specify for many
# of the server's control files begin with "/" (or "drive:/" for Win32), the
# server will use that explicit path.  If the filenames do *not* begin
# with "/", the value of ServerRoot is prepended -- so "/var/log/apache2/foo.log"
# with ServerRoot set to "" will be interpreted by the
# server as "//var/log/apache2/foo.log".
#

### Section 1: Global Environment
#
# The directives in this section affect the overall operation of Apache,
# such as the number of concurrent requests it can handle or where it
# can find its configuration files.
#

#
# ServerRoot: The top of the directory tree under which the server's
# configuration, error, and log files are kept.
#
# NOTE!  If you intend to place this on an NFS (or otherwise network)
# mounted filesystem then please read the LockFile documentation (available
# at <URL:http://httpd.apache.org/docs-2.1/mod/mpm_common.html#lockfile>);
# you will save yourself a lot of trouble.
#
# Do NOT add a slash at the end of the directory path.
#
ServerRoot "/etc/apache2"

#
# The accept serialization lock file MUST BE STORED ON A LOCAL DISK.
#
#<IfModule !mpm_winnt.c>
#<IfModule !mpm_netware.c>
LockFile /var/lock/apache2/accept.lock
#</IfModule>
#</IfModule>

#
# PidFile: The file in which the server should record its process
# identification number when it starts.
#
PidFile /var/run/apache2.pid

#
# Timeout: The number of seconds before receives and sends time out.
#
Timeout 300

#
# KeepAlive: Whether or not to allow persistent connections (more than
# one request per connection). Set to "Off" to deactivate.
#
KeepAlive On

#
# MaxKeepAliveRequests: The maximum number of requests to allow
# during a persistent connection. Set to 0 to allow an unlimited amount.
# We recommend you leave this number high, for maximum performance.
#
MaxKeepAliveRequests 100

#
# KeepAliveTimeout: Number of seconds to wait for the next request from the
# same client on the same connection.
#
KeepAliveTimeout 15

##
## Server-Pool Size Regulation (MPM specific)
## 

# prefork MPM
# StartServers: number of server processes to start
# MinSpareServers: minimum number of server processes which are kept spare
# MaxSpareServers: maximum number of server processes which are kept spare
# MaxClients: maximum number of server processes allowed to start
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

# worker MPM
# StartServers: initial number of server processes to start
# MaxClients: maximum number of simultaneous client connections
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadsPerChild: constant number of worker threads in each server process
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_worker_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

User www-data
Group www-data

#
# AccessFileName: The name of the file to look for in each directory
# for additional configuration directives.  See also the AllowOverride
# directive.
#

AccessFileName .htaccess

#
# The following lines prevent .htaccess and .htpasswd files from being 
# viewed by Web clients. 
#
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>

TypesConfig /etc/mime.types

#
# DefaultType is the default MIME type the server will use for a document
# if it cannot otherwise determine one, such as from filename extensions.
# If your server contains mostly text or HTML documents, "text/plain" is
# a good value.  If most of your content is binary, such as applications
# or images, you may want to use "application/octet-stream" instead to
# keep browsers from trying to display binary files as though they are
# text.
#
DefaultType text/plain


#
# HostnameLookups: Log the names of clients or just their IP addresses
# e.g., [www.apache.org](www.apache.org) (on) or 204.62.129.132 (off).
# The default is off because it'd be overall better for the net if people
# had to knowingly turn this feature on, since enabling it means that
# each client request will result in AT LEAST one lookup request to the
# nameserver.
#
HostnameLookups Off

# ErrorLog: The location of the error log file.
# If you do not specify an ErrorLog directive within a <VirtualHost>
# container, error messages relating to that virtual host will be
# logged here.  If you *do* define an error logfile for a <VirtualHost>
# container, that host's errors will be logged there and not here.
#
ErrorLog /var/log/apache2/error.log

#
# LogLevel: Control the number of messages logged to the error_log.
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
#
LogLevel warn

# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

# Include all the user configurations:
Include /etc/apache2/httpd.conf

# Include ports listing
Include /etc/apache2/ports.conf

# Include generic snippets of statements
Include /etc/apache2/conf.d/

#
# The following directives define some format nicknames for use with
# a CustomLog directive (see below).
#
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

#
# ServerTokens
# This directive configures what you return as the Server HTTP response
# Header. The default is 'Full' which sends information about the OS-Type
# and compiled in modules.
# Set to one of:  Full | OS | Minor | Minimal | Major | Prod
# where Full conveys the most information, and Prod the least.
#
ServerTokens Full

#
# Optionally add a line containing the server version and virtual host
# name to server-generated pages (internal error documents, FTP directory 
# listings, mod_status and mod_info output etc., but not CGI generated 
# documents or custom error documents).
# Set to "EMail" to also include a mailto: link to the ServerAdmin.
# Set to one of:  On | Off | EMail
#
ServerSignature On

<IfModule alias_module>
    #
    # Aliases: Add here as many aliases as you need (with no limit). The format is 
    # Alias fakename realname
    #
    # Note that if you include a trailing / on fakename then the server will
    # require it to be present in the URL.  So "/icons" isn't aliased in this
    # example, only "/icons/".  If the fakename is slash-terminated, then the 
    # realname must also be slash terminated, and if the fakename omits the 
    # trailing slash, the realname must also omit it.
    #
    # We include the /icons/ alias for FancyIndexed directory listings.  If
    # you do not use FancyIndexing, you may comment this out.
    #
    Alias /icons/ "/usr/share/apache2/icons/"

    <Directory "/usr/share/apache2/icons">
        Options Indexes MultiViews
        AllowOverride None
        Order allow,deny
        Allow from all
    </Directory>

</IfModule>

#
# Directives controlling the display of server-generated directory listings.
#
<IfModule mod_autoindex.c>

    #
    # IndexOptions: Controls the appearance of server-generated directory
    # listings.
    #
    IndexOptions FancyIndexing VersionSort HTMLTable NameWidth=*

    #
    # AddIcon* directives tell the server which icon to show for different
    # files or filename extensions.  These are only displayed for
    # FancyIndexed directories.
    #
    AddIconByEncoding (CMP,/icons/compressed.gif) x-compress x-gzip

    AddIconByType (TXT,/icons/text.gif) text/*
    AddIconByType (IMG,/icons/image2.gif) image/*
    AddIconByType (SND,/icons/sound2.gif) audio/*
    AddIconByType (VID,/icons/movie.gif) video/*

    AddIcon /icons/binary.gif .bin .exe
    AddIcon /icons/binhex.gif .hqx
    AddIcon /icons/tar.gif .tar
    AddIcon /icons/world2.gif .wrl .wrl.gz .vrml .vrm .iv
    AddIcon /icons/compressed.gif .Z .z .tgz .gz .zip
    AddIcon /icons/a.gif .ps .ai .eps
    AddIcon /icons/layout.gif .html .shtml .htm .pdf
    AddIcon /icons/text.gif .txt
    AddIcon /icons/c.gif .c
    AddIcon /icons/p.gif .pl .py
    AddIcon /icons/f.gif .for
    AddIcon /icons/dvi.gif .dvi
    AddIcon /icons/uuencoded.gif .uu
    AddIcon /icons/script.gif .conf .sh .shar .csh .ksh .tcl
    AddIcon /icons/tex.gif .tex
    AddIcon /icons/bomb.gif core

    AddIcon /icons/back.gif ..
    AddIcon /icons/hand.right.gif README
    AddIcon /icons/folder.gif ^^DIRECTORY^^
    AddIcon /icons/blank.gif ^^BLANKICON^^

    #
    # DefaultIcon is which icon to show for files which do not have an icon
    # explicitly set.
    #
    DefaultIcon /icons/unknown.gif

    #
    # AddDescription allows you to place a short description after a file in
    # server-generated indexes.  These are only displayed for FancyIndexed
    # directories.
    # Format: AddDescription "description" filename
    #
    #AddDescription "GZIP compressed document" .gz
    #AddDescription "tar archive" .tar
    #AddDescription "GZIP compressed tar archive" .tgz

    #
    # ReadmeName is the name of the README file the server will look for by
    # default, and append to directory listings.
    #
    # HeaderName is the name of a file which should be prepended to
    # directory indexes. 
    ReadmeName README.html
    HeaderName HEADER.html

    #
    # IndexIgnore is a set of filenames which directory indexing should ignore
    # and not include in the listing.  Shell-style wildcarding is permitted.
    #
    IndexIgnore .??* *~ *# RCS CVS *,v *,t 
</IfModule>

<IfModule mod_mime.c>

    #
    # AddType allows you to add to or override the MIME configuration
    # file mime.types for specific file types.
    #
    #AddType application/x-gzip .tgz
    #
    # AddEncoding allows you to have certain browsers uncompress
    # information on the fly. Note: Not all browsers support this.
    # Despite the name similarity, the following Add* directives have
    # nothing to do with the FancyIndexing customization directives above.
    #
    #AddEncoding x-compress .Z
    #AddEncoding x-gzip .gz .tgz
    #
    # If the AddEncoding directives above are commented-out, then you
    # probably should define those extensions to indicate media types:
    #
    AddType application/x-compress .Z
    AddType application/x-gzip .gz .tgz

    #
    # DefaultLanguage and AddLanguage allows you to specify the language of 
    # a document. You can then use content negotiation to give a browser a 
    # file in a language the user can understand.
    #
    # Specify a default language. This means that all data
    # going out without a specific language tag (see below) will 
    # be marked with this one. You probably do NOT want to set
    # this unless you are sure it is correct for all cases.
    #
    # * It is generally better to not mark a page as 
    # * being a certain language than marking it with the wrong
    # * language!
    #
    # DefaultLanguage nl
    #
    # Note 1: The suffix does not have to be the same as the language
    # keyword --- those with documents in Polish (whose net-standard
    # language code is pl) may wish to use "AddLanguage pl .po" to
    # avoid the ambiguity with the common suffix for perl scripts.
    #
    # Note 2: The example entries below illustrate that in some cases 
    # the two character 'Language' abbreviation is not identical to 
    # the two character 'Country' code for its country,
    # E.g. 'Danmark/dk' versus 'Danish/da'.
    #
    # Note 3: In the case of 'ltz' we violate the RFC by using a three char
    # specifier. There is 'work in progress' to fix this and get
    # the reference data for rfc1766 cleaned up.
    #
    # Catalan (ca) - Croatian (hr) - Czech (cs) - Danish (da) - Dutch (nl)
    # English (en) - Esperanto (eo) - Estonian (et) - French (fr) - German (de)
    # Greek-Modern (el) - Hebrew (he) - Italian (it) - Japanese (ja)
    # Korean (ko) - Luxembourgeois* (ltz) - Norwegian Nynorsk (nn)
    # Norwegian (no) - Polish (pl) - Portugese (pt)
    # Brazilian Portuguese (pt-BR) - Russian (ru) - Swedish (sv)
    # Simplified Chinese (zh-CN) - Spanish (es) - Traditional Chinese (zh-TW)
    #
    AddLanguage ca .ca
    AddLanguage cs .cz .cs
    AddLanguage da .dk
    AddLanguage de .de
    AddLanguage el .el
    AddLanguage en .en
    AddLanguage eo .eo
    AddLanguage es .es
    AddLanguage et .et
    AddLanguage fr .fr
    AddLanguage he .he
    AddLanguage hr .hr
    AddLanguage it .it
    AddLanguage ja .ja
    AddLanguage ko .ko
    AddLanguage ltz .ltz
    AddLanguage nl .nl
    AddLanguage nn .nn
    AddLanguage no .no
    AddLanguage pl .po
    AddLanguage pt .pt
    AddLanguage pt-BR .pt-br
    AddLanguage ru .ru
    AddLanguage sv .sv
    AddLanguage zh-CN .zh-cn
    AddLanguage zh-TW .zh-tw
</IfModule>

<IfModule mod_negotiation.c>
    #
    # LanguagePriority allows you to give precedence to some languages
    # in case of a tie during content negotiation.
    #
    # Just list the languages in decreasing order of preference. We have
    # more or less alphabetized them here. You probably want to change this.
    #
    LanguagePriority en ca cs da de el eo es et fr he hr it ja ko ltz nl nn no pl pt pt-BR ru sv zh-CN zh-TW

    #
    # ForceLanguagePriority allows you to serve a result page rather than
    # MULTIPLE CHOICES (Prefer) [in case of a tie] or NOT ACCEPTABLE (Fallback)
    # [in case no accepted languages matched the available variants]
    #
    ForceLanguagePriority Prefer Fallback

</IfModule>

<IfModule mod_mime.c>
    #
    # Specify a default charset for all pages sent out. This is
    # always a good idea and opens the door for future internationalisation
    # of your web site, should you ever want it. Specifying it as
    # a default does little harm; as the standard dictates that a page
    # is in iso-8859-1 (latin1) unless specified otherwise i.e. you
    # are merely stating the obvious. There are also some security
    # reasons in browsers, related to javascript and URL parsing
    # which encourage you to always set a default char set.
    #
    AddDefaultCharset ISO-8859-1

    #
    # Commonly used filename extensions to character sets. You probably
    # want to avoid clashes with the language extensions, unless you
    # are good at carefully testing your setup after each change.
    # See [http://www.iana.org/assignments/character-sets](http://www.iana.org/assignments/character-sets) for the
    # official list of charset names and their respective RFCs.
    #
    AddCharset us-ascii    .ascii .us-ascii
    AddCharset ISO-8859-1  .iso8859-1  .latin1
    AddCharset ISO-8859-2  .iso8859-2  .latin2 .cen
    AddCharset ISO-8859-3  .iso8859-3  .latin3
    AddCharset ISO-8859-4  .iso8859-4  .latin4
    AddCharset ISO-8859-5  .iso8859-5  .cyr .iso-ru
    AddCharset ISO-8859-6  .iso8859-6  .arb .arabic
    AddCharset ISO-8859-7  .iso8859-7  .grk .greek
    AddCharset ISO-8859-8  .iso8859-8  .heb .hebrew
    AddCharset ISO-8859-9  .iso8859-9  .latin5 .trk
    AddCharset ISO-8859-10  .iso8859-10  .latin6
    AddCharset ISO-8859-13  .iso8859-13
    AddCharset ISO-8859-14  .iso8859-14  .latin8
    AddCharset ISO-8859-15  .iso8859-15  .latin9
    AddCharset ISO-8859-16  .iso8859-16  .latin10
    AddCharset ISO-2022-JP .iso2022-jp .jis
    AddCharset ISO-2022-KR .iso2022-kr .kis
    AddCharset ISO-2022-CN .iso2022-cn .cis
    AddCharset Big5        .Big5       .big5 .b5
    AddCharset cn-Big5     .cn-big5
    # For russian, more than one charset is used (depends on client, mostly):
    AddCharset WINDOWS-1251 .cp-1251   .win-1251
    AddCharset CP866       .cp866
    AddCharset KOI8      .koi8
    AddCharset KOI8-E      .koi8-e
    AddCharset KOI8-r      .koi8-r .koi8-ru
    AddCharset KOI8-U      .koi8-u
    AddCharset KOI8-ru     .koi8-uk .ua
    AddCharset ISO-10646-UCS-2 .ucs2
    AddCharset ISO-10646-UCS-4 .ucs4
    AddCharset UTF-7       .utf7
    AddCharset UTF-8       .utf8
    AddCharset UTF-16      .utf16
    AddCharset UTF-16BE    .utf16be
    AddCharset UTF-16LE    .utf16le
    AddCharset UTF-32      .utf32
    AddCharset UTF-32BE    .utf32be
    AddCharset UTF-32LE    .utf32le
    AddCharset euc-cn      .euc-cn
    AddCharset euc-gb      .euc-gb
    AddCharset euc-jp      .euc-jp
    AddCharset euc-kr      .euc-kr
    #Not sure how euc-tw got in - IANA doesn't list it???
    AddCharset EUC-TW      .euc-tw
    AddCharset gb2312      .gb2312 .gb
    AddCharset iso-10646-ucs-2 .ucs-2 .iso-10646-ucs-2
    AddCharset iso-10646-ucs-4 .ucs-4 .iso-10646-ucs-4
    AddCharset shift_jis   .shift_jis .sjis

    #
    # AddHandler allows you to map certain file extensions to "handlers":
    # actions unrelated to filetype. These can be either built into the server
    # or added with the Action directive (see below)
    #
    # To use CGI scripts outside of ScriptAliased directories:
    # (You will also need to add "ExecCGI" to the "Options" directive.)
    #
    #AddHandler cgi-script .cgi

    #
    # For files that include their own HTTP headers:
    #
    #AddHandler send-as-is asis

    #
    # For server-parsed imagemap files:
    #
    #AddHandler imap-file map

    #
    # For type maps (negotiated resources):
    # (This is enabled by default to allow the Apache "It Worked" page
    #  to be distributed in multiple languages.)
    #
    AddHandler type-map var

    #
    # Filters allow you to process content before it is sent to the client.
    #
    # To parse .shtml files for server-side includes (SSI):
    # (You will also need to add "Includes" to the "Options" directive.)
    #
    AddType text/html .shtml
    AddOutputFilter INCLUDES .shtml
</IfModule>

#
# Action lets you define media types that will execute a script whenever
# a matching file is called. This eliminates the need for repeated URL
# pathnames for oft-used CGI file processors.
# Format: Action media/type /cgi-script/location
# Format: Action handler-name /cgi-script/location
#

#
# Customizable error responses come in three flavors:
# 1) plain text 2) local redirects 3) external redirects
#
# Some examples:
#ErrorDocument 500 "The server made a boo boo."
#ErrorDocument 404 /missing.html
#ErrorDocument 404 "/cgi-bin/missing_handler.pl"
#ErrorDocument 402 [http://www.example.com/subscription_info.html](http://www.example.com/subscription_info.html)
#

#
# Putting this all together, we can internationalize error responses.
#
# We use Alias to redirect any /error/HTTP_<error>.html.var response to
# our collection of by-error message multi-language collections.  We use 
# includes to substitute the appropriate text.
#
# You can modify the messages' appearance without changing any of the
# default HTTP_<error>.html.var files by adding the line:
#
#   Alias /error/include/ "/your/include/path/"
#
# which allows you to create your own set of files by starting with the
# /usr/share/apache2/error/include/ files and copying them to /your/include/path/, 
# even on a per-VirtualHost basis.  The default include files will display
# your Apache version number and your ServerAdmin email address regardless
# of the setting of ServerSignature.
#
# The internationalized error documents require mod_alias, mod_include
# and mod_negotiation.  To activate them, uncomment the following 30 lines.

#    Alias /error/ "/usr/share/apache2/error/"
#
#    <Directory "/usr/share/apache2/error">
#        AllowOverride None
#        Options IncludesNoExec
#        AddOutputFilter Includes html
#        AddHandler type-map var
#        Order allow,deny
#        Allow from all
#        LanguagePriority en cs de es fr it nl sv pt-br ro
#        ForceLanguagePriority Prefer Fallback
#    </Directory>
#
#    ErrorDocument 400 /error/HTTP_BAD_REQUEST.html.var
#    ErrorDocument 401 /error/HTTP_UNAUTHORIZED.html.var
#    ErrorDocument 403 /error/HTTP_FORBIDDEN.html.var
#    ErrorDocument 404 /error/HTTP_NOT_FOUND.html.var
#    ErrorDocument 405 /error/HTTP_METHOD_NOT_ALLOWED.html.var
#    ErrorDocument 408 /error/HTTP_REQUEST_TIME_OUT.html.var
#    ErrorDocument 410 /error/HTTP_GONE.html.var
#    ErrorDocument 411 /error/HTTP_LENGTH_REQUIRED.html.var
#    ErrorDocument 412 /error/HTTP_PRECONDITION_FAILED.html.var
#    ErrorDocument 413 /error/HTTP_REQUEST_ENTITY_TOO_LARGE.html.var
#    ErrorDocument 414 /error/HTTP_REQUEST_URI_TOO_LARGE.html.var
#    ErrorDocument 415 /error/HTTP_UNSUPPORTED_MEDIA_TYPE.html.var
#    ErrorDocument 500 /error/HTTP_INTERNAL_SERVER_ERROR.html.var
#    ErrorDocument 501 /error/HTTP_NOT_IMPLEMENTED.html.var
#    ErrorDocument 502 /error/HTTP_BAD_GATEWAY.html.var
#    ErrorDocument 503 /error/HTTP_SERVICE_UNAVAILABLE.html.var
#    ErrorDocument 506 /error/HTTP_VARIANT_ALSO_VARIES.html.var

<IfModule mod_setenvif.c>
    #
    # The following directives modify normal HTTP response behavior to
    # handle known problems with browser implementations.
    #
    BrowserMatch "Mozilla/2" nokeepalive
    BrowserMatch "MSIE 4\.0b2;" nokeepalive downgrade-1.0 force-response-1.0
    BrowserMatch "RealPlayer 4\.0" force-response-1.0
    BrowserMatch "Java/1\.0" force-response-1.0
    BrowserMatch "JDK/1\.0" force-response-1.0

    #
    # The following directive disables redirects on non-GET requests for
    # a directory that does not include the trailing slash.  This fixes a 
    # problem with Microsoft WebFolders which does not appropriately handle 
    # redirects for folders with DAV methods.
    # Same deal with Apple's DAV filesystem and Gnome VFS support for DAV.
    #
    BrowserMatch "Microsoft Data Access Internet Publishing Provider" redirect-carefully
    BrowserMatch "MS FrontPage" redirect-carefully
    BrowserMatch "^WebDrive" redirect-carefully
    BrowserMatch "^WebDAVFS/1.[012]" redirect-carefully
    BrowserMatch "^gnome-vfs/1.0" redirect-carefully
    BrowserMatch "^XML Spy" redirect-carefully
    BrowserMatch "^Dreamweaver-WebDAV-SCM1" redirect-carefully
</IfModule>

#<IfModule mod_status.c>
    #
    # Allow server status reports generated by mod_status,
    # with the URL of [http://servername/server-status](http://servername/server-status)
    # Change the ".example.com" to match your domain to enable.
    #
    #<Location /server-status>
    #    SetHandler server-status
    #    Order deny,allow
    #    Deny from all
    #    Allow from .example.com
    #</Location>
#</IfModule>

#<IfModule mod_info.c>
    #
    # Allow remote server configuration reports, with the URL of
    #  [http://servername/server-info](http://servername/server-info) (requires that mod_info.c be loaded).
    # Change the ".example.com" to match your domain to enable.
    #
    #<Location /server-info>
    #    SetHandler server-info
    #    Order deny,allow
    #    Deny from all
    #    Allow from .example.com
    #</Location>
#</IfModule>

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

```

////////////////////////////////////
Eso es todo
Gracias
CCP

---

### Post by marianom on 2007-08-01
Lo envolví entre CODES para que quede un poco más corto.

Fijate si tenés algo de php en /etc/apache2/mods-enabled/*.load o  /etc/apache2/mods-enabled/*.conf

---

### Post by ccp on 2007-08-01
Hola Facundo,
gracias por tu atención.

Mi conocimiento en la mayoría de las cosas es en gran parte por práctica, tratar de pensar y curiosear.
Hice algunos sites sobre HTML nada que un novato no pueda hacer.
Es obvio que esto es más ambicioso. Y que me excede. Pero no me voy a rendir así nomás.
Te digo lo que pienso respecto de lo que me decís en tu post.
En un post anterior puse lo que sería el contenido de la carpeta
/var/www/
o sea lo que se ve con
[http://localhost](http://localhost)
sería


ndex of /
[ICO] Name Last modified Size Description
[DIR] apache2-default/ 20-Nov-2004 17:16 -
[DIR] joomla/ 08-Jun-2007 16:28 -
[DIR] phpmyadmin/ 24-Mar-2007 20:47 -
Apache/2.2.3 (Ubuntu) Server at 127.0.1.1 Port 80

eso es lo que se ve si en mi navegador pongo esa url.
Lo que se veía, y que me mostraba que Apache andaba ok y procesaba los PHP como se debe, era cuando entraba en Joomla
Si ponía
[http://localhost/joomla/](http://localhost/joomla/)

aparecía una portada de un sitio web, realizado con Joomla, que es lo que empecé a tunear, por decirlo de algun modo, desde el administrador de Joomla.
Eso fue ayer.
Hoy no anduvo en ningun momento, poneindo esa cosa de si quiero abrir o guardar el PHP, etc.

Gracias again.
CCP

---

### Post by ccp on 2007-08-01
Hola Mariono,
en esa carpeta, nada que diga PHP

THKS
CCP

---

### Post by marianom on 2007-08-01
Hace un archivo que se llame php.conf y pone este es código

```

#
# PHP is an HTML-embedded scripting language which attempts to make it
# easy for developers to write dynamically generated webpages.
#

LoadModule php5_module modules/libphp5.so

#
# Cause the PHP interpreter to handle files with a .php extension.
#
AddType application/x-httpd-php .php
# AddType application/x-httpd-php-source .phps

#
# Add index.php to the list of files that will be served as directory
# indexes.
#
DirectoryIndex index.php

```

Grabalo en /etc/apache2/mods-enabled/

Fair warning 1: en "LoadModule" puse la dirección de mi .so de php. Es posible que el tuyo esté en otro lugar. Buscalo y pone el valor correcto ahí.
Fair warning 2: el LoadModule debería estar en el file llamado php.load pero vamos a ir probando así para ver.
Una vez hayas puesto la dirección de tu modulo php bien y hayas grabado, reinicia el apache y vemos como va.
Reiniciarlo puede ser con 
```
apachectl stop
apachectl start

```o
```
httpd stop
httpd start

```

---

### Post by ccp on 2007-08-01
Hola Mariano,
hice lo que me dijiste.
Puse el path correcto para el archivo .so.
lo guarde.
Restart Apache, no funcionó con los comandos que me pasaste, pero de un machete que tengo usé

$ sudo /etc/init.d/apache2 restart

Abrí una nueva pestaña en mi Firefox y lo mandé al archivo de prueba
test.php
y lo lee perfecto!

Pero.....
Si retrocedo a
[http://localhost](http://localhost)
y ahí le doy un doble click a

Joomla
o a
phpmyadmin
en ambos casos me dice que se trata de abrir un archivo que es
un PHTML file
y de nuevo la pregunta de si lo abre (no me pone con qué aplicación) o lo guarda.
Creo que vamos arrimando gracias a tu disposición de lazarillo.
(Yo crío perros, y eso es un gran elogio.)
Thks again

CCP

---

### Post by marianom on 2007-08-01
Según veo no reconoce el type PHTML y que tenemos que hacer que lo tome.
Te hago un ejemplo:
si revisas el archivo conf.php y el apache.conf vas a ver varias entradas que empiezan con 
AddType 
E.g.: 
AddType application/x-httpd-php .php
AddType application/x-compress .Z
AddType application/x-gzip .gz .tgz

Ahí le estamos indicando como se tiene que comportar cuando vea la extensión: si es .php, tiene que interpretarlo como un application/x-httpd-php, et cetera.
Tenemos que agregarle una entrada similar para el phtml en php. Entonces donde dice 
```
AddType application/x-httpd-php .php
```
debería decir 
```
AddType application/x-httpd-php .php .phtml
```

Así que hace ese cambio en php.conf, grabalo, reiniciar el apache y proba de nuevo.

---

### Post by ccp on 2007-08-01
Mariano,
Felizmente, con las indicaciones de tu post se solucionó. Mil gracias.
Voy a tener que reinstalar Mysql, porque el phpmyadmin me dice que hay un problema con el socket. EL error que me da es:

#2002 - El servidor no está respondiendo (o el socket del servidor MySQL local no está configurado correctamente)

De modo que reinstalaré Mysql y esperemos que vuelva a la normalidad. Te mando un abrazo y un enorme GRACIAS!!!

CCP

---

### Post by marianom on 2007-08-01
np.
Cambiate a PostgreSQL que es una base de datos más copada ;)

Una última cosa: ahora que tenes la data de donde van las cosas correctamente, hace un poco de search en la web para asegurarte que estás respetando las parametrizaciones del paquete (por ejemplo, como te dije antes, el LoadModule capaz que va en el archivo .load). El problema a veces de meter mano es que, cuando bajás una actualización de php -por ejemplo-, el sistema queda mal configurado porque no encuentra la instrucción en el lugar adecuado o te duplica entradas en los archivos de configuración  y terminás en un problema más grande.

Suerte.

---

### Post by facundocorradini on 2007-08-02
Yo te aconsejaría seguir usando MySQL porque es el que mejor se integra con PHP y el que está en más servidores....

---

### Post by Oktubre on 2007-08-02
Pegale una mirada a este sitio: 

[http://www.apachefriends.org/en/index.html](http://www.apachefriends.org/en/index.html)

Podes instalarte este paquete que te va a servir para lo que necesitas.

Saludos

---

### Post by ccp on 2007-08-03
Gracias a todos!!!
CCP

---

### Post by frankelydiaz on 2008-07-31
buen post:d me pasaba algo similar y leí este post y pues ^^ solucione mi problema gracias maestros:p

---

### Post by porquero on 2009-07-11
> **marianom said:**
> según veo no reconoce el type phtml y que tenemos que hacer que lo tome.
Te hago un ejemplo:
Si revisas el archivo conf.php y el apache.conf vas a ver varias entradas que empiezan con 
addtype 
e.g.: 
Addtype application/x-httpd-php .php
addtype application/x-compress .z
addtype application/x-gzip .gz .tgz

ahí le estamos indicando como se tiene que comportar cuando vea la extensión: Si es .php, tiene que interpretarlo como un application/x-httpd-php, et cetera.
Tenemos que agregarle una entrada similar para el phtml en php. Entonces donde dice 
```
addtype application/x-httpd-php .php
```
debería decir 
```
addtype application/x-httpd-php .php .phtml
```

así que hace ese cambio en php.conf, grabalo, reiniciar el apache y proba de nuevo.

esta es la respuesta!!!!
Gracias!

---

### Post by xristian on 2012-07-02
**Apache no ejecuta scripts PHP [Solución]**
 -------------------------------------------------------------
(Instala una página "index.html" para probar que el servidor apache funciona bien en la carpeta "public_html". Si la abre, quiere decir que apache funciona bien con los archivos html y el problema es que falla con los archivos php).


**Solución: **el problema puede ser un paquete no instalado:
#apt-get install libapache2-mod-php5

Una vez instalado, hay que añadir unas líneas en /etc/apache2/apache2.conf, o crear un nuevo archivo en /etc/apache2/mods-enabled/php.conf, con el siguiente contenido:

  [B]  LoadModule php5_module modules/libphp5.so

    [/B][B]AddType application/x-httpd-php .php
    AddType application/x-httpd-php-source .phps[/B]
------------------------------------
Salir y guardar.
Reiniciar servicio de apache.
------------------------------------

---

