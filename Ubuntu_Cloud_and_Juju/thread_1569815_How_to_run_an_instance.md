---
title: "How to run an instance?"
date: 2010-09-07
forum: Ubuntu Cloud and Juju
---

### Post by siteregsam on 2010-09-07
Hi,

I had installed Ubuntu 9.10 - Karmic Koala (i386) image from UEC store.
And after installing, i got following screen as how to start an instance...

[IMG]http://img530.imageshack.us/img530/552/howtorunhelpstoretab.png[/IMG]


When i run **euca-run-instances -k testkey --kernel eki-F63A10EF --ramdisk eri-0ABB115E emi-DFFF107A** i am getting following error....
[I]
root@sam-laptop:~# euca-run-instances -k testkey --kernel eki-F63A10EF --ramdisk eri-0ABB115E emi-DFFF107A
EC2_ACCESS_KEY environment variable must be set.
[COLOR=Red]Connection failed[/COLOR][/I]

How to setup [COLOR=RoyalBlue]EC2_ACCESS_KEY environment variable[/COLOR]?
Kindly some one help me....
Thanks in advance...

---

### Post by pnunn on 2010-09-08
You need to read the documentation mate... you need to source your eucarc file to get the environment variables set up correctly, after downloading them from the interface.

Peter.

---

### Post by baboli on 2010-09-08
> **siteregsam said:**
> Hi,

I had installed Ubuntu 9.10 - Karmic Koala (i386) image from UEC store.
And after installing, i got following screen as how to start an instance...

[IMG]http://img530.imageshack.us/img530/552/howtorunhelpstoretab.png[/IMG]


When i run **euca-run-instances -k testkey --kernel eki-F63A10EF --ramdisk eri-0ABB115E emi-DFFF107A** i am getting following error....
[I]
root@sam-laptop:~# euca-run-instances -k testkey --kernel eki-F63A10EF --ramdisk eri-0ABB115E emi-DFFF107A
EC2_ACCESS_KEY environment variable must be set.
[COLOR=Red]Connection failed[/COLOR][/I]

How to setup [COLOR=RoyalBlue]EC2_ACCESS_KEY environment variable[/COLOR]?
Kindly some one help me....
Thanks in advance...

login and run ". ~/.eucarc" you really need to read the document to get this going. I still have problem keeping the instances up and running, they terminate in 30 seconds or so.

---

### Post by siteregsam on 2010-09-08
Thanks Peter...
I will read the documentation....

---

### Post by siteregsam on 2010-09-08
Thanks baboli....

---

