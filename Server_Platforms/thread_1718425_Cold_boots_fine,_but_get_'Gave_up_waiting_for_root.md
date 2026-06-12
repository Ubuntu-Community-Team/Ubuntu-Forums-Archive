---
title: "Cold boots fine, but get 'Gave up waiting for root device' on reboot"
date: 2011-03-31
forum: Server Platforms
---

### Post by jpgator on 2011-03-31
Recently setup Ubuntu Server 10.10 on an old Dell Poweredge 2650.  It seemed to be working perfectly until I did my first reboot.  
 
I tried changing the 'root' reference on the linux line at the grub menu with no luck.  I suspect the problem is something else but I have no clue.
 
So far the behavior seems completely consistent.  If I physically power the machine down and start it back up everything works perfectly.  However, if I do a sudo reboot now I'll end up at the initramfs prompt.
 
Any help would be really appreciated because I'm not comfortable setting up my dev environment on this box until I'm sure it will be stable.  In case it matters the machine is running a single scsi drive and doesn't have a raid controller.
 
Thanks

---

### Post by jpgator on 2011-03-31
Add'l info....
 
When at the initramfs prompt if I wait about 30 seconds and type 'exit' the system takes me to the normal ubuntu logon.
 
Since I don't have a ''/boot/grub/menu.lst'', I edited '/etc/default/grub' and changed this line:
GRUB_CMDLINE_LINUX=""
to
GRUB_CMDLINE_LINUX="rootdelay=90"
 
This didn't make any difference.  Maybe I'm editing the wrong thing or maybe I'm completely off base in my troubleshooting.

---

### Post by matt_symes on 2011-03-31
Hi

Try adding it to this line (/etc/default/grub)

GRUB_CMDLINE_LINUX_DEFAULT="rootdelay=90"

along with the other options there.

Kind regards

---

### Post by matt_symes on 2011-03-31
Hi

> Since I don't have a ''/boot/grub/menu.lst''

You will not have. That is GRUB. Ubuntu now uses grub2.

Kind regards

---

### Post by jpgator on 2011-03-31
> **matt_symes said:**
> Hi
 
Try adding it to this line (/etc/default/grub)
 
GRUB_CMDLINE_LINUX_DEFAULT="rootdelay=90"
 
along with the other options there.
 
Kind regards
 
Thanks, I had it working for a few minutes but then got too aggressive with the delay (it seems to want more than 90).
 
I do have two other related questions though.  You mention adding it 'along with' the other options, what's the delimiter (comma, semicolon, etc)?
 
Also, I read you must run [FONT=Consolas]update-grub every time you modify /etc/default/grub.  Is this accurate?[/FONT]

---

### Post by matt_symes on 2011-03-31
Hi

> ... what's the delimiter ...

The delimiter is a space.

> Also, I read you must run update-grub every time you modify /etc/default/grub. Is this accurate?

Yes.

```
sudo update-grub
```

Kind regards

---

### Post by jpgator on 2011-03-31
Thanks so much for the help, it's working perfectly now. Here's what the top of my /etc/default/grub file looks like if it will help anyone else (commented out the original linux_default line while testing).
 
```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet"
GRUB_CMDLINE_LINUX_DEFAULT="rootdelay=180 quiet"
GRUB_CMDLINE_LINUX=""

```

---

