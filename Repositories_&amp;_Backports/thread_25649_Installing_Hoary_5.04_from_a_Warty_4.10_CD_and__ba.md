---
title: "Installing Hoary 5.04 from a Warty 4.10 CD and  backed-up repositories?"
date: 2005-04-10
forum: Repositories &amp; Backports
---

### Post by HJB on 2005-04-10
Hi, I have the Ubuntu Warty 4.10 CD and installed it on my Laptop. Then I updated and upgared everything to Hoary 5.04.
Lots of stuff was downloaded, but everything works great.

[COLOR=DarkOrange]I now LOVE UBUNTU and want  to install it my Desktop and throw WinDow$ out[/COLOR].

I don't want to go through the whole process of downloading stuff but would like to [COLOR=DarkOrange]backup the repositories[/COLOR].

The [Guide ](http://ubuntuguide.org/#backuprestoredownloadedrepositoriescache)mentions this BUT will it work if I first put in the  Warty 4.10 CD, install and then update/upgrade (using my backed-up repositories, to get to Hoary 5.04 (with OpenOffice's final release remember).

What (if any changes) should the above mentioned script have to fully do this?
Do I need to backup anything else?

Is this possible?

Please help and explain (very slowly with lots of scetches) how I should go about to do this.

Bye
HJB :-)

---

### Post by c_dog on 2005-04-10
You could use apt-build and Synaptic to build a personal repository of your /var/cache/apt folder (the place apt-get and Synaptic put the updated packages). Another way to get everything from the main and restricted repositories from the final release is to get the DVD image of the final Hoary and use it as a repository instead of Warty. Now that you've upgraded to Hoary it's probably not a good idea not to let anything get downgraded by Warty. Dump the Warty CD and get a Hoary CD or DVD. Just is case

---

