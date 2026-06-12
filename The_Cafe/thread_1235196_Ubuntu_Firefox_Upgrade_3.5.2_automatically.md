---
title: "Ubuntu Firefox Upgrade 3.5.2 automatically"
date: 2009-08-08
forum: The Cafe
---

### Post by ultimatebuster on 2009-08-08
Just wrote a shell script on upgrading Firefox to the latest version automatically. 
Thought I share it with you guys. 

[Download]("http://thekks.net/410")

:P

Edit: Updated to 3.5.3

---

### Post by Excedio on 2009-08-08
> **ultimatebuster said:**
> Just wrote a shell script on upgrading Firefox to the latest version automatically. 
Thought I share it with you guys. 

[Download]("http://thekks.net/410")

:P


Does it matter what version of Ubuntu I'm running or that I'm running a 64bit machine?

---

### Post by Giant Speck on 2009-08-08
Hmm... firefox-3.5 updated to 3.5.2 automatically on my computer...

---

### Post by speedwell68 on 2009-08-08
I don't wish to rain on anyone's parade here, but doesn't Firefox already update itself?

---

### Post by Giant Speck on 2009-08-08
> **speedwell68 said:**
> I don't wish to rain on anyone's parade here, but doesn't Firefox already update itself?

I'm guessing this for those that want Firefox 3.5.2 and not Shiretoko 3.5.2, if you know what I mean.

---

### Post by speedwell68 on 2009-08-08
> **Giant Speck said:**
> I'm guessing this for those that want Firefox 3.5.2 and not Shiretoko 3.5.2, if you know what I mean.

OK, on my computer I installed the stock Firefox as downloaded from the Mozilla website and those nice people at Mozilla have designed Firefox to update all on it's own.

---

### Post by Excedio on 2009-08-09
> **speedwell68 said:**
> OK, on my computer I installed the stock Firefox as downloaded from the Mozilla website and those nice people at Mozilla have designed Firefox to update all on it's own.


My Firefox was not updating as yours then. Because I have been running 3.0 for a while now.

But now I have a problem. When I upgraded, my Flash player stopped working. When I tried to install the missing plug-in it said "failed."

I tried following [this]("http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml") to no avail. Any help please?

---

### Post by Excedio on 2009-08-09
Thanks anyway guys, but I just fixed it myself. Downloaded the Tar file from Softpedia and dropped the .so file in my /.mozilla/plugin folder.

Success!

---

### Post by ultimatebuster on 2009-08-09
Don't care version.

Tested on Ubuntu 9.04 32bit and 64bit

And yes, these are for people who don't want Shiretoko 3.5.2, which caused a problem for me

---

### Post by aysiu on 2009-08-09
I think if you're going to go the script route, it's better to use UbuntuZilla:
[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

nanotube has put a considerable amount of work into the script to make it work with various scenarios and automatically update you to the latest Firefox. Right now the latest is 3.5.2, but very soon it'll be 3.5.3 and so on.

The critiques I'd make of your script are the same ones [nanotube originally made of my first install-latest-Firefox script back in 2006](http://ubuntuforums.org/showthread.php?t=293301). It will continue even if one of the commands errors out. It doesn't take into account multiple locales (assumes US English). It fetches only what is *currently* the latest Firefox and not perpetually whatever is the latest at future moments. It doesn't try other mirrors if the first download site fails.

I don't mean to demean your efforts any more than nanotube meant to demean mine. But it is best to advise new users to use the best methods available. If you have interest in contributing to UbuntuZilla, I'm sure nanotube could use the help.

For those who do not want to run a script, I have a one-line paste that installs the latest Firefox if you've already downloaded the .tar.bz2:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by steveneddy on 2009-08-09
Just install FF 3.5 with a ppa or add a repo and it will update automatically without a script.

---

### Post by nanotube on 2009-08-09
> **aysiu said:**
> I think if you're going to go the script route, it's better to use UbuntuZilla:
[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)


hi aysiu - thanks for the recommendation :)

just a quick note to update your ubuntuzilla link. due to recent changes at sourceforge, ubuntuzilla.wiki is no longer the location of the script's homepage. instead, just link straight to [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

and, ultimatebuster: indeed, if you are up for it, you're more than welcome to look over ubuntuzilla and suggest (or make) improvements. in particular, probably it would be cool to make it into a gui gtk app - but i just don't have the time to take that on at the moment. :)

---

### Post by BigCityCat on 2009-08-09
I haven't used 3.5 in Kubuntu but it crashes a lot on my windows drive so I am staying away from it till they fix it.

---

### Post by aysiu on 2009-08-09
I've updated the link appropriately. Thanks.

---

### Post by smart ali on 2009-08-09
> Open up Terminal (Applications > Accessories > Terminal) and run the following commands:

   1. cd /tmp
   2. wget "http://download.mozilla.org/?product=firefox-3.5.2&os=linux&lang=en-US"
      Note: Your download link may be different depending on your country and language. I got the link by clicking the download link, canceling  the automatic download, right-clicking the “Your download should automatically begin in a few seconds, but if not, click here” link, and selecting Copy Link Location.
   3. tar xvjf firefox-*.bz2
   4. sudo cp -r firefox /usr/lib/firefox-3.5.2
   5. sudo mv /usr/bin/firefox /usr/bin/firefox.old
   6. sudo ln -s /usr/lib/firefox-3.5.2/firefox /usr/bin/firefox-3.5.2
   7. sudo ln -s /usr/bin/firefox-3.5.2 /usr/bin/firefox

Close Firefox and then reopen. You should now be running Firefox 3.5.2.


I have written that in a terminal

it didn't work?

---

### Post by speedwell68 on 2009-08-09
> **BigCityCat said:**
> I haven't used 3.5 in Kubuntu but it crashes a lot on my windows drive so I am staying away from it till they fix it.

I have heard of a number of people having problems with FF 3.5.x in Windows.  But we have 3 Linux boxes running it here with no problems, me with Ubuntu 9.04, my wife with UNR 9.04 and my mate with OpenSuse 11.1.

---

### Post by abansb on 2009-08-09
I have also tried with no success for some reason I can't get the wget to download the tar file also tried the script but I tried running the firefox3.5.2upgrade.sh also tried ./firefox3.5.2upgrade.sh but still will not run. almost forgot I am running Ubunbtu 8.04.3 with Xubuntu

I am running firefox 3.0.13 would like to upgrade to the newest version 

Thanks 
Tom

---

### Post by ultimatebuster on 2009-08-09
> **abansb said:**
> I have also tried with no success for some reason I can't get the wget to download the tar file also tried the script but I tried running the firefox3.5.2upgrade.sh also tried ./firefox3.5.2upgrade.sh but still will not run. almost forgot I am running Ubunbtu 8.04.3 with Xubuntu

I am running firefox 3.0.13 would like to upgrade to the newest version 

Thanks 
Tom

go for 

```
sh firefox3.5.2upgrade.sh
```

 in the terminal

---

### Post by nanotube on 2009-08-09
> **aysiu said:**
> I've updated the link appropriately. Thanks.

how about the linky from [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox) ? :)

---

### Post by patman0623 on 2009-08-09
OK, guys, noob question: I was playing around with version 3.5 earlier, and left it be after a while. I am now using Shiretoko after the upgrade, and I do not want to use Shiretoko, especially as it is an alpha release.

How can I get the *standard* 3.5 release of FF on my computer?

---

### Post by abansb on 2009-08-09
Thanks that did it I am also a newbie to Ubuntu

edit: script worked great now using FF 3.5.2 

 
> **ultimatebuster said:**
> go for 

```
sh firefox3.5.2upgrade.sh
``` in the terminal

---

### Post by Giant Speck on 2009-08-09
> **patman0623 said:**
> OK, guys, noob question: I was playing around with version 3.5 earlier, and left it be after a while. I am now using Shiretoko after the upgrade, and I do not want to use Shiretoko, especially as it is an alpha release.

How can I get the *standard* 3.5 release of FF on my computer?

Shiretoko 3.5.2 is not an alpha release.   It's essentially the same thing as Firefox 3.5.2.  Namoroka is the alpha release, version 3.6 alpha 1.

---

### Post by patman0623 on 2009-08-09
> **Giant Speck said:**
> Shiretoko 3.5.2 is not an alpha release.   It's essentially the same thing as Firefox 3.5.2.  Namoroka is the alpha release, version 3.6 alpha 1.Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.3pre) Gecko/20090808 Ubuntu/9.04 (jaunty) Shiretoko/3.5.3pre

I assumed "pre" meant alpha of some sort. And, why does it download Shiretoko, it's interface is ugly, and I don't like it (so sue me).

---

### Post by nbv4 on 2009-08-09
yeah, same here. I thought the pre thing meant it wasn't the same as regular 3.5.2

---

### Post by aysiu on 2009-08-09
> **nanotube said:**
> how about the linky from [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox) ? :)
Fixed also.

---

### Post by ultimatebuster on 2009-08-10
Having 2 separate browser which are both Firefox is just annoying, and typing all the instructions in the terminal is just irritating. 

Why can't people at ubuntu just upgrade all the firefoxes to 3.5 via Software update?

---

### Post by aysiu on 2009-08-10
> **ultimatebuster said:**
> Having 2 separate browser which are both Firefox is just annoying, You don't have to launch both. You make the newer one your default and just use that. > and typing all the instructions in the terminal is just irritating. It's one line you copy and paste **with your mouse**. No typing involved at all.

> Why can't people at ubuntu just upgrade all the firefoxes to 3.5 via Software update? Because that's not Ubuntu's release model. Even though power users make up the bulk of its userbase *right now*, Ubuntu is really targeted at average users, who really don't care about cutting edge software. Most of them don't update their software more than every six months... sometimes even only once a year or two.

Other Linux distros like PCLinuxOS, Debian experimental, or Arch Linux are targeted at power users, and so they will put in new software the minute it comes out. If you like a rolling release model, you may prefer one of those. Unless you like to really get your hands dirty, I'd recommend Debian Unstable or PCLinuxOS over Arch.

---

### Post by FuturePilot on 2009-08-10
> **ultimatebuster said:**
> 

Why can't people at ubuntu just upgrade all the firefoxes to 3.5 via Software update?

What do you mean? Firefox 3.5 is in the repos. It's not going to replace 3.0.x but it's there.

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.2) Gecko/20090803 Ubuntu/9.04 (jaunty) Firefox/3.5.2

---

### Post by ultimatebuster on 2009-08-10
> **aysiu said:**
> You don't have to launch both. You make the newer one your default and just use that. 

Doesn't work. Everything will still launch in Firefox 3.0 (for me and another person)

> **aysiu said:**
> 
 It's one line you copy and paste **with your mouse**. No typing involved at all.

True, but you still have to press at least 5 buttons ;)

> **aysiu said:**
> 
 Because that's not Ubuntu's release model. Even though power users make up the bulk of its userbase *right now*, Ubuntu is really targeted at average users, who really don't care about cutting edge software. Most of them don't update their software more than every six months... sometimes even only once a year or two.

Other Linux distros like PCLinuxOS, Debian experimental, or Arch Linux are targeted at power users, and so they will put in new software the minute it comes out.
They should have an option to upgrade to newer releases, or allow the users to do it via an installer or something (like win)

---

### Post by aysiu on 2009-08-10
> **ultimatebuster said:**
> Doesn't work. Everything will still launch in Firefox 3.0 (for me and another person) Has worked fine for most people.

If you want to stick with Ubuntu, I can help you troubleshoot the issue.

> True, but you still have to press at least 5 buttons ;) Well, at least you're keeping your sense of humor about it. That's good.

> They should have an option to upgrade to newer releases, or allow the users to do it via an installer or something (like win) It's not like Windows, though. Windows is designed to be a virtually empty platform that gets updated every few years. Then third-party applications have to make themselves work on Windows, and it's up to the user or the third-party application to keep track of updates to programs.

The downside to that model (mainly for average users) is that it's up to the user or the program(s) to keep track of updates to programs.

The upside to that model (mainly for power users) is that the latest software can almost always be installed easily.

Ubuntu, and most Linux distributions, use a centralized software package management model, whereby the operating system isn't an empty platform for third-party software to be installed on, but the software itself is incorporated into the platform and tested for the platform, even if it's not installed by default. Since all the software uses shared libraries, for stability's sake, it makes sense to update all application versions together instead of one at a time.

Linux distributions that use a rolling release model have the same problem, except they update *everything* at once (not every six months or every year), which has the upside (mainly for power users) that the latest software can almost always be installed easily but the downside (mainly for average users) that the system is highly unstable.

I would say just use what works for you. If you like Windows, use Windows (I'm no hater). If you like Linux but don't dig Ubuntu's six-month release schedule, check out some rolling release distros Linux PCLinuxOS or Debian experimental or unstable.

---

### Post by Giant Speck on 2009-08-10
> **FuturePilot said:**
> What do you mean? Firefox 3.5 is in the repos. It's not going to replace 3.0.x but it's there.

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.2) Gecko/20090803 Ubuntu/9.04 (jaunty) Firefox/3.5.2

Wait.  How did you get Firefox 3.5 from the repos?  I installed it from the repos and it identifies itself as Shiretoko...

---

### Post by Mister LinOx on 2009-08-10
Yeah. I really don't like Shiretoko. Doesn't feel right. :P Anyone else like the way Firefox looks on Windows better than Linux or is that just me?

---

### Post by ultimatebuster on 2009-08-10
> **Mister LinOx said:**
> Yeah. I really don't like Shiretoko. Doesn't feel right. :P Anyone else like the way Firefox looks on Windows better than Linux or is that just me?

This sh script basically upgrades the existing firefox (i.e. the firefox icon from the menu, which will llink to 3.0.x) to 3.5.2. 

No extra Shiretoko or whatever, just simple firefox :)

> It's not like Windows, though. Windows is designed to be a virtually empty platform that gets updated every few years. Then third-party applications have to make themselves work on Windows, and it's up to the user or the third-party application to keep track of updates to programs.

The downside to that model (mainly for average users) is that it's up to the user or the program(s) to keep track of updates to programs.

The upside to that model (mainly for power users) is that the latest software can almost always be installed easily.

Ubuntu, and most Linux distributions, use a centralized software package management model, whereby the operating system isn't an empty platform for third-party software to be installed on, but the software itself is incorporated into the platform and tested for the platform, even if it's not installed by default. Since all the software uses shared libraries, for stability's sake, it makes sense to update all application versions together instead of one at a time.

Linux distributions that use a rolling release model have the same problem, except they update everything at once (not every six months or every year), which has the upside (mainly for power users) that the latest software can almost always be installed easily but the downside (mainly for average users) that the system is highly unstable.

I would say just use what works for you. If you like Windows, use Windows (I'm no hater). If you like Linux but don't dig Ubuntu's six-month release schedule, check out some rolling release distros Linux PCLinuxOS or Debian experimental or unstable.

I mainly uses Windows, but Ubuntu is a nice bonus for me. You know, people who wants to sneak on your computer don't usually look at your browsing history on a platform they don't know how to use. ;)

[COLOR="Cyan"][SIZE="1"]No I'm totally joking, Just saying[/SIZE][/COLOR]

---

### Post by DougieFresh4U on 2009-08-10
Was nice to update 'Firefox' today (Karmic-64 bit) and have it rid itself of the 'Shiretoko' name!!
Now maybe a few can 'quit' complaining of it not  identifying itself correctly. :lolflag:

---

### Post by winotree on 2009-09-07
With less than two years computer experience and less than two months Xubuntu experience, I found this method [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page) straight-forward: it was clearly explained and even offered to perform updates for me.  If or when Ubuntu offers a current version of Firefox with updates or if I change my mind about using this version, I've got a CD backup of 3.0.13.  What's not to like?  ;)

---

### Post by ultimatebuster on 2009-09-15
Updated to 3.5.3 today! :D

---

### Post by merlin666 on 2009-09-18
> **ultimatebuster said:**
> Updated to 3.5.3 today! :D

How did you do that?

---

### Post by aysiu on 2009-09-18
> **merlin666 said:**
> How did you do that?
You can paste one command into the terminal after downloading the .tar.bz2 file:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Or you can use a script that will automatically detect your architecture and download the latest Firefox for you automatically (and also check for updates... ask your for locale, etc.):
[http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net)

The script from the first post of this thread seems to have the worst of both of these methods. If you're going to paste in a bunch of single commands, you might as well do them all at once instead of creating a shell script (extra step). So go with the first method. If you prefer a shell script, at least get one that's sophisticated and can properly error out or check the integrity of downloads. So go with the second method.

---

### Post by NormanFLinux on 2009-09-18
Ubuntuzilla does it automatically for Firefox and Thunderbird. Appreciate the shell script though!

---

