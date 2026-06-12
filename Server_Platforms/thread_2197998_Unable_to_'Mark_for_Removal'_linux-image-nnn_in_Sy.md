---
title: "Unable to 'Mark for Removal' linux-image-nnn in Synaptic"
date: 2014-01-06
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2014-01-06
Hi all

Running Ubuntu Server 12.04 and wish to remove old linux-images to make space in boot folder.

Using Synaptic and right clicking on old linux-image, the 'Mark for Removal' option is not available.

What's missing, please?

---

### Post by deadflowr on 2014-01-06
Is the linux-image package you're clicking on actually installed?
Or are you sure you're running synaptic as root?

---

### Post by philinux on 2014-01-06
See step six. Do the dry run first. 

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

---

### Post by mörgæs on 2014-01-06
What does **sudo apt-get autoremove** yield? 

(with Synaptic closed)

---

### Post by CharlesA on 2014-01-07
> **mörgæs said:**
> What does **sudo apt-get autoremove** yield? 

(with Synaptic closed)

I tried that on my 12.04 box the other day and it didn't remove any of the old kernels. I had to list them with dpkg and remove them with apt-get.

Worth a shot, though!

---

### Post by mörgæs on 2014-01-07
Hmmm, strange. For me it works using 13.10, but I don't think the version should make a difference. 
Ok, back to Philinux...

---

### Post by ChrisRChamberlain on 2014-01-07
Thanks to all who replied.

Not being a Synaptic user, 'linux-image' was entered as a search string.

The result showed in the right top pane and regardless of which version was selected, the right click would not enable 'Mark for Removal'.

Equally, 'sudo synaptic' from a command window produces the same result.

'sudo apt-get autoremove' returns 0.

So it looks like [HTML] http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/[/HTML] might be the way to go.

Question remains - why is the 'Mark for Removal' option not enabled?

TIA

---

### Post by ibjsb4 on 2014-01-07
> **mörgæs said:**
> Hmmm, strange. For me it works using 13.10, but I don't think the version should make a difference. 
Ok, back to Philinux...

I have wondered why people have recommended autoremove for old kernels.  Will not work in 12o4.

---

### Post by ChrisRChamberlain on 2014-01-08
Thanks again to all who replied.

Resolved the removal of old kernels issue with Ubuntu-tweak, [http://www.noobslab.com/2013/06/ubuntu-tweak-085-released-install-it-in.html](http://www.noobslab.com/2013/06/ubuntu-tweak-085-released-install-it-in.html).

As to why the right click options are not what one would expect in Synaptic, that remains unresolved.

---

