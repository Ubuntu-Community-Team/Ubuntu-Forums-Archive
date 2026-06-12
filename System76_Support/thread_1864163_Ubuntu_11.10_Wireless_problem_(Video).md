---
title: "Ubuntu 11.10 Wireless problem (Video)"
date: 2011-10-18
forum: System76 Support
---

### Post by mahermali on 2011-10-18
Hi
I've found a problem when upgrading to ubuntu 11.10 regarding the network manager

After upgrading the wireless connection didn't work I thought it was a problem relate to the wlagn driver, but then it turns out that it is a problem with root access privliges.

for instance: when running the sotware center from the Golden menu I can't install or remove any software, the same thing for Synaptic, I have to run it from terminal with sudo.

This is not issue we are working with linux.
but then I found the problem is also with network-manager which is annoying.

The network manager can't communicate with wpa_supplicant unless I do it manually with wpa_gui as you will see in this video.

any idea?

This is very useful when you know that the problem is not with wireless driver, and it is a strange problem, I don't know if it is a bug in ubuntu 11.10 where the unlock key found in other places is not found in the network manager and software center.

I hope someone will have a look at the video on this link

[http://www.youtube.com/watch?v=SVqfpNAe7GA](http://www.youtube.com/watch?v=SVqfpNAe7GA)

Regards

---

### Post by isantop on 2011-10-18
Did you upgrade using the CD or with upgrade manager? If you used the CD, then this is a problem, but if you used update manager, then I'm guessing this was a glitch from the upgrade.

---

### Post by mahermali on 2011-10-18
Hi [isantop]("http://ubuntuforums.org/member.php?u=394913")
I've updated usinng the update manager, the issue is apparently related to privilege access and the system doesn't ask for it.

---

### Post by mahermali on 2011-10-19
hi
I solved the problem by uninstalling the networkmanager and installing wicd

Everything is now good, I think it's problem with the network manager, it can't communicate with wpa_supplicant.

regards

---

### Post by prosist on 2011-10-21
> **mahermali said:**
> hi
I solved the problem by uninstalling the networkmanager and installing wicd

Everything is now good, I think it's problem with the network manager, it can't communicate with wpa_supplicant.

regards

thanks sooo much. really. you helped convert a new ubuntu user :p

---

### Post by mahermali on 2011-10-21
> thanks sooo much. really. you helped convert a new ubuntu user :razz:you're welcome just forget to mention that:

when booting I had a problem the system is looking for network configuration which takes 2 minutes or more during the boot process --> Solve it by removing the dhcp entries in the interfaces file

also there is step to add it during startup:
add in the startup applications  this entry: 

name: whatever you want
command: wicd-gtk

and it will automatically connect to the wireless network at boot time.

regards

---

### Post by prosist on 2011-10-21
> **mahermali said:**
> you're welcome just forget to mention that:

when booting I had a problem the system is looking for network configuration which takes 2 minutes or more during the boot process --> Solve it by removing the dhcp entries in the interfaces file

also there is step to add it during startup:
add in the startup applications  this entry: 

name: whatever you want
command: wicd-gtk

and it will automatically connect to the wireless network at boot time.

regards

sorry, the problem came back after reboot =(

---

### Post by mahermali on 2011-10-21
in the unity just type wicd and the wicd program will be displayed then you can configure you network with Automatically connect.

Try it it worked perfectly for me.

---

### Post by prosist on 2011-10-22
> **mahermali said:**
> in the unity just type wicd and the wicd program will be displayed then you can configure you network with Automatically connect.

Try it it worked perfectly for me.

things worked really strange here. I already had installed wicd, then uninstalled network manager. I opened the wicd and then I was connected! I was quite happy, posted here and then thought: let's reboot!

then no wireless! again =(
I could see my home network, but I kept getting an "invalid password" or something.

---

### Post by emddom on 2011-10-25
Thanks !
Worked for me, too.

My wireless connection was extremely slow (280 B/s) 
after upgrading to 11.10.

---

### Post by Sonsum on 2011-10-26
While it doesn't have any pretty Gnome Shell support, WICD is the way to go. It's the only thing that would fix my wireless issue. 

Uninstalling network-manager and installing wicd worked for me.

---

### Post by b3rylord on 2011-11-01
When upgrading from 10.10 to 11.04 via the upgrade path 11.04 threw away the network connection used to do the upgrade and I had hours of struggling to get it to work again to the point where I may not upgrade to 11.10 for fear that the same thing will happen. I connect via a Vodafone dongle and the files I had to load and mess with were bcm43xx files. Anyone know why a working system would throw away its access point to the internet in the first place whilst doing an upgrade??

---

### Post by lordbah on 2011-11-02
Seems like every post about solving a wireless problem says to remove network-manager and install wicd. Is there no way to get it to work? I'd kinda like to keep it around for my wired connection which is working fine.

My problem is that it won't connect to the router. Even when I store the correct password (in network-manager Edit Connections) it still asks for a password. That dialog accepts a max of 26 characters, and when I generate a random password on the router it is longer than that. When I specify a shorter password on the router and then try to enter it in this dialog, the Connect button is disabled. The button enables when exactly 5 or 13 characters have been entered, which makes no sense at all to me. A password of exactly that length doesn't work either.

---

### Post by isantop on 2011-11-03
Try running these command:

```
sudo apt-get clean
sudo apt-get install --reinstall network-manager
```

You may need to connect to a wired network for this to work.

---

### Post by lordbah on 2011-11-04
> **isantop said:**
> Try running these command:

```
sudo apt-get clean
sudo apt-get install --reinstall network-manager
```

You may need to connect to a wired network for this to work.

Worked like a charm.

---

### Post by Sonsum on 2011-11-06
> **lordbah said:**
> Seems like every post about solving a wireless problem says to remove network-manager and install wicd. Is there no way to get it to work? I'd kinda like to keep it around for my wired connection which is working fine.

I'm not sure what happened, but I ended up reinstalling Ubuntu because I borked Gnome because of a few overly-ambitious tweaks. After it was done installing, it appeared that network-manager had gotten a new update. I think a newer version fixed whatever bug there was.

---

### Post by armless on 2011-11-23
My solution is restart with the the wireless adapter unpluged(or desactivated if its integrated) then enter the network manager->wireless and edit the conection and check the last option:available for all users and save then restart and plug the adapter or activate if integrated.
this is the way I solved it. thanks to the comunity:)
sorry for my english

---

### Post by kcs11 on 2013-01-29
> **mahermali said:**
> 
I hope someone will have a look at the video on this link

[http://www.youtube.com/watch?v=SVqfpNAe7GA](http://www.youtube.com/watch?v=SVqfpNAe7GA)

Regards


@mahermali  ---> [[http://www.youtube.com/watch?v=SVqfpNAe7GA]](http://www.youtube.com/watch?v=SVqfpNAe7GA])

I  like to know how you pulled up the wpa_gui  when you typed in "sudo  wpa_gui" in the terminal. Did you download some kind of application to  get that gui??   Please explain.

---

### Post by nothingspecial on 2013-01-29
This thread is old.

Closed.

---

