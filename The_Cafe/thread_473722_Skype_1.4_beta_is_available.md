---
title: "Skype 1.4 beta is available"
date: 2007-06-14
forum: The Cafe
---

### Post by frodon on 2007-06-14
[http://www.skype.com/intl/en/download/skype/linux/](http://www.skype.com/intl/en/download/skype/linux/)

Just to let you know that skype 1.4 beta is out, hope it will solve many of the issues that some of you (including me) had with the 1.3 version.
In my case i always had freeze problems with skype 1.3 when receiving or starting a call the result was a 30s freeze almost each time so i used the 1.2 version till now.

I hope this version will be rock solid, reading what the skype devs said it seems that the next version (after the 1.4) will contain the video support :)

More details here :
[http://share.skype.com/sites/linux/2007/06/skype_for_linux_14_beta.html](http://share.skype.com/sites/linux/2007/06/skype_for_linux_14_beta.html)
[http://share.skype.com/sites/garage/2007/06/skype_14_beta_for_linux.html](http://share.skype.com/sites/garage/2007/06/skype_14_beta_for_linux.html)

---

### Post by matthew on 2007-06-14
Good news! Thank you. I'm hopeful that we won't have to wait too long for the next version with the video capability...my extended family will not leave Windows so I can't use Ekiga with them and we would like to see one another as well as talk.

---

### Post by Bagboy23 on 2007-06-14
I use to have that same issue with freezing and the CPU bar would top out at 100%. Turining of the sound alerts stopped that prob.

Anyway Frodon, would be nice to get a review from you on the 1.4 beta.

---

### Post by frodon on 2007-06-14
Here is the answer from the skype staff about the freeze problem that many ubuntu users had with the 1.3 version, read post 27 :
[http://forum.skype.com/index.php?showtopic=42232&st=26#](http://forum.skype.com/index.php?showtopic=42232&st=26#)

Bagboy23, don't worry i will keep you up to date i will let skype run all night and see if tomorow i have still the freeze issue when starting a call.

---

### Post by moevmie on 2007-06-14
Does anybody know how i get this working on my AMD 64bit???? because from the .deb i get: 'wrong architecture'. 
Thanks

---

### Post by matthewartz on 2007-06-15
Would also love to hear a recommendation on easiest install on AMD64

---

### Post by odiseo77 on 2007-06-15
Great!! This beta version looks pretty cool (have just installed it so I have not tested it very in deep). Thanks for the good new, frodon :)

@ moevmie & matthewartz: have you tried with the ***--force-architecture*** option? (I'm not on 64 bits right now, so I don't remember exactly how it's done)

---

### Post by frodon on 2007-06-15
Ok after running this new beta version all nigh i tried to start a call this morning and still no freeze :), this version fully solve the freeze problem i had with the 1.3, i'm sticking with the 1.4 now.

---

### Post by moevmie on 2007-06-15
> **odiseo77 said:**
> 
@ moevmie & matthewartz: have you tried with the ***--force-architecture*** option? (I'm not on 64 bits right now, so I don't remember exactly how it's done)

i got it to work!!!! thanks to you and somebody on the skype forum.... [http://forum.skype.com/index.php?showtopic=88904&st=0&gopid=406929&#entry406929](http://forum.skype.com/index.php?showtopic=88904&st=0&gopid=406929&#entry406929)

m

---

### Post by Obor on 2007-06-15
I've been using 1.4 Alpha since it came out and it solved all my problems. Downloading the beta now. 
I don't like the fact that it opens new window for calls but other then that I think it brings skype for linux in line with other versions (obviously without the video but I don't miss that too much).

Good enough for me :D

---

### Post by Simpele on 2007-06-15
> **moevmie said:**
> Does anybody know how i get this working on my AMD 64bit???? because from the .deb i get: 'wrong architecture'. 
Thanks

Check [http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)
This explains how to install 1.4 alpha, but it's the same procedure for 1.4 beta, just different filenames regarding the Skype files.

---

### Post by eagleeyed on 2007-06-15
This has actually added problems with me.

I have recently downloaded the new Beta version.  In 1.3 I was not able to get my soundcard working with it (Behringer U-Control UCA-202), however the sound card works in Audacity.

I have just started the new version for the first time, I called echo123 to test my sound setting when the devices were set up, basically it recorded my message but when it came to playing it back it did the answering machine beep twice, left no time for the audio to be played back and gave me the 'if you could hear yourself...' speel.

I then tried to ring my personal mobile using Skype Out credit I have, when I answered on the mobile however Skype instantly crashed and closed, same thing happens after restarting the program and computer.

Chat still works fine which was all I was able to use on the previous version.

---

### Post by Rumpanzle on 2007-06-15
Is it just me, or is the whole tab thing gone? How do I hide offline users?

---

### Post by eagleeyed on 2007-06-15
Yes, tabs and groups are all gone.

This is what really annoyed me aswell.

I could not possibly think of a good reason to remove them.

---

### Post by henriquemaia on 2007-06-15
This new version solved almost all the problems I had. But, strangely, I can’t type the ç (cedilla) on the chat box. This is better then the previous version, where I couldn’t type all accents - but I had cedilla then.

Any ideas on how to solve this?

---

### Post by pickarooney on 2007-06-16
Using the alpha, and the freezing problem seems to be solved. Tried installing the beta via synaptic and apt-get but got problems with dependencies (libqt4-core, libqt4-gui, libasound2). I'm using Edgy Eft. Will the .deb for feisty on skype's page work?

---

### Post by odiseo77 on 2007-06-16
> **pickarooney said:**
> Using the alpha, and the freezing problem seems to be solved. Tried installing the beta via synaptic and apt-get but got problems with dependencies (libqt4-core, libqt4-gui, libasound2). I'm using Edgy Eft. Will the .deb for feisty on skype's page work?

I'm afraid it won't work; I tried to install it on Ubuntu Edgy 64 bits with the --force-architecture option and it complained that it needed higher versions of the necessary libraries that are available on Edgy's repositories, so you probably need to download the dynamic package from skype's site and run it from the terminal.

---

### Post by pickarooney on 2007-06-16
Cheers. Running the dynamic package and it seems pretty much the same as the alpha version, which is fine, as the freezing seems to be a thing of the past.

---

### Post by PartisanEntity on 2007-06-16
I upgraded yesterday, looks nice but I am very annoyed that I can't edit the contact list and not show offline users, anyone know if this is temporary? I have yet to see if it solves the issue I had with message not being delivered after Skype had been running for a while (only work around was to restart Skype)

---

### Post by Golyadkin on 2007-06-16
It is about time it is going to allow us to send SMS.... I don't know why that is taking so long.

---

### Post by Pekkalainen on 2007-06-16
Got the new version via Ubuntus update system and it turns out it has terrible sound quality, so terrible it has rendered skype useless for me. How do I revert back to the old version?

---

### Post by langi280179 on 2007-06-16
Skype 1.4 is a step forward concerning UI. 
Sound quality with echo123 was very bad, but this was due to bandwith problems. Sound quality is good now.

---

### Post by kszys on 2007-06-19
I have (very unwisely) done dist-upgrade to force install of skype 1.4 on Dapper :( This resulted in removing skype 1.3 and NOT installing skype 1.4... I cannot get 1.4 to run on Dapper at all... Even the static version just exists - no message, nothing... Any ideas how to go back to 1.3?

---

### Post by mtron on 2007-06-19
no way to get this working on dapper. 

Grab the old skype 1.3 deb at [http://download.skype.com/linux/skype_debian-1.3.0.53-1_i386.deb](http://download.skype.com/linux/skype_debian-1.3.0.53-1_i386.deb)

---

### Post by Johnsie on 2007-06-19
I'm sad to be saying this a year and a half later but Skype for Linux still isnt anywhere near as good as Skype for Windows. And Linux still lacks an acceptable solution for multimedia communication over the major IM networks. Unfortunately thats one of the main things people use their desktop computers for. I'm still waiting ona way to do cam with my yahoo friends. This is one of the main things holding me back from using Linux as my defaut operating system. I want to be able to do cam with my friends without them ahving to change their software.

---

### Post by frodon on 2007-06-19
> **Johnsie said:**
> I'm sad to be saying this a year and a half later but Skype for Linux still isnt anywhere near as good as Skype for Windows. And Linux still lacks an acceptable solution for multimedia communication over the major IM networks. Unfortunately thats one of the main things people use their desktop computers for. I'm still waiting ona way to do cam with my yahoo friends. This is one of the main things holding me back from using Linux as my defaut operating system. I want to be able to do cam with my friends without them ahving to change their software.Just use ekiga, it just works and there's also a version for windows :
[http://ekiga.org/index.php?rub=5](http://ekiga.org/index.php?rub=5)

The main problem if you want my opinion is proprietary softwares, if skype would have been open source some developers would have surely already added video support to skype.

---

### Post by Johnsie on 2007-06-19
Yeah I agree about the proprietty software thing being the cause.  Thanks for letting me know about eh windows version of ekiga. I might check that out when I get home from work. IM should really be open protocols like email... But I guess then it would be hard for the big companies to keep their customers.

---

### Post by frodon on 2007-06-19
> **Johnsie said:**
> Yeah I agree about the proprietty software thing being the cause.  Thanks for letting me know about eh windows version of ekiga. I might check that out when I get home from work. IM should really be open protocols like email... But I guess then it would be hard for the big companies to keep their customers.Yep that's the point. About ekiga windows version it is the first one developed and it is still  in beta stage so there's still some bugs, but it's a really good start.
I truly hope ekiga windows version will become soon as good as the linux one.

---

### Post by pete on 2007-06-19
Between losing the ability to manipulate my contacts (groups, hiding offline contacts, etc.) and a huge drop in sound quality, I found v1.4 to be pretty much unusable.  

I've gone back to 1.3.

---

### Post by Pekkalainen on 2007-06-19
How do I revert back to 1.3? :(

---

### Post by mtron on 2007-06-20
just uninstall the skype 1.4 via synaptic, or if you prefer the terminal:

```
sudo dpkg -r skype
``` 

then download the old 1.3. and double click on the package (gdebi package installer will open) or via terminal:

```
cd $HOME
wget http://download.skype.com/linux/skype_debian-1.3.0.53-1_i386.deb
sudo dpkg -i skype_debian-1.3.0.53-1_i386.deb
```

---

### Post by kszys on 2007-06-21
Worked like a charm! Thanks!

kszys.

---

### Post by proxess on 2007-06-21
i have never seen anything so ugly in my life... other than some few women here and there... this skype version is terrible, must roll back imediatly.

---

### Post by PartisanEntity on 2007-08-06
There is a new version: **Version 1.4.0.94 for Linux. August 1, 2007**

Has anyone tried it yet? Does it solve the audio problem?

---

### Post by frodon on 2007-08-06
Great, the previous was working great for me but i'm going to try this one as soon as i can :)

---

### Post by Obor on 2007-08-06
I never had problems with the previous one and this version works fine on my PC too. No issues at all (except for the ugly icon in my systray, on black background)

---

### Post by SLA_leandrin on 2007-08-06
The main problem about version 1.4 is they lack of support for OSS, it only works with ALSA.
The skype page says that all the future versions will only support ALSA too.

But despite of that, it seems fine to me.

---

### Post by PartisanEntity on 2007-08-06
I was not able to make voice calls with 1.4 because people on my contact list could not hear me even though I heard them quite well. I just installed the latest version and have yet to test it.

---

### Post by lodp on 2007-08-07
i had a few problems installing 1.4.0.94 from the deb package, as the installer complained about libqt4-core and libqt4-gui not being configured (event though appropriate versions of both of those were installed). i had adept re-install the two packages, and all worked out after that.

apart from that little issue, the new 1.4.0.94 works like a charm for me. and i can't see why anybody would find it less attractive than any 1.3 version.

---

### Post by frodon on 2007-08-07
Seems to work pretty well for me too though i had to delete my .skype directory to get it work

---

### Post by frodon on 2007-08-09
A new version is available 1.4.0.99 which correct some bugs that some users had with the 1.4.0.94 version :
[http://www.skype.com/intl/en/download/skype/linux/](http://www.skype.com/intl/en/download/skype/linux/)

---

### Post by PartisanEntity on 2007-08-11
This latest version works for me, voice calls are working again, however I noticed that while I am having a voice call, my wireless connection will disconnect for a second or two sporadically, actually it dips down to 0% strength and then comes back up again. Switching off Pidgin and Evolution seemed to improve the connection.

---

### Post by freeflyer57 on 2007-08-18
I Don't like anything about 1.4.0.99. Where can I get skype-1.4.0.74? I Had no problems with it. Now I don't get IM unless both of us are online, which is pointless. The other day my girlfriend, who lives in germany,  instant messaged me through skype to tell me that she was going to be in bavaria for three days. I never got the message. I was worried sick about where she was. When she finally got back home and logged on. All of the messages that she sent before she left were immediately sent to me. WTF!?

---

### Post by freeflyer57 on 2007-08-18
I found a place that has older versions of skype to revert back to!
[http://eclipxe.com.mx/debian/contrib/skype/]("http://eclipxe.com.mx/debian/contrib/skype/")

---

### Post by YannickDefais on 2007-08-18
Hi,

Well, for those of you willing to use VoIP with video there is Ekiga as mentioned before. But most people make a mistake : the whole point of using Ekiga is about using an industrial standard (SIP, or H.323 for instance), not about using  a particular software. This means Ekiga as a huge compatibility list with other softwares using those protocols on any system, including Windows of course.

I personally maintain a list of such softwares here (sorted by operating system and features):
[http://wiki.ekiga.org/index.php/Which_programs_work_with_Ekiga_%3F](http://wiki.ekiga.org/index.php/Which_programs_work_with_Ekiga_%3F)

The most convenient way, as for now, to be able to use Ekiga with someone using windows is either to ask him to install Ekiga-BETA for windows (but this might not work properly sometimes, it's still BETA) OR if your contact has windows XP to ask him to use Windows Messenger 5.1 which is shipped with XP (nothing to install!) and to follow this howto connect Windows Messenger to ekiga.net:
[http://wiki.ekiga.org/index.php/Connecting_Windows_Messenger_5.1_to_ekiga.net](http://wiki.ekiga.org/index.php/Connecting_Windows_Messenger_5.1_to_ekiga.net)

Ekiga is compatible for audio, video and instant messaging (text) with Windows Messenger 5.1.

In a near future, the incoming Ekiga 3.0 will have even more video codecs, and I highlight here the video codec H.264 which will bring to Ekiga the finest picture available today. H.264 is what iChat use. This is a really huge improvement over the actual H.261 video codec Ekiga 2.0.x uses. Other video codecs like H.263+ will bring even more compatibility for video chat with windows users, giving them more choice, e.g. they could use x-lite or kapanga.

Here is the Ekiga roadmap:
[http://wiki.ekiga.org/index.php/Roadmap_to_3.00](http://wiki.ekiga.org/index.php/Roadmap_to_3.00)

Regards,
Yannick

---

