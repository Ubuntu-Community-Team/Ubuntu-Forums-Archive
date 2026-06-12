---
title: "GNS3 Create Loopback and Bridge"
date: 2009-06-25
forum: Virtualisation
---

### Post by bluet0oth on 2009-06-25
I'm studing for my ccna, have been running gns on my xp box, but decided to use my ubuntu box so my wife can use the comp more,(she can't use ubuntu very well)

nehow... have GNS up and running, vpcs running, ios loaded everything going... how do I create a loopback and bridge it to my wireless card so i can telnet/ssh/sdm to gns??

---

### Post by Denz Choe on 2010-07-24
Hi Bluet0oth, I know this is a one year thread, I certainly hope you have found a solution on Ubuntu.
I'm trying to achieve the same thing;
Have you found a way to  "create a loopback and bridge it to your network card so you can  telnet/ssh/sdm to gns it?"

---

### Post by SivArt on 2011-01-29
Check the GNS3 guide:
[http://downloads.sourceforge.net/gns-3/GNS3-0.5-tutorial.pdf?download](http://downloads.sourceforge.net/gns-3/GNS3-0.5-tutorial.pdf?download)

The only difference is that you need to run GNS3 as root in order to bind the cloud to the network interface that you have selected, or you can create a loopback interface in ubuntu with a static IP in order to bind it with the GNS3 Cloud.

[http://www.gns3.net/phpBB/topic2226.html?sid=74f5095c49af738bf913a8d56c7fb71d](http://www.gns3.net/phpBB/topic2226.html?sid=74f5095c49af738bf913a8d56c7fb71d)

HTH
SivArt

---

