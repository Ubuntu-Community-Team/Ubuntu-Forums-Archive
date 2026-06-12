---
title: "Guide to Curse Client on Ubuntu 10.04"
date: 2010-05-25
forum: Wine
---

### Post by acidviews on 2010-05-25
Ok this is what i did firstly i installed wine
second a installed wine tricks 
wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
then
sh winetricks corefonts vcrun6

now to install i.e.6

sh winetricks

i then added .net 2.0 

although these are not the latest i have found them to work

this is when i installed curse 3 ( old version)
and i configured wine to run curse exe with the libry of inetcomm
in xp mode


And there we have it u should have a working version of client to
keep all of ya mods up 2 date ;)

---

### Post by ath88 on 2010-06-29
I did exactly as you described, i get to install it, but when i run CurseClient.exe through wine, i get to log in, but the window i just all gray. 

Got any ideas? Its quite annoying. :)

- ath88

---

### Post by amenfex on 2010-07-20
> **ath88 said:**
> I did exactly as you described, i get to install it, but when i run CurseClient.exe through wine, i get to log in, but the window i just all gray. 

Got any ideas? Its quite annoying. :)

- ath88

Having the same issue as well. 

But i didn't actually do one of the steps.

installing .net file because it wasn't listed like ie6 was.

---

### Post by amenfex on 2010-07-20
Wait, nevermind.

i accidently skipped the "sh winetricks corefonts vcrun6" part

woo hoo, thank you!

---

### Post by Melisandrew on 2011-05-27
Ive managed to install the program( curse) and im getting the grey screen, but i cant figure out where to install ie6 there is no prompt. do I simply go to its website? or what?

---

### Post by amenfex on 2011-05-27
I had the same issue but realized I skipped a step. 

It wouldn't hurt to double check and see if you missed a step.

---

### Post by Melisandrew on 2011-05-28
ive checked, double and triple checked. and i keep getting the error message 
Winetricks now lives in the svn repository at [http://winetricks.org](http://winetricks.org)

nothing pops up to search for the ie6 package. and when i go into winetricks itself it isnt in there......

---

### Post by Tweak42 on 2011-05-30
You need to use IE8 for the latest version of curse client.  If it hangs at login, just kill it and run it again.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=22334&iTestingId=59984](http://appdb.winehq.org/objectManager.php?sClass=version&iId=22334&iTestingId=59984)

---

### Post by Tweak42 on 2011-07-05
FYI: something borked the v3 curse client around 6/28.
[LIST]
[*]It's recognizing out-of-date addon need updates
[*]But is failing to download addons updated after 6/28.  
[*]Old addons seem to download, but not the ones updated after 4.2 patch.
[/LIST]
If you are using the v3 client please file a [detailed ticket]("http://clientsupport.curse.com/") to show your support so hopefully curse notices us and fixes it.  Make sure you mention you are using the _v3 curse client_ or you will more than likely get a canned windows answer for the v4 client that we cannot use.

---

### Post by raven2099 on 2012-11-28
how about 12.10???

i got wow working fine but curse runs into probs with the .net instalation

---

### Post by Tweak42 on 2012-11-28
> **raven2099 said:**
> how about 12.10???

i got wow working fine but curse runs into probs with the .net instalation

AFAIK because the v4 and v5 of the Curse client requires .NET installation it will not work under Wine.  Recent updates to support .NET under wine may have changed that as I haven't attempted in a year or so, but I doubt it.

The workaround I ended up using was to the Curse client in a Windows XP virtual machine and network share my WoW directory so the Curse client can update it.

---

### Post by raven2099 on 2012-12-01
mine harasses me a bout a .net pack even though i installed them all

12.10

---

