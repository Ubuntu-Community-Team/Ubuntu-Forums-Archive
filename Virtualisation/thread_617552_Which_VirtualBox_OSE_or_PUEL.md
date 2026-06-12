---
title: "Which VirtualBox: OSE or PUEL?"
date: 2007-11-19
forum: Virtualisation
---

### Post by bliffle on 2007-11-19
Which VirtualBox should I choose: OSE or PUEL? 

I have newly installed Gutsy and XP in dualboot on an IBM T60, I prefer running ubuntu now with infrequent XP use, and right now I only have one XP program, "TotalMedia" (for an HDTV stick) that I need to use.

And where are the best installation and usage specs for easy installation and light usage?

---

### Post by bodhi.zazen on 2007-11-19
Well, my bias is always open source. What feature do you need that is only available in the PUEL ? The big one is sharing hard drive partitions, but that can be done with network protocols (NFS / Samba) so you should be fine with open source.

The PUEL may be easier to install, I am not sure.

---

### Post by bliffle on 2007-11-19
I have NO experience with either OSE or PUEL. When I started trying one out I realized that it's a fair amout of work to do either one, so I ought to start with a good choice.

---

### Post by bodhi.zazen on 2007-11-19
virtualbox OSE is in the repos.

```
sudo apt-get install virtualbox-ose
```

Does not get much easier then that ....

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=virtualbox&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=virtualbox&searchon=name&subword=1&version=all&release=all)

---

### Post by thegnuguru on 2007-11-19
If you need USB support in the VM go with PUEL I think thats all that OSE is missing . Oh wait if you need a VM with a built in RDP server PUEL is the choice [who needs a VM with an RDP server anyway]

---

### Post by Coombabah on 2007-11-20
> **bodhi.zazen said:**
> Well, my bias is always open source....

My bias is also towards open source but VirtualBox OSE/PUEL seems a bit like Fedora/Red Hat licensing.

I like Ubuntu style open source where everyone gets the full version which is why I stopped using Fedora/Red Hat and ended up using Ubuntu.

The OSE VirtualBox is too crippled for my use as many of the features I regularly use like USB and remote access are missing.

The VMWare closed source version has a much friendlier license than the VirtualBox Closed Source version if you also want to use it at work.

I'm trying to expose colleagues to Ubuntu in Virtual Machines and VMWare seems to be the only suitable option at the moment that is free for commercial use.

Any suggestions on a viable Open Source alternative to VMWare?

---

### Post by pebo on 2007-11-20
I think you will need the PUEL for USB to work

---

### Post by Coombabah on 2007-11-20
> **bliffle said:**
> Which VirtualBox should I choose: OSE or PUEL? 

I have newly installed Gutsy and XP in dualboot on an IBM T60, I prefer running ubuntu now with infrequent XP use, and right now I only have one XP program, "TotalMedia" (for an HDTV stick) that I need to use.

And where are the best installation and usage specs for easy installation and light usage?

Have you tried using Kaffeine in Ubuntu?

---

### Post by bliffle on 2007-11-20
> **Coombabah said:**
> Have you tried using Kaffeine in Ubuntu?

I DID try Kaffeine, hoping to use a native linux application to display the HDTV, but I could never get it running right. At that time I also had a Hauppage 950 stick as well because it was recommended in these forums, but I never got it running right. So I fell back to using XP for my (infrequent) portable HDTV. I'd still like to get HDTV going on a native linux application and I'm willing to buy whatever HDTV tuner I need for that. In fact, the main reason I bought this T60 was to handle the CPU requirements of HDTV display (as well as provide a 16:9 screen). I didn't need to upgrade from my trusty old T40 for any other reason.

But as long as I've got this powerful machine with XP as well as ubuntu there's a side benefit from getting VirtualBox and wine going well and being able to handle a transition from XP to ubuntu: I can help my friends convert from Windows, and maybe I can even do some consulting and make some money at it!  I expect to start a VMWare adventure, too, and add that to my kitbag.
 
The HDTV sticks require USB, so it looks like I'll need PUEL. That's OK for isolated purposes like this as long as it's bounded, in a sortof lockbox. I don't mind paying reasonable and predictable prices.

---

### Post by maybeway36 on 2007-11-20
> **Coombabah said:**
> The OSE VirtualBox is too crippled for my use as many of the features I regularly use like USB and remote access are missing.

You could always use x11vnc. That's what I did when I had my VirtualBox machine.

---

