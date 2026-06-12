---
title: "D-BUS: JACK server could not be started"
date: 2013-05-30
forum: Ubuntu Studio
---

### Post by drumanart on 2013-05-30
After running MEAPSOFT I QjackCtl want run anymore.

The error I get: D-BUS: JACK server could not be started

I followed this threat with no success. [http://trac.jackaudio.org/wiki/WalkThrough/User/PulseOnJack](http://trac.jackaudio.org/wiki/WalkThrough/User/PulseOnJack)

If I log in as guest QjackCtl starts without errors.


Typing the command: fgrep -ie 'audio' /etc/group
Output:
audio:x:29:pulse,drumanart,timidity

Typing the command: cat /proc/asound/cards
Output: 
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xdbef8000 irq 22



Typing the command: getfacl /dev/snd/
Output:
drumanart@drumanart:~$ getfacl /dev/snd/* 
getfacl: Removing leading '/' from absolute path names
# file: dev/snd/by-path
# owner: root
# group: root
user::rwx
group::r-x
other::r-x

# file: dev/snd/controlC0
# owner: root
# group: audio
# flags: --t
user::rw-
user:drumanart:rw-
group::rw-
mask::rw-
other::---

# file: dev/snd/hwC0D0
# owner: root
# group: audio
# flags: --t
user::rw-
user:drumanart:rw-
group::rw-
mask::rw-
other::---

# file: dev/snd/pcmC0D0c
# owner: root
# group: audio
# flags: --t
user::rw-
user:drumanart:rw-
group::rw-
mask::rw-
other::---

# file: dev/snd/pcmC0D0p
# owner: root
# group: audio
# flags: --t
user::rw-
user:drumanart:rw-
group::rw-
mask::rw-
other::---

# file: dev/snd/pcmC0D1p
# owner: root
# group: audio
# flags: --t
user::rw-
user:drumanart:rw-
group::rw-
mask::rw-
other::---

# file: dev/snd/pcmC0D2c
# owner: root
# group: audio
# flags: --t
user::rw-
user:drumanart:rw-
group::rw-
mask::rw-
other::---

# file: dev/snd/seq
# owner: root
# group: audio
# flags: --t
user::rw-
user:drumanart:rw-
group::rw-
mask::rw-
other::---

# file: dev/snd/timer
# owner: root
# group: audio
# flags: --t
user::rw-
user:drumanart:rw-
group::rw-
mask::rw-
other::---

Thanks Martin

---

### Post by zequence on 2013-05-30
All you need in order to run pulseaudio on top of jack on Ubuntu, is to install jackd2 and pulseaudio-module-jack (the module will be loaded when you restart pulseaudio).

Starting jackdbus will then make the module load jack sink and source automatically. If you prefer jackd, you'll need to load the sink and source manually, using pactl (see pactl --help for details).

On Ubuntu Studio, all of this is set up by default. So, if you start jack using qjackctl, PA will autoconnect to jack.

---

### Post by drumanart on 2013-05-30
jackd2 and pulseaudio-module-jack are already the newest versions. I had QjackCtl running before I used MEAPSOFT.
Cheers

---

### Post by zequence on 2013-05-30
meapsoft won't mess up your jack or system settings
If you want to start from scratch, create a new user who has admin rights. Add that user to audio group (to get realtime privilege): 

```
sudo usermod -a -G audio $USER
```

login as the new user, start qjackctl

---

### Post by drumanart on 2013-05-31
Ok, with a new user account QjackCtl works. But is it also possible to make QjackCtl work again as it was before? I really don't understand what went wrong. Somehow it is a permission problem as QjackCtl works as guest and as well with a new created user-account.
Thanks Martin

---

### Post by drumanart on 2013-05-31
I reinstall Jack with:

I reinstalkled jacj:
sudo apt-get install jack-tools ant openjdk-6-jdk fftw3 qjackctl

and if I strat jackd first: 
jackd -r -d alsa -r 44100

QjackCtl opens without error.


Martin

---

### Post by zequence on 2013-05-31
I don't think it is permission related, but more so on user configuration files in the user home folder. If you did some changes, you probably messed something up. 
Creating a new user also made sure all the user settings were at default. The same with guest.

The default setup on Ubuntu Studio works just fine. You only need to learn how to configure jack for what you want to use it for.

---

