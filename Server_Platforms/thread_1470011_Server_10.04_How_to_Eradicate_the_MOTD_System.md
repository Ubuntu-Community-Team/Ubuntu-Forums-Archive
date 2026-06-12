---
title: "Server 10.04: How to Eradicate the MOTD System?"
date: 2010-05-02
forum: Server Platforms
---

### Post by Bob P on 2010-05-02
Is anyone else bothered by the garbage processing that is being forced upon the user via the Message of the Day?  

I want to completely remove the automated MOTD system and all of its components.

I have just installed Ubuntu Server 10.04.  I don't like the MOTD display.  It presents a lot of useless information that I don't want to see, and it causes an unacceptable delay between the time that a user logs on and the time that he gets to the bash prompt. 

Looking into the reason for the logon delay, I&#8217;ve learned a few interesting things.  It seems that the MOTD system is causing my server to perform all sorts of background tasks that I don&#8217;t want it to perform.  The MOTD system installs a cron job that runs in the background on the server every 10 minutes.  I don't want to see the system's text output every time that I log on (especially the ad for landscape and canonical.com), and running the unnecessary cron job every 10 minutes wastes CPU cycles.  Even worse, the logon delay can be HUGE if your system is firewalled, because the MOTD system attempts to make surreptitious calls to canonical without first obtaining permission from the administrator!  My firewall thwarts these attempts, thereby causing a delay in the display of the MOTD.  Others have experienced the same problem:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/522452](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/522452)

It looks like this bug may not have been fixed, because my server is VERY SLUGGISH after logging on, with an unacceptable delay in getting to the command prompt.  I found the following entries in my firewall log from last night that I find very concerning: (my actual non-routeable IP addresses have been changed)

```
May  1 21:13:35 firewall Shorewall:loc2net:REJECT:IN=eth1 OUT=eth0  SRC=192.168.0.55 DST=91.189.88.40 LEN=60 TOS=0x00 TTL=63 ID=29618 DF  PROTO=TCP SPT=41572 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0
May  1 21:13:35 firewall Shorewall:loc2net:REJECT:IN=eth1 OUT=eth0  SRC=192.168.0.55 DST=91.189.88.40 LEN=60 TOS=0x00 TTL=63 ID=29618 DF  PROTO=TCP SPT=41572 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0
May  1 21:13:35 firewall Shorewall:loc2net:REJECT:IN=eth1 OUT=eth0  SRC=192.168.0.55 DST=91.189.88.40 LEN=60 TOS=0x00 TTL=63 ID=29618 DF  PROTO=TCP SPT=41572 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0
May  1 21:13:35 firewall Shorewall:loc2net:REJECT:IN=eth1 OUT=eth0  SRC=192.168.0.55 DST=91.189.88.40 LEN=60 TOS=0x00 TTL=63 ID=29618 DF  PROTO=TCP SPT=41572 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0
May  1 21:13:35 firewall Shorewall:loc2net:REJECT:IN=eth1 OUT=eth0  SRC=192.168.0.55 DST=91.189.88.40 LEN=60 TOS=0x00 TTL=63 ID=29618 DF  PROTO=TCP SPT=41572 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0
May  1 21:13:35 firewall Shorewall:loc2net:REJECT:IN=eth1 OUT=eth0  SRC=192.168.0.55 DST=91.189.88.40 LEN=60 TOS=0x00 TTL=63 ID=29618 DF  PROTO=TCP SPT=41572 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0
May  1 21:13:35 firewall Shorewall:loc2net:REJECT:IN=eth1 OUT=eth0  SRC=192.168.0.55 DST=91.189.88.40 LEN=60 TOS=0x00 TTL=63 ID=29618 DF  PROTO=TCP SPT=41572 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0
May  1 21:13:35 firewall Shorewall:loc2net:REJECT:IN=eth1 OUT=eth0  SRC=192.168.0.55 DST=91.189.88.40 LEN=60 TOS=0x00 TTL=63 ID=29618 DF  PROTO=TCP SPT=41572 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0
```I don&#8217;t know why my server was trying to call 91.189.88.40.  I never authorized such action.  Here are the results of my Reverse DNS lookup:

```
91.189.88.40 resolves to
"drescher.canonical.com"
Top Level Domain: "canonical.com"
Country IP Address: UNITED KINGDOM
```I just don't like the idea of a server automatically performing tasks that the sysadmin never intended to be performed.  In addition to this being philosophically wrong, the MOTD system wastes resources by performing an unnecessary cron job every 10 minutes.

I would like to completely eliminate all of the functionality that is provided by Ubuntu Server&#8217;s MOTD system.  I would like to configure my server so that NO ADDITIONAL CODE of any kind is executed between the time that the user logs on and the time that the bash prompt becomes available.  Unfortunately, this turns out to be no easy task, as the update-motd system seems to be embedded in Server 10.04 and non-removable. I've searched quite a bit for a solution on this, and it doesn't seem to be an easy fix:


1.  Dustin Kirkland at Canonical seems to be the person who created the system.  I've read his documentation page on UpdateMOTD at [https://wiki.ubuntu.com/UpdateMotd](https://wiki.ubuntu.com/UpdateMotd).  Unfortunately the page tells you how to install the package but not how to remove it.

2.  His page suggests installing via the command "apt-get install update-motd".  Naturally, I've tried "apt-get remove update-motd" to get rid of the package.  Unfortunately doing this results in a "package is not installed" error.  So it seems that the functionality that is enabled by default in the Ubuntu Server 10.04 install is no longer installed via a removable package. 

3.  I've tried editing the /etc/pam.d/login and "/etc/pam.d/sshd files to comment out the line that says:
```
session   optional   pam_motd.so
```and then running "update-motd".  Unfortunately, this creates some problems.  I am now receiving erroneous display output when I log out.  The screen goes blank, and a full page of text (perhaps the text being displayed on another open console?) flashes briefly on screen, and then the blank screen displays the following message prior to logging me out:

```
"Sessions still open, not unmounting"
```I'd really like to eradicate the entire MOTD functionality on my server.   Because of this problem I've performed a CentOS 5.4 server install as proof of concept.  It was clean, with none of  these shennanigans.  Although I've been using Ubuntu desktops for several years, this kind of behavior is a deal-breaker -- especially on a server. 

If there is a simple solution to this problem, I'd love to hear it.  OTOH, if there is no easy fix, this looks like the end of Ubuntu for me.  I'd really prefer not to be forced to migrate to another distribution if I can avoid it.

Any insights would be sincerely appreciated.

PS - Here is a similar thread:

[http://ubuntuforums.org/showthread.php?t=1449020&highlight=motd+pam](http://ubuntuforums.org/showthread.php?t=1449020&highlight=motd+pam)

---

### Post by CharlesA on 2010-05-02
I don't know if there is a way to get rid of it. 

I haven't noticed any sluggishness from the server I have running 10.04, even when logging in with SSH (and I've got 2 VMs running).

I checked my system for update-manager by using this command:

```
aptitude show update-manager
```

I don't have it installed.

If you want to remove the message, check here: [http://www.microswamp.com/tech-notes/linux/127-ubuntu-ssh-change-welcome-message](http://www.microswamp.com/tech-notes/linux/127-ubuntu-ssh-change-welcome-message)

---

### Post by Bob P on 2010-05-02
Thanks for your input.

If you're not experiencing sluggishness, then maybe you have a much faster box than I have.  :p    Is your server firewalled?

Just to clarify, the only "sluggishness" that I've noticed occurs during the log-on process.  There isn't any sluggishness in server performance afterward.  The sluggishness I'm describing is a delay of several seconds between the time that the logon password is entered and the display of the MOTD message onscreen.  There is no lag between the display of the MOTD message and the user's acquisition of the command prompt. 

In my case, the network is behind a firewall that stops the server from communicating with the outside world.  Presumably the packet rejection implemented by the firewall is what's causing the sluggishness, as the server repeatedly tries to contact Canonical during the user's logon and fails.

---

### Post by Bob P on 2010-05-02
> **CharlesA said:**
> 
...I checked my system for update-manager by using this command:

```
aptitude show update-manager
```I don't have it installed.
It looks like your results parallel mine.  I have the functionality, but I also do not have the update-manager installed.  It looks like the functionality we're describing is something that is embedded into the distribution;  in other words, its something that cannot be removed.  :confused:

> If you want to remove the message, check here: [http://www.microswamp.com/tech-notes/linux/127-ubuntu-ssh-change-welcome-message](http://www.microswamp.com/tech-notes/linux/127-ubuntu-ssh-change-welcome-message)Thanks.  I actually found that page when I was Googling for information.  I'd like to go one step farther than stopping the information from being presented to a user.  I'd like to stop the processes that generates the information in the first place.

Thanks again.

---

### Post by PetruM on 2010-05-02
> **Bob P said:**
> I don&#8217;t know why my server was trying to call 91.189.88.40.  I never authorized such action.  Here are the results of my Reverse DNS lookup:

```
91.189.88.40 resolves to
"drescher.canonical.com"
Top Level Domain: "canonical.com"
Country IP Address: UNITED KINGDOM
```

That points to the ubuntu archive. The MOTD screen often shows how many packages require updating, so that call is for updating purposes only, I guess. :roll:

---

### Post by CharlesA on 2010-05-02
My machine is firewalled. Could be the reason I am not having any sluggishness is that my machine is faster I suppose.

I haven't limited any outbound connections, but I have blocked all inbounds that aren't already established or being set to accept.

---

### Post by Bob P on 2010-05-02
> **PetruM said:**
> That points to the ubuntu archive. The MOTD screen often shows how many packages require updating, so that call is for updating purposes only, I guess. :roll:
From a security standpoint, making that assumption requires quite a leap of faith:  It requires you to assume that because the software is making an undisclosed update check, it is also not performing any other undisclosed activities.  There is no reason to believe that a machine performing undisclosed activities is performing only innocuous undisclosed activities.  

The fact that the system is initiating undisclosed communication with the outside world, every time that a user logs on, is troublesome.  The fact that it is initiating undisclosed communication with the outside world during every logon, under the guise of performing an update, doesn't inspire confidence.  Any well designed Trojan Horse would behave in exactly this way -- by hiding it's improper activities under the guise of a proper activity.  If this were happening on a Windows system, everyone would be up in arms.  The only difference in this instance is that my machine is attempting to deliver my information to a different billionaire.

I don't want my server to initiate any contact with the outside world in the absence of my explicit instructions to do so.  I would really like to find a way to eradicate such behavior.  In this case, I was only saved because I had an extrusion detection system in place to identify and stop this kind of activity.

Eradicating this sort of behavior should be EASY to do in any server distribution.  I find the difficulty in eradicating this type of unauthorized behavior to be particularly troublesome.  From a security standpoint, this raises the question of whether Ubuntu Server 10.04 is an insecure system that is compromised by design.

---

### Post by tgalati4 on 2010-05-02
Well, you could just switch to plain-vanilla Debian.  I presume the update-motd code is open source.  So you can read through it and comment on it's actual programming.  You can also edit the login scripts so that motd is not executed.  It shouldn't be difficult to follow boot up scripts and intercept the code (delete or rename the scripts) to your liking.

Monitized motd is a small price to pay for Ubuntu's contribution in growing the Linux user base world wide.

---

### Post by Bob P on 2010-05-02
> **tgalati4 said:**
> ...  I presume the update-motd code is open source.  So you can read through it and comment on it's actual programming.  You can also edit the login scripts so that motd is not executed.  It shouldn't be difficult to follow boot up scripts and intercept the code (delete or rename the scripts) to your liking.
As I mentioned in my earlier posts, I have already done that.  Modifying the offensive scripts causes problems in its own right.  Its not a viable option.  Nor should it be a viable option.

Make no mistake about it -- Ubuntu was phoning home to Canonical every time that a user logged onto the system, and it was deigned to do this without the user's knowledge or consent.  Eradicating the behavior is particularly difficult, as there is no switch to turn the "feature" on or off.  In fact, the functions responsible for the activity have been embedded into the system as a non-removable package, and their functionality has been purposefully obfuscated in order to prevent the user from disabling them.

So it would seem that you don't have a problem with the situation.  That's fine, but I think that for people who do have a problem with the situation, your recommended solution isn't reasonable.  Nobody should have to reverse engineer a server distribution from source code in order to fix a gaping security hole.  The bug fixing process should have already taken care of that.  Since the bug report has been closed with the status of "fixed", its evident that we're not dealing with a bug -- if this problem is persistent then we're dealing with a feature that cannot be disabled.  There's a word for this: spyware.


> Monitized motd is a small price to pay for Ubuntu's  contribution in growing the Linux user base world wide.The concept of "monetizing" the MOTD screen is not really the issue, even though I think that many people would find such SPAM to be   objectionable in its own right.

The problem isn't something as innocuous as showing an ad to you on-screen without your consent -- the problem is that information is being transmitted from your computer to someone else's computer without without your knowledge or consent.   This OS is performing unauthorized transactions  behind the back of the sysadmin, and the sysadmin is left without the  ability to put an end to it, short of pulling the plug and installing  different software.  It would be a totally different situation if Ubuntu  disclosed this kind of activity prior to a system install, and you had  the opportunity to consent to the terms and conditions or reject them.   As it stands now, this kind of activity is taking place behind your  back.  That's dishonest.

Complacency about the concept of a "small price to pay" is especially  troublesome.  If this "feature set" is intentional, then it should not  be kept a secret.  It should be disclosed to the user prior to  committing to the install of the software.

Ubuntu ceases to be a "free" operating system if in choosing to use it,  you must consent to the transmission of non-public information to a  corporation on another continent, every time that a user logs onto the  system.

---

### Post by Nizumzen on 2010-05-02
> **Bob P said:**
> From a security standpoint, making that assumption requires quite a leap of faith:  It requires you to assume that because the software is making an undisclosed update check, it is also not performing any other undisclosed activities.  There is no reason to believe that a machine performing undisclosed activities is performing only innocuous undisclosed activities.

Well there is an easy way to find out.

Just check out the source code and see what it is really doing.

---

### Post by CharlesA on 2010-05-02
Did you tell it to automatically install security updates?

---

### Post by Bob P on 2010-05-02
> **Nizumzen said:**
> Well there is an easy way to find out.

Just check out the source code and see what it is really doing.
Finding the package is not easy.  As I mentioned before, I've dug through the MOTD system trying to figure out how it works.  Unfortunately the system is not completely documented, and the implementation is sufficiently obfuscated as to make reverse engineering an impossible task. 

I mentioned before that finding the source code is particularly difficult; two different people have observed that apt-get reports the responsible package as being uninstalled on the system.

---

### Post by Bob P on 2010-05-02
> **CharlesA said:**
> Did you tell it to automatically install security updates?
Yes -- security updates were approved, but I don't think that they are the root of the problem.

Looking at /etc/apt/apt.conf.d/50unattended-upgrades, lucid-security upgrades are uncommented.  So this could be in the differential diagnosis problem list.  But ...

My understanding is that security updates are supposed to be performed daily, as an object in /etc/cron.daily/apt, and that they are not supposed to occur every time that a user logs onto the system.

Looking at the update timestamps in /var/lib/apt/periodic/, it appears that the time stamps for the daily automatic updates are being refreshed on the daily schedule, and that these timestamps do not coincide with user logon events. In other words, according to the daily update timestamps, whatever is happending during the 8 second lag that persists between password entry and the availability of the command prompt are events that are  not attributable to daily security updates.

---

### Post by Xianath on 2010-05-02
This is just a shot in the dark, but have you tried removing landscape-common and landscape-client? Also, if you're too worried about unwanted traffic (and you should be), grab a network capture and inspect it in a network analyzer such as Wireshark. It is almost certainly a plain HTTP call, most likely some kind of SOAP binding. Just a guess, but worth checking out.

---

### Post by tgalati4 on 2010-05-02
To the OP:  I'm running hardy server on my machines and I have not noticed such behavior.  If it is something new in Lucid server then we should spend some time to figure it out.  I'm less inclined to be alarmist until I see the source code.  If I can't find the source code, then it's usually my fault not some conspiracy.  Your opening thread gives the impression of such a conspiracy.

What is the output of:

locate landscape

---

### Post by Bob P on 2010-05-02
My OP doesn't suggest any conspiracy.  It merely relates facts that I found in researching the problem.  The software's author is on the record in the bug report and his candor is very clear.  There are also other bug reports where people have challenged the appropriateness of the SPAM that Canonical has built into the MOTD system.

That said, I'm going to limit the amount of time that I will spend chasing down this problem for the Ubuntu community. Its the software developers' job to document the function, not a system administrator's job to reverse engineer it from source code.  Unfortunately this "feature" is not well documented and its functionality is purposefully obfuscated.   I can't see committing an inordinate amount of my time to tracking down bugs and/or obfuscated spyware features.  I have the option to use any distribution I like for the server build, and the path of least resistance for me is to pronounce UBUNTU SERVER = FAIL, to build a clean server on a trouble free OS like RHEL/CentOS 5.4, and to move along.  Those installations have not caused me any trouble and their documentation is unparalleled.  The Ubuntu experiment, in contrast, has resulted in a terrific waste of my time.

To answer your question, the output of the command you requested is perhaps 80 lines of text  That is far  more than I am willing to type, and I cannot capture the information from the system because it is presently in a state of isolation because it is not trustworthy.  My only option is to type what I see onscreen.  Here's a brief summary:

There are files in the following locations:

/etc/landscape
/etc/update-motd.d
/usr/bin
/usr/lib/python2.6/* (lots of files)
/usr/share/pyshared/* (lots)
/var/lib/dpkg/info/landscape-common.*

The significant question remains -- is it possible to eradicate the MOTD system in its entirety, or is it hard-coded into the system and if you want to use Ubuntu you're stuck with it?  Either way there's no documentation on how to remove this "feature", and plenty of people have complained about it.  I'm hoping that based upon your question, you're about to tell me that by purging landscape from my system the problem will go away.  If the solution is more complicated than that, then I'm going to have to pronounce this release as not ready for the enterprise and move along.

---

### Post by tgalati4 on 2010-05-02
My understanding is that Landscape is a proprietary Canonical product for remote server management.  Did you install Landscape on your system after the standard server installation?  If so, then a simple removal of Landscape should get you back to a simple, secure, Debian-based, server.

If, after you have removed Landscape you are still getting this "phone-home" behavior, then it's something that the community should be aware of.

If all of this Landscape stuff is automatically installed in the Lucid server, then that is also news to the community.

I'm not familiar with the terms-of-service for Landscape or exactly how it works--since it is proprietary, you won't be able to see the source code.

Again, if you installed it, then you should be able to uninstall it.

---

### Post by pdtpatrick on 2010-05-02
i've been wondering the cause of this for a while, came across this:

[http://www.etc.to/ubuntu-slow-ssh](http://www.etc.to/ubuntu-slow-ssh)

---

### Post by Bob P on 2010-05-03
> **tgalati4 said:**
> My understanding is that Landscape is a proprietary Canonical product for remote server management.  Did you install Landscape on your system after the standard server installation?  If so, then a simple removal of Landscape should get you back to a simple, secure, Debian-based, server.

If, after you have removed Landscape you are still getting this "phone-home" behavior, then it's something that the community should be aware of.

If all of this Landscape stuff is automatically installed in the Lucid server, then that is also news to the community.

I'm not familiar with the terms-of-service for Landscape or exactly how it works--since it is proprietary, you won't be able to see the source code.

Again, if you installed it, then you should be able to uninstall it.No, I did not install landscape.  I did a plain-jane Ubuntu Server 10.04  installation.  I also did an apt-get update to assure that I had the  latest packages and the problem didn't go away.

Based on the files that I found via the "locate landscape" command in the previous post, it looks like landscape is installed.  So I just tried to remove it:


```
# apt-get remove landscape
Reading package lists ... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package landscape
```As you can see, apt-get tells me that I don't have the package installed.  If that output is accurate then I can not explain why the "locate landscape" command produced the results that I posted previously.  It would appear that there is a set of files are embedded in the operating system via a package that is not available to be removed. I can't explain how they got there.  :confused:

All in all, this is proving to be a very frustrating test drive.  I'm fondling a stack of RHEL/CentOS installation CDs as I type this.

---

### Post by Bob P on 2010-05-03
> **pdtpatrick said:**
> i've been wondering the cause of this for a while, came across this:

[http://www.etc.to/ubuntu-slow-ssh](http://www.etc.to/ubuntu-slow-ssh)

Thanks for the link.  Just to clarify, I was not complaining about delays in SSH connections, though I do experience a delay in SSH connections that is comparable to the excessive delays that I am experiencing in logging on locally to tty1.  

I can see how mdns lookups and timeouts could prolong a remote SSH connection, but I don't see how mdns could prolong a local tty1 console logon.  I thought that these delays appeared to be attributable  to the MOTD shennanigans that are occurring behind my back.

---

### Post by tgalati4 on 2010-05-03
sudo apt-get remove landscape-common landscape-client

Use purge to remove config files as well.

---

### Post by Bob P on 2010-05-03
Just thought I'd pass this along as an update:

I mentioned previously that I edited the /etc/pam.d/logon and ssh files to comment out the motd references, hoping that this would put an end to the annoying MOTD display problem.  I have been performing a disk torture test for a few days that prevented me from rebooting the system.

After tonight's reboot, the MOTD messages are no longer displayed.  But the excessive delay that went along with them remains unchanged.  This suggests that the processes that had been taking place in the dark that delayed the user logons are still taking place, and only their output to the display has been silenced.

FWIW the firewall log entries seem to have stopped.  I'm going to keep my eyes on the logs to see if this improvement holds out.

At this point at least, it appears that ET is no longer phoning home, though he's still busy doing things on my server between the time that I enter a logon password and the time that I'm delivered to the command prompt.  Having to wait ~8 seconds every time that I log onto the system is annoying.  All of those delays will add up to a lot of wasted seat time over the lifetime of a server installation.

For comparison, the test installation that is running CentOS immediately delivers the user to the command prompt without any delay as soon as the password is entered.  Everything works like it is supposed to and no jumping through hoops is required.

Thanks to everyone for their ideas and suggestions.

---

### Post by Bob P on 2010-05-03
> **tgalati4 said:**
> sudo apt-get remove landscape-common landscape-client

Use purge to remove config files as well.Interesting.  It looks like landscape-common is part of the default 10.04 server install:

```
# apt-get remove landscape-common landscape-client
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package landscape-client is not installed, so not removed
The following packages will be REMOVED:
  landscape-common
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 1,335kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 54352 files and directories currently installed.)
Removing landscape-common ...
```It looks like I blew my chance to use the purge command.  Maybe I should have used both remove and purge at the same time.
```
# apt-get purge landscape-common landscape-client
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package landscape-common is not installed, so not removed
Package landscape-client is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```Not enough time to make any observations yet.

---

### Post by windependence on 2010-05-03
If you are contemplating a production install, I would seriously consider installing 8.04LTS instead of 10.4 because 10.4 is way too new for a production deploy IMHO. It was only released days ago.

PS, I sent you a PM.

-Tim

---

### Post by Bob P on 2010-05-03
Tim, thanks.  YGM.

---

### Post by Bob P on 2010-05-03
UPDATE: removing landscape-common didn't seem to change anything.  :confused:

---

### Post by Zeosa on 2010-05-04
You think this is bad, you should see what happens when a drive fails, or you lose an nfs drive....You can't ssh into the box to diagnose/repair, it freezes somewhere during this update-motd business. If your at a local console, you can <ctrl-c> out of it and continue on with your business, this doesn't work over ssh which effectively locks you out of the system.

---

### Post by Bob P on 2010-05-04
On a side note, I have had had problems logging in to the Ubuntu Forums today.  For some reason I cannot get onto the site unless I spoof a new MAC address and/or disable javascript in my browser.  Everything worked fine yesterday, but today my authentications keep getting dropped every time that I try to log in from the same computer / session I was using last night.  :(    I've had no problem logging on to this user account today from a different machine.  Aside from spoofing a new MAC,  is there anything else that I should do to try to fix this problem?  

Back to the topic at hand:  Zeosa -- in addition to the problems that I've mentioned, we have a new one:  
[I]
**The MOTD script now requires heretofore unnecessary system functions to be fully operational in order for the log-on process to be accomplished.  These new functions are not directly related to the process of user authentication, but they have been tied into the process of user authentication anyway.  Failure of these other (unnecessary) system functions can now cause a critical failure in user authentication / log-on.  They couldn't do this before.  **

[/I]**SHEESH!  This is a really ILL-CONCEIVED DESIGN!**  We have unnecessary functions that are interrupting necessary functions when they fail.  ](*,) I think that the person who is responsible for implementing this idea needs a lesson in the deign of fault tolerant systems.

This problem has just escalated to a new level.   This MOTD spamming feature has now made the server less fault tolerant.  It sounds like we're accumulating a number of good reasons to get rid of the MOTD function altogether.  The important question remains unanswered -- How do you do it???

---

### Post by tgalati4 on 2010-05-04
When I ssh into Hardy there is no update notification in the motd.  When I ssh into Jaunty, there is an update message embedded in motd.  So this functionality was added in Jaunty or Intrepid.

Rather than being something sinister, I think the slow response is due to ubuntu servers being slammed with the Lucid release.  Once an update is performed (sudo apt-get update) the update message gets set in /var/run and the /bin/login process spits it out.  It's unclear what happens if the update message is missing or out-of-date.  You would have to look at the /bin/login source code to see what the timeout period is.

For a server administrator, having the number of updates displayed when you ssh can be helpful.  It means do whatever tasks you have to do while logged in, but don't forget to check the updates before you leave.

If you haven't logged in for a while, it might take some time to update the cache.  This could be implemented using the wall command or sent via mail or included in the fortune.  It might be some simple coding to push it into the background to allow the command line to come up quickly.  I don't have Lucid on any of my servers.  I have to clear a few drives to make room for a Lucid test and that will take a few days.

I don't have a problem with the server checking the repos for updates during the login.  It has to be done sometime and if you only login once a month, then that's when it gets done.  If it delays ssh time-to-commandline, then that's a usability issue, not a security issue.  There should be a way to gracefully turn off such motd update checking, but it will take some more research.  

Hardy server is going to be around a while and many popular web apps are built for Hardy.  There's nothing in Lucid server that is a must-have for current server purposes, unless there are cloud apps or Landscape monitoring or Web 3.0 stuff that you need.  I would use Hardy Server and not loose sleep over it.

If you need Lucid server functionality and if this motd-update is still an issue then you should continue to escalate the issue.

---

### Post by Bob P on 2010-05-04
> **tgalati4 said:**
> Rather than being something sinister, I think the slow response is due to ubuntu servers being slammed with the Lucid release.  
Do you say that because you researched the source code and you know solid facts?  Or because you have looked at the server loads and you know that that this is a load issue?  Or are you just speculating that nothing is wrong because you have faith in Ubuntu?  I'd certainly welcome the presentation of objective data if you have it, but I am unlikely to be swayed by subjective opinion or an argument based only on faith in someone's intentions.

> For a server administrator, having the number of updates displayed when you ssh can be helpful.  It means do whatever tasks you have to do while logged in, but don't forget to check the updates before you leave.I agree, that information could be useful to someone.  If a server administrator finds that information to be helpful, then he should have the OPTION to turn ON that kind of feature.  If he doesn't find that information helpful then he should also have the option to turn the feature OFF.  Unfortunately, this feature doesn't have an On/Off switch.

Its kind of pointless to ram that feature down everyone's throats, based on the presumption that SOMEONE might find it useful.  I think a better solution to the problem would be to support the concept of USER CHOICE -- turn the feature on if you want it, turn it off if you don't.    Most people that are using linux aren't using linux because they like to be told, "You will do it our way and you will like it." As a design concept, this implementation warrants a FAIL.

> I don't have a problem with the server checking the repos for updates during the login.  It has to be done sometime and if you only login once a month, then that's when it gets done.  I do have a problem with forcing a human to wait in the foreground for a machine to perform a once-a-month task that would be better performed in the background!   

IMO that's a poorly conceived design that places too little focus on the value of human time.  With 10.04 we've got people staring at the console, waiting on machines instead of machines waiting on (serving) people.  I honestly can't see how anyone could think that it is a good idea to make the Super User / SysAdmin stare at a blank screen while he waits for the machine to perform a monthly task that's delaying his log on.

That's an example of extremely poorly thought out system design.  That kind of design only gets implemented by a programmer who is so focused on implementing his code idea that he fails to see the big picture about how the code effects the person that matters the most -- the USER.  In this case the programmer has lost sight of the forest for the trees.  Its one thing for a coder geek to miss the big picture. In a well controlled system design, a supervisor or team leader (geek herder) is responsible for oversight and this person should have recognized the problem and rejected the implementation.  

So where was the team leader/supervisor/design engineer who's responsible for oversight and usability design?      How is it that nobody recognized the potential for this implementation to adversely effect fault tolerance?  If Ubuntu has anyone in that sort of role, they should have recognized the problem and called for a design change.  But they missed the ball.  From an enterprise perspective these kinds of errors are made by minor league ballplayers.  This implementation is not suitable for major league baseball.  Another   FAIL.

> If it delays ssh time-to-commandline, then that's a usability issue, not a security issue.  That statement could be true or false, depending entirely upon the amount of downtime that is imparted by the delay.  If the delay is short and tolerable, then its a usability issue.  If the delay is infinite, as in the case of a failed remote log-on, then this isn't a usability issue or a security issue, its escalated into becoming a server reliability issue.  Yet another FAIL.

> If you need Lucid server functionality and if this motd-update is still an issue then you should continue to escalate the issue.I am patient but I am not a slow learner.  ;)

I'm three pages into "escalating" this issue, and that's as far as I'm willing to take it.  Ubuntu Server 10.04 has failed our proof of concept test.  Its just not ready for prime time enterprise deployment.  Its deficiencies seem to be lost on some people, maybe they just don't care. In playing the role of an "alarmist" I've led the horses to the water, but I can't make them drink it.  Its become evident that further action on my part will only amount to wasted effort.  I'm not going to pursue this any further, and turn this into any more of a  performance art spectacle than its already become.    

There are other solutions that offer more flexibility in configuration and better fault tolerance.  Its time to move along.

Thanks everyone for your time.

---

### Post by Zeosa on 2010-05-04
> **Bob P said:**
> 

This problem has just escalated to a new level.   This MOTD spamming feature has now made the server less fault tolerant.  It sounds like we're accumulating a number of good reasons to get rid of the MOTD function altogether.  The important question remains unanswered -- How do you do it???

Yup, I never cared much for the system, but 'tolerated' it, that is until I happened to be 3000 miles away from the office when a NAS unit failed. After a few frantic phone calls from my users I tried to connect to the box and it just hung after entering my credentials.

After a few hours I was able to get someone to come take a look, when we figured out what was going on I was, shall we say....less than pleased.

---

### Post by tgalati4 on 2010-05-04
I really think this is an expectation issue.  I have never considered Ubuntu server as "Enterprise Class".  It's free, convenient, and mostly reliable.  Suitable for many workloads, VM's, and development work.

There are many server choices.  The OP and others have shown Lucid's shortcomings.  It will only improve with your feedback.

---

### Post by Bob P on 2010-05-04
I don't think that my expectations are an "issue" at all.

Ubuntu is marketing its Server Edition as an enterprise class product.  Here is a two year old  page from the official website relating to the marketing of 8.04 LTS Server Edition:[INDENT][Latest Server Release Expands Ubuntu Enterprise Profile]("http://www.ubuntu.com/news/ubuntu-8.04-lts-server")
[/INDENT]At present Ubuntu is focusing on marketing [Ubuntu Enterprise Cloud]("http://www.ubuntu.com/cloud/private") to the enterprise IT market. Make no doubt about it, Canonical is trying to market Ubuntu Server products to the enterprise.  The question remains of whether the software is up to the task.

I've just Google'd for "ubuntu server enterprise".  The consensus of opinion in the IT industry seems to be that the server software just isn't there yet.

With feedback, hopefully the situation will improve.  In the interim, there are other available choices that meet the criteria for enterprise deployment, in addition to meeting the  proposed criteria of being free, convenient and *completely* reliable.  IMO reliability is a feature that can not be given too much attention.

Hopefully the feedback in this thread will be help to allow Ubuntu Server to become more competitive in its targeted marketplace.  Of course, there's always the possibility that negative feedback will be completely ignored.

---

### Post by arrrghhh on 2010-05-04
I had been using 9.10, and there was a small delay after logging in, but it was minimal.  Less than a second typically.

However, after a fresh 10.04 install I did notice that it took quite a bit longer to login via SSH.  I thought nothing of it, but did think that it was strange for my server install telling me to go to some website to buy some services that I don't need...

So my question - is this the culprit for the poor login times?  If it is, a solution from Canonical needs to be developed.  At best it's annoying, and it seems at worst it leaves your system completely unreachable.  Ridiculous.

---

### Post by i814u2 on 2010-05-04
Do I think it's odd that the system is setup by default to hit an outside location, yes. I would expect some sort of choice during the installation. If it's in there, I missed it as well because I have this on my Ubuntu Server 9.10 installs (two different machines currently).

I'm not looking to debate the issue, I just wanted to add how I removed the "issue" on my test machine.

Here is what I will say:
The MOTD is not at fault here. It's the updating of information, via unsolicited network traffic that's the main issue. Dynamic MOTD is a cool feature in my mind. Especially how it's laid out, because I can alter it easily.
Perhaps this was understood already, but I didn't gather that from most folks posting in this thread.

So, first things first:
I find a couple of items that I don't care to have (some for security reasons, some for performance, etc).
[LIST=1]
[*]The info about the system that is displayed at login. That does me no good unless I'm just logging into the machine. If I'm already logged in, it's just something running cycles in the background that doesn't need to.
[*]The advertising letting me know about landscape.canonical.com. Glad I know it exists now, but I don't care to know every time I log in.
[*]Checking for updates via the internet. I'll check when I want, thank you. Again, another option that doesn't need to run when I log in.
[/LIST] 

So here are the steps I took to remove the items I did not like.
This removes the update-checking from running automatically at login:
```
sudo mkdir /etc/update-motd.d/backup
sudo mv /etc/update-motd.d/90-updates-available /etc/update-motd.d/backup/90-updates-available
sudo mv /etc/update-motd.d/91-release_upgrade /etc/update-motd.d/backup/91-release_upgrade
sudo mv /etc/update-motd.d/99-reboot-required /etc/update-motd.d/backup/99-reboot-required
```
This removes the system information from running at login:
```
sudo apt-get purge landscape-common
```
NOTE: Originally I performed a "remove" instead of "purge". To fix this, I simply installed landscape-common again, and then performed the purge.

Now, update the database used by the locate command, and check that the landscape portion is gone:
```
sudo updatedb
sudo locate landscape
```
After running the locate command I have the following results:
[INDENT]/usr/lib/python2.6/dist-packages/smart/plugins/landscape.py
/usr/lib/python2.6/dist-packages/smart/plugins/landscape.pyc
/usr/share/pyshared/smart/plugins/landscape.py[/INDENT]
I'm not sure those are doing any harm, so I haven't bothered to remove them.

All of this should leave you with a plain MOTD that displays the uname info and the contents of /etc/motd.tail. If you want those gone, edit or move that file appropriately.

If there are questions with my steps, or any of my post, please let me know.

---

### Post by i814u2 on 2010-05-04
Also note, I notice that update-manager is supposedly NOT installed on my machine, yet I have files such as "/usr/lib/update-manager/check-new-release"
I find that odd as well, although perhaps the update-manager package is just a meta type package. I honestly haven't researched it much further, because I appear to have solved my issue relatively easily.

---

### Post by arrrghhh on 2010-05-04
i814u2, thanks!  That fixed it for me.  I didn't want any of it, so I just moved all the files in /etc/update-motd.d, did the update and purged landscape-common with aptitude.

Fixed!  Thank you so much!  The login is extremely quick now, and no spam or crap when I login!  Awesome!

---

### Post by tgalati4 on 2010-05-04
update-manager may be the gui that pops up to tell you that there are updates available.  The apt package system is the same between server and desktop.  The python landscape scripts would be interesting to read.

i814u2's decrapify procedure is helpful.  You have to do that in Windows--remove all the extra crap that you don't want.  Don't see why it would be any different with a commercialized version of Ubuntu.

Ubuntu Enterprise Server--Now with Less Crap

---

### Post by i814u2 on 2010-05-04
Good call on update-manager being the GUI portion. I'm sure that's true and not sure why I didn't think of it other than the fact that the names were the same. 

Glad to hear the steps were easy enough for others. 

Cheers

---

### Post by CharlesA on 2010-05-04
Thanks for the info. If I bother to remove those things from my server, I'll know how to. :)

There is a bit of a delay when I log into my box over SSH, but it's only a couple seconds. I haven't noticed any difference between when I am connecting locally or over the internet. Maybe it's just me.

---

### Post by i814u2 on 2010-05-04
> **CharlesA said:**
> Thanks for the info. If I bother to remove those things from my server, I'll know how to. :)

There is a bit of a delay when I log into my box over SSH, but it's only a couple seconds. I haven't noticed any difference between when I am connecting locally or over the internet. Maybe it's just me.

No, I would imagine that it isn't just your perception. 

The script items (the ones I move, not the package that gets removed) check whether there are updates or a new release. That requires contact to an outside server. That's part of the delay. 

The other part is the landscape-sysinfo (which is part of landscape-common package) running and gathering/displaying the system information portion.

---

### Post by Bob P on 2010-05-04
When I was using a machete to hack through this red tape, I started off doing the edits that I mentioned in the original post.  They didn't solve the problem.

Somewhere in my first efforts I followed a recommendation to mark the scripts in /etc/update-motd.d/* as non-executable.  As I see it, marking the scripts as non-executable accomplishes pretty much the same thing as hiding them in a "backup" directory -- its a band-aid fix. 

I'm not sure that hiding the scripts is a potentially successful approach.  The process that looks for the scripts is still executing. All that hiding the scripts does is to make it not process those scripts. This method blocks the offensive code in the scripts, but it doesn't block the offensive code that calls the scripts.  The process that we'd like to eradicate is still executing, and its still looking for the scripts when no such process should exist in the first place. We still have the problem of a rouge process that shouldn't be executing in the first place.  A better approach is needed.

My next step was to follow the advice of removing landscape-common.  I made the mistake of doing a "remove" instead of a "purge", so I had to reinstall the package and then purge it, as was recommended above.  Purging it didn't make any difference.  The process that causes script execution during the logons is still there.  Its still active, you just don't see the display output.  Maybe you guys were imagining an improvement or there was some sort of placebo effect that made everyone happy after they did the purge.  All I can say is that after performing all of these steps on my testbed install, my testbed machine remained every bit as slow after the mods as it was before them.

I'm sorry to say that I think these methods that have been suggested so far all fall short of the mark.  Maybe I was just able to see how pathetic the log-on performance has turned out to be because my testbed was a really slow machine -- slower than anything that any of us would seriously consider using for real deployment.   All that I can say for sure is that I've tried all of methods suggested in this thread, and the combination of them all still didn't improve the sluggish logon response.

That is to say, after the first reboot, the initial logon and all of the subsequent logons on tty1 remained really, painfully, slow.  Logons on tty2, tty3, tty4, etc. were very quick and painless.  Until I realized what was happening I mistakenly assumed that the problem was solved when it wasn't.  The time to CLI following a logon after a system restart remains every bit as slow as it ever was, as do subseuqent logons on tty1.  This suggests that the functionality hasn't been completely eradicated.  It looks like there's still some offensive code that is executing during the first logon cycle, and it also needs to be removed if you want to fully "de-crappify" your install.  A reasonable workaround though, is for the local user to use the alternate consoles.  Their response time is a lot faster.

FWIW I tried removing the python files.  It didn't help.

These ideas are a definite step in the right direction though.  Thanks everyone for your ideas.

---

### Post by arrrghhh on 2010-05-05
That's interesting, perhaps since my machine can reach the outside world it still makes the call but doesn't display anything so my prompt comes up much quicker...

The only thing I'm basing my experience on is after I hit enter when my password is done, I'm immediately (well, almost) met with a prompt.  It used to hang for 5-8 seconds on average before when it would display some info about my hard drive, updates, how I can manage my server at this website, blah blah blah.  

It doesn't visibly do that anymore, and the time is much shorter, so perhaps I incorrectly assumed it was gone?  I really don't have another way of referencing it.  I would still like to know if this is running, I would prefer that it didn't... All the reasons it's bad have already been discussed, and I do agree.  I don't want it running without my permission.

---

### Post by Bob P on 2010-05-05
I'd estimate that my tty1 logon delay is still about 8 seconds, just what it has always been.  I haven't actually clocked it, I just counted to eight.

Its hard to know what's actually going on, as its difficult to monitor exactly what's going on in the background prior to logging on.  I suppose I could try to watch the status of the ethernet light or the HD status light to see if there's any unexpected device activity, but those are very coarse indicators to rely on, and these status lights aren't visible from where I've got the console.

As an update -- now it looks like my previous assessment was wrong -- in the first few minutes after a restart the tty2 logons don't appear any faster than tty1 ... still an 8 second delay.

I'll stay tuned to this thread for a while to see if anyone comes up with a viable solution.  I'm a little concerned that by doing much more hacking at the box using a blind approach that I'm only likely to do more harm than good and render the system less reliable.

---

### Post by tgalati4 on 2010-05-05
How much RAM and what type of processor on this server?  It could simply be RAM-bound and it takes 8 seconds to swap the process.

And yes, there should be a simple command in the default Lucid server distro to enable or disable this login-triggered repo checking.  I have a feeling that it's a deeply-embedded framework that is used in both the desktop and server versions.

---

### Post by Bob P on 2010-05-05
the junk testbed is a 1.00 GHz P3 with either 512 MB or 1024 MB RAM (don't remember).  Either way, that much RAM should be adequate to load the kernel and provide an initial logon to a CLI.  I did a naked server install, boots to runlevel 3, no GUI, no add-on daemons that autostart.  

If this rouge process can fully exhaust 512 MB of RAM then we've got another good reason to disable it.  I was hoping we could improve the response time by eliminating the need for any disk bound I/O.

---

### Post by i814u2 on 2010-05-06
First, let me apologize for duplicating some of the information presented by others. I honestly just missed a few posts (or maybe a page) of this thread. Sorry for possibly adding, needlessly, to the thread.

On to the topic at hand. It seems that the updating of the MOTD is the only thing remaining right now (as landscape, etc, are removed). I find it odd that the program would cause such a delay if it doesn't find anything to run. What I mean by that is: the search is performed on the folder /etc/update-motd.d and it processes items in lexigraphical order. I suppose there could be a slight delay if it generated a list of files, then checked whether they were executable, versus checking a blank directory. However, I wouldn't imagine that delay to be 8 seconds worth. 

In that case, I agree that the only option left for you to try (at this point, still assuming the update MOTD is the issue) is to disable the updating entirely. I did some more searching and found this:
[https://help.ubuntu.com/9.04/serverguide/C/update-motd.html](https://help.ubuntu.com/9.04/serverguide/C/update-motd.html)

However, while reviewing my test machine, I noticed that the MOTD is already not being updated. I'm trying to determine what change made that happen. I've even re-installed the landscape-common package and it won't automatically update. Perhaps it's a time-based issue?

I'm now more confused after thinking I had the solution, I can't figure out why it's stopped now (because I'm not able to get it going at will either).

Maybe someone can help point me in the correct direction. I'd like to get this solved, for my own curiosity if nothing else.

---

### Post by Bob P on 2010-05-06
I'm going to put the "alarmist" hat back on again.  I downloaded the Ubuntu 10.04 Desktop Live CD today (Lucid Lynx).  The plan was to download the CD, burn it, test it for errors on the system that I used for burning, and then take it home to update a PC that I use for media center type stuff.  Some really alarming things happened, very much like the "alarmist" things that I observed in my initial post.

Normally, Ubuntu Live CDs or Install CDs (I have been using the term interchangeably) provide you with some menu selections at boot up.  You're normally asked whether you'd like to do things like take a test drive without changing your system, install, check the CD for errors, run Memtest, or boot through to your hard drive.  Not anymore.

This time, I downloaded and burned the "Install CD" and rebooted the system so that I could use the "check CD for errors" function that I remember being in all of the other Ubuntu CDs.  I had no intent of installing Ubuntu on this box, I just wanted to burn a CD and check it for errors.  This time I wasn't offered any boot up options.  I just had a blank screen displayed on my PC while Ubuntu Install CD did its thing.

Then the network firewall started issuing errors/alarms.  I got the exact same type of firewall log entries that I mentioned in my initial post:  Unauthorized attempts by the Ubuntu Live CD to access the internet, and establish contact wtih 91.189.90.132.  When the Gnome desktop finally appeared, all of my hard disks were mounted.

WTF?

There's no doubt about it, if you put this Live CD into your computer and boot, its going to mount your drives and attempt to establish contact with Canonical without notifying you of its intent. 

This is wholly unacceptable.  The only reason that I was even able to demonstrate this problem is because my system is behind a secure firewall that locks down all unauthorized incoming AND OUTGOING traffic.  For the average guy whose firewall is trying to protect him from inbound attacks, this kind of unauthorized traffic will go completely unnoticed.

I no longer think that I'm an alarmist.  I think that Ubuntu is doing things that are just plain WRONG.

See the other thread.

[http://ubuntuforums.org/showthread.php?p=9248766#post9248766](http://ubuntuforums.org/showthread.php?p=9248766#post9248766)

---

### Post by Axanon on 2010-05-06
In **/etc/update-motd.d/** are a series of scripts Ubuntu runs to generate the motd. Most of these scripts make calls to other scripts to generate messages for things like software upgrades, determining your system architecture, and a bunch of other useless crap.

I suggest looking through each of these and trace back what they're calling and remove what isn't needed. I *think* what your firewall is blocking is the system automatically checking for updates.

---

### Post by windependence on 2010-05-06
Bob, the delay is probably due to a DNS lookup for the Canonical servers. Whether that is appropriate is up for grabs but I think that is what is delaying your login similar to the problems you can have with ssh trying to look up the host name of a machine and the login is delayed.

-Tim

---

### Post by tgalati4 on 2010-05-06
The delay could also be dpkg checking the cache and comparing it to what is installed on the machine.  This is similar to the delay when bringing up synaptic.  Some smart person came up with a method to rewrite the cache so that synaptic only takes 2 seconds to come up instead of 8 seconds.  It has something to do with how dpkg reads each entry in the cache and then checks the installed binaries.  This cache file gets defragmented over time and it takes longer and longer to parse through.  I don't have the link but you can search for it.

So take a slow machine PIII? (that's 10 years old), probably a slow network card, slow dns lookup (because there is no router or local dns cache), a slow disk (to go with that slow PIII), and a slow dpkg cache refresh:

8 seconds to get to an ssh terminal with a motd and all of its glorious crapness.

The issue of contacting Canonical over the net could be viewed as a security risk, but then so is installing a new operating system.  Perhaps there should be a EULA that the user clicks through to acknowledge such behavior.

So we have determined that both the server and desktop editions of Lucid (and perhaps earlier) perform this "phone-home" activity.

Of course, you can't get the complete Ubuntu experience without a network connection, because there is not enough room on the CD for a "complete" install.

So what exactly is the security risk here?  You are downloading an executable ISO from some server.  Checking it's MD5 integrity, then booting off of it.  If you feel like it, install it to your hard disk.  Syncing a cache file with a site that presumably is trusted (Canonical) can't be much more of a security risk than all of the previous actions already taken.  I'm at a loss as to what the purpose of this thread is.

MOTD may have extra stuff in it that is not really needed, a slow ssh login can be caused by many things, and "phoning-home" to see if your system is up-to-date is an unacceptable security risk?

I will now sit in the corner with my tin foil hat on.

---

### Post by windependence on 2010-05-06
That's not the point. This whole thing is just more unnecessary bloat, and one more possible point of failure or security hole. Why?

-Tim

---

### Post by terazen on 2010-05-07
Same issue?

[http://ubuntuforums.org/showthread.php?t=1475940](http://ubuntuforums.org/showthread.php?t=1475940)

---

### Post by Zeosa on 2010-05-07
> **terazen said:**
> Same issue?

[http://ubuntuforums.org/showthread.php?t=1475940](http://ubuntuforums.org/showthread.php?t=1475940)


Looks like it ....that's pretty much the same thing that happened to me. Your SOL if it happens and your not at the console...the Ctrl-C doesn't work when logging in via ssh (obviously).

---

### Post by dblade on 2010-05-08
Since they are scripts like in other .d implementations, I decided to leave them in place and remove executable permission instead:

```

$ sudo chmod -R a-x /etc/update-motd.d/*       # don't run any of them!
$ sudo chmod +x /etc/update-mot.d/00-header    # add back motd uname -a
$ sudo sh -c "cat /dev/null > /etc/motd"       # blank current motd
$ sudo init 6                                  # reboot to test

```

it survived a couple reboots so far, but we will see if it stands the test of time if and when the following packages get upgraded (those actually installed):

```

$ apt-file search /etc/update-motd.d

```

base-files: /etc/update-motd.d/00-header
base-files: /etc/update-motd.d/10-help-text
base-files: /etc/update-motd.d/99-footer
cloud-init: /etc/update-motd.d/92-uec-upgrade-available
eucalyptus-common: /etc/update-motd.d/15-eucalyptus-url
fortunes-ubuntu-server: /etc/update-motd.d/60-ubuntu-server-tip
update-manager-core: /etc/update-motd.d/91-release-upgrade
update-notifier-common: /etc/update-motd.d/20-cpu-checker
update-notifier-common: /etc/update-motd.d/90-updates-available
update-notifier-common: /etc/update-motd.d/98-reboot-required

---

### Post by Vegan on 2010-05-08
I do not use Landscape so I do not have MOTD that I am aware of. I also do not have automatic updates active.

I do not see any undue traffic from the Linux box, so I am not concerned. If it was a problem, I would be.

---

### Post by dblade on 2010-05-08
Traffic wasn't an issue for me, its too much info spewing out at every login =)

---

### Post by ls8 on 2010-05-24
You should read 'man motd' and 'man motd.tail' for solution.

/etc/motd is a symbolic link to /var/run/motd. It's contents is generated by the scripts in /etc/update-motd.d/* plus file /etc/motd.tail. **To prevent this behavior, create a file /etc/motd.static and point the link /etc/motd to it.** This is not Ubuntu specific, this behavior is inherited from Debian testing.

---

### Post by CharlesA on 2010-05-26
Not that it will help you any, but I recently changed my input chain to "drop" as default and I noticed a bit of a delay before being asked for the passphrase. Turning it back to allow fixed the problem.

Probably the server "phoning home" to check for updates.

---

### Post by arrrghhh on 2010-05-26
> **CharlesA said:**
> Probably the server "phoning home" to check for updates.

This is the part that I want to disable - this is the part that I think most people have issue with as well.  Our Ubuntu servers should NOT be phoning to anybody without our permission!

---

### Post by LightningCrash on 2010-07-15
> **Zeosa said:**
> You think this is bad, you should see what happens when a drive fails, or you lose an nfs drive....You can't ssh into the box to diagnose/repair, it freezes somewhere during this update-motd business. If your at a local console, you can <ctrl-c> out of it and continue on with your business, this doesn't work over ssh which effectively locks you out of the system.

If you can SSH to the box, do the following

ssh -Y -f hostname "xterm"

This will spawn an xterm and will not do the stupid motd logon stuff.

I have a small script (simply "xon") to do this, it makes life great, especially in Solaris environments.

---

### Post by gmoore777 on 2010-07-20
1.) I agree with everything BobP says about this problem.
2.) to make light of this problem or to persuade him otherwise, is just inflammatory.
3.) In an attempt to securitize my 64-bit LucidLynx machines,
getting rid of the MOTD is one of the tasks that are documented in security books. The reason they state is that you don't want to give out any information about the machine to a hacker. (yeah, they will find another way, but at least it won't be via the MOTD)
4.) I think I stumbled upon one solution.

 I just commented out this line in /etc/pam.d/sshd

    # session    optional     pam_motd.so # [1]

I restarted the ssh daemon. (not sure if this was necessary)
   sudo /etc/init.d/ssh restart

I logged out then ssh-ed back in.

Not only did the MOTD not display, the file /var/run/motd
did not get regenerated. (and upon a reboot, the file does not even exist) So maybe nothing is being run which
in effect is what BobP was trying to achieve.

I also noticed that same line is in file: /etc/pam.d/login
so you would have to comment it out there as well.

and one would also have to comment out in file /etc/pam.d/login:

    # session    optional   pam_lastlog.so

So the "last login" does not display.
(although I did that, rebooted, ssh-ed in, and I still get the "Last login:" message??)

---

### Post by hackerb9 on 2010-08-03
I am very peeved about the delay. It's hard for me not to use the word "stupid" in this message. If I'm opening up a 
login shell, I've got business to do; there's no reason for there to be *any* delay when I login via console.

Here are a couple solutions I found helpful:

  $ touch ~/.hushlogin
  # On a per-user basis disables the useless motd delay.


  $ sudo apt-get purge update-notifier-common
  # Deletes the offending scripts in /etc/update-motd.d/,
  # but also gets rid of the update icon in gnome.


Of course, I suppose the correct solution would be to file a bug on the update-notifier-common package to have this 
change reverted. Does anyone know if this change originated with Ubuntu or Debian?

--b9

---

### Post by davidshere on 2010-08-11
> **tgalati4 said:**
> I'm at a loss as to what the purpose of this thread is.

Really?  It seems pretty clear to me:

> **Bob P said:**
> I'd really like to eradicate the entire MOTD functionality on my server.
> **Bob P said:**
> The significant question remains -- is it possible to eradicate the MOTD system in its entirety

The question is, "How do I turn it off?"  Why one wants to turn it off doesn't really matter.  If the answer is "You can't turn it off", that's a violation of the concept of "free software": [http://www.gnu.org/philosophy/free-sw.html](http://www.gnu.org/philosophy/free-sw.html)

"The freedom to study how the program works, **and change it to make it do what you wish...**"

If you can't change Ubuntu Lucid to make it do what you wish... is it really free software?

---

### Post by credomane on 2010-08-11
I've been reading through this thread. Saw bits and pieces of the solution but not all of it in one place. So here is what I do and seems to work perfectly fine for me. I've been doing this myself once I discovered it was no longer a cron job only thing.

update-motd has been turned into a meta package and functionality is now provided by *libpam-modules* by the module *pam_motd.so*.

To disable the update-motd you must comment out this line 
```
session    optional     pam_motd.so
```
in 
/etc/pam.d/login
AND
/etc/pam.d/sshd

I believe for Karmic and earlier there is a cron file in /etc/cron.d/ that runs every 10 minutes or so.

---

### Post by arrrghhh on 2010-08-12
I tried commenting out those lines, and now I have to hit enter before it gives me a login name option...

I'm currently using putty in Windows.

It's not a huge deal, but it will NOT prompt for a login userid without me hitting enter first.  It just shows a blank window...

Hrm, perhaps I was being impatient.  Seems to be working OK now.  Ignore me :P

Thanks for the tips, I commented out those two lines and it seems to login much, much quicker now.

---

### Post by Cool Javelin on 2010-10-05
This is kind of scary.

From what I have been reading in this thread (and others) it seems Ubuntu has added something that communicates with the outside world without telling anyone or giving the installer the option not to.

It seems like something Microsoft would do, and has the general feeling of being spyware. If not, then definitely adware.

This is not to say it is spyware, but it has that feeling.

One of the whole points to turning toward Linux in general is security, and Ubuntu in particular is trust and reliability. Windows isn't a secure OS, Linux is supposed to be, but now, they seem to be inserting code to make it more Windows like.

I have been working on the 10.04.1 server install for the last 2 or 3 weeks and I stumbled across this thread and, frankly, it has scared the s**t out of me.

From what I have gleaned from this, 8.04 (Hardy) or 8.10 (Intrepid) are the latest SAFE versions for Ubuntu.

I have a live CD install for 8.04, but would like a server version. Does anyone know where I can get the Hardy or Intrepid server CD image?

Trust is the key to success, and Ubuntu has lost mine from ver 9 on. Too bad, I really liked Ubuntu.

Mark.

---

### Post by CharlesA on 2010-10-05
Question: Do other distros check for updates automatically?

If that's the deal breaker for you, then use something that works for you.

If you want an option to turn off this behavior, file a bug report and cite your reasons.

---

### Post by Cool Javelin on 2010-10-06
Here is an interesting note.

After reading about this, the next time I logged into a terminal on my old Xubuntu 8.04 Hardy, I noticed a page of text similar to the one on my new Lucid server.

It didn't mention Canocal.com, but it did mention Ubuntu.com and I got to thinking about MOTD on my Xubuntu Hardy.

Sure enough, I found motd in /var/run, and a symlink in /etc and in several other directorys. I am removing now, I'll let you know if I break my system.

The whole point of me using Xubuntu is because I am using a slow old machine with limited resources, and this is just what I want, my machine running bunches of things in the background I don't know about and don't know what they do.

Mark.

---

### Post by vuser1 on 2010-12-14
For those who are still looking how to get rid of login delay (caused by motd update). Server 10.04

1. aptitude remove landscape-client landscape-common
2. comment line
session    optional   pam_motd.so
in /etc/pam.d/login and /etc/pam.d/sshd

---

### Post by chrislynch8 on 2010-12-15
> **vuser1 said:**
> For those who are still looking how to get rid of login delay (caused by motd update). Server 10.04

1. aptitude remove landscape-client landscape-common
2. comment line
session    optional   pam_motd.so
in /etc/pam.d/login and /etc/pam.d/sshd

This worked for me. It was so annoying, everytime I log in it tells me my IP address of the Server etc. Its a NON-GUI server install, only admin will be accessing it, what is the point of telling me what I already know. 

I have didn't turn on Automatic Update either, so I don't what to know when updates are available. 

Thanks for the Post,

Chris

---

### Post by pmenier on 2011-01-01
hello

You can just remove /etc/motd which is a symbolik link to /var/run/motd and touch /etc/motd with what you want.

Patrick

---

### Post by hellmitre on 2011-05-03
I believe all of this is linked to the scripts run from /etc/update-motd.d. If you remove the symlink to 50-landscape-sysinfo in that directory, I think it will remove the login prompt. This is less drastic than uninstalling the landscape client.

---

### Post by jharris1993 on 2012-03-09
> **davidshere said:**
> 
The question is, "How do I turn it off?"  Why one wants to turn it off doesn't really matter.  If the answer is "You can't turn it off", that's a violation of the concept of "free software": [COLOR=Navy]_[http://www.gnu.org/philosophy/free-sw.html](http://www.gnu.org/philosophy/free-sw.html)_[/COLOR]

"The freedom to study how the program works, **and change it to make it do what you wish...**"

If you can't change Ubuntu Lucid to make it do what you wish... is it really free software?

Folks, I hate to break the bad news to you, but Ubuntu has fallen sadly away from it's own credo as well - and I documented that on my own blog-site with an article titled *[COLOR=Blue]_[An Open Letter to Canonical and Ubuntu]("http://qatechtips.blogspot.com/2011/03/open-letter-to-cannonical-and-ubuntu.html")_[/COLOR].*

Ubuntu *used* to say that "It's all about giving the user choices."


[LIST]
[*]Where was the choice when I discovered that they have now adopted Grub2?
[*]Where was the choice when some [person of less than average intelligence] had the brilliant idea of making the Ubuntu default desktop as Mac-like as possible?
[*]Where was the choice when the entire system startup process was converted into some Fuster-Cluck that is darn-near impossible to work with unless you developed the &^@#%! thing?
[*]Where was the choice when Ubuntu decided that all text in a non-GUI environment should be shown at the monitor's highest resolution possible?  I hate to break the bad news to you - but my eyes have not been 20 years old for a long time now.
[*]Whatever happened to the "accessibility" everyone at Ubuntu is crowing about?  Now, I have to go find one of those sheet-sized magnifying lenses to put in front of my server's monitor so that I can see the *&^#@!*&ing!!! text.
[*]Whatever happened to the idea of inclusion?  I (politely!) raise these issues in various fora and I get flamed into oblivion.
[/LIST]
The fact that Canonical has decided to "monitize" Ubuntu and cram a bunch of non-choice items into it, does not surprise me at this point.

IMHO, the situation is like this:

[LIST]
[*]The Ubuntu Users/Sysadmins:   ](*,)
[*]The decision makers at Ubuntu / Canonical:  :-({|=
[/LIST]
Pretty darn sad if you ask me.

What say ye?

Jim (JR)

---

### Post by sffvba[e0rt on 2012-03-10
I say your post is too late (thread is about a year old) and off topic - Thread closed.


404

---

