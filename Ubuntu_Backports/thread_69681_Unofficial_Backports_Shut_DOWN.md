---
title: "Unofficial Backports Shut DOWN"
date: 2005-09-27
forum: Ubuntu Backports
---

### Post by jdong on 2005-09-27
After a quick exchange with fellow Ubuntu developers, we've decided to completely take down unoffial hoary-backports (i.e. Mirrormax, etc)

Please remove it from your /etc/apt/sources.list, and replace it with Official Backports (deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main restricted universe multiverse).



NOTE: hoary-backports-staging is still up since we have no other beta testing channels. All packages in there are BETA quality; don't cry to Ubuntu developers if something breaks, cry here.

---

### Post by matthew on 2005-09-27
Thanks for the heads up!

---

### Post by denisesballs on 2005-09-27
What about the hoary-extras?

---

### Post by jdong on 2005-09-27
[QUOTE=denisesballs]What about the hoary-extras?[/QUOTE]
Extras is unaffected by this announcements -- **backports** only.

---

### Post by John.Michael.Kane on 2005-09-27
Official Backports  are listed where on the site you posted.. also the only things listed seem to be zipfiles

---

### Post by matthew on 2005-09-27
[QUOTE=SD-Plissken]Official Backports  are listed where on the site you posted.. also the only things listed seem to be zipfiles[/QUOTE]
In your sources.list, remove any previous backports repos. In their place put the line:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main restricted universe multiverse

Then use Synaptic normally.

---

### Post by John.Michael.Kane on 2005-09-27
Thanks

---

### Post by urbandryad on 2005-09-27
I don't know how to do this? Does this pertain to me? o.o

---

### Post by jdong on 2005-09-27
[QUOTE=urbandryad]I don't know how to do this? Does this pertain to me? o.o[/QUOTE]

ALT+F2, then "gksudo gedit /etc/apt/sources.list". Add:

```

deb http://archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse

```

and remove 

```

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main restricted universe multiverse

```

---

### Post by urbandryad on 2005-09-27
okay, wasn't really clear. I don't have the internet at home, where my Linux computer is. So is this a think where it automatically updates with the internet? I don't understand. I'm a newbie.

---

### Post by Leif on 2005-09-27
[QUOTE=urbandryad]okay, wasn't really clear. I don't have the internet at home, where my Linux computer is. So is this a think where it automatically updates with the internet? I don't understand. I'm a newbie.[/QUOTE]

yes, this is about internet updates, so you shouldn't worry about it

---

### Post by almarag on 2005-09-27
Ok, now I have the official backports in sources.list. But i have some questions:

1. ¿Why some packages just dissapear from the face of the earth? I mean: no sun-j2re1.5, samba just broken, no wine, etc. ¿This packages will comeback later? ¿Or I have to search for my own?

2. ¿The change of repositories mean that backport will be officially supported?

Thanks in advance.

---

### Post by jdong on 2005-09-27
> **almarag]Ok, now I have the official backports in sources.list. But i have some questions:

1. ¿Why some packages just dissapear from the face of the earth? I mean: no sun-j2re1.5, samba just broken, no wine, etc. ¿This packages will comeback later? ¿Or I have to search for my own?
[/quote]
sun-j2re1.5 removed due to legal conflicts said:**
> 

2. ¿The change of repositories mean that backport will be officially supported?

Thanks in advance.
Yes, we are .

---

### Post by almarag on 2005-09-27
"samba idn what you're talking about"

Sorry, samba is another problem... not have to do with backports.

Many thanks for your answer.

Bye.

---

### Post by MightyFlea on 2005-09-27
Hey,

what also seems to have vanished from backports is hplip and its related packages.

I can live with the packages being marked as "local" until I upgrade to breezy, but it's kind of weird.
Were they forgotten?

---

### Post by xbaez on 2005-09-28
"ALT+F2, then "gksudo gedit /etc/apt/sources.list". Add:"

Whenever I press ALT+F2 gnome-panel produces an error, and I have to restart
then all my application icons (klipper, amarok, gaim...) stop working

Any idea were to fix this? I'm giving Gnome a shot

Regarding to backports, from what I know breezy will include Eclipse, is this right?
Or is this a program for backports?

---

### Post by jakeofnote on 2005-09-28
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hoary-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hoary-backports/universe/binary-i386/Packages.gz)  MD5Sum mismatch

yeah, thats the problem i get...
wonder what it means...
HELP!!!
tried a lot of things to avoid typos

---

### Post by numberexhaust on 2005-09-28
Hey guys, don't you think someone should add this to the ubuntuguide?  I was setting up a new machine today and was unaware of this, and seeing as how I use the guide for convenience, I was very frustrated.

It's a very simple edit, I'd be willing to do it as well.

---

### Post by ktgeorge on 2005-09-29
[QUOTE=jdong]ALT+F2, then "gksudo gedit /etc/apt/sources.list". Add:
```

deb http://archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse

```
and remove 
```

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main restricted universe multiverse

```[/QUOTE]

is working, thanks jdong

---

### Post by Struck on 2005-09-29
Hi, Im new at Using UBUNTU and need help >.< and im having problems with updates

 sudo apt-get update
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
  404 Not Found
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Release
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
  404 Not Found
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Release
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
  404 Not Found
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Release
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
  404 Not Found
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Release
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Release
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Release [102B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Release [101B]
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Release [107B]
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Release
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Release [108B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Release [104B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Release [110B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Release [106B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Release [103B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Release [109B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Sources
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Release [108B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Release
Fetched 1058B in 2s (433B/s)
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz)  404 Not Found
Reading Package Lists... Done
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
root@pc12:/home/andrea #

and I read somewhere that I need to use the ubuntu backports and it says on the thread to

ALT+F2, then "gksudo gedit /etc/apt/sources.list". Add:

Code:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main restricted universe multiverse


and remove

Code:

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main restricted universe multiverse


so I pressed alt+F2 and a small window with RUN APPLICATION poped up and i typed gksudo gedit /etc/apt/sources.list pressed ENTER and another window poped up UNTITLED1-gedit...so uhmm do I add  deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main restricted universe multiverse after typing gksudo gedit /etc/apt/sources.list? DO I run it in terminal window?

I'd really apprecciate your help and thank you very much in advance.

---

### Post by ericsp on 2005-09-29
Hi,

the file /etc/apt/sources.list contains a list with all the repositories that you use with apt-get (commandline) or synaptic (under X). The command that you describe adds another repository to your list. After that, you have to run from the command line: sudo apt-get update or you have to start synaptic (System - Administration - Synaptic Package Manager) and press the reload button. (I am using Ubuntu with Gnome - If you cannot find it, type from the command line: sudo synaptic )
This will 'activate' your changes. After this, you can install packages with apt-get install [package-name] or via selecting the relevant package under synaptic. If you are a newbie, I would suggest starting with synaptic first, to get an idea what is available. Synaptic does have an option to add repositories to the sources.list under Settings - Repositories. Choose "Add - Custom" Then paste the line with the repository into the field and add the repository. Reload as described above, etc.

Hope this helps

Eric

---

### Post by Leif on 2005-09-29
[QUOTE=Struck]
so I pressed alt+F2 and a small window with RUN APPLICATION poped up and i typed gksudo gedit /etc/apt/sources.list pressed ENTER and another window poped up UNTITLED1-gedit...so uhmm do I add  deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main restricted universe multiverse after typing gksudo gedit /etc/apt/sources.list? DO I run it in terminal window?
I'd really apprecciate your help and thank you very much in advance.[/QUOTE]

this doesn't work for me either. instead of doing alt+f2, open a terminal, enter sudo gedit /etc/apt/sources.list, and do the rest as explained above.

---

### Post by dcstar on 2005-10-01
[QUOTE=numberexhaust]Hey guys, don't you think someone should add this to the ubuntuguide?  I was setting up a new machine today and was unaware of this, and seeing as how I use the guide for convenience, I was very frustrated.
It's a very simple edit, I'd be willing to do it as well.[/QUOTE]
This is exactly the sort of issue that gives Linux a bad name in the "non-geek" community.
Some technical change is made - and it doesn't matter for whatever reason - yet the documentation that "normal" people **rely** on to be able to use the full capabilities and features that may be available isn't updated to reflect the changes.
Using basic Release Management practices should have had the documented "unofficial" sources still available until the various available documentation was updated.

---

### Post by Jonathan2007 on 2005-10-01
[QUOTE=almarag]"samba idn what you're talking about"
Sorry, samba is another problem... not have to do with backports.
Many thanks for your answer.
Bye.[/QUOTE]
Actually I have a feeling that backports may be related to the samba problem. If you don't know about the samba problem please look at [this]("http://ubuntuforums.org/showthread.php?p=369116") thread. One or 2 people said commenting out backports worked for them but it didn't for me and some others so if you could shed any light on if this is a backports or another problem or if you know how to fix it I would greatly appreciate it.

---

### Post by jdong on 2005-10-01
Ok, thanks -- haven't seen that thread yet. Either way, mirrormax is shut down, so for all intents and purposes those packages do not exist anymore.

---

### Post by Omnios on 2005-10-01
I havent changed backports for months this is what I have im assumming there rolled uo into one though. Any helop would be apreaciated. 

```
## Backports
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse
```

Thanks

---

### Post by jdong on 2005-10-01
Delete your 2nd and 3rd lines

---

### Post by Wide on 2005-10-01
I did the sources.list update & all went perfectily.
I'm enclosing my sources.list for other to refrence
Please note the commented out notes for file diffrences.
Hope this helps someone;-) 
```
#################################
####Last edit Oct, 1 2005 TJD####
#################################
## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted
## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe
deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted
deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe
deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse
## Old Mirrormax Backports, now dead Oct. 1 2005 
##deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
##New Official Backports
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted

```

---

### Post by stoneguy on 2005-10-01
One hiccup I came across after changing the repositories was that Firefox 1.07 wouldn't install as an upgrade. I had to remove 1.06 and then install 1.07.
Yeah, I knew when I started including those back-alley repositories I could get into trouble. I'm not complaining.

---

### Post by joshuapurcell on 2005-10-01
[QUOTE=dcstar]This is exactly the sort of issue that gives Linux a bad name in the "non-geek" community.
Some technical change is made - and it doesn't matter for whatever reason - yet the documentation that "normal" people **rely** on to be able to use the full capabilities and features that may be available isn't updated to reflect the changes.
Using basic Release Management practices should have had the documented "unofficial" sources still available until the various available documentation was updated.[/QUOTE]
The ubuntu guide maintainer may not be in constant contact with the people who decide what happens with the repositories, and I can guarantee he doesn't have constant contact with the developers of each piece of software he has listed on his site. Think about it for a sec... community-based projects can't work the way you are demanding this work. The forum is a central place for everyone to get information, and chances are the guy who maintains ubuntuguide.org is in the same boat as you and me on this.

Besides, this type of change is simple to fix, and it isn't anything that would hose your system or something if you didn't happen to come across this thread and find out what was going on.

---

### Post by dcstar on 2005-10-01
[QUOTE=joshuapurcell]The ubuntu guide maintainer may not be in constant contact with the people who decide what happens with the repositories, and I can guarantee he doesn't have constant contact with the developers of each piece of software he has listed on his site. Think about it for a sec... community-based projects can't work the way you are demanding this work. The forum is a central place for everyone to get information, and chances are the guy who maintains ubuntuguide.org is in the same boat as you and me on this.
Besides, this type of change is simple to fix, and it isn't anything that would hose your system or something if you didn't happen to come across this thread and find out what was going on.[/QUOTE]
The point is that those not fully aware of **all** of the places to look at will have suffered frustration when trying to use the Backports because of the documentation issue.
And while I fully understand that the further away from the Backports project the longer it will take to update that particular information source, surely some mechanism can be put in place so people that refer to resources such as this can be notified of significant changes?
It wouldn't be too difficult for a big message in the Backports FAQ (or whatever) to say something like:
"If you refer to the Backports Project on an external site, please subscribe to the critical-backports-notifications mailing list (or whatever) for any important updates!"
Clowning around with the "you shouldn't use that, it's not up to date, look here" paradigm is one reason why "ordinary" computer users have an issue with using Linux over more centralised (and probably simpler) alternatives.
I was under the impression that part of the Ubuntu concept was trying to make things better in this area?

---

### Post by jdong on 2005-10-01
Documentation gets outdated -- no matter what OS, it's true. (It's not funny how often MS decides to screw around with SMB/CIFS during unrelated security updates, and never every say a word as the Samba team uncovers the change)

This is more of a harmless shutdown -- no drastic functionality is lost, and users get naturally alerted to the situation, as 404 warnings appear during routine updates.



It's the user's responsibility to keep track of repositories being used, and the documentor's responsibility to keep his information up-to-date. To be honest, I'd like to see UbuntuGuide's content merged into the Ubuntu Wiki.

---

### Post by boxerboy on 2005-10-02
[QUOTE=jdong]Documentation gets outdated -- no matter what OS, it's true. (It's not funny how often MS decides to screw around with SMB/CIFS during unrelated security updates, and never every say a word as the Samba team uncovers the change)
This is more of a harmless shutdown -- no drastic functionality is lost, and users get naturally alerted to the situation, as 404 warnings appear during routine updates.
It's the user's responsibility to keep track of repositories being used, and the documentor's responsibility to keep his information up-to-date. To be honest, I'd like to see UbuntuGuide's content merged into the Ubuntu Wiki.[/QUOTE]

personaly i dont think they can merge due to wiki is officail and ubuntuguide.org isnt. dont get me wrong i love ubuntuguide its helped me alot with the repos and some other stuff. about the backports are they good or bad and does the hoary backports still work for breezy or should i find officail breezy backports if out yet. see i hear and read different things on backports and not really sure what to believe.

---

### Post by walterBE on 2005-10-02
[QUOTE=joshuapurcell]The ubuntu guide maintainer may not be in constant contact with the people who decide what happens with the repositories, and I can guarantee he doesn't have constant contact with the developers of each piece of software he has listed on his site. Think about it for a sec... [/QUOTE]
I have send an email tot the maintainer of the guide about this. I let you know so that not everybody is emailing to the maintainer.

---

### Post by jdong on 2005-10-02
[QUOTE=boxerboy]personaly i dont think they can merge due to wiki is officail and ubuntuguide.org isnt. dont get me wrong i love ubuntuguide its helped me alot with the repos and some other stuff. about the backports are they good or bad and does the hoary backports still work for breezy or should i find officail breezy backports if out yet. see i hear and read different things on backports and not really sure what to believe.[/QUOTE]

There's no restriction on Wiki content -- that's all community-contributed. It'd be a simple copy-paste job for anyone with some free time (if licensing permits, of course)

As far as Backports on Breezy, breezy-backports will be open when breezy+1's development branch is open -- not before so.

As far as leaving hoary-backports lines in, that's 100% safe, and the repository will just be a dud since it'd contain 100% outdated packages relative to Breezy.

---

### Post by paulhoy on 2005-10-03
[QUOTE=dcstar]This is exactly the sort of issue that gives Linux a bad name in the "non-geek" community.
Some technical change is made - and it doesn't matter for whatever reason - yet the documentation that "normal" people **rely** on to be able to use the full capabilities and features that may be available isn't updated to reflect the changes.
Using basic Release Management practices should have had the documented "unofficial" sources still available until the various available documentation was updated.[/QUOTE]

And several months later .. they still haven't changed it .. sigh ...

---

### Post by daller on 2005-10-03
About the "sun-j2re1.5"-package...

It's back in the repository - but will it stay?

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main restricted universe multiverse

And to the ones of you, not using Breezy yet - Why not? I've been using it for a month now! - Without any major problems...

---

### Post by pestie on 2005-10-03
Doesn't look like it:
```

# aptitude search j2re
v   j2re1.3                                                               -
v   j2re1.4                                                               -

```
Sorry to bitch so much, folks, but this totally blows. I, too, went looking to the Ubuntu Guide for help today and just wasted a good hour or so pulling my hair out over this. I know, it's the nature of the community effort, but I would have thought there'd be a more prominent notice about things like w32codecs and the Sun JRE disappearing from backports. It's worse that things like Azureus are still there, but with broken dependencies. Even knowing that ubuntuforums.org is the place to go to look for answers, it took me a fair amount of searching before I found this.

---

### Post by jdong on 2005-10-03
I've already made that clear in several ways... the over 10 threads here at the forums where I've explained it... mailing lists... irc on #ubuntu-devel...

I would still offer it if lawyers wouldn't hunt me down for it :)


Azureus stays because it's perfectly valid once you create your own sun-j2re1.5 using java-package and fakeroot.

---

### Post by pestie on 2005-10-03
I think, though, that that's exactly the problem - to get anything done, one has to troll through countless forum postings, mailing lists and IRC channels. Not everyone has the time or desire to do so. I don't so much mind it most of the time, but even I tend to just lurk around the perhiphery of the forum here, and I wouldn't even know where to begin looking for relevant mailing lists, and I don't use IRC.

Anyway, most of this is immaterial. Thanks for letting me know about java-package. I installed it, used it, and it worked. I wrote a little HOWTO and posted it [here](http://www.ubuntuforums.org/showthread.php?p=385185). Hopefully it'll help a few people. That's what the community spirit is all about, right? Heh...

---

### Post by angrykeyboarder on 2005-10-04
[quote=daller]
And to the ones of you, not using Breezy yet - Why not? I've been using it for a month now! - Without any major problems...[/quote]

Cautious maybe?  Different Strokes for different folks?

Heck, there are still people using Warty.......

---

### Post by angrykeyboarder on 2005-10-04
[quote=pestie] ...I wouldn't even know where to begin looking for relevant mailing lists........[/quote]

Come on now, you couldn't even take a guess?

How did you find ubuntuforums.org?

---

### Post by Zalbor on 2005-10-04
I try to install dvdrip, but there are broken dependancies. It needs transcode, which "will not be installed", and when I try to see why I get "transcode: Depends: libgcc1 (>=1:4.0.0-7) but 1:4.0-0pre6ubuntu7 is to be installed"

The version of libgcc1 I need just doesn't exist. I did change my sources.list about the backports. Maybe I need to do something more? This is the file:

```
deb http://gr.archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu hoary main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu/ hoary-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe multiverse

deb http://gr.archive.ubuntu.com/ubuntu/ hoary-updates main restricted universe multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu hoary-updates main restricted universe multiverse

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

deb http://gr.archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted
deb-src http://gr.archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted

deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

---

### Post by pestie on 2005-10-04
[QUOTE=angrykeyboarder]Come on now, you couldn't even take a guess?
How did you find ubuntuforums.org?[/QUOTE]

OK, yes, I could use Google, I could ask on the forums, I could do a lot of things. Apparently I should have been clearer and said that *off the top of my head* I wouldn't even know where to begin looking for relevant mailing lists. Does that help?

Nit-picking aside, this still doesn't address the core of the problem, which is that the open-source world's approach to documentation is seriously lacking. Mailing lists, forums and (god help us) wikis are a sloppy mish-mash of conflicting reports, out-of-date information, and some of the worst writing ever committed to quasi-permanent storage. That's why I've taken to writing a HOWTO now and then when I run up against something that was an ass-ache for me. I'm at least making some effort to help the situation rather than just bitching about it (but I'm not above doing that, either).

---

### Post by tomski on 2005-10-18
[QUOTE=pestie]this still doesn't address the core of the problem, which is that the open-source world's approach to documentation is seriously lacking. Mailing lists, forums and (god help us) wikis are a sloppy mish-mash of conflicting reports, out-of-date information, and some of the worst writing ever committed to quasi-permanent storage. That's why I've taken to writing a HOWTO now and then when I run up against something that was an ass-ache for me. I'm at least making some effort to help the situation rather than just bitching about it (but I'm not above doing that, either).[/QUOTE]


well said

---

### Post by fut21 on 2005-10-18
You could join "the P.L.F ubuntu team" and support them. They want to make mirrors with all the nessesary package you want.

Join them here:
[http://placelibre.ath.cx/keyes/index...pot-plf-ubuntu](http://placelibre.ath.cx/keyes/index...pot-plf-ubuntu)

---

