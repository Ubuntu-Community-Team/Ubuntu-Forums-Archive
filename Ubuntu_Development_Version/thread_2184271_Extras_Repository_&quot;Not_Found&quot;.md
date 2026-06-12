---
title: "Extras Repository &quot;Not Found&quot;"
date: 2013-10-28
forum: Ubuntu Development Version
---

### Post by fantab on 2013-10-28
Installed Trusty Development yesterday. When I run 'apt-get update' I get:

```
...
Err http://extras.ubuntu.com trusty/main Sources                              
  404  Not Found
Err http://extras.ubuntu.com trusty/main amd64 Packages                                 
  404  Not Found
Err http://extras.ubuntu.com trusty/main i386 Packages                                  
  404  Not Found
...

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/main/source/Sources  404  Not Found

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Is it just me or something wrong with the repo?

---

### Post by David D. on 2013-10-28
The Extras reproository is not active for Trusty yet.

---

### Post by sammiev on 2013-10-28
You can # then out for now or switch them to saucy.

---

### Post by Cavsfan on 2013-10-28
Yes, I switched my extra to saucy at the suggestion of some kind person on here can't remember. You can right click on it in the terminal and then "open link" you will see that tasty has not been added yet.
[http://extras.ubuntu.com/ubuntu/dists/](http://extras.ubuntu.com/ubuntu/dists/)

I keep checking it from time to time. I'm sure when it comes up someone will mention it.

---

### Post by fantab on 2013-10-28
I thought so.
Thanks...

---

### Post by Sworddragon on 2013-11-01
> **David D. said:**
> The Extras reproository is not active for Trusty yet.

I'm wondering why it isn't simply cloned from/pointed to the Saucy repository as Trusty installations will still need the Saucy entries to get access to all packages.

---

### Post by Cavsfan on 2013-11-02
> **Sworddragon said:**
> I'm wondering why it isn't simply cloned from/pointed to the Saucy repository as Trusty installations will still need the Saucy entries to get access to all packages.

I wondering why **Oneiric** is still on that list. It has gone bye bye quite a while ago. It reached EOL on May 9 2013.
But look at how early this is in the cycle too as to why Trusty hasn't been added.

Just use Saucy for now and then when Trusty is added fix it.

---

### Post by Cavsfan on 2013-11-21
I re-installed and commented out the extra repository. I want this to be totally Trusty with nothing else mixed into it.
I wonder if someone would be willing to let us know when there is a Trusty extra repository?
I certainly would be appreciative! :)

---

### Post by oldos2er on 2013-11-22
[s]It's working for me.

Edit: I should specify I'm using Server, not desktop. Not sure if that makes a difference or not.[/s]

Edit 2: Someday I may learn to engage my brain before posting.

---

### Post by Cavsfan on 2013-11-22
> **oldos2er said:**
> It's working for me.

Edit: I should specify I'm using Server, not desktop. Not sure if that makes a difference or not.

Thanks but I guess it does matter.

[http://extras.ubuntu.com/ubuntu/dists/](http://extras.ubuntu.com/ubuntu/dists/)

We all get an error with extras uncommented out.

---

### Post by oldos2er on 2013-11-22
No, you're right, I forgot I ran an upgrade rather than doing a clean install, so when I uncommented 'extras' it was checking the saucy repo, not trusty. D'oh.

Sorry.

---

### Post by Cavsfan on 2013-11-26
Did a clean install the other day and extras repository is commented out by default. It is important to enable Partners though which is not on by default because that is where flash updates come from.
Flash needed updating after installation.

---

### Post by philinux on 2013-11-27
Did a clean install this aft from a zsynced iso and extras were enable by default.  Although not for very long ;)

---

### Post by gacb on 2013-12-05
I expect it will have to wait until 19 December.

---

