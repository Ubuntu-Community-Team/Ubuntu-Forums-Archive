---
title: "Lightweight Server help?"
date: 2008-05-08
forum: Server Platforms
---

### Post by mikeypsquared on 2008-05-08
Hello, I thank you for taking the time to read this.


I want to know the best possible configuration i can do with Ubuntu(or another linux). The reason i want to do Ubuntu is ease of use with apt-get.

I am looking to run a ftp, forum(php?), and latter a http server.
I don't mind running it in console, and i am a little new to linux.
My setup is:

PII(233mhz)-in the near future i can upgrade it to 400mhz
512mb of ram
250gb hard-drive.
with Ubuntu 6.06.2 server

I was wondering what packages come default with this linux distro, and how to remove them, to get the bare essential of what i need. Or would i be better with another distro(im not all to linux familar, but willing to dig through documentation)Also i would like recommendations of what software to use with this server(really lightweight)and any guides that you may have, and any dependencies they may have.

Thanks!

---

### Post by Dr Small on 2008-05-08
If you want a bare minimal of packages with ubuntu for a server, then here is my suggestion, and has worked great for my server.

Install a text-based install of Ubuntu from the alternate CD. No need for the Ubuntu Server distro. You can install LAMP if you want, but I recommend against it. After the install, you should have a bare minimal Ubuntu system (well, not really completely bare... but).

Then you can build the system from the ground up, starting with SSH, FTP (if you really want it), Xampp (for a complete webserver), Webmin (if you really need it, for Remote Administration from a Web Browser).

That is basically what I have done, and it allows you to install what you want for the system, and gives you expirience at building it up.

Dr Small

---

### Post by FakeOutdoorsman on 2008-05-08
> **Dr Small said:**
> ...You can install LAMP if you want, but I recommend against it...
Why would you recommend against a LAMP (Linux, Apache, mySQL, PHP) server?  This is an industry standard and would run perfectly on his hardware (I have a similar computer as the original poster).  You then recommend XAMPP, which contains Apache, mySQL, and PHP but has some other, extra heft.

XAMPP is good if you are learning and is sometimes used as a development server, but I would recommend against using it as a live web server.  By default, many security features are not enabled.

You could start off with the alternate disc and add your intended packages (including the server kernel), but in the end you would have something similar to a bare install if you used the server disc.

For the original poster, you can start with [Apache, PHP, and mySQL]("https://wiki.ubuntu.com/ApacheMySQLPHP") [Ubuntu Wiki] since I assume the forum software will require this.

As for another distro, Debian Etch is rock stable and is easier to configure to be lightweight since the base/minimal install is smaller.  Ubuntu Server can be made fairly lightweight as well and would work just fine for a small site.  It would be good if you are a beginner and familiar with Ubuntu.

If you choose Debian or Ubuntu, make sure to read [Securing Debian Manual]("http://www.debian.org/doc/manuals/securing-debian-howto/") before going live.

---

### Post by songshu on 2008-05-08
> **mikeypsquared said:**
> 

I was wondering what packages come default with this linux distro, and how to remove them, to get the bare essential of what i need. 

Thanks!

i think you are spot on with the server cd, this will install ubuntu base.
i would not call it a bare minimum, but it is a very sensible default to build from. it contains basic programs but no "real" server applications like apache or mysql, mail etc...


what you would need to to is figure wich forum software you would like to use, there are many to choose from, and then follow a simple howto that describes the setup.

phpbb2 would be a good choice for example

and 

```
apt-get install phpbb2
```

would install it

---

### Post by mikeypsquared on 2008-05-09
Thank you guys for all the advice. i decided upon Debian 4, with the netinst cd. It took me ages to set it up, not because of the txt based installer but grub and lilo booting. Classic Error 18, where the older computer bios wouldn't detect all gigs, and failed to start(seperate /boot paritions). anyway, i got that resolved and got a txt based debian install. I'm also using the jfs filesystem. So would it be wiser to use apt-get or aptitude?

Once i get the packages i want (either apt-get or aptitude) I goggled, and someone mention openshh, or something, that they used there laptop to log into the server and configure it with a gui. Can anyone give me a brief tutorial or link to that?
I don't think i can configure these packages, apache, mysql without having a gui. Or is there some guide after you get the server up. I know i'm using debain, but i was wondering if there is some easier way besides install a heavy gui onto the system and uninstalling it. I have settled with apache and phpBB. Thanks for the help guys!

Thanks

---

### Post by songshu on 2008-05-09
in etch aptitude is recomended, at the moment etch was released it had some clear advantages ober apt-get..

after it released apt-get got some improvements so later versions would probably be apt-get again.
you can use both of them anyway.

ssh is the best way to login to a remote machine. period......


one thing about the gui,
you don't need it, and its not usefull in anyway.


try something simple first with a guide like this one for example [http://doc.ubuntu.com/ubuntu/serverguide/C/](http://doc.ubuntu.com/ubuntu/serverguide/C/)

if you do
```
aptitude install openssh-server
```

you can login from a different machine by doing

```
ssh username@192.168.0.2
```

simple as that

if you want to install a webserver you do
```

aptitude install apache2
```

after you did that you can use your browser to go to that ip address, probably not much to see but you will know if "it works"

---

