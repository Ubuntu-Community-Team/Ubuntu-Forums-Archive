---
title: "FFADO/Firewire/Jack"
date: 2010-12-11
forum: Ubuntu Studio
---

### Post by dawiba on 2010-12-11
Hi Everyone

Jack has been running fine but last night it stopped and wouldn't start again. Of course, I started messing around and ended up in a worse situation.

So because this is still a fairly new install, I decided just to reinstall Ubuntu. Once I'd done that, I reinstalled Jack and the other audio software I want to use, but now I can't get Jack to start at all with my firewire interface. It starts fine using a USB interface, but nothing with firewire. As far as I can work out, the ffado-dbus-server isn't running or won't start, so Jack doesn't see the firewire interface.

Any help here would be very welcome :)

---

### Post by trulan on 2010-12-11
Do you get any meaningful output from 
```
ffado-diag
```

---

### Post by dawiba on 2010-12-12
I get a load of stuff with this at the end

```
=== REPORT ===
FireWire kernel drivers:

The new FireWire kernel stack is loaded. 
This stack is not supported by FFADO. Please use the old stack.
```

In the meantime, I was thinking what to do next, when I got a popup telling me there were drivers for my video card. So, because I had been using that driver before I reinstalled, that's what I did. Then I thought, 'Why not?' and tried Jack again. It started :D

I promise, all I did between Jack starting and not starting was to install the video driver. I have no idea why this should have made a difference, but it looks like it has.

All that aside, looking at the output from ffado-diag, do I need to load the old firewire stack?

---

### Post by trulan on 2010-12-12
It is regrettable that ffado-diag still reports that the new stack is not supported - The new stack **is** supported in Ubuntu Maverick and will be the only option in Natty.  It does seem to take some fiddling to get things to start up on a new setup, I'm not sure why.  Possibly rebooting helped, or something was updated during installing the video drivers (such as ldconfig or maybe a rebuilding of the initramfs) but at any rate glad to hear it is working.

---

### Post by prokoudine on 2010-12-12
> **dawiba said:**
> I promise, all I did between Jack starting and not starting was to install the video driver. I have no idea why this should have made a difference, but it looks like it has.

Maybe it just ran modprobe raw1394 for you?

---

### Post by dawiba on 2010-12-12
I'm really not sure what happened myself, but it works now. I think I've got what I need in terms of software now, so I'll leave well alone.

For what it's worth, I had been trying to install gdigi when I lost everything (sound). It was after I did...

```
sudo apt-get install build-essential libasound2-dev libgtk2.0-dev libglib2.0-dev libexpat1-dev
wget http://d10xg45o6p6dbl.cloudfront.net/projects/g/gdigi/gdigi-0.2.0.tar.bz2

```

...that everything started to go wrong.

It seems it can't be downloaded anywhere anymore, so I'll give up on that as it's not something that's essential for me.

Thanks for the replies and the help/advice

---

### Post by trulan on 2010-12-12
> **prokoudine said:**
> Maybe it just ran modprobe raw1394 for you?
No he's running stock 10.10, with the new firewire stack.  So running modprobe raw1394 would cause problems, not solve them.

No clue why gdigi would have caused problems - and build-essential and those -dev packages should've been fine as well.  Anyway, I hope it continues to work for you.  I've been imaging my studio partition onto an external USB hard drive (very easy to do with gparted) just in case I royally break something and need to restore my system.  I haven't needed it yet but I've had some close calls.

---

