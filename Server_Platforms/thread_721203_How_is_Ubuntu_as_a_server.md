---
title: "How is Ubuntu as a server?"
date: 2008-03-11
forum: Server Platforms
---

### Post by OMJD on 2008-03-11
Hi,

I've used Ubuntu before as a desktop, and I'd still be using it if it wasn't for the compatibility issues. (I play Windows games) Despite that though, I was very impressed.

I'm running a dedicated server which currently runs RHEL4. We're thinking about moving to another service provider and I see they have Ubuntu server edition listed as an option. May I ask how it performs as a server? What advantages does it have over RHEL? And does it have any disadvantages? (In terms of security and functionality)

Lastly, is it compatible with WHM/cPanel?

Thanks for your time. :)

- Rich

---

### Post by hyper_ch on 2008-03-11
Well, I rather prefer debian as server as it has been proofen to be rock-solid.

If you know your way around ubuntu then maintaining a debian server isn't that much different. Packages are usually a bit older than on ubuntu server (depends of course which version) but on a server you go for stability and not bleeding edge and Debian has an excellent record of it.

---

### Post by Digimer on 2008-03-11
I have to agree with Hyper_ch, Debian as a server is my first choice. It's packages are notoriously "old", but that is by design. Something doesn't make it into the Debian Stable branch until it's quite proven reliable and secure.

That said, Ubtuntu is based on Debian, so it's easy of administration (from a sysadmin point of view) is there. I generally use Ubuntu on workstations specifically because it's got the newer packages and is easier to use from a user's point of view and has a larger selection of packages available. However, I wouldn't stress too much over it being a server, though I would pare it down some. 

*Personally*, I'd take Ubuntu over Redhat-based distros (and before I am flamed to death, I got my start in Linux from RH5.1 - FC3 before switching). I find the server config and administration of Debian-based boxes more sane. A perfect example is managing a web server with many virtual hosts... Debian (and Ubuntu) break up all VH containers into individual files that are linked into a 'sites-enabled' directory, making it very easy to temporarily [en|dis]able specific virtual hosts where Redhat-based distros use (or at least used to use) a monolithic config file. That said, I know some who preferred that config.

In the end, you'll be fine with any modern Linux distro, and you'll certainly be better off than with using a Windows-based server.

Digi

---

### Post by netlogic on 2008-03-11
If you need commercial applications, RHEL.  If you are happy with GPL apps, Debian or Ubuntu. If you need non-X86 support, Debian. I have been moving to Ubuntu from Debian. You have to remember, unstable branch in Debian has no security support if you need to move out from the stable branch.  Debian has a VERY slow cycle in the stable branch. 

Outline
1. If you want to get a job doing Linux, go RHEL. 
2. Home servers, Ubuntu. 
3. Your future goal is embedded system, Debian.

---

### Post by SunnyRabbiera on 2008-03-11
From what i know Ubuntu is not real good with servers.
Debian, BSD, redhat and even solaris might be better for you in this area.
I say go with Debian or BSD, both are known for their reliability.

---

### Post by netlogic on 2008-03-11
I personally think it doesn't matter anymore. If you need Oracle and other commercial apps, you are going to need RHEL. If you are migrating from Solaris to Linux, moving to RHEL is a better choice. For home servers? Who cares which one person picks. These days, what makes  a better server? Is it how quick the security patches are rolled out, release cycle, or hardware support that stock kernel supports? Even Slackware and FreeBSD can be a good candidate.

---

### Post by ubnuturero on 2008-03-11
Well after  7 prereleases for Ubuntu Gutsy  and those prereleases are for testing I can say that  ubuntu gutsy  is rock solid as server.

And all the packages that get installed from  MAIN / RESTRICTED are really stable and  with fast security updates.

Also you get 18 months support if you are not using an LTS. with LTS as Dapper or the to be released hardy you will have support for 5 years.

You can install Gutsy Server today  or Dapper  and when  Hardy gets released Just do a:

do-release-upgrade  and  you are done and can keep it there for  5 years or  do another  do-release-upgrade  when  ubuntu 8.10 gets released.

If you are using your server as a plain simple mail  / web server  you can keep with the latest ubuntu  version  ( antivirus/antispam  are better every new release ) 

Only if you have  something developed for an especific version then  use the LTS.


Remember  once  the linux kernel or apache web server or postfix  get released  they are released after beeing tested. then  gets packaged for ubuntu  and also gets tested before released every new ubuntu version.

Just one question:  What Linux Distro you thing  ubuntuforums.org launchpad.net  is running ?


My $0.02

---

### Post by jonabyte on 2008-03-11
> **SunnyRabbiera said:**
> From what i know Ubuntu is not real good with servers.


Not sure where you are getting your information, but I now have a few servers running Ubuntu server version and there has been no issue. I would say these are as stable as it gets.
My other servers run Slackware, which I still consider the best option for servers. The only reason I decided to add some Ubuntu is that the community for it is much greater than Slackware is.

---

### Post by bharadwaj on 2008-03-11
in the recent testing Vista is considered to be the most stable OS and folloewed by Ubuntu and it's quite obvious that Ubuntu Gusty gibbon is doing a very fair job out there....

---

### Post by hyper_ch on 2008-03-11
in what testing and who sponsored it?

---

### Post by netlogic on 2008-03-11
Vista?
hmm... a bit confused. Most companies are skipping Vista, sticking with XP, and waiting for Windows 7 to roll out for their client machines.

Ubuntu servers are fine. If you don't want to deal with the learning curve of other Linux's package management philosophies, stick with Ubuntu.  If you really care about the out of box experience for servers, picking the right Linux distro does matter.  I know Ubuntu has a bad rep, because it is cater to newbie and Digg users treat Linux as Ubuntu. The bottom line is Ubuntu servers are very functional. Debian is good too. If you want to install Linux on a mainframe for FREE, Debian is a good choice. Otherwise, I like Suse Enterprise or RHEL on mainframes.

---

### Post by tubezninja on 2008-03-11
> **bharadwaj said:**
> in the recent testing Vista is considered to be the most stable OS and folloewed by Ubuntu and it's quite obvious that Ubuntu Gusty gibbon is doing a very fair job out there....

I can agree that ubuntu is quite stable.  I'm using it on three production servers, starting with Gutsy when it came out in October.  I've been quite happy with it and it's much nicer to implement, set up and maintain than the other entrenched platforms in our work environment (SuSE, Solaris.. we got rid of Redhat in late 2006).


Unfortunately, I have to scratch my head at any test results that purport Windows Vista to be the most stable.  Based on what criteria?  Who did the test?

I will say that above all, Vista is *consistent*... that is to say, consistently **UN**stable, and rebooting doesn't help much.

We have a legacy Windows 2003 server, that we may upgrade to 2008.  Maybe.

---

### Post by netlogic on 2008-03-11
Don't forget Vista pissed off many sysadmins throughout the world.  When the accounting departments are tightening the IT budget, I can't believe Ms wants to sell corporations gaming rigs as corporate machines. We saw XP machine price dropped to $250. Now, we are back to Core2Duo with 2gigs of ram to run a word processor at twice the cost? Talk about a company that doesn't understand and ignore what IT departments beg them to do.  I wish they make it illegal to put Msoffice trialware on all the new PC. If users can get used to Openoffice, there will be more Linux adoption in many corporations. The bottom line is most office users are so used to MSOFFICE. Most users hate playing with the operating system. They only care about the apps and file manager. I am trying to be nice. Don't get me started on Vista. I think SP1 actually made things worse.

---

### Post by koenn on 2008-03-11
> **bharadwaj said:**
> in the recent testing Vista is considered to be the most stable OS and folloewed by Ubuntu and it's quite obvious that Ubuntu Gusty gibbon is doing a very fair job out there....

Vista ? I thought this thread was about **server** operating systems.

---

### Post by OMJD on 2008-03-19
Thanks for the responses guys.

One further question, does anyone know if cPanel/WHM will work on Ubuntu server edition? I know it's not officially supported, but it does support Debian so that may suggest it'd run on Ubuntu, or am I wrong?

Cheers

- Rich

---

### Post by hyper_ch on 2008-03-19
if it runs on Debian it most likely runs also on Ubuntu...

---

### Post by lespaul_rentals on 2008-03-19
Come on guys, lay off Vista.  It is a great server OS.  I have had over 5 hours uptime on my Vista mainframe at the company I work for.  The only time it needs to restart is an occassional crash, but I called Microsoft and they said it was a problem with my hardware, not Vista.  It needs no firewall; the default Windows Firewall works fine.  We have never had a hack attempt.  Also, no rootkits exist for Vista.  We don't even need an anti-virus application because Windows Defender blocks all malware.  There are no need for logs to see if someone is trying to hack or whatever, because Vista is practically inpenetrable to all but the most talented hackers.

In case anyone's wondering, it is our main webserver, file server, and also Internet gateway.  Rock solid.

---

