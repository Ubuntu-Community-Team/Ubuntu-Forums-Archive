---
title: "How to make Kubuntu (KDE) blazing fast and optimise it for performance"
date: 2011-11-30
forum: Tutorials
---

### Post by kio_http on 2011-11-30
I've been seeing a lot of comments criticizing KDE and Kubuntu  especially concerning performance and decided to write this thread.
 [B][SIZE=3]
[COLOR=Navy]Contents[/COLOR]
_____________________________________________
[/SIZE][/B]**[COLOR=Black]_[SIZE=3]1. Don't be scared from a previous experience with it[/SIZE]_[/COLOR]**
**[SIZE=3]_2. Updates_[/SIZE]**
[SIZE=3]_**3. Graphic drivers**_[/SIZE]
[SIZE=3][U][B]4. Optimising KDE settings
[/B][/U][/SIZE][SIZE=2][B]1) Reducing shader quality and CPU usage
 [/B][/SIZE][SIZE=2][B]2) Configuring Desktop Effects
[/B][/SIZE][SIZE=2]** 3) Speeding up KDE start up**[/SIZE]
 [SIZE=2][B]4) Removing unwanted animations
 [/B][/SIZE][SIZE=2][B]5) Disable unwanted krunner plugins
[/B][/SIZE][SIZE=2]** 6) Don't keep to many plasmoids (desktop or dashboard widgets)**[/SIZE]

[SIZE=3]**_Misc_**[/SIZE]
 [B][SIZE=2]1) Install the kubuntu-low-fat-settings package
 2) Reset KDE to defaults
[/SIZE][/B]
[SIZE=2][B][U][SIZE=3]Common stereotypes/thoughts about Kubuntu[/SIZE]
[/U][/B] [B]1) Kubuntu is Ubuntu with plain KDE on it.
 2) Kubuntu should include a branded wallpaper[/B][/SIZE]

[SIZE=3]**_Useful tip_**[/SIZE]

 **[SIZE=3]_____________________________________________[/SIZE]**
[B]
[COLOR=Black]_[SIZE=3]1. Don't be scared from a previous experience with it[/SIZE]_[/COLOR][/B]

Don't give up on Kubuntu because you tried it months back and  didn't like it. I know that this sounds stupid but this is the major  mistake people make. KDE has been seeing a lot of performance fixes only  recently most notably the[ kwin port to Open GL 2 and GLES.  ]("http://blog.martin-graesslin.com/blog/2011/07/running-kwin-with-opengl-es-2-0/")If you look at [Martin Gräßlin's blog]("http://blog.martin-graesslin.com/blog/"),  there is a lot of information about performance improvements being  done. In fact expect the January release of KDE 4.8 to be a real  exceptional improvement in terms of performance with improvements like [dolphin 2.0 ]("http://cristalinux.blogspot.com/2011/11/look-at-kde-48-dolphin-20.html")and  QML. When KDE 4.0 was released, it did suffer from lacking features and  performance issues. However it was a complex (and necessary) transition  because KDE 3 relied on a lot of older things like QT3 which were no  longer being supported. Up to KDE 4.5 the main focus was on enriching  functionality, now that all the improvements have been made, developers  are focusing on performance.

**[SIZE=3]_2. Updates_[/SIZE]**

As  I mentioned early, massive improvements are brought with each update.  However not all these updates reach users quickly enough because of  Ubuntu's way of dealing with them. To get the latest (stable) version of  KDE, keep a regular check on [kubuntu.org]("http://www.kubuntu.org/") for information about the latest release. You can get latest KDE updates from the kubuntu backports ppa.

Note:  This is an official ppa maintained by the Kubuntu packaging team itself  for stable releases of KDE. The packages undergo a lot of testing  before being released. First they are tested by KDE uptream then by the  Kubuntu team.

To add this ppa

1) The command line way

```
sudo apt-add-repository ppa:kubuntu-ppa/ppa
sudo apt-add-repository ppa:kubuntu-ppa/backports
sudo apt-get update
sudo apt-get dist-upgrade

```2) The GUI way

Open Muon Package Manager from the menu (on taskbar). Click Settings and "Configure software sources"

The following dialogue should show up
[IMG]http://www.picamatic.com/show/2011/11/30/05/36/8053823_624x437.png[/IMG]
Under the "Other Software" tab add "ppa:kubuntu-ppa/ppa" and "ppa:kubuntu-ppa/backports" (without quotes) and update the system in Muon.

[SIZE=3][U]**3. Graphic drivers**
[/U][/SIZE]Note: I would not recommend messing too much with drivers do this only if you think you have faulty drivers.

KDE relies a lot of graphic drivers and it is common to see drivers getting fixes specifically to support functionality in KDE

Nvidia Users  and Intel users can get updates from this ppa of stable drivers (Use instructions in previous section to add)
**ppa:ubuntu-x-swat/x-updates**

Ati users should read [this article]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") from the Ubuntu Documentation

[B]Intel  Users might want to try experimental SNA support. Intel SNA is a new  acceleration method for Intel GPU's. While it is aimed at Sandy Bridge  chips, it also helps older GPU's as well. If you know the risks see [this]("https://launchpad.net/%7Esarvatt/+archive/intel-sna") to enable SNA

[/B][SIZE=3][U]**4. Optimising KDE settings**

[/U][/SIZE]There are many tweaks to make KDE run smoothly on your system.
[SIZE=2][B]
1) Reducing shader quality and CPU usage[/B][/SIZE]

Although  it may sound like I am trying to give you bad quality graphics, I  assure you this is not the case. The shader quality change will be  completely unnoticeable on your system.  

Open System Settings and click on "Application Appearance"
Under Style, go to the "fine tuning tab" and set Low display resolution and Low CPU" as shown
[IMG]http://www.picamatic.com/show/2011/11/30/07/10/8053970_632x456.png[/IMG]
[SIZE=2]**2) Configuring Desktop Effects**[/SIZE]

Desktop  composition is quite popular on OS GUI's nowadays from Windows 7 to OS X  and GNOME however they do demand some GPU power.  

To open the configuration pane, open "Desktop Effects" from system settings

_**a. The General Tab**_

If  your computer is really slow and has a very outdated GPU consider  disabling the effects altogether.  (For most users, this is not  necessary). 

If you chose to keep desktop effects, I would recommend changing animation speed to Fast in the combobox.
[U]
**b. The All effects  Tab**[/U]
Here I would recommend looking into three plugins

**Blur**
Blur  is the most resource hungry effect in KDE although it does look really  nice and most systems should handle it just fine. However I would  recommend clicking the wrench to configure and and reduce the strength  of the effect. According to me a lower strength actually looks slightly  better. If you don't want blur or believe that you system cannot handle  it, feel free to disable the effect.
  
[B]Translucency
[/B]This  plugin by default makes your windows translucent when dragged. I find  that this is rather unnecessary and wastes resources for no reason. I  would recommend disabling it
  
[B]Resize Window
[/B]Enabling  this effect actually speed up resizing Windows. Under the configuration  options you will find that you can use either the outline or a scaled  texture.

[U][B]c. The Advanced Tab

[/B][/U]Here,  I would recommend you set scale method to "Crisp" for best results. The  visual difference between these options is really negligible. 

Note:  Changing Compositing type to "Xrender" uses the CPU for effects,  although many effects will get disabled this is a very good idea on old  graphic cards that are not supposed to be doing compositing. (Similar to  disabling all effects in a way)

**On some Intel Chips I have noticed better performance with vsync on**
[IMG]http://www.picamatic.com/show/2011/11/30/07/48/8054012_646x478.png[/IMG]

[SIZE=2][B]3) Speeding up KDE start up

[/B][/SIZE]In  "System Settings" under "system administration" launch the "Startup and  Shutdown" settings and enter the service manager section. Disable  services that you do not need E.g If you do not need bluetooth, uncheck  "BlueDevil"

Note: By default KDE restarts all applications that  have not been closed on shutdown when it starts up. If you like this  behavior, I find that it is faster to Hibernate (Suspend to Disk) rather  than shutdown the system.

You can change KDE's autostart behavior in the Session Management section in this same configuration dialogue.

[IMG]http://www.picamatic.com/show/2011/11/30/07/55/8054024_645x476.png[/IMG]

[SIZE=2][B]4) Removing unwanted animations

[/B][/SIZE]The  default oxygen style comes with many unwanted animations that can be  disabled without significantly reducing the user experience.

Press "Alt + F2" and type "oxygen-settings"
[IMG]http://www.picamatic.com/show/2011/11/30/08/03/8054026_454x93.png[/IMG]

Under  the "Animations" tab disable the unwanted animations. I would recommend  disabling all of them as none of them are actually useful or  significantly noticeable. They also use a considerable amount of  resources.
[IMG]http://www.picamatic.com/show/2011/11/30/08/07/8054031_598x474.png[/IMG]

[SIZE=2][B]5) Disable unwanted krunner plugins

[/B][/SIZE]Krunner  is an extremely powerful tool in KDE. However not everybody uses all  the features that it offers. (Some people merely use it to run commands)  Disabling the plugins that you do not use will reduce resource usage

Press "Alt + F2" and press the wrench on the left side. Disable all the plugins that you do not need.

[IMG]http://www.picamatic.com/show/2011/11/30/08/14/8054039_423x504.png[/IMG] 

[SIZE=2][B]6) Don't keep to many plasmoids (desktop or dashboard widgets)

[/B][/SIZE] To many plasmoids can significantly reduce performance especially CPU usage monitors and such. Don't keep too many plasmoids.

[SIZE=3]
[/SIZE] [SIZE=2][B][U][SIZE=3]Misc[/SIZE]

[/U][/B][/SIZE]If KDE is still running slow there are two things you can do.

1) Install the kubuntu-low-fat-settings package

This  package is intended for slow computers and allowed me (with some more  tweaks) to run Kubuntu on a 600 Mhz Pentium 3 with 768 Mb RAM. More  details can be found [here]("http://dohbuoy.wordpress.com/2011/09/23/slim-it-down/").

2) Reset KDE to defaults

If  you feel that you have messed up KDE too much and want to revert to  defaults, you can delete all its settings and have KDE recreate them.

[COLOR=Red]Note: You will lose all settings (Desktop, Documents, Pictures etc remain).[/COLOR]

Login to a console session or in recovery mode do

You may explore the .kde folder for a particular config file that you wish to reset instead of deleting the whole thing.

```
cd /home/MyUsername
rm -rf .kde

```3) Removing Ubuntu/Lubuntu/Xubuntu packages for a pure Kubuntu system

Since [Aysiu]("http://ubuntuforums.org/member.php?u=21941") has a perfect tutorial on his website I will [redirect you there]("http://www.psychocats.net/ubuntu/purekde"). His blog also has a lot of other valuable information e.g how to chose between DE's


[SIZE=2][B][U]Common stereotypes about Kubuntu
  
[/U][/B][/SIZE]1) Kubuntu is Ubuntu with plain KDE on it.

This is quite untrue. While the Kubuntu development team is extremely  small they have made muon, the message notifier and some other small  things. Many of them also do a lot of upstream work on KDE which  obviously reaches all distros. This is the spirit of Open Source, we do  not want things to be Kubuntu. Fedora and OpenSuSe specific, we share  each other's contributions.

2) Kubuntu should include a branded wallpaper

As some of you may recall in the KDE3 days Kubuntu did indeed have its  own wallpaper. However nowadays, Kubuntu's ISO reaches 699 Mb, so  including a wallpaper makes it by pass the cd limit. CD size is a major  constraint for Kubuntu. However you can install the kubuntu-full package  for more things (This package may give a lot of unwanted things  beware). kdegames and all popular packages are available in the repos. 
[SIZE=3][COLOR=Black]
  [/COLOR][/SIZE][SIZE=2][B][U]Useful tip
[/U][/B][/SIZE]By default when installed on a small screen device,  Kubuntu uses a different interface. If you want to use the normal  interface on a device like a netbook, go to system settings >  Workspace Behaviour > Workspace and change it to desktop

[IMG]http://www.picamatic.com/show/2011/11/30/09/06/8054124_652x486.png[/IMG]
[SIZE=3][COLOR=Black]
Thanks  for reading, I hope you liked this post. Feel free to contribute tips  of your own. If your KDE system is slow, I can try to help you if you  provide your hardware information and the list of processes running with  CPU and memory usage.[/COLOR][/SIZE]

---

### Post by nothingspecial on 2011-12-02
Thank you.

---

### Post by kio_http on 2011-12-03
> **nothingspecial said:**
> Thank you.

Glad you like it, but maybe "U"buntuforums isn't the best place for this post it seems. Not many people use KDE here.

---

### Post by kef_kf on 2011-12-03
Good stuff, thanks.

---

### Post by kio_http on 2011-12-05
Image host is down, if it doesn't come back up, I'll try to sort that out.

---

### Post by kio_http on 2011-12-06
Images Fixed!

---

### Post by lykwydchykyn on 2011-12-06
Thanks for this.

I've also found that disabling Nepomuk and Strigi can make a significant difference, and I rarely use it anyway.  What are your thoughts on this?

---

### Post by kio_http on 2011-12-06
> **lykwydchykyn said:**
> Thanks for this.

I've also found that disabling Nepomuk and Strigi can make a significant difference, and I rarely use it anyway.  What are your thoughts on this?

Strigi is disabled by default and in newer releases of KDE nepomuk does not cause a significant slow down. However if you don't use it you might as well disable it. Disabling akondani might be OK too. Actually I think the low fat settings disables all of these.

---

### Post by kappel79x64 on 2011-12-07
hi,


my kde runs better now and respond much faster, the lag is now gone.

i left nepomuk untouched but i changed every other option like you explained, and the PPA update didnt get me into any trouble but i didnt noticed any improvement from the update either. 




):P ciao

---

### Post by goucher on 2011-12-16
Thanks for this.:KS

---

### Post by samgoober on 2012-02-01
Thank you for taking the time to write this post my friend! It was most-kind of you to take the time to help out what has to be (or will be) thousands of people. You are a true gentleman.

Thanks again,
Sam

---

### Post by jan-12 on 2012-02-06
Exactly what I was looking for since moving to Kubuntu Oneiric.  Thanks, man!;)

---

### Post by ibm450 on 2012-02-09
thanks & good informative post.

any further updates to this post, any extra tweaks available? is there to switch off HHD when not in use or at idle?

:popcorn:

---

### Post by kio_http on 2012-03-11
> **ibm450 said:**
> thanks & good informative post.

any further updates to this post, any extra tweaks available? is there to switch off HHD when not in use or at idle?

:popcorn:

```
sudo apt-get install hdparm
sudo hdparm -Y /dev/sdX
```

---

### Post by Chichipio on 2012-03-30
Thanks for this. I like it when people don't just give you a recipe to follow blindly, but actually explain the reason behind each step. I've learned some cool things.

I kept noticing some choppiness (nothing serious, but still) on my system that even disabling "desktop effects" altogether didn't seem to help. Now, with your tips, I can see that the animations were to blame for that and, after disabling them, everything runs smoothly even with some nice effects enabled.

---

### Post by BertN45 on 2012-03-30
I get tempted to try it again, do you think it runs on my old desktop (see signature). If I install the desktop, can I delete it again with all the corresponding applications or is it safer to dual boot?

---

### Post by Ravi5kumar on 2012-03-31
Thanks you! I bookmarked this page! Just one question though I think it is silly Will this tweaks applicable for the final release of kubuntu 12.04 LTS??

---

### Post by kio_http on 2012-04-08
> **BertN45 said:**
> I get tempted to try it again, do you think it runs on my old desktop (see signature). If I install the desktop, can I delete it again with all the corresponding applications or is it safer to dual boot?

Your desktop meets the system requirements and should work fine. I didn't quite understand the "an I delete it again with all the corresponding applications or is it safer to dual boot?" part?

Does the desktop already have Ubuntu or something?

---

### Post by herophuong on 2012-04-26
Thank you.
OT: Where's the thank button anw?

---

### Post by gelie on 2012-06-20
Thank you for the very helpful info. Some of it I knew, but it was good to have a more complete look at my system (at a time when I was just about to distro hop, again).

---

### Post by Dinoraptor101 on 2012-07-30
This is really awesome!! disabling the settings made KDE not only running fast .. but more stable on my low-tech 

Computer


AMD Turion 64
2GB DDR1 RAM
128 Gb ATI Radeon

---

### Post by Numer0bis on 2012-08-06
Thanks soo much for your insight knowledge. I really love KDE but always sued xubuntu on my small laptop as it only comes with 2GB of ram. With those settings KDE actually runs quite smoothly.:KS:KS:KS

---

### Post by vasilbelarus on 2012-08-15
This post is wery usefull! Thanks! :)

---

### Post by kio_http on 2012-09-15
> **Numer0bis said:**
> Thanks soo much for your insight knowledge. I really love KDE but always sued xubuntu on my small laptop as it only comes with 2GB of ram. With those settings KDE actually runs quite smoothly.:KS:KS:KS

Glad you liked it. I always felt that people nowadays use XFCE and LXDE on certain computers that are more powerful than they think is a waste of the hardware unless of course the DE is their primary choice.

If the early KDE 4 releases were more stable, it would have been nice. Because now people who tried 4.0, 4.1 etc have prejudice against 4.9 without even trying it.

---

### Post by serdotlinecho on 2012-10-16
Yeah, kde 4.9 is really nice...i'm using kde 4.9(kde-standard package, though) now on top of ubuntu 12.10.  :lolflag:

---

### Post by robtygart on 2012-10-16
Thanks nice thread.

I use Kubuntu on a 2006 HP Pavillin, and its sweet, with effets.

---

### Post by wingnux on 2012-10-17
Really helpful post. Thank you very much!

---

### Post by fooey on 2012-10-22
As someone who hasn't tried KDE in a LONG time, and after reading this post, it makes me want to check it out again. It seems to have matured quite a bit. I'm always up for a change so definitely going to check it out. Thanks

---

### Post by bigpook on 2012-11-13
Good Stuff! Thanks for documenting these changes.

---

### Post by offgridguy on 2012-11-13
Thank you to OP for this.

---

### Post by Deevad on 2012-11-19
Thank you , very informative and still work for my 12.04.

---

### Post by addegsson on 2012-11-22
This is great! :)

---

### Post by sumethc on 2012-12-14
It doesn't end well for me, I'm sorry to report.  I just updated the system by adding new sources via Muon Package Manager following the tutorial ("ppa:kubuntu-ppa/ppa" and "ppa:kubuntu-ppa/backports") and found that, besides a few new applications, I have lost the Muon Package Manager and Muon Software Center, even though I don't really care much for the latter. I found this to be rather disturbing because I seem to understand that no application should be removed in the process. Now I also found that the effect of my original window switching isn't the same anymore. 

My main concern is getting back the Muon Package Manager. Can somebody help? My system is Kubuntu 12.04 LTS running on a dual boot MacBook 3,1 (OS X 10.5.8). How can I remove all new packages that were just installed and get back to the previous state? Thanks for any help.

---

### Post by bvpainter on 2012-12-24
I fairly recently installed Kubuntu 12.4 and at first found it rather slow and heavy on resources. I followed the instructions and everything speeded up. However I thought I would retry with Neopmuk working, so I could use the backup facility. Big mistake. Kubuntu started to use a lot of my resources again, so goodbye Neopmuk, and return of a much more responsive machine.

---

### Post by mendieta on 2012-12-27
Thank you for this. This is what I do on my Kubuntu installs:

* disable ALL startup services in KDE (everything works anyways, I think they are started on demand, but login is faster)
* removed KDEPIM, and configured Akonadi to use no resources beyond the default
* disabled Nepomuk

Another interesting idea (that I use on a netbook):

* install a command line Ubuntu server, or just netinstall
* add a minimal kde 
[http://www.kubuntuforums.net/showthread.php?43708-SOLVED-Building-a-light-KDE4-desktop-for-a-netbook-off-of-Karmic](http://www.kubuntuforums.net/showthread.php?43708-SOLVED-Building-a-light-KDE4-desktop-for-a-netbook-off-of-Karmic)

---

### Post by DeMus on 2013-02-17
Mendieta:

* disable ALL startup services in KDE (everything works anyways, I think they are started on demand, but login is faster)

Is it really safe to disable all the startup services? I have been looking at them a couple of times and I am not sure if I can disable one or not. You say: disable them all.
It's not that some things don't work anymore? The moment I should need a service it will be started?
When you do disable all of them do you notice a general increase in speed, or is it only at log-in?

---

### Post by kio_http on 2013-03-11
> **DeMus said:**
> Mendieta:

* disable ALL startup services in KDE (everything works anyways, I think they are started on demand, but login is faster)

Is it really safe to disable all the startup services? I have been looking at them a couple of times and I am not sure if I can disable one or not. You say: disable them all.
It's not that some things don't work anymore? The moment I should need a service it will be started?
When you do disable all of them do you notice a general increase in speed, or is it only at log-in?

It depends on your needs, I wouldn't recommend disabling everything especially on laptops where bluetooth and notification stuff etc is needed.

Assuming you have a lot of RAM it would only increase startup time and not significantly imporve overall performance.

---

### Post by bs27975 on 2013-05-20
> **kio_http said:**
> 
.
.
.
**_[SIZE=3]Misc[/SIZE]_**

If KDE is still running slow there are two things you can do.

1) Install the kubuntu-low-fat-settings package

This  package is intended for slow computers and allowed me (with some more  tweaks) to run Kubuntu on a 600 Mhz Pentium 3 with 768 Mb RAM. More  details can be found [here]("http://dohbuoy.wordpress.com/2011/09/23/slim-it-down/").
.
.
.


Link above appears broken, update appreciated.

---

### Post by durduvakis on 2013-06-25
nice thread, and I would say kde has improved dramatically since last year even.
Although it is not kde related, for nvidia users, switching the GPU setting inside "PowerMizer" > Preferred Mode, from "Adaptive" to "Prefer Maximum Performance" has dropped the temperature of my laptop's cpu from 40c to 34c (idle). Actually pc gamers know this setting well.

---

### Post by mastablasta on 2013-12-21
great post. makes me feel confident to put the 64 bit on 1 GB ram maschine. CPU shoudl be ok, GPu should be sort of ok. we'lll see hwo it goes. at the moment i have it on a 1,2 GB maschine but this one has better GPU

---

### Post by krust13579 on 2014-05-16
I always liked the kde desktop, but it was running slow; this will sure help me. Thanks.

---

### Post by vasa1 on 2014-09-21
@OP, please see [http://ubuntuforums.org/showthread.php?t=2219737](http://ubuntuforums.org/showthread.php?t=2219737). You may want to edit (or ask a mod to edit) your first post re. low-fat-settings.

---

### Post by MountainX on 2015-01-17
Thank you! KDE is my favorite DE.

---

