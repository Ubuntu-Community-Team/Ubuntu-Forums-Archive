---
title: "Python-apt templates"
date: 2014-11-09
forum: Ubuntu Development Version
---

### Post by Chanath on 2014-11-09
I was thinking for sometime about the contents of /usr/share/python-apt/templates in many releases of Ubuntu. I can understand having Debian.info in that, but it is hard to understand why Blankon.info and Tanglu.info in it. I actually forgot about this python-apt business, but seeing information on a development release of Tanglu 2.0 Beta 2 in Distrowatch reminded me of this, and I checked the python-apt's templates, and these Blankon.info and Tanglu.info are there in Vivid Ubuntu-Gnome. The question is, is Ubuntu copying from these two distros, or otherwise?

Edit: In Ubuntu, there is no Blankon.info, only Tanglu.info, and that was there in 14.04 too.

Edit2: Copying is quite alright in Linux distros, but carelessness of the devs not to delete these repos is not that good.

Edit3: If you download the Tanglu 2.0 Beta 2 and check the contents of its python-apt/templates, you'd find that it is the same as the Vivid Gnome python-apt/templates.

---

### Post by mc4man on 2014-11-09
> **Chanath said:**
>  The question is, is Ubuntu copying from these two distros, or otherwise?

Edit: In Ubuntu, there is no Blankon.info, only Tanglu.info, and that was there in 14.04 too.

Edit2: Copying is quite alright in Linux distros, but carelessness of the devs not to delete these repos is not that good.
.
Do you have any clue as to what you're talking about?

---

### Post by grahammechanical on 2014-11-09
If the code is open source then anyone is free to "copy" the code and use it so long as the conditions of the open source licence are complied with. Those text files might have a practical purpose for all I know or they may simply be a condition of the license.

Regards.

---

### Post by Chanath on 2014-11-10
> **grahammechanical said:**
> If the code is open source then anyone is free to "copy" the code and use it so long as the conditions of the open source licence are complied with. Those text files might have a practical purpose for all I know or they may simply be a condition of the license.

Regards.

I agree, Graham, only I was thinking a lot about why Ubuntu-Gnome edition was getting into trouble for sometime. The 14.04/14.10 release got troubles in booting up, the 15.04, well in development, is getting late with the latest Gnome DE, while the mothership Debian has it in the repos. I have both Debian and Ubuntu Gnome, so I know the difference. I was unhappy earlier that Debian was late and was happy that Ubuntu was quicker, but now it appears otherwise. That's all, I wanted to say. Regards!

---

### Post by Chanath on 2014-11-10
> **mc4man said:**
> Do you have any clue as to what you're talking about?

Yes, I know what I am talking about. I have remastered a lot of distros and I know how to pull apps from other distros. Take care!

---

### Post by zika on 2014-11-10
> **Chanath said:**
> Yes, I know what I am talking about. I have remastered a lot of distros and I know how to pull apps from other distros. Take care!Great! Would You take some time and explain to us why, how and when these templates are used? Nice opportunity for lot of us to use someone with such experience. Thank You in advance.

---

### Post by Chanath on 2014-11-10
> **zika said:**
> Great! Would You take some time and explain to us why, how and when these templates are used? Nice opportunity for lot of us to use someone with such experience. Thank You in advance.

Remastering is easy, when someone else had written the code, but that also mean that I don't know how to code. All I know is how to read the code in a different way; I simply read it to see how the logic in it works. For example, the Remastersys had stopped developing, but the code stayed back, and reading through it, you can see how to remaster Trusty and/or Utopic distros. I'd try the Vivid too, while it is still in development, but I am not at all keen on Unity anymore. Ubuntu would turn Unity to work in mobiles, tablets, laptops and desktops, but newer the Unity, less it would be useful for the desktop/laptop, so if I try to remaster, it would be Kubuntu, Lubuntu, Xubuntu etc. I've already done Utopic Kubuntu, Lubuntu and Xubuntu, especially Xubuntu with Kwin. It was thought that Xubuntu with Compiz would be nicer than with Kwin, but I find Kwin to be neater, and less buggy than with Compiz. 

Anyway, coming back to remastering, python-apt templates is what one needs when updating and upgrading. Have look at Ubuntu clones such as Mint or Zorin, and check the python-apt templates there. You'd notice there are Mint.info and Zorin.info in the respective distros, but when you open the .info file, you'd see Ubuntu repos there. To update/upgrade you need the lsb-release distro name exactly equal to the .info file name in the python-apt/templates. By the way, I remaster the distros for fun and to put in my friend's laptops. Anyone can do that kind of remastering. 

In Trusty/Utopic/Vivid Gnome(and also Ubuntu/Kubuntu/Lubuntu/Xubuntu) releases, I don't know whether Ubuntu devs are pulling Debian/Tanglu/Blankon repos or otherwise. And, it doesn't matter. But, if Debian repos are going to be ahead of Ubuntu repos, I'd move into Debian, as my only grudge against Debian was the lateness of upgraded apps in Debian repos before. Of course, I am talking about testing repos, just like we are using vivid repos here. 

By the way, Zika, I just wanted to have a discussion here, not an argument. Take care!

---

### Post by zika on 2014-11-10
> **Chanath said:**
> By the way, Zika, I just wanted to have a discussion here, not an argument. Take care!Ditto. Why do You think I've asked a question if I did dot want a discussion? I do want argument(s) but not the way You've used that word... ;) Now I'm to read Your argument(s) and will be back if I have any new question or else to say. Take care (without exclamation mark). ;)
Back, after reading it carefully. No answer to my one and only question: [COLOR=#000000][I]why, **how** and when these templates are used?
[/I]I've asked that question just because there was already a conversation about that... I do have some answer(s) but I wanted to check them with someone that have wider experience than that of mine. I'm just Ubuntu+/-[/COLOR][COLOR=#000000][FONT=arial]&#949; guy... ;)[/FONT][/COLOR]

---

### Post by Chanath on 2014-11-10
> **zika said:**
> Ditto. Why do You think I've asked a question if I did dot want a discussion? I do want argument(s) but not the way You've used that word... ;) Now I'm to read Your argument(s) and will be back if I have any new question or else to say. Take care (without exclamation mark). ;)
Back, after reading it carefully. No answer to my one and only question: [COLOR=#000000][I]why, **how** and when these templates are used?
[/I]I've asked that question just because there was already a converstaion about that... I do have some answer(s) but I wanted to check them wit someone that have wider experience than that of mine. I'm just Ubuntu+/-[/COLOR][COLOR=#000000][FONT=arial]&#949; guy... ;)[/FONT][/COLOR]

Ok, Zika, let me know your answers on [COLOR=#000000][I]why, **how** and when these templates are used?
[/I][/COLOR]

---

### Post by mc4man on 2014-11-10
The files are added upon accepted request to the debian source & are used per distro. So in the case of Ubuntu just the ubuntu files.
"but carelessness of the devs not to delete these repos is not that good." - nonsense

Ex. blankon - 
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=747498](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=747498)

---

### Post by Chanath on 2014-11-10
> **mc4man said:**
> The files are added upon accepted request to the debian source & are used per distro. So in the case of Ubuntu just the ubuntu files.
"but carelessness of the devs not to delete these repos is not that good." - nonsense

Ex. blankon - 
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=747498](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=747498)

Hmmm...bugs on Debian?
Are we talking about Ubuntu or Debian?
Blankon is supposed to be based on Ubuntu, not the other way. Can you tell us, mc4man, why Ubuntu Gnome Vivid needs Blankon Tambora info in it? Or Tanglu Aequorea info in it? The development release of Tanglu is Bartholomea, and Tanglu is based on Debian. The last Blankon distro was released on 2014-02-15.
Is Ubuntu Gnome Vivid based on Blankon or Debian, mc4man?

Edit: To update and dist-upgrade Vivid, you don't need **any** other files in python-apt/templates except Ubuntu.info and Ubuntu.mirrors. You change the name in lsb-release to any name you desire and rename the Ubuntu.info to that name, and you can update and upgrade your Vivid. Do you agree?

---

### Post by ventrical on 2014-11-10
> **Chanath said:**
> Hmmm...bugs on Debian?
Are we talking about Ubuntu or Debian?
Blankon is supposed to be based on Ubuntu, not the other way. Can you tell us, mc4man, why Ubuntu Gnome Vivid needs Blankon Tambora info in it? Or Tanglu Aequorea info in it? The development release of Tanglu is Bartholomea, and Tanglu is based on Debian. The last Blankon distro was released on 2014-02-15.
Is Ubuntu Gnome Vivid based on Blankon or Debian, mc4man?

"but carelessness of the devs not to delete these repos is not that good." 

 Hi Canath,

  We all know that there are housekeeping issues with usr/share/python-apt/templates/ but they are not affecting the distro currently.  This also applies to ubuntu.info file and the addendums there - however, after they are amended  then the data is just cursory but to cite it as carelessness of the devs is a big slight - don't you think?


Regards..

---

### Post by ventrical on 2014-11-10
> **Chanath said:**
> 

Edit: To update and dist-upgrade Vivid, you don't need **any** other files in python-apt/templates except Ubuntu.info and Ubuntu.mirrors. You change the name in lsb-release to any name you desire and rename the Ubuntu.info to that name, and you can update and upgrade your Vivid. Do you agree?

I see you found out  (as did I) that it is not really that big of an issue. So since it is editable we can take control .. but if you decide to do this then don't forget to flag it as read only - if you do not want any changes. Of course , as you do this it will prevent any overwrites and as the cycle develops over time that file may need to be over wrote - if not - may cause issues.

Regards..

---

### Post by Chanath on 2014-11-10
> **ventrical said:**
> "but carelessness of the devs not to delete these repos is not that good." 

 Hi Canath,

  We all know that there are housekeeping issues with usr/share/python-apt/templates/ but they are not affecting the distro currently.  This also applies to ubuntu.info file and the addendums there - however, after they are amended  then the data is just cursory but to cite it as carelessness of the devs is a big slight - don't you think?


Regards..

Hi Ventrical,

I noticed this "housekeeping" problem way down in Quantal, there was gNewsense and Debian info in that. It never changed in Trusty or Utopic and now in Vivid. I don't think they are putting much heart into producing Ubuntu-Gnome now.

---

### Post by zika on 2014-11-10
> **ventrical said:**
> there are housekeeping issues with usr/share/python-apt/templates/Which are those...?

---

### Post by Chanath on 2014-11-10
> **ventrical said:**
> I see you found out  (as did I) that it is not really that big of an issue. So since it is editable we can take control .. but if you decide to do this then don't forget to flag it as read only - if you do not want any changes. Of course , as you do this it will prevent any overwrites and as the cycle develops over time that file may need to be over wrote - if not - may cause issues.

Regards..

Yes, Ventrical, I know that. This overwriting can be blocked while upgrading. Thanks for the discussion.:p

---

### Post by ventrical on 2014-11-10
> **zika said:**
> Which are those...?

Non essential  verbose.

```

Suite: trusty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 14.04 'Trusty Tahr'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: trusty
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 14.04 'Trusty Tahr'

Suite: trusty
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*14.04
MatchURI: cdrom:\[Ubuntu.*14.04
Description: Cdrom with Ubuntu 14.04 'Trusty Tahr'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: trusty
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: trusty
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: trusty-security
ParentSuite: trusty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: trusty-security
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: trusty-updates
ParentSuite: trusty
RepositoryType: deb
Description: Recommended updates

Suite: trusty-updates
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: trusty-proposed
ParentSuite: trusty
RepositoryType: deb
Description: Pre-released updates

Suite: trusty-proposed
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: trusty-backports
ParentSuite: trusty
RepositoryType: deb
Description: Unsupported updates

Suite: trusty-backports
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates


Suite: saucy
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 13.10 'Saucy Salamander'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: saucy
ParentSuite: saucy
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 13.10 'Saucy Salamander'

Suite: saucy
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*13.10
MatchURI: cdrom:\[Ubuntu.*13.10
Description: Cdrom with Ubuntu 13.10 'Saucy Salamander'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: saucy
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: saucy
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: saucy-security
ParentSuite: saucy
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: saucy-security
ParentSuite: saucy
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: saucy-updates
ParentSuite: saucy
RepositoryType: deb
Description: Recommended updates

Suite: saucy-updates
ParentSuite: saucy
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: saucy-proposed
ParentSuite: saucy
RepositoryType: deb
Description: Pre-released updates

Suite: saucy-proposed
ParentSuite: saucy
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: saucy-backports
ParentSuite: saucy
RepositoryType: deb
Description: Unsupported updates

Suite: saucy-backports
ParentSuite: saucy
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates


Suite: raring
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 13.04 'Raring Ringtail'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: raring
ParentSuite: raring
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 13.04 'Raring Ringtail'

Suite: raring
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*13.04
MatchURI: cdrom:\[Ubuntu.*13.04
Description: Cdrom with Ubuntu 13.04 'Raring Ringtail'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: raring
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: raring
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: raring-security
ParentSuite: raring
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: raring-security
ParentSuite: raring
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: raring-updates
ParentSuite: raring
RepositoryType: deb
Description: Recommended updates

Suite: raring-updates
ParentSuite: raring
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: raring-proposed
ParentSuite: raring
RepositoryType: deb
Description: Pre-released updates

Suite: raring-proposed
ParentSuite: raring
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: raring-backports
ParentSuite: raring
RepositoryType: deb
Description: Unsupported updates

Suite: raring-backports
ParentSuite: raring
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates


Suite: quantal
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 12.10 'Quantal Quetzal'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: quantal
ParentSuite: quantal
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 12.10 'Quantal Quetzal'

Suite: quantal
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*12.10
MatchURI: cdrom:\[Ubuntu.*12.10
Description: Cdrom with Ubuntu 12.10 'Quantal Quetzal'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: quantal
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: quantal
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: quantal-security
ParentSuite: quantal
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: quantal-security
ParentSuite: quantal
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: quantal-updates
ParentSuite: quantal
RepositoryType: deb
Description: Recommended updates

Suite: quantal-updates
ParentSuite: quantal
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: quantal-proposed
ParentSuite: quantal
RepositoryType: deb
Description: Pre-released updates

Suite: quantal-proposed
ParentSuite: quantal
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: quantal-backports
ParentSuite: quantal
RepositoryType: deb
Description: Unsupported updates

Suite: quantal-backports
ParentSuite: quantal
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates

Suite: precise
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 12.04 'Precise Pangolin'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: precise
ParentSuite: precise
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 12.04 'Precise Pangolin'

Suite: precise
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*12.04
MatchURI: cdrom:\[Ubuntu.*12.04
Description: Cdrom with Ubuntu 12.04 'Precise Pangolin'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: precise
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: precise
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: precise-security
ParentSuite: precise
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: precise-security
ParentSuite: precise
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: precise-updates
ParentSuite: precise
RepositoryType: deb
Description: Recommended updates

Suite: precise-updates
ParentSuite: precise
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: precise-proposed
ParentSuite: precise
RepositoryType: deb
Description: Pre-released updates

Suite: precise-proposed
ParentSuite: precise
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: precise-backports
ParentSuite: precise
RepositoryType: deb
Description: Unsupported updates

Suite: precise-backports
ParentSuite: precise
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates

Suite: oneiric
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 11.10 'Oneiric Ocelot'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: oneiric
ParentSuite: oneiric
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 11.10 'Oneiric Ocelot'

Suite: oneiric
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*11.10
MatchURI: cdrom:\[Ubuntu.*11.10
Description: Cdrom with Ubuntu 11.10 'Oneiric Ocelot'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: oneiric
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: oneiric
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: oneiric-security
ParentSuite: oneiric
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: oneiric-security
ParentSuite: oneiric
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: oneiric-updates
ParentSuite: oneiric
RepositoryType: deb
Description: Recommended updates

Suite: oneiric-updates
ParentSuite: oneiric
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: oneiric-proposed
ParentSuite: oneiric
RepositoryType: deb
Description: Pre-released updates

Suite: oneiric-proposed
ParentSuite: oneiric
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: oneiric-backports
ParentSuite: oneiric
RepositoryType: deb
Description: Unsupported updates

Suite: oneiric-backports
ParentSuite: oneiric
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates


Suite: natty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 11.04 'Natty Narwhal'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: natty
ParentSuite: natty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 11.04 'Natty Narwhal'

Suite: natty
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*11.04
MatchURI: cdrom:\[Ubuntu.*11.04
Description: Cdrom with Ubuntu 11.04 'Natty Narwhal'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: natty
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: natty
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: natty-security
ParentSuite: natty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: natty-security
ParentSuite: natty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: natty-updates
ParentSuite: natty
RepositoryType: deb
Description: Recommended updates

Suite: natty-updates
ParentSuite: natty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: natty-proposed
ParentSuite: natty
RepositoryType: deb
Description: Pre-released updates

Suite: natty-proposed
ParentSuite: natty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: natty-backports
ParentSuite: natty
RepositoryType: deb
Description: Unsupported updates

Suite: natty-backports
ParentSuite: natty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates

Suite: maverick
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 10.10 'Maverick Meerkat'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: maverick
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*10.10
MatchURI: cdrom:\[Ubuntu.*10.10
Description: Cdrom with Ubuntu 10.10 'Maverick Meerkat'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: maverick
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: maverick
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: maverick-security
ParentSuite: maverick
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: maverick-updates
ParentSuite: maverick
RepositoryType: deb
Description: Recommended updates

Suite: maverick-proposed
ParentSuite: maverick
RepositoryType: deb
Description: Pre-released updates

Suite: maverick-backports
ParentSuite: maverick
RepositoryType: deb
Description: Unsupported updates

Suite: lucid
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 10.04 'Lucid Lynx'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: lucid
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*10.04
MatchURI: cdrom:\[Ubuntu.*10.04
Description: Cdrom with Ubuntu 10.04 'Lucid Lynx'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: lucid-security
ParentSuite: lucid
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: lucid-updates
ParentSuite: lucid
RepositoryType: deb
Description: Recommended updates

Suite: lucid-proposed
ParentSuite: lucid
RepositoryType: deb
Description: Pre-released updates

Suite: lucid-backports
ParentSuite: lucid
RepositoryType: deb
Description: Unsupported updates

Suite: karmic
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 9.10 'Karmic Koala'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: karmic
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*9.10
MatchURI: cdrom:\[Ubuntu.*9.10
Description: Cdrom with Ubuntu 9.10 'Karmic Koala'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: karmic-security
ParentSuite: karmic
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: karmic-updates
ParentSuite: karmic
RepositoryType: deb
Description: Recommended updates

Suite: karmic-proposed
ParentSuite: karmic
RepositoryType: deb
Description: Pre-released updates

Suite: karmic-backports
ParentSuite: karmic
RepositoryType: deb
Description: Unsupported updates

Suite: jaunty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 9.04 'Jaunty Jackalope'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: jaunty
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*9.04
MatchURI: cdrom:\[Ubuntu.*9.04
Description: Cdrom with Ubuntu 9.04 'Jaunty Jackalope'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: jaunty-security
ParentSuite: jaunty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: jaunty-updates
ParentSuite: jaunty
RepositoryType: deb
Description: Recommended updates

Suite: jaunty-proposed
ParentSuite: jaunty
RepositoryType: deb
Description: Pre-released updates

Suite: jaunty-backports
ParentSuite: jaunty
RepositoryType: deb
Description: Unsupported updates

Suite: intrepid
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 8.10 'Intrepid Ibex'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: intrepid
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*8.10
MatchURI: cdrom:\[Ubuntu.*8.10
Description: Cdrom with Ubuntu 8.10 'Intrepid Ibex'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: intrepid-security
ParentSuite: intrepid
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: intrepid-updates
ParentSuite: intrepid
RepositoryType: deb
Description: Recommended updates

Suite: intrepid-proposed
ParentSuite: intrepid
RepositoryType: deb
Description: Pre-released updates

Suite: intrepid-backports
ParentSuite: intrepid
RepositoryType: deb
Description: Unsupported updates


Suite: hardy
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 8.04 'Hardy Heron'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: hardy
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*8.04
MatchURI: cdrom:\[Ubuntu.*8.04
Description: Cdrom with Ubuntu 8.04 'Hardy Heron'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: hardy-security
ParentSuite: hardy
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: hardy-updates
ParentSuite: hardy
RepositoryType: deb
Description: Recommended updates

Suite: hardy-proposed
ParentSuite: hardy
RepositoryType: deb
Description: Pre-released updates

Suite: hardy-backports
ParentSuite: hardy
RepositoryType: deb
Description: Unsupported updates


Suite: gutsy
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu
BaseURI-sparc: http://archive.ubuntu.com/ubuntu/
MatchURI-sparc: archive.ubuntu.com/ubuntu
MirrorsFile: Ubuntu.mirrors
Description: Ubuntu 7.10 'Gutsy Gibbon'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: gutsy
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*7.10
MatchURI: cdrom:\[Ubuntu.*7.10
Description: Cdrom with Ubuntu 7.10 'Gutsy Gibbon'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: gutsy-security
ParentSuite: gutsy
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-sparc: http://security.ubuntu.com/ubuntu/
MatchURI-sparc: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: gutsy-updates
ParentSuite: gutsy
RepositoryType: deb
Description: Recommended updates

Suite: gutsy-proposed
ParentSuite: gutsy
RepositoryType: deb
Description: Pre-released updates

Suite: gutsy-backports
ParentSuite: gutsy
RepositoryType: deb
Description: Unsupported updates


Suite: feisty
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
MirrorsFile: Ubuntu.mirrors
Description: Ubuntu 7.04 'Feisty Fawn'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: feisty
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*7.04
MatchURI: cdrom:\[Ubuntu.*7.04
Description: Cdrom with Ubuntu 7.04 'Feisty Fawn'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: feisty-security
ParentSuite: feisty
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
Description: Important security updates

Suite: feisty-updates
ParentSuite: feisty
RepositoryType: deb
Description: Recommended updates

Suite: feisty-proposed
ParentSuite: feisty
RepositoryType: deb
Description: Pre-released updates

Suite: feisty-backports
ParentSuite: feisty
RepositoryType: deb
Description: Unsupported updates

Suite: edgy
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
MirrorsFile: Ubuntu.mirrors
Description: Ubuntu 6.10 'Edgy Eft'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: edgy
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*6.10
MatchURI: cdrom:\[Ubuntu.*6.10
Description: Cdrom with Ubuntu 6.10 'Edgy Eft'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: edgy-security
ParentSuite: edgy
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
Description: Important security updates

Suite: edgy-updates
ParentSuite: edgy
RepositoryType: deb
Description: Recommended updates

Suite: edgy-proposed
ParentSuite: edgy
RepositoryType: deb
Description: Pre-released updates

Suite: edgy-backports
ParentSuite: edgy
RepositoryType: deb
Description: Unsupported updates

Suite: dapper
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
MirrorsFile: Ubuntu.mirrors
Description: Ubuntu 6.06 LTS 'Dapper Drake'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained (universe)
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software (Multiverse)
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: dapper
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*6.06
MatchURI: cdrom:\[Ubuntu.*6.06
Description: Cdrom with Ubuntu 6.06 LTS 'Dapper Drake'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: dapper-security
ParentSuite: dapper
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
Description: Important security updates

Suite: dapper-updates
ParentSuite: dapper
RepositoryType: deb
Description: Recommended updates

Suite: dapper-proposed
ParentSuite: dapper
RepositoryType: deb
Description: Pre-released updates

Suite: dapper-backports
ParentSuite: dapper
RepositoryType: deb
Description: Unsupported updates

Suite: breezy
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
MirrorsFile: Ubuntu.mirrors
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 5.10 'Breezy Badger'
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright
Component: universe
CompDescription: Community-maintained (Universe)
Component: multiverse
CompDescription: Non-free (Multiverse)

Suite: breezy
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*5.10
MatchURI: cdrom:\[Ubuntu.*5.10
Description: Cdrom with Ubuntu 5.10 'Breezy Badger'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: breezy-security
ParentSuite: breezy
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 5.10 Security Updates

Suite: breezy-updates
ParentSuite: breezy
RepositoryType: deb
Description: Ubuntu 5.10 Updates

Suite: breezy-backports
ParentSuite: breezy
RepositoryType: deb
Description: Ubuntu 5.10 Backports

Suite: hoary
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
MirrorsFile: Ubuntu.mirrors
Description: Ubuntu 5.04 'Hoary Hedgehog'
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright
Component: universe
CompDescription: Community-maintained (Universe)
Component: multiverse
CompDescription: Non-free (Multiverse)

Suite: hoary
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*5.04
MatchURI: cdrom:\[Ubuntu.*5.04
Description: Cdrom with Ubuntu 5.04 'Hoary Hedgehog'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: hoary-security
ParentSuite: hoary
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 5.04 Security Updates

Suite: hoary-updates
ParentSuite: hoary
RepositoryType: deb
Description: Ubuntu 5.04 Updates

Suite: hoary-backports
ParentSuite: hoary
RepositoryType: deb
Description: Ubuntu 5.04 Backports

Suite: warty
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
Description: Ubuntu 4.10 'Warty Warthog'
Component: main
CompDescription: No longer officially supported
Component: restricted
CompDescription: Restricted copyright
Component: universe
CompDescription: Community-maintained (Universe)
Component: multiverse
CompDescription: Non-free (Multiverse)

Suite: warty
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*4.10
MatchURI: cdrom:\[Ubuntu.*4.10
Description: Cdrom with Ubuntu 4.10 'Warty Warthog'
Available: False
Component: main
CompDescription: No longer officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: warty-security
ParentSuite: warty
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Ubuntu 4.10 Security Updates

Suite: warty-updates
ParentSuite: warty
RepositoryType: deb
Description: Ubuntu 4.10 Updates

Suite: warty-backports
ParentSuite: warty
RepositoryType: deb
Description: Ubuntu 4.10 Backports

```


Regards..

---

### Post by ventrical on 2014-11-10
> **Chanath said:**
> Hi Ventrical,

I noticed this "housekeeping" problem way down in Quantal, there was gNewsense and Debian info in that. It never changed in Trusty or Utopic and now in Vivid. I don't think they are putting much heart into producing Ubuntu-Gnome now.

Personally I think that there are two issues here that you are trying to append into one. Python-apt is just producing templates from its' script routine, essential and non essential. That would be an issue to take up with the developers directly  IMHO. I essentially agree with you that most of those files are not pertinent to the ubuntu current development cycle.

Secondly, the gnome project has had it's ups and downs. Then support is there one day and then seems to wane and many testers find themselves pulling in ppas, etc, is why I gave up on testing it. But I do not see your point how the /templates/ files is adversely affecting the  gnome development current. SO I think I may be missing somthing here :) Not your bad !, Mine :)

Regards..

---

### Post by Chanath on 2014-11-10
> **ventrical said:**
> Personally I think that there are two issues here that you are trying to append into one. Python-apt is just producing templates from its' script routine, essential and non essential. That would be an issue to take up with the developers directly  IMHO. I essentially agree with you that most of those files are not pertinent to the ubuntu current development cycle.

Secondly, the gnome project has had it's ups and downs. Then support is there one day and then seems to wane and many testers find themselves pulling in ppas, etc, is why I gave up on testing it. But I do not see your point how the /templates/ files is adversely affecting the  gnome development current. SO I think I may be missing somthing here :) Not your bad !, Mine :)

Regards..

I agree, ventrical, there are two issues here. I wanted to say something about the python-apt templates, and the second issue is about the Ubuntu-Gnome. You are not missing anything. I am somewhat dissapointed with Ubuntu-Gnome and the second issue just jumped in. I actually like Gnome 3, so I'd be enjoying it in Debian and OpenSuse, or even Fedora. I would like Ubuntu to put some interest on Gnome 3, rather than Unity, which is running away from us laptop/desktop guys. Regards.

---

### Post by zika on 2014-11-10
> **ventrical said:**
> Non essential  verbose. Regards..Aside from that (fact that You've repeated/posted(full version each time) several times) any other? (We've talked about that, more than that file deserves attention, in my opinion). Let me repeat that what is in that file has its purpose, in my opinion. To stay on topic, files that are topic here have their reason of being there, on of those is mentioned in the URL given above. It is nice to see that in U+1 we have time to chat (sadly, repeatedly) about stuff like this. Looks like another calm U+1 round... ;)

---

### Post by ventrical on 2014-11-10
> **zika said:**
> Aside from that fact that You've repeated/posted(full version each time) several times? 

You asked!  .. and you are mistaken my friend. I did not post the full-version (as you implied) I copied from trusty to warty. There is a big difference. You can repeat your opinion all you like , all you wish - you say it has it's purpose .. I say it is housekeeping issue based on facts.   


> 
(We've talked about that, more than that file deserves attention, in my opinion). Let me repeat that what is in that file has its purpose, in my opinion. To stay on topic, files that are topic here have their reason of being there, on of those is mentioned in the URL given above. It is nice tosee that in U+1 we have time to chat (sadly, repeatedly) about stuff like this. Looks like another calm U+1 round... ;)



ummm.. whatever :) as you say . :)

---

### Post by Elfy on 2014-11-10
Bicker ye not.

Thanks ;)

---

### Post by zika on 2014-11-10
> **Elfy said:**
> Bicker ye not.Thanks ;)Point taken, over & out.

---

### Post by ventrical on 2014-11-10
> **Chanath said:**
> I agree, ventrical, there are two issues here. I wanted to say something about the python-apt templates, and the second issue is about the Ubuntu-Gnome. You are not missing anything. I am somewhat dissapointed with Ubuntu-Gnome and the second issue just jumped in. I actually like Gnome 3, so I'd be enjoying it in Debian and OpenSuse, or even Fedora. I would like Ubuntu to put some interest on Gnome 3, rather than Unity, which is running away from us laptop/desktop guys. Regards.

As zika has said ;

> 
Looks like another calm U+1 round... :wink:


:) I may just may give gnome3 a spin again. But as you say , lunity is running away with this convergence/phone/desktop/ scheme and unity8 is another story all together...:) so in all the fray, floss , the razzle and the dazzle I found razorqt, a neat little minimal desktop experience in the ubuntu repos so when things get slow and dry I can build on that  and do some ovverclocking .. etc.. Apologies for being off topic.

Regards..

---

### Post by Chanath on 2014-11-10
> **ventrical said:**
> As zika has said ;

:) I may just may give gnome3 a spin again. But as you say , lunity is running away with this convergence/phone/desktop/ scheme and unity8 is another story all together...:) so in all the fray, floss , the razzle and the dazzle I found razorqt, a neat little minimal desktop experience in the ubuntu repos so when things get slow and dry I can build on that  and do some ovverclocking .. etc.. Apologies for being off topic.

Regards..

Yes, Please.
Give Ubuntu-Gnome a go, Ventrical. I'd be happy to know your experience in it. I am keeping it and updating/upgrading everyday. One day, Gnome 3.14 would be there. I'd really like the Ubuntu-Gnome devs to succeed. Regards!

---

### Post by zika on 2014-11-10
> **Chanath said:**
> Yes, Please. Give Ubuntu-Gnome a go, Ventrical. I'd be happy to know your experience in it. I am keeping it and updating/upgrading everyday. One day, Gnome 3.14 would be there. I'd really like the Ubuntu-Gnome devs to succeed. Regards!(Kind of offtopic, but...)
3.14 is here:
1. [https://launchpad.net/~ricotz/+archive/ubuntu/testing?field.series_filter=vivid](https://launchpad.net/~ricotz/+archive/ubuntu/testing?field.series_filter=vivid)
2. Vivid has 3.14 as far as I can locate versions... I might be wrong... And it works... ;) Not that I work in it 24/7 but...

---

### Post by ventrical on 2014-11-10
> **Chanath said:**
> Yes, Please.
Give Ubuntu-Gnome a go, Ventrical. I'd be happy to know your experience in it. I am keeping it and updating/upgrading everyday. One day, Gnome 3.14 would be there. I'd really like the Ubuntu-Gnome devs to succeed. Regards!

Goes to show how much I know. :)

[http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/)

  I thought they killed that distro.  Iv'e been using unity for  so long that I forgot about it.  I'll dl the iso and take a look see at how far they come. Oh .. yeah .. (one more off topic msg) :) ... I recall now why I stopped testing .. It was because that there were a lot of bugs back a few cycles ago and I found it impossible to quickly train and migrate noobs to it's desktop experience. As soon as there was once crash , burp or hic-up it was .. See!  There .. I can't handle this .. I want my Windows XP back .. etc .. yadda.. Oy. :)

Ok .. will give it a spin.

:)

---

### Post by Chanath on 2014-11-10
> **ventrical said:**
> Goes to show how much I know. :)

[http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/)

  I thought they killed that distro.  Iv'e been using unity for  so long that I forgot about it.  I'll dl the iso and take a look see at how far they come. Oh .. yeah .. (one more off topic msg) :) ... I recall now why I stopped testing .. It was because that there were a lot of bugs back a few cycles ago and I found it impossible to quickly train and migrate noobs to it's desktop experience. As soon as there was once crash , burp or hic-up it was .. See!  There .. I can't handle this .. I want my Windows XP back .. etc .. yadda.. Oy. :)

Ok .. will give it a spin.

:)

Good.
Right now, there is a bug, which takes off all your gnome-shell-extensions when you reboot, that is, you have to re-enable them every time. Don't know how long you'd stand that. Regards.

---

### Post by ventrical on 2014-11-10
> **Chanath said:**
> Good.
Right now, there is a bug, which takes off all your gnome-shell-extensions when you reboot, that is, you have to re-enable them every time. Don't know how long you'd stand that. Regards.

Personally I do not mind the headaches.  What really gets my hair up is when I am trying to teach new prospects.  It is a very unforgiving trade/hobby .. but that's what I do  (also with Kelcom). Unity is a little more user friendly but even that nowadays is beginning to be a tough sell.

 I am just saying that  I do not expect any time soon that gnome-3 will be awarded the  Noob Friendly Seal of Approval. :)

Regards..

---

### Post by ventrical on 2014-11-10
> **Chanath said:**
> Good.
Right now, there is a bug, which takes off all your gnome-shell-extensions when you reboot, that is, you have to re-enable them every time. Don't know how long you'd stand that. Regards.

I'm about to give it a spin  in a little bit. Got the iso.. etc... supper...done .. now tea time .. and then will spin.

---

### Post by ventrical on 2014-11-10
> **Elfy said:**
> Bicker ye not.

Thanks ;)


  I , Puck, a bickerer call?  :)

  If us shadows have offended
  R'membr tis only ubuntu.info needs not be ammended 
  With superfluosity uncomprehended!

jk
:)

---

### Post by Elfy on 2014-11-10
:)

---

### Post by Hazzabin on 2014-11-10
Hey guys

Slightly off topic but but........Gnome 15.04 as Chanath said does drop the extensions each reboot, you need to reset them, other than that mines been running
without to many glitches, I also added flashback just for fun, also runs well......so at my wimp I can choose which one I want to 'play' with

just my 5 pennies worth :lolflag:

---

### Post by Cavsfan on 2014-11-10
> **ventrical said:**
> [http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/)

Nice find! I'd be interested in that if I had another partition. But I don't see that happening. :p

> **ventrical said:**
> I'm about to give it a spin  in a little bit. Got the iso.. etc... supper...done .. now tea time .. and then will spin.

By all means let us know how it goes. I'm using Vivid Mate, which as you know is solely based on gnome. I don't think you can find an ISO for it. I just turned my devel install of Utopic Mate into Vivid Mate.
The developers were saying they were going to update Mate so that a dist-upgrade can be made to Vivid when it's released. And I have seen many, many Mate system updates. 
Perhaps they will make an ISO download at release time.

What is that Ubuntu Gnome system - gnome shell or gnome shell and flashback without Unity? Just curious.

---

### Post by Hazzabin on 2014-11-10
Gnome Shell Cavsfan this message coming from Mate mate :)

---

### Post by mc4man on 2014-11-10
> **Chanath said:**
> Hmmm...bugs on Debian?
Are we talking about Ubuntu or Debian?
Blankon is supposed to be based on Ubuntu, not the other way. Can you tell us, mc4man, why Ubuntu Gnome Vivid needs Blankon Tambora info in it? Or Tanglu Aequorea info in it? The development release of Tanglu is Bartholomea, and Tanglu is based on Debian. The last Blankon distro was released on 2014-02-15.
Is Ubuntu Gnome Vivid based on Blankon or Debian, mc4man?

Edit: To update and dist-upgrade Vivid, you don't need **any** other files in python-apt/templates except Ubuntu.info and Ubuntu.mirrors. You change the name in lsb-release to any name you desire and rename the Ubuntu.info to that name, and you can update and upgrade your Vivid. Do you agree?

Ubuntu bases on Debian & uses many of their sources *untouched*. That's the case here.  (check the package name in python-apt changelog, do you see ubuntu in it's name?
 If you were to start using Debian, (jesse or sid),  you'd find this in the templates folder - 
> $ ls
Blankon.info     Debian.info     gNewSense.info     Tanglu.info     Ubuntu.info
Blankon.mirrors  Debian.mirrors  gNewSense.mirrors  Tanglu.mirrors  Ubuntu.mirrors

So why don't you do that & complain to Debian about inc. ubuntu in the templates & see where that leads...

(- the existence of template files for other distro's is irrelevant,  as is the basis of this thread

---

### Post by ventrical on 2014-11-10
> **Cavsfan said:**
> Nice find! I'd be interested in that if I had another partition. But I don't see that happening. :p



By all means let us know how it goes. I'm using Vivid Mate, which as you know is solely based on gnome. I don't think you can find an ISO for it. I just turned my devel install of Utopic Mate into Vivid Mate.
The developers were saying they were going to update Mate so that a dist-upgrade can be made to Vivid when it's released. And I have seen many, many Mate system updates. 
Perhaps they will make an ISO download at release time.

What is that Ubuntu Gnome system - gnome shell or gnome shell and flashback without Unity? Just curious.

I started a new thread here:  [http://ubuntuforums.org/showthread.php?t=2252276](http://ubuntuforums.org/showthread.php?t=2252276)

so as to not be off topic.

Regards... live session is awesome!!

---

### Post by grahammechanical on 2014-11-10
> [COLOR=#000000]Perhaps they will make an ISO download at release time.[/COLOR]

How about having Ubuntu Mate as a flavour? And there is a session on it at the Ubuntu Online Summit on Thursday at 19.00 hours

[https://ubuntu-mate.org/](https://ubuntu-mate.org/)

[http://summit.ubuntu.com/uos-1411/2014-11-13/](http://summit.ubuntu.com/uos-1411/2014-11-13/)

In defence of the Ubuntu Gnome devs. There are only a few of them and Gnome.org does keep improving (to put it politely) Gnome 3 shell, which is the default user interface on Ubuntu Gnome.

In defence of Ubuntu devs. If someone wants to fork Ubuntu in some way, then they are free to do that but it would be wrong to press gang Ubuntu devs into doing the work of a project that others have started. The decision was made a long time ago not to make the Gnome 3 shell the default Ubuntu UI. The deed is done.

---

### Post by ventrical on 2014-11-10
> **grahammechanical said:**
> How about having Ubuntu Mate as a flavour? And there is a session on it at the Ubuntu Online Summit on Thursday at 19.00 hours

[https://ubuntu-mate.org/](https://ubuntu-mate.org/)

[http://summit.ubuntu.com/uos-1411/2014-11-13/](http://summit.ubuntu.com/uos-1411/2014-11-13/)

In defence of the Ubuntu Gnome devs. There are only a few of them and Gnome.org does keep improving (to put it politely) Gnome 3 shell, which is the default user interface on Ubuntu Gnome.

In defence of Ubuntu devs. If someone wants to fork Ubuntu in some way, then they are free to do that but it would be wrong to press gang Ubuntu devs into doing the work of a project that others have started. The decision was made a long time ago not to make the Gnome 3 shell the default Ubuntu UI. The deed is done.

An with all due respect , ubuntu-desktop unity7  is a lot easier to teach people. I think also because of the bug fixes and support overall. 

Regards..

---

### Post by ventrical on 2014-11-10
@graham..

btw .. i am not giving up on unity8 and convergence by any stretch (and I doubt Canonical will either) but some type of gnome convergence would seem to have been a lot easier... 

  it's the graphical drivers and patching the depends which seems to be the hurdle.Hardware changes so fast. To stay current then something has to get obsoleted or blacklisted. Had it happen to me on older machines. One day .. perfect 3D unity, kde compiz.. etc. Then , update .. and gone.

  Basically it 's like a bridge too far from a development perspective... me thinks.

---

### Post by Chanath on 2014-11-11
> **ventrical said:**
> An with all due respect , ubuntu-desktop unity7  is a lot easier to teach people. I think also because of the bug fixes and support overall. 

Regards..

True enough, but it is even easier, if one installs Plank or Docky, then you can simply forget about the left bar and link most of the needed stuff to the bottom dock. With Gnome 3, you can make the "favorites bar" move to the bottom with an extension, and things become esier. Won't write much about Gnome3 experience here, but move to your post, so it would be more relevant. This paython-apt post could be closed or it could be kept open, so others could comment further. 
take care. :p

---

### Post by Cavsfan on 2014-11-11
> **Hazzabin said:**
> Gnome Shell Cavsfan this message coming from Mate mate :)

Thanks for that info. So, no flashback? Or you just have to sudo apt-get install that?

> **grahammechanical said:**
> How about having Ubuntu Mate as a flavour? And there is a session on it at the Ubuntu Online Summit on Thursday at 19.00 hours

[https://ubuntu-mate.org/](https://ubuntu-mate.org/)

In defence of the Ubuntu Gnome devs. There are only a few of them and Gnome.org does keep improving (to put it politely) Gnome 3 shell, which is the default user interface on Ubuntu Gnome.

In defence of Ubuntu devs. If someone wants to fork Ubuntu in some way, then they are free to do that but it would be wrong to press gang Ubuntu devs into doing the work of a project that others have started. The decision was made a long time ago not to make the Gnome 3 shell the default Ubuntu UI. The deed is done.

If in flavour you mean installing Ubuntu and then adding some mate packages to make it Mate that would not be the same. You probably already know that though.
Mate had one session option when I first installed it, then after I installed Cairo Dock it had 2 that being the other one.

Here's some info on Mate: [http://mate-desktop.org/](http://mate-desktop.org/)
And here is some info on the direction of Mate: [http://mate-desktop.org/blog/mate-interview-with-linux-luddites/](http://mate-desktop.org/blog/mate-interview-with-linux-luddites/)

Not sure if I am off topic or not. :)

---

### Post by Cavsfan on 2014-11-11
> **Hazzabin said:**
> Gnome Shell Cavsfan this message coming from Mate mate :)

Thanks for that info. So, no flashback? Or you just have to sudo apt-get install that?

> **grahammechanical said:**
> How about having Ubuntu Mate as a flavour? And there is a session on it at the Ubuntu Online Summit on Thursday at 19.00 hours

[https://ubuntu-mate.org/](https://ubuntu-mate.org/)

[http://summit.ubuntu.com/uos-1411/2014-11-13/](http://summit.ubuntu.com/uos-1411/2014-11-13/)

In defence of the Ubuntu Gnome devs. There are only a few of them and Gnome.org does keep improving (to put it politely) Gnome 3 shell, which is the default user interface on Ubuntu Gnome.

In defence of Ubuntu devs. If someone wants to fork Ubuntu in some way, then they are free to do that but it would be wrong to press gang Ubuntu devs into doing the work of a project that others have started. The decision was made a long time ago not to make the Gnome 3 shell the default Ubuntu UI. The deed is done.

If in flavour you mean installing Ubuntu and then adding some mate packages to make it Mate that would not be the same. You probably already know that though.
Mate had one session option when I first installed it, then after I installed Cairo Dock it had 2 that being the other one.

Here's some info on Mate: [http://mate-desktop.org/](http://mate-desktop.org/)

Not sure if I am off topic or not. :)

---

### Post by Hazzabin on 2014-11-11
Flashback, yes you have to install sudo or synaptic

---

