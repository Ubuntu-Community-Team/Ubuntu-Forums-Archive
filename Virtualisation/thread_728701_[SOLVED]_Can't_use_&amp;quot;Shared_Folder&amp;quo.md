---
title: "[SOLVED] Can't use &amp;quot;Shared Folder&amp;quot; of Virtual Box"
date: 2008-03-19
forum: Virtualisation
---

### Post by x86scorpion on 2008-03-19
Hi to all! newbie here! :)

[IMG]http://i26.tinypic.com/312b90n.jpg[/IMG]

```
I've installed Virtual Box properly 'till I'm stuck on using "Shared Folder".
```

[IMG]http://i25.tinypic.com/2qjhsep.jpg[/IMG]

>>   net use x: \\vboxsvr\XPFiles

then I got this error.

system error 53 has occured.
the network path was not found.

??? but I could even get online.

[IMG]http://i28.tinypic.com/2ij4oi.jpg[/IMG]

please help, thanks!


Ubuntu Desktop Edition 7.10
AMD Athlon(tm) LE-1620 2.40 GHz
EMX-AMD690HD
2GB RAM
80GB SATA

---

### Post by Kiri on 2008-03-19
Have you tried doing it the explorer way?

> In a Windows guest, starting with VirtualBox 1.5.0, shared folders are browseable and are therefore visible in Windows Explorer. So, to attach the host's shared folder to your Windows guest, open Windows Explorer and look for it under "My Networking Places" -> "Entire Network" -> "VirtualBox Shared Folders". By right-clicking on a shared folder and selecting "Map network drive" from the menu that pops up, you can assign a drive letter to that shared folder.



---

### Post by stalker145 on 2008-03-19
> **Kiri said:**
> Have you tried doing it the explorer way?

Dang, beat me to it.

> **x86scorpion said:**
> >>   net use x: \\vboxsvr\XPFiles

then I got this error.

system error 53 has occured.
the network path was not found.

The suggestion above is how I do it. Open up the Network Neighborhood, search Entire Network, and then Virtualbox Share Folders. If you want to have a persistent connection every time you start the VM, you can simply use Map Network Drive.

Bingo

---

### Post by x86scorpion on 2008-03-19
```
...
```
[IMG]http://i27.tinypic.com/2efmdg2.png[/IMG]
```
...
```
[IMG]http://i27.tinypic.com/fum73a.jpg[/IMG]
```
...
```
[IMG]http://i28.tinypic.com/2zthde9.png[/IMG]
```
...
```

sorry guys I don't see it,
please help, I DON'T GET IT! :confused:

WinXP loads fine, AUDIO/CD-ROM/USB's working...
everything seems to be OK except this "Shared Folder"

I'm using VirtualBox 1.5.6

---

### Post by Kiri on 2008-03-19
In your screenshot it shows that your shared folder alias is "\\vboxsvr\VirtualFiles".
You need to use this exact name when you mount the drive.
So you should type:
net use x: \\vboxsvr\VirtualFiles

---

### Post by x86scorpion on 2008-03-19
[IMG]http://i32.tinypic.com/2z6hu9t.png[/IMG]

still the same... :confused:
thanks for hanging up Kiri

---

### Post by Kiri on 2008-03-19
Hmm, are you running XP with admin rights or logged in as administrator?

---

### Post by x86scorpion on 2008-03-19
[IMG]http://i30.tinypic.com/2na5jrs.png[/IMG]

Didn't change anything from here.

---

### Post by Kiri on 2008-03-19
You DID install guest additions right?
From the VM window menu:
"Devices>Install Guest Additions"

---

### Post by x86scorpion on 2008-03-19
when I click 

Devices >> Install Guest Additions

nothing happens

---

### Post by x86scorpion on 2008-03-19
I was about to ask, What do we mean of
"This feature requires Guest Addition" ?

---

### Post by Kiri on 2008-03-19
you have to mount the cd-rom image file (from the same devices menu in your VM) which has the vbox guest additions.
Its in the vbox folder where you installed vbox and is named  "vboxguestadditions.iso"

---

### Post by x86scorpion on 2008-03-19
[IMG]http://i26.tinypic.com/e01nd3.png[/IMG]

came up with this, what should I do next?

---

### Post by Kiri on 2008-03-19
This is in your windows guest VM right?
Then double click the VBoxGuestAdditions and install it. It should also work from the device menu now it is mounted like I described before...

---

### Post by x86scorpion on 2008-03-19
[IMG]http://i26.tinypic.com/2hs1d0i.png[/IMG]
[IMG]http://i32.tinypic.com/2qtlix3.png[/IMG]


WOWWW!!! works perfect now!!! :biggrin:

You deserve to be a member of Ubuntu Forums. Patient enough to guide a newbie like me! Thanks for sharing your knowledge!!! 

Here's my 5star for you!!!
THANKS Kiri :KS:KS:KS:KS:KS

---

### Post by Kiri on 2008-03-19
Haha! Thanks! :)
Actually I'm a newbie too though. I only started using virtualbox this week, and linux last week, so I know how confusing it is. 
Anyway, glad it worked for you. Maybe you will help me next time ;)
:KS Peace

---

### Post by x86scorpion on 2008-03-19
[IMG]http://i29.tinypic.com/30svaz8.png[/IMG]

> **Kiri said:**
> Anyway, glad it worked for you. Maybe you will help me next time ;)
:KS Peace

SURE! as long as I can, why not :wink:
I will never forget Kiri who gave the first shot of my Ubuntu experience! :)

---

