---
title: "Automounting USB harddrive?"
date: 2007-06-21
forum: The Cafe
---

### Post by mlanza on 2007-06-21
I have 2 Western Digital USB harddrives for Dell.  One--I've had for some time--is connected to the back.  It's label is DOCS.  The other is fairly new.  It is connected to a USB port on the front.  It's label is MEDIA.

The DOCS drive successfully automounts every time.  The MEDIA drive automounts sometimes, but is inconsistent.  If I pull the USB cord and reconnect it signals that a USB device has been connected and mounts.

What do I need to do to cause the drive to successfully automount on every boot?

~Mario

---

### Post by Polygon on 2007-06-21
im pretty sure that if you just leave it plugged in when the comp is off, then turn on the computer, it SHOULD automount fine.

but if that doesnt work, try putting a entry in /etc/fstab for the hard drive and it should mount on boot.

---

### Post by prizrak on 2007-06-21
I don't have a problem automounting my USB drives Hard or otherwise ;)

---

### Post by dkaddict on 2007-06-22
> **prizrak said:**
> I don't have a problem automounting my USB drives Hard or otherwise ;)

prizrak. With all due respect m8, saying that your HD gets mounted isn't really going to be of much assistance to the person who started this thread. Perhaps it may help if you explained how you have set yours up eh? I dunno thugh, I may be lacking the requisite telepathic powers to operate with all of the clairvoyant Ubuntu heads.

Mlanza,

I am nothing other than a slightly advanced point and click merchant but managed to solve the problems I had with getting USB to work properly on my notebook. My devices were only recognised if I plugged them before I switched my notebook on. It was a right pain for a whie. I tried everything, like editing 'fstab' and using 'pmount'. It got really confusing because some threads talked adding devices to 'fstab' while others said that now the 'pmount' command should be used instead of adding drives to 'fstab'. I found so much information on the subject of mounting USB drives, I couldn't see the wood for the trees.
Check these out. I was just too much of a newb to know where to start. Obviously, none of the many how2s etc in these links helped me at all.

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=Mount+USB+devices&fullsearch=Text](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=Mount+USB+devices&fullsearch=Text)

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=automount+USB&fullsearch=Text](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=automount+USB&fullsearch=Text)

I had virtually given up looking for an answer to my problem. I happened upon the solution by chance.

I found out that it was something to do with ACPI. There is loads of stuff which can help with ACPI and USB. 

I posted how I got mine working here>>

[http://ubuntuforums.org/showthread.php?t=477270](http://ubuntuforums.org/showthread.php?t=477270)

It got approved by someone here but again, I am a novice, so...

Hope I have helped a little

peace

dk

---

### Post by prizrak on 2007-06-22
> **dkaddict said:**
> prizrak. With all due respect m8, saying that your HD gets mounted isn't really going to be of much assistance to the person who started this thread. Perhaps it may help if you explained how you have set yours up eh? I dunno thugh, I may be lacking the requisite telepathic powers to operate with all of the clairvoyant Ubuntu heads.


dk
Hehe, sorry you are correct. Lack of sleep is catching up with me. 

OP,
Have you tried swapping USB cables between the two to see if it's a cable fault? It sounds like hardware issue to me. Another possible thing to do is perhaps refresh the firmware on the drive, there might be something wrong with that. Be very careful with that though, you can royally screw your drive.

---

