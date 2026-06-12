---
title: "installed ubuntu-desktop on server but can't get it to start"
date: 2018-06-24
forum: Server Platforms
---

### Post by mitchwall on 2018-06-24
Hey guys,

some days ago I rented a server (a virtual machine) on strato.de and now I am trying to install a GUI on it. 
I have successfully installed ubuntu-desktop (1.361.1) but somehow I can't get it running.
I am using [COLOR=#333333][FONT=verdana]OS Ubuntu 16.04 LTS 64bit. 
[/FONT][/COLOR]Whenever I connect using ssh root@myip through the command line just stay in the command line.
Shouldn't the GUI directly boot up? Or do I have to start it manually? How do I do that?

btw I am using a mac with high sierra 10.13.5


Thanks in advance,

mitchwall

---

### Post by TheFu on 2018-06-24
No. GUIs don't work that way, especially over remote connectivity.  I don't have time to explain everything, but you'll need some sort of remote X/Windows tool, which isn't pre-installed on OSX.  Or you can use x2go or you can  use an ssh-tunnel + VNC. I use x2go myself.  

Also, heavy desktops like KDE or Gnome3 (which is the Ubuntu Desktop default) don't work well over remote connections.  I'd remove that package and install lxde instead.

It is a terrible idea to allow remote root into a Linux server, without highly restricted source IPs **and** using ssh-keys.
And running a GUI as root is even worse than allowing a locked down remote root.

I;ve posted here about x2go before for mac users and others have chimed in with more details. Please search the forums.

---

### Post by QIII on 2018-06-24
Moved to Server Platforms.

I am going to echo the bit about root logins over SSH:  Don't.  Ever.

Also, if you are going to be using this as an actual server, especially exposed to the web, adding a desktop just creates more attack surface by running a lot of unnecessary services.   I don't know what you plan to do with the VM, but in all but a very few circimstances I would recommend strenuously against a desktop.

---

### Post by mitchwall on 2018-06-24
Thank you for moving my post to the right section;)

As you have guessed, I have little to no experience when it comes to Linux. 
Maybe I should tell you what I am trying to achieve.
I am trying to find a way to run a program (something like whatsapp or Spotify) which I will have to control from time to time and I figured out that a GUI on a server would probably work best. The server / program won't be exposed to the internet (for others to find) it would just use the service of the application through the internet.
To you think that under this circumstances it would still be a bad idea set up a GUI. nor use ssh? 
Thanks in advance):P

---

### Post by TheFu on 2018-06-24
Always use ssh for server management.  If there is any open port on the internet, it will be discovered in hours.  Doesn't matter what port, which protocol. It will be found. Most protocols are not really very secure, unless you use PKI with private keys that aren't ever public to anyone else.

When you've learned more and have a better security stance from experience and practice, you can add a GUI later, but really for server management, ssh is **the** method to use, know, love.

IMHO.

If you are still convinced that you want a GUI, I'd push you to use x2go for a number of reasons. x2go is based on NX which uses ssh (and only ssh) for the encrypted tunnel and authentication. But please don't run with root.  That is a terrible idea and will cause issues, soon.

---

