---
title: "VMWare Server 2 Beta"
date: 2007-11-13
forum: Virtualisation
---

### Post by Lem on 2007-11-13
Anyone tried it yet? Looks good.. [http://www.vmware.com/beta/server/](http://www.vmware.com/beta/server/)

---

### Post by ikama on 2007-11-14
Hello,
installed nice so far. But I have a problem with logging in the web ui. As far as I have sawn in several forums this is related to pam library problems.

Does anybody have made similar experience?

---

### Post by Delvien on 2007-11-14
Im going to try this when i get home tonight, sounds fun ! :)

---

### Post by Zeosa on 2007-11-14
The new web interface seems pretty slick....

BUT.....For some reason, I can't get it to start any VM's on the server I'm using for testing .....But it did the same thing with 1.x....

My logfiles show :

Nov 13 13:38:25.179: vcpu-0| MONITOR PANIC: vcpu-0:FPU Safety: Error: FPU instruction executed in monitor contextNM: cs:eip 0x4020:0xd9e79 %cr0: 0x8001003b CR[0]: 0x60000010
Nov 13 13:38:25.179: vcpu-0| Core dump with build build-63231


I'd love to be able to put it to use, but I'm tired of banging my head against the wall with it right now :(

---

### Post by Nelson-Ray on 2007-11-14
How do you run vmware server beta 2 ? I don't get anything in my gnome menu in Gutsy. From the terminal I type in "vmware" and it says try "man vmware" and i looked through it but I dont see any options besides "vmware" ?

---

### Post by Nelson-Ray on 2007-11-14
Ok, I see that you have to go through a web browser. Problem is, neither root or regular user account lets me login :(

---

### Post by Zeosa on 2007-11-14
There's a post on the vmware forums about this very issue.....

[http://communities.vmware.com/thread/112671?tstart=15](http://communities.vmware.com/thread/112671?tstart=15)

You have to edit the authorization.xml file to change the allowed user login....

---

### Post by rliegh on 2007-11-14
I'm running it now; I'm pleased that beta 2 is able to successfully install the sound device for my Vista VM, the previous version wasn't able to use it for some reason. 

The sound is choppy (which is odd) but I'm sure that a good half of that is *vista* anyway. :lolflag:

I *hate* the web UI and the security implications make me **** bricks; but it *is* a server product. I simply downloaded 'lokkit' and used it to configure iptables, and I'm hoping for the best :(

**_[edit]_** I have a hard time with the web UI; it *constantly* loses the virtual machine, forcing me to shut the thing down and re-start it. This is getting *really annoying*.

**_[edit #2]_** It turns out that you can generate and then copy & paste a unique URL to the VM, and then access it in your web browser. I'm going to try doing that to get around the mysterious 'disappearing VM' problem.

---

### Post by Delvien on 2007-11-15
> **rliegh said:**
> I'm running it now; I'm pleased that beta 2 is able to successfully install the sound device for my Vista VM, the previous version wasn't able to use it for some reason. 

The sound is choppy (which is odd) but I'm sure that a good half of that is *vista* anyway. :lolflag:

I *hate* the web UI and the security implications make me **** bricks; but it *is* a server product. I simply downloaded 'lokkit' and used it to configure iptables, and I'm hoping for the best :(

**_[edit]_** I have a hard time with the web UI; it *constantly* loses the virtual machine, forcing me to shut the thing down and re-start it. This is getting *really annoying*.

**_[edit #2]_** It turns out that you can generate and then copy & paste a unique URL to the VM, and then access it in your web browser. I'm going to try doing that to get around the mysterious 'disappearing VM' problem.


Mind you, it is a beta, I would suggest you post this on their discussion forums so they can debug.

---

### Post by rliegh on 2007-11-15
> **Delvien said:**
> Mind you, it is a beta, I would suggest you post this on their discussion forums so they can debug.

Good suggestion; google (specifically *gmail*) made me forget what the meaning of the word "beta" is. :(

---

### Post by djsroknrol on 2007-11-16
After the authorization edit, it worked a charm for me...I really like the web interface and better security so far...

My .02 from the desert...

---

### Post by gwi on 2007-11-26
In installed Vmware Server 2.0 beta. When I try to login in the web UI as root, nothing happens. (Well, the username and password boxes and the login button are grayed, and /ver/log/messages shows that the password was accepted).

If I use another username I get an access denied message (as expected).

If I change the username in /etc/vmware/hostd/authorization.xml, root gets an access denied message (again: as expected). Now the other username gets the grayed controls, without anything happening.

Anyone know what's wrong? Were can I find more logging/debug information?

---

### Post by terrylim01 on 2007-11-27
I simply set up root password by

**sudo passwd root**

and enter username "root" and password.

It works.

I moved existing VM disk images (1.0.4) and create new environments.

So far so good.

I am using Gusty 64bit. VMware 2.0 beta.

Terry Lim

---

### Post by DizzyCoder on 2007-12-05
I'm using it on 64bit 7.10 with some success.  I don't know that the performance is there though.  I have to get my win2k3 OS off my striped raptors and install a RAID card that ubuntu recognizes... there is where I will keep my 'datastore' - which is a neat feature.

Theoretically, I should be able to boot up in WinX64 and use the same VM I created in Gutsy inside VMWare Workstation 6... I believe the performance will not be wonderful from winbloze... but I will try out both and post my results.

Another thing I will try is RDP'ing into the Win box instead of the clunky java (I'm presuming) interface via the web... see if there's any difference with that.

The VMI functions of Server2 should make it lickeditty-split, and from what I understand, the same features are available in Workstation 6 when the VM is created in Server2

---

### Post by Pocadotty on 2007-12-06
Tried it...

not sure what to make of the UI though... I prefer having a regular window running it.  However there are some pretty nice improvements.

buggy and very prone to crash (at least for me)... and for some reason It wouldnt let me add USB device... deal breaker there... So I went back to 1.04

look forward to using it when it is a bit more mature

---

### Post by NoThanksM$ on 2007-12-06
In the VMWare forums they've said that USB isn't functional in this release, it will be added in a future beta.  

I don't push my VM very hard, but I really haven't had any crashes or bugginess so far, it's been very stable for me.  I also would rather have the stand-alone app, but that aside for a first beta it seems pretty solid.

---

### Post by salvador24 on 2007-12-06
So I'm running winxp under Gutsy with VMWare Server 1.04 without any problems now.  I have a core duo 1.67Ghz with 2gb ram.  Has anyone noticed a compelling reason to try the beta?  Are you all noticing that it runs more smoothly?

---

### Post by NoThanksM$ on 2007-12-07
Personally, I wouldn't say there are many compelling reasons at this point.  I did it because I had upgraded to Gutsy and figured I might as well go with 2.0 rather than reinstall 1.04.  The one thing for me that has been a HUGE improvement, and I don't know if this is because of the OS upgrade or VMWare upgrade, is that I mainly use my VM for listening to music through Yahoo Music Jukebox as I'm subscribed to Yahoo's subscription service.  Under 1.0x, the audio would frequently have to rebuffer when I was streaming, so I'd have to download anything I wanted to listen to first.  Don't have that problem now.  

For anyone else who uses their VM for a subscription music service, if you have a Plays For Sure player, once they add the USB 2.0 support in you should be able to transfer tracks from the VM, which will be much more convenient than rebooting into Windows.

---

### Post by Synt4xError on 2009-01-31
Whoops

---

### Post by Synt4xError on 2009-01-31
[https://127.0.0.1:8333](https://127.0.0.1:8333) or 8222 - This is your VMWare URL in Firefox or any explorer.

Does anyone know why mine won't show up anymore? It was working perfectly one moment, then the next it just won't connect anymore.

Firefox says:
"Can't establish a connection to the server at 127.0.0.1:8333"

Does anyone know any configurations I could do to get it working again????

Thanks!

---

