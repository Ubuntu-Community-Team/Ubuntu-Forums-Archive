---
title: "Need advice setting up home server !"
date: 2009-04-01
forum: Server Platforms
---

### Post by gorucan on 2009-04-01
Hello,

If am really new to linux and i don't have clue about it i only know how to use GUIs and i understand shell a little but i barely know the basic commands.....

I want to have LAMP server - i don't even know differences between ftp  lamp samba and all this... so i need someone to tell me how do i set it up as easy as possible.

I want to understand how i can access the server from anywhere,  any browser... and can i upload to that server through browser?

I want domain assigned to it also, how do i do it?

If i install server  8.10 is that okay? and check LAMP in installation or something else also?

I just need configuration that will work. and i  have router also, is that bad? I don't even know how to do this port forwarding or what it is. 


I would kindly ask someone to explain all this to me as you would to your grandmother, pastoral edition =) Please don't just give me links, only when the articles respond to my answers.

Seeking short tutorial for complete newbies.

---

### Post by primaxx on 2009-04-01
Hi,

what you are asking for is an essay! :-)

So, even though you don't want it; here's the links...

**Lamp Server + more on Ubuntu 8.10 Server:**
[http://www.howtoforge.com/perfect-server-ubuntu-8.10](http://www.howtoforge.com/perfect-server-ubuntu-8.10)
or
[http://www.ubuntugeek.com/step-by-step-ubuntu-810-intrepid-ibex-lamp-server-setup.html](http://www.ubuntugeek.com/step-by-step-ubuntu-810-intrepid-ibex-lamp-server-setup.html)

**Add Gnome-Desktop (gui) and/or webmin to Ubuntu 8.10 Server**
[http://www.ubuntugeek.com/ubuntu-serverinstall-gui-and-webmin-in-ubuntu-810-intrepid-ibex-guide.html](http://www.ubuntugeek.com/ubuntu-serverinstall-gui-and-webmin-in-ubuntu-810-intrepid-ibex-guide.html)

**Ftp-access to your server:**
[http://www.howtoforge.com/setting-up-proftpd-tls-on-ubuntu-8.10](http://www.howtoforge.com/setting-up-proftpd-tls-on-ubuntu-8.10)

**How to get access to your server through the free service dyndns (Then your domain on the Internet will be something like mypersonaldomain.dyndns.org):**
[http://www.dyndns.com/services/dns/dyndns/howto.html](http://www.dyndns.com/services/dns/dyndns/howto.html)

**How to forward ports from Internet to your server in your router:**
[http://www.portforward.com/](http://www.portforward.com/)

Then I have to say:
What you are asking covers a lot of things, and not all of them are easy to manage. 

I think you should ask yourself what you really want to do with your server, and then post it here.

Good luck! ;)

PS!
If you expose your server to the Internet, google how to secure it...

---

### Post by Iowan on 2009-04-01
Links are gonna be your best resources for awhile.  Specific questions can be answered, but if a link has already touched on it, why post the same information? [Here]("https://help.ubuntu.com/8.04/serverguide/C/index.html") is yet another one - on servers.  In fact, [https://help.ubuntu.com](https://help.ubuntu.com) has several pages that may be of interest.

---

### Post by redonwhite on 2009-04-01
Hey I'm setting up a home server too.  Thanks for all the links.  Ive only got through 2 of them and I've already learned twice as much as I did.  Thanks again.

---

### Post by redonwhite on 2009-04-01
Can I read/write files using Webmin?

---

### Post by primaxx on 2009-04-02
> **redonwhite said:**
> Can I read/write files using Webmin?
Yes you can, through Webmin's Java-based File manager. 
You find it under *Others->File manager* (Directly translated from Norwegian, but I assume it's called so in English as well...) :)

---

### Post by hyper_ch on 2009-04-02
what do you want to do with the server?

---

### Post by gorucan on 2009-04-02
> **primaxx said:**
> Hi,

what you are asking for is an essay! :-)

So, even though you don't want it; here's the links...

**Lamp Server + more on Ubuntu 8.10 Server:**
[http://www.howtoforge.com/perfect-server-ubuntu-8.10](http://www.howtoforge.com/perfect-server-ubuntu-8.10)
or
[http://www.ubuntugeek.com/step-by-step-ubuntu-810-intrepid-ibex-lamp-server-setup.html](http://www.ubuntugeek.com/step-by-step-ubuntu-810-intrepid-ibex-lamp-server-setup.html)

**Add Gnome-Desktop (gui) and/or webmin to Ubuntu 8.10 Server**
[http://www.ubuntugeek.com/ubuntu-serverinstall-gui-and-webmin-in-ubuntu-810-intrepid-ibex-guide.html](http://www.ubuntugeek.com/ubuntu-serverinstall-gui-and-webmin-in-ubuntu-810-intrepid-ibex-guide.html)

**Ftp-access to your server:**
[http://www.howtoforge.com/setting-up-proftpd-tls-on-ubuntu-8.10](http://www.howtoforge.com/setting-up-proftpd-tls-on-ubuntu-8.10)

**How to get access to your server through the free service dyndns (Then your domain on the Internet will be something like mypersonaldomain.dyndns.org):**
[http://www.dyndns.com/services/dns/dyndns/howto.html](http://www.dyndns.com/services/dns/dyndns/howto.html)

**How to forward ports from Internet to your server in your router:**
[http://www.portforward.com/](http://www.portforward.com/)

Then I have to say:
What you are asking covers a lot of things, and not all of them are easy to manage. 

I think you should ask yourself what you really want to do with your server, and then post it here.

Good luck! ;)

PS!
If you expose your server to the Internet, google how to secure it...

Thank you a lot =) I will read them as fast as possible but i have got to go practising piano now =)
I hope i won't need more than like 3 days setting this up...
Securing the server... hmm... because of my privacy? I wouldnt use same computer for server and e-shopping anyway... you meant it should be secure so somebody doesnt use my server as their spyware zombie?


> **Iowan said:**
> Links are gonna be your best resources for awhile.  Specific questions can be answered, but if a link has already touched on it, why post the same information? [Here]("https://help.ubuntu.com/8.04/serverguide/C/index.html") is yet another one - on servers.  In fact, [https://help.ubuntu.com](https://help.ubuntu.com) has several pages that may be of interest.

Good, will read. When i get specific qustions i will ask on this thread.

> **hyper_ch said:**
> what do you want to do with the server?

Actually i want to access my server from any computer or internet cafe or anywhere and access it's files or upload from any computer to my server. I would also like my mails to be stored on my server not on google's or microsoft's for example, and another thing i really want is to connect my domain ([www.juregorucan.com](www.juregorucan.com)) with it and make my own website, another thing i would like to do is to be able to live stream videos stored on my server in any webbrowser on any computer.
I would also like to use it as remote drive, means so i could open files without ''downloading'' them first (although i know they must be downloaded to be displayed - isn't that called FTP ?  =)=) sorry i really am newb for this stuff that's why i am seeking your help guys.

Thanks all, keep posting if you find anything good for me to read please  !

Cya,
j

---

### Post by gorucan on 2009-04-06
bumpidi bumpidi bump.
Anyone going to post anything else?

Edit:
I got additional question...

what is difference between raw desktop and server editions kernels?

If i do step by step from the ''perfect LAMP server guide'' i could actually do it all with desktop, installing packages from same repository right?

---

### Post by hyper_ch on 2009-04-06
have a look at the perfect server setups by Falko on [http://www.howtoforge.com](http://www.howtoforge.com)

Only problems you might have if you don't ahve a static pulic ip address.

---

