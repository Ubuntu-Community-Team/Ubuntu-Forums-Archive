---
title: "Ubuntu - Finally a Linux distro worth paying for!, and few suggestions"
date: 2007-03-07
forum: The Cafe
---

### Post by muncrief on 2007-03-07
First of all, thanks to all who have made Ubuntu a reality. I had given up on ever being able to run Linux as my primary desktop, but today I'm running Ubuntu Edgy AMD64, yes AMD64, with only a few minor weaknesses in functionality, primarily browser multimedia pausing, fast-forwarding, and rewind.

I was able to replace Microsoft with openOffice, which has really improved tremendously. I replaced OneNote with Basket 1.0, an incredible new Linux program that finally competes head to head with MS. And I'm in the process of evaluating two web site development programs (Quanta Plus and Aptana) to move from FrontPage. And the best part? I can run highly efficient Ubuntu Edgy servers as VMs to simultaneously develop web sites.

In fact, for the first time in a decade I actually made donations to Linux, evenly split between Ubuntu and Linux Mint.  Mint is a fantastic Ubuntu derived desktop OS with all codecs and multimedia installed by default. It's a great distro for those who aren't against proprietary codecs being included in the install, and it's solidly based on Ubuntu Edgy. The only drawback right now is that they only have an i386 distro.

As I said in the beginning my only suggestion to the Ubuntu community is to assist with the development of browser plugins capable of displaying control bars for pausing, fast-forwarding, rewinding, etc. Internet multimedia. This has always been a Linux weakness, but it appears that all the codecs are written and working (I have no codec problems, I even have WMV9, on AMD64). It just seems that neither MPlayer, Totem, or VLC have been able to use them fully, and not being a Linux developer I don't know why.

But once again, Awesome job everybody!. My goodness, even Beryl is rock solid, and I mean granite solid, on Ubuntu. Just amazing. I'll be sending more donations as soon as possible, and look forward to Ubuntu being the first Linux community to overcome the browser multimedia problems.

OK, I'm off to learn how to make Apache web sites on Ubunut! Have a great day everyone!
:popcorn:

---

### Post by BarfBag on 2007-03-07
Welcome to the world of free software.  I've donated to various open source projects as well.  I should probably donate to Ubuntu, as I've been using it for over a year now.

---

### Post by Graduate on 2007-03-07
A few years ago, I could not see myself with linux as my main OS. Oh, how times change. Bob Dylan was right. :)

---

### Post by panch0 on 2007-03-09
With the latest MPlayer (1.0rc1) codecs like WMV9 are supported natively, so they shouldn't be a problem.

---

### Post by DoctorMO on 2007-03-09
How did they manage that? isn't there a windows media patent pool ready to strike on anyone who dares use their 'IP'

---

### Post by maniacmusician on 2007-03-09
> **muncrief said:**
> First of all, thanks to all who have made Ubuntu a reality. I had given up on ever being able to run Linux as my primary desktop, but today I'm running Ubuntu Edgy AMD64, yes AMD64, with only a few minor weaknesses in functionality, primarily browser multimedia pausing, fast-forwarding, and rewind.

I was able to replace Microsoft with openOffice, which has really improved tremendously. I replaced OneNote with Basket 1.0, an incredible new Linux program that finally competes head to head with MS. And I'm in the process of evaluating two web site development programs (Quanta Plus and Aptana) to move from FrontPage. And the best part? I can run highly efficient Ubuntu Edgy servers as VMs to simultaneously develop web sites.

In fact, for the first time in a decade I actually made donations to Linux, evenly split between Ubuntu and Linux Mint.  Mint is a fantastic Ubuntu derived desktop OS with all codecs and multimedia installed by default. It's a great distro for those who aren't against proprietary codecs being included in the install, and it's solidly based on Ubuntu Edgy. The only drawback right now is that they only have an i386 distro.

As I said in the beginning my only suggestion to the Ubuntu community is to assist with the development of browser plugins capable of displaying control bars for pausing, fast-forwarding, rewinding, etc. Internet multimedia. This has always been a Linux weakness, but it appears that all the codecs are written and working (I have no codec problems, I even have WMV9, on AMD64). It just seems that neither MPlayer, Totem, or VLC have been able to use them fully, and not being a Linux developer I don't know why.

But once again, Awesome job everybody!. My goodness, even Beryl is rock solid, and I mean granite solid, on Ubuntu. Just amazing. I'll be sending more donations as soon as possible, and look forward to Ubuntu being the first Linux community to overcome the browser multimedia problems.

OK, I'm off to learn how to make Apache web sites on Ubunut! Have a great day everyone!
:popcorn:
Yeah, Linux is much, much better for developing sites, mostly due to the fact that it's a piece of cake to set up a local apache server to do your developing in. Oh, and Quanta Plus is a pretty good piece of software. 

I'd say that VM's for just developing websites is a bit overkill.

As for learning to use apache; just install the newest version from the repos, then "chown -R [username] /var/www", stick your website in /var/www, and you're golden! you can access your site anytime by just typing "localhost" in a web browser.

The reason I recommend the chown command is that permissions are weird on /var/www and that gets annoying if you're constantly developing. chown'ing the whole thing is a bit hack-ish and pretty messy, it's never given me any problems. 

So, enjoy your Ubuntu! And make sure to try out other derivatives like Kubuntu (KDE) and Xubuntu (XFCE) as well :)

Cheers

---

