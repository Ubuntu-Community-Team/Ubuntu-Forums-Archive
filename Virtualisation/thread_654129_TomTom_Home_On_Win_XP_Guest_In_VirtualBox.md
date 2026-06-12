---
title: "TomTom Home On Win XP Guest In VirtualBox"
date: 2007-12-30
forum: Virtualisation
---

### Post by linux4me on 2007-12-30
After a bit of trial and error, I got TomTom Home to run on a Windoze XP guest using VirtualBox on my Gutsy machine.

VirtualBox runs fine, Windoze starts up fine, USB is working fine, and TomTom Home loads up just fine.

TomTom Home recognizes my Go 720 and I can download and install updates, but when I try to use the "manage my device" option I get an error message that says "navigator failed to initialize".

I have searched here, the TomTom knowledgebase, and Googled but couldn't find a solution.

Has anyone managed to get that feature to work?

---

### Post by linux4me on 2007-12-31
I'm a little closer than when I first posted.

I found that in Windoze if I disable Autoplay for the TomTom I can actually operate the TomTom from the PC; however, it still hangs occasionally. I recommend disabling Autoplay to anyone else who is trying to get Home to work.

Still looking for a fix. I submitted a support ticket to TomTom, but I'm not hopeful they will help since I'm using a virtual environment.

---

### Post by linux4me on 2008-01-07
I got an answer back from TomTom support for anyone else struggling with this issue:
> The My Device icon will link you with our online emulator. This will allow you to plan trips through TomTom HOME and save them to your Go 720. This feature is currently under development. As such, it is not yet accessible. Please rest assured that TomTom is doing everything possible to complete this quickly and efficiently. We appreciate your patience while we continue to improve your customer experience. On your system you are getting the freezing because it is searching for the file need.

If you are trying to plan a trip please plan it directly from the unit .

---

### Post by casper911ca on 2008-12-09
I have installed Windoze XP on my VirtualBox (proprietary version, not OSE) and it recognizes the device but TomTom HOME does not install. I've tried the obvious routes on installing it and made sure the box was up to date (SP3, etc.) and still does not install. When run the program it has the usual install shield dialogue and asks me "install" or "Don't Install" and after hitting install nothing happens. I've tried running the .exe on the Device, i've tried downloading the software (twice) from the TomTom server and running that, but its the always the same deal. I *kinda* got it working in Wine by downloading the correct .dll's and the .manifest's (msvcr80, Microsoft.VC80.CRT.manifest)  but it will not connect to the device. I have java installed on the VM, thought that might be an issue since i heard the HOME software is 85%+ Firefox code.

I know it works since I did get it working on my roomates Windoze XP machine. Is there something missing on my VM that im overlooking?

---

### Post by linux4me on 2008-12-09
> **casper911ca said:**
> I have installed Windoze XP on my VirtualBox (proprietary version, not OSE) and it recognizes the device but TomTom HOME does not install. I've tried the obvious routes on installing it and made sure the box was up to date (SP3, etc.) and still does not install. When run the program it has the usual install shield dialogue and asks me "install" or "Don't Install" and after hitting install nothing happens. I've tried running the .exe on the Device, i've tried downloading the software (twice) from the TomTom server and running that, but its the always the same deal. I *kinda* got it working in Wine by downloading the correct .dll's and the .manifest's (msvcr80, Microsoft.VC80.CRT.manifest)  but it will not connect to the device. I have java installed on the VM, thought that might be an issue since i heard the HOME software is 85%+ Firefox code.

I know it works since I did get it working on my roomates Windoze XP machine. Is there something missing on my VM that im overlooking?

Are you using Virtual Box from the repositories, or the version directly from Sun? I just tried installing both the version of Tom Tom Home my Go 720 came with, version 1.6.020, and then uninstalled that and installed the latest version, version 2.5, and they both installed fine on my installation of Winblows on the Sun version of Virtual Box. 

If you're using VB from the repositories, I would remove it and try using the version directly from Sun. Your Windows installation should be retained as all of it is in the hidden folder ".VirtualBox" in your home directory so you hopefully won't have to go through the painful process of another Micro$oft installation.

---

### Post by s.illes79 on 2009-07-07
> **casper911ca said:**
> I have installed Windoze XP on my VirtualBox (proprietary version, not OSE) and it recognizes the device but TomTom HOME does not install. I've tried the obvious routes on installing it and made sure the box was up to date (SP3, etc.) and still does not install. When run the program it has the usual install shield dialogue and asks me "install" or "Don't Install" and after hitting install nothing happens. I've tried running the .exe on the Device, i've tried downloading the software (twice) from the TomTom server and running that, but its the always the same deal. I *kinda* got it working in Wine by downloading the correct .dll's and the .manifest's (msvcr80, Microsoft.VC80.CRT.manifest)  but it will not connect to the device. I have java installed on the VM, thought that might be an issue since i heard the HOME software is 85%+ Firefox code.

I know it works since I did get it working on my roomates Windoze XP machine. Is there something missing on my VM that im overlooking?

Hi casper911ca,

Did you manage to install it? I'm having the same problem, I click on the downloaded tomtomhome install exe but nothing happens.

Thanks

---

### Post by Remuzzz on 2009-07-17
I think I have a solution, installing this worked for me:

[http://www.microsoft.com/downloads/details.aspx?FamilyId=32BC1BEE-A3F9-4C13-9C99-220B62A191EE&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyId=32BC1BEE-A3F9-4C13-9C99-220B62A191EE&displaylang=en)

---

### Post by neylitalo on 2009-08-27
> **Remuzzz said:**
> I think I have a solution, installing this worked for me:

[http://www.microsoft.com/downloads/details.aspx?FamilyId=32BC1BEE-A3F9-4C13-9C99-220B62A191EE&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyId=32BC1BEE-A3F9-4C13-9C99-220B62A191EE&displaylang=en)

Worked for me.

---

### Post by Nicram on 2009-09-25
> **Remuzzz said:**
> I think I have a solution, installing this worked for me:

[http://www.microsoft.com/downloads/details.aspx?FamilyId=32BC1BEE-A3F9-4C13-9C99-220B62A191EE&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyId=32BC1BEE-A3F9-4C13-9C99-220B62A191EE&displaylang=en)

It worked for me too! At last! I was wondering what the problem is?
As usual This community is the best one.
Thanks

---

### Post by Alibloke on 2010-01-10
Kickass!  Nice work guys, just what I was looking for - thanks.

---

### Post by krivine on 2010-03-14
Worked for me. Much obliged!

---

### Post by peterm34 on 2010-12-16
Installing the Microsoft download worked for me, too, once I realised that I needed to install Windows XP SP2. As ever, a MS problem, not a Linux one, and MS's error message was far from helpful - mentioned missing dlls, without specifying what they were. Why can't the MS installer just grab them from its website???

Enough of my rant. Many thanks to Remuzzz for the suggestion.

---

### Post by fabricator4 on 2011-05-21
> **Remuzzz said:**
> I think I have a solution, installing this worked for me:

[http://www.microsoft.com/downloads/details.aspx?FamilyId=32BC1BEE-A3F9-4C13-9C99-220B62A191EE&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyId=32BC1BEE-A3F9-4C13-9C99-220B62A191EE&displaylang=en)

This fix still works, thankyou.

I had no clue what the problem was, since the TomTom Home install was bombing with no error messages.

Chris

---

### Post by dilaudid on 2011-05-25
> **Remuzzz said:**
> I think I have a solution, installing this worked for me:

[http://www.microsoft.com/downloads/details.aspx?FamilyId=32BC1BEE-A3F9-4C13-9C99-220B62A191EE&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyId=32BC1BEE-A3F9-4C13-9C99-220B62A191EE&displaylang=en)
Thanks - that fixed it for me. I guess most windows users without virgin installs already have the VC redist installed.

---

