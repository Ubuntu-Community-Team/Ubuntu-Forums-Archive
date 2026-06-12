---
title: "Trying again"
date: 2007-06-27
forum: Ubuntu Christian Edition
---

### Post by rcdeacon on 2007-06-27
I tried unsuccessfully to install CE 3.0 (Feisty). Had to give up since it wouldn't even load the live cd (very disappointed). I do however have ce 2.2 (Edgy?) and I am considering installing it. It will run live (did that last night) and it has e-sword and some other things that would be really helpful for me as a pastor. I have decided a while back that linux is for me and I currently use another linux os as my primary os. I also run vmware server so that I can use Logos Bible Study which is a great tool. I have been unsuccessful in getting Logos to work with Crossover Office which would be preferable to running xp in vmware. However, with all that said in order for this change to take place I need ce to work on my Dell Dimension 4600 (which it will) and also on my Acer 5002 wlmi laptop with a broadcom 4318 (air force 1) wireless adapter. My question is very simple, is this "doable?" My main concern is the laptop and the wireless. The wireless works well in my current linux os and I noticed that there were some posts that indicated wireless in Edgy may be a problem. Any help would be appreciated.

---

### Post by tak1150 on 2007-06-27
Hi Pastor,

Have you tried the latest version of CE (3.2)?

I'm not sure what you mean when you say "it wouldn't even load the live CD." If this means that the computer boots to the harddrive instead of the CD-ROM, then you can configure the BIOS to preferably boot from CD instead of HDD (on Dells, hit F2 or 12 right when you turn on the computer).

Sometimes, it's the quality of the CD that's the problem. I had to burn a new CD with slower burning speed one time to get a good working CD.

> My main concern is the laptop and the wireless. 
You should be able to test the wireless card before installation with the Live CD. I know that Feisty has more hardware support than Edgy.

God bless your ministry,
Tak

---

### Post by rcdeacon on 2007-06-27
My Dell will not load the cd at all. It will load ce 2.2 but NOT 3.0. No version of Fiesty will load live. I have posted this before on the main forums and it is a problem experienced by a fair number of people. If I remember correctly it has something to do with the tty job control stuff. At any rate Ubuntu 7.04, Kubuntu 7.04 and Ubuntu CE 3.0 are a wash for me.

Also wireless will NOT work easily off the live cd. I need to use ndiswrapper and use the windows driver that came with my Acer. I did not know if others had a different experience. My current os works well on both but there are desirable features on CE. I'm not sure what to do at this point.

---

### Post by tak1150 on 2007-06-27
Is your other OS MEPIS?
If so, you can try to download and install the .deb files of e-Sword and whatever else that you like on U-CE from the [website]("http://www.whatwouldjesusdownload.com/christianubuntu/2007/05/popular-packages.html").
Since MEPIS is based on Debian/Ubuntu, this may work, but I'm not 100% sure.

However, if all you want is e-Sword, which I think is the best Bible study software out there (even better than Quick Verse, which I paid money for), then you can follow this [how-to]("http://ubuntuforums.org/showthread.php?p=2418830#post2418830") to install it without having U-CE.

---

### Post by rcdeacon on 2007-06-27
Yes I do use Mepis. I am currently using Mepis 6.5 but there seems to be some dependencies that need to be addressed to use e-sword in Mepis. (gambus-runtime was one but there are others as well) I am somewhat cautious at this point.

EDIT: OK, I found out all of the dependencies and installed e-sword. It did install but I must run it in a small window on the desktop. If I enlarge the window wine shuts e-sword down. Not sure what that is all about. I nstalled the wine from the Mepis repository (which is actually the Dapper repository I think).

---

### Post by tak1150 on 2007-06-27
in a terminal, type
```
winecfg
```

and a window should come up. Under Graphics (i think), there is an option to turn off virtual desktop (which I think is the small window that you're looking at).

Blessings,
Tak

---

### Post by rcdeacon on 2007-06-27
Thanks Tak, but e-sword will still abruptly stop whenever you try to resize the window or even just when you try to change resources.

---

### Post by tak1150 on 2007-06-28
I was thinking about your problem, and I thought...

you could install Ubuntu 6.10 (not the CE), since you said that edgy CD does boot. Then you can upgrade to 7.04 through Update Manager. Then you can use the "convert_me" script at U-CD website to turn the regular Feisty into CE (3.2)! 

It's rather time consuming, but if you do it in this sequence, you will have less chance of running into problems.

---

### Post by benjoseph on 2007-06-28
I have download E-sword on my PC with Ubuntu 7.04. After the installation on APPLICATION-ACCESSORY- two icon of E-Sword appear: 

Ubuntu CE Users: 

You MUST disable dansguardian before running the e-Sword Installer. You can do this using the built in dansguardian GUI(System>Administration>Configure Parental Controls). 

Once the e-Sword Installer has successfully completed you can re-enable dansguardian. 

Click OK to continue with the e-Sword Installer.

I have tried to find the "DANSGUARDIAN" following the lead SYSTEM-Administration- Configure parent control, but with no avail. I am so frustrated because I have used E-Sword almost seven years now. I out there any one who can help me with simple explanation (I am 63 years old and I have not a great knowledge of PC let alone Ubuntu. 

Thank you very much.

---

### Post by tak1150 on 2007-06-28
Hi,

1. To get to DansGuardian, look for the icon in the "Administration" menu (see 1st screenshot)

2. There are two ways to enable e-Sword installer.
1) Disable DansGuardian
See the 2nd screenshot; click "disable"

2)Allow downloading of ".exe" files
See 3rd screenshot; click on the "Advanced" tab on the top, then click on "file extensions"
Then add "#" mark before ".exe" (4th screenshot). Then click on "save" to save the change.

3. After doing either 1) or 2), click on "Save & Exit" button.

4. Sometimes, you have to wait a few minutes for the effect to kick in (at least true in my laptop).

5. Now you're ready to click on "e-Sword installer"!

*If you did the 2) method, you won't have to bother with DansGuardian in the future when you want to install e-Sword modules

---

### Post by benjoseph on 2007-06-28
Thanks very much for your effort. By the screen-shot you send me, I have realized that I do not get your same menù when I go to System-ADMINISTRATION. The DansGuardian menù dose not appear   on my SYSTEM -ADMINISTRATION list. My version of Ubuntu is not a Christian one, is that probably the reason I cannot see the same menù as yours. I am disheartening to say the list. What I price to pay to have choose Linux. This of course those not mean I am going back to Windows, over my dead body. 

Please folks help me get E-Sword on my PC. That is my favorite program. I feel lost without it. 

Thank you any way for your help. What a fantastic bunch of people you are!

God bless you

---

### Post by tak1150 on 2007-06-28
> My version of Ubuntu is not a Christian one, is that probably the reason I cannot see the same menù as yours. 

Yes. If it's not the Christian Edition, you don't have to worry about DansGuardian b/c you don't have it.

---

### Post by rcdeacon on 2007-06-28
Tak, thanks for the reply. I am giving serious consideration to installing Ubuntu. I hesitate for two reasons. First, Mepis really does run good right out of the box including multimedia stuff. Second, I have used KDE so long I don't know how I can adjust to Gnome. There are a number of things in Ubuntu especially the CE strain that I really like and I think it will work good for me. In fact so good, I may not even have to install vmware server (I do this mainly for Logos). Let me think on it some more and if you can provide any additional insights as to the benefits of such a large change please feel free to post or pm me. thanks again, God bless.

EDIT: BTW i have edgy but it is the ce version of edgy. Can I install that and still upgrade to 7.04?

---

### Post by ArgusVision on 2007-06-29
Have you tried running an "Alternate" CD? I know the last time I looked there wasn't one for CE,but you could get a standard Ubuntu Alternate and then use Synaptic to upgrade to most of the app's and features of CE.
So far i've been able to locate most everything except the parental controls. (you'd think they'd include that w/ _**Edubuntu **_that I got for my kids) 

Also, are you using the same .iso burner that you used with edgy? And, did you get a good clean download? 
The CE version I downloaded encountered GRUB errors when i tried to install. though the live CD was fine...

I know I get a little wordy but I hope it works for you.

---

### Post by rcdeacon on 2007-06-29
I did use the same burner (since then I have acquired another additional burner) but I burned a number of disks including ubuntu, kubuntu and ce. All of the disks worked fine except th 7.04 disks. I managed to find Edgy and I am downloading it now. Perhaps I will install it and try to upgrade to Feisty.

---

### Post by tak1150 on 2007-06-29
Hi rcdeacon,

You can upgrade from Edgy CE to Feisty CE, but it would be a "cleaner" installation if you go from Edgy to Feisty to CE, b/c you won't be overwriting any CE stuff. Maybe I'm being too cautious, but I think it's good to be cautious when you install an OS.

---

### Post by david_kt on 2007-07-08
> **benjoseph said:**
>  My version of Ubuntu is not a Christian one, is that probably the reason I cannot see the same menù as yours. I am disheartening to say the list. What I price to pay to have choose Linux. This of course those not mean I am going back to Windows, over my dead body. 

Please folks help me get E-Sword on my PC. That is my favorite program. I feel lost without it. 

Thank you any way for your help. What a fantastic bunch of people you are!

God bless you

If you use normal Ubuntu, you could follow below "how to":

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

Theoretically, this "how to" should work on any linux version running wine, and off-course any ubuntu version.

DK

---

### Post by mhancoc7 on 2007-07-08
> **benjoseph said:**
> 

Please folks help me get E-Sword on my PC. That is my favorite program. I feel lost without it. 

Thank you any way for your help. What a fantastic bunch of people you are!

God bless you

You can use the s-Sword installer found here.
[http://www.whatwouldjesusdownload.com/christianubuntu/2007/05/popular-packages.html](http://www.whatwouldjesusdownload.com/christianubuntu/2007/05/popular-packages.html)

Jereme

---

