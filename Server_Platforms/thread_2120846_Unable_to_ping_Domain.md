---
title: "Unable to ping Domain"
date: 2013-02-27
forum: Server Platforms
---

### Post by IJselflearner on 2013-02-27
Hi All,
 
**please help, I am slowly losing heart with Ubuntu.**
there's a lot of complications.
 
How can I ever ping my Domain?
I followed a guide in setting up static ip *([http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html)).*
I am trying to connect my Ubuntu machine to a domain, and fail . . .fail . . . and fail. No disrespect, but those who created tutorials seem's to be created it incompletely. configuration doesn't simply work, there are some preconfigurations that are not discussed, that are needed to be done beforehand and we are just left full of questions and desperations. Ubuntu is getting very hard on us.
 
Business is bound to get stagnant just spending time only configuring a non user friendly setup and hard coded configuration.
 
Less support!!!
 
This gives me an idea to look on the bright side of others who can make things simple, user-friendly, easy and incomparable, well support software vendor. so that we can focus on bringing new opportunities for our business.
 
 
Desperate and Hopeless . . .

---

### Post by Lisiano on 2013-02-27
*Not a domain pro*
First off... Why are you following a guide made for 8.10?... That was literally 4 years ago and we will soon have 13.04...
Secondly: Take a look at this [technet article]("http://technet.microsoft.com/en-gb/magazine/2008.12.linux.aspx"). Not sure if it will solve all your problems but seems to be a good starting point. Note. That article bases on Red Hat, so only the general configuration principle applies. Substitute any Red Hat specific instructions for Debian/Ubuntu specific instructions.

EDIT: Another article, but this one is for Ubuntu: [https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

---

### Post by darkod on 2013-02-27
What do you have as domain controller? Samba DC?

That article by the looks of it is only for setting up a static IP. Static IP doesn't allow you domain name pinging by default unless you have a correct DNS server configured and using it, and you also need to have the domain controller up and running.

---

### Post by IJselflearner on 2013-02-27
Darkod,
 
I have a Samba 4 DC ([http://wiki.samba.org/index.php/Samba4/HOWTO](http://wiki.samba.org/index.php/Samba4/HOWTO)), it is up and running, Windows 7 client is connected to it now.
What are the configurations that I needed to work on to join an Ubuntu to my Samba DC? cause all of the tutorials and guides doesn't seem to work for me. even this ([https://help.ubuntu.com/community/LikewiseOpen](https://help.ubuntu.com/community/LikewiseOpen))
 
My brain is drained with this.
 
Any help will be highly appreciated.
 
Thanks.

---

### Post by IJselflearner on 2013-02-27
Lisiano,
 
 
Have you tried joining an Ubuntu 12.10 Quantal to a Samba DC?
Can you share your configuration to us?
 
 
Thanks for your generosity. Hope you find that easy to do.
 
Thanks.

---

### Post by darkod on 2013-02-27
Unfortunately I'm no expert in domains, but did you notice that samba4 howto you linked says in its title "how to install active directory compatible domain controller"? Maybe that's why windows clients connect easily, but linux don't.

If you need it to be AD compatible DC, you did it OK it seems, it's working for windows clients. But for linux you might need few tweaks. Notice how the howto itself doesn't have a section on connecting linux clients, only windows.

This is a youtube video about joining 11.10 to samba domain. I didn't have time to watch it, I just found it on google and giving you the link, hope it can help you:
[http://www.youtube.com/watch?v=yizms_dGvRs](http://www.youtube.com/watch?v=yizms_dGvRs)

---

### Post by Lisiano on 2013-02-27
Sorry, as I have stated at the beginning, I'm not an expert on domains. But it seems the wiki page I linked to at the beginning is what you want [https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)
Feel free to post back with any questions.
Also, if I were you, I'd leave client running of DHCP, less problems, also the proper DNS server gets set up (As long as you have a proper DHCP server).

---

### Post by IJselflearner on 2013-02-27
thanks for the quick reply, Darkod.
 
I've been watching that tutorial over and over. It's pretty easy for him, because he has already done configurations beforehand, (which he did not disclosed). I was wondering if a Windows client can join the Samba server by just supplying the right "IP and DNS" input why is it not posssible with Ubuntu? The better should be the relationship between Ubuntu machines.
 
I am very glad when I had the Samba 4 AD DC, worked in an automated way. everything is auto-configured.
 
If this is not possible with Samba 4, should I then configure another Samba (Samba3) to let Ubuntu machines have a Domain Controller?
 
You do enlighten me, Darkod.
 
Thanks.

---

### Post by darkod on 2013-02-27
Unfortunately, I don't know samba in details, but I do think it's more windows oriented.

For example, samba shares are usually for windows machines to access them, although linux can too.

So, just because the samba server is installed on ubuntu server, it doesn't mean joining ubuntu client will be easier. In fact, if samba is more windows oriented joining windows client in an easier way is logical.

Most of the configuration seems to be on the server side, not on the client side. Maybe some is missing on the server. Just because windows can join, doesn't mean everything is configured all the way. Remember, that howto was for AD compatible DC, oriented more to windows. Maybe they left out part of the configuration that is needed for linux clients.

I don't know what to recommend at this moment. Google is full of tutorials and forum threads about joining linux machines to samba domain, take a look and hopefully you will recognize some good tutorial when you find it.

---

