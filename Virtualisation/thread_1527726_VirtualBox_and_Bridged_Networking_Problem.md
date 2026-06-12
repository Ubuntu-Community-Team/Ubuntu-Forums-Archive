---
title: "VirtualBox and Bridged Networking Problem"
date: 2010-07-09
forum: Virtualisation
---

### Post by JustinR on 2010-07-09
Hey everybody!

I'm using the latest VirtualBox 3.2.6 on Ubuntu 10.04 32bit. I'm not sure when this happend, maybe within the last few days, that the bridged networking feature has stopped working. I run a Drupal webserver that requires bridged networking so this is a big problem for me.

So anyways, whenever I select bridged networking it does list eth0 and eth1, like always, (eth1 is the one I use). So when I select eth1 it selects successfully but below the dropdown box it usually lists the hardware interface that its actually (if I remember correctly) connecting to (Dell Wireless 1345 blah blah blah). But now this doesn't show up. Neither does it for eth0. So now whenever the VM web server tries to connect it times out. So now I need to know why its not working. So I searched for bridged networking and VirtualBox on google but all of the solutions were from 2008 which were too outdated. But they lead me to look at the files "/etc/network/interfaces" and "/etc/vbox/interfaces".

The /etc/network/interfaces file does not list eth1 but it lists loopback and eth0 fine.

The /etc/vbox/interfaces file is non existant, so does VirtualBox still use this? Actually the whole directory was empty.

Then I was lead to a command leaving me to think it could be an Ubuntu problem, the command was "sudo /etc/init.d/networking restart". When I run this I get this error, > [sudo] password for justin: 
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth1=eth1.
                                                                         [ OK ]


But I can connect to Eth1 (wireless) just fine. When I click connection information from the network app in Ubuntu it lists my current wifi connection as eth1.

I'm so confused with all of this! Is this an Ubuntu or VirtualBox problem?

I tried reinstalling virtualbox with no help and also reconfiguring the kernel module but that didn't work.

So does anybody have any troubleshooting tips or solutions that could help me?

Thank you.

---

### Post by JustinR on 2010-07-11
Bump... Has anybody ever experienced this problem before?

---

### Post by lackskill on 2010-07-27
I'm having a very very similar problem.  Wondering if you've had any luck.  My searching led me to the same places you did.  I followed the directions and got nowhere.  I'm not positive that it was working correctly directly prior, but I did install updates this morning, including a kernel update.  Any help is greatly appreciated.  I'm leaving first thing tomorrow morning for a road trip and would like to get this resolved before I leave if possible.

Will post back with updates if I find a solution.

---

### Post by JustinR on 2010-07-28
Hi, sorry this is a little late - I never got an email response that someone replied to this thread.

Anyways, no I have not found a solution so I've bee using NAT to connect to the internet. But my Drupal Web Server seems to be working with bridged fine for some odd reason - I have no idea why none of my other VM's work with bridged - but the only reason I need bridged is for this web server and it seems to be working fine now.

But for now the problem remains unsolved.

---

### Post by JustinR on 2010-07-30
I finally figured it out, sort of.

The Virtual Box module 'vboxnetflt' wasn't loading correctly.

So I tried a combination of 'sudo /etc/init.d/vboxdrv setup' and 'sudo modprobe vboxnetflt' and it started working.

---

