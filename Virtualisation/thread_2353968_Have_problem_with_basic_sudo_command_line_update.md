---
title: "Have problem with basic sudo command line update???"
date: 2017-02-26
forum: Virtualisation
---

### Post by mwoosley on 2017-02-26
Could someone please tell me why my Ubuntu Server 16 LTS will not update from the command line?  When I type 'sudo apt-get update' my distro err's out.  Below is the image I captured from my VM within VirtualBox.

Thank you very much for any and all help to this newbie ;-)  BTW, this is all started when I was attempting to install the Guest Additions...

Mike

[ATTACH=CONFIG]273909[/ATTACH]

---

### Post by deadflowr on 2017-02-26
*Thread moved to **Virtualisation**.* 

You need to figure out your networking situation for the virtual machine.
Do this in the Virtualbox settings page in the Virtualbox home page.
(Or whatever the Virtualbox main page is called...)

---

### Post by mwoosley on 2017-02-26
I was pushed over here by potentially one of Oracles VirtualBox moderators.  Does it matter that I can ping 8.8.8.8 and get a successful response back? I have setup all of my distro's pretty much the same as the ones in the classes I'm taking on Udemy. Of course I may have made a mistake somewhere, but for now, I'm at a loss. Again, newbie here...

---

### Post by Habitual on 2017-02-27
All my Vbox guests utilize NAT.

---

### Post by steeldriver on 2017-02-27
Being able to ping 8.8.8.8 is useful (it means your guest system has a route to hosts beyond your host system and router) however it doesn't tell the whole story - likely your system is not configured to use 8.8.8.8 as one of its DNS servers

---

### Post by ajgreeny on 2017-02-27
First try ```
ping 216.58.210.46
``` then immediately try ```
ping google.com
```
Any difference?  There should not be as they are both the same destination but if you can not reach google.com it suggests a DNS problem which we will try to help with.

---

### Post by mwoosley on 2017-02-27
Thanks ajgreeny.  Between the time I left my message the first time and discovering your input for my problem I was able to get past my initial problem.  The way I got it to work was setting the network adapter to bridged inside VirtualBox network settings.  Once I did that, the server clicked right on and seems to be functioning fine.  I did not try that earlier as I had seen on other posts that using the bridged option wasn't recommended.  My only issue now is that after doing the first update/upgrade I still have 10 packages that can be updated of which 7 updates are security related.  I am attempting to figure out how to implement those now, as the update/upgrade process is not working for me ;-(

Thanks again for your recommendations and help.

Best,
Mike

---

### Post by efflandt on 2017-02-28
Did you try **dist-upgrade** which is smarter about upgrading things than **upgrade**, especially if dependencies change (see **man apt**)

---

### Post by ajgreeny on 2017-02-28
I normally run my VMs using bridged mode for the network and have never had a problem with it, but my host is using ethernet, not wifi, and I am not sure whether or not that could make any difference to the success or failure of the connections in bridged mode.

---

### Post by Delvien on 2017-03-16
> **ajgreeny said:**
> I normally run my VMs using bridged mode for the network and have never had a problem with it, but my host is using ethernet, not wifi, and I am not sure whether or not that could make any difference to the success or failure of the connections in bridged mode.

As long as the correct adapter is set, if running bridged, it doesn't matter if its wifi or Ethernet (as far as connecting to the network is concerned.)

---

