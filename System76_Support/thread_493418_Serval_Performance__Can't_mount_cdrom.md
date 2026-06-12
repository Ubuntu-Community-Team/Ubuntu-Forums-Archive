---
title: "Serval Performance / Can't mount cdrom"
date: 2007-07-05
forum: System76 Support
---

### Post by hartt on 2007-07-05
Sorry to post two issues in one day. This one shouldn't be too hard though.

Just noticed that I can't mount any CDs or DVDs. I get and error message saying:

Cannot mount volume.
Unable to mount the volume 'label on disc here'.
Details: mount: mount point /media/cdrom0 does not exist

Here is the contents of my fstab if that is of any help.

# /etc/fstab: static file system information.
#
# &lt;file system&gt; &lt;mount point&gt;   &lt;type&gt;  &lt;options&gt;      $
proc    /proc   proc    defaults        0       0
/dev/sda1       /       ext3    defaults,errors=remount-ro      0       1
/dev/sda5       none    swap    sw      0       0
/dev/scd0       /media/cdrom0   udf,iso9660     user,noauto     0       0


I haven't been playing with anything. Really!

---

### Post by thomasaaron on 2007-07-06
> I haven't been playing with anything. Really!
Sure you haven't! :^o  (Just joking...)

I've never gotten that message before (that is the 'label on disc here' part of it).
That sounds like it is the name of the CD volume, which means it's a used CD.
It may be in some non-compatible format.

First, see if the drive will mount other CD's and DVD's. If it does, it is a problem with the disk.

If it won't mount any CD's, try the following command:
sudo mkdir /media/cdrom0

Then see if it will mount. (I don't think you should have to reboot for that...)

Best,
Tom

---

### Post by hartt on 2007-07-06
Hmm. That was easy. I thought I had tried it. But that seemed to have done the trick.

Ok. Maybe I was playing a bit. :biggrin: But I don't know how I could have deleted /media/cdrom0. Weird. 

Thanks a bunch.

---

### Post by mjamesd on 2007-12-19
*phew* i got this error after i had dropped my laptop... what a coincidence that i had somehow deleted /media/cdrom0 as well. thanks for the fix!

---

