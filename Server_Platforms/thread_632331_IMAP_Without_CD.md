---
title: "IMAP Without CD"
date: 2007-12-05
forum: Server Platforms
---

### Post by kmac on 2007-12-05
So, I'm setting up my WebServer and am also configuring it to use sendmail. I'm following a pretty straightforward tutorial and the guidance of one of my professors. However, I've come to a point where I need to install IMAP, which is preloaded on the Gutsy Server cd-rom. However, I'm ssh'ing into my server at home and cannot use the force to move the cd into the drive. I can just as well wait until I get home tonight at nine, but I was just wondering if there is anyway to install it from the web, because apt-get leads me back to the same place and tells me to insert the CD.

Thanks,
--Kyle

---

### Post by MJN on 2007-12-05
Comment out the CD repositories in /etc/apt/sources.list, run apt-get update and you should be good to go.

Mathew

---

### Post by kmac on 2007-12-05
thanks alot. 

I figure that might work, but didn't know if apt-get would know to look somewhere else besides the cdrom for the package.

thanks a bunch

--Kyle

---

