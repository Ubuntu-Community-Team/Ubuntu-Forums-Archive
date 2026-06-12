---
title: "uPnP - uShare and Xbox 360 problems"
date: 2010-11-29
forum: Server Platforms
---

### Post by floatingpoint on 2010-11-29
Hello, hope this is the right forum.

I've installed uShare on my Ubuntu Server, but I can't see it from my Xbox.

My ushare.conf file looks like this

```

USHARE_NAME=mediaserver
USHARE_IFACE=eth0
USHARE_PORT=
USHARE_TELNET_PORT=
USHARE_DIR=/media
USHARE_OVERRIDE_ICONV_ERR=
USHARE_ENABLE_WEB=yes
USHARE_ENABLE_TELNET=
USHARE_ENABLE_XBOX=yes
USHARE_ENABLE_DLNA=
```

The server is hard-wired to the router, and the Xbox 360 connects through my MacBook Pro (which connects wirelessly to the router), I have a feeling this has something to do with the problem.

Any thoughts?

---

### Post by yettiman2208 on 2010-11-29
a few of your options are not specified from that source.


there should be a number following the "port=" line.

also specify the line "enable_dlna=" with a no at the end. my understanding is that you need to specify a lot of these settings.

google ushare xbox 360 setup to get common setup files.

---

### Post by Kluttz on 2010-11-29
I strongly suggest to ditch uShare and go with miniDLNA.
I first started off with uShare and quickly look for others are it was not good at all.

There are some others available list here: [LINK]("http://en.wikipedia.org/wiki/List_of_streaming_media_systems")

I have been using MiniDLNA for the last few months and its been great.
- Free
- Auto updates content 
- uses little resource
- can access videos, music and images.

To install on ubuntu...

sudo apt-get -y install libavutil-extra-49 libavcodec-extra-52 libavformat-extra-52
sudo apt-get -y install libavutil-dev libavcodec-dev libavformat-dev libflac-dev libvorbis-dev libid3tag0-dev libexif-dev libjpeg62-dev libsqlite3-dev
sudo apt-get install cvsnt
cd /tmp
cvs -z3 -d:pserver:anonymous@minidlna.cvs.sourceforge.net:/cvsroot/minidlna co -P minidlna
cd minidlna
sudo make
sudo make install
sudo cp linux/minidlna.init.d.script /etc/init.d/minidlna
sudo chmod 755 /etc/init.d/minidlna
sudo update-rc.d minidlna defaults
sudo nano /etc/minidlna.conf
(make your changes you need to for your network)
sudo /etc/init.d/minidlna start

all the configuration can be found in '/etc/minidlna.conf'

Good Luck

---

### Post by devind25 on 2011-05-18
Ok I know this is old but hopefully someone can assist me. For some reason when I get to this part: sudo cp linux/minidlna.init.d.script /etc/init.d/minidlna
It tells me that 
```
cp: missing destination file operand after `linux/minidlna.init.d.script/etc/init.d/minidlna'
Try `cp --help' for more information.

```
Can anyone tell me why it is telling me that? Because if I could get past that step then I could edit the config file to my liking. Any help is appreciated.

---

### Post by devind25 on 2011-05-22
Really? Nobody has any suggestions?

---

### Post by devind25 on 2011-05-22
Ok I fixed the problem and edited the config file but when I go to start the service it says fail. Everything looks right in the config file. Now what am I doing wrong?

---

### Post by devind25 on 2011-05-22
Ok problem is now fixed. Just had to restart computer.

---

### Post by dawer on 2011-05-29
Kluttz,

Thanks for this guide which i have been trying to follow. Im very new to Ubunto so please forgive me. I get too "cvs -z3 -d:razz:server:anonymous@minidlna.cvs.sourceforge.net:/cvsroot/minidlna co -P minidlna " but am then asked for a password. "server@minidlna.cvs.sourceforge.net's password:" Am i missing something here? what is this password.

---

### Post by Kluttz on 2011-06-01
Wow I forgot about this thread.  I was not getting any notifications.

Interesting you were getting a password prompt.  I never did.

I haven't installed it since so I do not know.  I will have to test it out and let you know if I get the same error msg.

I will check my notes but Im pretty sure I copied/pasted them here.

Otherwise, they're others that are good to use such as  ps3mediaserver (from what I have read) and Twonkymedia.  Twonky is not free though.

---

