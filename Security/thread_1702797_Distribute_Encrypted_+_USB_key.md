---
title: "Distribute Encrypted + USB key"
date: 2011-03-08
forum: Security
---

### Post by JFollest on 2011-03-08
Is it possible:
 setup an Ubuntu install
Then Encrypt it with Luks or whatever i chose
Set it up to boot off of a USB key only

Once thats done can I throw it all back on a cd to be used as a distribution.

The reason I ask is, I need to setup some good security for a friends computer, however I dont have direct access to it. If I can set it up in this way then mail them the Disc and actual USB key 

Would it work?
What program would I use to make the distribution Disc?

Thanks for your help!
Joe

---

### Post by bodhi.zazen on 2011-03-08
> **JFollest said:**
> Is it possible:
 setup an Ubuntu install
Then Encrypt it with Luks or whatever i chose
Set it up to boot off of a USB key only

Once thats done can I throw it all back on a cd to be used as a distribution.

The reason I ask is, I need to setup some good security for a friends computer, however I dont have direct access to it. If I can set it up in this way then mail them the Disc and actual USB key 

Would it work?
What program would I use to make the distribution Disc?

Thanks for your help!
Joe

I think it would be easier to simply encrypt the resulting iso.

If you want to encrypt the installation it needs to be set up (the crypt + LVM (if needed) + the initramfs) at installation.

---

### Post by JFollest on 2011-03-08
Thanks for the reply.

How could I make this simple for someone with minimal computer knowledge though?
This is why I am trying to do it all beforehand. This way they just install and they are good to go, and noone can get in their system without the USB key.

Thanks
Joe

---

### Post by JFollest on 2011-03-08
Or are you saying 
Do everything I need to
Make it an Iso 
then they install that way..?

Thats what I am thinking but was wondering if it would work correctly as long as I sent the USB key with it.

Thanks again
Joe

---

### Post by bodhi.zazen on 2011-03-08
Make a custom iso and have your friend install the iso.

I seriously doubt you need to encrypt the iso or send a usb key.

Encrypting your friends installation without teaching him or her to manage encryption is cruel and may easily result in data loss.

---

### Post by JFollest on 2011-03-08
> **bodhi.zazen said:**
> Make a custom iso and have your friend install the iso.

Yes but the ubuntu will be alternate and encrypted for them the made into an iso.

I seriously doubt you need to encrypt the iso or send a usb key.

Lol, no i didnt meant encrypt the iso.
The USB key is for the boot up off of USB. They need to have security where noone can get in except them with USB key.

Encrypting your friends installation without teaching him or her to manage encryption is cruel and may easily result in data loss.


Thanks again
Joe

---

