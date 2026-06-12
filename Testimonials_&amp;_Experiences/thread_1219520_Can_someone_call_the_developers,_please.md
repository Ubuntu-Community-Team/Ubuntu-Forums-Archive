---
title: "Can someone call the developers, please?"
date: 2009-07-21
forum: Testimonials &amp; Experiences
---

### Post by AICollector on 2009-07-21
Listen, I know Ubuntu is Canocial's centerpieace, but after using Kubuntu...honestly, and that was a release? Your sure? It felt like Alpha to me.

This is a very silly situation. Why is KPackageKit included? It's not anywhere near prime-time usage. Why the hell is KNetworkManager on here and other systems not? Did you acutally beta-test that thing?

Listen, GNOME is not for everyone. Kubuntu 9.04 is a terrible release, it's not just lacking polish, it's lacking testing of two major system-critical parts. How can I connect without a connection manager that times out before it even sends a signal? How can I install software with a packagemanager that somehow blocks half it's updates? What the hell is wrong with you people? Why the hell does it feel like you just threw everything togther? So much for this thing being part of the 'Ubuntu' family, it's user friendly, sure...if your idea of 'user friendly' means "takes up less then 4 hours to install and set up correctly."



Please, either release a functional Kubuntu 9.10, or dont release one at all. I dont mean to tread on anyone's feelings, but the Kubuntu line seems to be going downhill over the past few releases. Can you people PLEASE just give Kubuntu some attention for once?

-AICollector

---

### Post by izizzle on 2009-07-21
Hmmm... I'd say Kubuntu is pretty stable actually...I like KPackageKit more than Synaptic and I never had any trouble with KNetworkManager, although I know some people do. I use WICD anyways. As for blocking half the updates...have you made sure all your sources are enabled and functional?

---

### Post by jerrrys on 2009-07-21
Fud

---

### Post by cariboo on 2009-07-21
This really isn't a support question, it is more of a rant, Moved to Testimonials & Experiences.

---

### Post by wirelessmonkey on 2009-07-22
I use Kubuntu, have no problems with KPackageKit, and I use XSupplicant, rather than KnetworkManager, so there?
Seriously, as cariboo said, this is a rant.
WM

---

### Post by Dullstar on 2009-07-22
I've been doing great with Ubuntu, so maybe you could switch to that.
XFCE is okay.
Try an earlier version, I've heard that the desktop environment used by earlier Kubuntu versions are better.

EDIT:  Don't know if earlier versions of KDE would do anything, but you say the Kubuntu family was once better?

---

### Post by ubuntu27 on 2009-07-22
I am not a Kubuntu user, but give it another chance on new releases..

Or, go to the following website and update Kubuntu Jaunty's KDE:


Follow the instruction [on this site]("http://www.kubuntu.org/news/kde-4.2.4") to install/update KDE:

[http://www.kubuntu.org/news/kde-4.2.4](http://www.kubuntu.org/news/kde-4.2.4)



More info:

[http://kde.org/announcements/announce-4.2.4.php](http://kde.org/announcements/announce-4.2.4.php)

 **KDE Community Improves Desktop with KDE 4.2.4**

> KDE Community Ships Fourth Translation and Service Release of the 4.2 Free Desktop, Containing Numerous Bugfixes, Performance Improvements and Translation Updates 

---

### Post by Dullstar on 2009-07-22
By the way, if you'd like to know something there are several desktop environments you can add WITHOUT harming your current ones.

I have GNOME, KDE, XFCE, LXDE (I learned of this one on Wikipedia), and Fluxbox.  In my opinion, GNOME was the best, but different people have different opinions.

I will post the directions for all of these in the appropriate section.

---

### Post by Armor Nick on 2009-07-22
I haven't used Kubuntu in a while because I don't see the need to change from Gnome (most apps I use are GTK). But if I had to, I'd use Mandriva or OpenSuse. Ubuntu is basically a GTK distro, while Mandriva and Suse do KDE much better.

---

### Post by irv on 2009-07-22
I see AICollector gave his rant, and has not been back to post again. Maybe he is not looking for advice?
Anyway, I can't give any, I use Ubuntu not Kubuntu.

---

### Post by AICollector on 2009-07-22
My apologies...but spending four bloody hours on a setup using tools that dont seem quite right for the job had my temper flaring like a box of thermite with a flare attached.

KPackageKit just tells me it has 8 blocked updates avaible...ummm...why are they blocked, and why is it telling me there are updates when it won't let me install them? That brings me onto KNetworkManager...due to the rather insane way KPackageKit works, I could not remove the malfunctioning KNetworkMangager, because KPackageKit removes, then downloads, then installs a replacement package, instead of Synaptic; which downloads, removes, installs. So I would of had to cut my internet connection to download a new connection manager...

I tried Mandriva, X wont boot. I tried OpenSUSE, and for some reason my screen brightness is brought down quite hard. (to the point of not being able to see the screen if light is only reflecting off it)


I also got fed up with Kubuntu's inclusion of PulseAudio, which kills sound through Phonon right away. Which means either Amarok and system sounds work (when PulseAudio gives up) or flash and vlc works. I removed Pulseaudio and added in a Gstreamer backend for Phonon, which solved that problem.

My main problem, though, was that Kubuntu is part of the Ubuntu family, Kubuntu was by no means easy to setup, and there are even a few leftovers where help boxes (which are intended to guide the user in some instances) refer to the distro as 'Ubuntu'. 



BTW, the reason I moved from GNOME to KDE was because I rather like Amarok, Oxygen and all that jazz. Attempting to install KDE side-by-side with GNOME left me with no working desktop enviroment.


Simply put; if I hadnt spent the last few months reading up on programs, then I would of given up entirely.

---

### Post by izizzle on 2009-07-22
KPackageKit blocks updates for a reason. If you would have downloaded and installed them, they may have clashed with earlier versions of the packages which were already installed on your system. Alternatively, you could have done "apt-get dist-upgrade" and it would have installed the blocked updates.

I don't use pulseaudio anyway, so can't help you there.

As for the network manager: Install WICD through KPackageKit and remove KNetworkManager from the autostart list or alternatively remove it from your computer. I don't know what was so hard there...

Kubuntu is and will stay part of the Ubuntu family of distros, because for *MOST* people it is easy to set up and because it uses the same base.

---

### Post by irv on 2009-07-22
> **izizzle said:**
> KPackageKit blocks updates for a reason. If you would have downloaded and installed them, they may have clashed with earlier versions of the packages which were already installed on your system. Alternatively, you could have done "apt-get dist-upgrade" and it would have installed the blocked updates.

I don't use pulseaudio anyway, so can't help you there.

As for the network manager: Install WICD through KPackageKit and remove KNetworkManager from the autostart list or alternatively remove it from your computer. I don't know what was so hard there...

Kubuntu is and will stay part of the Ubuntu family of distros, because for *MOST* people it is easy to set up and because it uses the same base.
I also use the wicd network manager but I use it on Ubuntu not kubuntu. I find it much better to work with and it just find all the wireless connections around me no matter where I am. Just a matter of clicking on the connect button and you set to go.

---

### Post by HappyFeet on 2009-07-22
> **AICollector said:**
> 
KPackageKit just tells me it has 8 blocked updates avaible...ummm...why are they blocked, and why is it telling me there are updates when it won't let me install them? I could not remove the malfunctioning KNetworkMangager, because KPackageKit removes, then downloads, then installs a replacement package, instead of Synaptic; which downloads, removes, installs. So I would of had to cut my internet connection to download a new connection manager...

I tried Mandriva, X wont boot. I tried OpenSUSE, and for some reason my screen brightness is brought down quite hard. (to the point of not being able to see the screen if light is only reflecting off it)
I also got fed up with Kubuntu's inclusion of PulseAudio, which kills sound through Phonon right away. Which means either Amarok and system sounds work (when PulseAudio gives up) or flash and vlc works. I removed Pulseaudio and added in a Gstreamer backend for Phonon, which solved that problem.

Sounds to me like your computer is *very* linux incompatible. (there are a few computers that are very proprietary) I can run any distro with any desktop environment with no problems. Perhaps you should just stick to windows until you can get a computer that is either linux friendly, or with linux preinstalled. Good luck to you and peace.

---

### Post by AICollector on 2009-07-22
> **izizzle said:**
> KPackageKit blocks updates for a reason. If you would have downloaded and installed them, they may have clashed with earlier versions of the packages which were already installed on your system. Alternatively, you could have done "apt-get dist-upgrade" and it would have installed the blocked updates.

I don't use pulseaudio anyway, so can't help you there.

As for the network manager: Install WICD through KPackageKit and remove KNetworkManager from the autostart list or alternatively remove it from your computer. I don't know what was so hard there...

Kubuntu is and will stay part of the Ubuntu family of distros, because for *MOST* people it is easy to set up and because it uses the same base.


I dont use it either, but I have to wonder why PulseAudio (which conflicts with Phonon, which is also provided by default, thus causing lack of any and all sound) was installed by default.

Yes, thank you for your little how-to there, as it so happens, I am COMPLAINING because KPackageKit will REFUSE to do anything with WICD until KNetworkManager is gone. I don't know about you, but under the particular physical laws of MY Universe, once I disconnect from the internet and remove the program that connects me to it, I cannot then download another program off the internet to connect to the internet. So, I'd love to be able to do what you suggest. What I acutally had to do to get online was go on KPackageKit, reload, download Synaptic. Run Synaptic to install WICD (which removed KNetworkManger and the related Plasmaoid) and bingo. THAT was what was so bloody hard about it. If I installed any updates then KNetworkManager would refuse to function at all. Let alone give me the 10 minutes it does after a fresh install to get everything sorted.

Now, if I have to explain that all again, I shall scream.

---

### Post by AICollector on 2009-07-22
> **HappyFeet said:**
> Sounds to me like your computer is *very* linux incompatible. (there are a few computers that are very proprietary) I can run any distro with any desktop environment with no problems. Perhaps you should just stick to windows until you can get a computer that is either linux friendly, or with linux preinstalled. Good luck to you and peace.

Linux incompatible? No, not really. Vista was far worse, beleive me.

Stick to WIndows? are you mad? I have no intention of going back to that defragging, anti-virus scanning hell-hole.

---

### Post by HappyFeet on 2009-07-22
> **AICollector said:**
> Linux incompatible? No, not really. Vista was far worse, beleive me.

Stick to WIndows? are you mad? I have no intention of going back to that defragging, anti-virus scanning hell-hole.

Well obviously linux is not running good for a reason. Anyway, why not try a gnome based distro. It is painfully obvious that KDE is not working for you. Have fun pulling your hair out.

---

### Post by AICollector on 2009-07-22
KDE IS working for me. It's just painfully obvious that the software provided cannot do the job it was put in to do.

---

### Post by izizzle on 2009-07-22
> **AICollector said:**
> I dont use it either, but I have to wonder why PulseAudio (which conflicts with Phonon, which is also provided by default, thus causing lack of any and all sound) was installed by default.

Yes, thank you for your little how-to there, as it so happens, I am COMPLAINING because KPackageKit will REFUSE to do anything with WICD until KNetworkManager is gone. I don't know about you, but under the particular physical laws of MY Universe, once I disconnect from the internet and remove the program that connects me to it, I cannot then download another program off the internet to connect to the internet. So, I'd love to be able to do what you suggest. What I acutally had to do to get online was go on KPackageKit, reload, download Synaptic. Run Synaptic to install WICD (which removed KNetworkManger and the related Plasmaoid) and bingo. THAT was what was so bloody hard about it. If I installed any updates then KNetworkManager would refuse to function at all. Let alone give me the 10 minutes it does after a fresh install to get everything sorted.

Now, if I have to explain that all again, I shall scream.

Dude, chill. KPackageKit works if you know how to use it. If Synaptic is easier for you, go with it. Sheesh....do you need a medic?

---

### Post by irv on 2009-07-22
I am sitting in a Coffee shop right now, here is what I mean by wicd finding wireless networks.
[ATTACH]122033[/ATTACH]

---

### Post by HappyFeet on 2009-07-22
> **AICollector said:**
> KDE IS working for me. It's just painfully obvious that the software provided cannot do the job it was put in to do.

Why does it work for other people then?

---

### Post by Tamlynmac on 2009-07-22
[> ]("http://ubuntuforums.org/member.php?u=718079")[jerrrys]("http://ubuntuforums.org/member.php?u=718079")
Fud

+1

Others should have noted your response and believed. "yawn"

---

### Post by AICollector on 2009-07-22
I see, so instead of saying 'Hang on a min, there is a bit of a problem here' you accuse me of spreading FUD?

As it happens, I had mentioned this a few weeks eariler, though I cannot remember doing so :S

[http://ubuntuforums.org/showthread.php?t=1203979](http://ubuntuforums.org/showthread.php?t=1203979)

I'll need a bloody medic if people accuse me...ME of FUD. How bloody well dare you! I Love Linux, and I'm SO bloody sorry if something fails to meet my extremely low standards of being able to connect to the network and behave sanely!


As an experiment, try and install wicd through KPackageKit if you have KNetworkManager. Go on. Give it a go.

Done it? Good.

See the problem?

Good. That was what was pissing me off.


I dont bloody beleive half of you people, you'll be calling me a M$ shill next! How bloody well dare you! :x

---

### Post by HappyFeet on 2009-07-22
[IMG]http://www.boston.com/yourlife/family/blog/baby-crying%20jpg.jpg[/IMG]
Btw, [here]("http://ftp.osuosl.org/pub/ubuntu/pool/universe/w/wicd/wicd_1.5.9-2_all.deb") is the .deb file for wicd. Click to install.

---

### Post by Tamlynmac on 2009-07-22
> HappyFeet

[IMG]http://www.boston.com/yourlife/family/blog/baby-crying%20jpg.jpg[/IMG]
Btw, [here]("http://ftp.osuosl.org/pub/ubuntu/pool/universe/w/wicd/wicd_1.5.9-2_all.deb") is the .deb file for wicd. Click to install. 	

:lolflag:  :lolflag:

---

### Post by irv on 2009-07-22
The same version is in the repo!!!

---

### Post by AICollector on 2009-07-22
Oh, thank you so much.

Oh, by the way, dependancies are not satisfiable...without an internet connection.

So really, you've been really helpful.
Do continue, I'm sure when your as frustrated by things as I am, I'll be sure to repay your debt in full.

---

### Post by kelvin spratt on 2009-07-22
My advice is walk away and have a think there is always a solution sometimes we can't see the wood for the trees.

---

### Post by AICollector on 2009-07-22
What a good idea! Yes, I can see there are some folks here who just arent bothering to read what I type in it's entirerity. 

Cheerio.

-AICollector

---

### Post by HappyFeet on 2009-07-22
I suggest you start a thread in the appropriate forum to get help. This thread is going nowhere and should be closed.
> **AICollector said:**
> 
Do continue, I'm sure when your as frustrated by things as I am, I'll be sure to repay your debt in full.
I've never been frustrated by ubuntu, as it has always worked perfect for me. So don't hold your breath waiting for that to happen.  Take care AlCollector, and good luck.

---

### Post by izizzle on 2009-07-22
> **AICollector said:**
> I see, so instead of saying 'Hang on a min, there is a bit of a problem here' you accuse me of spreading FUD?

As it happens, I had mentioned this a few weeks eariler, though I cannot remember doing so :S

[http://ubuntuforums.org/showthread.php?t=1203979](http://ubuntuforums.org/showthread.php?t=1203979)

I'll need a bloody medic if people accuse me...ME of FUD. How bloody well dare you! I Love Linux, and I'm SO bloody sorry if something fails to meet my extremely low standards of being able to connect to the network and behave sanely!


As an experiment, try and install wicd through KPackageKit if you have KNetworkManager. Go on. Give it a go.

Done it? Good.

See the problem?

Good. That was what was pissing me off.


I dont bloody beleive half of you people, you'll be calling me a M$ shill next! How bloody well dare you! :x

I did install bloody WICD from bloody KPackageKit and it worked bloody fine! You're not a vampire by any chance, are you? :P

---

