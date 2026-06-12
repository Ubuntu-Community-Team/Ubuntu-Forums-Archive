---
title: "Should I use webmin? ... suggest potential problems, or alternatives please"
date: 2009-03-05
forum: Server Platforms
---

### Post by davewantsmoore on 2009-03-05
Continued from discussion on webmin debian incompatibilities here:  [http://ubuntuforums.org/showthread.php?p=6804162](http://ubuntuforums.org/showthread.php?p=6804162)

> **memilanuk said:**
> I don't necessarily have a problem with using the CLI to set up or maintain a machine... but for some things I think it's a bit simpler/easier to be able to 'see' things in a GUI.


You and I are in the same situation.

I am now just about to setup a home server, and trying to chose a distro and method of management.

(From my reading, it seems the biggest issue with webmin is the fact that it doesn't obey the debian standard for maintaining config files.)


I am seriously considering ubuntu + webmin as my home server... but I'd like to know from users out there what currently works and what doesn't under webmin on ubunutu.

I'd like my server to be able to do LAMP/proxy/DNS/LDAP and manage storage (NFS/CIFS/RAID5).

I'm quite happy to handle maintainability problems (upgrades etc.) myself.... but if any of these above features are particularly broken, then I'll have to reconsider either webmin or ubuntu.


I realise the future is eBox ... but it doesn't quite include the features I want... hopefully it will in future.

I'd prefer not to move to another Linux variant, as I am quite comfortable on debian based distro.

---

Can I get some comments from those using webmin as to what is currently broken on deb/buntu ?!

If anyone advises me to steer clear of webmin... then what other options do I have? (eBox doesn't offer everything I want) ...  Is there anything cool coming in 9.x that I should wait around for?

---

### Post by benjicharlton on 2009-03-05
I use webmin to manage my ubuntu server....but I install it from latest releases on the webmin site....

It is working with no tweaking needed.  

Webmin is no longer part of the ubuntu universe.  

But the webmin packages are still packaging for ubuntu server (deb)

search for sites which explain the installation...follow the instructions on a clean server..
works quite well out of the box..

---

### Post by davewantsmoore on 2009-03-05
> **benjicharlton said:**
> Webmin is no longer part of the ubuntu universe.  

Sure, I understand this.


> **benjicharlton said:**
> works quite well out of the box..

So all of the services I listed previously, are able to be configured and work correctly ?!   Excellent.

---

### Post by sloggerkhan on 2009-03-05
I'm not sure how much gui front end you are looking for, but I just install lxde or xfce on my server, don't have it boot to X, though. Just when I log in I can xforward or startlxde or startxfce if I need a gui.

---

### Post by davewantsmoore on 2009-03-06
> **sloggerkhan said:**
> I'm not sure how much gui front end you are looking for, but I just install lxde or xfce on my server

Thanks.  Although having X installed on my server doesn't really help much in managing things like: firewall rules, squid, bind, file shares, ldap, etc.

I will give webmin a go and report back...  I'd truly like to use eBox, but it doesn't seem to be as complete as I require.

---

