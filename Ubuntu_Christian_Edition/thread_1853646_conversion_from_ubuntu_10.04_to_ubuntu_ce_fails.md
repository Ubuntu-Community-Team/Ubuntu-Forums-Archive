---
title: "conversion from ubuntu 10.04 to ubuntu ce fails"
date: 2011-10-02
forum: Ubuntu Christian Edition
---

### Post by rss0213 on 2011-10-02
Hi.  Ubuntu newbie here.  Thankfully I ran across the CE flavor while researching a problem running tinyproxy and dansguardian to filter web content.  This is a new machine that I built for my kids, but I am still a Linux novice.  Anyway, I decided to convert to CE because the process looked so easy on the installation page ([http://ubuntuce.com/convert.htm](http://ubuntuce.com/convert.htm)), but when I run the wget command, it looks like I'm missing a couple dependencies.  Tried to install one of them, and then found another missing dependency.  Check out the messages below.  What I want to know is... do I just have to keep going through all these until I've installed all the dependencies, or is there a better way?  Seems like I should have everything needed since I'm on 10.04...

[I]The following packages have unmet dependencies:
  ubuntu-ce: Depends: xiphos but it is not going to be installed
             Depends: wine-christian-repos but it is not going to be installed
E: Broken packages

stafford@stafford-desktop:/etc$ sudo apt-get xiphos
E: Invalid operation xiphos
stafford@stafford-desktop:/etc$ sudo apt-get install xiphos
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xiphos: Depends: xulrunner-1.9.1 but it is not installable
E: Broken packages
[/I]

---

### Post by nmhenry71655 on 2011-10-08
I'm currently downloading Lucid to run in a Virtual Machine. I'll see if I can produce the same error. I will let you know.

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-09
> **rss0213 said:**
> [I]
stafford@stafford-desktop:/etc$ sudo apt-get install xiphos
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. [B]This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.[/B]
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xiphos: Depends: xulrunner-1.9.1 but it is not installable
E: Broken packages
[/I]


from their website it looks like development ended back with 9.10, and you have 10.04, so it is likely that you downgraded to an unstable variant of a no longer developed version of Linux.

I run Xbuntu 11, and I had no problems getting Xiphos on my computer.  I also run another machine with the regular Ubuntu 11 and I've been runnig Xiphos on their just fine for over a year.

---

### Post by nmhenry71655 on 2011-10-09
Ok,

Downloaded Lucid and installed it in a Virtual Machine. I ran the command located here:

[http://ubuntuforums.org/showthread.php?t=1492885]("http://ubuntuforums.org/showthread.php?t=1492885")

Mine ran great on a clean install. Had some issues with the Update-Manager but I think it is unrelated to this issue.

The wine that is used for Ubuntu CE is 1.0.1. I think you have a later version installed. So the first task is to remove the later versions and let the ubuntu-ce package pull in the wine it needs.

So first let's uninstall all Wine related packages.

Click on Application->Accessories->Terminal.

Then enter this at the prompt:

```
sudo apt-get --purge remove wine
```

Now for your Xiphos problem, the xulrunner on my system is 1.9.1. Don't know what it is on yours but remove it and again let the ubuntu-ce package pull in what it needs.

Run this command at the prompt.

```
sudo apt-get --purge remove xulrunner
```

This should remove both from your system.

Then follow the instructions at 

[http://ubuntuforums.org/showthread.php?t=1492885]("http://ubuntuforums.org/showthread.php?t=1492885")

and let us know how it went.

Shalom

---

### Post by jonathonblake on 2011-10-28
> **rss0213 said:**
> 
[I]The following packages have unmet dependencies:
  ubuntu-ce: Depends: xiphos but it is not going to be installed
             Depends: wine-christian-repos but it is not going to be installed
E: Broken packages

You can safely ignore *Wine-Christian Repos*.  It provides a "simple" way to install some gratis Christian software that requires Wine.

Maybe a shell script that provides the same functionality should be provided. Something along the lines of *e-Sword_installer*, available from  [http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042) except it installs the software that Wine-Christian Repos installs. Probably would also be a good idea to revisit what should be included, prior to writing a shell script to install the various programs.

> The following packages have unmet dependencies:
  xiphos: Depends: xulrunner-1.9.1 but it is not installable
E: Broken packages


That bug should have been fixed in the last release of Xiphos.  I don't if the version of Xiphos in the Ubuntu repository is the current version, or not.

jonathon

---

