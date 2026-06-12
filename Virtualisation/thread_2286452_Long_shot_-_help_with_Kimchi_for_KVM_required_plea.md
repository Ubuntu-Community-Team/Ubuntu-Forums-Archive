---
title: "Long shot - help with Kimchi for KVM required please"
date: 2015-07-12
forum: Virtualisation
---

### Post by npinn001 on 2015-07-12
So I have Kimchi installed and working as per the instructions on github:

[HTML]https://github.com/kimchi-project/kimchi[/HTML]

I can connect to the web page and log in, and can create a guest vm all fine.

My problem comes why I try to connect to it via the novnc or spice windows. With novnc I get an error of 1006. With Spice, I get Error: unexpected protocol mismatch. 

Really not sure what to try. I am using UFW, but the correct ports are open and even if I turn UFW off, the error persists.

Any ideas?

---

### Post by KillerKelvUK on 2015-07-13
Just given this a try and got it working...

Ubuntu 15.04 host, couple of vm's using VNC and a win vm using spice.  I run a desktop on my host and all connections from Chrome on the host connected to the guest console...spice was a little iffy with bad fonts and wasn't stable but hey I didn't debug.  Tested from my Macbook on local network (same subnet), no messing with firewall ports...Safari v8.0.7 could access past the login page but not connect to a guest session...same error as your for novnc (code 1006).  Quick google finds this  [https://forge.univention.org/bugzilla/show_bug.cgi?id=33587](https://forge.univention.org/bugzilla/show_bug.cgi?id=33587) which reads like browser incompatibilities as well as a few other bits n' bobs...so I drop Chrome onto the Macbook and all works...also tested from latest IE version in a Win8.1 Parallels guest off the Macbook and that worked fine.  So you should take a look at an alternative browser and see if that gives you any better results.

---

### Post by npinn001 on 2015-07-14
Thanks for the tip. I tried it and it worked, but only when i logged in to the server and started kimchi manually and stayed logged on with it running. Some issue with the github service i think.

On a side note i installed a vm with kimchi but it was slow. Realised you cant use virtio with it so virt-manager still wins.

---

### Post by KillerKelvUK on 2015-07-14
Yeah, never found a web-gui yet that can replace 100% of virt-manager...and virt-manager can't replace 100% of virsh.  That said I'm not managing lots of hosts so have had no real impetus to crack this one, I know some of the community members here do manage lots of vm's so maybe they have better alternatives to suggest.

The issue with kimichi and having to manually start and remain logged in sounds like its could be permissions issue as in the process is being started by a user account that doesn't have permissions to create the network sockets necessary maybe?

---

### Post by npinn001 on 2015-07-14
> **KillerKelvUK said:**
> Yeah, never found a web-gui yet that can replace 100% of virt-manager...and virt-manager can't replace 100% of virsh.  That said I'm not managing lots of hosts so have had no real impetus to crack this one, I know some of the community members here do manage lots of vm's so maybe they have better alternatives to suggest.

The issue with kimichi and having to manually start and remain logged in sounds like its could be permissions issue as in the process is being started by a user account that doesn't have permissions to create the network sockets necessary maybe?

Thanks for that, will investigate this tonnight. To be fair, I only run about 4 or 5 VMs, I just like to have a way of managing them that doesnt rely on having a linux machine to hand- I mainly use a chromebook so web seemed good. 

Feel like I should learn Virsh as this might solve all my issues given I can ssh from the chromebook.

Thanks for all your help.

---

### Post by KillerKelvUK on 2015-07-14
> **npinn001 said:**
> Feel like I should learn Virsh as this might solve all my issues given I can ssh from the chromebook.

Thanks for all your help.

Have a look at tunnelling X via ssh...I've done this previous from one linux box to another i.e. install virt-manager on the host...then off a remote machine connect using SSH but enabling X redirection and then launch virt-manager from the ssh terminal...with redirect X the actual GUI appears on your remote desktop although its using X server resources from the host.  I'm not 100% sure but X redirection may be possible with a Chromebook using a valid SSH client, that maybe worth a little time to look into rather than web-gui's.  Virsh is definitely something to get to grips with, although its pretty straight forward tbh.

---

### Post by cristiandeives on 2015-07-14
What guest did you create which was slow? Kimchi does use virtio when creating VMs, at least in the ones I've tried.

---

