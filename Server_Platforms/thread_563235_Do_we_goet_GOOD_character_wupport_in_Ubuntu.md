---
title: "Do we goet GOOD character wupport in Ubuntu"
date: 2007-09-29
forum: Server Platforms
---

### Post by kasperbs on 2007-09-29
I have just finished setting up a Ubuntu-Server as my file server just to find out that I need to install the Full Ubuntu Desktop Installation.

 - I have the Desktop Ubuntu version on my Desktop where I have no problems with character support for Danish letters like ÆØÅ, but i just figured out that when i rsync my backup over ssh to the server, there is no support for those characters.

I will now have to take a backup of my settings files and install the full blown ubuntu installation instead and then shutdown gdm and use that.

But does anyone know if there will be support for those things in future releases of Ubuntu-Server, because i kind of like that minimal install?

---

### Post by Braino on 2007-09-29
Hold on now, don't go re-installing the desktop version of Ubuntu. The main difference between the two are the things that are installed by default. With apt-get/synaptic, you can turn the default install of either one into the other. What editor are you using to view the files with those characters? You are probably using the wrong character encoding when you are trying to view them.

---

### Post by kasperbs on 2007-09-29
OK that sounds, interesting! if I turn the server edition into the Desktop will that give me exactly what I get from a clean Desktop install where I have the right characters?

I view the files in nautilus, the terminal and from putty. There are two folders on my server that are shared over a samba network, thats what I thought was the problem because it was a windows thing. But I then realized that it also happened when i used rsync and ssh, so it has to be a problem on the server.

Also if I create a directory from nautilus with the samba shares mounted, the characters show fine, but viewed on the server they turn into strange looking characters.

But I like the idea of turning the server into a full desktop if that will give me the support!

---

### Post by Braino on 2007-09-29
Hrm, that's odd. So you have filenames with special characters in them, and they don't display correctly in the terminal window. You could be using something other than Unicode, but that's not the default behavior.  What do you see when you type in 'locale -a' ? See if this article helps you at all: 
[http://www.linux.com/articles/51644]("http://www.linux.com/articles/51644")

---

### Post by kasperbs on 2007-09-30
this is what i get!
> $ locale -a
C
da_DK
da_DK.iso88591
da_DK.iso885915
da_DK.utf8
en_US
en_US.utf8
POSIX
But if it can solve it, I can as well install the full Ubuntu Desktop onto the server.

Some more Info:
I have tried to mkdir from putty (over ssh) which gives me the following:
> rudolf@ubuntu-server:~$ mkdir tæsk
rudolf@ubuntu-server:~$ ls -l
total 4
drwxr-xr-x 2 rudolf rudolf 4096 2007-09-30 13:19 t?sk
If i do it from within my ubuntu machine where the server folders are mounted with smbfs I can make a directory and that will show fine in the system i created it from which is Ubuntu but on the server it will show wrong.

---

### Post by Braino on 2007-09-30
The encoding you probably want is 'da_DK.utf8'. You should check your Ubuntu desktop to see what that command spits out, and adjust your server to have the same thing. In the link I gave you above, there are instructions to do just that (the first part under 'Reconfiguring a system for International Characters').  HTH

---

### Post by kasperbs on 2007-10-01
Hi sorry I forgot to mention that, but i have already done evrything suggested in that article. And it has been da_DK.UTF-8 from the start, so that is what I have to change. You see UTF-8 was what I choose on install and that doesn't work but neither does any of the other encodings listed from locale -a. I have tried to specify every one of them. I have even tried to specify them as the only one on the server independently.

So I think I will just go ahead and install the full blown desktop that I know have the support. Could you ellaborate on what you mentioned by going from the minimal server install to the full Ubuntu. Otherwise I will have to format and install evreything from scratch.

Thanks for all your help so far

---

### Post by Braino on 2007-10-01
I don't know how much of a help I've been :)

You can install a full-blow desktop by typing 'sudo apt-get install ubuntu-desktop' into the terminal. That's a meta-package that points to all of the other packages that are included on the desktop version.

---

### Post by kasperbs on 2007-10-01
Cheers mate then I can hopefully get the same character support as on my Ubuntu Desktop.

---

### Post by kasperbs on 2007-10-06
Well I finallt got it working with good character support. But I had to reinstall Ubuntu-Desktop from scratch, but nevermind t's working now, thanks for all the help

---

### Post by Sturmeh on 2007-10-06
Be sure to turn the spell checker on aswell. 
You'll find that very useful.

---

### Post by James79 on 2007-10-06
> **Sturmeh said:**
> Be sure to turn the spell checker on aswell. 
You'll find that very useful.

Oh the irony :roll:

---

