---
title: "Broken CD drive? Integrity check on burned installer CDs failing reliably."
date: 2009-12-31
forum: System76 Support
---

### Post by phyzome on 2009-12-31
I'm preparing to reformat my panp4i and lay down Ubuntu Karmic over an encrypted partition, but I can't get the installer disk to burn properly:

[LIST=1]
[*]Torrented the alternate installer ISO
[*]Verified the MD5 of the image
[*]Burned the image to a CD-RW
[*]CD-RW failed integrity self-test (while checking liblocale-gettext-perl)
[*]Burned image to a different CD
[*]Second CD *also* failed integrity check, on *same file*
[/LIST]

Does this mean my internal CD drive is broken? I haven't had the opportunity to try booting another computer from the CDs. Besides that, what other tests can I run?

---

### Post by thomasaaron on 2009-12-31
Now, are you running 9.04? If so, Brasero in 9.04 was junk. Have you tried burning it with Nautilus?

If you're on 9.10, Brasero seems pretty solid to me so far. But you might try a different program.

---

### Post by phyzome on 2010-01-01
Using 8.10. Not sure what I used... I right-clicked the .iso and selected "Write to Disk", which I suppose is Nautilus.

---

### Post by thomasaaron on 2010-01-04
In 8.10, if you put in a CD, it opens a file browser. If you drag your .iso into that browser, and then select "Write ***" within the browser, *that* should be burning with Nautilus.

I'm not sure what the "Write" in the submenu uses. Never really did it that way. Anyway, try it the way I just mentioned. If you still get issues, it probably is your drive.

---

### Post by phyzome on 2010-01-04
I had to re-enable auto-running of programs for blank CDs in the Media Handling tab of the File Management preferences window, but yes, that's the same interface I see when using "Write to Disc" in the context menu of an .iso in Nautilus.

I have also started seeing the following message when inserting a CD:

"**Unable to mount Ubuntu 9.10 amd64:**
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

Not sure if that is related, or is just some generic failure. If you think it's the latter, I'll remove it from this post so as not to confuse future searchers. :-)

Update: I erased the disk and tried burning with Brasero (I mean, why not try?), but it stopped 34% of the way through the "creating image checksum" step. I think this means that the drive is not reliably reading around the 34% mark.

---

### Post by thomasaaron on 2010-01-04
Yeah, you might try re-seating the drive. Sometimes that helps. Perhaps it took a little bump and now has a screwy connection.

Beyond that, I'd call it toasted. 

Shoot me an email at support...at...system76...etc...

---

### Post by phyzome on 2010-01-31
I reburned the LiveCD on another machine entirely, and when I boot my laptop from it, the integrity check works. So, the optical drive must be bad. I'll email you at the support address.

---

### Post by thomasaaron on 2010-02-01
Cool.

---

