---
title: "pidgin 2.6 is out now with voice and video support"
date: 2009-08-19
forum: The Cafe
---

### Post by imlinux on 2009-08-19
this is exciting pidgin with video support, but only for XMPP protocol. you can get new pidgin from [here]("http://www.getdeb.net/app/Pidgin")

---

### Post by CharmyBee on 2009-08-19
It also has a nice vulnerability. I would hold it off until they can confirm that fixed.

---

### Post by Baneblade on 2009-08-19
> **CharmyBee said:**
> It also has a nice vulnerability. I would hold it off until they can confirm that fixed.

What vulnerability?

---

### Post by Polygon on 2009-08-19
> **Baneblade said:**
> What vulnerability?

and does this vulnerability effect 2.6.1 as well?

---

### Post by unoodles on 2009-08-19
I'm pretty sure the vulnerability is only in the updated version.
Here's the /. article on it:
[http://tech.slashdot.org/story/09/08/19/2128210/Pidgin-Adds-Google-Talk-Voice-and-Video-Support-and-a-Vulnerability?art_pos=3](http://tech.slashdot.org/story/09/08/19/2128210/Pidgin-Adds-Google-Talk-Voice-and-Video-Support-and-a-Vulnerability?art_pos=3)

---

### Post by fireman biff on 2009-08-19
According to the [Pidgin changelog]("http://developer.pidgin.im/wiki/ChangeLog#version2.5.908182009") and the [article]("http://www.coresecurity.com/content/libpurple-arbitrary-write") slashdot linked to, the vulnerability existed in 2.5.8 and was fixed in 2.5.9 (which was released the same day as 2.6.0).

The vulnerability is supposedly also in versions prior to 2.5.8, so upgrading might actually be a good idea.

---

### Post by rajcan on 2009-08-19
Is 2.6 available for Intrepid? I'm seeing it for Hardy and Jaunty, but that doesn't do me any good.

---

### Post by sports fan Matt on 2009-08-19
Im planning to retry pidgin.

---

### Post by kevdog on 2009-08-19
You could just as well compile from source as well.  Its very easy to do and only takes minutes.

---

### Post by 3rdalbum on 2009-08-19
> **rajcan said:**
> Is 2.6 available for Intrepid? I'm seeing it for Hardy and Jaunty, but that doesn't do me any good.

It's available as source code, which means you can compile it. Pidgin is easy to compile, just make sure you have the OpenSSL development libraries installed and that you enable them in the configure script (otherwise you won't have MSN support).

Remember to check out the available build options with:

```
./configure --help
```

---

### Post by sports fan Matt on 2009-08-19
error while downloading: Error: Dependency is not satisfiable: pidgin-data (>= 1:2.6.1)

---

### Post by fireman biff on 2009-08-19
> **sox fan Matt said:**
> error while downloading: Error: Dependency is not satisfiable: pidgin-data (>= 1:2.6.1)

pidgin-data is also available on getdeb. Look at the download links and you will see 4 packages that you need to install to use pidgin: pidgin, libpurple0, libpurple-bin and pidgin-data.

If you try to install one and it complains that one of the others is not satisfiable, just install that other one first.

---

### Post by fireman biff on 2009-08-19
> **kevdog said:**
> You could just as well compile from source as well.  Its very easy to do and only takes minutes.

I tried doing that today and eventually gave up. After spending a while sorting out all the dependencies it told me it installed, but when I tried to run it there was an error message saying it was unable to find libpurple. I just reinstalled the version from the repository.

---

### Post by coldReactive on 2009-08-19
Waiting for it to be in the update manager so I don't get any nasty errors.

---

### Post by FuturePilot on 2009-08-19
Gajim is my client of choice, but these new features are tempting me to try Pidgin again.

---

### Post by coldReactive on 2009-08-20
How long does it take to get into the PPA or repo or whatever for Ubuntu? I'm still waiting.

---

### Post by fireman biff on 2009-08-20
> **coldReactive said:**
> How long does it take to get into the PPA or repo or whatever for Ubuntu? I'm still waiting.

From Pidgin's download page: "This PPA is maintained by one developer, so please be patient. It often lags behind the source releases a couple of days."

The karmic repository will probably take longer, and older releases will probably take even longer (if they get it at all).

---

### Post by sports fan Matt on 2009-08-20
question: Pidgin 2.6.1  is the version on getdeb.net
however I have: Pidgin 2.5.8
(libpurple 2.6.1) after downloading from the website..is this the correct version?

---

### Post by fireman biff on 2009-08-20
> **sox fan Matt said:**
> question: Pidgin 2.6.1  is the version on getdeb.net
however I have: Pidgin 2.5.8
(libpurple 2.6.1) after downloading from the website..is this the correct version?

Just remove all the current packages:
```
sudo apt-get remove libpurple0 libpurple-bin pidgin pidgin-data
```

Then, install the files from getdeb one by one. If the installer says the file depends on one of the other files you downloaded then install the other file first. If it depends on another package that is not satisfiable you should use apt-cache to figure out what package to install or search google.

---

### Post by keiichidono on 2009-08-20
> **coldReactive said:**
> How long does it take to get into the PPA or repo or whatever for Ubuntu? I'm still waiting.

If you can't wait, you might wanna try Arch Linux. :P

---

### Post by coldReactive on 2009-08-20
> **CalvinB said:**
> If you can't wait, you might wanna try Arch Linux. :P

Problem: Don't like terminal much.

Problem: Any guides on how to get DVD Playback and are there any flashplugin-nonfree like on Ubuntu? I don't like gnash nor swfdec.

Problem: I absolutely HATE make/install.

---

### Post by sports fan Matt on 2009-08-20
all fixed :)

---

### Post by hyperdude111 on 2009-08-20
> **rajcan said:**
> Is 2.6 available for Intrepid? I'm seeing it for Hardy and Jaunty, but that doesn't do me any good.

It will still work.

---

### Post by mac-duff on 2009-08-20
Hi,

has anybody figured out how does video work?

---

### Post by firefeather on 2009-08-20
> **fireman biff said:**
> I tried doing that today and eventually gave up. After spending a while sorting out all the dependencies it told me it installed, but when I tried to run it there was an error message saying it was unable to find libpurple. I just reinstalled the version from the repository.

I used this command (after putting the terminal into the directory where all the GetDeb files were and making sure no other debs are in the directory)

```
sudo dpkg -i *.deb
```

---

### Post by sikku on 2009-08-20
I am not sure but pidgin 2.6.1 does not have voice and video support whih was installed from the getdeb site...

I tried to install from source but the pidgin.im site says that we should get this line at the end of ./configure
[INDENT]Build with voice and video.... yes [/INDENT]But I am not able to get it... I get No...

Check this link: [http://developer.pidgin.im/wiki/GSoC2008/VoiceAndVideo](http://developer.pidgin.im/wiki/GSoC2008/VoiceAndVideo)

I have installed everything which that link says but I am not able to get the required output.... :(

Can anybody help???

---

### Post by fireman biff on 2009-08-20
> **firefeather said:**
> I used this command (after putting the terminal into the directory where all the GetDeb files were and making sure no other debs are in the directory)

```
sudo dpkg -i *.deb
```

Thanks for the advice, I did manage to get it installed like this. Unfortunately now my system is complaining that I have unmet dependencies (libzephyr3 seems to have been replaced by libzephyr4 in karmic, not that I use Zephyr anyway).

Its nice to be running something other than version 2.5.8 since that one had the big vulnerability, but I really would like to be able to use the voice/video which the getdeb release doesn't seem to support. I guess I'll try installing from source again sometime.

---

### Post by fireman biff on 2009-08-20
Alright, I reinstalled from source and Pidgin complained that it couldn't find libpurple.so.0 again. Fortunately [I was able to solve that with the help of an old thread]("http://ubuntuforums.org/showthread.php?t=491673").

I now have Pidgin 2.6.1 installed on karmic. Help > About shows that I have "Voice and Video: Enabled" and the Conversation menu now has a submenu called Media containing Audio Call, Video Call, and Audio/Video Call. Unfortunately all my online contacts are using old versions of Pidgin or Gmail so I can't test it...

---

### Post by kevdog on 2009-08-20
Do I need to write a how-to how to compile this?  I don't have Jaunty installed however am confident I could compile it in Intrepid.

---

### Post by sikku on 2009-08-21
Has anyone installed it in Jaunty by compiling from source???

---

### Post by puccaso on 2009-08-21
i am getting a "libzephyr3" error... how do i fix this?

---

### Post by sikku on 2009-08-21
I think nobody has compiled on jaunty...

---

### Post by sikku on 2009-08-21
> **puccaso said:**
> i am getting a "libzephyr3" error... how do i fix this?

Can you put paste the complete error message which u get....

---

### Post by alexcckll on 2009-08-21
Umm - what version of Ubuntu will Pidgin 2.6.x make it into?

Just that I wouldn't feel confident doing anything except relying on official packages...

---

### Post by mac-duff on 2009-08-21
Ok,

I ve compiled now Pidgin and have a option video audio but which is also by gmail users greyed out. Do the gmail user also has to run Linux and Pidgin so it does not work with the gmail client on windows?

Another point is, I had to update gstreamer and gst plugin base and now I cant play mp3s with Totem any more, VLC works.

Error is:
```

Totem could not startup.
Could not find the audio output. You may need to install addiotional GStreamer plugins...

```

I ve already reinstalled the packages over the package manager

Thx

---

### Post by Tibuda on 2009-08-21
> **alexcckll said:**
> Umm - what version of Ubuntu will Pidgin 2.6.x make it into?

Just that I wouldn't feel confident doing anything except relying on official packages...

Karmic, aka 9.10

---

### Post by dumblebee100 on 2009-08-21
pidgin 2.6.1 segfaults with google talk so no question of video or audio support ..

even wine version not working ..it says " pidgin.dll not found ..probably gtk+ not found"

so stuck with using pidgin portable version 2.5.8

pidgin portable version 2.6.1 also gives problems ...after connecting to accounts then font becomes gibberish ...I mean I cannot see my buddies ..all they become blacked out ..I mean to say ..they look like striked out with some black lines ....so I cant use even pidgin portable version 2.6.1 ...

Long live pidgin ..which doesnt work for me ..in anyways

---

### Post by sikku on 2009-08-21
I installed pidgin 2.6.1 from source in Fedora 11 and is working fine... I can voice chat and video chat with the other person who is in gtalk... Everything perfect... Clear voice and clear video...
The only problem is if the other party tries to call and if I accept the call the call does not get connected... Instead it says "call in progress". Or else everything is fine...

But not so in Ubuntu... It does not work... The final output of the ./configure command always gives

Build with voice and video..... :No

I tried to install all the dependencies given by the pidgin team... Now all I get is volume problem... The system says I do not have sound card... I probably have to instal gstreamer libraries... This is disgusting....

I have Fedora 11 also installed in my system and I am happy using that... I was happy with Ubuntu... But now I sadly have to tell that it sucks... :(

---

### Post by DigitalDuality on 2009-08-21
> **coldReactive said:**
> Problem: Don't like terminal much.
1. Then why use linux?
2. After install and setup, you can use the terminal as much or as little as you want.

> **coldReactive said:**
> Problem: Any guides on how to get DVD Playback and are there any flashplugin-nonfree like on Ubuntu? I don't like gnash nor swfdec.
Installing restricted stuff in arch is just as simple as it is in Ubunt.

> **coldReactive said:**
> Problem: I absolutely HATE make/install.

Arch's repo's (official and the AUR community) are almost as vast as Ubuntu's.  No need to make install.

---

### Post by kagashe on 2009-08-22
> **sikku said:**
> Has anyone installed it in Jaunty by compiling from source???
Go to [this thread]("http://ubuntuforums.org/showthread.php?t=1244589"), follow korin43's post for compiling. I have used his compiled binary from PPA and voice and video is enabled and working.

kagashe

---

### Post by kevdog on 2009-08-22
Was the video portion working??  - The last time I checked out the mtn vv version - only audio was working -- however this was back in like April or something.

---

### Post by sikku on 2009-08-22
> **kagashe said:**
> Go to [this thread]("http://ubuntuforums.org/showthread.php?t=1244589"), follow korin43's post for compiling. I have used his compiled binary from PPA and voice and video is enabled and working.

kagashe

Thanx for guiding me.... :)

---

### Post by chandru155 on 2009-08-22
Thanks. With that un install command, i successfully un installed my older version and installed the latest version. Thaks

---

### Post by andersja on 2009-08-26
> **sikku said:**
> I think nobody has compiled on jaunty...

We should try to get this onto jaunty-backports and into the karmic repository ASAP?

[http://packages.ubuntu.com/en/source/karmic/pidgin](http://packages.ubuntu.com/en/source/karmic/pidgin) - still showing 2.5.8?

Does anyone know when to expect this?

---

### Post by coldReactive on 2009-08-26
--- Delete Post ---

---

### Post by alexcckll on 2009-08-27
> **danielrmt said:**
> Karmic, aka 9.10
So probably when I buy my next laptop from Linux Emporium late next year then?

---

### Post by coldReactive on 2009-08-27
> **alexcckll said:**
> So probably when I buy my next laptop from Linux Emporium late next year then?

Late next year? You'd be using 10.04 or 10.10 then.

---

### Post by alexcckll on 2009-08-27
> **coldReactive said:**
> Late next year? You'd be using 10.04 or 10.10 then.
Probably so.. I'm one of your basic LTS-to-LTS, only-upgrade-between-OS-versions-with-help-from-my-vendor customers..

Sorry - the machine is a lifeline..

Please remind me - I get full support on 8.04LTS until  late in 2011, don't I?

---

### Post by 4th guy on 2009-08-27
April 2011
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Release_history](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Release_history)

---

### Post by Ric_NYC on 2009-08-27
Pidgin has a strange integration with the taskbar. It changes the shutdown button. 

Is there a way to turn it off?

---

### Post by coldReactive on 2009-08-27
> **Ric_NYC said:**
> Pidgin has a strange integration with the taskbar. It changes the shutdown button. 

Is there a way to turn it off?

Go into plugins and disable nautilus integration. See if that works.

---

### Post by kevdog on 2009-08-27
If you can compile -- then you can get any version with pidgin voice and video support.  Don't be so helpless!

---

### Post by coldReactive on 2009-08-27
> **kevdog said:**
> If you can compile -- then you can get any version with pidgin voice and video support.  Don't be so helpless!

Ubuntu already has 2.6.1 in the PPA. I would think it has the support.

---

### Post by Tibuda on 2009-08-27
> **coldReactive said:**
> Ubuntu already has 2.6.1 in the PPA. I would think it has the support.

Only Jaunty and Karmic. Intrepid and Hardy users need some dirty compiling.

---

### Post by alexcckll on 2009-08-31
> **danielrmt said:**
> Only Jaunty and Karmic. Intrepid and Hardy users need some dirty compiling.
Umm - so is this another case of production users like me just waiting?

Are there plans for full videoconferencing functions to be available in IM clients in the next Long Term Support release of Ubuntu Desktop?

---

### Post by alexcckll on 2009-08-31
> **kevdog said:**
> If you can compile -- then you can get any version with pidgin voice and video support.  Don't be so helpless!
I've never compiled production systems in my life.  Are the requested enhancements on Canonical's maintenance list?

---

### Post by alexcckll on 2009-09-16
I say again - Are the requested enhancements on Canonical's maintenance list?

---

### Post by coldReactive on 2009-09-16
> **alexcckll said:**
> I say again - Are the requested enhancements on Canonical's maintenance list?

2.6.1 is in Karmic Publishing, so it will be included in the repos for Karmic.

---

### Post by alexcckll on 2009-09-18
> **coldReactive said:**
> 2.6.1 is in Karmic Publishing, so it will be included in the repos for Karmic.
Umm... so does that mean that full videoconferencing for all IM protocols will be fully supported out of the box in 9.10?  And I trust that condition would continue so that when the next Long Term Support release was available... they would be fully supported?

So - I could buy a new laptop and have it all running out of the box?

---

### Post by coldReactive on 2009-09-18
> **alexcckll said:**
> Umm... so does that mean that full videoconferencing ***_for all IM protocols_*** will be fully supported out of the box in 9.10?  And I trust that condition would continue so that when the next Long Term Support release was available... they would be fully supported?

So - ***_I could buy a new laptop and have it all running out of the box_***?

No and No.

Most computers are geared to windows, if **_*everything*_** works out of the box, you must be lucky.

---

### Post by alexcckll on 2009-09-18
> **coldReactive said:**
> No and No.

Most computers are geared to windows, if **_*everything*_** works out of the box, you must be lucky.
Hmm -funny that.  I bought this Thinkpad R61i from Linux EMporium.. and Ubuntu 8.04LTS was running happily out of the box.  All I had to do was follow the instructions to get the restricted stuff on it.. 

I would be going back there for future machines.

I admit - I am using a preinstalled instance of Ubuntu 8.04.3.

---

### Post by Tibuda on 2009-09-18
Yeah, buying Linux preinstalled is the best way to give manufacturers incentive to support Linux. I have also bought it preinstalled in my laptop and everything worked out of the box in all the clean installs I made (hardy, intrepid, jaunty and karmic). Wireless, webcam, sound, everything...

---

### Post by coldReactive on 2009-09-18
> **danielrmt said:**
> Yeah, buying Linux preinstalled is the best way to give manufacturers incentive to support Linux. I have also bought it preinstalled in my laptop and everything worked out of the box in all the clean installs I made (hardy, intrepid, jaunty and karmic). Wireless, webcam, sound, everything...

Dell uses hacks to make sure their hardware works though. So if you reinstall on some machines, you might run into some problems.

---

### Post by toupeiro on 2009-09-18
> **coldReactive said:**
> Dell uses hacks to make sure their hardware works though. So if you reinstall on some machines, you might run into some problems.

They also provide an Emergency recovery partition.

---

### Post by alexcckll on 2009-09-19
From what I gather, Dell run their own repositories, so any new software changes that come in go through an even stronger testing process before being released to the more mainstream user community.

While I might be interested in playing with different software on a non-lifeline machine.. I must admit that I'd be squeamish over stepping outside the standard repositories... 

As they commented.. the average mainstream user *doesn't care* that they're not running the latest; they just want the kit to work.

---

