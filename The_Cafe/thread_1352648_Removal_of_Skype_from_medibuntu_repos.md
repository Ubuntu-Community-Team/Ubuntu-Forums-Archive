---
title: "Removal of Skype from medibuntu repos"
date: 2009-12-11
forum: The Cafe
---

### Post by Linuxforall on 2009-12-11
As of yesterday Ubuntu devs have decided to remove Skype from mediuntu repos affecting all the variants of Ubuntu from Hardy to Lucid. They cite some compatibility issue with skype-common in Ubuntu and Skype offered by the company. They are now referring people to directly download Skype from the Skype site rather than depend on Medibuntu.

Sad part is that the Skype in medibuntu has worked flawlessly for me with regards to webcam since Hardy. The version thats provided at the Skype site refuses to recognize the webcam even when the LD_Preload command is issued. All you get is green lines. Its quite unfortunate as some of us depend on Skype to stay in touch with our relatives and loved ones abroad. Since no other video or audio video client works as good as Skype and Gyachi is still not out for x64 Karmic, its indeed a very tough situation for those that need Skype. Wish Ubuntu hadn't withdrawn it at this stage but rather with the release of new distro when they could ascertain that there indeed exist a version of Skype thats fully functional as the one included in the medibuntu repos.

As a matter of fact, of all the distros, only Ubuntu's Skype worked fine right out of the box as regards to working with webcams, rest of them all had their issues and needed workarounds which sometimes proved flaky in the long run.

Sorry for my rant and I know Skype is not the end of the world for some and neither is the lack of audio video messaging but for many, with long distance phone calls being expensive, audio and video messaging is the only way to stay in touch.

---

### Post by Physical Hook on 2009-12-11
I thought they had the same version as if you would download it from the official Skype website :-k

---

### Post by Linuxforall on 2009-12-11
> **Physical Hook said:**
> I thought they had the same version as if you would download it from the official Skype website :-k

Unfortunately, the one on Skype site has the same version but due to the way its compiled, it refuses to work with the webcam on x64 Karmic.

---

### Post by Physical Hook on 2009-12-11
> **Linuxforall said:**
> Unfortunately, the one on Skype site has the same version but **due to the way its compiled**, it refuses to work with the webcam on x64 Karmic.

Skype isn't open source so no one besides Skype can compile it. Am I wrong ? 
In fact, there are several versions of Skype available ( 8.04, 8.10+, etc. ) - have you tried all of them ?

---

### Post by Linuxforall on 2009-12-11
I tried the version listed for 8.10+ for x64. The skype-common file used in Medibuntu varied from the one used by Skype and thats why it was pulled from the repo.

---

### Post by zipperback on 2009-12-11
> **Physical Hook said:**
> Skype isn't open source so no one besides Skype can compile it. Am I wrong ? 

It's closed source. And there are numerous open source alternatives for it. I don't really understand why someone would want to lock themselves into using a close source application when there are some really good open source alternatives available.

- zipperback
:popcorn:

---

### Post by Physical Hook on 2009-12-11
> **zipperback said:**
> It's closed source. And there are numerous open source alternatives for it. I don't really understand why someone would want to lock themselves into using a close source application when there are some really good open source alternatives available.

- zipperback
:popcorn:

Because all of my friends use Skype instead of MSN or Yahoo ( just an example )  ? :)

---

### Post by Linuxforall on 2009-12-11
> **zipperback said:**
> It's closed source. And there are numerous open source alternatives for it. I don't really understand why someone would want to lock themselves into using a close source application when there are some really good open source alternatives available.

- zipperback
:popcorn:

If you can give me even one that does audio and video without requiring calisthenics to make it run, I am all for it. Till date there isn't any in open source world that does video and that too with the quality of Skype. Most of them do audio and even then, to bring in other non Linux users into the fold is quite difficult.

---

### Post by FuturePilot on 2009-12-11
Is there a link to the discussion on the reasons for removal?

---

### Post by Regenweald on 2009-12-11
> **zipperback said:**
> It's closed source. And there are numerous open source alternatives for it. I don't really understand why someone would want to lock themselves into using a close source application when there are some really good open source alternatives available.

- zipperback
:popcorn:

I'd like to hear more about these wonderful FOSS alternatives please..

---

### Post by Linuxforall on 2009-12-11
> **FuturePilot said:**
> Is there a link to the discussion on the reasons for removal?

[https://launchpad.net/medibuntu/+announcement/4539](https://launchpad.net/medibuntu/+announcement/4539)

---

### Post by Queue29 on 2009-12-11
> **Regenweald said:**
> I'd like to hear more about these wonderful FOSS alternatives please..

Same here. Not even the stupid Cheese app works with my webcam. Skype on the other hand does video calls just fine. Yet another step in the wrong direction.

---

### Post by Linuxforall on 2009-12-11
The saddest part is that I convert many ex Windows users here to Linux, specifically Ubuntu and lots of them are old folks who have family abroad so they desperately need Skype. With removal of a perfectly functioning Skype without even asking its users, Ubuntu devs yet again show their high handedness here. The Skype package offered at Skype site just doesn't work with webcams and if one has to go through contortions to make it work, whats the point of installing it on a first time Ubuntu user.

---

### Post by SLEEPER_V on 2009-12-12
that sucks.  I just got my inlaws a webcam so they can watch my 2 yr old open christmas presents.

---

### Post by kostkon on 2009-12-12
> **Linuxforall said:**
> The Skype package offered at Skype site just doesn't work with webcams and if one has to go through contortions to make it work, whats the point of installing it on a first time Ubuntu user.
Strange, because mine works OTB with the version from Skype's website.

---

### Post by Linuxforall on 2009-12-12
> **SLEEPER_V said:**
> that sucks.  I just got my inlaws a webcam so they can watch my 2 yr old open christmas presents.

I can well relate to that, I use Skype daily to talk to my nine year old nephew in Germany, its nice to see him daily which would otherwise not be possible without Skype.

---

### Post by Linuxforall on 2009-12-12
> **kostkon said:**
> Strange, because mine works OTB with the version from Skype's website.

What cam? Here I have Microdia which has the driver in the kernel itself. The cam works fine in Cheese but all I get is green lines in Skype.

---

### Post by kostkon on 2009-12-12
Also, I think the OP read the announcement wrongly and didn't check the bug report where it clearly says that the same static packages that are now being provided by medibuntu will be made available by Skype on their site in a few days time.
> After some discussion on irc with a skype dev, I think the best proposition is to stop distributing them, as they are apparently going to provide i386 & amd64 & skype-static packages on skype.com.

---

### Post by kostkon on 2009-12-12
> **Linuxforall said:**
> What cam? Here I have Microdia which has the driver in the kernel itself. The cam works fine in Cheese but all I get is green lines in Skype.
Logitech QuickCam Express Plus. Works OTB everywhere.

---

### Post by Linuxforall on 2009-12-12
> **kostkon said:**
> Also, I think the OP read the announcement wrongly and didn't check the bug report where it clearly says that the same static packages that are now being provided by medibuntu will be made available by Skype on their site in a few days time.

Yep lets hope its sooner than later, so far the packages there have multiple issues if you check the Skype forums, webcam being a primary one.

You are lucky that your cam works without any glitches, all I get here is the dreaded green stripes whereas in Cheese it works fine, with the medibuntu skype package, I had absolutely zero issues, cam or sound.

---

### Post by FuturePilot on 2009-12-12
> **kostkon said:**
> Also, I think the OP read the announcement wrongly and didn't check the bug report where it clearly says that the same static packages that are now being provided by medibuntu will be made available by Skype on their site in a few days time.

No, it's definitely completely gone. Not listed here anymore [http://packages.medibuntu.org/karmic/index.html]("http://packages.medibuntu.org/karmic/index.html")

---

### Post by SunnyRabbiera on 2009-12-12
Heres hoping the official package will work now, if it doesnt then I guess someone can demand the package back.
File a million complaints, its the only way to get things done.

---

### Post by Linuxforall on 2009-12-12
I just wish that the official functional medibuntu package was not removed abruptly till Skype had something that worked on offer.

---

### Post by SunnyRabbiera on 2009-12-12
> **Linuxforall said:**
> I just wish that the official functional medibuntu package was not removed abruptly till Skype had something that worked on offer.

Indeed, well if the new version that is said to be released screws up I say complain, bug report, shove it down their throats until functionality is restored.
The app might be closed source, but come on this is nonsense.

---

### Post by Linuxforall on 2009-12-12
[http://forum.skype.com/index.php?showtopic=411441](http://forum.skype.com/index.php?showtopic=411441)

Goes to show the severity of the webcam issue with new Skype, none of the solutions listed have so far worked out in my case.

---

### Post by Kimm on 2009-12-12
> **Linuxforall said:**
> Unfortunately, the one on Skype site has the same version but due to the way its compiled, it refuses to work with the webcam on x64 Karmic.

Oh? I'm running the latest [Skype beta]("http://www.skype.com/intl/sv/download/skype/linux/choose/") in Karmic x64. It works great with my webcam...

---

### Post by Linuxforall on 2009-12-12
> **Kimm said:**
> Oh? I'm running the latest [Skype beta]("http://www.skype.com/intl/sv/download/skype/linux/choose/") in Karmic x64. It works great with my webcam...

You are lucky, out here sound works fine, video is all but green color.

---

### Post by Icehuck on 2009-12-12
> **Kimm said:**
> Oh? I'm running the latest [Skype beta]("http://www.skype.com/intl/sv/download/skype/linux/choose/") in Karmic x64. It works great with my webcam...

And this helps the OP how?

---

### Post by SunnyRabbiera on 2009-12-12
> **Icehuck said:**
> And this helps the OP how?

Indeed, like I said though wait it out and if the new release doesnt work file complaints at medibuntu to give the package back.

---

### Post by Linuxforall on 2009-12-12
> **SunnyRabbiera said:**
> Indeed, like I said though wait it out and if the new release doesnt work file complaints at medibuntu to give the package back.

Actually I have saved it, so in case anyone has issues with the latest from Skype, I will upload it for them.

For fellow Opera users, I will share it via Opera Unite ;)

---

### Post by SunnyRabbiera on 2009-12-12
> **Linuxforall said:**
> Actually I have saved it, so in case anyone has issues with the latest from Skype, I will upload it for them.

For fellow Opera users, I will share it via Opera Unite ;)

well thats nice of you, and shove it in the face of medibuntu when/if the official release fails.

---

### Post by Linuxforall on 2009-12-12
This was a hasty decision on Ubuntu's part. They could have waited till release of Lucid instead of taking it out mid way. Maybe the devs think that Video chat is not used by most Ubuntu users but they are truly wrong if they think in those terms.

---

### Post by Icehuck on 2009-12-12
> **Linuxforall said:**
> This was a hasty decision on Ubuntu's part. They could have waited till release of Lucid instead of taking it out mid way. Maybe the devs think that Video chat is not used by most Ubuntu users but they are truly wrong if they think in those terms.

I'm gonna go with it's just another way to push empathy and that whole telepathy thing.

Conspiracy theory ftw!

---

### Post by adeypoop on 2009-12-12
I believe the version in medibuntu was an older version than the one available from Skype's website not compiled differently or anything like that.  I'm surprised so many seem to find the older version works better for them I've gone with the newer version of skype myself and had good success with it after a bit of fiddling around. 

Here is what i had to do on my Dell PC in case this helps anyone, first of all my usb webcam must be plugged into the usb port on the pc itself (ie not a usb hub on the monitor), also i have to run the following command to start skype

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

no idea what it does, but it works for me. Hope that helps some of you having problems

---

### Post by Linuxforall on 2009-12-12
> **Icehuck said:**
> I'm gonna go with it's just another way to push empathy and that whole telepathy thing.

Conspiracy theory ftw!

Good point, however Empathy in Ubuntu only supports audio/video in Gtalk and no other protocols. The video support is flaky and unlike Skype's P2P tech establishing incoming connection to improve video quality, there is nothing similar in Empathy yet. Also the Empathy in Fedora 12 showed cam icon for MSN and Yahoo accounts along with Google, that indicates it has cam support for the other protocols as well, too bad didnt get a chance to try it out thoroughly but google quality was nothing to write about.

---

### Post by alexcckll on 2009-12-12
Umm - is one of the main reasons that Skype is closed-source?  Maybe Canonical could talk with Skype's owners about offering it via the Partner repository?

That way - they do the same as with Adobe... and everyone's happy.

---

### Post by phrostbyte on 2009-12-12
Did it ever occur to you that perhaps Skype doesn't want Ubuntu distributing it's software?

Also Medibuntu is not affiliated with the Ubuntu project. 

The "official" way to get closed source into the Ubuntu distro is via the "partner" repository which is built into Ubuntu. But only with Skype's permission is this possible.

---

### Post by Linuxforall on 2009-12-12
> **adeypoop said:**
> I believe the version in medibuntu was an older version than the one available from Skype's website not compiled differently or anything like that.  I'm surprised so many seem to find the older version works better for them I've gone with the newer version of skype myself and had good success with it after a bit of fiddling around. 

Here is what i had to do on my Dell PC in case this helps anyone, first of all my usb webcam must be plugged into the usb port on the pc itself (ie not a usb hub on the monitor), also i have to run the following command to start skype

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

no idea what it does, but it works for me. Hope that helps some of you having problems

Yes the one in medibuntu is older by .1 the trick you describe doesn't work here I am afraid.

---

### Post by Keyper7 on 2009-12-12
Something is strange here. Skype is a binary blob and the only difference between the medibuntu version and the official version is the packaging, as far as I know. The medibuntu maintainers cannot recompile or anything, simply get the files from the official site and repackage. Why would one version work and the other don't?

---

### Post by SunnyRabbiera on 2009-12-12
well for those interested the .debs are still here:
[http://packages.medibuntu.org/pool/non-free/s/skype/](http://packages.medibuntu.org/pool/non-free/s/skype/)

back em up while you can.

> **Keyper7 said:**
> Something is strange here. Skype is a binary blob and the only difference between the medibuntu version and the official version is the packaging, as far as I know. The medibuntu maintainers cannot recompile or anything, simply get the files from the official site and repackage. Why would one version work and the other don't?

backhacking I suspect

---

### Post by Linuxforall on 2009-12-12
> **Keyper7 said:**
> Something is strange here. Skype is a binary blob and the only difference between the medibuntu version and the official version is the packaging, as far as I know. The medibuntu maintainers cannot recompile or anything, simply get the files from the official site and repackage. Why would one version work and the other don't?

I have been thinking about that aspect as well, somehow from the very beginning the medibuntu version has been issue less whereas the one from Skype has never functioned with the webcam. I tried it from Intrepid stage where it refused to work cam and sound and now in Jaunty, all I get is green stripes with the cam.

---

### Post by marin123 on 2009-12-13
> **SunnyRabbiera said:**
> well for those interested the .debs are still here:
[http://packages.medibuntu.org/pool/non-free/s/skype/](http://packages.medibuntu.org/pool/non-free/s/skype/)

back em up while you can.



backhacking I suspect

too bad this forum doesnt have THANK YOU! button... i've been messing around with skype whole day (and i should be studying :P ), this finally made it to work :)

---

### Post by Mr. Picklesworth on 2009-12-13
Hey, Linuxforall, the first line of your original post ("As of yesterday Ubuntu devs have decided to remove Skype from mediuntu repos affecting all the variants of Ubuntu from Hardy to Lucid.") is really misleading. While anyone can be an Ubuntu developer, it sounds like you are suggesting Medibuntu is an official part of Ubuntu. It is not :)

---

### Post by Linuxforall on 2009-12-13
> **marin123 said:**
> too bad this forum doesnt have THANK YOU! button... i've been messing around with skype whole day (and i should be studying :P ), this finally made it to work :)

This clearly proves that the version at Skype doesn't work and taking off Skype from Medibuntu was a really premature decision on part of the maintainer.

---

### Post by Linuxforall on 2009-12-13
> **Mr. Picklesworth said:**
> Hey, Linuxforall, the first line of your original post ("As of yesterday Ubuntu devs have decided to remove Skype from mediuntu repos affecting all the variants of Ubuntu from Hardy to Lucid.") is really misleading. While anyone can be an Ubuntu developer, it sounds like you are suggesting Medibuntu is an official part of Ubuntu. It is not :)

While its not official, the links are there in FF that comes with Ubuntu and for all the essential needs, its recommended to put the medibuntu repos. It may not be official but it makes Ubuntu run for many of us.

---

### Post by Wiebelhaus on 2009-12-13
*posted in wrong thread*

---

### Post by Linuxforall on 2009-12-13
By taking out a perfectly working package and leaving the users with no choice but to download a non-functional package.

---

### Post by MaindotC on 2009-12-13
> **Mr. Picklesworth said:**
> While anyone can be an Ubuntu developer, it sounds like you are suggesting Medibuntu is an official part of Ubuntu. It is not :)

Damn you Picklesworth!!

---

### Post by Pyux on 2009-12-13
Skype Official Repo

Copy paste into /etc/apt/sources.list and run the Key command in terminal. Sucks that its out of Medibuntu but theres still a repo for us.

#### Skype - [http://www.skype.com](http://www.skype.com)
## For Key run this command: gpg --keyserver pgp.mit.edu --recv-keys 0xd66b746e && gpg --export --armor 0xd66b746e  | sudo apt-key add -
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

---

### Post by Linuxforall on 2009-12-13
Pyux,

Many thanks, is this the same version that comes in Medibuntu?

---

### Post by Pyux on 2009-12-13
Never used MediBuntu version, no idea what version it is. But this one is up to date and works.

---

### Post by skipknyc on 2009-12-13
> **SunnyRabbiera said:**
> well for those interested the .debs are still here:
[http://packages.medibuntu.org/pool/non-free/s/skype/](http://packages.medibuntu.org/pool/non-free/s/skype/)

back em up while you can.



backhacking I suspect

Hi there!

This is wonderful! Which one of these should I install?

Thanks!

---

### Post by marin123 on 2009-12-13
> **skipknyc said:**
> Hi there!

This is wonderful! Which one of these should I install?

Thanks!

skype common medibuntu 2 and skype 2.0.1.47 (amd64 or i386 - depends on your architecture)
this works beautiful on my 64-bit karmic... :)

---

### Post by Linuxforall on 2009-12-13
> **Pyux said:**
> Never used MediBuntu version, no idea what version it is. But this one is up to date and works.

This version is the same one that Skype gives out at their site and sadly has the same issue with webcam.

---

### Post by fragos on 2010-02-06
Ubuntu Tweak has a repository for Skype that worked for me. Only problem was that although removing Skype from Medibuntu they left reference to it in the repository. I had to temporarily remove the Medibuntu repository to access the Skype one. After installing Skype I disabled it's repository and enabled Medibuntu again.

---

### Post by samantha_ on 2010-02-06
aww comeon... why remove it.
hmm. wait. 
a good idea would be add it to the canonical "partner" repos..
After asking skype of course.

---

### Post by Add3r on 2010-02-14
> **SunnyRabbiera said:**
> well for those interested the .debs are still here:
[http://packages.medibuntu.org/pool/non-free/s/skype/](http://packages.medibuntu.org/pool/non-free/s/skype/)

back em up while you can.

  Thanks Sunnyrabbiera! they work!

Just for the cronicle,
 
I am using Skype with Ubuntu 9.04 on an Asus A8M, and with the inbuilt webcam Z-Star Microelectronics Corp. USB 2.0 (bus ID: ID 0ac8:0321).
I was having the "green screen" or no screen at all problem.
I solved it:
1- doing a remove-purge of my previously installed Skype (the package from the skype website)

2- installing the old Medibuntu skype packages, namely packages
skype-common_2.0.0.68+repack-0medibuntu3_all.deb
skype-static_2.0.0.68+repack-0medibuntu3_i386.deb

3-launching Skype with the command: LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

Now my webcam works with skype.Finally...

---

### Post by grj23 on 2010-05-02
Hi

Just discovered this.  After a year of Ubuntu Skype working fine(ish), I upgraded to Lucid Lynx a couple of weeks ago.  Skype became a bit more flaky, and eventually was regularly opening, and immediately closing down again.

I decided to try to reinstall, thinking that perhaps I just didn't have the latest [medibuntu]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository") and therefore doing the command in the link might work.

Except I wasn't allowed to re-install.  Suspicious, I thought, but oh well.  I uninstalled, and then discovered that I wasn't allowed to install it any more.  Ah - got to start trusting those little nagging doubts :)

So then I went to [the skype website]("http://www.skype.com/download/skype/linux/choose/"), and did it like that bad old days in windoze! :o

But it worked perfectly - video and audio working flawlessly.  So I guess I just keep on with this until it breaks and then try to figure out what the latest way of installing is.  Hopefully it's at least another 6 months or so...

---

### Post by fragos on 2010-05-02
Update Manager can directly work with the source at Skype. Here's the Software Source Preferences.

URI: [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/)
Distribution: stable
Components: non-free

---

### Post by cariboo on 2010-05-02
To see why skype is no longer in the repositories have a look [here]("https://help.ubuntu.com/community/SkypeEthics").

---

### Post by mf205 on 2010-05-02
I have the same problem as others (Logitech cam gives green flickering lines in Skype, though works in cheese).  When I follow others' suggestions using the old medibuntu debs and the LD_PRELOAD command, I get

ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

The file /usr/lib/libv4l/v4l1compat.so does exist.
Can anyone help?  I'm running 64-bit Lucid.

---

### Post by Hotwheelz79 on 2010-05-03
> **fragos said:**
> Update Manager can directly work with the source at Skype. Here's the Software Source Preferences.

URI: [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/)
Distribution: stable
Components: non-free

Hi fragos,

Can u pls confirm what the key one should be using to access the official repo.

Is it still D66B746E

Thanks.

:-)

---

### Post by fragos on 2010-05-03
I looked in Software Sources-> Authentication tab and found 7FAC5991. Note that I used Ubuntu Tweak to add this repository, I highly recommend it.

---

### Post by mf205 on 2010-05-05
I've solved my own problem from #61: the LD_PRELOAD command needs to be preceded by sudo.  This may help others.  But is there any way round this (e.g. changing permissions for something) so that I don't need to enter my password in order to run Skype?

---

