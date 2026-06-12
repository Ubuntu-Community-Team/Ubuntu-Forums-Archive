---
title: "cdrom not accessible through Brasero"
date: 2009-02-22
forum: Server Platforms
---

### Post by finite9 on 2009-02-22
I run server 8.10 with no X, but I installed a few programs and run them with X11 forwarding on a client.  One of them is Brasero for burning ISOs on the server, but when I start it via X11 forwarding, it cannot 'see' the dvdrom drive on the server to be able to format the inserted DVD-RW.  As in, when I select Erase from the menu, everything is greyed out and my LiteOn drive is not listed in the drop down box.  Not that I can select the drop down box as all the controls are greyed out.

Does anyone have any tips on what the problem could be?  How can I format a DVD-RW at the terminal and how do I burn an iso from the terminal?

EDIT:

I just found another post on google (ubuntuforums) and a suggestion was to post output of lshw, so here is my output.  Notice that the name is LiteOn DVDRW (which it is) but capabilities says that it is not a DVD-RW drive.  Why?

```

sudo lshw -class disk -class storage
```

```
*-cdrom
          description: DVD writer
          product: DVDRW SOHW-1653S
          vendor: LITE-ON
          physical id: 0.1.0
          bus info: scsi@6:0.1.0
          logical name: /dev/cdrom
          logical name: /dev/cdrw
          logical name: /dev/dvd
          logical name: /dev/dvdrw
          logical name: /dev/scd0
          logical name: /dev/sr0
          version: CS0M
          capabilities: removable audio cd-r cd-rw dvd dvd-r
          configuration: ansiversion=5 status=nodisc
```

---

### Post by finite9 on 2009-06-08
I find I get zero replies to my posts these days.  If you want to do a job right, you need to do it yourself:

It was because it was an IDE device and I had set my bus in the BIOS to AHCI, which does not work nicely with IDE devices.  I had to go out and buy an SATA DVD-RW drive and then it all worked like a charm.

As I was dependant on best performance for my RAID disks, I did not want to go with IDE compatible mode in the BIOS.

---

