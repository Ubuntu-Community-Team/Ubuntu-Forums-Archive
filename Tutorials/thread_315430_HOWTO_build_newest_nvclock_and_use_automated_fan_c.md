---
title: "HOWTO: build newest nvclock and use automated fan control"
date: 2006-12-09
forum: Tutorials
---

### Post by Jons_Collasius on 2006-12-09
this howto allows you to build nvclock from cvs and use automated fan control with a demonized perl script.

sorry, my english is a bit rusty...

**get, configure, make and install nvclock from cvs**

first we make sure, that no nvclock package is installed and install needed packages.
```
sudo aptitude remove nvclock
sudo aptitude install cvs automake
```

you need to get, configure and make the newest nvclock source from cvs.
```
cd /usr/local/src
sudo cvs -z3 -d:pserver:anonymous@nvclock.cvs.sourceforge.net:/cvsroot/nvclock co -P nvclock
cd nvclock
sudo sh autogen.sh
sudo ./configure
sudo make
```

test nvclock
```
./src/nvclock -i
./src/nvclock -F 100 -f
```

if these two commands work, install nvclock
```
sudo make install
```

[COLOR="Red"]some times the installation fails. in this case just cp nvclock by hand
```
sudo cp /usr/local/src/nvclock/src/nvclock /usr/bin/nvclock
```[/COLOR]


**use automated fan control**

we use automated fan control with a litle perl script.
touch a new file and chmod it.
```
sudo touch /usr/bin/auto_fan
chmod 755 /usr/bin/auto_fan
```

insert this code in the new file, with a text editor of your choice
```
#!/usr/bin/perl

use strict;
use warnings;

my $nextDown = time();

while(1) {
  my ($tempGPU, $speedFan) = (qx(nvclock -i) =~ /GPU temperature: (\d+)C.*Fanspeed: (\d+)/s);
  my $newSpeed = $tempGPU * 2 - 100;
  $newSpeed = 20 if($newSpeed < 20);
  $newSpeed = 100 if($newSpeed > 100);
# print "GPU: $tempGPU°C   Board: $tempBoard°C   OldFan: $speedFan%   NewFan: $newSpeed\n";
  if($speedFan < $newSpeed) { 
    system("nvclock -F $newSpeed -f > /dev/null");
  } else {
    if($nextDown < time()) {
      system("nvclock -F $newSpeed -f > /dev/null");
      $nextDown = time()+30;      
    }      
  }
  sleep(2);
}

```

the line *my $newSpeed = $tempGPU * 2 - 100;* controls the fan speed settings. with this settings fan speed will be 20%@60°C and 100%@100°C. my fan runs 34%@64°C GPU in almost every game. in idle (listening ogg files in the evening, while loading new oggs :)) the fan slows down to 20%.

you should nice auto_fan to 15, else it lags in games, when auto_fan is running
```
nice -n 15 auto_fan
```

you can demonize this perl with start-stop-daemon.
start auto_fan
```
start-stop-daemon --start --oknodo --nicelevel 15 --pidfile /var/run/auto_fan.pid -m -b --exec /usr/bin/auto_fan
```

stop auto_fan
```
start-stop-daemon --stop  --oknodo --pidfile /var/run/auto_fan.pid
```

i inserted this two lines in /etc/init.d/gdm
find *log_begin_msg "Starting GNOME Display Manager..."* and insert the start command after it.

find *log_begin_msg "Stopping GNOME Display Manager..."* and insert the stop command after it.

have fun and a whispering quit nv card.

---

### Post by _simon_ on 2007-10-28
I have a dual screen setup (1680x1050 on screen 1 and 1280x1024 on screen 2)

Since I've started using this script, screen 1's resolution will change at random, but I don't know what it's changing to or why.

Any ideas? I can't see anything in the script that would do this.

I use Compiz-Fusion, could it be related somehow?

EDIT: Looks like this was down to a bad xorg, after reconfiguring it seems to be fine now.

---

### Post by syxbit on 2007-12-24
you're amazing
i was shocked when i first installed the 8800gt
it's far louder than when I'm playing Crysis in Windows!

thanks a lot. saved me a bunch of time

---

### Post by pwc on 2008-01-01
I installed the 8800 GT a few days ago and also was shocked at the sound of fan, which was quiet in XP(duel boot). I had to fix that! I followed the howto by  Jons_Collasius and thank god now it's quiet.
I did'nt do the demonize step at end because I did'nt understand the insert start command. Do you just type the word start after the line log_begin_msg "Starting GNOME Display Manager..." or is there more to it than that. I don't want to mess things up after getting this far.

thanks, pwc

---

### Post by ubun_two on 2008-01-04
First of all, thank you VERY MUCH for this article.  It's kind of funny that an article written a year ago is coming very handy now, with new 8800GT.  And newbie like me could follow it!

I got almost everything working as described in the article...except for the last step.

I inserted the start-stop-daemon line to /etc/init.d/gdm file as described in the document, but the fan doesn't seem to slow down upon boot-up at all.

But when I copy and paste the exact line to terminal manually after logging in, fan does slow down, so the command itself works.

Anyone has any idea why that is???:confused:

I am using EVGA 8800GT, Gutsy 32bit, and nVidia driver version 169.07.

---

### Post by guitarist809 on 2008-01-06
Thanks for the tut! Worked great :) I wish Nvidia would release a new driver that fixed the fan speed so I don't have to worry about this if I ever reformat =\

---

### Post by phekdra on 2008-01-10
> **ubun_two said:**
> 
I inserted the start-stop-daemon line to /etc/init.d/gdm file as described in the document, but the fan doesn't seem to slow down upon boot-up at all.

But when I copy and paste the exact line to terminal manually after logging in, fan does slow down, so the command itself works.

Anyone has any idea why that is???:confused:


I'm also having the same problem and would like to know if anyone has a solution.

Phekdra

---

### Post by OliW on 2008-01-14
Also having the same issue.

---

### Post by arito on 2008-01-16
Many thanks for the instructions. The command works as it's supposed to. The demonizing on the other hand doesn't work for some reason - which seems to be the case for a few others here too. I wasn't quite sure how to add those two lines of code to /etc/init.d/gdm, but I just made a new row for both of them and pasted the code there. I hope that's how it should be done.

---

### Post by kiroro on 2008-01-18
Help: having errors when I run:
```

sudo ./configure

```
I have this:

```

checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for library containing getopt_long... none required
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.4.0... checking for x11... checking whether -R must be followed by a space... neither works
checking for dnet_ntoa in -ldnet... no
checking for dnet_ntoa in -ldnet_stub... no
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... no
checking for XOpenDisplay in -lX11... no
checking for XextFindDisplay in -lXext... no
configure: creating ./config.status
config.status: creating src/Makefile
config.status: creating src/backend/Makefile
config.status: error: cannot find input file: src/nvcontrol/Makefile.in

```

I followed the instruction above and things went well untill I configure. If run 'sudo make' after this, it tells me: 'make: *** No targets specified and no makefile found.  Stop.'
Please help me!

---

### Post by KicktheCAN on 2008-01-20
When I use "chmod 755 /usr/bin/auto_fan" I get back "This operation is not allowed". I can not seem to find a way to change the permissions of the file so I can not use the script, could anybody help me with this?

Edit: I just opened it as root, problem solved.

---

### Post by XtremeGamer99 on 2008-01-21
Everyone that is having trouble with the daemonizing: Are you sure that you aren't using KDM? If you're using KDM, you need to edit the kdm file, rather that the gdm. It works perfectly for me.

=)

---

### Post by tissetosse on 2008-01-21
> i inserted this two lines in /etc/init.d/gdm
find log_begin_msg "Starting GNOME Display Manager..." and insert the start command after it.

find log_begin_msg "Stopping GNOME Display Manager..." and insert the stop command after it.

have fun and a whispering quit nv card.

Cant get this to work, Ive added the line but it doesnt work, either the log in screen doesnt boot or the fan control doesnt start. When I type the line in the terminal it works perfectly. Anyone who got this working and can post how they inserted the lines? 

/Mattias

---

### Post by XtremeGamer99 on 2008-01-21
As I said with my last post, are you using KDM?

You have to edit the KDM file instead of of the GDM file if you are.

Also, I'm using Debian Lenny, and not Ubuntu, which might also be why it works for me. <_<

---

### Post by OliW on 2008-01-21
Well I'm positive that I'm not using KDM and it doesn't work.

---

### Post by KicktheCAN on 2008-01-21
Where are you supposed to put those lines in the gdm file? I think that may be why it is not working for me.

---

### Post by phekdra on 2008-01-21
> **KicktheCAN said:**
> Where are you supposed to put those lines in the gdm file? I think that may be why it is not working for me.

I've tried moving them around within the file (yes, I'm using GDM :) ) but haven't had any luck so far. Would someone who has got it to work post their gdm file please to put the rest of us out of our (noisy) misery...

Phekdra

---

### Post by hotweiss on 2008-01-21
Same problem here, the auto_fan does not start when I boot, but when I run it in terminal it works. And yes, I am using Gnome, so the instructions apply to me.

---

### Post by hotweiss on 2008-01-21
Adding it auto_fan to GDM didn't work, but I added it to Sessions (in Preferences) and now my PC is silent again.

---

### Post by KicktheCAN on 2008-01-21
> **hotweiss said:**
> Adding it auto_fan to GDM didn't work, but I added it to Sessions (in Preferences) and now my PC is silent again.

I just did this but now I can not log into Ubuntu. Whenever I try I get a black screen and I can alt+f2 to a text-only login screen but then it brings me back to the graphical login screen.

---

### Post by Artemis3 on 2008-01-21
Here is a simplified (or refined) method.

uninstall nvclock if you have it (sudo apt-get remove nvclock)

Download the [nvclock source package](http://www.linuxhardware.org/nvclock/nvclock0.8b3a.tar.gz) from its page, no need for cvs.

Install automake for autogen.sh (sudo apt-get install automake)

Untar the package in your folder (tar -xzfv nvclock0.8b3a.tar.gz) and cd to it.

./autogen.sh ; ./configure --disable-nvcontrol ; make
sudo make install

/usr/local/bin/nvclock -f -F auto

Done!

Well, actually you will want to run this in a startup script (who needs gdm anyway? :)) Just add the above command to the file /etc/rc.local, just above "exit 0" (sudo nano /etc/rc.local)

---

### Post by hotweiss on 2008-01-22
> **Artemis3 said:**
> Here is a simplified (or refined) method.

uninstall nvclock if you have it (sudo apt-get remove nvclock)

Download the [nvclock source package](http://www.linuxhardware.org/nvclock/nvclock0.8b3a.tar.gz) from its page, no need for cvs.

Install automake for autogen.sh (sudo apt-get install automake)

Untar the package in your folder (tar -xzfv nvclock0.8b3a.tar.gz) and cd to it.

./autogen.sh ; ./configure --disable-nvcontrol ; make
sudo make install

/usr/local/bin/nvclock -f -F auto

Done!

Well, actually you will want to run this in a startup script (who needs gdm anyway? :)) Just add the above command to the file /etc/rc.local, just above "exit 0" (sudo nano /etc/rc.local)

Or you can download the deb here:

[http://morgoth.free.fr/ubuntu/pool/main/n/nvclock/](http://morgoth.free.fr/ubuntu/pool/main/n/nvclock/)

---

### Post by OliW on 2008-01-24
Hardy testers using 169.07 (with broken fan controller) should do an update as the new driver released today (169.09) has a working (quiet) fan. Woo.

---

### Post by pointfivezero on 2008-02-05
> **XtremeGamer99 said:**
> Everyone that is having trouble with the daemonizing: Are you sure that you aren't using KDM? If you're using KDM, you need to edit the kdm file, rather that the gdm. It works perfectly for me.

=)

Great script, this is what I have been waiting for, for a very long time! 

Perfect (ok, maybe the editing of init.d/kdm put me off a little buuuuuut, nah I will live with a quiet pc!)

---

### Post by geoff123 on 2008-05-26
Here's another script which i hope helps someone. I did this because I'm more familiar with python.  I wish Nvidia and Ubuntu would get this fan issue properly fixed.  

An alternate way without modifying startup folders is to run it with "screen", but need to manually start it after reboot. Also any improvements appreciated.

screen nice -n 15 ./auto_fan3.py

---

### Post by billybag on 2008-09-09
for some reason i get "Error: Your card doesn't support fanspeed adjustments!"

i have geforce on a newer dell xps m1530

---

### Post by mastergunner on 2008-09-10
....

---

### Post by Muskokas.Finest on 2008-11-08
Yea I'm having the same problem with nvclock telling me my card doesn't support fan speed adjustments. I'm on a Toshiba P100 with an Nvidia 7900GS. Is there some sort of workaround?

---

### Post by ottar t on 2008-11-23
skipped the start stop deamons and just added nv-auto-fan as program to preferences > sessions for each user.
(as mentioned by other's)

regards 
ottar t


Hello all
New, but keen user of ubuntu 8.10.
Have nvidia 6600GT that does not support nvclock -f -F auto, so based on a script :
# NVidia Fan Speed Revisited
# October 30th, 2008 by Mitch Frazier inHOWTOs
# Mitch Frazier is an Associate Editor at Linux Journal.
#
i made nv-auto-fan in usr/bin/ by using command nvclock -f -F $$%.

start stop deamons works with sudo in terminal:
sudo start-stop-daemon --start --oknodo --nicelevel 15 --pidfile /var/run/nv-auto-fan.pid -m -b --exec /usr/bin/nv-auto-fan
&
sudo start-stop-daemon --stop  --oknodo --pidfile /var/run/nv-auto-fan.pid 
and i get reduced fan speed: 
-- Sensor info --
Sensor: GPU Internal Sensor
GPU temperature: 65C
Fanspeed: 40.0%

however, I can't get the deamon to start in /etc/init.d/gdm when i put the start-stop-deamon (without sudo) there. Have also tried to put the entry in /etc/rc.local, but without any success.
Hope somebody can guide me to finalise this issue? Preferably the deamon should also work for other users on the pc without the need for root access..

regards
ottar t

---

### Post by graysky on 2009-03-14
Great thread.  Here is what I did to get the current version (0.8b4) installed (without GUI) on Intrepid x86_64:

```
tar zxvf nvclock0.8b4.tar.gz
cd nvclock0.8b4/
sudo aptitude install automake
sudo sh autogen.sh
./configure --disable-nvcontrol --prefix=/usr
make
./src/nvclock -i
sudo make install
```

---

### Post by karg on 2011-10-02
This is my solution for automatic fan control with nvclock:

[http://ubuntuforums.org/showthread.php?p=11304775#post11304775](http://ubuntuforums.org/showthread.php?p=11304775#post11304775)

---

