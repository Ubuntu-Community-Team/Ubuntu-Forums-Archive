---
title: "Tutorial:  instalar y configurar MPD + Sonata (Updated)"
date: 2010-03-13
forum: Software
---

### Post by leonardomdq on 2010-03-13
[LEFT][CENTER][LEFT][FONT=System]**[SIZE=4]Como instalar y configurar MPD + Sonata[/SIZE]**[/FONT][COLOR=Blue]**[SIZE=4] (ACTUALIZADO)[/SIZE]**[/COLOR]
[/LEFT]
 


[LEFT][[IMG]http://img163.imageshack.us/img163/6590/pantallazoen.png[/IMG]]("http://img163.imageshack.us/i/pantallazoen.png/")
[/LEFT]
[/CENTER]
[/LEFT]


Para los que aún no saben que es MPD y Sonata, les explicaré brevemente… MPD (Music Player Deamon) es un reproductor de audio que funciona en el background de nuestro sistema. Puede reproducir música sin problemas pero necesita un gestor visual para poder controlar la música que se quiere reproducir. Es ahi cuando llega Sonata. Sonata es un gestor visual para controlar la música que se reproduce en el MPD.
 MPD no depende de Sonata. Ya que la música se reproduce en el background de sistema podemos facilmente terminar Sonata y aún así la música seguirá reproduciendose. Hasta pueden terminar la sesión del sistema con CTRL+ALT+BACKSPACE y la música seguirá sonando en el background.
 MPD junto a Sonata hacen una buena combinación ya que consumen pocos recursos y facil de manejar luego de haberlo configurado en un principio.


Instalamos MPD + Sonata:

Abrimos una consola y ponemos lo siguiente:
```
sudo apt-get install mpd sonata
```Terminada la instalación vamos a editar el archivo de configuracion de MPD, para configurar el demonio.
```
sudo gedit /etc/mpd.conf
```1) Buscamos la linea :
```
music_directory
```En esta linea tenemos que poner la ruta hacia la carpeta de música.

Ejemplo: 
```
/home/tu_usuario/Música
```2) En este paso tenemos que cambiar la ubicacion de todas las carpetas de MPD (de esta manera nos apropiamos de todos los archivos de MPD)
```

playlist_directory    "/home/**tu_usuario**/.mpd/playlists"
db_file                "/home/**tu_usuario**/.mpd/tag_cache"
log_file        "/home/**tu_usuario**/.mpd/log"
error_file        "/home/**tu_usuario**/.mpd/errors.log"
pid_file        "/home/**tu_usuario**/.mpd/pid"
state_file        "/home/**tu_usuario**/.mpd/state"

```3)Una ves que ya tenemos todos los archivos dirigidos a nuestro home, podemos cambiar el usuario y puerto (muchas veces el puerto 6600 que viene por defecto trae problemas)
Deben eliminar el # que esta delante de "port" .
```

user     "**tu_usuario**"
port     "8888"

```4) Usuarios con Pulseaudio, buscar y modificar como esta aca:

```

audio_output {
        type    "pulse"
        name    "My MPD PulseAudio Output"
}

```5) Ahora elegir el mezclador, seleccionamos el siguiente (tiene que quitar el # que esta delante)
```

mixer_type "software"

```Guardamos y cerramos el mpd.conf.


Ahora vamos a crear las carpetas

```
mkdir -p ~/.mpd/playlists
```Le asignamos permisos correspondientes:
```
sudo chmod 644 /etc/mpd.conf
```Creamos la base de datos:
```
mpd --create-db
```Para terminar reiniciamos el daemon:
```
sudo /etc/init.d/mpd restart
```Ya tenemos instalado y configurado nuestro demonio MPD, ahora vamos a configurar Sonata.

Abrimos Sonata previamente instalado, nos posamos sobre el y con el boton derecho del mouse vamos a "preferencias" y modificamos en la primer solapa MPD poniendo el puerto (8888), tu_usuario (en mi caso puse "leonardo") y directorio de musica.

**IMPORTANTE:** Para que MPD reconosca las carpetas de música tenemos que tener las carpetas separadas, un ejemplo:

[[IMG]http://img293.imageshack.us/img293/6209/dreamsbyleonardomdq.png[/IMG]](http://img293.imageshack.us/i/dreamsbyleonardomdq.png/)



Dejo una captura a modo de ejemplo de las preferencias de MPD:

[[IMG]http://img62.imageshack.us/img62/7035/screenshotkxn.png[/IMG]]("http://img684.imageshack.us/img684/1356/screenshotsi.png")


No creo olvidarme nada, cualquier cosa me avisan.


Saludos y no duden en preguntar :D

---

### Post by Mustaine666 on 2010-03-14
leonardo.. hice todo lo que explicas en el tutorial..
pero tengo el problema que me dice.. sin permiso de lectura..
en la barra de progreso de arriba.. y no reconoce los archivos de la biblioteca..

---

### Post by rubioo on 2010-03-14
Gracias por la info. leo :D

---

### Post by leonardomdq on 2010-03-16
> **Mustaine666 said:**
> leonardo.. hice todo lo que explicas en el tutorial..
pero tengo el problema que me dice.. sin permiso de lectura..
en la barra de progreso de arriba.. y no reconoce los archivos de la biblioteca..
Hola Mustaine, ayer instale un Xubuntu 9.10 y le puse sonata+mpd sin problemas..
Tambien en Lucid va barbaro, como te decia el otro dia, te aconsejo que borres todo lo que sea sonata, mpd y actualiza los repositorios ... recien ahi segui el tutorial.

Mira en Ubuntu 10.4 alpha3 va barbaro :D

[[IMG]http://img684.imageshack.us/img684/9579/pantallazo1g.th.png[/IMG]](http://img684.imageshack.us/i/pantallazo1g.png/)

---

### Post by Mustaine666 on 2010-03-16
lo borre desde el gestor de paquetes de synaptic.. 

desinstale completamente.. 

me faltarian actulizar los repositorios.. podrias explicar como se hace?..

---

### Post by guillermolisi on 2010-03-16
Tal vez con actualizar los repos se referia a ```
sudo apt-get update
```para que el cache de repositorios en la maquina contenga las ultimas versiones de los paquetes.

En Synaptic es el boton de Reload/Recargar.

---

### Post by leonardomdq on 2010-03-16
Como te dice Guillermo actualiza los repositorios.
No te olvides de borrar todo rastro de sonata y mpd.

si vas a /usr/share y ahi tenes la carpeta sonata y el mpd.conf (eliminalos).

Para desintalar sonata y mpd en una terminal pones:
```
sudo aptitude remove mpd sonata
```

Reinicia y recien ahi seguis el tutorial.

Avisa como te fue.
Saludos ;)

---

### Post by Mustaine666 on 2010-03-16
luego de borrar reinicie la pc.. y empeze..

```

sudo apt-get install mpd sonata

```


en una parte cuando esta configurando me devuelve esto.. que me parece muy raro..

```

Configurando mpd (0.15.8+git20100312.469c9b5-0ubuntu1~ripps1~karmic) ...
 * Starting Music Player Daemon mpd                                              * creating /var/lib/mpd/tag_cache... 
                                                                         [ OK ]

Configurando python-eggtrayicon (2.25.3-3ubuntu1) ...
listen: bind to 127.0.0.1:6600 failed: Address already in use (continuing anyway, because at least one address is bound)
Failed to load database: Failed to open database file "/var/lib/mpd/tag_cache": No such file or directory


```


bueno.. prosegui en la instalacion ... 

configure el mpd.conf.. 

y ejecuto el comando este.. en la consola..

```

sudo mpd --create-db
```

```

mofle@mofle-desktop:~$ sudo mpd --create-db
[sudo] password for mofle: 

** ERROR **: option parsing failed: Unknown option --create-db

aborting...
Cancelado
mofle@mofle-desktop:~$ 
```

me devolvio eso ..

reinicie.. la pc.. y cuando lo abro a sonata.. abre sin la cruz roja que denota que no anda.. 

que puede ser? .. se les ocurre algo?

---

### Post by leonardomdq on 2010-03-16
Para solucionar eso edita el mpd.conf , busca esta linea y comentala  (comentar es agregarle # adelante), guardas los cambios y reinicia el  sistema.

```

# For network
**[COLOR=Red]#bind_to_address        "localhost"[/COLOR]**
#
# And for Unix Socket
#bind_to_address        "/var/run/mpd/socket"

```

---

### Post by Mustaine666 on 2010-03-16
> **leonardomdq said:**
> Para solucionar eso edita el mpd.conf , busca esta linea y comentala  (comentar es agregarle # adelante), guardas los cambios y reinicia el  sistema.

```

# For network
**[COLOR=Red]#bind_to_address        "localhost"[/COLOR]**
#
# And for Unix Socket
#bind_to_address        "/var/run/mpd/socket"

```


lo comento con "#" .. reinicio.. vuelvo a abrir sonata.. y no pasa nada ... sigue con lo mismo.. sin reconocer la biblioteca..

---

### Post by Mustaine666 on 2010-03-27
les comento.. tuve que reinstalar ubuntu.. por algunos problemas.. de q no iniciaba.. y decidi intentar instalar otra vez sonata y mpd .. 

esta vez la instalacion fue sin errores sin nada.. el unico problema.. es que cuando voy a crear la base de datos

```

sudo mpd --create-db

```

me devuelve esto. .

```

mustaine@mustaine-desktop:~$ sudo mpd --create-db
[sudo] password for mustaine: 
listen: Failed to listen on *:6600: Address already in use
Cancelado
mustaine@mustaine-desktop:~$ 

```

bueno.. por mis conocimientos.. es por q mpd esta corriendo..

entonces.. lo que hice fue poner

```

sudo killall mpd
```

y volvi a intentar hacer la base de datos.. 
y me devolvio esto

```

mustaine@mustaine-desktop:~$ sudo killall mpd
mustaine@mustaine-desktop:~$ sudo mpd --create-db
mustaine@mustaine-desktop:~$ 

```

reinicie.. la pc .. y sigue sin andar! .. que puede ser?

---

### Post by leonardomdq on 2010-03-28
reintentemos entonses.

el archivo mpd.conf que te quede como el mio salvo lo que esta en rojo que es la ruta a la carpeta de la musica

abri una consola y pone esto:
```
sudo gedit /etc/mpd.conf
```ahora edita tu mpd.conf y dejalo como esta el mio.
```

# An example configuration file for MPD
# See the mpd.conf man page for a more detailed description of each parameter.


# Files and directories #######################################################
#
# This setting controls the top directory which MPD will search to discover the
# available audio files and add them to the daemon's online database. This 
# setting defaults to the XDG directory, otherwise the music directory will be
# be disabled and audio files will only be accepted over ipc socket (using
# file:// protocol) or streaming files over an accepted protocol.
#
music_directory        **[COLOR=Red]"/home/leonardo/Música"[/COLOR]**
#
# This setting sets the MPD internal playlist directory. The purpose of this
# directory is storage for playlists created by MPD. The server will use 
# playlist files not created by the server but only if they are in the MPD
# format. This setting defaults to playlist saving being disabled.
#
playlist_directory        "/var/lib/mpd/playlists"
#
# This setting sets the location of the MPD database. This file is used to
# load the database at server start up and store the database while the 
# server is not up. This setting defaults to disabled which will allow
# MPD to accept files over ipc socket (using file:// protocol) or streaming
# files over an accepted protocol.
#
db_file            "/var/lib/mpd/tag_cache"
# 
# These settings are the locations for the daemon log files for the daemon.
# These logs are great for troubleshooting, depending on your log_level
# settings.
#
# The special value "syslog" makes MPD use the local syslog daemon. This
# setting defaults to logging to syslog, otherwise logging is disabled.
#
log_file            "/var/log/mpd/mpd.log"
#
# This setting sets the location of the file which stores the process ID
# for use of mpd --kill and some init scripts. This setting is disabled by
# default and the pid file will not be stored.
#
pid_file            "/var/run/mpd/pid"
#
# This setting sets the location of the file which contains information about
# most variables to get MPD back into the same general shape it was in before
# it was brought down. This setting is disabled by default and the server 
# state will be reset on server start up.
#
state_file            "/var/lib/mpd/state"
#
###############################################################################


# General music daemon options ################################################
#
# This setting specifies the user that MPD will run as. MPD should never run as
# root and you may use this setting to make MPD change its user ID after
# initialization. This setting is disabled by default and MPD is run as the
# current user.
#
user                "mpd"
#
# This setting sets the address for the daemon to listen on. Careful attention
# should be paid if this is assigned to anything other then the default, any.
# This setting can deny access to control of the daemon.
#
# For network
#bind_to_address        "localhost"
#
# And for Unix Socket
#bind_to_address        "/var/run/mpd/socket"
#
# This setting is the TCP port that is desired for the daemon to get assigned
# to.
#
#port                "6600"
#
# This setting controls the type of information which is logged. Available 
# setting arguments are "default", "secure" or "verbose". The "verbose" setting
# argument is recommended for troubleshooting, though can quickly stretch
# available resources on limited hardware storage.
#
#log_level            "default"
#
# If you have a problem with your MP3s ending abruptly it is recommended that 
# you set this argument to "no" to attempt to fix the problem. If this solves
# the problem, it is highly recommended to fix the MP3 files with vbrfix
# (available from <http://www.willwap.co.uk/Programs/vbrfix.php>), at which
# point gapless MP3 playback can be enabled.
#
#gapless_mp3_playback            "yes"
#
# This setting enables MPD to create playlists in a format usable by other
# music players.
#
#save_absolute_paths_in_playlists    "no"
#
# This setting defines a list of tag types that will be extracted during the 
# audio file discovery process. Optionally, 'comment' can be added to this
# list.
#
#metadata_to_use    "artist,album,title,track,name,genre,date,composer,performer,disc"
#
###############################################################################


# Symbolic link behavior ######################################################
#
# If this setting is set to "yes", MPD will discover audio files by following 
# symbolic links outside of the configured music_directory.
#
#follow_outside_symlinks    "yes"
#
# If this setting is set to "yes", MPD will discover audio files by following
# symbolic links inside of the configured music_directory.
#
#follow_inside_symlinks        "yes"
#
###############################################################################


# Zeroconf / Avahi Service Discovery ##########################################
#
# If this setting is set to "yes", service information will be published with
# Zeroconf / Avahi.
#
#zeroconf_enabled        "yes"
#
# The argument to this setting will be the Zeroconf / Avahi unique name for
# this MPD server on the network.
#
#zeroconf_name            "Music Player"
#
###############################################################################


# Permissions #################################################################
#
# If this setting is set, MPD will require password authorization. The password
# can setting can be specified multiple times for different password profiles.
#
#password                        "password@read,add,control,admin"
#
# This setting specifies the permissions a user has who has not yet logged in. 
#
#default_permissions             "read,add,control,admin"
#
###############################################################################


# Input #######################################################################
#

input {
        plugin "curl"
#       proxy "proxy.isp.com:8080"
#       proxy_user "user"
#       proxy_password "password"
}

#
###############################################################################

# Audio Output ################################################################
#
# MPD supports various audio output types, as well as playing through multiple 
# audio outputs at the same time, through multiple audio_output settings 
# blocks. Setting this block is optional, though the server will only attempt
# autodetection for one sound card.
#
# See <http://mpd.wikia.com/wiki/Configuration#Audio_Outputs> for examples of 
# other audio outputs.
#
# An example of an ALSA output:
#
audio_output {
    type        "alsa"
    name        "My ALSA Device"
    device        "hw:0,0"    # optional
    format        "44100:16:2"    # optional
    mixer_device    "default"    # optional
    mixer_control    "PCM"        # optional
    mixer_index    "0"        # optional
}
#
# An example of an OSS output:
#
#audio_output {
#    type        "oss"
#    name        "My OSS Device"
#    device        "/dev/dsp"    # optional
#    format        "44100:16:2"    # optional
#    mixer_device    "/dev/mixer"    # optional
#    mixer_control    "PCM"        # optional
#}
#
# An example of a shout output (for streaming to Icecast):
#
#audio_output {
#    type        "shout"
#    encoding    "ogg"            # optional
#    name        "My Shout Stream"
#    host        "localhost"
#    port        "8000"
#    mount        "/mpd.ogg"
#    password    "hackme"
#    quality        "5.0"
#    bitrate        "128"
#    format        "44100:16:1"
#    protocol    "icecast2"        # optional
#    user        "source"        # optional
#    description    "My Stream Description"    # optional
#    genre        "jazz"            # optional
#    public        "no"            # optional
#    timeout        "2"            # optional
#}
#
# An example of a httpd output (built-in HTTP streaming server):
#
#audio_output {
#    type        "httpd"
#    name        "My HTTP Stream"
#    encoder        "vorbis"        # optional, vorbis or lame
#    port        "8000"
#    quality        "5.0"            # do not define if bitrate is defined
#    bitrate        "128"            # do not define if quality is defined
#    format        "44100:16:1"
#}
#
# An example of a pulseaudio output (streaming to a remote pulseaudio server)
#
#audio_output {
#    type        "pulse"
#    name        "My Pulse Output"
#    server        "remote_server"        # optional
#    sink        "remote_server_sink"    # optional
#}
#
## Example "pipe" output:
#
#audio_output {
#    type        "pipe"
#    name        "my pipe"
#    command        "aplay -f cd 2>/dev/null"
## Or if you're want to use AudioCompress
#    command        "AudioCompress -m | aplay -f cd 2>/dev/null"
## Or to send raw PCM stream through PCM:
#    command        "nc example.org 8765"
#    format        "44100:16:2"
#}
#
## An example of a null output (for no audio output):
#
#audio_output {
#    type        "null"
#    name        "My Null Output"
#}
#
# This setting will change all decoded audio to be converted to the specified
# format before being passed to the audio outputs. By default, this setting is
# disabled.
#
#audio_output_format        "44100:16:2"
#
# If MPD has been compiled with libsamplerate support, this setting specifies 
# the sample rate converter to use.  Possible values can be found in the 
# mpd.conf man page or the libsamplerate documentation. By default, this is
# setting is disabled.
#
#samplerate_converter        "Fastest Sinc Interpolator"
#
###############################################################################


# Volume control mixer ########################################################
#
# These are the global volume control settings. By default, this setting will
# be detected to the available audio output device, with preference going to 
# hardware mixing. Hardware and software mixers for individual audio_output
# sections cannot yet be mixed.
#
# An example for controlling an ALSA, OSS or Pulseaudio mixer; If this
# setting is used other sound applications will be affected by the volume
# being controlled by MPD.
#
#mixer_type            "hardware"
#
# An example for controlling all mixers through software. This will control
# all controls, even if the mixer is not supported by the device and will not
# affect any other sound producing applications.
#
mixer_type            "software"
#
# This example will not allow MPD to touch the mixer at all and will disable
# all volume controls.
#
#mixer_type            "disabled"
#
###############################################################################


# Normalization automatic volume adjustments ##################################
#
# This setting specifies the type of ReplayGain to use. This setting can have
# the argument "album" or "track". See <http://www.replaygain.org> for more
# details. This setting is disabled by default.
#
#replaygain            "album"
#
# This setting sets the pre-amp used for files that have ReplayGain tags. By
# default this setting is disabled.
#
#replaygain_preamp        "0"
#
# This setting enables on-the-fly normalization volume adjustment. This will
# result in the volume of all playing audio to be adjusted so the output has 
# equal "loudness". This setting is disabled by default.
#
#volume_normalization        "no"
#
###############################################################################


# MPD Internal Buffering ######################################################
#
# This setting adjusts the size of internal decoded audio buffering. Changing
# this may have undesired effects. Don't change this if you don't know what you
# are doing.
#
#audio_buffer_size        "2048"
#
# This setting controls the percentage of the buffer which is filled before 
# beginning to play. Increasing this reduces the chance of audio file skipping, 
# at the cost of increased time prior to audio playback.
#
#buffer_before_play        "10%"
#
###############################################################################


# Resource Limitations ########################################################
#
# These settings are various limitations to prevent MPD from using too many
# resources. Generally, these settings should be minimized to prevent security
# risks, depending on the operating resources.
#
#connection_timeout        "60"
#max_connections        "10"
#max_playlist_length        "16384"
#max_command_list_size        "2048"
#max_output_buffer_size        "8192"
#
###############################################################################


# Character Encoding ##########################################################
#
# If file or directory names do not display correctly for your locale then you 
# may need to modify this setting. After modification of this setting mpd 
# --create-db must be run to change the database.
#
filesystem_charset        "UTF-8"
#
# This setting controls the encoding that ID3v1 tags should be converted from.
#
id3v1_encoding            "UTF-8"
#
###############################################################################

```Otra cosa, el comando 
[COLOR=Red]sudo mpd --create-db[/COLOR] es obsoleto. (no lo utilises)

Despues de hacer esto, arrancas sonata desde Aplicaciones > sonido y video > sonata

abris las preferencias y que te quede como en el screenshot

[[IMG]http://img519.imageshack.us/img519/6118/pantallazo1l.th.png[/IMG]]("http://img519.imageshack.us/i/pantallazo1l.png/")

Luego cerras sonata, reinicias la pc y tendria que quedar andando.

Avisa como te fue, no toques nada si dudas de algo, mejor consultanos.

Exitos ;)

---

### Post by Mustaine666 on 2010-03-28
sigo con el mismo problema.. 

este es mi mpd.conf
```

# An example configuration file for MPD
# See the mpd.conf man page for a more detailed description of each parameter.


# Files and directories #######################################################
#
# This setting controls the top directory which MPD will search to discover the
# available audio files and add them to the daemon's online database. This 
# setting defaults to the XDG directory, otherwise the music directory will be
# be disabled and audio files will only be accepted over ipc socket (using
# file:// protocol) or streaming files over an accepted protocol.
#
music_directory		"/home/mustaine/Música"
#
# This setting sets the MPD internal playlist directory. The purpose of this
# directory is storage for playlists created by MPD. The server will use 
# playlist files not created by the server but only if they are in the MPD
# format. This setting defaults to playlist saving being disabled.
#
playlist_directory		"/var/lib/mpd/playlists"
#
# This setting sets the location of the MPD database. This file is used to
# load the database at server start up and store the database while the 
# server is not up. This setting defaults to disabled which will allow
# MPD to accept files over ipc socket (using file:// protocol) or streaming
# files over an accepted protocol.
#
db_file			"/var/lib/mpd/tag_cache"
# 
# These settings are the locations for the daemon log files for the daemon.
# These logs are great for troubleshooting, depending on your log_level
# settings.
#
# The special value "syslog" makes MPD use the local syslog daemon. This
# setting defaults to logging to syslog, otherwise logging is disabled.
#
log_file			"/var/log/mpd/mpd.log"
#
# This setting sets the location of the file which stores the process ID
# for use of mpd --kill and some init scripts. This setting is disabled by
# default and the pid file will not be stored.
#
pid_file			"/var/run/mpd/pid"
#
# This setting sets the location of the file which contains information about
# most variables to get MPD back into the same general shape it was in before
# it was brought down. This setting is disabled by default and the server 
# state will be reset on server start up.
#
state_file			"/var/lib/mpd/state"
#
# The location of the sticker database.  This is a database which
# manages dynamic information attached to songs.
#
sticker_file		"/var/lib/mpd/sticker.sqlite"
#
###############################################################################


# General music daemon options ################################################
#
# This setting specifies the user that MPD will run as. MPD should never run as
# root and you may use this setting to make MPD change its user ID after
# initialization. This setting is disabled by default and MPD is run as the
# current user.
#
user				"mpd"
#
# This setting specifies the group that MPD will run as. If not specified
# primary group of user specified with "user" setting will be used (if set).
# This is useful if MPD needs to be a member of group such as "audio" to
# have permission to use sound card.
#
group				"audio"
#
# This setting sets the address for the daemon to listen on. Careful attention
# should be paid if this is assigned to anything other then the default, any.
# This setting can deny access to control of the daemon.
#
# For network
bind_to_address		"localhost"
#
# And for Unix Socket
#bind_to_address		"/var/run/mpd/socket"
#
# This setting is the TCP port that is desired for the daemon to get assigned
# to.
#
#port				"6600"
#
# This setting controls the type of information which is logged. Available 
# setting arguments are "default", "secure" or "verbose". The "verbose" setting
# argument is recommended for troubleshooting, though can quickly stretch
# available resources on limited hardware storage.
#
#log_level			"default"
#
# If you have a problem with your MP3s ending abruptly it is recommended that 
# you set this argument to "no" to attempt to fix the problem. If this solves
# the problem, it is highly recommended to fix the MP3 files with vbrfix
# (available from <http://www.willwap.co.uk/Programs/vbrfix.php>), at which
# point gapless MP3 playback can be enabled.
#
#gapless_mp3_playback			"yes"
#
# This setting enables MPD to create playlists in a format usable by other
# music players.
#
#save_absolute_paths_in_playlists	"no"
#
# This setting defines a list of tag types that will be extracted during the 
# audio file discovery process. Optionally, 'comment' can be added to this
# list.
#
#metadata_to_use	"artist,album,title,track,name,genre,date,composer,performer,disc"
#
# This setting enables automatic update of MPD's database when files in 
# music_directory are changed.
#
#auto_update	"yes"
###############################################################################


# Symbolic link behavior ######################################################
#
# If this setting is set to "yes", MPD will discover audio files by following 
# symbolic links outside of the configured music_directory.
#
#follow_outside_symlinks	"yes"
#
# If this setting is set to "yes", MPD will discover audio files by following
# symbolic links inside of the configured music_directory.
#
#follow_inside_symlinks		"yes"
#
###############################################################################


# Zeroconf / Avahi Service Discovery ##########################################
#
# If this setting is set to "yes", service information will be published with
# Zeroconf / Avahi.
#
#zeroconf_enabled		"yes"
#
# The argument to this setting will be the Zeroconf / Avahi unique name for
# this MPD server on the network.
#
#zeroconf_name			"Music Player"
#
###############################################################################


# Permissions #################################################################
#
# If this setting is set, MPD will require password authorization. The password
# can setting can be specified multiple times for different password profiles.
#
#password                        "password@read,add,control,admin"
#
# This setting specifies the permissions a user has who has not yet logged in. 
#
#default_permissions             "read,add,control,admin"
#
###############################################################################


# Input #######################################################################
#

input {
        plugin "curl"
#       proxy "proxy.isp.com:8080"
#       proxy_user "user"
#       proxy_password "password"
}

#
###############################################################################

# Audio Output ################################################################
#
# MPD supports various audio output types, as well as playing through multiple 
# audio outputs at the same time, through multiple audio_output settings 
# blocks. Setting this block is optional, though the server will only attempt
# autodetection for one sound card.
#
# See <http://mpd.wikia.com/wiki/Configuration#Audio_Outputs> for examples of 
# other audio outputs.
#
# An example of an ALSA output:
#
audio_output {
	type		"alsa"
	name		"My ALSA Device"
	device		"hw:0,0"	# optional
	format		"44100:16:2"	# optional
	mixer_type      "hardware"	# optional
	mixer_device	"default"	# optional
	mixer_control	"PCM"		# optional
	mixer_index	"0"		# optional
}
#
# An example of an OSS output:
#
#audio_output {
#	type		"oss"
#	name		"My OSS Device"
##	device		"/dev/dsp"	# optional
##	format		"44100:16:2"	# optional
##	mixer_type      "hardware"	# optional
##	mixer_device	"/dev/mixer"	# optional
##	mixer_control	"PCM"		# optional
#}
#
# An example of a shout output (for streaming to Icecast):
#
#audio_output {
#	type		"shout"
#	encoding	"ogg"			# optional
#	name		"My Shout Stream"
#	host		"localhost"
#	port		"8000"
#	mount		"/mpd.ogg"
#	password	"hackme"
#	quality		"5.0"
#	bitrate		"128"
#	format		"44100:16:1"
##	protocol	"icecast2"		# optional
##	user		"source"		# optional
##	description	"My Stream Description"	# optional
##	genre		"jazz"			# optional
##	public		"no"			# optional
##	timeout		"2"			# optional
##	mixer_type      "software"		# optional
#}
#
# An example of a recorder output:
#
#audio_output {
#	type		"recorder"
#	name		"My recorder"
#	encoder		"vorbis"		# optional, vorbis or lame
#	path		"/var/lib/mpd/recorder/mpd.ogg"
##	quality		"5.0"			# do not define if bitrate is defined
#	bitrate		"128"			# do not define if quality is defined
#	format		"44100:16:1"
#}
#
# An example of a httpd output (built-in HTTP streaming server):
#
#audio_output {
#	type		"httpd"
#	name		"My HTTP Stream"
#	encoder		"vorbis"		# optional, vorbis or lame
#	port		"8000"
##	quality		"5.0"			# do not define if bitrate is defined
#	bitrate		"128"			# do not define if quality is defined
#	format		"44100:16:1"
#	max_clients	"0"			# optional 0=no limit
#}
#
# An example of a pulseaudio output (streaming to a remote pulseaudio server)
#
#audio_output {
#	type		"pulse"
#	name		"My Pulse Output"
##	server		"remote_server"		# optional
##	sink		"remote_server_sink"	# optional
#}
#
## Example "pipe" output:
#
#audio_output {
#	type		"pipe"
#	name		"my pipe"
#	command		"aplay -f cd 2>/dev/null"
## Or if you're want to use AudioCompress
#	command		"AudioCompress -m | aplay -f cd 2>/dev/null"
## Or to send raw PCM stream through PCM:
#	command		"nc example.org 8765"
#	format		"44100:16:2"
#}
#
## An example of a null output (for no audio output):
#
#audio_output {
#	type		"null"
#	name		"My Null Output"
#	mixer_type      "none"			# optional
#}
#
# This setting will change all decoded audio to be converted to the specified
# format before being passed to the audio outputs. By default, this setting is
# disabled.
#
#audio_output_format		"44100:16:2"
#
# If MPD has been compiled with libsamplerate support, this setting specifies 
# the sample rate converter to use.  Possible values can be found in the 
# mpd.conf man page or the libsamplerate documentation. By default, this is
# setting is disabled.
#
#samplerate_converter		"Fastest Sinc Interpolator"
#
###############################################################################


# Normalization automatic volume adjustments ##################################
#
# This setting specifies the type of ReplayGain to use. This setting can have
# the argument "off", "album" or "track". See <http://www.replaygain.org>
# for more details. This setting is off by default.
#
#replaygain			"album"
#
# This setting sets the pre-amp used for files that have ReplayGain tags. By
# default this setting is disabled.
#
#replaygain_preamp		"0"
#
# This setting enables on-the-fly normalization volume adjustment. This will
# result in the volume of all playing audio to be adjusted so the output has 
# equal "loudness". This setting is disabled by default.
#
#volume_normalization		"no"
#
###############################################################################


# MPD Internal Buffering ######################################################
#
# This setting adjusts the size of internal decoded audio buffering. Changing
# this may have undesired effects. Don't change this if you don't know what you
# are doing.
#
#audio_buffer_size		"2048"
#
# This setting controls the percentage of the buffer which is filled before 
# beginning to play. Increasing this reduces the chance of audio file skipping, 
# at the cost of increased time prior to audio playback.
#
#buffer_before_play		"10%"
#
###############################################################################


# Resource Limitations ########################################################
#
# These settings are various limitations to prevent MPD from using too many
# resources. Generally, these settings should be minimized to prevent security
# risks, depending on the operating resources.
#
#connection_timeout		"60"
#max_connections		"10"
#max_playlist_length		"16384"
#max_command_list_size		"2048"
#max_output_buffer_size		"8192"
#
###############################################################################


# Character Encoding ##########################################################
#
# If file or directory names do not display correctly for your locale then you 
# may need to modify this setting.
#
filesystem_charset		"UTF-8"
#
# This setting controls the encoding that ID3v1 tags should be converted from.
#
id3v1_encoding			"UTF-8"
#
###############################################################################
```


... las capturas del problema . .
sonata
[[img]http://j.imagehost.org/t/0673/Pantallazo.jpg[/img]](http://j.imagehost.org/view/0673/Pantallazo)

carpeta de la musica
[[img]http://j.imagehost.org/t/0076/Pantallazo-1.jpg[/img]](http://j.imagehost.org/view/0076/Pantallazo-1)

preferencias
[[img]http://j.imagehost.org/t/0376/Pantallazo-2.jpg[/img]](http://j.imagehost.org/view/0376/Pantallazo-2)


sigue sin cargar la biblioteca :S

---

### Post by leonardomdq on 2010-03-28
> **Mustaine666 said:**
> 

carpeta de la musica
[[IMG]http://j.imagehost.org/t/0076/Pantallazo-1.jpg[/IMG]]("http://j.imagehost.org/view/0076/Pantallazo-1")

Por lo que veo dentro de esas capetas tenes mas carpetas no?
osea si tenes subcarpetas no las vas a ver en la biblioteca, mira mi directorio de música:

[[img]http://j.imagehost.org/t/0226/Pantallazo.jpg[/img]](http://j.imagehost.org/view/0226/Pantallazo)

---

### Post by Mustaine666 on 2010-03-28
claro lo tenia en subcarpetas..  ahora lo deje asi.. 

[[img]http://j.imagehost.org/t/0773/Pantallazo.jpg[/img]](http://j.imagehost.org/view/0773/Pantallazo).. reinicio.. y cuento como me fue..

---

### Post by Mustaine666 on 2010-03-28
Nada.. sigue sin cargar la biblioteca.. saque todos los cd.. de los directorios.. y deje los cds sueltos..  dentro de la carpeta musica..

---

### Post by leonardomdq on 2010-04-14
Actualizado ;)

---

### Post by NauTiluS1 on 2010-09-28
muy bueno el tutorial amigo.

se que la sigte. pregunta no va con el tema, pero me puedes decir como se llama el tema que estas usando en el pantallazo.

---

### Post by shini-kire on 2011-04-05
No me lee los directorios :/ nada de nada.

---

