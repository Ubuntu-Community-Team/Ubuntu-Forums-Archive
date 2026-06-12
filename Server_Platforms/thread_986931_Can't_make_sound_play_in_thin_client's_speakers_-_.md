---
title: "Can't make sound play in thin client's speakers - LTSP 4.2 on Edubuntu 7.10"
date: 2008-11-19
forum: Server Platforms
---

### Post by nestort on 2008-11-19
Hi all,

I have a problem trying to get sound at thin clients connected to a server that runs Edubuntu 7.10 with LTSP 4.2. I have downloaded and installed the packages LTSP-esd-alsa_1.0.0-2.tgz and ltsp-sound-1.0-0.2.tar.bz2, as recommended in [http://wiki.ltsp.org/twiki/bin/view/Ltsp/WorkInProgress#esd_ALSA_sound_on_LTSP_4_2](http://wiki.ltsp.org/twiki/bin/view/Ltsp/WorkInProgress#esd_ALSA_sound_on_LTSP_4_2) and the LTSP Sound Twiki in [http://www.ltsp.org/twiki/bin/view/Ltsp/Sound](http://www.ltsp.org/twiki/bin/view/Ltsp/Sound) .
The thing is, once I have installed these files, gdm crashes immediately after graphic login, with the surprising following error:
```

/etc/gdm/Xsession: Beginning session setup...
/etc/ltsp-sound.sh: 49: Syntax error: "(" unexpected (expecting "fi")

```
Now, I've seen that this script is called in /etc/profile, at the end. I have also seen that this script in particular starts with #!/bin/sh and that, if I use bash instead, there is no more syntax error message, although gdm crashes equally.
Moreover, this ltsp-sound.sh script is called in /etc/profile just after a umask 022 command.
And even another strange thing: if I just put an "exit 0" at the very beginning of ltsp-sound.sh, gdm still crashes the same way.
Preventing ltsp-sound.sh from loading lets gdm work fine but I can't make the sound played by a thin client sound through its loudspeakers -- it sounds through the server's.
I have also put the following code in /etc/X11/Xsession as said in the sound twiki:

```

REMOTE_X11=${DISPLAY%:*}
 if test "$REMOTE_X11" == ""
 then
  export REMOTEX_11=false
 else
  export ESPEAKER=$REMOTE_X11:16001
  export ESDDSP_MIXER=1
  export LD_PRELOAD="/usr/lib/libesddsp.so.0 /usr/lib/libesd.so.0 $LD_PRELOAD"
  export REMOTE_X11=true
 fi

```

I've added this code just before the code that sources every file in the session directory via run-parts function

I don't know how to go on now: the script that causes the syntax error is supposed to make work sound on thin clients through ALSA. Without it but with the modified /etc/X11/Xsession sound should also work. I have tried setting the sound output (System->Preferences->Sound) through ALSA, ESD and OSS at no avail...

By the way, the thin client does sucessfully load its sound server according to one of the messages during boot.

Any ideas? Am I doing something completely wrong??
Thank you in advance

Néstor

---

### Post by nestort on 2008-12-11
Well, just to keep this thread alive and to ask if there is something wrong with my specification of the problem. This is the first time I post a thread here and maybe I have not been accurate enough. Or maybe chaotic? :confused:
Thanks!!

---

### Post by nestort on 2009-01-26
OK, after trying a lot, I think I have solved the issue... These are the steps to follow:
- Download, uncompress and install (as root or with sudo) both LTSP-esd-alsa_1.0.0-2.tgz and ltsp-sound-1.0-0.2.tar.bz2
- Install esound package
- Make sure /etc/ltsp-sound.sh has 755 permissions
- Finally, edit /etc/ltsp-sound.sh and make it like the following:
```

#!/bin/sh

# This is the server-side sound script for LTSP-4.1.  It will setup your
# environment to feed a sound stream to the LTSP client.
#
# This was originally written by Andrew Williams, but has been modified
# by Richard June and James McQuillan to work with LTSP-4.1.
#
# This package is released under the auspices of the GPL
# Copyright (c) 2002 by Andrew Williams (Vartech Solutions)
# Permission is hereby granted, free of charge, to any person obtaining a
# copy of this software and associated documentation files (the "Software"),
# to deal in the Software without restriction, including without limitation
# the rights to use, copy, modify, merge, publish, distribute, sublicense,
# and/or sell copies of the Software, and to permit persons to whom the
# Software is furnished to do so, subject to the following conditions:
#
# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESSED OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL
# VARTECH SOLUTIONS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
# WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF
# OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.
#
################################################################################
# We support ESD and NAS directly, MAS support is planned next. If you want to #
#   use arts with ltsp, you need to use NAS, then tell arts to output to NAS   #
#   for full information, see http://www.ltsp.org/sound/                       #
################################################################################

# Aquesta linia esta per a eliminar errors:

#exit 0

# i aqui continua l'arxiu original 
#(excepte la 1a linia que esta canviada a /bin/bash enlloc de /bin/sh

DOMAIN=`dnsdomainname`

#comentada perque genera un error!! (la instruccio sed, que no se que coi fa!)
#MYNAME=`echo $DISPLAY | cut -d: -f1 | sed s/\\\.${DOMAIN}//`
MYNAME=`echo $DISPLAY | cut -d: -f1`



#if afegit per mi. no se com va, de fet


echo MYNAME-$MYNAME >>$HOME/ltsp-sound-meu.log

#atencio: MYNAME no agafa localhost si som al servidor, ja que DISPLAY, si som el servidor, val :0.0
#de fet, esta be: -n significa que TRUE si la cadena no te longitud zero; -a significa AND logic
if [ -n "${MYNAME}" -a "${MYNAME}" != "localhost" ]; then
  #
  # Usage:  get_cfg PARM [DEFAULT]
  #
  #atencio: he eliminat la paraula function perque sembla que no cal...
  get_cfg () {
    VALUE=`/usr/bin/ltspinfo \
               -h ${MYNAME}      \
               -c $1`
    if [ "$#" -gt 1 -a -z "${VALUE}" ]; then
      echo $2
    else
      echo ${VALUE}
    fi
	
    unset VALUE
  }

  eval `get_cfg SOUND`
  if [ "$LTSP_SOUND" = "Y" ] ; then
    eval `get_cfg SOUND_DAEMON`
    case "${LTSP_SOUND_DAEMON}" in
      esd)   REMOTESOUNDIP=`echo $DISPLAY | cut -d: -f1`
             REMOTESOUNDPORT="16001"
             LIBESDPATH="/usr/lib/libesd.so.0"
             LIBESDDSPPATH="/usr/lib/esound/libesddsp.so.0"
		echo REMOTESOUNDIP-$REMOTESOUNDIP >>$HOME/ltsp-sound-meu.log

             #
             # if netcat is installed, we'll check to see if the
             # terminal is listening
             #
             if [ "$REMOTESOUNDIP" -a -x "`which nc 2> /dev/null`" ]; then
               NC=`/bin/nc -v -w 1 -z -n $REMOTESOUNDIP $REMOTESOUNDPORT 2>&1 \
                   | grep -v open$`
		echo NC=$NC
               if [ "${NC}" ]; then
                 #
                 # netcat says the terminal is not listening, bail!
                 #
			#touch $HOME/bailout.log
                 unset REMOTESOUNDIP
                 unset REMOTESOUNDPORT
                 unset LIBESDPATH
                 unset LIBESDDSPPATH
               fi
             fi

             #
             # don't use this hack for local X sessions, root, and only if
             # the pre-load libraries are found
             #
             if [      "${REMOTESOUNDIP}" \
                 -a -x "$LIBESDPATH"      \
                 -a -x "$LIBESDDSPPATH" ]
             then
		echo "ara els 3 exports" >>$HOME/ltsp-sound.log
               export ESPEAKER=${REMOTESOUNDIP}:16001
               export ESDDSP_MIXER=1
               export LD_PRELOAD="$LIBESDPATH $LIBESDDSPPATH"
               /usr/bin/esdctl unlock
             fi
             #
             # clean up temporary variables
             #
             unset REMOTESOUNDIP
             unset REMOTESOUNDPORT
             unset LIBESDPATH
             unset LIBESDDSPPATH
             ;;

      nasd)  LIBAUDIO=/usr/X11R6/lib/libaudiooss.so.1
             if [ -f ${LIBAUDIO} ]; then
               if [ `echo "${LD_PRELOAD}" | grep -c ${LIBAUDIO}` ]; then
                 export LD_PRELOAD="${LIBAUDIO}"
               else
                 export LD_PRELOAD="${LIBAUDIO} ${LD_PRELOAD}"
               fi
             fi
             export AUDIOSERVER="$DISPLAY"

             #
             # Uncomment the following to enable this to work with "wine"
             # This also works well with the Linux ICA client.
             #    export AUDIOOSS_WINE_HACK="y"
             ;;

      rplay) export LD_PRELOAD="/usr/local/lib/devrplay.so"
             ;;

      *)     #
             # No more options available get on with Life
             #
             ;;
    esac
  fi
fi

unset DOMAIN
unset MYNAME
unset get_cfg


```

That worked for me! :guitar: Quite wierd indeed to have to manually edit that script, but... 

So, this should be tagged as Solved. Although I don't know how...

---

