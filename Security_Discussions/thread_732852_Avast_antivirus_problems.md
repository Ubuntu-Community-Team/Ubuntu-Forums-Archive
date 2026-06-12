---
title: "Avast antivirus problems"
date: 2008-03-23
forum: Security Discussions
---

### Post by Anila on 2008-03-23
Hello everyone, I have just installed ubuntu and I installed Avast antivirus also. It required me an registration and i inserted it, but the problem is that the antivirus interface showed up only once, and when i try to run it again it shows an "Avast! Information" with the message " Deleted stale lock file '/home/user/.avast/lockfile-user' ". I click ok and then it still requires me the registration key which is valid for 12 months. Even when i still insert the product key again, the antivirus window dont show up. I would really appreciate your help
thnx
Anila

---

### Post by LaRoza on 2008-03-23
There is an easy solution: Don't use Avast.

See: [http://ubuntuforums.org/showthread.php?t=694198](http://ubuntuforums.org/showthread.php?t=694198)

---

### Post by Forrest Gumpp on 2008-03-23
Viruses tend not to be a problem under Linux, Anila..  Just forget about the program.  This is just one of those areas wherein Linux is VASTLY different to the Windows experience.  Its a bit like defragging:  you have to do it under Windows, but unless your drives are virtually full, it just isn't a requirement under Linux.  Relax. Read. Enjoy.

Its an entirely new world.

---

### Post by Anila on 2008-03-23
Thanks allot, i already uninstalled it, it was really helpfull the information i got.
Anila

---

### Post by bhavi on 2008-03-24
Anila, Working of linux and windows viruses is explained in detail here:

[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

---

### Post by jitsu on 2008-04-05
I installed Avast this morning and am having problems with it. It's installed and I haven't been able to do anything else with it, nor am I able to find it.

I'm going to take the advice here and uninstall it. 

How do I uninstall it?  I'm not that proficient with the terminal and it's not showing up in the add/remove list.

thanks

---

### Post by brian_p on 2008-04-05
> **jitsu said:**
> I installed Avast this morning and am having problems with it. It's installed and I haven't been able to do anything else with it, nor am I able to find it.

I'm going to take the advice here and uninstall it. 

How do I uninstall it?  I'm not that proficient with the terminal and it's not showing up in the add/remove list.

thanks

Was it a .deb package? The Home Edition? if so, in a terminal (sorry about that) do:

```
sudo apt-get remove --purge avast4workstation

```

---

### Post by jitsu on 2008-04-05
Brian:
It was a deb package and apparently something went awry.

thank you very much for the help,
Charles

---

### Post by kutjara on 2008-04-05
Let me just add a small counterargument.

Whether or not you run an antivirus on Linux really depends on your degree of interaction with Windows users, and how important that interaction is to you.

Let me offer an example. I run a consulting business and most of my clients use Windows. Part of what I do involves receiving emails containing attachments from one Windows user and forwarding it to one or more other Windows users (often without needing to open or read the email myself). Given that many of my clients are willfully clueless about even the most basic Windows hygiene, it is very possible (even probable) that some of their networks are infected with all manner of malware.

Now, if I simply forwarded messages willy-nilly, I could easily be sending malware-laden emails to my clients. Given their level of technical obtuseness, it wouldn't matter very much to them that I was not the originator of the virus/trojan/rootkit; they'd just say I'd destroyed their computers. That's what we call a relationship-destroying event.

That's the reason I use ClamAV on my Linux box. Not to protect my machine, but to protect my business. The alternative would be for me to open and personally inspect every attachment, but if I did, I wouldn't really have time to do anything else.

Of course, no antivirus scanner is perfect, and virii do get through, but Windows users (even fairly clueless ones) understand this, because it happens to them all the time (and they've read about it happening in "Ooh Aren't I a Big Impressive CIO" magazine), so it's much easier to say "darn, I guess my antivirus didn't catch it," than, "well, I don't use antivirus, because I'm superior to you Windows using lackeys."

Yeah, a lot of this is just window-dressing (pardon the pun), but then 99% of business is window-dressing.

---

