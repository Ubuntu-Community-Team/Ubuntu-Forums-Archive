---
title: "Need help installing Office 2007 via Wine"
date: 2009-03-24
forum: Wine
---

### Post by Duranxl on 2009-03-24
Hi all. I noticed there are many guides concerning how-to install office 2007.
like:
[http://ubuntumanual.org/posts/165/install-microsoft-office-2007-in-ubuntu-8-10](http://ubuntumanual.org/posts/165/install-microsoft-office-2007-in-ubuntu-8-10)
or
[http://www.programmerfish.com/roffice-2007-in-linux](http://www.programmerfish.com/roffice-2007-in-linux)
or
[http://samanathon.com/how-to-install-microsoft-office-2007-in-ubuntu-804/](http://samanathon.com/how-to-install-microsoft-office-2007-in-ubuntu-804/)

Most guides come to this step:
```
./winetricks gdiplus riched20 riched30 msxml3 msxml4 msxml6 corefonts tahoma vb6run vcrun6 msi2
```

However i always get this error:
```
:~/.wine/drive_c$ sh winetricks msxml3 dotnet20 gdiplus riched20 riched30 vcrun2005sp1  
Using native,builtin override for following DLLs: msxml3
Executing wine regedit ~/.wine/drive_c/winetrickstmp/override-dll.reg
Executing wine msiexec /i ~/.winetrickscache/msxml3.msi
Note: command 'wine msiexec /i ~/.winetrickscache/msxml3.msi' returned status 103.  Aborting.
:~/.wine/drive_c$
```

Then when i run the installer the installer prompts "there has been an error" or something..and i can quit the installer.
Any help?
I'm using wine 1.1.17

---

### Post by hikaricore on 2009-03-24
There was just a thread on this: [http://ubuntuforums.org/showthread.php?t=1102840](http://ubuntuforums.org/showthread.php?t=1102840)
Have you tried following this guide?  I have no further info to offer just linking.

---

### Post by carml on 2009-03-24
Why do you need to install Micro Office 2007?

---

### Post by Duranxl on 2009-03-24
> **hikaricore said:**
> There was just a thread on this: [http://ubuntuforums.org/showthread.php?t=1102840](http://ubuntuforums.org/showthread.php?t=1102840)
Have you tried following this guide?  I have no further info to offer just linking.
Thanks, but it still does not work.
I've downgraded to .16 but now the installer just disappears with the error:
```
fixme:ntdll:NtCreatePort (0x13a1c0,0x33f9b0,188,256,(nil)),stub!

```
> **carml said:**
> Why do you need to install Micro Office 2007?

Because i cannot use openoffice for any documents because all the documents i make will end up differently for everyone else in Office. 
Don't get me wrong, i like OO, but unless everyone starts using it, i can't use it..

---

### Post by NightMKoder on 2009-03-24
> **carml said:**
> Why do you need to install Micro Office 2007?

<rant>
I believe what you mean by this is "Why don't you use OpenOffice?" I agree, OpenOffice is a very good free alternative office suite, and I do suggest using it instead of Microsoft's. There are a number of great comparisons, and the official openoffice website has a very neat one: [http://www.openoffice.org/product/docs/ms2007vsooo2.pdf](http://www.openoffice.org/product/docs/ms2007vsooo2.pdf) (sorry, pdf). If that is good enough for you Duranxl, then we can end the thread here.

That said, please don't discuss alternatives. The topic of this thread is HOW to get Office 2007 working in *ubuntu, not WHY. There are valid arguments both ways, but they are not the point of this thread.
</rant>

Getting back to the topic:
Please use the how-to I wrote. And if any of those winetricks at some point succeeded, I strongly suggest starting with a fresh wine directory. You should NOT need to do ANY winetricks to install office. I wrote the guide specifically so people would not follow these tutorials (which are just outdated). The other problem with using such an extensive list of winetricks is that there is no way to debug them. So when your wine finally breaks or you can't install something, there is a good chance that noone will have any idea what is going on.

My 3c.

EDIT: Beaten to the followup.
> **Duranxl said:**
> Thanks, but it still does not work.
I've downgraded to .16 but now the installer just disappears with the error:
```
fixme:ntdll:NtCreatePort (0x13a1c0,0x33f9b0,188,256,(nil)),stub!

```


Because i cannot use openoffice for any documents because all the documents i make will end up differently for everyone else in Office. 
Don't get me wrong, i like OO, but unless everyone starts using it, i can't use it..

Try with a fresh wine prefix (#1 note from the thread)

---

### Post by carml on 2009-03-24
I was just wondering why he needed Office,and I heard about some differences in the encoding between Openoffice and Office.That was only curiosity, no more. :)

---

### Post by Duranxl on 2009-03-24
awesome, having a new folder just for office fixed it!
It's weird that the guides are so outdated, since they're for 8.10.. ah well guess wine really improved since the guides were written

thanks guys

edit: fonts like calibri are totally ugly though...?

---

