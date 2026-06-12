---
title: "do-release-upgrade -- Is it necessary?"
date: 2016-03-27
forum: Ubuntu, Linux and OS Chat
---

### Post by neu5eeCh on 2016-03-27
So, I just recently upgraded my own system (Kubuntu) and that of my family's (Ubuntu), 5 systems in all, from 15.04 to 15.10. 

And now? USB DVDRW drives are unusable --- _on any of them_ and with _either_ of my USB drives. So, there seems to be a **major** bug or regression. The question I ask myself: Is this worth sorting out? 16.04 is going to be released soon and in less than a month's time every answer will be: *Upgrade to 16.04*.

Trouble is, my kids do need to use the optical drives. So I was thinking about updating to 16.04 now. I ran across [this]("http://serverfault.com/questions/592007/do-release-upgrade-d-ubuntu-13-10-14-04-failing"):

>  This answer is almost off-topic, but something what I've been wondering.

  Every time I upgrade Debian or some of its derivates, such as Ubuntu or Mint, I just do
  sed -i -e 's/olddistroname/newdistroname/g' /etc/apt/sources.list
apt-get update && apt-get dist-upgrade
reboot
  And then I enjoy my new, just released distro. 

  This has worked for me since forever. All this do-release-upgrade hoopla makes me a very confused, angry, old-beard. 
  So my sub-question is: what is the benefit of those do-release-upgrade  style commands if they don't even work? What's wrong with the proven,  working way? (apt-get versus aptitude is another fight I'm just trying  to digest)
     


Kubuntu says to use the command: ```
**kubuntu-devel-release-upgrade**
``` And I'm wondering how this is any different than simply changing the repositories (and momentarily disabling 3rd party repositories).

Same with Ubuntu. (I assume Ubuntu prefers *do-release-upgrade*). Just go ahead and use do-release-upgrade (to a Beta)? Any recommendations? Experience?

---

### Post by Bucky Ball on 2016-03-27
As for 16.04 LTS: Expect breakage. It is common in the last month and not a good idea to go there if you are needing stable machines.

Rather than going there, as it seems your more urgent issue is actually getting the USB DVD drives to work, if you haven't already I'd suggest you concentrate on posting a new thread about the actual issue and seeing if any of us can help you with it.

Your other option is to do a clean install of 14.04 LTS which is supported until 2019 and then upgrade to 16.04 LTS anytime before then. (LTS releases upgrade directly to LTS releases.)

PS: Please acknowledge the original poster when you are quoting other users with name and link to original thread would be good, not just from here, but anywhere. Thanks.

---

### Post by neu5eeCh on 2016-03-27
Thanks Bucky Ball,

As for acknowledging the original --- I did. Link was provided. See original post.

I also have already posted a support thread:

[http://ubuntuforums.org/showthread.php?t=2318518](http://ubuntuforums.org/showthread.php?t=2318518)

I checked in with Askubuntu:

[URL="http://askubuntu.com/questions/750586/after-upgrade-from-15-04-15-10-usb-dvd-drives-no-longer-recognized-by-ubuntu"]http://askubuntu.com/questions/750586/after-upgrade-from-15-04-15-10-usb-dvd-drives-no-longer-recognized-by-ubuntu
[/URL]
And commented on a pre-existing bug:

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/646293](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/646293)   

So yeah, this isn't my first day on the job. And based on that experience, I get the feeling the devs have pretty much decided they can live with this bug. So, if I'm already dealing with breakage, how 'bout my original question?

---

### Post by grahammechanical on 2016-03-27
If you look at the wiki on upgrading you will see that the command do-release-upgrade is applicable to server installs. With a server edition we only have the command line. But with a desktop edition we can upgrade to the next release of Ubuntu using Update Manager.

Also, the sed command that you quoted changes the URLs in the sources.list file. That is all it does. Unlike update manager it does not run upgrade scripts. After running that command we have to run update/upgrade/dist-upgrade to make the change over. And who knows what incompatibility problems we may get.

I will use that sed command during the first week after 16.04 is released to convert an install of 16.04 into an install of 16.10 development version. As each version of Ubuntu is built on the code of the previous version the code difference between the released version and the development version is not so great until 2 or 3 weeks after development has started. Not much risk during the first week or two of the development cycle.

Personally, I would not use that sed command or do-release-upgrade to upgrade one released version of Ubuntu to the next released version. Not on a desktop version of Ubuntu/Kubuntu.

Oh, by the way, if you run do-release-upgrade -d you will get shifted onto the development version whether you want it or not. And then you will be stuck until the development version becomes the released version.

[https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)

> Just go ahead and use do-release-upgrade (to a Beta)?

It does not work like that, The Beta is the development version. So, do-release-upgrade from 14.04 will try to shift you onto 15.10. But from 15.10 it will come up empty until 16.04 is released.

Regards.

---

### Post by neu5eeCh on 2016-03-27
Thanks for that Grahammechanical. I usually prefer to do everything by command line. So... I've used do-release-upgrade for the last three release cycles. No problems.

However, your opinion is just what I was looking for.

By the sound of it, your advice would be to wait until the official release, then use the update manager.

---

### Post by neu5eeCh on 2016-03-27
Okay. Just reporting back. I took the advice recommending the Update Manger rather than the command line. 

Since my system was already suffering "breakage", I decided to upgrade to 16.04 BETA.

Went to the library (fiber optic) and downloaded the upgrade in 7 minutes flat. The Update Manager locked up. Had to logout to kill it. Continued the installation via the command line (so much for that...) -- sudo dpkg --configure -a. Based on this experience, I'm of the mind that the command line is in fact a better way to upgrade a system. 

I'm typing this on 16.04. There are some minor issues -- my beloved radiotray no longer works. I'm also getting [this bug]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1558331") as regards my PPAs. But... this isn't the first BETA I've used. I expect most of this will be cleared up within the next month. 

Most importantly: upgrading to 16.04 did _not_ fix the DVDRW bug. I've reported it [here]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/1562589"). We'll see if it gets any love.

---

