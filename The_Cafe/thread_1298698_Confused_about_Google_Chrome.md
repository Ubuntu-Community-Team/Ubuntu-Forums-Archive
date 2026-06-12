---
title: "Confused about Google Chrome"
date: 2009-10-23
forum: The Cafe
---

### Post by mikebeecham on 2009-10-23
Hi guys,

I've just decided to go download Google Chrome for Ubuntu, and have to say that I'm really impressed.  One thing that does erk me, however, is the gtk theme.

For some reason it's not a true representation of my gtk theme, but seems to throw purple into the top bar.  I dont have a stitch of purple in my GTK theme, so wonder why it's doing that?

Is there anyway that I can change the colours myself to match what I use GTK-wise?  

Also, are there any GOOD Chrome theme sites?

Thanks

---

### Post by cb951303 on 2009-10-23
That bug has been fixed couple weeks ago on daily chromium builds (version 4)
[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

---

### Post by mikebeecham on 2009-10-23
Hey CB...I've added the PPA to my sources list, but it's asking me for a key?  I'm not that experienced in this area yet, so wonder if you could guide me in how to get this key, and get it recognised.

Thanks

---

### Post by cb951303 on 2009-10-23
```

-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESaSPtAEEAK1nJtoDZ0ewpOOf0ET6Vp28LqO9mB4ubWjzXyRSbiha5pCvnnSIU1K+7Gzb
t3r0iUV9eKLUmf8pqfF/9kwsoqFqFSCjp+XjUzXsEChcGBWvyfGdTX8ClFfwNxSVLvGSqmdX
gZhs0F8tQB0lPWHGy3VvEt7wG/VHqpcOYpdNYRqxABEBAAG0IExhdW5jaHBhZCBQUEEgZm9y
IGNocm9taXVtLWRhaWx5iEYEEBECAAYFAknOwV0ACgkQ9rPTxuzZSv0f2QCeLjemEkq5tYjI
xtFpw3F11szeakYAoKsBZcl3Az08cYEd9UNZjQE1j4YtiEYEEBECAAYFAknS5Z8ACgkQrZOR
ep7Yx+qZ8wCfZYBABDkYO0Ulrivpxn6hARmgLxEAn0SeWaGjVQ4UE3zpNESguf+t9K1xiLYE
EwECACAFAkmkj7QCGwMGCwkIBwMCBBUCCAMEFgIDAQIeAQIXgAAKCRBam/O7Tl4XtV/2BACs
/RTpEWB/NUlluJmp1e6iFoyyfbT+HOD3hg35aQMzbdcmijsAiY9MvIfZ0YKWyqNUdGpDj5n0
bUNO0IcvKBBkOn5o4CiBsMp4DJHdrgJU4S00nAJK00E8I/yAv+x4C9uOacW3yrzSHs7Hv/vG
6Z1Jh+1JrabK13hdhwOL8+aY6Q==
=9P6G
-----END PGP PUBLIC KEY BLOCK-----

```

Save the above key as a text file and then import the file from Authentication tab on the below window.

You can always find the keys on PPA's launchpad page, just click the "Technical details about this PPA" link.

Cheers :popcorn:

EDIT: AFAIK key retrieval from PPAs will be automatic in karmic.

---

### Post by mikebeecham on 2009-10-23
well mate, I did that...it seems to have accepted it, but there's nothing to download??

I've gone through update manager, as well as checking synaptic....nothing?

Any thoughts?

---

### Post by cb951303 on 2009-10-23
Did you update the database? Click the reload button on Synaptic.
Also did you add the correct PPA? There are 4 repos. You are probably on Jaunty (9.04) so double check that you included the Jaunty repo.

---

### Post by howefield on 2009-10-23
> **mikebeecham said:**
> well mate, I did that...it seems to have accepted it, but there's nothing to download??

You did reload Synaptic to let it pull the contents from the PPA you just added ?

---

### Post by HappinessNow on 2009-10-23
It seems like this thread would be better placed in Absolute Beginner Talk?

---

### Post by hoppipolla on 2009-10-23
> **&#20170 said:**
> It seems like this thread would be better placed in Absolute Beginner Talk?

well, sometimes Synaptic does fail to see things (ofc when apt  fails to see them too). Erm... I usually find I have put the repo in wrong or specified an incorrect or unsupported release (such as Karmic instead of Jaunty on some repos).

As long as none of that is the case and he has updated, it should be fine =S

---

### Post by mikebeecham on 2009-10-23
I dont think this should be in Absolute Beginner talk, as this has turned into a bit of a support thread, and is nothing to do with basic understanding of linux!

That said, I've checked and I can see that the correct repo has been chosen.  I've reloaded synaptic, and can see a Chromium, but this seems to be a game.  Would it be getting confused with this by any chance?

---

### Post by howefield on 2009-10-23
Isn't the pacakge called chromium-browser ?

---

### Post by joey-elijah on 2009-10-23
An easy way to install missing GPG keys is just to use this script.

You run it, it gets your keys. No input required!

[http://www.omgubuntu.co.uk/2009/09/automatically-install-missing-ppa-gpg.html](http://www.omgubuntu.co.uk/2009/09/automatically-install-missing-ppa-gpg.html)

It literally turned me into a lazy PPA adder, but hey! :p 

Run it, check for updates and then install "chromium-browser".

It might be worth bearing in mind that Chromium is less stable than Google Chrome proper. 

On the Google Chrome front - it'll get the fix from Chromium in a week or so i'd imagine. If you don't want to wait that long there are gorgeous themes available @ 

[https://tools.google.com/chrome/intl/en/themes/index.html](https://tools.google.com/chrome/intl/en/themes/index.html)

There a lot of lame choices there, too. (Mariah Carey theme anyone?!) 

If you're using Dust or Karmic's "new" default theme i recommend '[Earthy]("https://tools.google.com/chrome/intl/en/themes/theme_earthy.html")' - it's gawjus.

---

