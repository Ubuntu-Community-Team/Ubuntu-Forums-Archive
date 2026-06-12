---
title: "ltsp on server 6.06-xdcmp not found"
date: 2006-10-10
forum: Server Platforms
---

### Post by sudhashen on 2006-10-10
Hi

Run into a bit of a problem-I've installed ltsp on ubuntu 6.06 as per the wiki ubuntultsp/ltspquickinstall.  I came up trumps but could not get past the xdm/gdm/kdm screen. I then checked up the /etc directory and saw that I did not have X installed(no X11 directory). Read up a bit further and discovered something called ltspadmin which made things easier for you. I made the mistake of installing and running this.  Now I have the problem where xdmcp is not detected by this utility.  After much hair pulling and a sleepless morning, I found this article - [https://launchpad.net/distros/ubuntu/+source/gdm/+bug/27885](https://launchpad.net/distros/ubuntu/+source/gdm/+bug/27885)

Seems I should not have been so hasty! the article warns you about running ltspcfg - it will screw things up.  Well I already have :oops: 

My question is, what do I do to fix this? I hope I can avoid wiping and reloading the server! :-s

---

### Post by fnjordy on 2006-10-11
Ideally you should setup your server in such a configuration that it is easy to wipe and re-install.  This makes it very convenient to change Linux distributions or perform a clean install instead of dist-upgrade.  The LVM install option on the alternative install CD helps to make this more convenient as you can resize your disk volumes and have more than the limit imposed on disk partitions.

As to your current problem try apt-get remove on ltsp-server and re-install.  There are some big differences between LTSP and MueKow that don't help, for example LTSP uses XDMCP but MueKow uses SSH to login.

I think the first question is really: do you want a Ubuntu MueKow LTSP configuration or do you want a stock LTSP.org one?

---

### Post by sudhashen on 2006-10-15
Thank you for the answer-I just followed the procedures on the ubuntu wiki forum.  I had no idea I would be a victim of a mix-up between servers until after the fact :confused: - ok I should have had a good read before just going ahead :rolleyes:  

I think I'm going to have to do a readup on the differences between setup.  So far I see that MueKow is still experimental?

---

