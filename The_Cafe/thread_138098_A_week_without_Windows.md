---
title: "A week without Windows"
date: 2006-03-01
forum: The Cafe
---

### Post by knalle on 2006-03-01
Because of ongoing pressure and right out harassment from **Linux Nerds**, like my works BOFH and **Linux Security Advisor** for **Lamers TV**; **Cato Saksvik**, I have tried the following experiment; I made my Windows computer a [dualboot]("http://windows.about.com/cs/dualboot/") with Ubuntu Linux, and now I have set my self a test on now long it will take me to reboot to good old Windows.
 
I'm not going into how i installed (K)**Ubuntu Linux** because that was pretty easy, just slap in the cd and go. The only initial problems I had was to get my **Nvidia 6800** going and, this [Nvidia How to]("http://www.ubuntuforums.org/showthread.php?t=75074") from **ubuntuforums.org** helped me, later Cato called me a **lamer** and **luser** because I could just have installed **Mepis Linux** and written; “sudo nvidia-glx-config enable”. Thanks.
 
Anyway everything is up and running with Ubuntu Linux, so lets see how i survived the week:
 
[SIZE=3]**Monday:**[/SIZE]
The first thing I did was to install the **Mozilla Browser** and used **OpenOffice** to write stuff for my blog, I don't care much for the **Konqueror** browser, but thats just old habit. After writing I posted to my lamers.tv and found the expected SSH and SFTP tools. But when I wanted to create a new XHTML page I got the first problem. I'm used to **Macromedia Dreamweaver** so what could replace it? Kate, Emacs, VIM and other text editors just don't cut it to day as development tools so i was pleasantly surprised when i found [**Quanta Plus**]("http://quanta.sourceforge.net/"), a free web developer IDE for your KDE desktop.
 [B]
Quanta Plus[/B] had all the tools I expected; A node driven **project tree**, **remote synchronizing** and SFTP support,  plus it has a **good editor** with **syntax highlighting** for most known geekspeak like PHP, XHTML, CSS and Javascript. Together with **The Gimp** I found to have all the tools I needed to work remotely with my web development.
 [B]
[SIZE=3]Tuesday:[/SIZE][/B]
Mia, a friend, came by and she wanted to **secure backup** some of my musical files, I haven't tried CD burning with this distro yet, so does **K3B** work? Yes like a charm, full speed burning and verifying with my **NEC 3550A**. No problems there.
 [B]
[SIZE=3]Wednesday:[/SIZE][/B]
Cato, Lamers TV's Linux Security Advisor dropped by and after a while he was able to forgive me that i had installed **Ubuntu Linux** instead of **Mepis Linux**, an hour with biblical lectures about Mepis Linux later we decided to do a professional stress test of the system by installing and playing [Enemy Territory]("http://enemy-territory.4players.de:1041/")  on the computer. The game runs **OpenGL** but since I had fixed my Nvidia driver the game ran smoothly. We're so professional!
 [B]
[SIZE=3]Thursday:[/SIZE][/B]
Some new banners for **Lamers TV** required me to dive into **The Gimp**, after some hours I started to get a hang of the layers and the channels. I have been a payed **Adobe Photoshop** user for years so getting used to The Gimp took a while. But now I'm able to do many of the things I do in Photoshop like red eye removal and photo collages. And the nice thing is that I haven't yet found a format The Gimp cant read, even most of my old Photoshop files. Export and filters support in Gimp is also excellent. I mostly work in GIF, JPEG and PNG so I'm not much of a power user.
 [B]
[SIZE=3]Friday:[/SIZE][/B]
More professionalism, in the evening Bård, Cato and Rune gathered up to play the weekly matches of [StarCraft]("http://www.blizzard.com/starcraft/"), this posed the first real problem. How? After 60 minutes of hard tweaking of my **WINE** registry config I got **StarCraft Broodwar** running with sound and was ready to join the others on the LAN where they were waiting with their **Windows XP** running StarCraft ready machines.
 
Big grins, some mentioned the lame fact that if i had dualbooted back to Windows we could have save us a lot of time that I needed to get StarCraft running in Ubuntu Linux. But we got it all running and played happily for 3 hours before a kernel panic(?) killed my computer and I was kicked out of the game.
 
 This was my first Ubuntu Linux **crash** but a major one, everything froze, and I had to **reboot** the computer with the power button while Bård and Rune was laughing and calling me and my Linux installation names. **Owned**!
 [B]
[SIZE=3]Saturday:[/SIZE][/B]
Nothing special to report about, I took some pictures with my **Canon Ixus** and was seriously doubting that I would be able to get my photos over to my computer, but **Ubuntu Linux** found my **SanDisk**  USB reader without installing drivers like I had to in **Windows**. Nice! The pictures was also easily arranged in my home folder with **Konqueror** and the fixed in **Gimp** if they were to dark, or had to red eyes etc. I also found a nice alternative to the IRC client in Mozilla, **Konversation**  is a very nice IRC client with OSD and pop up notification! I'm starting to like this.
 [B]
[SIZE=3]Sunday:[/SIZE][/B]
Second Ubuntu Linux **crash**, don't know what happened, I had **Gimp**, **Konversation**, about 20 **Mozilla**'s, **Quanta** and **Kaffeine** running and was working when the damn computer froze on me again, no keyboard, no mouse, just freeze. Hm.... what is this?
 
I'm actually used to reboot my **Windows** weekly, so I expect the same from **Linux**, and I know it can be more stable than this, gotta investigate these freezes with some deep drilling of **/var/log**.
 
[SIZE=3]**conclusion so far:**[/SIZE]
So far I've been a Ubuntu Linux user for about a month now, but I was dualbooting a lot because I simply didn't take the time to find the alternatives to the way I work in Windows. So far I've been very pleased, especially with **Quanta Plus**, I haven't rebooted to Windows for about 1 and a half week now.
 

**  Happy Hacking!**

---

### Post by nocturn on 2006-03-01
Just a quick note on the crashing.

I had this a lot with some Nvidia drivers and RenderAccel on.  Check your xorg.log file for Xid errors.  

The symptom is a completely frozen desktop (even the clock in Gnome), but I was always still able to SSH in from other machines.

Anyway, good luck.

---

### Post by FoxLogic on 2006-03-01
Kubuntu always froze on me as well.  I got the Gnome version of it and haven't had that problem.

---

### Post by DrFunkenstein on 2006-03-01
[QUOTE=FoxLogic]Kubuntu always froze on me as well.  I got the Gnome version of it and haven't had that problem.[/QUOTE]
How about some more information?
What version was it, what hardware did you use, did you also have an nvidia card, might it have been related to the RenderAccel bug nocturn mentioned?


Anyway, to the OP, very good read and it's great that you enjoy Kubuntu thus far. And of course, had you used mepis, you'd not experience these freezes, I'm sure. ;) (SCNR)

---

### Post by knalle on 2006-03-01
[QUOTE=DrFunkenstein]And of course, had you used mepis, you'd not experience these freezes, I'm sure. ;) (SCNR)[/QUOTE]

I know, everything is bliss in Mepis, according to certain geeks i know \\:D/

---

### Post by FoxLogic on 2006-03-01
[QUOTE=DrFunkenstein]How about some more information?
What version was it, what hardware did you use, did you also have an nvidia card, might it have been related to the RenderAccel bug nocturn mentioned?
[/QUOTE]


nVidia? are you kidding?  Imagin the guy from Mortal Kombat that would say "Don't make me laugh".

Man I use ATI.

---

### Post by Brunellus on 2006-03-01
[QUOTE=FoxLogic]nVidia? are you kidding?  Imagin the guy from Mortal Kombat that would say "Don't make me laugh".

Man I use ATI.[/QUOTE]
Imagine the guy from Mortal Kombat saying "FATALITY."

ATI's binary-only drivers for Linux are rubbish;  the open-source drivers are not good, either.  If you want hardware rendering that works with Linux, you are more or less compelled to use nvidia hardware and their binary drivers.  

All the spec-sheet chest thumping is useless if your card doesn't have proper driver support.

---

### Post by BoyOfDestiny on 2006-03-01
[QUOTE=Brunellus]Imagine the guy from Mortal Kombat saying "FATALITY."

ATI's binary-only drivers for Linux are rubbish;  the open-source drivers are not good, either.  If you want hardware rendering that works with Linux, you are more or less compelled to use nvidia hardware and their binary drivers.  

All the spec-sheet chest thumping is useless if your card doesn't have proper driver support.[/QUOTE]

The open source drivers are not good? They are great!

I'm using the open source drivers for my 9250 based card, and the x300 in my laptop seems to have dri in dapper without fglrx.

They work for me, meaning they provide 3d acceleration. Are they not good in the sense you can't squeeze all the performance out of the card? Frankly I rather just use the open drivers since they are open...

---

### Post by knalle on 2006-03-01
[QUOTE=Brunellus]Imagine the guy from Mortal Kombat saying "FATALITY."
[/QUOTE]

man Mortal Kombat, I'm talkin **Starcraft** here, then its more like: "nuclear launch detected" :)

---

### Post by commodore on 2006-03-01
How can someone call himself a geek if he uses Windows? It's not even UNIX based.

---

### Post by knalle on 2006-03-01
[QUOTE=commodore]How can someone call himself a geek if he uses Windows? It's not even UNIX based.[/QUOTE]

please, i'm not a **geek**, i'm a **lamer**, see [http://lamers.tv/](http://lamers.tv/), my blog about how lame i am.

---

### Post by DrFunkenstein on 2006-03-01
[QUOTE=commodore]How can someone call himself a geek if he uses Windows? It's not even UNIX based.[/QUOTE]
This has got to be the lamest forum post I ever read.

P.S.: lamers.tv, great name for a website.:-D

---

### Post by phen on 2006-03-01
kaffeine makes my laptop chrash, too. Sometimes, it simply freezes everything. the last crash happend when some friends were visiting me.. .. -Exactly! indeed they were THOSE friends, i always try to convince to use linux by saying "it is much more stable than your louse windows"

grrrr

---

### Post by knalle on 2006-03-01
[QUOTE=phen]indeed they were THOSE friends[/QUOTE]

they laugh at me for the smallest problems, and when we go out i have to buy beer

---

### Post by briancurtin on 2006-03-01
[QUOTE=knalle]Kate, Emacs, VIM and other text editors just don't cut it to day as development tools[/QUOTE]
haha

---

### Post by briancurtin on 2006-03-01
[QUOTE=commodore]How can someone call himself a geek if he uses Windows? It's not even UNIX based.[/QUOTE]
this is funny too

---

### Post by xequence on 2006-03-01
[QUOTE=commodore]How can someone call himself a geek if he uses Windows? It's not even UNIX based.[/QUOTE]

I feel my avatar says my reply to that post o_O

---

### Post by FoxLogic on 2006-03-01
[QUOTE=Brunellus]Imagine the guy from Mortal Kombat saying "FATALITY."

ATI's binary-only drivers for Linux are rubbish;  the open-source drivers are not good, either.  If you want hardware rendering that works with Linux, you are more or less compelled to use nvidia hardware and their binary drivers.  

All the spec-sheet chest thumping is useless if your card doesn't have proper driver support.[/QUOTE]


Donno what your talking about, but I've never had an Issue with my ATI card in Linux, not on any distro.  It shows up exactly how it's suppose to show up and actually, I get more FPS in games designed on Windowns, on the Linux ports.  Not only that FPS usually is around 70 to 78 FPS in America's Army.

Don't feed me that bull, my ATI card works wonders on my computer.

I would believe if you are having trouble, ask me for ATI help then.

---

### Post by Bandit on 2006-03-01
[QUOTE=FoxLogic]Donno what your talking about, but I've never had an Issue with my ATI card in Linux, not on any distro.  It shows up exactly how it's suppose to show up and actually, I get more FPS in games designed on Windowns, on the Linux ports.  Not only that FPS usually is around 70 to 78 FPS in America's Army.

Don't feed me that bull, my ATI card works wonders on my computer.

I would believe if you are having trouble, ask me for ATI help then.[/QUOTE]
My card is a 9250 also, even tho the box advirtised 9200SE. Under Breezy32bit my card works great also. Not a single problem. Under Breezy64bit there is some kind of bug but I am sure it will be fixed in Dapper very soon.
Cheers,
Joey

EDIT: My 9250 is slower then my FX5500. Of course the 9250 only has 126MB RAM and 64bit interface were the FX5500 has 256MB RAM and 128bit interface. But the 9250 doesnt crash like a blindfolded drunk every 5 minutes..

---

