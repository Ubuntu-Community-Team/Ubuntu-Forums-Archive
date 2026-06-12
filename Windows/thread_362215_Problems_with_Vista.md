---
title: "Problems with Vista"
date: 2007-02-15
forum: Windows
---

### Post by matt huvu on 2007-02-15
Hi everybody,

I tried to install Ubuntu on a laptop running under Vista and,
while I was resizing the main partition, gParted told me that
this partition was corrupted, and that I had to run the following
command "chkdsk /f" under windows and  then had to reboot
my laptop twice. 

When I run this command, Windows tells me that I have a security
level that is not high enough to allow running this command!!!

So, I tried to use the windows built in device for resizing this
partition. It doesn't work anymore!!!!

I posted something on the french forum about ubuntu but nobody
seems to know how to help me.

So, if someone is able to give me some help, you are welcome ...

---

### Post by insane_alien on 2007-02-15
hmm, is your HDD encrypted? that could cause it to look corrupted. also vista's UAC is a PITA.

---

### Post by matt huvu on 2007-02-15
That's a good question, I don't know.
I didn't anything  for that so I think it's encrypted.
How do Ido to make my HDD not encrypted?

And what do UAC and PITA mean?

I know I have a big (enormous would be better) lack of technical vocabulary in english
(and it's not my mother language, I'm french (Sorry...))

Thanks for hypothetical further help... (is it a correct sentece???)

---

### Post by miseljt on 2007-02-15
Which version of Vista do you have? I think Business and Ultimate have the file encryption, but I'm not entirely sure.

---

### Post by insane_alien on 2007-02-15
Sorry, i didn't realise english wasn't your native language (the bit about posting on a french forum should have been a big clue). 

UAC is User Account Control, microsoft's flawed and horrible annoying version of sudo.
PITA, this isn't technical, its Pain In The ***.

If you haven't done anything to encrypt your HDD i don't think it will be encrypted, but with my experiences of vista so far... well... anything that can go wrong does go wrong.

---

### Post by kevinf311 on 2007-02-15
The higher versions of Vista include something called BitLocker. Here is the [French wikipedia article]("http://fr.wikipedia.org/wiki/BitLocker_Drive_Encryption") on it.

If you have BitLocker enabled then you may run into problems with the installation of other operating systems. You need to turn off bitlocker from within vista, defragment your volume, then try to resize your partition with the Live CD. Bitlocker in theory is a good system, but you can't do much when it's on. 

If your system doesn't have Bitlocker then I am not sure what could be causing the "corruption" error.

---

### Post by uNmentaLogic on 2007-02-16
> **matt huvu said:**
> Hi everybody,

I tried to install Ubuntu on a laptop running under Vista and,
while I was resizing the main partition, gParted told me that
this partition was corrupted, and that I had to run the following
command "chkdsk /f" under windows and  then had to reboot
my laptop twice. 

When I run this command, Windows tells me that I have a security
level that is not high enough to allow running this command!!!

So, I tried to use the windows built in device for resizing this
partition. It doesn't work anymore!!!!

I posted something on the french forum about ubuntu but nobody
seems to know how to help me.

So, if someone is able to give me some help, you are welcome ...


To open a command box type cmd in the search option in the start menu (first pic)then right click on it (second pic) then click on Run as administrator input password or click ok when UAC asks for confirmation then try the command again

---

### Post by matt huvu on 2007-02-18
this problem is solved but I have another one bigger now:
I've been able to install ubuntu and to resize my main partition with vista on it
but when I tried to use ubuntu after restarting my computer, it didn't work!

At this moment, vista was working normally. So I though ubuntu was not install
correctly and then I tried to reinstall it, and now vista doesn't work.

What can I do to make vista rework as before installing ubuntu?

My version of vista is "home premium".

---

### Post by kevinf311 on 2007-02-18
Could you be more specific about "doesn't work?"

Does Vista not show up in the Grub menu? Does it fail to boot? How far does it get before failing?

What size did you resize the Vista partition to?

---

### Post by matt huvu on 2007-02-19
When I start vista, I see the screen with "(c) Microsoft Coroporation"
written on the bottom of it.

After this, there's a wonderfull black screen and nothing else after !!!
Even if I wait for 1 or 2 hours to be sure that nothing happens after...

That's the reason why I say vista does'nt work (as it should have to do)...

After this bad news, I have a good one: I've been able to make ubuntu 
work normally!!! :D  

But I need vista too because I've installed some softwares that were working
under XP and that still work with vista and that I need for my studies
(mathematica,...)

---

### Post by kevinf311 on 2007-02-19
Well, congratulations on getting Ubuntu up!

I understand the need for windows applications because of school. I had a similar situation.

You may have to go in and recover Vista. I'm not sure what with installing another OS would make Vista crash (perhaps it got sad?). I have only installed the Vista Betas so I don't know how the actual installer works. In XP you could go and pretend that you were making a new XP installation and then choose for the existing XP install to be automatically repaired.

I am reluctant to tell you to do this with Vista because if they have changed the installation procedure, you may end up overwriting your existing install. If you see a way to repair the existing installation in the installer, you might try that. If you do, and it functions like the one in XP, your system files will be fixed and your programs will remain intact. You may have to reactivate your copy.

It is possible that this will also overwrite the master boot record where the grub is that lets you choose which OS to boot up. If that happens then you will have flip-flopped your operating systems :( There is however a way to recover the grub. I have not actually tried it though. The Grub section of this [HowTo]("http://www.ubuntuforums.org/showthread.php?t=358183&highlight=recover+grub") might be helpful if you loose the master boot record recovering Vista.

Good Luck!

[edit]
So I've just heard that Vista can't handle its partition being resized. So, upon installing Vista, you must create unpartitioned space to later use for Ubuntu. Here is the [thread]("http://www.ubuntuforums.org/showthread.php?p=2184558#post2184558").

---

### Post by LaRoza on 2007-04-04
I've seen that blank screen before. When I leave a flash drive with portable applications on in plugged in and try to start Vista.

On a side note, I overwrote Vista Home Premium with Ubuntu.

---

