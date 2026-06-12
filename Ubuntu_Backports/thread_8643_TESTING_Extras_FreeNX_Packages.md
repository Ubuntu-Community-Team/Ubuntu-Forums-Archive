---
title: "TESTING Extras: FreeNX Packages"
date: 2004-12-19
forum: Ubuntu Backports
---

### Post by jdong on 2004-12-19
FreeNX 0.2.7  plus the latest nx stuff has been packaged, from the Kanotix guys.

Currently in warty-extras-staging.

apt-get install freenx nxclient

nxsetup --setup-nomachine-key

---

### Post by stoffe on 2005-05-20
Hello. I'm having problems with this one... I've made two installations so far, and it all seems to work, with the little exception that I can't get a client to work so I can try it! I've looked at HOWTOs here and on other places too, and I do think that the problem is the client not the server... but I can't find any details on that.

I've tried on two machines, one with real keys and one with nomachine keys, but I can't get the nxclient to work. It just pops up a small empty dialog that can't be interacted with, apart from clicking an ok button. Tried to download other possible clients like nxdesktop(?) but nothing seems to work. 

I've a friend who runs a freenx server which he can connect to from Windows, but no dice for me there either. Of course, I don't get to the part where I can enter a ip at all for the nxclient...

On one of the machines, it says this:```
$ nxclient
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset

```if that is of any help...

Any ideas?

---

### Post by jdong on 2005-05-20
I've seen that nxclient doesn't work. That's a known issue atm.

However, the NX Server should work perfectly, as it does on two of my systems. Make sure you go into Synaptic, search for "nx", and install all relevant packages. Installing "freenx" does NOT get all the dependencies for you (known bug upstream)


Also, make sure you ran **nxsetup --install  --clean --setup-nomachine-keys**. It may look like APT already does this for you, but it isn't.

---

### Post by stoffe on 2005-05-20
[QUOTE=jdong]I've seen that nxclient doesn't work. That's a known issue atm.

However, the NX Server should work perfectly, as it does on two of my systems. Make sure you go into Synaptic, search for "nx", and install all relevant packages. Installing "freenx" does NOT get all the dependencies for you (known bug upstream)


Also, make sure you ran **nxsetup --install  --clean --setup-nomachine-keys**. It may look like APT already does this for you, but it isn't.[/QUOTE]
 Ok, then I know about nxclient, thanks! :)

I'm gonna test the server from a Windows machine, I think I got that right but had no way of testing...

Btw, if apt doesn't do those steps, why does it ask what kind of keys I want to use?

---

### Post by jdong on 2005-05-20
I don't know, that puzzled me too, unless that was work-in-progress at kalyxo.

---

### Post by ioliver on 2005-06-20
If you do

export LANG=C

before running nxclient, then you don't get the error under Hoary.

nxclient still doesn't work, but at least it gets further!

Ian

---

