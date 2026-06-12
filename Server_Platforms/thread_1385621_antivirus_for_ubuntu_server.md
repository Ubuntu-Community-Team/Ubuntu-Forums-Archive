---
title: "antivirus for ubuntu server"
date: 2010-01-19
forum: Server Platforms
---

### Post by OYY on 2010-01-19
I have a lot of windows client. What is the best antivirus for the ubuntu server? Need some help on this. Thank! 
Actually the ubuntu server need for the antivirus to protect that system?

---

### Post by blackened on 2010-01-19
[http://clamtk.sourceforge.net/]("http://clamtk.sourceforge.net/")

[http://www.avast.com/linux-home-edition]("http://www.avast.com/linux-home-edition")

---

### Post by sxmaxchine on 2010-01-19
hello if you are looking for an anti virus you try avast also i wouldnt use clam because i personaly dont trust an antivirus that is open to the public to change

---

### Post by blackened on 2010-01-19
> **sxmaxchine said:**
> hello if you are looking for an anti virus you try avast also i wouldnt use clam because i personaly dont trust an antivirus that is open to the public to change

Please tell me that you meant this to be ironic because otherwise I will be forced to intellectually flay you.

---

### Post by steven.jones on 2010-01-20
> **blackened said:**
> Please tell me that you meant this to be ironic because otherwise I will be forced to intellectually flay you.

Use small words though....

regards

---

### Post by steven.jones on 2010-01-20
> **OYY said:**
> I have a lot of windows client. What is the best antivirus for the ubuntu server? Need some help on this. Thank! 
Actually the ubuntu server need for the antivirus to protect that system?

I use avast home for my Windows Vista and XP clients, its free, I use clamav for sendmail and grey listing as well....the samba share could be vunerable....in terms of spreading a virus between windows machines via a common share.....Linux itself is in-vunerable to Windows viruses...and does not need protecting. I would set auto security updates though...a worm is your biggest risk...also an iptables firewall....

Many viruses come via phising or spam attacks so grey-listing blocks most of these, clamav catches viruses quite well, ive been running it for 4 years now, it even catches some phishing emails....

regards

Steven

---

### Post by dnvikram on 2010-01-20
> **sxmaxchine said:**
> hello if you are looking for an anti virus you try avast also i wouldnt use clam because i personaly dont trust an antivirus that is open to the public to change

What is the logic behind this rationale of not trusting ClamAV ?Because its OpenSource? If that's the case,then I am sorry to tell you that its a flawed argument.Infact,its the other way round.

"Given enough eyeballs,all bugs are shallow" -- Linus Torvalds

---

### Post by OYY on 2010-01-20
how to install and use in ubuntu server:(? all is in text mode so how to configure,scan,and update even checking it's function probably or not?

---

### Post by dnvikram on 2010-02-02
> **OYY said:**
> how to install and use in ubuntu server:(? all is in text mode so how to configure,scan,and update even checking it's function probably or not?

I would suggest,go through the CLAMAV manuals/tutorials for performing the basic anti-virus scans/checks.It always good to learn the command line way as you learn the inner workings of the app/system that way and know what you are doing.Still,if you want the GUI version,follow the below link.

[http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html]("http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html")

[https://help.ubuntu.com/community/ClamAV]("https://help.ubuntu.com/community/ClamAV")

---

