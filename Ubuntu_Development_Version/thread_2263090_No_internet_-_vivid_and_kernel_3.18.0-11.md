---
title: "No internet - vivid and kernel 3.18.0-11"
date: 2015-01-29
forum: Ubuntu Development Version
---

### Post by grahammechanical on 2015-01-29
apt-get update gives for all repositories

> 101: network is unreachable 

Web browsers give

> This webpage is not available. error code: ERR_ADDRESS_UNREACHABLE

OS is connected to the router which in turn is connected to the ISP. The router connectivity tests shows all is connected to the ISP and beyond.

Run recovery mode>network and got a white flashing cursor. Cannot update that way. 

Loaded 14.04.1 which I keep as a fall-back for times like this and I can update and connect to the web. That confirms that the UK is still connected to the internet and that I did not go to sleep in a constitutional monarchy and wake up in a dictatorship.

Loaded vivid with kernel 3.18.0-9 and I am now using vivid that I can update and connect to the web with.

Conclusion: The latest is not always the greatest. Don't use the development release as the only OS.

Regards.

---

### Post by harry332 on 2015-01-29
Did you try kernel 3.18.0-12, in proposed now?
That works fine here. But then again, so did 3.18.0-11 also work fine.

---

### Post by osmoma on 2015-01-29
Are we in the same boat (same error)?
Ref: [http://ubuntuforums.org/showthread.php?t=2261135](http://ubuntuforums.org/showthread.php?t=2261135)

I will now try the proposed core 3.18.0-12.
Run: 
$ software-properties-gtk
and enable `Pre-released updates (vivid proposed)`  and `Canonical Partner` repositories.  Then

sudo apt-get update 
sudo apt-get upgrade 
sudo apt-get dist-update

---

### Post by ventrical on 2015-01-29
It just updated network mgr/others and it is working ok here in 3.18. n-11

---

### Post by grahammechanical on 2015-01-29
An update brought in kernel 3.18.0-12 and the problem is now fixed. For a short while today the development release was not so boring.

---

