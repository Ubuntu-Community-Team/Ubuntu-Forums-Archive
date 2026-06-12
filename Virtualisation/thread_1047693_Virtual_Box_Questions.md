---
title: "Virtual Box Questions"
date: 2009-01-22
forum: Virtualisation
---

### Post by Universal344 on 2009-01-22
I am looking into possibly running OpenSUSE 11.1 on Ubuntu using Virtual Box.  However, I do have some questions:

1. I checked Add/Remove for Virtual Box and found Virtual Box OSE (Open Source Edition).  Can I go ahead and download the OSE through Add/Remove or should I get it another way?

2. Will 5gb be enough for OpenSUSE (I only have 14.5gb or so free on ubuntu)

3. I assume it will store it in a virtual hard disk file somewhere on my system, is there a certain place I should put it?

4. Are there any major bugs that I could encounter or anything else that is important to know?

---

### Post by slick666 on 2009-01-22
[LIST=1]
[*]The OSE edition is almost fully functional. Virtual box offers another Paid version to companies and has a license agreement so home users can get it free (as in beer). I recommend just using the one in Synaptic for now. if you find you need the functionality of the full fledged version you can always install it later.
[*] check the OpenSuse requirements. I'm guessing 5gigs might be close for a regular install but you might be able to do simpler install that takes up less space.
[*]My way of doing it is to create a Virtualbox directory in my home directory but unless you have some special multi HD or partition scheme it doesn't really matter.
[*]The current version in the repo is an older 1.X series. I know virtual box has a newer version out. check out Virtualbox's [Changelog]("http://http://www.virtualbox.org/wiki/Changelog") to see what bugs you might have/
[/LIST]

---

### Post by tmetzcc325 on 2009-01-22
I've found that downloading the .deb from the virtualbox site works well.  It is not the OSE, but still free, and comes with built in support for USB (which I believe the OSE version lacks).  In addition, you can get version 2.1 instead of the 1.x that is in the ubuntu repos (if that sort of thing is important to you).

I'd say that if disk space isn't a concern, go with a 10GB vhdd, just to be on the safe side.  But like slick said, this all depends on which version and the software that you want to install.  When you first try to create a virtual machine, the software will guide you through creating the vhdd, which is stored in the .VirtualBox directory in your home, but this may be configurable.

---

### Post by dmizer on 2009-01-23
Moved to the virtualization sub forums for more targeted help.

Thank you :)

---

### Post by Dedoimedo on 2009-01-23
Hello,

You can solve the space issue if you have an external hard storage device. But 5gb should be enough. BTW, you can place the files anywhere you want.

Maybe this will interest you:
[http://www.dedoimedo.com/computers/virtualization-tips.html](http://www.dedoimedo.com/computers/virtualization-tips.html)

VB OSE is good enough, no USB support, though.

Dedoimedo

---

### Post by Orographic on 2009-01-23
From Add/Remove: 

"VirtualBox is a free x86 virtualization solution allowing a wide range of x86 operating systems such as Windows, DOS, BSD or Linux to run on a Linux system. This package provides the binaries for the Open Source Edition of VirtualBox. The virtualbox-ose-source package is also required in order to compile the kernel modules needed for virtualbox-ose."

Do we only need to tick the VirtualBox OSE box in Add/Remove if we want this version installed in Ubuntu (8.10)? I'm not sure what that last sentence above means. Do I need the  'virtualbox-ose-source package' as well, as mentioned above?

I originally tried both the Add/Remove version and 2.1 in Intrepid to run XP and they worked really well, except both caused kernel panic at times on shutdown which I could never resolve...

I used the Ubuntu Geek help files to install 2.1.0 but the link is down at present.

---

### Post by Orographic on 2009-01-24
Anyone got an answer to my question?

---

### Post by dmizer on 2009-01-24
> **Orographic said:**
> Do I need the  'virtualbox-ose-source package' as well, as mentioned above?

Obviously you need both. Have you tried it? It may automatically check the other. If it does, it will tell you. If it doesn't you will need to look for it in Synaptic.

Edit, looks like it's automatic, see attached image.


According to what I've read, you're probably better off using the version from the Virtualbox site rather than the version in the repositories anyway.

---

### Post by Orographic on 2009-01-25
I wouldn't say its obvious. That's why I was asking as I am new to Ubuntu and was unsure. It was a genuine question.

I have used 2.1.0 and if you had read my post carefully, also the add/remove version (OSE). I was getting occasional kernel panic on shutdown in both versions of VB, so being quite new to Ubuntu, thought it might have been a problem with how I was installing it.

---

### Post by dmizer on 2009-01-25
> **Orographic said:**
> I wouldn't say its obvious. That's why I was asking as I am new to Ubuntu and was unsure. It was a genuine question.

My apologies, I didn't intend to come off as condescending. I just meant that if the summary in Synaptic says you need both, then you need both. There's no reason to distrust what Synaptic says.

I read other posts which indicated kernel panic. Apparently this is unique to the OSE virtualbox that ships with the Hardy repositories. If you use the free, official vitualbox (non-OSE version), then there is no kernel panic. I don't know if this applies to Ibex or not.

I have not used virtualbox, so I really can't testify to this. It's only what I read here in the forums.

---

### Post by Orographic on 2009-01-25
No worries. I think I can understand your post now. I had kernel panic in both the OSE and non OSE version (2.1.0) but will look into it again. I did an Acronis re-image of Intrepid in between installing the OSE and non OSE versions so theoretically I shouldn't have experienced kernel panic again in the non OSE version.

I might try just downloading the .deb file from the VB site and installing it that way on Intrepid. I think I have to add a line to my sources list if I do it this way. I have just imaged Intrepid again, so if I have any problems, I can revert to that image.

I guess there is a chance the kernel panic wasn't related to VB and was fixed with Intrepid updates. Without VB installed, my system has been running perfectly for weeks.

---

