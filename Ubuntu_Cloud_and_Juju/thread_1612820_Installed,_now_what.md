---
title: "Installed, now what?"
date: 2010-11-03
forum: Ubuntu Cloud and Juju
---

### Post by deunnero on 2010-11-03
Ok, so I have a few spare computers that I wanted to test...

SETUP :

Main router >
   Home computers
Second router >
   Cloud controller
   Cloud node x4

These computers really aren't that great, but I installed the ubuntu enterprise cloud on one and set it up as the main cluster
then for all the other computers I set them up as nodes.

So... I've been able to get into the store ([https://192.168.2.108:8443](https://192.168.2.108:8443))  I added M/DB Appliance
Ubuntu 10.04 LTS Lucid Lynx(i386)  they all installed properly


SSH'ing into the server with putty works like a charm...
I know how to use sudo apt-get and stuff...


But how do I add applications that will scale up/down? 
How do I create instances?

I've been looking on how to control the cloud.... but so far all I can find on it is "How good" it is....

Any help or point to some guides would be nice....

Thanks,
Jon.

---

### Post by kim0 on 2010-11-04
Hey there

Your probably want to follow starting step 6 on
[https://help.ubuntu.com/community/UEC/PackageInstallSeparate#STEP](https://help.ubuntu.com/community/UEC/PackageInstallSeparate#STEP) 6: Obtain Credentials

Using euca2ools to manage VMs. Once that works, you may want to use a GUI tool such as
[https://help.ubuntu.com/community/UEC/ElasticFox](https://help.ubuntu.com/community/UEC/ElasticFox)
or HybridFox

For applications that scale, it's not that easy :) The application needs to be written to scale, and it's always different per application what needs to be done

---

### Post by deunnero on 2010-11-05
Thanks,
Hybridfox now connects, Thanks for that! :)

I'm doing the publication thing now.... the only one that worked was 
eucalyptus-nc-publication   all the others are unkown jobs.


I thought that all the instances auto connected. Guess not... working on some of the others to see if it fixes my issues.   

[IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-snc4/hs971.snc4/76483_465035897940_555042940_5517940_1360347_n.jpg[/IMG]


Update:  I even went back and installed the publication stuff, it said that they were up to date.   Not sure what is going on....?

---

### Post by kim0 on 2010-11-06
If you're using 10.10 you do not need to do any publication thing manually! The page says "As of Ubuntu 10.04 LTS, all component registration should be automatic"

---

