---
title: "[SOLVED] LAMP on Ubuntu Desktop?"
date: 2007-06-27
forum: Server Platforms
---

### Post by xIke on 2007-06-27
Is this possible?  I like the polish of Desktop, but need Apache, MySQL, etc.

Thanks

---

### Post by AlexThomson_NZ on 2007-06-27
Yep, you can install Apache, MySQL, etc. easily through synaptic

Tomcat, Java etc are easily installed by downloading Linux installers from the respective sites

---

### Post by tmatt95 on 2007-06-27
> **xIke said:**
> Is this possible?  I like the polish of Desktop, but need Apache, MySQL, etc.

Thanks
Below is a link to an article detailing how to set it up. I have used this guide to get it to install on my 7.10 desktop instillation. If you have any problems there are also trouble shooting stages which come in handy when going through the guide!!

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Best regards,

Matt

P.S Good luck with the set up :D

---

### Post by xIke on 2007-06-27
Wow, thanks a lot everyone.  I honestly expected at least a few "zomg! reed the manual nOOb!!" comments.

Props.

---

### Post by bikeboy on 2007-06-27
Not around here. If you give those sorts of comments it's greatly frowned upon, part of what makes Ubuntu so good. You will find LAMP easy, if I can do it without previously knowing anything about it, you will be fine.

---

### Post by Alterax on 2007-06-27
Agreed.  Besides, when it all comes down, we were all n00bs at one time or another, so we wouldn't have much room to talk.

Going back to LAMP, it's an easy install.  I use it for a lot myself.

---

### Post by lunatinker on 2007-06-28
this is probably non-productive or not the best way, but i installed Ubuntu server (LAMP option) and then apt-get ubuntu-desktop. eveyrthing works super, but then i'm just getting into linux this week for 1st time. 
cheers. feel free to totally ignore this method.

---

### Post by xIke on 2007-06-28
I got it all working with Synaptic Package Manager.  Ease-of-use has come a long way since the last time I played with linux.  I'd really Ubuntu continues to take off with vendors.

---

### Post by AlexThomson_NZ on 2007-06-28
> **xIke said:**
> I'd really Ubuntu continues to take off with vendors.

well it's certainly looking good- I read somewhere today a couple of vendors have been seeing Dell's success with Ubuntu and are making plans of their own (inc. HP) :)

---

### Post by ParadoxMDB on 2007-07-02
> **tmatt95 said:**
> Below is a link to an article detailing how to set it up. I have used this guide to get it to install on my 7.10 desktop instillation. If you have any problems there are also trouble shooting stages which come in handy when going through the guide!!

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Best regards,

Matt

P.S Good luck with the set up :D

I've tried using the sudo tasksel option specified in the URL, once a blue screen with a few options appear it then gives me the option to install LAMP Server, with both LAMP Server and Ubuntu desktop selected, I then hit enter. When it reaches the "Installing packages" screen it remains on 0% and nothing seems to happen, no packages are attempted to install either. I've tried this many times and it still ends up doing nothing at all. Is this some sort of error? Is there something else I need to do?

Is installing the services manually (as guided through in the URL) the only alternative?

P.S. I'm running Ubuntu 7.10 Desktop Edition.

Please help!

---

### Post by ParadoxMDB on 2007-07-02
> **ParadoxMDB said:**
> I've tried using the sudo tasksel option specified in the URL, once a blue screen with a few options appear it then gives me the option to install LAMP Server, with both LAMP Server and Ubuntu desktop selected, I then hit enter. When it reaches the "Installing packages" screen it remains on 0% and nothing seems to happen, no packages are attempted to install either. I've tried this many times and it still ends up doing nothing at all. Is this some sort of error? Is there something else I need to do?

Is installing the services manually (as guided through in the URL) the only alternative?

P.S. I'm running Ubuntu 7.10 Desktop Edition.

Please help!

Never mind, I found a simpler method:

[LIST=1]
[*]Open Synaptic Package Manager
[*]Select "Edit" -> "Mark Packages by Task"
[*]Select "LAMP Server"
[*]Click OK
[*]Click Apply
[*]Wait for Synaptic to download and install the services.
[/LIST]

---

### Post by beemzet on 2007-07-03
you can download XAMPP from [www.xampp.org](www.xampp.org)

---

### Post by Wilochka on 2007-07-04
Whenever i do sudo tasksel, LAMP does not show up *at all*. Same thing when I go to select it in  Synaptic Package Manager. Any help would be greatly appreciated:D

---

### Post by Copter on 2007-07-23
> **ParadoxMDB said:**
> Never mind, I found a simpler method:

[LIST=1]
[*]Open Synaptic Package Manager
[*]Select "Edit" -> "Mark Packages by Task"
[*]Select "LAMP Server"
[*]Click OK
[*]Click Apply
[*]Wait for Synaptic to download and install the services.
[/LIST]
Hi!

I have just used your method on Xubuntu 7.04 desktop and so far Apache and PHP works like a charm Thanks for this info. I have read dozen posts about installing LAMP by using tasksel. I must say that this method is way better because you know exacly which packages are installed or removed. I did not have to worry that "it will delete my desktop...".

thanks!
copter :]

---

