---
title: "usb flash drives, some unmount, some eject  in nautilus"
date: 2012-06-04
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mc4man on 2012-06-04
I've got 9 here, 5 different manufacturers. 4 only unmount, 5 only eject from nautilus

Was wondering if anyone knew what defined that, seems to be hardware based
So - 
3 Sandisk - all unmount (the isofs partition is long gone on all
1 Kingston DataTraveler - unmount

1 Memorex TravelDrive - eject 
1 Hp 16 GB  - eject
3 pny  - all eject

The umount only get a new style icon, the eject only get  the older icon, as seen in screen of the 'new' Disks utility - another example of gnome's 'less shown the better' .
 
(- In Disks all can be unmounted or ejected, though no more power down for any usb drive of any type which isn't a big deal though useful for some

---

### Post by dino99 on 2012-06-04
have you ran pciids & usbids to update the list ?

sudo update-usbids && sudo update-pciids

---

### Post by mc4man on 2012-06-04
> **dino99 said:**
> have you ran pciids & usbids to update the list ?

sudo update-usbids && sudo update-pciids
Just tried - 
> sudo update-usbids && sudo update-pciids
[sudo] password for doug: 
--2012-06-04 10:25:19--  [http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids)
Resolving [www.linux-usb.org](www.linux-usb.org) ([www.linux-usb.org](www.linux-usb.org))... 216.34.181.97
Connecting to [www.linux-usb.org](www.linux-usb.org) ([www.linux-usb.org)|216.34.181.97|:80](www.linux-usb.org)|216.34.181.97|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 476196 (465K) [text/plain]
Saving to: `/var/lib/usbutils/usb.ids.new'

100%[==============================================================================>] 476,196      846K/s   in 0.5s    

2012-06-04 10:25:21 (846 KB/s) - `/var/lib/usbutils/usb.ids.new' saved [476196/476196]

Done.
Downloaded daily snapshot dated 2012-05-07 03:15:01

The same is still seen on flash, some eject only, some unmount only, (usb hdd's can only be unmounted

On previous 12.10 install this changed with udisks2 being installed

---

### Post by dino99 on 2012-06-04
> **mc4man said:**
> Just tried - 


The same is still seen on flash, some eject only, some unmount only, (usb hdd's can only be unmounted

On previous 12.10 install this changed with udisks2 being installed

so before getting udisk2, does these sticks managed correctly ? i suppose that some of the sticks are not fully managed yet due to missing hardware's ids

what happen on Precise with these sticks ?

---

### Post by mc4man on 2012-06-04
Opp's,  not udisks2 install, it was the upgrade of gvfs* (change there was to start monitoring udisks2

So if I where to downgrade gvfs* then all flash drives would get eject & safely remove, (power down), as would usb hdd's

Edit: the icon for these flash & all usb hdd's seems new - never seen here before, shown in screen

---

### Post by dino99 on 2012-06-04
> **mc4man said:**
> 

Edit: the icon for these flash & all usb hdd's seems new - never seen here before, shown in screen


oh yes very new, and nice :P

---

### Post by mc4man on 2012-06-04
The difference may be this in syslog - clipped out as rest per drive is the same

The flash drive(s) getting the unmount option & new icon shows this

>  doug-XPS-M1330 kernel: [   52.789248] scsi 6:0:0:0: [COLOR="Blue"]Direct-Access[/COLOR]     SanDisk  Cruzer           1.02 PQ: 0 ANSI: 2

while the one(s) getting the eject & old icon show - 
>  doug-XPS-M1330 kernel: [   43.877368] Initializing [COLOR="Blue"]USB Mass Storage driver[/COLOR]...
Jun  4 10:59:50 doug-XPS-M1330 kernel: [   43.877519] scsi5 : usb-storage 2-1:1.0
So i guess this may just be the way it is now?

---

### Post by dino99 on 2012-06-04
well dont know what the new way is

[https://launchpad.net/ubuntu/quantal/+package/udisks](https://launchpad.net/ubuntu/quantal/+package/udisks)

[http://suckered.us/site1/?__proxy_url=aHR0cHM6Ly9sYXVuY2hwYWQubmV0L3VidW50dS9xdWFudGFsL2kzODYvbGliZ2R1LWRldi8zLjAuMi0ydWJ1bnR1Nw==](http://suckered.us/site1/?__proxy_url=aHR0cHM6Ly9sYXVuY2hwYWQubmV0L3VidW50dS9xdWFudGFsL2kzODYvbGliZ2R1LWRldi8zLjAuMi0ydWJ1bnR1Nw==)

---

