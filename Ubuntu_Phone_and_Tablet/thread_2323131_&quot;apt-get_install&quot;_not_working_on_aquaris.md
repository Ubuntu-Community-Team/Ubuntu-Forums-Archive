---
title: "&quot;apt-get install&quot; not working on aquaris M10"
date: 2016-05-03
forum: Ubuntu Phone and Tablet
---

### Post by tegner on 2016-05-03
When running e.g.,

apt-get install screen

system complains with

Error:Unable to write to /var/cache/apt

What is the recommended way to resolve this on the M10?
Thanks,
/jon

---

### Post by Johan_Helsingius on 2016-05-03
The file systems are mounted read-only. You can remount them writable, but it has been said that that disables the normal update mechanism.

---

### Post by tegner on 2016-05-04
That's bad. Main reason for buying it was to be able to install arbitrary desktop applications. But maybe this will change with time...

---

### Post by tegner on 2016-05-04
One idea would be to just go ahead and try to remount writable and start using apt-get to. However, would feel better about this path if it is reasonably easy to re install the original system in order to get the tablet back in its original state?

---

### Post by Johan_Helsingius on 2016-05-04
I assume that is what "Erase & Reset Everything..." does.

---

### Post by tegner on 2016-05-04
Hm, feeling stupid, that is simple! Thanks!

---

### Post by grahammechanical on 2016-05-04
> Main reason for buying it was to be able to install arbitrary desktop applications. But maybe this will change with time...

It is my understanding that the M10 Ubuntu edition came with a click package called Puritine installed. That should also have some standard desktop applications such as Libreoffice bundled with it. Is this not true? I do not think that Puritine can be used to install other deb packaged applications but Libertine can.

Puritine is actually a Libertine container in which the pre-selected deb packaged apps run. As I understand things, Libertine itself, if installed, will let us install and run any deb based application. This might help

[https://wiki.ubuntu.com/Touch/Libertine](https://wiki.ubuntu.com/Touch/Libertine)

Note this comment before you do any thing.

> [COLOR=#ff0000]Ubuntu Touch images with the Puritine click installed need some extra  work to get Libertine working.  If you want to experiment with that,  contact a Libertine developer on the[/COLOR] [#ubuntu-unity IRC channel]("http://webchat.freenode.net/?channels=#ubuntu-unity") [COLOR=#ff0000]on Freenode.[/COLOR]

Traditional applications that run on the X Server can be used to do damage to the OS because the X server allows applications all kinds of access to the system. This is not possible with Ubuntu phones and tablets because (1) they do not use the X server but Mir as a compositor and (2) click packages are tightly confirmed in regards to what they can do.

Installing traditional X server apps (deb packaged) the way you are thinking of doing is not a good idea because they are not designed to run on the Mir compositor. With Libertine the X server (deb) app runs inside a Linux Container and it runs on X-Mir. So, it is both able to run as if it was running on X server and prevented from accessing the OS in ways that can be used maliciously.

Regards.

---

### Post by Johan_Helsingius on 2016-05-05
So if I understand you correctly, the way to go is to install Libertine?

---

### Post by tegner on 2016-05-05
grahammechanical: Thanks for info!
But regarding libertine "You can use the Libertine app to create a container, but unfortunately it only supported the creation of LXC-based containers, which are not supported by the version of the kernel on most Ubuntu Touch devices." Might be a show stopper in this case?

Also, [COLOR=#000000]"Erase & Reset Everything..." does not seem to remove packages installed through apt-get, I tried installing some packages, and then did a "Erase and Reset everything". Packages were still there when unit was up again.[/COLOR]

---

### Post by krusty8 on 2016-05-16
> **tegner said:**
> 
But regarding libertine "You can use the Libertine app to create a container, but unfortunately it only supported the creation of LXC-based containers, which are not supported by the version of the kernel on most Ubuntu Touch devices." Might be a show stopper in this case?

Here's some further hints from a Canonical employee: [https://lists.launchpad.net/ubuntu-phone/msg19958.html](https://lists.launchpad.net/ubuntu-phone/msg19958.html)
and here's a report of someone succeeding: [http://wayneward.co.uk/ubuntu-touch/ubuntu-m10-arrived/](http://wayneward.co.uk/ubuntu-touch/ubuntu-m10-arrived/)

---

### Post by grahammechanical on 2016-05-16
The version of Ubuntu for Devices in Ubuntu phones & tablets is actually built on Ubuntu 15.04 code. And I think that is why LXC is not compatible. At some point in the future Ubuntu for Devices will have to be built on 16.04 code. And I suspect that it will be a radically different OS. I think it will be built on Snappy Ubuntu Core with snap apps instead of click apps and then Libertine will come into its own.

Hopefully, by then, some of the traditional desktop apps will have been re-packaged as snappy packages and so will be available through the app store. Ubuntu 16.04 desktop has a package called snapd that lets snap packages run on 16.04 desktop under Unity 7. At present there are very few snap packages available but those that are can be found by searching Ubuntu Software for "x11 apps." Ubuntu software will remove the space between x11 & apps. So, put it back and you will see 8 snap packaged apps. Three of which are familiar to Ubuntu phone users. The Clock, the Calculator and Notes.

It indicates the direction being taken for both phones, tablets and desktop Ubuntu. 

Regards.

---

### Post by tegner on 2016-05-18
Thanks! Under the circumstances (I like the unit and don't have that much spare time), it seems wise to sit back and wait for upgrades ;-)

---

