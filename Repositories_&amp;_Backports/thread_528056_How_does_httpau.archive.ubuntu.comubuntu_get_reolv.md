---
title: "How does http://au.archive.ubuntu.com/ubuntu/ get reolved?"
date: 2007-08-17
forum: Repositories &amp; Backports
---

### Post by chandra on 2007-08-17
Dear Folks,

I live in Australia and have locale-dependent lines like

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty main restricted

in /etc/apt/sources.list

How does a URL like [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) get resolved?

Does it happen "intelligently"?

I am with iiNet who host Ubuntu mirrors along with other Linux distributions. Downloading from their mirror does not count toward my quota. Do I need to explicitly change my /etc/apt/sources.list file to include their mirror, or does apt-get automagically point to the closest mirror (presumably iiNet's)?

Thank you.

---

### Post by yesterday on 2007-08-20
Hi Chandra

[http://au.archive.ubuntu.org](http://au.archive.ubuntu.org) points to the ubuntu server mirror in Australia.

You can see that by going to the address in your web browser.

To use the iinet servers you have to explicity add it to your repo list.  It should be fairly in easy to do it via Synaptic.  In the repositories main tab there should be a menu list that has "Ubuntu Official Mirror" or something like that.  If you choose the option to choose a third party mirror, a list of mirrors should open up and you can select the iinet mirror.  Or you can add the mirror directly to your sources.list file.  I think the site is [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/)

Sorry for the vague Synpatic instructions but I'm not on  anymore.

---

### Post by chandra on 2007-08-21
Dear Yesterday,

> [http://au.archive.ubuntu.org](http://au.archive.ubuntu.org) points to the ubuntu server mirror in Australia.

Do you know where this is located and who hosts it?

> In the repositories main tab there should be a menu list that has "Ubuntu Official Mirror" or something like that. If you choose the option to choose a third party mirror, a list of mirrors should open up and you can select the iinet mirror. 

I am running Kubuntu Feisty with synaptic 0.57.11.1ubuntu14 but I cannot get to these options or behaviours.

> Or you can add the mirror directly to your sources.list file. I think the site is [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/)

Thanks for that; I have done it.

Would you know whether these lines should be added at the top or the bottom of the existing repository locations in /etc/apt/sources.list to be used preferentially?

Thanks.

---

### Post by yesterday on 2007-08-24
I *think* that higher listed entries have preference, but I don't quote me on that.

It shouldn't matter too much because the iinet mirrors are full mirrors, so commenting out the au.ubuntu.org is not a problem

---

