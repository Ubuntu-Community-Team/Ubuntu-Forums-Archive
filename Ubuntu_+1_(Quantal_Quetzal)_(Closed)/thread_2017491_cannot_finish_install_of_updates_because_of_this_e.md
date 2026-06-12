---
title: "cannot finish install of updates because of this error"
date: 2012-07-05
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-07-05
I just updated thismorning and the updates will not finish..installing..

---

### Post by Rallg on 2012-07-05
That seems like an odd error. I cannot imagine why those two packages should have the same files in a man (manual) folder.

Try this: Re-name the offending python man page to something else. See if the update proceeds.

That might mean you'll have incorrect man pages, at least for now, but how often do you use them?

---

### Post by paul_in_london on 2012-07-05
You can install the deb file like this (I had to do it earlier):

```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/python3-software-properties_0.84_all.deb
```

---

### Post by ventrical on 2012-07-05
> **Rallg said:**
> That seems like an odd error. I cannot imagine why those two packages should have the same files in a man (manual) folder.

Try this: Re-name the offending python man page to something else. See if the update proceeds.

That might mean you'll have incorrect man pages, at least for now, but how often do you use them?


Nope .. didn't work . I just most recently experiemnted with installing Thunar file manager on this install .. so I will remove that and see what happens.

---

### Post by ventrical on 2012-07-05
Here is the bug:

[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1021122](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1021122)

---

### Post by dino99 on 2012-07-05
waiting for a newer 0.8.6 package, but purging 0.8.3 first, then 0.8.4 can be installed with no problem.

---

### Post by ventrical on 2012-07-05
> **dino99 said:**
> waiting for a newer 0.8.6 package, but purging 0.8.3 first, then 0.8.4 can be installed with no problem.

The fix just came down the tube. It auto removed the python offender.

thnks:)

---

### Post by ventrical on 2012-07-05
> **paul_in_london said:**
> You can install the deb file like this (I had to do it earlier):

```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/python3-software-properties_0.84_all.deb
```

Yes .. Paul .. this worked ! :) but the fix came down the pipe simutaneously.

thnks!

---

### Post by ventrical on 2012-07-05
I have to make a side-note about apport. For once it actually worked !! LOL. Just amazing.  It recognized the bug, filed it, matched it and brought me promptly to the page. Thats a nice piece of work.

Bravo to the apport teams ! Keep that good work going!

---

### Post by spiky001 on 2012-07-08
Hi  I had the same problem the other day as well with python3 I purged as mention earlier really messed up system, No biggy What i,m asking if I reinstall from the same 12.10, downloaded about 20/07/2010 will that update ok now, or is there a newer version that would be better to download

---

### Post by ventrical on 2012-07-08
A newer version would then be updated if you chose to update the re-install.

---

