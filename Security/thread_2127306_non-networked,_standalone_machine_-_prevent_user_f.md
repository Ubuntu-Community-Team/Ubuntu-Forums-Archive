---
title: "non-networked, standalone machine - prevent user from copy files off of computer"
date: 2013-03-19
forum: Security
---

### Post by SwanRonson on 2013-03-19
hi there,
i need to lock down a machine (running 12.04 LTS) so that guest users (who, for various reasons, will be logged in via a named standard account, not the "Guest" account) cannot copy any files off of the machine.

LAN and wireless access will be turned off via disabling of said components via pwd-protected bios settings.

i would like to prevent the users from plugging in a USB drive into the open ports and simply dragging and dropping files on to the USB stick. i know i can disable the individual USB ports via pwd-protected bios settings, but that still leaves the issue of needing 2 active USB ports for the keyboard and mouse to plug into. (i have already thought of shutting down all USB ports and using PS/2 keyboard/mouse, but i'd like to be able to use USB keyboard/mouse due to availability).

so, my questions are:
[LIST]
[*]any tips on how to allow use of USB keyboard/mouse but prevent use of USB drive/stick or any other USB-based device?
[*]any other security holes that i should be aware of which would allow guest users to copy files off of the machine?
[/LIST]

thanks so much!

---

### Post by sanderj on 2013-03-19
When I plug in a USB-flash-stick, lsmod shows as extra modules:

> nls_iso8859_1          12713  1 
> usb_storage            57199  1 

So, how about disabling (the loading of) usb_storage? Maybe block it in /etc/modprobe.d/blacklist, or just remove usb-storage.ko from your system, 

/lib/modules/3.8.0-13-generic/kernel/drivers/usb/storage/usb-storage.ko

Or compile a kernel without usb_storage?

EDIT: tested it:

Unplug usb storage sticks.

Then

```
sudo rmmod usb_storage
sudo nano /etc/modprobe.d/blacklist.conf
```

at the end, add:

```
blacklist usb_storage
```

Save and exit.

Now plug in a usb stick ... and see that it does NOT work ...

---

### Post by Cheesemill on 2013-03-19
I have tried this and it does work.

It was quite some time ago so I can't remember the exact details but blacklisting the usb_storage module is definitely the way to go.

Some other considerations...
Make sure your machine doesn't have a CD-R or DVD-R drive.
Is it feasable for a user to make a copy either by simply copying the data with a pen and paper or by taking a photograph?
How physically secure is the machine? Could someone bypass your OS altogether by booting a live CD/USB or could they simply walk out with the hard drive in their pocket?

As any good admin will tell you physical access = root access, the only method you can use to protect against the users having physical access is to use full disk encryption. Ideally your machine would be locked up tight in a secure cabinet, with only keyboard/mouse/monitor/power cables exiting the case.

---

### Post by SwanRonson on 2013-03-21
thanks fellas. i will try the usb_storage method right now.

---

### Post by SwanRonson on 2013-03-22
additional question re usb_storage:

is there any way to only disable it for a certain user, or for non-admin users? i'd like to be able to log in as my administrator account and add files if necessary. thanks so much fellas!

---

### Post by sanderj on 2013-03-22
> **SwanRonson said:**
> additional question re usb_storage:

is there any way to only disable it for a certain user, or for non-admin users? i'd like to be able to log in as my administrator account and add files if necessary. thanks so much fellas!

First tell us if the method described works for you ...

---

### Post by SwanRonson on 2013-03-22
> **sanderj said:**
> First tell us if the method described works for you ...

you're right, i got ahead of myself.

the usb_storage method didn't work for me. i'm guessing i'm doing something wrong?

i did the [FONT=courier new]sudo rmmod usb_storage[/FONT]

and then when i open blacklist.conf, at the end it says:

[FONT=courier new]blacklist usb_storage[/FONT]

is there anything else i should check? would it be helpful if i post a printout of lsmod?

---

### Post by Stonecold1995 on 2013-03-23
Just a warning: while you can prevent users from copying files via USB, if they know any programming they could set certain files to be uploaded online once network is re-enabled, then have the script/program delete itself.

---

### Post by SeijiSensei on 2013-03-23
Filling the USB ports with epoxy is another effective solution.  I'm not joking, either.  That's a pretty common practice in security conscious organizations.  If you need to enable a mouse and keyboard, use wireless ones and mount the receiver with super glue and epoxy so it cannot be removed.

---

