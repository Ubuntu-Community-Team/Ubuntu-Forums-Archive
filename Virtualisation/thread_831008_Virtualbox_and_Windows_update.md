---
title: "Virtualbox and Windows update"
date: 2008-06-16
forum: Virtualisation
---

### Post by adambot on 2008-06-16
Greetings,

I setup a virtualbox instance, however i cannot get any windows updates to work.  I have bridged my networking and have a public IP address for my virtual machine, however windows updates just fail.

I first tried the version in the repository, then i tried version 1.60 and now 1.62 straight from sun and was unable to get windows update to work in any of them.

Has anyone else had this problem??  has anyone else gotten this fixed??

thanks,
Adam(bot)

---

### Post by ASL4U on 2008-06-19
I also have this problem - but a tiny bit different because when I installed - I GOT updates. Through the virtual XP I opened IE and went to Microsoft, it validated my "machine" and I got the update to SP3 and everything there.... at that moment.
Now -its two days later - and while I an still go to microsoft's website, still get validated - still go through the download process... the files will not install.
I am not sure it has anything to do with anything - but there was an ubuntu update - and I had to do something with my virtualBox (rebuild it or something...) to make it run again .. but ever since then I cannot get windows updates.
I'm very VERY new - here... and with linux... but I'm "old" (I remember DOS) so I'm kinda comfortable with the command line...
I just dont know how to make anything work in linux.
Anybody got any ideas as to what might be happening with our virtual XPs?
I'm wondering if the update and rebuild changed the permission of the virutalbox internet access so it can access the net - but cannot install from the net directly.
I can download and install - everything works fine - except I cannot update Windows... 
hoping for guidance!
Thank you!

---

### Post by schpidah on 2008-07-30
I had the same problem.  It turned out that it was caused by doing a "repair" installation on WinXP Pro SP2 (which I did to "virtualize" a previously "real" installation of XP). This is a known problem with XP SP2 (and has nothing to do w/ VirtualBox). A couple of possible fixes can be found here:

[http://support.microsoft.com/kb/943144]("http://support.microsoft.com/kb/943144")

Regards

---

