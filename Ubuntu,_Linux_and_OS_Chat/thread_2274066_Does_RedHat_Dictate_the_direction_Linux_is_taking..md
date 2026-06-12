---
title: "Does RedHat Dictate the direction Linux is taking."
date: 2015-04-17
forum: Ubuntu, Linux and OS Chat
---

### Post by RichardET on 2015-04-17
Why is Canonical allowing Red Hat to dictate the main direction of Linux?  People choose Ubuntu because they like it, and think it is a better OS than mainstream commercial products such as OS/X and Windows, or perhaps a better version of Linux than other distributions.  The open source community should not allow one company to dictate the direction of all other open source OS varieties.

---

### Post by cariboo on 2015-04-17
This post really didn't belong in the thread it was in. To answer your question, Ubuntu is based on Debian, they decided to use systemd instead of upstart, it has nothing to do with RedHat. As a side note, many Ubuntu developers are also Debian developers.

---

### Post by grahammechanical on 2015-04-17
The value of Free and Open Source Software (FOSS) is that a Linux distribution can use code from any FOSS project provided the developers comply with the open source license that the code is released under. So, if the code is useful and it works, then why not use it? Who cares where it came from? I certainly do not.

Another value of FOSS which has been used from the beginning is something called "fork the code." This is an option that is always available to developers. And a prime example of it is LibreOffice.

There should be a difference between FOSS ethics and prejudice. The Ubuntu Code of Conduct says this:

> We invite anybody, from any company, to participate in any aspect of the  project. Our community is open, and any responsibility can be carried  by any contributor who demonstrates the required capacity and  competence.

[http://www.ubuntu.com/about/about-ubuntu/conduct](http://www.ubuntu.com/about/about-ubuntu/conduct)

Regards.

---

### Post by Lars Noodén on 2015-04-17
As to forking the code, systemd should have been launched in a fork but it wasn't so now we, even in Ubuntu, are stuck with pre-alpha (still adding features) code forced out into production and with it a monstrosity of complex interdependencies.  I followed the Debian discussion from a distance and was surprised when they left it to a single person to make the decision, as I myself thought it would have a snowball's chance of being adopted based on what I had read of it.  

> **RichardET said:**
> Why is Canonical allowing Red Hat to dictate the main direction of Linux?  People choose Ubuntu because they like it, and think it is a better OS than mainstream commercial products such as OS/X and Windows, or perhaps a better version of Linux than other distributions.  The open source community should not allow one company to dictate the direction of all other open source OS varieties.

Canonical follows Debian in lock-step because Debian is its base.  And although some strange stuff happened in Debian in regards to [systemd](http://forums.debian.net/viewtopic.php?f=20&t=120652&start=0) it continues to follow it.  For users, there remain now the BSDs, in particular PC-BSD for the desktop, and then of the Linuxes, only maybe Devuan will make it. A remote hope is that Devuan gets off the ground and Ubuntu is able to change to it as a base, but again Ubuntu is closely tied to Debian and it would be a big change.   However, Mint was able to switch from Ubuntu to Debian, so there is an idea of how such a change can be done and the work involved, if there is a collective will to do so.

---

### Post by RichardET on 2015-04-17
I know Ubuntu is a Debian derivative, but systemd is a Red Hat initiative, as far as I know.    Marc Espie of OpenBSD is very critical of the systemd avalanche.  Basically an OS has to maintain its own codebase, with limited developer support, or accept the inevitable, which is systemd.  I realize from a linux user perspective, systemd is irrelevant, but for the smaller OS players, such as the *BSD's, the systemd change is a serious issue.

---

### Post by kostkon on 2015-04-17
> **RichardET said:**
> Why is Canonical allowing Red Hat to dictate the main direction of Linux?  People choose Ubuntu because they like it, and think it is a better OS than mainstream commercial products such as OS/X and Windows, or perhaps a better version of Linux than other distributions.  The open source community should not allow one company to dictate the direction of all other open source OS varieties.
if you're talking about systemd, Mark gave an answer about the decision to switch to it [on the Linux Action Show]("https://www.youtube.com/watch?v=r9qeQ7o33GE#t=2940") some months ago.

But it's true, many feel like systemd was forced into us. It's, also, true that Red Hat has taken control of the Gnome project (and that made Canonical turn to Qt). Also, Red Hat is behind PulseAudio, partly behind Wayland, and many others..

---

### Post by vellon on 2015-04-18
I'm surprised to hear people still whining about systemd, considering that hardly anyone will notice it. I keep reading that everyone is going to abandon Linux and move to the BSDs in protest? Has that not happened yet?

Still, there is always Devuan. How is that getting along, BTW?

---

### Post by buzzingrobot on 2015-04-18
While personally I think the dispute over systemd was grossly, often embarrassingly,  blown out of proportion, if someone wishes it to be a factor in their distribution choice, that's fine with me.  For me, though, init systems should only be visible to normal users when they break.

We users are free to exercise 'choice' by choosing this distribution versus that distribution, by installing this package versus that package. The people who make those distributions and the software those packages contain are just as free to make their own decisions. 

Red Hat controls Red Hat. There's no need to engage in conspiracy theories.

---

### Post by RichardET on 2015-04-18
I agree with the editors to move my thread;  it has more significance on its own.  
I used systemd on Opensuse a while ago -it seemed ok to me, so I realize that as a user, its irrelevant, "unless it breaks", as someone earlier mentioned, but RH is a NYSE company and has significant power and sway within the Linux community, as well as amongst larger companies who use Linux technologies , such as 
Intercontinental Exchange;  They moved to RH from Sun Solaris because RH was an NYSE company.  SAS partners with RH also.

I have always thought of RH as a tech leader, but my Linux interest moved away from RH by 2001, when I started using YDL and SuSE, admittedly though, both RH knock-offs.

Two years ago, I discovered Ubuntu and have never seriously looked back, but once again, RH is there on my hard drive.  I will accept it for now - what else can I do?!

---

### Post by buzzingrobot on 2015-04-18
How can Red Hat be on your drive if you're using Ubuntu?  By that token, Canonical is on all those Red Hat systems using Upstart.

---

### Post by mastablasta on 2015-04-18
> **vellon said:**
> I'm surprised to hear people still whining about systemd, considering that hardly anyone will notice it. 

if there is beta or even alpha grade software (as some mention) in production it will be noticed as more people adopt it. especialyl if it wasn't implemented propperly.

to me the funniest thing was when they used an argument that it will make system boot faster, but then they dropped some function regarding that and afterwards they said it will take slightly longer to boot.

---

### Post by vellon on 2015-04-18
> **mastablasta said:**
> if there is beta or even alpha grade software (as some mention) in production it will be noticed as more people adopt it. especialyl if it wasn't implemented propperly.


It is not alpha or beta software, but opponents here like to spread that FUD. It is in production, RHEL 7. Have you noticed any issues there? If so, tell us about them.

---

### Post by Morbius1 on 2015-04-18
> Does RedHat Dictate the direction Linux is taking.
Of course not. At least not by itself.

From: [http://www.linuxfoundation.org/news-media/announcements/2015/02/linux-foundation-releases-linux-development-report](http://www.linuxfoundation.org/news-media/announcements/2015/02/linux-foundation-releases-linux-development-report)
> The Top 10 organizations sponsoring Linux kernel development since the last report include Intel, Red Hat, Linaro, Samsung, IBM, SUSE, Texas Instruments, Vision Engraving Systems, Google and Renesas.
Somebody&#8217;s gotta pay the bills for this thing.

 As for the systemd subtext in this thread it's proponents out manoeuvred everyone else and made many things dependent on it so it's irrelevant if it's technologically superior or a piece of ...... It is what it is.

---

### Post by buzzingrobot on 2015-04-18
> **Morbius1 said:**
> 

 As for the systemd subtext in this thread it's proponents out manoeuvred everyone else and made many things dependent on it so it's irrelevant if it's technologically superior or a piece of ...... It is what it is.

One thing I think that is at play in that squabble is that the two sides seem to have different visions of what Linux should be.  The anti-SystemD folks, at least so far as I've followed them, take a traditionalist stance that argues for Linux being, and remaining, a *Unix* that exists to be used by people who want to run a *Unix*, and see SystemD as a heresy because it isn't Unix-y enough. (One could argue that Unix itself  has not been all that Unix-y since the availability of mice and graphical displays.)

Whereas the SystemD folks seem to be interested in the broader potential of Linux as a platform.

---

### Post by RichardET on 2015-04-20
> **buzzingrobot said:**
> How can Red Hat be on your drive if you're using Ubuntu?  By that token, Canonical is on all those Red Hat systems using Upstart.

touche.  I guess my point was that if I wanted a RH OS, I might as well go with Fedora, but I saw Ubuntu as different, and I liked that, but I guess in reality, its really not that much different.  

I guess this leads to the obvious question - beyond Unity, what exactly am I getting with Ubuntu that I don't get with say OpenSUSE or Fedora?

---

