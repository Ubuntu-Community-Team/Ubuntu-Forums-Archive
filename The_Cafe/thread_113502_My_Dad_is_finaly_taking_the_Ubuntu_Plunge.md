---
title: "My Dad is finaly taking the Ubuntu Plunge"
date: 2006-01-06
forum: The Cafe
---

### Post by Omnios on 2006-01-06
Yesterday my dad bought a 120 gig drive and is planning on partioning it to install NT and Ubuntu onto it. His main drive is XP.  SO the main drive will be XP then he wants to probably make the new drive 3 40 gig partions with NT on the first one. probably Ubuntu on the second and the last drive as far32 for file sharing between win and Ubuntu. 

 Are there any serios flaws in this apreach, My main concern would be his grub

---

### Post by lleb on 2006-01-06
just asking, but why NT?

anyways, install NT first, then XP, then ubuntu.  not even sure you can dual boot NT with XP.  NT does not play nice with others even other MS OSs.

---

### Post by Omnios on 2006-01-06
[QUOTE=lleb]just asking, but why NT?

anyways, install NT first, then XP, then ubuntu.  not even sure you can dual boot NT with XP.  NT does not play nice with others even other MS OSs.[/QUOTE]

 He has an older version of outocad which he cant seem to get working in XP but worked in NT

---

### Post by Omnios on 2006-01-06
[QUOTE=lleb]just asking, but why NT?

anyways, install NT first, then XP, then ubuntu.  not even sure you can dual boot NT with XP.  NT does not play nice with others even other MS OSs.[/QUOTE]

 He has an older version of outocad and autocad cd tutorials which he cant seem to get working in XP but worked in NT. The thing is the tutorials dont want to work in XP

---

### Post by dragonfyre13 on 2006-01-06
Yes. I currently have 2 40GB hard drives, and the problem is, grub gets borked. Solution to this is to load NT first, partitioning everything normally, before loading Ubuntu.

Install Ubuntu to the designated partition, but as you are going though the installation, when you get to the partition manager, make sure that you specify hdb's Ubuntu partition as "/", and then make a tiny (10-20MB or so) partition for grub on the 1st hard drive (hda).

Make sure to set (In the partition manager) the grub partition on hda as "/boot". Basically, windows boot manager doesn't play nice when it sees the MBR referring to another drive for the boot manager, so XP takes over, and borks GRUB.

I've had no problems since setting it up like this. ^_^

---

### Post by dragonfyre13 on 2006-01-06
Try using wine? Don't think it will work, but if it does, then you can give him a major reason to switch. Also, seeing as how it's an older version, it may not have as many compatability issues.

---

### Post by Bandit on 2006-01-06
[QUOTE=Omnios]He has an older version of outocad which he cant seem to get working in XP but worked in NT[/QUOTE]
Go into WinNT/System32 and look for setver.exe.
Delete it and edit your config.sys file were it shows File=??
Set it to "Files=99" and see if that doesnt fix it.

BTW, glad to here he is at least trying something better out.

Cheers,
Bandit

---

### Post by dragonfyre13 on 2006-01-06
Also, there is a way to do the dual boot of both XP and NT if XP is installed first, by hiding the other partition from XP, when XP boots, and When NT boots, you hide the XP partition. You can do this with grub. Just make sure not to boot into either windows OS before finishing the Grub modifications.

---

### Post by dragonfyre13 on 2006-01-06
Umm, did you mean "C:\Windows\System32" ?

XP uses Windows, not WinNT.

You may have to boot into safe mode for that, if you can at all. Otherwise, CLI it.

---

### Post by Bandit on 2006-01-06
[QUOTE=dragonfyre13]Umm, did you mean "C:\Windows\System32" ?

XP uses Windows, not WinNT.

You may have to boot into safe mode for that, if you can at all. Otherwise, CLI it.[/QUOTE]
Yea Windows.. They switch up some much I couldnt remember.
Just delete the Setver.exe file and up your File=?? to 99 in your config.sys.
I have had to do with some many computers at work cuz the software was designed for WinNT4 or DOS.
It doesnt hurt windows at all.
Cheers,
Joey

---

### Post by dragonfyre13 on 2006-01-06
It disables some of the planned higher level functions, but nothing the put into implimentation actually needs the settings like they are.

---

### Post by Bandit on 2006-01-06
[QUOTE=dragonfyre13]It disables some of the planned higher level functions, but nothing the put into implimentation actually needs the settings like they are.[/QUOTE]
Well its just advice..
I personaly have not noticed and stability problems doing this.
But its just advice, take it as you will...
Cheers...

---

### Post by dragonfyre13 on 2006-01-06
That's what I was saying. I haven't found anything that it breaks either (though, I used to do more windows tinkering than I do now) I think what you removed was mainly for things that were planned on being implimented, but microsoft never got around to it.

---

### Post by newbie2 on 2006-01-06
[QUOTE=Omnios]He has an older version of outocad and autocad cd tutorials which he cant seem to get working in XP but worked in NT. The thing is the tutorials dont want to work in XP[/QUOTE]

> Older versions of Windows – Windows 98, 98 Second Edition and Millennium Edition – are going unpatched. While these versions of Windows do contain the affected component, Microsoft said the vulnerability is not critical because an "exploitable attack vector" has not been identified that would justify a critical severity rating. Microsoft will only release updates for "critical" security issues on these dating operating systems.

[COLOR="Red"]Users still running Windows NT and pre SP 4 versions of Windows 2000 also get nothing because these have reached the end of Microsoft's mandated support lifecycles.[/COLOR]
[http://www.channelregister.co.uk/2006/01/06/microsoft_wmf_vulnerability_patch/](http://www.channelregister.co.uk/2006/01/06/microsoft_wmf_vulnerability_patch/)
:rolleyes:

---

### Post by poofyhairguy on 2006-01-06
I would:

Install NT for a week alone and let him go through the tutorials. 

Then after he is done I would erase that junk and put the XP and Ubuntu on. After the week he will be dying for a modern OS.

Its not worth fighting such an old OS for some tutotials. 

Actually if it was me I would buy him a book on that software and throw the NT CD away when he was not looking. "Sorry dad, but I won't let you use such primative technology."

LOL

Once again, I am partially joking.

---

