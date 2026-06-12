---
title: "UK ISDN with B410P on Ubuntu 10.04 server (64 bit) with Asterisk"
date: 2010-08-01
forum: Server Platforms
---

### Post by bryhhh on 2010-08-01
I've been having awful trouble getting our company's Asterisk system up and running on Ubuntu 10.04. It has taken two of us (not including the very kind Digium support person who spent a lot of time trying to help us resolve this issue) a couple of weeks solid trying to get this working without success. I've done more Googling than I care to remember, and found very little in the way of help for this set up, but now that I've resolved it, I'm posting this, in the hope that it might help someone else with a similar set up.

_Our scenario._

[LIST]
[*]We have 2 ISDN lines (4 voice channels).
[*]A dedicated Dell Power Edge Server.
[*]A Digium B410P card with hardware echo cancellation.
[*]And a number of Polycom 335 Soundpoint IP phones.
[/LIST]

_Scope_

I'm not going to cover the provisioning of phones here, nor am I going to cover the configuration of asterisk, as this has already been covered at numerous other sites.

_Install the Operating System_

I don't need to detail this part, other than to say, the only component I select during the install is the SSH Server. I did have a problem on the server I have, in that I had to modify grub.cfg, because without the modification, Ubuntu would not boot on the server. To correct this I had to add the parameter rootdelay=120 to the kernel options. I did this just as the installation finished by issuing the following commands:

```
mv /target/boot/grub/grub.cfg /target/boot/grub/grub.cfg.org
sed -e 's/quiet/quiet rootdelay=120/' /target/boot/grub/grub.cfg.org > /target/boot/grub/grub.cfg
```

DHCP had autoconfigured the network interface, so I also had to edit /etc/network/interfaces to give the system a static IP.

_Installation of prerequisite software_

The polycom phones by default use FTP to download their configuration. Having toyed with using TFTP, I decided to stick with FTP, so I used proftpd-basic as the FTP server. **Notice that I don't install libpri from the Ubuntu repositories - this omission is critical.**

```
apt-get update
apt-get install debconf-utils
echo proftpd-basic shared/proftpd/inetd_or_standalone select standalone | debconf-set-selections
apt-get install proftpd-basic build-essential libxml2-dev ncurses-dev bison flex libnewt-dev
```

_Installation of Dahdi Drivers and Tools_

```

cd /usr/src/
wget http://downloads.asterisk.org/pub/telephony/dahdi-linux-complete/releases/dahdi-linux-complete-2.3.0.1+2.3.0.tar.gz
tar -xzf dahdi-linux-complete-2.3.0.1+2.3.0.tar.gz
cd dahdi-linux-complete-2.3.0.1+2.3.0/linux/
make
make install
cd ../tools/
./configure
make
make install
make config
dahdi_genconf modules

```

_Install Libpri_

```

cd /usr/src/
wget http://downloads.asterisk.org/pub/telephony/libpri/libpri-1.4.11.3.tar.gz
tar -xzf libpri-1.4.11.3.tar.gz
cd libpri-1.4.11.3
make
make install

```

_Install Asterisk_

```

cd /usr/src/
wget http://downloads.asterisk.org/pub/telephony/asterisk/releases/asterisk-1.6.2.9.tar.gz
tar -xzf asterisk-1.6.2.9.tar.gz
cd asterisk-1.6.2.9
./configure
make
make install
make samples

```

_Configure Asterisk to start at boot_

```
sed -i 's/exit 0//' /etc/rc.local
echo 'asterisk &' >> /etc/rc.local
echo 'exit 0' >> /etc/rc.local

```

_Configure the B410P card_

For my setup, the following are the configurations files that I'm using

**/etc/asterisk/chan_dahdi.conf**

```

[trunkgroups]

[channels]
language=en
switchtype=euroisdn
usecallerid=yes
cidsignalling=v23
callwaiting=no
usecallingpres=yes
callwaitingcallerid=yes
threewaycalling=no
transfer=no
canpark=no
cancallforward=no
callreturn=yes
echocancel=yes
echocancelwhenbridged=no
;pridialplan=dynamic
pridialplan=unknown
prilocaldialplan=dynamic
context=incoming
cid_number=01234567890
fullname=Some Company
group=1
callgroup=1
pickupgroup=1
signalling=bri_cpe
channel => 1,2,4,5

```

**/etc/dahdi/system.conf**

```

span= 1,1,0,ccs,ami
bchan = 1,2
hardhdlc = 3
span=2,2,0,ccs,ami
bchan = 4,5
hardhdlc = 6
loadzone = uk
defaultzone=uk

```

At this point, you will need to have configured your own dialplan to suit your own requirements, then reboot the system, before logging on and issuing the following command

```

sudo dahdi_cfg -vvv

```

At this point, the system seemed to require a further reboot, but after that, when you launch the asterisk console, issue the following commands, and you should see asterisk detecting the lines connected to your card.

```

asterisk -rvvv
dahdi show status
dahdi show channels

```

Test from another phone making a call to the ISDN number. If your dialplans are correct, your phones will ring, if not you will see a message on the asterisk console telling you it wasn't able to handle the incoming call.

Initially when I tried to get asterisk working with the B410P, I didn't receive any message on the asterisk console, nor did any phones ring. This was due to me using the Ubuntu packaged version of libpri. Compiling from source, as per these instructions resolved the problem for me.

---

