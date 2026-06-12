---
title: "removing unnessary services"
date: 2004-11-09
forum: Server Platforms
---

### Post by ubuntu_demon on 2004-11-09
Hi,

I removed some services that I think are not necessary for most users (fam,portmap and smptd) I think these services aren't accesible from other machines but why run unnessary services ?

I think fam and portmap are only used when browsing for files in an network. I use ssh (filezilla) for filetransfers between my pc's so I don't need them.

apt-get remove fam portmap

(gnome-desktop-environment is also removed but this is just a virtual package)

smptd :

I commented the following three lines in /etc/postfix/master.cf :

pico /etc/postix/master.cf

#127.0.0.1:smtp inet n   -       -       -       -       smtpd
#::1:smtp       inet n   -       -       -       -       smtpd
#submission inet n      -       -       -       -       smtpd

after that do : sudo postfix reload

Ofcourse the user is still able to get emails from other users and services.

What do you guys think ? Did I do something stupid or should this be standard in the next release of ubuntu ?

---

### Post by ubuntu_demon on 2004-11-09
i've also removed cupsys since I don't need a printerserver.

sudo apt-get remove cupsys

---

### Post by ubuntu_demon on 2004-11-12
*bump*

---

### Post by tvlad on 2004-11-12
I tend to simply delete the links in the given runlevel, though uninstalling them might be a better idea if you don't really need'em et all.

And usually i rm, or ln the necessary links, can't say update-rc.d is smth that i like too much too use, rcconf is nice though. I did a nmap on my ip, and i have microsoft-ds on port 445 or a number near that, i'm in win atm, i looked through /etc/init.d , etc/inetd.conf, and i found no mention of it, what service starts it ?

---

### Post by ubuntu_demon on 2004-11-12
I switched over to hoary.

I think the standard ubuntu installation is quite secure but I also think that if you are sure you aren't going to use some service you should just shut it down or remove the package.(or edit the config file) By the way I don't think the services I mentioned were accesible from out of my machine.

But can't you see the links in rc*.d when you type 

locate fam | grep etc/rc
and
locate portmap | grep etc/rc

?

---

### Post by ashley_v on 2004-11-18
Ok as soon as your getting your Ubuntu desktop installed keep an eye out for open services with new packages that get installed.  Like this:

Lets say you only need 1 open port to be online during your installation.  And it happens to be dhcp client.  So run netstat -lap or whatever options you prefer to pass  to it, man netstat for that.

So you might see a bunch of garbage just ignore anything using a unix domain socket and look for tcp services.  Then just take them succers out with the killall -9 program command.

So I may see famd and portmap and cupsd etc.

killall -9 famd && /etc/init.d/portmap stop ; killall -9 cupsd | netstat -lpa 

When all is said and done the only tcp stuff you should see for a standalone box running dhcp client should look like this:

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 *:bootpc                *:*                     LISTEN

And that can be filtered by only allowing your dhcp server or what not.  Thats a matter for iptables to do so get in touch with iptables is most important.

Notice that killlall -9 and stopping services with /etc/init.d/service stop and even the way I did it simultaneoulsy with one command and using operands is just an example of how to do process management in Linux.  There are many other ways to do it, but was just wanting to show you the possiblities.  You can even write a small shell script to do it for you.  

Is just that just because you installing Ubuntu does not mean your box is safe during the installation process in fact is when your computer is most vulnerable cause services are being started and stopped on demand with default configurations being installed.  Unless you DID NOT install from untrust network then make sure you don't just sit there or run off while it's installing.  Monitor it!  If you see deselect saying "setting up portmap" then there you know you have portmap deamon rpc running and with no firewall anyone can map thoose with rpcinfo over the net or by some other means.

And this is only for one time thing.  Once your box is installed then remember to disable or plain out remove the service so you don't have to do that on every boot.

---

### Post by ubuntu_demon on 2004-11-18
just do :
sudo apt-get install nmap
sudo nmap -sV localhost

and find out what services you want to remove. 

For example :

Removing the smtpd of postfix by editting /etc/postfix/master.cf and placing #'s for the smtpd lines.

stop fam,portmap ,cups by removing those links (or chmod -x) in /etc/rc0.d /etc/rc1.d /etc/rc2.d/

It's better not to remove those packages so you don't break ubuntu-base or ubuntu-desktop.

By the way if you do nmap from another PC you get to see the services that are really "open". I think you should see only cups with a default warty installation. (so the default configuration is reasonably secure)

---

