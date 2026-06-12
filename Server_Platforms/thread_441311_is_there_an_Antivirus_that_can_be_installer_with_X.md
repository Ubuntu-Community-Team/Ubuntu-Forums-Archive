---
title: "is there an Antivirus that can be installer with Xubuntu?"
date: 2007-05-12
forum: Server Platforms
---

### Post by conducteur on 2007-05-12
Hiya,

I have just migrated  to Xubuntu 7.04 Feisty and I thought I might as well install an antivirus package.

Synaptic suggests ClamAV, F-Prot and Amavis.

I tried all three (in turn) but none ever accepted to launch.

Usually Synaptic just works fine, but this time it was a complete disaster.

Could someone please help me?

Thanks in advance,

Conducteur

---

### Post by bscbrit on 2007-05-12
Clamav runs as a daemon - there is nothing for you to see usually unless you call it from your MTA, e.g. evolution.  Are you sure that a. none of them launched, and b. that you tried to start them as root and not as a normal user?

---

### Post by conducteur on 2007-05-12
Thank you for your answer.

You are probably right. I just launched them but I have no idea if it was as a simple user or as Root 

Maybe part of the problem lies in the fact that Xubuntu has no default "root" user.

What would you advise me to do?

Thanks in advance,

Conducteur

---

### Post by bscbrit on 2007-05-12
YOU are the default root user, it just that you have to use the 'sudo' command to access the system as root.

Firstly, there is absolutely no need to run an antivirus package unless you are acting as a mail server because, although it is possible for someone to write a linux virus, there do not appear to be any in the 'wild' at the moment. (Comment:  I am not looking for anyone to respond with their claims that linux viruses do exist - please don't, it will not help the OP).  However, if you are serving emails to a Microsoft machine then you can clean up emails before passing them on.

Secondly, if you simply want to sweep your own emails for viruses then I will need to know a little more about which email program you will be using (Evolution is the default but there are others), which antivirus package you have decided to use and whether you are also planning to install Amavis.  Note:  Amavis is NOT an antivirus package, it simply enables other programs to easily access whatever antivirus and anti-spam packages you have installed.

The easiest method is to install an antivirus package and let Evolution call it for each email in turn.

---

### Post by conducteur on 2007-05-12
Thanks for your answer.

I am using Mozilla Thunderbird, because I know it quite well as I already used it under Windows.

I don't mind using any particular antivirus program, as long as it's easy to configure and use. Clamav would be fine, but so would AVG and F-Prot.

I'm looking forward to any help you can give me.

Conducteur

---

### Post by Enverex on 2007-05-12
If you want a GUI for ClamAV, just look into KlamAv or gvirusscan (er, can't remember the name of the GTK based one).

---

### Post by garybrlow on 2007-05-12
Its ClamTK. :P

---

### Post by conducteur on 2007-05-12
Many thanks,

I have just installed clamTK following your message. It installed fine, but then I can't launch it (How am I supposed to launch it, by the way? I would like to have a nice icon to click on).

Can you help?

Thanks,

Conducteur

---

### Post by conducteur on 2007-05-12
UPDATE !

ClamTK works indeed as an icon, but then, when I click on "upgrade signatures" it says I must be "root" to perform this operation. How do I do this, since there is no"root" user in Xubuntu?

Conducteur

---

### Post by Enverex on 2007-05-12
You use sudo.

---

### Post by Enverex on 2007-05-13
Ok, turns out I was thinking of "avscan" but it's GTK1 so it looks awful, heh, nevermind.

---

### Post by CharlesG on 2007-05-25
I have a similar problem with Xubuntu.  I'm trying to install F-Prot (I'm happy with a command line programme) but when I try to, I need libman-perl (I think that's the one) installed.  When I go to Synaptic, look this up, and go to install, I receive a warning that a number of my installed packages, including Firefox and Abiword are going to be uninstalled.  I do not want this.  I don't have this incompatibility with Kubuntu, and am wondering if anyone knows about this.

---

