---
title: "HDD encryption with keyfile on USB (new method)"
date: 2008-06-25
forum: Security
---

### Post by antipode888 on 2008-06-25
I'm not sure if this is the right place to post this (my first post), but I've put together what I think is a new + improved variation on full hard disk encryption in Ubuntu.

It includes:
* full hard disk encryption (with the exception of /boot)
* storage of the encryption key on an encrypted external device like a USB drive or SD card
* swap encryption with a randomized key
* simplified step-by-step process within the native Live CD environment (the ONLY extra package installed being cryptsetup)
* actual desktop installation accomplished with the standard GUI setup wizard (this last fact is the main newness about my article)

Anyway, please give it a whirl:
[http://mazeoflies.com/articles/2008/06/09/ubuntu-hard-drive-encryption-with-external-key](http://mazeoflies.com/articles/2008/06/09/ubuntu-hard-drive-encryption-with-external-key)

I'd love to hear what you guys think.

---

### Post by hyper_ch on 2008-06-25
why not posting it here into the howto section?

---

### Post by Chayak on 2008-06-25
Been done before using the alternate install CD with the entire /boot partition on the USB thumbdrive.  Though installing in the live enviornment is different.

---

### Post by antipode888 on 2008-06-27
@hyper_ch: I can't use the "Tutorials & Tips" section because according to the guidelines "Posts that contain only links to offsite pages or blog posts" are not considered tutorials.  My HOWTO is offsite, so this looked like the most relevant category.

@Chayak: The method I'm talking about doesn't put the /boot partition on the USB thumbdrive but rather just the encryption key.  That much has definitely _[been done before]("https://help.ubuntu.com/community/GutsyLUKSTwoFormFactor")_ but I'm hoping that my article develops the idea further.

---

### Post by hyper_ch on 2008-06-27
well, I meant you could just copy'n'paste the whole howto here also

---

