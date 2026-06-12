---
title: "Anybody else annoyed with the new network manager?"
date: 2009-09-10
forum: The Cafe
---

### Post by hellmet on 2009-09-10
Trying to manually add an IP in the new network manager shipped with Jaunty is slightly frustrating. One doesn't get to tab between the fields of the address line and the netmask doesn't get automatically added. A pain for new users, I'm sure.
I have filed a bug-report regarding the same, and if you too are annoyed by it, go ahead and support the bug.
Oops, here is the link to the bug: [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/426815](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/426815)

---

### Post by 23meg on 2009-09-10
It would help if you posted a link to the bug report you filed.

---

### Post by Icehuck on 2009-09-10
I was very annoyed with network manager in general that I just went to managing my connections via CLI only.

---

### Post by earthpigg on 2009-09-10
> **23meg said:**
> It would help if you posted a link to the bug report you filed.

+1.

i filed this one because of a complaint quite similar to yours... something that was clearly possible, but not not displayed as an option in the GUI:

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/395641](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/395641)

---

### Post by hellmet on 2009-09-11
> **Icehuck said:**
> I was very annoyed with network manager in general that I just went to managing my connections via CLI only.
Which is not an option for everybody.

---

### Post by slakkie on 2009-09-11
> **hellmet said:**
> Which is not an option for everybody.

why not?

---

### Post by earthpigg on 2009-09-11
> **slakkie said:**
> > [QUOTE]I was very annoyed with network manager in general that I just went to managing my connections via CLI only.
Which is not an option for everybody.
why not?[/QUOTE]

> **slakkie said:**
> why not?

[here]("http://www.ubuntu.com/community/ubuntustory/philosophy") is your answer:

>    1.  Every computer user should have the freedom to download, run, copy, distribute, study, share, change and improve their software for any purpose, without paying licensing fees.
   2. Every computer user should be able to use their software in the language of their choice.
_***   3. Every computer user should be given every opportunity to use software, even if they work under a disability.***_

if you disagree with that philosophy, i suggest you visit [this website]("http://www.microsoft.com/") for software that will better fit your outlook on life.

regards,


chris

---

### Post by t0p on 2009-09-11
> **Icehuck said:**
> I was very annoyed with network manager in general that I just went to managing my connections via CLI only.

This difficulty adding ip addresses stumped me.  It was far easier to open a terminal and use **ifconfig**.  *Far* easier.  To me, anyway.  YMMV etc.

---

### Post by slakkie on 2009-09-12
> **earthpigg said:**
> [here]("http://www.ubuntu.com/community/ubuntustory/philosophy") is your answer:

if you disagree with that philosophy, i suggest you visit [this website]("http://www.microsoft.com/") for software that will better fit your outlook on life.


Uhm.. yes? I fail to see your point, especially the MS part.
What does a disability have anything to do with the command line? 

I just asked a question why the CLI would not be an option for someone...

---

### Post by earthpigg on 2009-09-14
blind, learning disability, dyslexia, speaks a language that is support by ubuntu's GUI itself but has very little/no web support, etc.

there are a number of reasons why people may not be able to use the command line.

granted, of course, most people that do not use it ***choose*** not to for some reason or another but surely we can all use our imaginations as to why someone may be able to point-and-click but not type.

the command line is not an option for everybody.

---

### Post by slakkie on 2009-09-14
> **earthpigg said:**
> 
granted, of course, most people that do not use it ***choose*** not to for some reason or another but surely we can all use our imaginations as to why someone may be able to point-and-click but not type.

the command line is not an option for everybody.

The choosing part is correct, but that is because they choose to neglect the cli. By cli configuration I do not expect a network to be setup everytime by using ifconfig commands, just setting the configuration in /etc/network/interfaces. Which should be doable by anyone, disabled or not.

Creating a script with ifconfig commands is also possible by all kinds of people. I don't agree with you that the cli is not always an option, it is always an option, wheter someone wants to use it or not is something else.

---

### Post by hellmet on 2009-09-17
CLI is definitely an option and the preferred one for most of us. However, not everyone would like to use that option - like ma's and grandma's (and pa's too) ..

---

### Post by ve4cib on 2009-09-17
I've never been a fan of the standard Network Manager that ships with Ubuntu.  Generally I just replace it with WICD; it's lighter, does the same thing in the end, but is generally easier-to-use in my experience.

If you're really annoyed with NM-Applet & Network Manager go check out WICD.  It should be on the Jaunty repo, and I'm pretty sure it's available for Hardy and Intrepid too.  Failing that here's the URL: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by BrokenKingpin on 2009-09-17
I am pretty proficient with the CLI, but I would prefer to be able to edit my connection information with a GUI tool. Although it isn&#8217;t hard through the CLI, it just makes it easier in general to do it with a GUI, as you really don&#8217;t need to learn the correct commands to accomplish the task.

---

### Post by hellmet on 2009-09-18
> **ve4cib said:**
> I've never been a fan of the standard Network Manager that ships with Ubuntu.  Generally I just replace it with WICD; it's lighter, does the same thing in the end, but is generally easier-to-use in my experience.

If you're really annoyed with NM-Applet & Network Manager go check out WICD.  It should be on the Jaunty repo, and I'm pretty sure it's available for Hardy and Intrepid too.  Failing that here's the URL: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
Tried WICD and it looks good, although I've not tried wireless networking on it. Also, I couldn't figure out a way to connect using PPP which gnome network manager provides by default.

---

### Post by speedwell68 on 2009-09-18
> **ve4cib said:**
> i've never been a fan of the standard network manager that ships with ubuntu.  Generally i just replace it with wicd; it's lighter, does the same thing in the end, but is generally easier-to-use in my experience.

If you're really annoyed with nm-applet & network manager go check out wicd.  It should be on the jaunty repo, and i'm pretty sure it's available for hardy and intrepid too.  Failing that here's the url: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

^^^whs.

---

### Post by niteshifter on 2009-09-18
> **earthpigg said:**
> 

if you disagree with that philosophy, i suggest you visit [this website]("http://www.microsoft.com/") for software that will better fit your outlook on life.



Nice argument. Utterly blown by pointing people to the first major commodity OS vendor to implement Accessibility features. Since the Windows 2.0 days - years before Mr. Torvalds made his famous UseNet posting, years before GNOME and KDE. See [this page]("http://www.microsoft.com/enable/microsoft/history.aspx").

I'm certainly no MS fanboi, but let's give credit where it's due - Microsoft has been ahead on this particular curve for decades. What we see here in the Linux world is based upon Microsoft's research and efforts.

I know this because back in 1990 (Win 3.0) I had personal (family) reasons to get involved with local clinics trying to use the technology (aids for visually and hearing impaired folks).

---

### Post by hellmet on 2009-10-05
I just checked with 9.10 Beta and it is still the same. Can anybody else confirm this? Or am I reeeeally doing something wrong?

---

### Post by cariboo on 2009-10-05
Karmic is still in beta, if you really have problems with network manager, just remove it, you don't need it, if you are using a static ip address.

---

### Post by hellmet on 2009-10-11
That's not exactly a solution, you know. Beta is supposed to be a bug-reporter version and I just did that. Removing it is not the answer.

---

