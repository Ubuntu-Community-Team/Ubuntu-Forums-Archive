---
title: "TFTP server problem"
date: 2007-11-21
forum: Server Platforms
---

### Post by davidgarcin on 2007-11-21
Hi all,
I'm having a problem getting a TFTP server to work correctly in Ubuntu Gusty.  I need it to transfer a binary memory image to a development board that will (eventually) be running uClinux, an embedded distro.

I installed xinetd, tftpd, and tftp as per this excellent how-to: [http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/](http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/).

I have a /tftpboot folder, and my /etc/xinetd.d/tftp is as follows:

service tftp
{
protocol        = udp
port            = 69
socket_type     = dgram
wait            = yes
user            = nobody

server          = /usr/sbin/in.tftpd
server_args     = -s /tftpboot
disable         = no
}

The board firmware settings are as follows (by all accounts, they are correct, and I don't really expect anyone here to have experience on this side of it, so just for FYI):
server: 192.168.1.101
client: 192.168.1.102
gateway: 127.0.0.1
netmask: 255.255.255.0
filename: image.bin
.....

The gateway setting is a little strange, but it doesn't seem like it should matter, and when using Windows w/ the TFTP-GUI server, it is necessary for things to work right.  And yes, I have tried setting the gateway to the router address (192.168.1.1).

The service seems to run fine, and when I run the network download command from the board via the terminal connection it connects to the TFTP server, but I get a 'file not found' error.  If I change the filename setting to /tftpboot/image.bin (which seems wrong),  I get an access denied error.....  I have set the permissions of /tftpboot and image.bin to global read/write access and 'nobody' owner with:

$ sudo chmod -R 777 /tftpboot
$ sudo chown -R nobody /tftpboot

Am I doing anything obviously wrong on the server side of things?  The board is a Freescale M5275EVB in case anyone is wondering.

Thanks,
-David

---

### Post by HermanAB on 2007-11-22
I can remember something about TFTP being VERY finicky about directory and file permissions.  This is a security precaution.  Since the protocol itself has none, it relies on the file system and refuses to do anything unless the permissions are set just right.  You have to read the man page for details.

---

### Post by steve.horsley on 2007-11-22
HermanAB is right about the server being picky. You might get a clue as to what's wrong if you run the server from the command line (and look at what it prints out). It looks like the command would be:
**/usr/sbin/in.tftpd -s /tftpboot**.
but you may get "address in use" problems unless you stop xinetd listening there first.

If if works from t command line but not from xinetd, suspect directory permissions. It needs to be readable by everybody (becase xinetd runs the server as user nobody).

---

### Post by livingtarget on 2007-11-22
Doing this myself at the moment with a LPC2292 board from Embedded Artists. I'm currently at the stage where uCLinux is running properly. This is my honours project by the way, doing something in the form of a home security system. I got TFTP boot to work on linux. 

Note I used tfpd-hpa which is not quite the same I think. I did stumble upon the same tutorial. 

From my project log:
> 
6/11/2007 Boot from TFTP
-> Set up TFTP server on linux
-> For ubuntu/debian:
sudo apt-get install tftpd-hpa (just the daemon not the client, I don't even have xinetd)
gksudo gedit /etc/default/tfpd-hpa
-> Change RUN_DAEMON="no" to RUN_DAEMON="yes"
-> Move the linux.bin and romfs.bin to /var/lib/tftpboot
-> Now (re)start the server
sudo /etc/init.d/tftp-hda restart
-> Verify IP address of the board with "printenv ipaddr", "printenv serverip", "printenv netmask"
-> In the UBoot terminal do:
tftpboot 81008000 linux.bin
tftpboot 81500000 romfs.bin
go 81008000
-> UC Linux boots!


I had a good link I found, but I forgot where it went.

My board is: 192.168.1.1 255.255.255.0
My computer is: 192.168.1.3 255.255.255.0 (static, using a different network card for this anyway)

Also a note I just linked the board and my computer without anything in between. So it's only talking to the board.

Hope it helps a bit, some may be specific to my board. Some may not. I had to use TFTP because it didn't recognise my kingston 1gb SD card, I've since got a SANDISK 256mb which is known to work. So I now have two valid boot methods. 

Also had insane troubles compiling a ucLinux kernel. Lots of manual patching involved from obscure mailing lists. So in the end I just stuck with a pre-compiled kernel for now.

If you want to co-operate & share know-how a bit, let me know. May come in handy in the future.

---

### Post by davidgarcin on 2007-11-22
Thanks for your responses, guys.  I have mucked around with the permissions a fair bit, and so I think my next step will be starting tftpd from the command line, as Steve suggests.  Of course, I'm home for the weekend and far away from my dev comp and board, so I won't be able to try anything until Monday.

@livingtarget:  I had also tried tftp-hpa at some point, but I think I got even less far (I don't think the board would even connect to the server).  I may give it a try again if I can't get anywhere with tftpd.  I also tried with a crossover cable, that gave me the same errors.  Your notes from tftp-hpa will be helpful if I go that route.

Out of curiosity, was UBoot factory-installed?  It sounds a lot more versatile than Freescale's dBug, that's for sure.  I would be happy to co-operate a bit in the future.  Thankfully, the uClinux kernel is ported to our specific dev board, so I haven't really had too much compilation trouble.  But yes, the obscure mailing lists are getting their share of mail from me too, uClinux-dev mostly.

I'll post the results of my tinkerings in a couple days.
-Dave

---

### Post by livingtarget on 2007-11-22
Hey Dave,

Uboot was not factory installed, you needed to flash the ROM to include it. My cpu (arm7) was made by philips (now called NXP) and they had a flash utility for Windows and there was a command line utility under Linux which I used to put UBoot on there. The command line utility also opens a terminal to the board, so you can input commands and read back from it through the serial port.

It might be more hassle than it's worth to switch over to UBoot once you're used to the other one. After all all it does is boot the device load a few drivers for Ethernet & MMC/SD and that's it.

Anyway here are links to the UBoot webpages if you are interested:
(old) [http://sourceforge.net/projects/u-boot](http://sourceforge.net/projects/u-boot)
new: [http://www.denx.de/wiki/UBoot/WebHome](http://www.denx.de/wiki/UBoot/WebHome)

only just realised the sourceforge page was a bit outdated, I think my Uboot is 1.1.6 which might be a bit out of date. Maybe I'll try and do a compile again soonish just for the sake of being up to date.

Is your board ARM architecture based at all?

---

### Post by davidgarcin on 2007-11-22
My board is for a Coldfire processor, which is based on the old 68k architecture from Motorola.  Functionally quite similar to ARM, but fairly different in implementation.

I'm looking at using UBoot in the future, because dBug only allows you to boot the board from 0x0 (bottom address for the flash, where dBug is installed) or halfway through the flash (I don't remember the address off the top of my head).  Halfway-through only gives me 1 MB to play with, so that doesn't work too well.  Right now I use dBug/tftp to write the uClinux image to RAM, then manually tell dBug to start execution at the beginning address for the kernel.  Eventually I'll have to have the image in flash, so I need something more versatile.

From what I can tell, UBoot doesn't officially support Coldfire, but I've heard of people getting it to work.  I might just end up writing my own processor init/boot code, I don't know.

EDIT: A little Googling reveals that Coldfire is officially supported.  I'll have to look into it.

---

### Post by davidgarcin on 2007-11-26
Good news:  the tftp server is working.
Bad news: I feel like an idiot.

The problem was that my /etc/xinetd.d/tftp was actually at /etc/xinet.d/tftp.....

Yup.  It would seem that my prior comments about the board connecting to the server were completely off the mark.  At least, I would assume so, given that I don't see how the service would be started in the first place.  Still, one would think you would get a more helpful error message, like "Can't connect to server", and that when you change the filename parameter, it would give the same error message as previously, not an "Access denied" message.

Anyway, that's my walk of shame :-).  Thanks for your help, everyone.
-Dave

---

