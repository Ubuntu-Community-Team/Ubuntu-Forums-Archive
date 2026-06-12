---
title: "ZoneMinder: move Events storage location"
date: 2009-09-25
forum: Server Platforms
---

### Post by joeinbend on 2009-09-25
I posted over in the ZoneMinder forums as well but no response: I have installed ZoneMinder 1.23.3 on my Ubuntu server 9.04, everything works great. In the Options, I moved the storage location for Events from its' default over to my RAID volume, to keep it from eating up the space on my small OS drive. It stores the events, I can see them, but I cannot play them back in the browser. The likely suspect is that it needs a link between the old path and the new one, but I need the actual syntax on now that should be. Anyone done this and can point me in the right direction? I need actual verbatim lines if it is for adding a symlink, as I am still pretty green at understanding how symlinks play out.

Cheers!

---

### Post by tgalati4 on 2009-09-30
man ln

Something like:

sudo ln -s /RAID/New_events_location /home/user/original_events_location

---

### Post by joeinbend on 2009-10-01
Here's what I ended up doing, and I'm not sure if this is the recommended method, but it appears to have worked. I left the path settings in ZoneMinder alone, then at the console I went to /usr/share/zoneminder and deleted the folders "events" and "images", then replaced them with symlinks to where I wanted the data to be stored. In my case it was "sudo ln -s /var/RAID/ZM/EVENTS events" and likewise for the "images" path. Restarted Zoneminder, and I can see that my data is being dumped to the correct location.

This is something I just pieced together with tinkering with symlinks; is there a better way to do this, a "best practices", or a reason not to do it the way I did?

---

### Post by mcreef on 2013-04-22
I know this is an old post, but it was the first that came up in my search, and in case anyone else stumbles upon it in the way I did, I figured I would add a note...

[This zoneminder wiki page]("http://www.zoneminder.com/wiki/index.php/Using_a_dedicated_Hard_Drive"), seems to point to a potential problem with the above listed technique, so give it a read before creating a symlink.

---

### Post by wildmanne39 on 2013-04-22
Thread closed. Please do not post in old threads.

---

