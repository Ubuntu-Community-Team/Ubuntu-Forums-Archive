---
title: "Can't connect to network in Windows Virtual PC"
date: 2013-08-24
forum: Virtualisation
---

### Post by AlexBooton on 2013-08-24
As it says in the subject.  The little network icon is empty and there is no connectivity.

In Windows Virtual PC settings I've selected "Shared networking (NAT)".  Also tried the other options for the adapter but nothing works.

ifconfig says the network is up but there is no activity other than "TX packets: nnn" where nnn is a low number that gradually increases.  All other TX and RX counts are zero.

What can I do to fix this?

This is on Win7 with U12.04 32 bit.

Thanks

---

### Post by tripp98 on 2013-08-24
it sounds like your running ubuntu in the virtual pc.  if so what IP is the ubuntu box getting?  open terminal type ifconfig
or you can right click the network icon next to the clock.  go to the 2nd from bottom and left click connection info.

it will tell you your default route (your router) as well.  if it looks correct.  try from terminal and type ping (the default route in connection info) -c 4

the -c 4 will only touch it 4 times

post back with results and someone can assist more.

---

### Post by AlexBooton on 2013-08-24
> **tripp98 said:**
> it sounds like your running ubuntu in the virtual pc.  if so what IP is the ubuntu box getting?  open terminal type ifconfig
or you can right click the network icon next to the clock.  go to the 2nd from bottom and left click connection info.

it will tell you your default route (your router) as well.  if it looks correct.  try from terminal and type ping (the default route in connection info) -c 4

the -c 4 will only touch it 4 times

post back with results and someone can assist more.

Thanks for the feedback.

Yes, I'm running ubuntu in the virtual pc.

It seems I don't have an IPv4 address!  Just an IPv6 one which is useless since I don't have any v6 connectivity.  I can see with ifconfig that there is just a v6 IP which oddly seems to be up; or at least that's what ifconfig says.

The 2nd from bottom option "Network information" on the network icon next to the clock is disabled.  But the bottom option "Edit connections" works and the 3rd from bottom "Enable networking" is checked.

In "Edit connections" the method on the v4 tab is "Shared with others".  I've tried some of the other options and given an IP, net mask, etc.  But nothing has enabled v4.

There are no routes on the Routes tab.

I seem to be stuck.  Is there a way to get this to work?

Thanks

---

### Post by tripp98 on 2013-08-25
On the virtual pc settings do you have a network card enabled?  Make sure you have it set to use external network.  I think thats the term that they use.

---

### Post by AlexBooton on 2013-08-25
> **tripp98 said:**
> On the virtual pc settings do you have a network card enabled?  Make sure you have it set to use external network.  I think thats the term that they use.

Hi and thanks for the feedback.

The setting I have is "Shared Networking (NAT)".  I believe that's the correct one but I've tried the others as well.  Nothing seems to work.

There is no option that resembles "use external network" or anything close.  There is "Internal network" but that is not what I want (I think). 

Thanks

---

### Post by AlexBooton on 2013-08-28
Hi,

Just to close the loop, I gave up on MS Virtual PC and went with Virtualbox.  I now have network connectivity.

---

### Post by dhunt84971 on 2013-08-28
That is funny.  I was going to suggest going to VMWare Player.  I use that under a Windows 7 host and it runs Ubuntu like a champ.  One thought, I have used Microsoft Virtual PC in the past and I seem to remember being able to pick the NIC that the guest would use.  Just a suggestion, but did you verify that the NIC being provided to the guest was the correct one?

---

