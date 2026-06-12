---
title: "Cannot run/Start Runes of Magic using wine. clientupdte.exe error message Help needed"
date: 2010-07-31
forum: Wine
---

### Post by scrypt on 2010-07-31
Hello all.

I recently installed Runes of magic using the latest version of Wine on my Ubuntu Lucid (10.04) Installation.

All seemed to be working well until I tried to start Runes of Magic from the desktop icon. It opened RoM launcher, and then began to update Clientupdate.exe and the various RoM Patches. They also seemed to be installing okay. That was until what looked like right before Runes of Magic was about to start. I was then met with an old looking Windows error message that stated:

Clientupdte.exe has encountered an error and needs to close. please go to wine/hq for a solution. I have searched thoroughly for a fix, and not been able to find one. I am hoping somebody here may be able to help me fix this.

 has anyone here ver had a similar issue and found a solution to get Runes of Magic working?

 Can snybody help me fix this please

Scrypt

---

### Post by scrypt on 2010-07-31
I managed to fully install all Runes of Magic Patches and all Client.exe updates after installing Winetricks and then installing Windows ie6 (Internet Explorer 6).

I installed Windows ie6 using ubuntu terminal ans using command:

sh winetricks ie6

I then followed all prompts using default values to install Windows ie6.

All updates and patches seemed to install fine. I could the click start game on RoM Launcher. But Runes of Magic would not start.
I am met with A Black screen as though RoM is loading and about to start and then I am met this error message::

A Critical error has occurred and the game will be shut down. Please use the button below to send an error report to Runewalker. We will treat this report as confidential and annonymous.

I am so close to getting Runes of Magic working now apart from this issue.
Does anybody know how to fix this problem

Scrypt

---

### Post by scrypt on 2010-08-01
Hello

I am still having problems starting/Running Runes of Magic using Wine.

Instaling Winetricks and using that ti install wininit and ie6 had helped a little.
I can now start rom and i am met with a screen with a women standing with a bow and arrow and falling leaves, and the games introduction Music. But that is it. I can get NO further. I canot play RoM either.

Can any body help me to fix this ?

---

### Post by scrypt on 2010-08-01
Still needing help with this

---

### Post by nixIT on 2010-08-03
I found this link on the net, followed it and BAM, was able to play RoM in Ubuntu 10.04.

[http://timashley.me/node/265](http://timashley.me/node/265)

However, instead of the directx that it suggests installing, I installed the d3dx9 package, and I did not install vcrun2005sp1.

I can say, that until I followed this guide, I could not get RoM running, I would get the same client error as you.

Also, if you get the error, you will need to end the clientupdate process in order to re-run and play the game.

hope this helps


--nixIT

---

### Post by scrypt on 2010-08-03
Thank-You for your reply nixIT.

I will give your suggestions a try, and post back how I get on

Scrypt

---

