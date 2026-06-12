---
title: "PLF repository verification question?"
date: 2005-11-19
forum: Repositories &amp; Backports
---

### Post by wargames on 2005-11-19
Hi, I was using this PLF guide ([http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)) posted in the forums to install libdvdcss2 and w32codecs.
I used the Secondary mirrors provided in my sources.list:

## FTP mirror from [http://free.fr](http://free.fr) (french ISP)
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

And after I did a "sudo apt-get update" and then issued a "sudo apt-get install libdvdcss2" and then a "sudo apt-get install w32codecs" both times it asked me the following:

WARNING: The following packages cannot be authenticated!
 
Install these packages without verification [y/N]?

I went ahead and answered "yes" both times, but I'm now wondering if it was safe to do so?

Was it alright to go ahead and answer "yes" and install both of these packages anyway from these secondary PLF repositories? Anyone else get this warning?

---

### Post by uberlinux on 2005-11-19
I would definately trust the PLF site & repositories.

---

### Post by manicka on 2005-11-19
[QUOTE=uberlinux]I would definately trust the PLF site & repositories.[/QUOTE]
Absolutely, I would trust them. They have been well known and trusted packagers for Mandrake/Mandriva for a number of years and have recently started an Ubuntu repo.

---

### Post by wargames on 2005-11-19
Thanks guys. :)

---

### Post by rattusdatorum on 2005-12-13
and why is there the auth problem anyway?

---

### Post by manicka on 2005-12-14
[QUOTE=rattusdatorum]and why is there the auth problem anyway?[/QUOTE]

because the repo is not an official ubuntu one

---

### Post by nocturn on 2005-12-14
[QUOTE=uberlinux]I would definately trust the PLF site & repositories.[/QUOTE]

The point is not if you trust PLF, which I would also do.  But packages that are not signed by a trusted key may be tampered with.  

A cracker could have uploaded a backdoored version of the w32codecs package without the knowledge of PLF, this thread would be addressed by signing and authenticating the packages.

I'm not warning anyone not to install them, but keep in mind that this is a possibility.

---

### Post by nocturn on 2005-12-14
[QUOTE=manicka]because the repo is not an official ubuntu one[/QUOTE]

Yes, but unofficial Repos can also sign packages, you would only have to import their key once.

---

### Post by uopjohnson on 2006-02-10
Does anyone know where to find the public key for the plf repo?

---

### Post by Freyr Vanir on 2006-02-12
Here is the PLF Public Key.
[http://plf.zarb.org/plf.asc](http://plf.zarb.org/plf.asc)

You can find a link to it on this webpage too.
[http://plf.zarb.org/packages.php](http://plf.zarb.org/packages.php)

---

