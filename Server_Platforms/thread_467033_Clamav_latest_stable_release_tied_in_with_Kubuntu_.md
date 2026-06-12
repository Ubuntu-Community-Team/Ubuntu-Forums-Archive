---
title: "Clamav latest stable release tied in with Kubuntu 6.06 Autostarts"
date: 2007-06-07
forum: Server Platforms
---

### Post by shaggly on 2007-06-07
Hi guys,

This may have seemed like a simple thing to do, but I searched for ages without finding a good method that someone had used before.

I'm running Kubuntu 6.06 (386), and I didn't want to upgrade to Feisty on this machine, as it's also used as our company server for certain packages. Our company isn't that large, so I also use it as my desktop rather than a dedicated server. That in itself, as some of you will know, poses all kinds of "interesting" sceanrios that aren't always addressed in any great depth. There are a lot of wonderful guides for LAMPP machines, and for desktops, but not a huge amount for those of us that are "half-breeds". :D

My issue was a common one. I wanted to have clamav running to check not only my outgoing emails for business, but also to check my incoming personal and business mail. The version in the repositories for 6.06 is a little too old for my liking, but it is tailored for Kubuntu - making it a no brainer to install and get running. What I wanted was a happy medium inbetween. I wanted the latest stable version, but I also wanted to feel like it was actually meant to be part of my Kubuntu setup.

So, after a lot of searching, and fiddling about I came up with a fix for the both.

I'm not posting this as a How-to, merely in the hope that it will save someone all the aggravation that I went through to get to the end result. You follow these hints at your own risk, but it has worked nicely for me.

I'm running Kubuntu 6.06, but the version I originally installed came from the nice chaps at LXF (Linux Format) and therefore also included all of the standard gnomey Ubuntu components. I liked this setup, as I could switch between Gnome and KDE. I settled for KDE in the end. I've installed a LAMPP server on here for testing, and also as a mail server for my business mail. The pc's not my newest one, this one's a Athlon XP 2500+ with 1GB of RAM and it makes a nice workhorse.

Anyway, that's enough of the blurb - onto the nitty gritty.

From installing the repository version, and then uninstalling it afterwards I had noticed that the following files were still installed (which turned out to be handy).

> /etc/init.d/clamav-daemon     [COLOR="Blue"]linked to /etc/rc6.d/K20clamav-daemon[/COLOR]
[COLOR="Blue"]which looks for --->[/COLOR] /usr/sbin/clamd     [COLOR="Blue"]deleted when you uninstall Kubuntu clamav[/COLOR]
[COLOR="Blue"]and uses --->[/COLOR] /etc/clamav/clamd.conf     [COLOR="Blue"]not deleted when you uninstall[/COLOR]
[COLOR="Blue"]also uses --->[/COLOR] /etc/clamav/clamav-base.init     [COLOR="Blue"]sets up the /var/run/clamav directory if it doesn't exist[/COLOR]
[COLOR="Blue"]also left was --->[/COLOR] /etc/default/clamav-daemon     [COLOR="Blue"]This file is hashed out anyway.[/COLOR]
[COLOR="Blue"]and then during runnning the process file is --->[/COLOR] /var/run/clamav/daemon-clamd.pid     [COLOR="Blue"]which should be created when clamd starts[/COLOR]

For Freshclam there is 
/etc/init.d/clamav-freshclam     [COLOR="Blue"]linked to /etc/rc6.d/K20clamav-freshclam[/COLOR]
[COLOR="Blue"]which looks for --->[/COLOR] /usr/bin/freshclam     [COLOR="Blue"]deleted when you uninstall Kubuntu freshclam[/COLOR]
[COLOR="Blue"]and uses --->[/COLOR] /etc/clamav/freshclam.conf [COLOR="Blue"]not deleted when you uninstall[/COLOR]
[COLOR="Blue"]and uses the logifle --->[/COLOR] /var/log/clamav/freshclam.log    [COLOR="Blue"]which will get recreated[/COLOR]
[COLOR="Blue"]and then during running the process file is --->[/COLOR] /var/run/clamav/freshclam.pid     [COLOR="Blue"]which should be created when freshclam starts[/COLOR]

So, having seen how Kubuntu autostarts clamd and also freshclam, it was just a matter of making sure that the install of the latest version of Clamav behaved itself in its locations during install. That was a matter of changing the default ./configure locations and also using the right .conf files once it was installed. All of which I'll detail below.


[LIST=1]
[*]To avoid the error message: SECURITY WARNING: NO SUPPORT FOR DIGITAL SIGNATURES when updating the definitions file, you need to install libgmp3-dev first before compiling clamav. I learnt this the hard way...
[*]Then download the latest stable version (0.90.3 at this time) from [[COLOR="Red"]http://www.clamav.net/download/sources[/COLOR]]("http://www.clamav.net/download/sources")

[*]Place it in a convenient place. I happen to use /home/user/installers/clamav

[*]Unzip it. ```
 tar -xvf clamav-0.91rc1.tar.gz
```
[*]Go to the new directory ```
cd clamav-0.91rc1/
```
[*]Run the configure script with new options ```
./configure --prefix=/usr  --libdir=/usr/lib/clamav --includedir=/usr/include/clamav --sysconfdir=/etc/clamav
```
[*]N.B. You can compile clamav with milter support just in case you use sendmail at some stage, but note that libmilter and its development files are required. Just add --enable-milter to the configure parameters above.
[*]Do the make ```
make
```
[*]Now, you can either install ```
sudo make install
```
[*]Or, if you use Checkinstall (as I do) to make debs you can ```
sudo checkinstall -D
``` which will give you a nice convenient .deb package if you have to uninstall
[*]Then you need to edit the /etc/clamav/clamd.conf and /etc/clamav/freshclam.conf files. I have two versions that I used previously at /usr/local/etc which incorporated the original kubuntu parameters, but with a couple of edits of my own. I'll attach copies of those at the end of the post. If you want to use them (at your own discretion), then simply rename them from .conf.txt files back to .conf files.
[*]As I already had copies, I'll just copy them to the correct spot.```
cd /usr/local/etc
``````
sudo cp clamd.conf /etc/clamav/
``````
sudo cp freshclam.conf /etc/clamav/
```
[*]Now, to get it all running, go into System Settings --> System Services and try and start clamav-daemon and clamav-freshclam[/LIST]

As I said, this all works for me now. After a restart clamd and freshclam are automatically running in the background, and they're the newer versions. To upgrade, I believe that you'll have to uninstall and recompile the latest and greatest, but if you used checkinstall then it should be a piece of cake.

I really hope that this helps out some of the other people who searched for the answer to this problem, but couldn't find anything in a complete form.

Cheers.

---

