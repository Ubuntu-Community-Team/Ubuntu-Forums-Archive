---
title: "Parental Controls"
date: 2006-11-20
forum: Ubuntu Christian Edition
---

### Post by pianoboy3333 on 2006-11-20
Considering that dansguardian is included with UbutnuCE, I was wondering if anyone here could help me set it up since I have a few questions, please take a look at [http://www.ubuntuforums.org/showthread.php?p=1784785](http://www.ubuntuforums.org/showthread.php?p=1784785)

Mainly, I was questioning if dansguardian was the best choice for parental controls, it seems you can just edit the files with your user password with sudo.

If it is a good choice, can anyone here help me set it up? I have it installed, but I'm not sure as to how it works with squid or something of the like.

Also, I was wondering if there were any other recommendations for a parental control program I was looking at CensorNet, but I could not get the iso to work :(

---

### Post by tonhou on 2006-11-20
Jereme has very nice scripts that will install the required programs and give a gui front end for editing configuration files. Take a look at this page (below) and down near the bottom you will find one under "Web Content Filtering only" which may suit:

[http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/download.html](http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/download.html)

If you really want to do everything manually, the scripts are based on the install and configuration of Dansguardian, tinyproxy & firehol from this howto (please note squid is not used and will conflict with tinyproxy if installed):

[http://www.ubuntuforums.org/showthread.php?t=207008](http://www.ubuntuforums.org/showthread.php?t=207008)

Hope this helps.

--Tony

---

### Post by pianoboy3333 on 2006-11-20
> **tonhou said:**
> Jereme has very nice scripts that will install the required programs and give a gui front end for editing configuration files. Take a look at this page (below) and down near the bottom you will find one under "Web Content Filtering only" which may suit:

[http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/download.html](http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/download.html)

If you really want to do everything manually, the scripts are based on the install and configuration of Dansguardian, tinyproxy & firehol from this howto (please note squid is not used and will conflict with tinyproxy if installed):

[http://www.ubuntuforums.org/showthread.php?t=207008](http://www.ubuntuforums.org/showthread.php?t=207008)

Hope this helps.

--Tony

But if this is only set up for a single computer, can't the user just edit the config. files with sudo?

---

### Post by mhancoc7 on 2006-11-20
> **pianoboy3333 said:**
> But if this is only set up for a single computer, can't the user just edit the config. files with sudo?

Yes. The idea behind including Parental Controls is to help parents protect their children. We always suggest to users that they give their kids seperate user accounts so they will not be able to make the changes.

See: [Web Filtering Tips]("http://www.whatwouldjesusdownload.com/christianubuntu/2006/09/web-filtering-tips.html")

God Bless, Jereme

---

