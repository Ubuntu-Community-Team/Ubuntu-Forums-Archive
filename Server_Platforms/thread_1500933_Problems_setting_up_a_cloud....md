---
title: "Problems setting up a cloud..."
date: 2010-06-03
forum: Server Platforms
---

### Post by EclipseOTO on 2010-06-03
Hey y'all,

So I'm trying to set up some semblance of a cloud set up, but I'm running in to major problems.  I've been following the guide here:

[https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)

and I get to the part where I try and start an image, it says ```
FinishedVerify: Not enough resources (VmTypeAvailability{type=VmType{name='m1.small', cpu=1, disk=2, mem=128},
max=0, available=0} < 1: vm instances.

```So I found this website:

[http://www.smop.co.uk/mediawiki/index.php/Eucalyptus](http://www.smop.co.uk/mediawiki/index.php/Eucalyptus)

where it suggested that maybe my node wasn't registered.  Now when I try to register the node, again following those earlier instructions I get the error:
```

/usr/bin/ssh-copy-id: ERROR: No identities found

```when I enter
```

sudo -u eucalyptus ssh-copy-id -i ~eucalyptus/.ssh/id_rsa.pub

```can someone give me a hand with setting this up please?

Thanks a ton,
Pete

---

### Post by suseendran.rengabashyam on 2010-06-04
Hi,

Have a look at this link for more details

[http://cssoss.wordpress.com/2010/03/22/more-cores-more-vms/](http://cssoss.wordpress.com/2010/03/22/more-cores-more-vms/)

and for a comprehensive UEC guide try

[http://cssoss.wordpress.com/](http://cssoss.wordpress.com/)

Hope this helps.

---

### Post by EclipseOTO on 2010-06-04
Ah!  These instructions are much better!!! Thank you!

---

