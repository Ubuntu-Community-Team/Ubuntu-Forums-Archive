---
title: "Why is CentOS so popular."
date: 2010-04-16
forum: The Cafe
---

### Post by themarker0 on 2010-04-16
I've done a mini survey among people i know... And found no actual reason.

---

### Post by matthew.ball on 2010-04-16
Probably because it is the free version of Red Hat Enterprise.

---

### Post by JonRohan on 2010-04-16
As above. It is based on the popular, proven Red Hat Enterprise without the costs. A great balance imo.

Plus a lot of Red Hat programs can port easily to CentOS.

---

### Post by themarker0 on 2010-04-16
> **JonRohan said:**
> As above. It is based on the popular, proven Red Hat Enterprise without the costs. A great balance imo.

Plus a lot of Red Hat programs can port easily to CentOS.


When is see VPS's, i mostly see CPanel. Nothing else :/

---

### Post by JonRohan on 2010-04-16
cPanel is a software package to run a Linux server. So underneath cPanel can be CentOS, Red Hat, Debian etc.

---

### Post by toupeiro on 2010-04-16
It's rhel without RHN or enterprise support.

---

### Post by Paqman on 2010-04-16
> **themarker0 said:**
> And found no actual reason.

Apart from being a free version of the number one Linux distro?

---

### Post by toupeiro on 2010-04-16
> **Paqman said:**
> Apart from being a free version of the number one Linux distro?

^ This.  When I think of a broad linux desktop distribution for Jon Q. Average, I think of ubuntu (not meant as a slam to ubuntu at all!!  Actually a very sincere compliment.)

When I think of bulletproof, rock solid stability in a linux distro that, quite literally, have experienced uptimes spanning years with 0% issues and significantly high load/visibility, I think RHEL.

CentOS gives you that, without the safety-net most enterprises want/demand.

---

### Post by bwhite82 on 2010-04-16
> **toupeiro said:**
> When I think of bulletproof, rock solid stability in a linux distro that, quite literally, have experienced uptimes spanning years with 0% issues and significantly high load/visibility, I think RHEL.


I think Debian when I think of this. But to each his own. MANY MANY MANY companies rely on RHEL to run their mission critical servers.

---

### Post by matthew.ball on 2010-04-16
I actually thought Slackware, but exactly as you said, to each his own.

Speculatively, I'd say the reason Red Hat is mostly used in businesses is because of the professional support available.

---

### Post by Linuxforall on 2010-04-16
RHEL is what makes CentOS, many small companies on budget depend on CentOS and its community driven support, for them, its improbable to buy any enterprise level OS and since one gets all the security, stability of RH, CentOS gets the nod.

---

### Post by HermanAB on 2010-04-17
RHEL/CentOS/Scientific are used widely by governments and large corporations for a number of reasons:
1. Easy to deploy with Kickstart.
2. Co-operation with CSE, RCMP, NIST and NSA.
3. Availability of copyright management tools and 
4. Commitment to GPL2 (avoidance of GPL3).

Point 1 matters to the people that have to install tens of thousands of machines.

Point 2 matters to the Info Security guys and they have a lot of pull.

Points 3 and 4 matter to the Legal Eagles and they always have the final say.

---

### Post by toupeiro on 2010-04-17
> **matthew.ball said:**
> I actually thought Slackware, but exactly as you said, to each his own.

Speculatively, I'd say the reason Red Hat is mostly used in businesses is because of the professional support available.

I think my own personal record I've seen on a RHEL server without a reboot was a RHEL4 VM I had running on ESX.  uptime showed almost 740 days. (I can't remember exactly anymore, but it was close)  The only reason I had to bring it down is because I couldn't vmotion it across the different CPU generations my ESX hosts were runningm which is no fault of RHEL.  Still, 740 days without a reboot, or a glitch is some phenomenal uptime.  I'm not saying it couldn't be done on Debian or Slackware, but I've done it on RHEL and that sold me pretty hard on it. :)  Debian and Slackware are great distro's.

---

### Post by juancarlospaco on 2010-04-17
*It sux very well.*

---

### Post by kenweill on 2010-04-17
CentOS is popular among Cabal Online Administrators. Cabal Online Server is designed to be installed/running on CentOS.

---

### Post by snowpine on 2010-04-17
Very stable, and contrary to popular belief, not just for servers. I run CentOS on my desktop computer and it is fantastic. Some of the apps are a little old (OpenOffice 2.3!!) but extremely stable.

---

### Post by HermanAB on 2010-04-17
Yup.  I now use Scientific Linux for work and Ubuntu for play.  Scientific is the same as RHEL/CentOS, but without the trademark issues.

Scientific is the only distro that may be legally installed and distributed to third parties.  The other option is to strip the trademark crud from Ubuntu, RHEL, Mandriva or whatever oneself, but it is a total waste of time to do so.

---

### Post by mickie.kext on 2010-04-18
> **HermanAB said:**
> RHEL/CentOS/Scientific are used widely by governments and large corporations for a number of reasons:
1. Easy to deploy with Kickstart.
2. Co-operation with CSE, RCMP, NIST and NSA.
3. Availability of copyright management tools and 
4. Commitment to GPL2 (**avoidance of GPL3**).

Point 1 matters to the people that have to install tens of thousands of machines.

Point 2 matters to the Info Security guys and they have a lot of pull.

Points 3 and 4 matter to the Legal Eagles and they always have the final say.

Not true about "avoidance of GPLv3". There will be a lot of GPLv3 software in upcoming RHEL 6, namely GCC and other GNU stuff who shitched to GPLv3 (and RH is one of main GCC contributors, they did not opose to switching to GPLv3), OpenOffice is LGPLv3 (and it is already in RHEL 5), and loads of other stuff which I cant remember right now. 

FUD about GPLv3 is pushed by Microsoft, Apple and certain people from BSD camp (who are influenced by two mentioned companies), and it is just hate towards GPL altogether. They think that GPL will die if they spread enough FUD about GPLv3, so people start switching to BSD and MIT so companies can steal code and get back only what they see fit (or nothing).

Red Hat obviously ignores that FUD and distributes GPLv3 software as usual. They think [their mother was right, and that sharing is good]("http://www.youtube.com/watch?v=ySyPIoyXJ-k").

---

### Post by Bachstelze on 2010-04-18
> **Soldierboy said:**
> I think Debian when I think of this.

LOLwut?

[img]http://research.pandasecurity.com/blogs/images/debian_openssl.png[/img]

---

### Post by CharlesA on 2010-04-18
If I needed insane uptimes, I would be using CentOS or RHEL.

Otherwise I stick with Ubuntu/Debian.

---

### Post by kaldor on 2010-04-18
Like posted before; CentOS is the free version of RedHat's Enterprise Linux. If you need RHEL stability but don't want to pay for it/support, grab CentOS.

Also think about the training people have for server-related jobs. My local colleges focus on Windows 2003, Solaris 8, SuSE and Fedora. Fedora is based on RHEL and SuSE uses the RPM system. People are trained to use RedHat's products and get used to it. Easier to hire a RedHat's certified administrator compared to other distros. Etc etc...

---

