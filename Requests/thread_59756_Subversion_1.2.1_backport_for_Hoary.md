---
title: "Subversion 1.2.1 backport for Hoary"
date: 2005-08-25
forum: Requests
---

### Post by supanova on 2005-08-25
Hi All

Where could I find a backport for Subversion 1.2.1? If it does not exist would someone kindly consider it
 
Thanks

---

### Post by supanova on 2005-08-29
Hi 

I see that subversion 1.2.0 is in the breezy repos, which is great. I see that the subversion site mentions that 1.2.3 fixes several bugs in 1.2.0

I see that the debian site has a deb file for 1.2.3... will ubuntu make this availble? If not then is it safe to use the installation from the debian site?

One other thing...

How does something go from experimental to stable if the subversion site lists 1.2.3 as stable already... was just wondering what the process is

Thanks  :razz:

---

### Post by jdong on 2005-08-29
It requires backporting of perl bindings and swig libraries, an upward dependency spiral. Unfortunately, it can't be backported.

---

### Post by retrakker on 2005-08-31
Well, I just built it from source. Make sure you have uninstalled everything regarding Subversion before you start. I needed 1.2.x for converting my CVS repositories. Now I can start with cvs2svn.

---

### Post by jdong on 2005-08-31
Umm,  the current Breezy version fails at ./configure due to old swig libs...

---

### Post by retrakker on 2005-08-31
[QUOTE=jdong]Umm,  the current Breezy version fails at ./configure due to old swig libs...[/QUOTE]
 Sorry, what I didn't mentioned: I compiled from vanilla sources, not from the debian version. It might be that there are things patched into the Breezy package that are not present in the vanilla stuff. I just mentioned that for people who need a svn 1.2.x running (i needed fsfs support for converting a bunch of CVS repositories). It might be not suitable for backporting.

Update: just checked ./configure --help 

```

--with-swig=PATH        Try to use 'PATH/bin/swig' to build the swig
                          bindings. If PATH is not specified, look for a
                          'swig' binary in your PATH.

```

---

### Post by supanova on 2005-09-06
Hi All

Is the following correct

> The problem with backporting is making sure that whatver is being backported does not break anything else in the "officially supported" supported repositories?

This leads me to something else....

Disk space is cheap these days so why not simply be able to download everthing at once. You compile and indicate where you'd like everything installed. e.g. /apps/svn1.2.3 and presto.


Seems like backporting is pain because we are always worried about breaking something else. I see the point if one needs complete integration, but who really cares if python X is installed and a whole bunch of packages need that X version but what you are trying to install needs version Y.... then you thoughts might be "no problem.... I'll run ver Y just for this".... but you can't .... i'm babbling now

Ciao

---

