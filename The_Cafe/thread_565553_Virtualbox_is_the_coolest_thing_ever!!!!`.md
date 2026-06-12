---
title: "Virtualbox is the coolest thing ever!!!!`"
date: 2007-10-02
forum: The Cafe
---

### Post by jrharvey on 2007-10-02
I just installed 32bit windows in my 64 bit ubuntu with virtualbox. Would you believe that windows is actually running my 3d architecture programs faster and better than it does when I natively boot windows. That is astonishing to me.

---

### Post by notwen on 2007-10-02
VBox is the goodness. =]

---

### Post by ukripper on 2007-10-02
+1:)

---

### Post by stimpack on 2007-10-02
I love it, they give us the same GUI as on the Windows version, not some command line alternative. This is a *true* cross platform app and it does its job in an incredibly easy to use way.

---

### Post by Incense on 2007-10-02
Seamless mode is pretty awesome.

---

### Post by n3tfury on 2007-10-02
> **Incense said:**
> Seamless mode is pretty awesome.

sure is!!!

mine:

---

### Post by Ozor Mox on 2007-10-02
Would this enable me to install Windows XP within this application and then install Windows software like games natively? Does it save what you've installed in a virtual drive on the computer somewhere?

---

### Post by maybeway36 on 2007-10-02
To install VirtualBox with APT:
```
sudo echo "deb http://www.virtualbox.org/debian feisty non-free" >> /etc/apt/sources.list
wget -q -O- http://www.virtualbox.org/debian/innotek.asc | sudo apt-key add -
sudo apt-get update
sudo apt-get install virtualbox
```

---

### Post by RageOfOrder on 2007-10-02
> **maybeway36 said:**
> To install VirtualBox with APT:
```
sudo echo "deb http://www.virtualbox.org/debian feisty non-free" >> /etc/apt/sources.list
wget -q -O- http://www.virtualbox.org/debian/innotek.asc | sudo apt-key add -
sudo apt-get update
sudo apt-get install virtualbox
```

To install VirtualBox with Portage
```
# emerge virtualbox
```

:popcorn:

---

### Post by maniacmusician on 2007-10-02
> **stimpack said:**
> I love it, they give us the same GUI as on the Windows version, not some command line alternative. This is a *true* cross platform app and it does its job in an incredibly easy to use way.

I think that's largely because it uses Qt as its toolkit, and Qt is really big on being cross-platform.

---

### Post by maybeway36 on 2007-10-02
> **RageOfOrder said:**
> To install VirtualBox with Portage
```
# emerge virtualbox
```

:popcorn:

Yeah, some people have it in their own repos :P

---

### Post by jrharvey on 2007-10-02
It wont let me enable seamless mode. That looks freakin awsome and I want to try it but what do I have to do???

---

### Post by stimpack on 2007-10-02
you need VB 1.5 then you need to install the new 1.5 virtual additions in windows.

---

### Post by Incense on 2007-10-02
> **Ozor Mox said:**
> Would this enable me to install Windows XP within this application and then install Windows software like games natively? Does it save what you've installed in a virtual drive on the computer somewhere?

Yes you can install XP in virtual Box, and some games work alright. Most recent games need a real graphics card, and the virtual one just doesn't cut it. Most hard core gamers will set up a duel book. Your OS would be stored as one big file on your drive that you can back up, or move to other systems if you need. 

Good times!
:guitar:

---

### Post by jrharvey on 2007-10-02
I can't seem to get the shared folder's working or USB flash memory. Is this dissabled in the free version?

---

### Post by mips on 2007-10-02
> **jrharvey said:**
> I can't seem to get the shared folder's working or USB flash memory. Is this dissabled in the free version?

Nope it is enabled. Check the virtualbox website, there is a howto for the USB. Shared folders should just work once you set them up in vb.

---

### Post by Incense on 2007-10-02
> **jrharvey said:**
> I can't seem to get the shared folder's working or USB flash memory. Is this dissabled in the free version?

The shared folder will show up as a network drive, so check through my network places if you have a windows guest. USB is a bit more complicated. Generic devices like keyboards and mice work fine, but other devcies take a bit of work.

---

### Post by jrharvey on 2007-10-02
Thanks guys sooo much. I didnt mean for this to be a help me thread but i guess i did have a couple of questions. I got my shared folders and my usb drive working. Its incredibly fast and I still dont understand why its faster than a native install of xp but i guess it has something to do with the difference between 32bit and 64bit architecture.... Maybe. What a wonderfull program and thanks to whoever designed it.

---

### Post by Frak on 2007-10-02
But, no gutsy version yet :(

Oh well, compiling from source never hurt anyone :)

---

### Post by GSF1200S on 2007-10-02
> **jrharvey said:**
> Thanks guys sooo much. I didnt mean for this to be a help me thread but i guess i did have a couple of questions. I got my shared folders and my usb drive working. Its incredibly fast and I still dont understand why its faster than a native install of xp but i guess it has something to do with the difference between 32bit and 64bit architecture.... Maybe. What a wonderfull program and thanks to whoever designed it.

I think its faster because the 3d program is running from a .vdi. Im not sure why, since a .vdi file is in fact stored on the hard drive, but a fresh install of Windows on a hard drive seems slower than a VBox install.

And im really glad it works so well for you :) I use VBox myself and I love it. I really like the dynamically expanding .vdi's too. It literally only uses space when you need it.

I really hope something is worked out with 3d games in Vbox one day, although realistically it prolly wont happen for 3-4 years. Thats a pretty big feat, and its going to be even harder with DX10, DX11, etc...

---

### Post by Frak on 2007-10-02
> **GSF1200S said:**
> I think its faster because the 3d program is running from a .vdi. Im not sure why, since a .vdi file is in fact stored on the hard drive, but a fresh install of Windows on a hard drive seems slower than a VBox install.

And im really glad it works so well for you :) I use VBox myself and I love it. I really like the dynamically expanding .vdi's too. It literally only uses space when you need it.

I really hope something is worked out with 3d games in Vbox one day, although realistically it prolly wont happen for 3-4 years. Thats a pretty big feat, and its going to be even harder with DX10, DX11, etc...
The closests to Graphics is VMware, and they can only do it on Windows with DX9. Its still sketchy also.

Yeah, it will be a big feat to get. Though I give it 5 years+

---

### Post by Incense on 2007-10-02
> **Frak said:**
> But, no gutsy version yet :(

Oh well, compiling from source never hurt anyone :)

I got it running by adding the fiesty repo, and using apt-get install virtualbox. Seamless isn't quite as nice (the windows task bar sat in front of the kpanel), and it seemed to run a bit slower, but it worked.

---

### Post by GSF1200S on 2007-10-02
> **Frak said:**
> The closests to Graphics is VMware, and they can only do it on Windows with DX9. Its still sketchy also.

Yeah, it will be a big feat to get. Though I give it 5 years+


Yeah, that sounds about right. Im aware that VMware was working on this. I dont know how hard it will be once the technology is developed to actively keep up with DX releases, though.

Oh well, im 23.. I should be able to see it sometime in my lifetime. Oh man that would be awesome.

Of course, as ive gotten into Linux, ive had less and less to do with gaming. I just would rather tinker with linux or web design or... or... its been such a good thing for me. Games are fiction and thats where Windows left me; Linux has by some weird twist introduced me to REAL fundamental issues, wants, etc.

So, ehh, if it never happens it wont matter to me.

---

### Post by Frak on 2007-10-02
> **Incense said:**
> I got it running by adding the fiesty repo, and using apt-get install virtualbox. Seamless isn't quite as nice (the windows task bar sat in front of the kpanel), and it seemed to run a bit slower, but it worked.
Thx, didn't think of using an old package.

---

### Post by mips on 2007-10-03
> **Frak said:**
> But, no gutsy version yet :(

Oh well, compiling from source never hurt anyone :)

Why do you want to make things so hard for yourself ?

Just download v1.5 for feisty, [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)
and install it in Gutsy, works fine.

---

### Post by n3tfury on 2007-10-03
> **Incense said:**
> Iand it seemed to run a bit slower, but it worked.

anybody else with gutsy want to comment? that's not such good news :/

---

### Post by vikrant82 on 2007-10-03
Vbox is as cool with Gutsy as it was with Feisty , may be he's talking about seamless mode being slow. Havent noticed it though.

---

### Post by mips on 2007-10-03
> **vikrant82 said:**
> Vbox is as cool with Gutsy as it was with Feisty , may be he's talking about seamless mode being slow. Havent noticed it though.

Same here, vb 1.5 running just fine on my & a friends laptop with gutsy.

---

### Post by n3tfury on 2007-10-03
awesome,thanks.

---

### Post by Incense on 2007-10-03
> **vikrant82 said:**
> Vbox is as cool with Gutsy as it was with Feisty , may be he's talking about seamless mode being slow. Havent noticed it though.

Could have been because I'm in Kunbuntu? Not too sure really. I was seamless that felt slow. Could just be my system though. I'm sure once Gusty is gold and they have an official package we'll have no problems. The joys of beta. Glad it's working fine for you guys!

---

### Post by dondad on 2007-10-03
> **Frak said:**
> But, no gutsy version yet :(

Oh well, compiling from source never hurt anyone :)

The fiesty .deb from the virtualbox website works fine in Gutsy. I have an install in the fiesty partition of my computer. I installed the fiesty deb in Gutsy, then copied the disk file from the fiesty partition and was up and running.

---

### Post by Incense on 2007-10-03
> **dondad said:**
> The fiesty .deb from the virtualbox website works fine in Gutsy. I have an install in the fiesty partition of my computer. I installed the fiesty deb in Gutsy, then copied the disk file from the fiesty partition and was up and running.

When I did it that way the kernel would not compile. Maybe the devs fixed it since then, or my system just didn't like it.

---

### Post by Frak on 2007-10-03
> **Incense said:**
> When I did it that way the kernel would not compile. Maybe the devs fixed it since then, or my system just didn't like it.
It may just be your kernel, I tried it and it worked fine :) (Thanks everybody)

---

### Post by Incense on 2007-10-03
> **Frak said:**
> It may just be your kernel, I tried it and it worked fine :) (Thanks everybody)

:lolflag: Thanks for making me the odd guy out Gutsy!

---

### Post by aktiwers on 2007-10-03
[http://ubuntuforums.org/showthread.php?t=433359](http://ubuntuforums.org/showthread.php?t=433359)

---

