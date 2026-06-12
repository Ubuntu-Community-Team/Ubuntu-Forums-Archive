---
title: "Is Firestarter running"
date: 2006-10-05
forum: Server Platforms
---

### Post by Ronin2007 on 2006-10-05
I just installed Ubuntu today and so far I love it.  It's fast and smooth. I was able to install all the things I need without too much problems.  However  I do have a question about Firestarter.  After I installed Firestarter via Synaptic Package Manager and configured it, is there a way to make sure it's running on my computer. I tried checking with the ps command but I don't see any instances of firestarter (unless it listed under a different name). Also
does it automatically load when I boot or turn on my computer?

---

### Post by wieman01 on 2006-10-05
It's definitely listed under a different name (cannot remember the exact name though). "firestarter" happens to be the GUI for Firestarter only...

Yes, it load automatically when you boot the system. You can even see the service loading... it should equally show in the boot log-files. 

Type "sudo firestarter" in a terminal window to load the GUI. The GUI should show you the status of the Firestarter daemon.

---

### Post by szf on 2006-10-05
I've installed firestarter [back]("http://ubuntuforums.org/showthread.php?p=1474916#post1474916") when I first installed Ubuntu. I could never load the notifier into Sessions... can anyone assist us?

---

### Post by Ronin2007 on 2006-10-05
Thanks for the replies fellas. 

As long as firestarter starts up when my computer boots up, I'll be satisfied. As for firestarted loading into the notifier, yeah I really wish there was a solution for that.

---

### Post by towsonu2003 on 2006-10-06
hi
you dont need the gui of firestarter to be running... I personally see it as a security issue as well. but that's another issue. 

you can check with 
sudo /etc/firestarter/firestarter.sh status

it will start on boot, but not as a process. it's basically a script that tells your real firewall (iptables) what to do and when

the common problems to stop it from running would be:
- using dial up: make sure it starts everytime you dial out
- using more than one interfaces to connect to web
i.e. I use eth0 for wired and eth1 for wireless internet connections. when I start eth0, I have to tell firestarter (tru its gui, ner preferences) that I am using eth0. when I switch to eth1 for wireless, I stop firestarter, tell it to use eth1, and start it again.

---

### Post by Ronin2007 on 2006-10-06
Thanks, towsonu2003's 

That's good to know. Now I feel secured.

---

### Post by PvSinNL on 2006-10-07
AFAIK, you should normally only have to run Firestarter manually once (to configure iptables, as others have pointed out). In my experience, Firestarter doesn't play nicely with Network Manager, though. Every time nm configures a new connection, it wipes all iptables settings (check "sudo iptables -L"). This is probably expected (and proper?) behaviour, but it necessitates re-running Firestarter every time one 'changes' networks or reconnects (and at least once on boot up). Since my machine is behind a NAT router most of the time, I don't worry about it too much, but it is slightly inconvenient.

---

