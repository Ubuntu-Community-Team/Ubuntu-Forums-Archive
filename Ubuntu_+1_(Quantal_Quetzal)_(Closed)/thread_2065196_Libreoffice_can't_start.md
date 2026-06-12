---
title: "Libreoffice can't start"
date: 2012-10-01
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Milos_SD on 2012-10-01
Hello. I upgraded to 12.10 yesterday, and now I can't start Libreoffice apps. There is no segfault or any other error, it just shows splash screen and that is it, no loading or anything. I have 64bit version of Ubuntu, and I used to have simular problem with libreoffice 3.6 from ppa in 12.04.

---

### Post by grahammechanical on 2012-10-01
Have you removed that ppa from Software Sources? Have you tried Un-installing and re-installing through the Software Centre?

Regards.

---

### Post by Milos_SD on 2012-10-01
I removed that PPA right away, when I noticed it doesn't work. I'm going to reinstall libreoffice right now, but I don't think if will help.

---

### Post by mlentink on 2012-10-01
I have the exact same problem, which I have also posted as a question (not yet as a bug) on [Launchpad]("https://answers.launchpad.net/ubuntu/+source/libreoffice/+question/209850"). To add, I also get a warning: 
```
Fontconfig warning: "/usr/lib/libreoffice/share/fonts/truetype/fc_local.conf", line 13: Having multiple <family> in <alias> isn't supported and may not works as expected
```, but this is most likely *unrelated*, and already reported as a bug.
I do not have the ppa installed and removed/purged and then reinstalled lo already, without results.

---

### Post by Milos_SD on 2012-10-01
Here is the output of command: soffice --valgrind

[http://pastebin.com/zF24Cutd](http://pastebin.com/zF24Cutd)

Edit: And here is dmesg part:

```
[20450.672054] soffice.bin[22341]: segfault at 0 ip 00007f4ae08645f0 sp 00007fff0f5d3998 error 4 in libuno_sal.so.3[7f4ae0838000+4f000]
```

---

### Post by mlentink on 2012-10-03
Hi Milos_SD,

Did you get any further with this? If there is something I can do please let me know. In the evening I'll have a look to see whether OO has the same behavior, but at the moment I'm stuck. LO is simply not useable in 12.10 64bit

---

### Post by dino99 on 2012-10-03
no problem on i386 :P

---

### Post by Milos_SD on 2012-10-03
> **mlentink said:**
> Hi Milos_SD,

Did you get any further with this? If there is something I can do please let me know. In the evening I'll have a look to see whether OO has the same behavior, but at the moment I'm stuck. LO is simply not useable in 12.10 64bit

Well, only that it is the same error I had on 12.04 with LO 3.6 from PPA. It has something to do with "libuno". Maybe some problem with java? What java version do you have? I have Oracle Java 8 beta from webupd8 ppa (and it was the same with oracle java 7).

---

### Post by dino99 on 2012-10-03
i've purged previous oracle package since there is some insecurity with java; so only using openjdk now.

---

### Post by thotz on 2012-10-03
Hi, I opened Libreoffice and got an error.

Filed this bug report: [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1060902](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1060902)

---

### Post by Aenima99x on 2012-10-03
I have no problem using LibreOffice on 64-bit.

---

### Post by mlentink on 2012-10-03
And my dmesg
```
[36903.326237] soffice.bin[6636]: segfault at 0 ip 00007f9128c935f0 sp 00007fff370ba298 error 4 in libuno_sal.so.3[7f9128c67000+4f000]
```

Same as Milos_SD in other words, and looks definitely like a bug in libuno

---

### Post by mlentink on 2012-10-03
As promised I just did a sudo apt-get remove --purge libreoffice* and subsequently installed openoffice from ppa (ppa:upubuntu-com/office) 
It works normally. (Hadn't used it in a while, and the lack of integration with Unity isn't very nice...)

Does anyone know how to revert to a previous version of LO, i.e. pre 3.6?

Thx.

---

### Post by mlentink on 2012-10-03
> **Aenima99x said:**
> I have no problem using LibreOffice on 64-bit.

So what version are you using, on what version of Ubuntu?

---

### Post by mc4man on 2012-10-03
Works fine here on 64 bit, recent daily Ubuntu install (though no issue with prev. older installs.

Maybe remove uno-libs3  , then see if there are any libuno* libs left in /usr/lib and or /usr/lib/ure/lib. If so remove then re-install whatever was removed 
(I use synaptic for such as the history shows all plainly

---

### Post by jerrylamos on 2012-10-03
This is a B2 amd64 install, updated daily.  Libre Office Writer comes up O.K. from the launcher  Haven't done anything extensive with it yet.  Acer Aspire 5253 wide screen notebook.  Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6310]

---

### Post by Milos_SD on 2012-10-03
> **mc4man said:**
> Works fine here on 64 bit, recent daily Ubuntu install (though no issue with prev. older installs.

Maybe remove uno-libs3  , then see if there are any libuno* libs left in /usr/lib and or /usr/lib/ure/lib. If so remove then re-install whatever was removed 
(I use synaptic for such as the history shows all plainly

I already tried this too (stumbled upon that "solution" on launchpad), but it didn't help. Still the same segfault with error 4 in libuno.so.3

---

### Post by mc4man on 2012-10-03
> **Milos_SD said:**
> I already tried this too (stumbled upon that "solution" on launchpad), but it didn't help. Still the same segfault with error 4 in libuno.so.3
Have you tried booting to a live session with a recent or current image & seeing what happens..

---

### Post by Aenima99x on 2012-10-03
> **mlentink said:**
> So what version are you using, on what version of Ubuntu?

LibreOffice 1:3.6.1~rc2-1ubuntu5
Ubuntu 12.10

---

### Post by mlentink on 2012-10-04
> **mc4man said:**
> Have you tried booting to a live session with a recent or current image & seeing what happens..

Thx for the hint, will try that tonight

---

### Post by mlentink on 2012-10-04
> **Aenima99x said:**
> LibreOffice 1:3.6.1~rc2-1ubuntu5
Ubuntu 12.10

Hmm. I wonder what is different in your setup vs. Milos_SD's and mine.

---

### Post by Aenima99x on 2012-10-04
> **mlentink said:**
> Hmm. I wonder what is different in your setup vs. Milos_SD's and mine.

Mine's just a standard install and I run updates daily. 
Let me know if you want me to check for certain files installed/not installed to try and compare. The one thing I don't have installed is libreoffice-java-common

---

### Post by pqwoerituytrueiwoq on 2012-10-04
my office works under xubuntu
i filtered to libreoffice and this is my list
[IMG]http://i.imgur.com/YfMLD.png[/IMG]

---

### Post by Milos_SD on 2012-10-06
This was fixed in 3.6.2-rc2 for me. :)

---

### Post by GlennW on 2012-10-06
I don't know if this is the right thread but I need some help in installing LO. I run Ubuntu 11.04 and, up until a week ago, was running LO. Then following an update it crapped out completely. I have attempted to reinstall numerous times via various methods but each to no avail. 

Whether the terminal or synaptic, the error messages are the same: 

[INDENT]Depends: libreoffice-core but it is not going to be installed
Depends: libreoffice-writer but it is not going to be installed[/INDENT]

And it goes on from there with more libreoffice items that won't be installed.

I need something installed. I don't care if it's the latest LO or not, or even if it's OO! I need something. 

BTW, LO runs fine on my laptop which is also running 11.04.

Thanks for having a look at this.

---

### Post by dino99 on 2012-10-06
3.6.2 crash here on i386 logged as gnome-classic when i want to load an .ods calc file(quantal-proposed) and worst: no menu bar again, so back to 3.6.1

---

### Post by Harry33 on 2012-10-07
The version 3.6.2 rc 2 update in QQ is of low quality.
No menus and crashes, regression.

Here is the bug report (1062757):
[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1062757](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1062757)

---

### Post by GlennW on 2012-10-07
Bump!

I don't know if this is the right thread but I need some help in installing LO. I run Ubuntu 11.04 and, up until a week ago, was running LO. Then following an update it crapped out completely. I have attempted to reinstall numerous times via various methods but each to no avail.

Whether the terminal or synaptic, the error messages are the same:

    Depends: libreoffice-core but it is not going to be installed
    Depends: libreoffice-writer but it is not going to be installed

And it goes on from there with more libreoffice items that won't be installed.

I need something installed. I don't care if it's the latest LO or not, or even if it's OO! I need something.

BTW, LO runs fine on my laptop which is also running 11.04.

Thanks for having a look at this.

---

### Post by dino99 on 2012-10-07
i suppose you have some extra ppa(s) installed, and some package(s) might conflict with LO; so start by purging the ppa(s). I have purged and reinstalled LO here on i386 and did not get issue at all.

---

### Post by GlennW on 2012-10-07
> **dino99 said:**
> i suppose you have some extra ppa(s) installed, and some package(s) might conflict with LO; so start by purging the ppa(s). I have purged and reinstalled LO here on i386 and did not get issue at all.

Thanks dino. Might you be able to tell me how to purge such ppa's? I'm not so good with such details.

Thanks.

---

### Post by Harry33 on 2012-10-08
Libreoffice 3.6.2 rc2 is fixed now in QQ repos,
the new version is 3.6.2~rc2-0ubuntu2.

---

### Post by dino99 on 2012-10-08
> **GlennW said:**
> Thanks dino. Might you be able to tell me how to purge such ppa's? I'm not so good with such details.

Thanks.

you might find what you need by googling around "ubuntu ppa purge"

):P

---

### Post by dino99 on 2012-10-08
> **Harry33 said:**
> Libreoffice 3.6.2 rc2 is fixed now in QQ repos,
the new version is 3.6.2~rc2-0ubuntu2.

Cant fully agree:

***
rationale:
LibreOffice with libreoffice-gtk installed would otherwise be unusable in gnome-classic. The only possible workaround would be to disable or remove libreoffice-gtk with a severe impact on desktop integration.
***

as gnome-classic is my default choice, thats bad. All that trouble due to unity (which also will be killed like unity-2d, only GS will survive)

---

### Post by Harry33 on 2012-10-08
> **dino99 said:**
> Cant fully agree:

***
rationale:
LibreOffice with libreoffice-gtk installed would otherwise be unusable in gnome-classic. The only possible workaround would be to disable or remove libreoffice-gtk with a severe impact on desktop integration.
***

as gnome-classic is my default choice, thats bad. All that trouble due to unity (which also will be killed like unity-2d, only GS will survive)

Right then Dino,
what is your issue with this new update.
I have menu's back now and LO does not crash anymore.

---

### Post by dino99 on 2012-10-08
> **Harry33 said:**
> Right then Dino,
what is your issue with this new update.
I have menu's back now and LO does not crash anymore.

i'm still using 3.6.1, as that dev comment seems too scary to me (dont want to dive in trouble by now)

---

### Post by avinas on 2012-10-08
My Libre Office is strating, but after one or two movements it crashing computer badly - black screen, no reaction to anything (to restart sequence with disk syncronisation either)

---

### Post by philinux on 2012-10-08
> **avinas said:**
> My Libre Office is strating, but after one or two movements it crashing computer badly - black screen, no reaction to anything (to restart sequence with disk syncronisation either)

Just double checked here and it's working fine. Mine is a clean install beta 2.

Maybe try removing any OO config files to start with.

---

### Post by mlentink on 2012-10-10
> **Harry33 said:**
> Libreoffice 3.6.2 rc2 is fixed now in QQ repos,
the new version is 3.6.2~rc2-0ubuntu2.

Which repos? In synaptic it's still 3.6.1, Where did you get the 3.6.2?

> **philinux said:**
> Just double checked here and it's working fine. Mine is a clean install beta 2.

I'll try that, since I'm getting the feeling that this isn't something that's going to be resolved by release time, we're getting close.

---

### Post by Harry33 on 2012-10-11
> **mlentink said:**
> Which repos? In synaptic it's still 3.6.1, Where did you get the 3.6.2?


It was first in proposed, but now it is main too.

Here:
[https://launchpad.net/ubuntu/quantal/+source/libreoffice/1:3.6.2~rc2-0ubuntu3](https://launchpad.net/ubuntu/quantal/+source/libreoffice/1:3.6.2~rc2-0ubuntu3)

---

### Post by GlennW on 2012-10-11
> **Harry33 said:**
> It was first in proposed, but now it is main too.

Here:
[https://launchpad.net/ubuntu/quantal/+source/libreoffice/1:3.6.2~rc2-0ubuntu3](https://launchpad.net/ubuntu/quantal/+source/libreoffice/1:3.6.2~rc2-0ubuntu3)

My question is, can I install 1.3.6.2 rc2 on 11.04? If so, how? Don't mean to be obtuse.....

---

### Post by ALinuxWindowsBalance on 2012-10-11
Wait, Ubuntu 12.10?
Where can I find it?

---

### Post by mcellius on 2012-10-11
> **ALinuxWindowsBalance said:**
> Wait, Ubuntu 12.10?
Where can I find it?

You can find the various alpha and beta versions of Ubuntu 12.10 here ([http://www.ubuntu.com/testing](http://www.ubuntu.com/testing)).  The final release version won't be out until October 18th, so what you'll get right now is still being tested.  If you like testing, join in!  If you want stability, though, you might want to wait until next week.

---

### Post by mlentink on 2012-10-12
> **philinux said:**
> Just double checked here and it's working fine. Mine is a clean install beta 2.

> **mlentink said:**
> 
I'll try that, since I'm getting the feeling that this isn't something that's going to be resolved by release time, we're getting close.


Thx philinux, did a fresh install of quantal last night and it's working now!

---

