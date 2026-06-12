---
title: "Issues With VirtualBox And &quot;Internal Networking&quot;"
date: 2009-03-18
forum: Virtualisation
---

### Post by HotDogBunToo on 2009-03-18
Well I have a guest instance of XP running on it and almost everything is working as I want it to - except for ONE major quirk being the networking to work - specifically the "Internal Network" option which I need so I can connect to stuff in the VM from the outside world which would mean getting a 192.168.1.X IP address.  Pretty much how VMWare has this option painlessly easy.  Yet I'm getting NO connection whatsoever.  Even when I specify the network name as "intnet" as the instructions say I'm still coming up with the dead end 169.XXX.XXX.XXX address upon loading up my virtual XP system - also tried entering in IP address manually and I'm still getting no luck :(

Of course NAT and "Host Interface" works with no problems but again they are not options for me since I'll need to access my virtual XP from the outside world (e.g. music streaming to phone, remote access to do windows stuff, web services, etc) but so far I'm clueless as to how to resolve this.  Why couldn't this be as easy as VMWare?  Any help would be appreciated :(

---

### Post by bodhi.zazen on 2009-03-18
Please start with the sticky :

[http://ubuntuforums.org/showpost.php?p=6122142&postcount=3](http://ubuntuforums.org/showpost.php?p=6122142&postcount=3)

Then if you are still having problems tell us what you have tried in terms of bridged networking and what version of VirtualBox you are using.

---

### Post by Jose Catre-Vandis on 2009-03-18
If you are behind a router, wouldn't you need to port forward that virtual PC (or such like) so that it can be seen by the outside world? What IP address would you use to connect from the outside world, given the "open" IP address would most likely be assigned to your router and then on to your real PC, or such like? This doesn't sound like a VBox problem but a ports / router issue?

---

### Post by HotDogBunToo on 2009-03-18
> **Jose Catre-Vandis said:**
> If you are behind a router, wouldn't you need to port forward that virtual PC (or such like) so that it can be seen by the outside world? What IP address would you use to connect from the outside world, given the "open" IP address would most likely be assigned to your router and then on to your real PC, or such like? This doesn't sound like a VBox problem but a ports / router issue?

Yup, that's what I regularly do.  For instance if I'm running a service in Virtual XP that uses port 79 and virtual is recognized on the network as 192.168.1.109 it makes life easy to throw that in the router and access it from the outside world using my ip address (e.g. 66.179.99.XXX is my outside address, I can just use 66.179.99.XXX:79 to gain access).

The problem however is getting the VBox XP a 192.168.1.XXX address that is visible on my network.  In VMWare this is pretty much lazyman's work since upon setting a VM and setting it to use bridged networking it's pretty much child's play to get a 192 address.  With this? Not so much a cakewalk lol.  Thus I might have to address this via bodhi.zazen's suggestions



> **bodhi.zazen said:**
> Please start with the sticky :

[http://ubuntuforums.org/showpost.php?p=6122142&postcount=3](http://ubuntuforums.org/showpost.php?p=6122142&postcount=3)

Then if you are still having problems tell us what you have tried in terms of bridged networking and what version of VirtualBox you are using.

Thanks, but when I tried using VBoxAddIF it's an unknown command that also isn't installable by itself.  Unless there's stuff in the rest of that post of yours that I have to add into the setup of things beforehand?  I dunno I'll continue to perhaps tinker with that and see how things'll go

---

### Post by bodhi.zazen on 2009-03-18
You have not told us what version of virutal box you are using.

Since the command was not found I assume it is a more recent version.

shut down the guest.

in the network tab, from the pulldown menu, select eth0 (bridged networking)

re-start the guest

---

### Post by HotDogBunToo on 2009-03-19
> **bodhi.zazen said:**
> You have not told us what version of virutal box you are using.

Since the command was not found I assume it is a more recent version.

shut down the guest.

in the network tab, from the pulldown menu, select eth0 (bridged networking)

re-start the guest

lol thanks for your help - I resolved it thanks to your help :popcorn:

You're right, I'm on the latest version thus far (2.1.4) and realized I had inserted IP address settings in VBox XP manually so it wasn't showing on the network at all.  Following your direction (under "Host Interface" which is the only one of the networking choices that'll allow me to select eth0) I'm FINALLY able to have the virtual machine show up in my router's clients table.  So router showing virtual instance of XP in network shows that this is resolved, and made extra sure by streaming my music to my phone so all is gravytrain 

My only question is what's the difference in having the VM show up in my local network via "Host Interface" + eth0 and "Internal Network" options? With the way things was worded in the help file I thought "Internal Network" was the only way to go & "Host Interface" would only have VM getting internet connection via 172 address & not getting any visibility on network.  

Ah well - I'll readup on this if I'm bored later, I'm happy all is well now with this - time to start jamming next time I'm out! ^_^

---

### Post by Jose Catre-Vandis on 2009-03-20
The internal network option allows multiple VMs to be able to see each other in a closed environment, like their own little separate LAN. This is offered as an option for two reasons:


1. Security. In host interface networking mode, all traffic goes through an interface of the host system. It is therefore possible to attach a packet sniffer (such as Ethereal) to the host interface and log all traffic that goes over a given interface. If, for any reason, you prefer two or more VMs on the same machine to communicate privately, hiding their data from both the host system and the user, Host Interface Networking therefore is not an option.

2. Speed. Internal networking is more efficient than host interface networking, as VirtualBox can directly transmit the data without having to send it through the host operating system's networking stack.

---

