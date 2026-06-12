---
title: "[SOLVED] Configuracion Proxy Synaptic Package Manager"
date: 2009-08-14
forum: Software
---

### Post by juandeargentina on 2009-08-14
Ubunteros, buenas tardes, 

Tengo Xubuntu Jaunty y tengo el siguiente problema (exactamente este ([http://ubuntuforums.org/showthread.php?t=773902](http://ubuntuforums.org/showthread.php?t=773902))

Instale NTLMAPS todo bien pero me consumia mucha memoria lo desinstale y anda todo bien excepto que el gestionador de paquetes Synaptic me sigue apareciendo como que tengo la configuración del proxy (aclaro que ahora esta en 'direct connection...').

Por lo que googlee esto es un bug no corregido? Si es asi, como upgradeo mi sistema ahora??

Les tiro el mensaje de error....

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)

Por otro lado apt.conf esta vacío. No se que mas hacer....ya me frustré. :(

Gracias de antemano.

---

### Post by guillermolisi on 2009-08-14
Si no usas mas proxy no te hace falta ese archivo.

Revise en dos de mis maquinas que no usan proxy y compare contra la que uso en el trabajo, que si lo usa, y esta solamente en la ultima.

No estara mal la configuracion en la PC habiendole quedado configurado un proxy general que ya no se usa ?

Todo esto suponiendo que salis directo a Internet

---

### Post by juandeargentina on 2009-08-14
> **guillermolisi said:**
> Si no usas mas proxy no te hace falta ese archivo.

Revise en dos de mis maquinas que no usan proxy y compare contra la que uso en el trabajo, que si lo usa, y esta solamente en la ultima.

No estara mal la configuracion en la PC habiendole quedado configurado un proxy general que ya no se usa ?

Todo esto suponiendo que salis directo a Internet

Guillermo, antes que nada gracias por responder. 

En realidad puedo navegar perfecto, puedo conectarme con el Pidgin a cualquier lado...el tema es con Synaptic.

En el link que yo mandé, lo mismo que le pasa al flaco ese me pasa a mí. Esta confirmado que es un bug, porque si pones que salis directo a internet y todavia aparece el proxy es que evidentemente es un error, no hay mucha ciencia en eso.

Mi unica esperanza es que el proxy este configurado a "nivel sistema" :confused:

Por otro lado me cuesta creer que no haya un workaround, por lo menos por parte de la gente de Canonical. Esto IMHO, es un bug gravisimo. Me fije en launchpad (aunque no estoy seguro si lo hice bien) y hace como 2 meses que tienen ese error. ¿Que pasa si hay una actualización de urgencia?

Me imagino que estoy equivocado, por eso es que acudo (ya un poco desesperado) a este foro, no me gusta j***r. 

Saludos

---

### Post by staar on 2009-08-14
pregunta, si actualizas tu sistema con aptitude o apt-get el problema aparece? o es solo con Synaptic?

saludos

---

### Post by juandeargentina on 2009-08-14
> **staar said:**
> pregunta, si actualizas tu sistema con aptitude o apt-get el problema aparece? o es solo con Synaptic?

saludos

Gracias por responder...

Si, me aparece "exactamente" el mismo error.

---

### Post by Hei Ku on 2009-08-14
sudo rm /etc/apt/apt.conf

Y si esto te pone nervioso, te recomiendo paciencia, y moderacion.

---

### Post by juandeargentina on 2009-08-14
> **Hei Ku said:**
> sudo rm /etc/apt/apt.conf

Y si esto te pone nervioso, te recomiendo paciencia, y moderacion.

Gracias Hei por responder, pero no, no funciono.

Se puede "reinstalar" Synaptic? Podra ser eso la clave para la solución?

Sds

---

### Post by Hei Ku on 2009-08-14
Corriste "sudo apt-get update" despues de borrar el archivo?

---

### Post by juandeargentina on 2009-08-14
> **Hei Ku said:**
> Corriste "sudo apt-get update" despues de borrar el archivo?

No, perdon pero no me imagine que tenía que hacer eso, si corri el Synaptic y me dió el mismo error.

Despues de que leí tu mensaje de ahora repeti los pasos y sigue igual.

Gracias de nuevo por tu ayuda.

---

### Post by Hei Ku on 2009-08-14
Pega exacto el error

---

### Post by juandeargentina on 2009-08-14
> **Hei Ku said:**
> Pega exacto el error

te paso

=================================================================
guyfawkes@ubuntu:~$ sudo apt-get update
[sudo] password for guyfawkes: 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release.gpg
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Translation-en_US
  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/jaunty/Release.gpg](http://wine.budgetdedicated.com/apt/dists/jaunty/Release.gpg)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/jaunty/main/i18n/Translation-en_US.bz2](http://wine.budgetdedicated.com/apt/dists/jaunty/main/i18n/Translation-en_US.bz2)  Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
guyfawkes@ubuntu:~$ 
======================================================================
es esto no?

---

### Post by guillermolisi on 2009-08-14
es esto lo que esta mal y es un resabio del producto que tenias instalado
> 127.0.0.1:5865

apunta a la misma PC (esa direccion IP es la maquina misma, localhost) y usa el port TCP 5865 que seguramente usaba antes para gestionar las conexiones via ese producto desinstalado (o solo borrado de archivos ?).

Como desinstalaste ese producto ?

---

### Post by juandeargentina on 2009-08-14
> **guillermolisi said:**
> es esto lo que esta mal y es un resabio del producto que tenias instalado


apunta a la misma PC (esa direccion IP es la maquina misma, localhost) y usa el port TCP 5865 que seguramente usaba antes para gestionar las conexiones via ese producto desinstalado (o solo borrado de archivos ?).

Como desinstalaste ese producto ?

el producto (ya lo dije pero por las dudas lo repito) es NTLMAPS.

A rigor de verdad no recuerdo muy bien pero no fue borrando archivos (recuerden que yo soy un newbie :) )

el comando que utilice fue este
sudo apt-get remove ntlmaps
(y todo salio sin errores)

Una aclaración que creo importante es que no es un problema del ntlmaps porque si fuere asi tampoco me funcionaria el Firefox o cualquier aplicación que salga por internet. 

Aparte, y esto si es claro, si en la configuración del programa pongo "direct connection..." tiene que funcionar tal como pasa cuando sacas el proxy en Firefox.

---

### Post by Hei Ku on 2009-08-14
Podes confirmar que ya no está funcionando? Reiniciaste la maquina desde que lo desinstalaste?

Anda a la carpeta /etc/ntlmaps/ y fijate que no haya ningun archivo.

Si existe alguno, pone en una terminal: 

sudo rm -R /etc/ntlmaps/*

---

### Post by juandeargentina on 2009-08-14
> **Hei Ku said:**
> Podes confirmar que ya no está funcionando? Reiniciaste la maquina desde que lo desinstalaste?

Anda a la carpeta /etc/ntlmaps/ y fijate que no haya ningun archivo.

Si existe alguno, pone en una terminal: 

sudo rm -R /etc/ntlmaps/*

Hola gracias de nuevo por tu tiempo.

si, reinicie.

En la carpeta estaba el archivo de configuración (server.cfg). Hice lo que me dijiste y por un momento me ilusione...lamentablemente no funciono, sigue con el mismo error.

---

### Post by Hei Ku on 2009-08-14
Postea el resultado de esto:

cat ~/.bashrc

---

### Post by juandeargentina on 2009-08-14
> **Hei Ku said:**
> Postea el resultado de esto:

cat ~/.bashrc

Aqui va...

====================================================================
guyfawkes@ubuntu:~$ cat ~/.bashrc
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# don't overwrite GNU Midnight Commander's setting of `ignorespace'.
export HISTCONTROL=$HISTCONTROL${HISTCONTROL+,}ignoredups
# ... or force ignoredups and ignorespace
export HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
	# We have color support; assume it's compliant with Ecma-48
	# (ISO/IEC-6429). (Lack of such support is extremely rare, and such
	# a case would tend to support setf rather than setaf.)
	color_prompt=yes
    else
	color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    #alias grep='grep --color=auto'
    #alias fgrep='fgrep --color=auto'
    #alias egrep='egrep --color=auto'
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi
guyfawkes@ubuntu:~$
=========================================================================

---

### Post by Hei Ku on 2009-08-15
Acá no pareciera haber nada que apunte al proxy todavia. Una mas:

sudo cat /etc/apt/apt.conf.d/01proxy

En mi caso, ese archivo esta vacío, pero quizas quedó algo guardado y es lo que está molestando.

---

### Post by juandeargentina on 2009-08-15
> **Hei Ku said:**
> Acá no pareciera haber nada que apunte al proxy todavia. Una mas:

sudo cat /etc/apt/apt.conf.d/01proxy

En mi caso, ese archivo esta vacío, pero quizas quedó algo guardado y es lo que está molestando.

Bien...ahí no existe ese archivo...sin embargo encontre dos archivos parecidos.
proxy~
_proxy

el primero esta vacío.

el segundo...
guyfawkes@ubuntu:~$ sudo cat /etc/apt/apt.conf.d/_proxy
Acquire::http::Proxy "http://127.0.0.1:5865/";
guyfawkes@ubuntu:~$ 

procedi a borrar ambos y voila! problem solved!!

Muchas gracias a vos y Guillermo por su ayuda. Me quedan dos preguntas.

1) sabes o tenes idea que pudo ser?? ahora me queda la duda si no fui yo quien 'renombro' el archivo o algo parecido.

2) Como cierro este thread? tengo que editarlo y poner SOLVED o RESUELTO?

Probablemente moleste de nuevo cuando tenga que configurar el CNTLM

---

### Post by Hei Ku on 2009-08-15
El Synaptic no actualiza esta configuracion, y el apt.conf parece que actualiza cuando tiene una nueva configuracion, no cuando le sacas todo.

Con poner SOLVED en el titulo del thread alcanza, como hiciste ahora.

---

### Post by juandeargentina on 2009-08-15
> **Hei Ku said:**
> El Synaptic no actualiza esta configuracion, y el apt.conf parece que actualiza cuando tiene una nueva configuracion, no cuando le sacas todo.

Con poner SOLVED en el titulo del thread alcanza, como hiciste ahora.

cosa e' mandinga!! yo no puse Solved en el titulo. pero bueno ahi esta.

muchas gracias nuevamente. buenfinde.

---

