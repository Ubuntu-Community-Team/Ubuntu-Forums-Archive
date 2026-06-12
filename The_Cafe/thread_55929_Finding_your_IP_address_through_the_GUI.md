---
title: "Finding your IP address through the GUI"
date: 2005-08-10
forum: The Cafe
---

### Post by agger on 2005-08-10
Kerberos wrote, [in another thread](http://www.ubuntuforums.org/showthread.php?t=53286&page=8&pp=10) :
> So Linux is somehow better for normal users because it only lets you check your IP (and do god knows what else) through the command line only?

Surely your not seriously saying that having boxes _right there_ that can contain useful information, yet dont, is somehow a good thing? That the only way to find it out is by typing an unguessable command into the terminal, and this is somehow making Linux better?

If you go to Applications/System Tools/Network Tools in the GNOME menu, for "Network device" choose the network card you're using for your LAN - prolly "Eth1".

And presto, it shows your IP address!

Actually, that's how Ubuntu usually is: Any information about your system you can find on M$-Windows you will also be able to find through Ubuntu's GUI. Later, when used to using Ubuntu, you may grow to love the command line as well, I know I have  :-)

---

### Post by sapo on 2005-08-10
Whats so difficult about:

Clicking with the right button in the top panel -> Add to Panel -> Network Monitor.. and then:

oh.. its a miracle, i have my ip adress on the screen :rolleyes:

[[IMG]http://img360.imageshack.us/img360/5346/screenshot20vx.th.png[/IMG]](http://img360.imageshack.us/my.php?image=screenshot20vx.png)

---

### Post by aysiu on 2005-08-10
Frankly, GUI support for the finding of IP addresses isn't what makes an OS superior to another OS, but as above folks have mentioned--the GUI is possible. What makes Linux "superior" for me (as no OS can be inherently superior to another OS--it's all about the user) is:

1. Free licensing (no stupid activation keys)
2. Choice of software, choice of OS, choice of desktop, choice of decorations and icons--choice, choice, choice
3. Ease of customization (linked to choice)--Windowblinds was a pain in my...
4. Free cost for OS, free cost for software
5. Community--when I have Windows problems, I don't know where to turn, and often Googling does not help
6. Security. Linux was built with a secure user set-up. When you don't run as administrator in Windows, updating and using some applications can be a pain in the...
7. Ease of software installation. I used to be a big fan of setup.exe, next, next, next, finish, reboot, but Synaptic Package Manager is cool, and I almost never need programs that aren't in the repositories.

But that's just me. As I said before, it's all about user preference. For some users, what makes an OS superior to another is graphically being able to check the IP address. To each her own. I'm just glad I don't feel the compulsion to sign up for some Windows forum just to bash Windows.

---

### Post by egon spengler on 2005-08-10
[QUOTE=agger]Kerberos wrote, [in another thread](http://www.ubuntuforums.org/showthread.php?t=53286&page=8&pp=10) :


If you go to Applications/System Tools/Network Tools in the GNOME menu, for "Network device" choose the network card you're using for your LAN - prolly "Eth1".

And presto, it shows your IP address!

Actually, that's how Ubuntu usually is: Any information about your system you can find on M$-Windows you will also be able to find through Ubuntu's GUI. Later, when used to using Ubuntu, you may grow to love the command line as well, I know I have  :-)[/QUOTE]

That only shows my LAN adress, what about WAN?

[QUOTE=sapo]Whats so difficult about:

Clicking with the right button in the top panel -> Add to Panel -> Network Monitor.. and then:

oh.. its a miracle, i have my ip adress on the screen :rolleyes:
[/QUOTE]

I don't use gnome, how would I do that in fluxbox?

---

### Post by Sam on 2005-08-10
[QUOTE=egon spengler]That only shows my LAN adress, what about WAN?[/QUOTE]
Create a launcher and use this command:
```
zenity --info --info-text `w3m www.whatismyip.com -dump_source|grep "<TITLE>"|cut -d " " -f 5`
```

Then you'll have you gui wan ip tool :wink:

---

### Post by RastaMahata on 2005-08-10
when I tell people to give me their IP, i tell them to go to [www.whatismyip.com](www.whatismyip.com)
It's far easier for them to do that, no matter what system they're using.

---

### Post by npaladin2000 on 2005-08-11
Actually, there's only one way to find out your IP address in Windows2000 or WindowsXP unless you're using static IP.  That way happens to be the command line.   Sorry.  :)

---

### Post by TravisNewman on 2005-08-11
[QUOTE=npaladin2000]Actually, there's only one way to find out your IP address in Windows2000 or WindowsXP unless you're using static IP.  That way happens to be the command line.   Sorry.  :)[/QUOTE]
 um... the network status gui has it. The internal IP anyway. External, I don't know a command or a gui built in to tell you

---

### Post by agger on 2005-08-11
[QUOTE=panickedthumb]um... the network status gui has it. The internal IP anyway. External, I don't know a command or a gui built in to tell you[/QUOTE]

The original "dealbreaker" for our friend Kerberos was the perceived lack of a GUI to display the LAN IP address.

If the WAN IP address is different because the network uses NAT, a firewall or
some such device, I don't see how you could find out without depending on 
some external site. So the easiest and most userfriendly way to determine your
WAN IP address is to point your browser to [www.myipaddress.com](www.myipaddress.com) or to use
a launcher as Sam made above ... :-)

---

### Post by jerome bettis on 2005-08-11
[QUOTE=Sam]Create a launcher and use this command:
```
zenity --info --info-text `w3m www.whatismyip.com -dump_source|grep "<TITLE>"|cut -d " " -f 5`
```

Then you'll have you gui wan ip tool :wink:[/QUOTE]


LOL very very nice

where'd you learn that?  anymore tricks like that you know of?

---

### Post by Sam on 2005-08-11
[QUOTE=jerome bettis]LOL very very nice

where'd you learn that?  anymore tricks like that you know of?[/QUOTE]
lol glad you like it ! This is someone in the forum who posted the trick about parsing whatismyip.com source. I made a bash script for myself and post it with zenity in order to have a gui tool... :-P

Other tricks like that ??? Uh my box has a lot of tiny things added on the fly, I cannot made a list with each of them... But when someone has a problem and I have something helpful I try to help ! Ask if you have a particular problem...

---

### Post by FLeiXiuS on 2005-08-11
Oh download the gdesklet to display it on your desktop.  :-)  It'll do internal and external.

---

