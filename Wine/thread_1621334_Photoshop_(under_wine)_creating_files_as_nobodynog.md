---
title: "Photoshop (under wine) creating files as nobody/nogroup"
date: 2010-11-14
forum: Wine
---

### Post by RySites on 2010-11-14
I apologize if this should be in the wine forum but I have the feeling this problem is due to my lack of knowledge of ubuntu permissions. I checked/googled the wiki but did not see anything about this.
Anyways, everytime my wife creates an image in photoshop, the file is saved with the permissions nobody/nogroup.  I would like this to be created as wife/family.  How can I set wine up to automatically do this?  
Thanks in advance

---

### Post by waynefoutz on 2010-11-14
I'm not sure what the answer is. Running programs under WINE is more of an art than a science. Some programs run nicely, but most have glitches that can be anywhere from an annoyance to making the program downright unusable. 

Are you aware of GimpShop?

[http://www.gimpshop.com/]("http://www.gimpshop.com/") It's Gimp, the Photoshop alternative that comes with Ubuntu out of the box, but it's been altered to look and function more like Photoshop. Try downloading the .deb file and installing that on Ubuntu and see if it's a viable alternative.

here's the link to the .deb file

[http://rapidshare.com/#!download|340l32|86270575|gimpshop_2.2.11-1_i386.deb|11514]("http://rapidshare.com/#!download|340l32|86270575|gimpshop_2.2.11-1_i386.deb|11514")

---

### Post by coffeecat on 2010-11-14
> **RySites said:**
> Anyways, everytime my wife creates an image in photoshop, the file is saved with the permissions nobody/nogroup.  I would like this to be created as wife/family.  How can I set wine up to automatically do this?  
Thanks in advance

A few questions: where are the files being saved to, and what filesystem? You say that when your wife creates an image this happens. What happens when you save an image? Are you and your wife using the same machine but with different accounts or are you using different machines?

---

### Post by RySites on 2010-11-15
Hello
I am sorry...we were working yesterday and a few things came to light.
First, when she creates something on the laptop, and passes it over to the desktop, that's when the nobody/nogroup thing occurs.  While we were editing some code yesterday i noticed this.  So it's not necessarily wine/photoshop.
Second, she works on the laptop as username Wife. I am on desktop as Husband.  Both are in the Family group.  I created an account on desktop called Wife and made the UID of Wife on laptop and desktop the same. Why is it when she transfers something over the network to me, it gets the nobody/nouser designation?
thanks!

---

### Post by coffeecat on 2010-11-15
Sorry I didn't twig this yesterday, but nobody and nogroup are user and group accounts on Unix/Linux systems with UID and GID of 65534 and 65534. Tbh, I'm not really clear what they're for, but a little (a very little) on nobody:

[https://wiki.ubuntu.com/nobody](https://wiki.ubuntu.com/nobody)

If you make a test file and...

```
sudo chown 65534:65534 testfile
```... you'll see nobody and nogroup under properties.

But what this doesn't explain is why your wife's files are being reassigned to nobody:nogroup somewhere between the laptop and desktop. I have seen this once before but, frustratingly, can't remember the details and circumstances. If I find something, I'll post back.

**Edit:** I've remembered!

> **RySites said:**
> First, when she creates something on the laptop, and passes it over to the desktop, that's when the nobody/nogroup thing occurs.

You were using samba shares to do the "passing over", weren't you? Yes I've seen this when writing to a share from the remote machine. I'm not sure why, but you need to look at sharing options.

---

### Post by coffeecat on 2011-03-03
I find it quite extraordinary that the OP has never bothered to post in this thread again.

---

