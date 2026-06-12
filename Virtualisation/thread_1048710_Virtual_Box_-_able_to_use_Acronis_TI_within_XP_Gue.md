---
title: "Virtual Box - able to use Acronis TI within XP Guest?"
date: 2009-01-23
forum: Virtualisation
---

### Post by Orographic on 2009-01-23
Hi all,

I am thinking of installing VB (either OSE or 2.1.2) on my Intrepid system and then installing XP in Virtual Box.

My questions:

Can I then install Acronis TI into my XP guest and restore a previously made .tib file of XP that is activated?

What would be the best way to do this?

---

### Post by Shazaam on 2009-01-24
Sounds like a good idea as long as Acronis will run in a virtual machine. You will probably need to make a virtual machine with multiple virtual drives.

Some links...
[http://www.acronis.com/resource/tips-tricks/2008/backup-running-virtual-machine.html](http://www.acronis.com/resource/tips-tricks/2008/backup-running-virtual-machine.html)
[http://www.google.com/search?hl=en&as_q=&as_epq=virtual+machine&as_oq=Acronis&as_eq=&num=10&lr=&as_filetype=&ft=i&as_sitesearch=&as_qdr=all&as_rights=&as_occt=any&cr=&as_nlo=&as_nhi=&safe=images](http://www.google.com/search?hl=en&as_q=&as_epq=virtual+machine&as_oq=Acronis&as_eq=&num=10&lr=&as_filetype=&ft=i&as_sitesearch=&as_qdr=all&as_rights=&as_occt=any&cr=&as_nlo=&as_nhi=&safe=images)

---

### Post by Dedoimedo on 2009-01-24
Sure, it will work.
I've done it a few times. Works great ...
Dedoimedo

---

### Post by Orographic on 2009-01-24
Could you explain the way in which you did it? Would be great to know the steps you took.

---

### Post by Dedoimedo on 2009-01-25
Hello,

I'll even write a tutorial, but that will take some time ... :)

Here's what I did:

1) Created a virtual machine with 2 partitions, c: system and d: data. Installed XP.
2) Created Ultimate Boot CD for Windows with ATI plugin. See here:
[http://www.dedoimedo.com/computers/ubcd4win.html](http://www.dedoimedo.com/computers/ubcd4win.html)
3) Booted the virtual machine of CD; this can be an iso, as well.
4) Created an image of the c: partition and saved it to d: drive. If you have network and sharing enabled in the PE environment, you can also save to your host.
5) Boot the virtual machine.
6) Copy the image to anywhere you like.

An even simpler method:

vmdk files are just ... files. They contain your entire virtual machine. So you can simply copy them - this is equivalent to full hard disk copy / clone. And you can also use tar and bunzip/gunzip to make them smaller.

Another method:

Use PartImage or CloneZilla for the task. I have written a step-by-step tutorial for this and demonstration was done in virtual machines, including XP, so not only does it work, it works great and reliably:

[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)

Cheers,
Dedoimedo

---

### Post by Orographic on 2009-01-25
Thanks for putting in so much effort, it is appreciated. I will slowly look into it all as time permits.

---

