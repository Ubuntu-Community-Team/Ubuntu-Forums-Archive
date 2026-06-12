---
title: "Can we improve software installation for those without broadband?"
date: 2007-03-04
forum: The Cafe
---

### Post by laxmanb on 2007-03-04
Software installation with linux stinks,if you don't have a broadband connection!! If anybody has tried installing even the simplest piece of software from packages should know, it is a pain... why can't linux offer simpler installation options for software??  the FOSS guys have improvided on nearly everything else... 

For windows, you can always use CDs that come with magazines, with linux, this is a huge pain, even the simplest package has dependencies, and then they have dependencies... I find it just horrible, InstallShield/Windows Installer are both easier/better methods of installing software...

---

### Post by aysiu on 2007-03-04
Well, I think you're overgeneralizing. It's not software installation in *Linux* that stinks without a broadband connection. It's software installation in *Ubuntu* that stinks without a broadband connection. Ubuntu is only one CD (possibly one DVD, if you order it from Amazon.com or if you have the kind of connection to download a 4 GB file.. and also a DVD burner... but if you had the latter two things, then you wouldn't really need it, would you).

Some other distros have more than one CD, though, and those extra CDs are full of software--Fedora, Debian, and Mandriva come to mind, but I'm sure there are others.

I do think it'd be great if someone (not me, since my webhost's bandwidth allocation is rather conservative), hosted a site that had popular Ubuntu packages bundled with the necessary dependencies (the ones that are not already included in a default Ubuntu installation)--a site specifically targeted at Ubuntu users without an internet connection.

I'd also love to see Ubuntu Plus updated for Edgy Eft, but I commend those who put it together for getting Dapper Drake and Breezy Badger up and running:
[https://ubuntuplus.bountysource.com/](https://ubuntuplus.bountysource.com/)

P.S. I've retitled your thread to more descriptively reflect the content. "my problem with linux..." is a bit vague and gives forum members no idea what your thread is about.

---

### Post by koenn on 2007-03-04
There are linux distributions that offer DVD's and CD-sets full of software so you don't need to install from the internet. 
Other distributions, such as Ubuntu, have a complete system 'for an average user' on 1 CD and offer the rest from online repositories which, indeed, work faster if you have broadband. 

I suggest you buy yourself a Suse or Redhat CD set.

---

### Post by aysiu on 2007-03-04
> **koenn said:**
> There are linux distributions that offer DVD's and CD-sets full of software so you don't need to install from the internet.  For the record, [Ubuntu has a DVD you can buy on Amazon](http://www.amazon.com/Ubuntu-6-10-PC-Edition/dp/B000K2P4WW/ref=pd_bbs_sr_3/103-5357499-6829412?ie=UTF8&s=software&qid=1173025498&sr=8-3), but... it includes the entire Main and Restricted repositories. I don't believe it contains Universe or Multiverse.

If those last two sentences don't mean anything to you, read this:
[http://www.ubuntu.com/ubuntu/components](http://www.ubuntu.com/ubuntu/components)

---

### Post by koenn on 2007-03-04
> **aysiu said:**
> I do think it'd be great if someone hosted a site that had popular Ubuntu packages bundled with the necessary dependencies (the ones that are not already included in a default Ubuntu installation)--a site specifically targeted at Ubuntu users without an internet connection.


I don't quite understand what you mean here. What's the difference with the regular repo's ? You install whatever package you want, and dependencies are only added if they're needed - i.e. if they're not installed already.

---

### Post by PriceChild on 2007-03-04
You may like the idea of a handy tool called "aptoncd" which will be appearing in feisty for the first time.

To cut a long story short, it will allow the user to create repositories on disks including all currently installed packages, entire sections in synaptic, entire repos (e.g. multiverse) etc. etc.

I think this is going to be really good for those of you with friends on broadband.... just stick in a Live cd, install aptoncd and burn the universe from a friends pc then take it back home!

---

### Post by aysiu on 2007-03-04
> **koenn said:**
> I don't quite understand what you mean here. What's the difference with the regular repo's ? You install whatever package you want, and dependencies are only added if they're needed - i.e. if they're not installed already.
The difference is that someone who knows someone else with broadband (a neighbor, a relative), has broadband available on Windows and not Ubuntu (say, if wireless works on the Windows partition but not on the Ubuntu one), or is able to do personal downloads legally at work over broadband, can download the bundle and then do a quick ```
sudo dpkg -i *.deb
``` once the bundle is transferred to the Ubuntu computer and untarred.

---

### Post by Omnios on 2007-03-04
Hi my dad manages Dapper updates on dial up by launching it when he goes to bed and letting it run all night. He manages some really big updates over nite and is finding doing this more managable. Only other thing I could suggest is better compression of the packages which may help.


 ANother possiblity would be to have non official add on cds sort of like automatix on a cd but not shure how that would work.

 ALso I downloaded and made the CD's for my dad for the install and another possiblity could be to see if you can downlaod it as a internet caffee

---

### Post by aysiu on 2007-03-04
> **Omnios said:**
> Hi my dad manages Dapper updates on dial up by launching it when he goes to bed and letting it run all night. He manages some really big updates over nite and is finding doing this more managable. That brings up a good point--there are two things at issue here--dial-up (or any kind of slow connection) and *no* internet connection. There's a big difference. For dial-up, software installation is a small inconvenience, and your dad found a good way to deal with that inconvenience. For those without internet connections, it's a **big** inconvenience... or a no-go altogether.

> ANother possiblity would be to have non official add on cds sort of like automatix on a cd but not shure how that would work. Such a CD, as I mentioned before, exists for Dapper and Breezy but not yet for Edgy.

---

### Post by laxmanb on 2007-03-04
Yeah, but it's not ubuntu but linux in general... I had FC5 for a while... the DVD had a lot of applications, a lot of which were really useful... but installing something that's not on the DVD was a pain...

examples
 a. Sun's Java 6: Java 5 is somewhere in the repositories but Java 6 is hard to find... and  if you decide to do an offline installation, there's a lot of configuration that needs to be done... The windows installer comes as a simple point and click executable... it does everything for you. In ubuntu, it's a self extracting archive... you extract it, you move it to /usr/lib/jvm/, you have to configure update-alternatives... really, how do you expect newbies to the command line to do all this...

b. MP3 support: I tried an offline install of gstreamer-ugly... first you download the .deb package, then you find all it's dependencies: lib-a52, id3tag, 9-10 other packages, then you have to install the dozen dependencies, then it's done...

to sum up: how can you call yourself "for human beings" ... lotsa people have to depend on offline installations... if it's this hard, people will either call linux too hard or themselves too stupid...

---

### Post by aysiu on 2007-03-04
> **laxmanb said:**
> 
b. MP3 support: I tried an offline install of gstreamer-ugly... first you download the .deb package, then you find all it's dependencies: lib-a52, id3tag, 9-10 other packages, then you have to install the dozen dependencies, then it's done... This is why I threw out the idea of a site hosting full bundled packages--including dependencies. There's no reason Ubuntu has to be involved in that (it has nothing to do with the Ubuntu software and everything to do with someone bundling the dependencies and hosting them on a server somewhere--this'd be a great community project).

> how can you call yourself "for human beings" ... lotsa people have to depend on offline installations... if it's this hard, people will either call linux too hard or themselves too stupid... "For human beings" is a marketing slogan indicating that its development is focused on ease of use, not that it can adapt to every conceivable situation out there. Hell, a lot of people don't even have computers, let alone an internet connection.

The focus of Ubuntu cannot be on what's on its way out but on what's on its way up. Dial-up is on its way out. No connection is on its way out. Sure, there will probably always be some people who are on dial-up or no connection, but the numbers grow fewer and fewer each day. Probably the next step for people in remote or rural areas is to go to some kind of satellite internet connection, since broadband ethernet probably won't make it out there.

That said, I think this is a valid issue, and maybe we can ask the developers to address it in the release after Feisty Fawn. Feisty's focus seems to be on building solid usability--particularly I'm thinking of bullet-proof-x, network browsing, and easy codec installation, among [other specifications for the April release](https://blueprints.launchpad.net/ubuntu/feisty/+specs).

Maybe the community can help steer Feisty+1 in the direction of accessibility--even more language support, better off-line or dial-up support (particularly for software installation), etc.

---

### Post by jackrobinson on 2007-03-04
> **aysiu said:**
> 
 Such a CD, as I mentioned before, exists for Dapper and Breezy but not yet for Edgy.
Aysiu sorry about making repeated corrections to your automatix related statements (I don't want to make this a habit).. 
There is no CD version of automatix for Dapper (or Edgy as you pointed out). There is one CD version based on a **VERY OLD** version of automatix(1) for Breezy and after confirming with the Automatix Team,  it **does not come with support of any shape or form** from the Automatix Team. In any case even Automatix Main does not support Breezy any longer.

---

### Post by aysiu on 2007-03-04
> **jackrobinson said:**
> Aysiu sorry about making repeated corrections to your automatix related statements (I don't want to make this a habit).. 
There is no CD version of automatix for Dapper (or Edgy as you pointed out). There is one CD version based on a **VERY OLD** version of automatix(1) for Breezy and after confirming with the Automatix Team,  it **does not come with support of any shape or form** from the Automatix Team. In any case even Automatix Main does not support Breezy any longer.
I'm actually not talking about Automatix (though I was responding to someone who was referring to the Automatix CD). I was talking about Ubuntu Plus.
[https://ubuntuplus.bountysource.com/](https://ubuntuplus.bountysource.com/)

---

### Post by jackrobinson on 2007-03-04
> **aysiu said:**
> I'm actually not talking about Automatix (though I was responding to someone who was referring to the Automatix CD). I was talking about Ubuntu Plus.
[https://ubuntuplus.bountysource.com/](https://ubuntuplus.bountysource.com/)
aah alright.. thanks for the clarification and the link. This surely looks interesting.

---

### Post by aysiu on 2007-03-04
> **jackrobinson said:**
> This surely looks interesting. It's wonderful, actually... just not updated for Edgy.

---

### Post by frodon on 2007-03-06
I always wondered why no-one took the initiative to make a live CD of edgy with all the codecs, java, flash installed and containing the drivers for nvidia and ATI.
It is really easy to do with reconstructor :
[http://reconstructor.aperantis.com/index.php?option=com_content&task=view&id=14&Itemid=37](http://reconstructor.aperantis.com/index.php?option=com_content&task=view&id=14&Itemid=37)

@aysiu, yes this idea is great and the same CD can be done in several hours using apt-on-cd, the only thing needed is a host to spread this CD :
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

I believe both tools are available in the repositories, so all can change if you want, this only need arms to become real ;)

---

### Post by PriceChild on 2007-03-06
@frodon: Linux Mint?

---

### Post by frodon on 2007-03-06
Linux Mint represent the kind of project i'm talking about however linux Mint has some weird limitation that i don't really understand :
> Installation Notes: 
- the more people download the ISO file the slower the download speeds are. The more people download the torrent, the faster their download speeds become.
- always check the MD5 before burning the ISO. If you keep getting the wrong MD5 from one of our mirrors, please tell us on the forums.
- mintDisk only works on installed system, not from the liveCD (this is due to a problem in the installer)
- do not install anything and keep your session in English if you're planning to install. You can always change the language once the system is installed (this is due to a problem in the installer).
- if you want to avoid warning messages on upgrades add the following line to your /etc/apt/apt.conf (or create the file if inexistant): APT::Get::AllowUnauthenticated 1 ;
For me the perfect solution would be to release for each version of ubuntu a CD containning all the ubuntu repositories for those without internet connections and also leave a document on the desktop after a fresh install which would contain these informations :
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Thanks to this document left on the desktop we would not need anymore automated scripts and users wouldn't be lost anymore trying ubuntu for the first time.
I don't know if this is on a spec somewhere but it surely need to be concidered as positive improvement.

---

### Post by aysiu on 2007-03-06
What about [Ubuntu Ultimate Edition](http://ubuntusoftware.info/ultimate/#1.2)?

---

### Post by watson540 on 2007-03-07
> For me the perfect solution would be to release for each version of ubuntu a CD containning all the ubuntu repositories for those without internet connections and also leave a document on the desktop after a fresh install which would contain these informations :
[https://help](https://help).

I agree, however.. It would definitely be more than just A cd :). I like the idea of having them roled into 1 maybe two dual layer dvd's. heh. 

Ultimate edition is a great choice for the internet impaired. Even betterif you know someone with broadband so you could roll your own for exactly what you need.

Also, i saw some repo dvd's floating on linuxtracker.org the other day. Sure would love to have them EDIT: On that note, im very surprised someone hasnt popped up on ebay selling repo's :)

---

### Post by aysiu on 2007-03-08
Amazon.com sells Ubuntu DVDs that contain the entire Main and Restricted repositories.

Unfortunately, a lot of what people want is in the Universe and Multiverse repositories, so that's no solution.

---

### Post by mdsmith on 2007-03-08
I haven't tried Amazon for cds or dvds, have always getten mine from Linux Central. Dvds run about  usd 15 with shipping. Installation isn't a problem. Software doesn't  take much time with Synaptic unless you want something like the KDE desktop for Ubuntu. Updates are the real problem unless you can get on top of them real quick. I just scroll down the list of updates and pick out a reasonable amount (I am usually getting about 30k speed) and do it in groups.  Don

---

