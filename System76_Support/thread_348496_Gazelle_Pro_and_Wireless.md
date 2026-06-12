---
title: "Gazelle Pro and Wireless"
date: 2007-01-28
forum: System76 Support
---

### Post by aay on 2007-01-28
I've seen a couple of posts from people who have had problems with wireless after suspending/hibernating.

Carl posted in one thread that the issue could be resolved [here]("http://knowledge76.com/index.php/Network_manager_applet").

I'm afraid that I still have problems even after making the aforementioned changes to /etc/network/interfaces

I'm making this post because I seem to have found a way around this problem and I thought it might be of help to others.

If you Networkmanager doesn't detect any wireless signal after hibernating/suspending, then try the following.

First remove the intel wireless module from the kernel like this:
sudo rmmod ipw3945

Next reload the same module
sudo modprobe ipw3945

After doing this, Network manager should start detecting wireless signals again.

Of course if you have a different model laptop and/or a different card then you may need to unload/reload a different module.

To check which driver you are using do:
lsmod |more

or likely, lsmod |grep ipw 

And you should see something like 
ipw3945               124576  1

Use the appropriate module listed.

I'm looking into a better (automatic) way of dealing with this and will post back if/when I get this working.

Adam

---

### Post by crichell on 2007-01-29
Thanks for the addition.  It may be possible to put ipw3945 into the /etc/default/acpi-support file to unload and reload the module (although I thought acpi was already doing this for all network interfaces).

---

### Post by aay on 2007-01-29
> **crichell said:**
> Thanks for the addition.  It may be possible to put ipw3945 into the /etc/default/acpi-support file to unload and reload the module (although I thought acpi was already doing this for all network interfaces).

Carl,

Thanks for the tip.  I checked /etc/default/acpi-support and indeed ipw3945 wasn't listed.  I've added it and I'll monitor whether the unloading and reloading works well.  Hopefully this will solve the problem altogether.

Adam

---

### Post by crichell on 2007-01-30
Adam - we've been testing succesfully with ipw3945 in there - let me know if it works for you.

Thanks,

---

### Post by aay on 2007-01-30
> **crichell said:**
> Adam - we've been testing succesfully with ipw3945 in there - let me know if it works for you.

Thanks,

Carl,

I placed ipw3945 in /etc/default/acpi-support.  I've only tested this for a day or so, but so far I'm not having any problem resuming wireless after waking the laptop up from hibernate.  I'll post back if I see this problem show up again, but it seems like this is the fix which is needed.  This is probably a fix that should get scripted into the next version of the driver update.

Thanks,

Adam

---

