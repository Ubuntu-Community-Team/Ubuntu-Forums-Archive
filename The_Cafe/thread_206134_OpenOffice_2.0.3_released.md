---
title: "OpenOffice 2.0.3 released"
date: 2006-06-29
forum: The Cafe
---

### Post by linbetwin on 2006-06-29
[http://download.openoffice.org/2.0.3/index.html](http://download.openoffice.org/2.0.3/index.html)

---

### Post by bruce89 on 2006-06-29
At last!

---

### Post by linbetwin on 2006-06-29
[quote=bruce89]At last![/quote]

Apparently the delay was due to a bug affecting the Windows 98 version. It's nice to see that the OOo team thinks about Windows 98 users, now that even Microsoft has abandoned them.

---

### Post by bruce89 on 2006-06-29
[QUOTE=linbetwin]Apparently the delay was due to a bug affecting the Windows 98 version. It's nice to see that the OOo team thinks about Windows 98 users, now that even Microsoft has abandoned them.[/QUOTE]
That's nice of them.  In fact X-Plane (simulator) fixed support for either win98 or win95.

---

### Post by andylawrence on 2006-06-29
I hate to ask a stupid question, but since this is a point release will the updated packages make it into the repositories or should I just go download the binaries from openoffice.org?

---

### Post by GuitarHero on 2006-06-29
Yeah how long does it take for stuff in the repos to update.

---

### Post by tseliot on 2006-06-29
I can backport it as soon as it hits Dapper's repos or Debian Sid's

---

### Post by ember on 2006-06-29
Well - it will take some days for the localized versions to arrive anyway.

---

### Post by BWF89 on 2006-06-29
Just got it a couple of hours ago.

---

### Post by Lux Perpetua on 2006-06-29
Can someone summarize this release? What's new? What's fixed? Who should upgrade?

---

### Post by Sirin on 2006-06-29
I will download it for my Ubuntu system, but unfortunately, I don't think it will be able to replace Office 2007 on my Windows XP system. :lol:

---

### Post by BWF89 on 2006-06-29
[QUOTE=Lux Perpetua]Can someone summarize this release? What's new? What's fixed? Who should upgrade?[/QUOTE]
[http://development.openoffice.org/releases/2.0.3.html](http://development.openoffice.org/releases/2.0.3.html)

---

### Post by oyvindaa on 2006-06-30
I'm using OpenOffice on both my computers now (Ubuntu 6.06 and Windows XP) and I will continue doing so in the future. Just don't see the point in paying for something when you can get something just as good for free.

---

### Post by Bad Seed on 2006-06-30
[QUOTE=Lux Perpetua]Who should upgrade?[/QUOTE]
Everyone: [OpenOffice Multiple Vulnerabilities]("http://secunia.com/advisories/20867/").

---

### Post by rcarring on 2006-06-30
It looks like it's a good idea to upgrade to the latest version.

One difference I found was in the series of Options, the option marked Paths contains far fewer "paths" than did version 2.02.

---

### Post by BWF89 on 2006-06-30
I figure since OpenOffice is a free download might as well upgrade with every release whether you need to or not.

---

### Post by mscman on 2006-06-30
They finally added an update manager!  No more reinstalling every time there's a release!  Yay! =D>

---

### Post by forrestcupp on 2006-06-30
[QUOTE=BWF89][http://development.openoffice.org/releases/2.0.3.html](http://development.openoffice.org/releases/2.0.3.html)[/QUOTE]

So, I read all the technical crap that they said they fixed.  In plain, simple english, are there really any noticable differences in the new version?

---

### Post by BWF89 on 2006-06-30
@Forrestcup: Your avatar seriousaly freaks me out

---

### Post by PapaWiskas on 2006-06-30
[QUOTE=BWF89]@Forrestcup: Your avatar seriousaly freaks me out[/QUOTE]


LOL.....

---

### Post by bruce89 on 2006-06-30
[QUOTE=mscman]They finally added an update manager!  No more reinstalling every time there's a release!  Yay! =D>[/QUOTE]
I don't think it does that, I think that it just tells you when there is an update.  I don't know though, an update manager would be brilliant for Windows (we already have a better system - apt).

---

### Post by 1002285 on 2006-07-01
I have OOo 2.0.2 Estonian version. If I upgrade it, will I loose menus in my language? And if this happens, what can I do to get it back once the localised version is out?

---

### Post by yotama9 on 2006-07-02
I hate to ask realy dumb question....

how do I install it? all I get from the tar file are rpm files :(

---

### Post by barbarian on 2006-07-02
[I]sudo alien yourpackage.rpm
sudo dpkg -i yourpackage.deb[/I]

---

### Post by yotama9 on 2006-07-02
and in the case at hand? 
I need to use 

sudo alien -d *.rpm
sudo dpkg -i *.deb 

asuming that I want full install of OO

---

### Post by jeremy on 2006-07-02
[QUOTE=Sirin]...I don't think it will be able to replace Office 2007 on my Windows XP system. :lol:[/QUOTE]
No, it won't be able to replace it, but you can always uninstall it. You won't get your money back though.

---

### Post by JoWilly on 2006-07-02
[quote=forrestcupp]So, I read all the technical crap that they said they fixed.  In plain, simple english, are there really any noticable differences in the new version?[/quote]

Security fixes, bug fixes,  and improved MS Office import/export filters.

---

### Post by JoWilly on 2006-07-02
Oh... yeah, and it  seems there's now also native 64bit support (I've tested it on fedora 6 test1,  much faster).

---

### Post by JoWilly on 2006-07-02
[quote=forrestcupp]So, I read all the technical crap that they said they fixed.  In plain, simple english, are there really any noticable differences in the new version?[/quote] 
This is in plain English on the main openoffice.org page : ;)


OpenOffice.org 2.0.3 is recommended for all. Enhancements  include:[LIST]
[*]performance improvements: for example, a 23 percent improvement in certain Calc benchmarks
[*] further improvements to file format compatibility with Microsoft Office files
[*] new email integration features for users wanting to send emails in Microsoft file formats
[*] more control over how exported PDF documents will display when opened in a PDF reader
[*] support for more languages and improvements in hyphenation and thesaurus
[*] support for Intel architecture for Mac OS X plus improved Mac OS X System integration
[*] built-in check for updated versions[/LIST]

---

### Post by forrestcupp on 2006-07-03
[QUOTE=JoWilly]This is in plain English on the main openoffice.org page : ;)
[/QUOTE]

Thank you, I just went to the link that was posted, and not to the main page.

BWF89, sorry about freaking you out.  I'm not really a freak, just someone who was fiddling around with the GIMP.

---

### Post by yotama9 on 2006-07-03
I tried to install it (using alien -i -c) and it all went wierd telling me that there is other program installing pkgs working (when non were workin) when it had finnished I open synaptec and saw that all was installed

I moved to /opt/openoffice directory and typed in:

./swriter

this is what I got:

[email]shuki@shuki-laptop:/opt/openoffice.org[/email]2.0/program$ ./swriter
[Java framework] Invalid value for bootstrap variable: UNO_JAVA_JFW_VENDOR_SETTINGSjavaldx failed!
[Java framework] Invalid value for bootstrap variable: UNO_JAVA_JFW_VENDOR_SETTI

---

### Post by cyboreal on 2006-07-03
[QUOTE=tseliot]I can backport it as soon as it hits Dapper's repos or Debian Sid's[/QUOTE]
tseliot, it's in Debian Sid's repos but has a number of dependencies that conflict with K/Ubuntu 6.06, e.g. KDE 3.5.3 for the openoffice.org-kde package.  Can you give us an update on the status of the backport for OOo 2.0.3?

---

### Post by ashrack on 2006-07-04
I am only interested in this:
 further improvements to file format compatibility with Microsoft Office files

What exactly do they mean by that?

---

### Post by tseliot on 2006-07-04
[QUOTE=cyboreal]tseliot, it's in Debian Sid's repos but has a number of dependencies that conflict with K/Ubuntu 6.06, e.g. KDE 3.5.3 for the openoffice.org-kde package.  Can you give us an update on the status of the backport for OOo 2.0.3?[/QUOTE]
It can't be backported (AFAIK) from Sid therefore we have to wait for Edgy's version of openoffice and then the backport might be easier to do.

---

### Post by 3z3k3l on 2006-07-06
[QUOTE=yotama9]and in the case at hand? 
I need to use 

sudo alien -d *.rpm
sudo dpkg -i *.deb 

asuming that I want full install of OO[/QUOTE]

Do you have to un-install the old OpenOffice?

because I get
```
Selecting previously deselected package openoffice.org-debian-menus.
dpkg: regarding openoffice.org-debian-menus_2.0.3-2_all.deb containing openoffice.org-debian-menus:
 openoffice.org-core conflicts with openoffice.org-unbundled
  openoffice.org-debian-menus provides openoffice.org-unbundled and is to be installed.
dpkg: error processing openoffice.org-debian-menus_2.0.3-2_all.deb (--install):
 conflicting packages - not installing openoffice.org-debian-menus
Errors were encountered while processing:
 openoffice.org-debian-menus_2.0.3-2_all.deb

```

If so how do you uninstall since it came with Drapper adn it won't let you do it in Syn?

Thanks!

---

### Post by desperado666 on 2006-07-06
Easy Method here

[http://www.glasen-hardt.de/openoffice.org/download.html](http://www.glasen-hardt.de/openoffice.org/download.html)

---

### Post by loko on 2006-07-12
why there is only openoffice 2.0.2-2ubuntu12.1 available instead of 2.0.3?

i assume they have ported some of the features into 2.0.2 or what does that version-number mean?

---

### Post by bruce89 on 2006-07-12
> **loko said:**
> why there is only openoffice 2.0.2-2ubuntu12.1 available instead of 2.0.3?

i assume they have ported some of the features into 2.0.2 or what does that version-number mean?

AFAIK, they have backported the security fixes to 2.0.2.  I assume that they don't want to upgrade to 2.0.3 becuase it might break things.

---

### Post by tseliot on 2006-07-12
> **tseliot said:**
> It can't be backported (AFAIK) from Sid therefore we have to wait for Edgy's version of openoffice and then the backport might be easier to do.
Yesterday I tried to backport it from Edgy but the compilation failed :(

---

### Post by bruce89 on 2006-07-12
> **tseliot said:**
> Yesterday I tried to backport it from Edgy but the compilation failed :(

That's probably why they backported the security fixes to 2.0.2 instead.

---

### Post by JoWilly on 2006-07-12
> **loko said:**
> why there is only openoffice 2.0.2-2ubuntu12.1 available instead of 2.0.3?

i assume they have ported some of the features into 2.0.2 or what does that version-number mean?

2.0.3 was sent to the build queue, but the builds failed. We need to wait for the packages to get fixed.

---

