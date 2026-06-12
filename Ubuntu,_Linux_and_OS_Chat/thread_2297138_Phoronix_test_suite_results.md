---
title: "Phoronix test suite results"
date: 2015-10-01
forum: Ubuntu, Linux and OS Chat
---

### Post by RichardET on 2015-10-01
[http://www.phoronix.com/scan.php?page=article&item=linux-sep15-6way&num=1](http://www.phoronix.com/scan.php?page=article&item=linux-sep15-6way&num=1)

Hello Ubuntu'ers!  You should be proud - your distribution of choice is a pack leader! What's the deal with OpenSUSE?  I am surprised at how weak this dsitribution is these days in comparison to others.

---

### Post by tgalati4 on 2015-10-01
OpenSUSE uses a combination of XFS (home directory) and btrs (system) file systems, so perhaps the interaction of two different file systems causes slower performance on most benchmarks.  Someone must have thought it was a good idea, so they implemented it.  One test is worth a thousand expert opinions.

Reading the comments are interesting.  There are a lot of factors to consider when doing such full-system testing. 

Use what works.

---

### Post by mastablasta on 2015-10-02
also in test OpenSUSE uses KDE Frameworks 5, which is still kind of in beta and has some known performance "issues". As I know it's performance is not yet on par with KDE 4.

---

### Post by RichardET on 2015-10-02
It's an inside joke for me - I was a Suse'r for about 13 yrs before switching to Ubuntu in 2013.  Over those dozen years, the remarks on their forum site about Ubuntu were sometimes rather nasty, but these days in 2015, their forum seems practically dead, as well as their ideas on how to push their OS further along, other than continuously updating KDE into the bloatware that it is today.  OpenSUSE leaders need to do some of that, now.

---

### Post by buzzingrobot on 2015-10-02
> **mastablasta said:**
> also in test OpenSUSE uses KDE Frameworks 5, which is still kind of in beta and has some known performance "issues". As I know it's performance is not yet on par with KDE 4.

OpenSuse does seem to be in a bit of an identity crisis at the moment. 

I find KDE4 at this point to be very solid and reliable.  I'm sure it's a resource issue that prevents parallel development and maintenance of both 4 and 5, in addition to the attractions of working on the new stuff rather than fixing bugs and backporting features.  I've checked out 5 on both 15.10 and the Fedora 23 pre-releases. Much more mature than earlier. Crash notices from Plasma, System Settings and elsewhere are pretty frequent still. No surprise in pre-releases, hope they're gone by release. 

The automatic opening of KWallet vanished for some time during the development cycle but seems to be back. (KWallet's traditionally annoying and intrusive behavior is the main reason I don't use KDE. It's thoroughly user-hostile in design, implementation and presentation. It's intended to increase security, but it actually has the opposite impact because it drives users to just disable the thing. KDE should adopt Gnome's approach to passwords and secrets, and make KWallet entirely optional if the devs are convinced it has something extra to offer.

---

