---
title: "Edubuntu gdm and lts.conf questions"
date: 2006-06-30
forum: Server Platforms
---

### Post by ckr on 2006-06-30
Hi,

I did an Edubuntu server install.  After some tweaking, I am able to get 3/4 of my lab to boot and log in to the dektop.  However, the remaining machines go throught the graphical booting process, fail to load the graphical login window and default to a text login that says "ltsp login:"  It is reporting that it is on TTY1.

Without opening every case, these computers should be similar to the others that worked.  (They are all donated computers that have been stripped down to be used as thin clients.)  I'm at a loss on why these handful of computers fail to reach the graphical login.  Also, using the users that I have created does not work at the text login, so I'm not sure what username it wants.

My thoughts are either that these non-working machines lack enough memory (thought they work fine in K12 LTSP which we've used previously), or it's a video driver issue.  For the K12 LTSP, I always modified lts.conf to use the "vesa" driver for maximum compatiblity.  However, I do not have a lts.conf file.  It is not there.   :confused:  I have no idea where the Edubuntu LTSP is pulling its config info from.  The file is not in the default location, and using the locate command with an updated database only lists the example file that comes with the system.

Would anyone have any thoughts on this?  And I would suggest a sub-forum for LTSP issue if possible.

Thanks to all,

Ckr

---

### Post by ckr on 2006-06-30
An update to my previous post.

After a moment of thinking about the login being on tty1, I switched it to tty7 and the graphical login screen appeared.  So all of the stations now work. :o 

Still, does anyone know where my lts.conf file would be?

---

### Post by nwp2006 on 2006-07-04
[QUOTE=ckr]
Still, does anyone know where my lts.conf file would be?[/QUOTE]

I am hoping someone can answer this too.  I am trying to enable sounds on the clients, but I do not have an lts.conf file.

---

### Post by b4k4 on 2006-07-04
I have the same thing with the tty1 - 7 thing. I wonder why?


There is no lts.conf on a fresh install. You have to make one. There is a howto on the wiki:

[http://www.edubuntu.org/ThinClientConfig]("http://www.edubuntu.org/ThinClientConfig")

---

### Post by ckr on 2006-07-05
Thanks for your reply.

Would you think that the video for the clients defaults to an "auto" setting, or to "vesa"?  I've found in the past that the "auto" setting had some trouble with the ancient graphics on some of my clients.  We use donated/old machines for the clients.  Also, I wonder if it takes the rest of xorg.conf from the server for the resolutution settings then?

I have a few clients where the resolution for gdm is out of range of the monitor for some reason, forcing me to ctrl-alt-+ to cycle resolutions to make the monitors legible.  This confuses the users (teachers and students) to the point where they think the machines are broken.  I've usually had to tweak lts.conf to fix this.

Overall, I think this version of LTSP is seems very good with slight testing.  Plus it's Ubuntu, which I'm thrilled to be able to use over Fedora.  Not that there's anything wrong with Fedora, of course.:-\" 

Ckr

---

