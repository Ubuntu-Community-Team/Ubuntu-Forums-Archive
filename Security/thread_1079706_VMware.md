---
title: "VMware"
date: 2009-02-24
forum: Security
---

### Post by NaF on 2009-02-24
This might not be the proper place to ask this question. But I actually don't know where else to turn.

My bank requires Internet Explorer 6+ to do online banking.
I've tried different approaches mainly had most success with ies4linux, but since my bank updated their client-side security-thingy dingy, that stopped working, and told me to update my version of IE. :mad:

My solution is just to VM Windows Xp -.- But I actually don't know how to secure it properly. I think just by only loading my VM 5 minutes a month should take it out of any imitate spotlight. 
But I've look6ed at some open source ways of securing the thing
and the firewall or packet filter PApi. Would just blocking EVERY ip in the world 'cept my bank (and any third-party involved in the transactions) secure the system truly? 
Or am I just being paranoid?

---

### Post by bodhi.zazen on 2009-02-24
Virtualization, VMWare or otherwise, keeps the guest OS (Windows) separate from the host as much as possible.

Security on the Guest is exactly the same as if you were running Windows on a physical box.

While nothing is impossible, it is very very unlikely any malware on the guest (Windows) will affect the host.

Finally, if you wish to make it a little more secure, on VMWare please use NAT (instead of Bridged networking).

Then set up Windows and your banking access, then run in a snapshot only. Any malware you get will be gone when you reboot.

---

### Post by NaF on 2009-02-24
> **bodhi.zazen said:**
> 
While nothing is impossible, it is very very unlikely any malware on the guest (Windows) will affect the host.

(...) please use NAT (instead of Bridged networking).

Then set up Windows and your banking access, then run in a snapshot only. Any malware you get will be gone when you reboot.

AH! fancy, didn't think the snapshot-direction, great tip! But concerning the use of PApi, it was more to make sure, that anyone didn't intercept my connection to the bank, but that requires malware in place, or how :oops:?

---

### Post by bodhi.zazen on 2009-02-24
Well, any connection to your bank should be https

or over ssl

ssl (https) encrypts your data so you  shoule be good to go.

If someone can crack ssl, then you and the bank are in trouble.

---

### Post by NaF on 2009-02-24
> **bodhi.zazen said:**
> Well, any connection to your bank should be https

or over ssl

ssl (https) encrypts your data so you  shoule be good to go.

If someone can crack ssl, then you and the bank are in trouble.

Thank you :-) 
(It's impossible to thank forum staff's posts?)

---

### Post by bodhi.zazen on 2009-02-24
No, we had to disable the thanks feature for the moment ;)

---

### Post by xoros on 2009-04-30
I also don't know where to post about vmware,  but since you are discussing its' security:

I want to know is there anyway to shut off vmware??  I always see a bunch of processes for vmware that are always running and they are starting up upon boot up of the os, even though I have not run vmware!  

I would like to have them shut off and only come on when I actually run vmware.   

Possible?

---

### Post by cariboo on 2009-05-01
There is the [Virtualization]("http://ubuntuforums.org/forumdisplay.php?f=308") forum, that may answer some of your questions.

---

