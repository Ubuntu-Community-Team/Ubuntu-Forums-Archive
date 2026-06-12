---
title: "Fedora Graphics Test Week kicks off tomorrow (Tuesday)!"
date: 2013-04-22
forum: Ubuntu, Linux and OS Chat
---

### Post by AdamWill on 2013-04-22
I hope no-one minds me posting this here - I don't spam about all kinds of Fedora events, but Graphics Test Week is a bit of an exception. It's of interest beyond the Fedoraverse, because Fedora devs contribute a lot of work to upstream graphics development, and we don't do any non-upstreamed work on graphics in Fedora; so if you come along and contribute testing, you're contributing to overall F/OSS graphics development, not just to Fedora, and the benefits will come to your distribution as well as Fedora and all others :)

Tomorrow, Tuesday 2013-04-23, is [Intel graphics Test Day](https://fedoraproject.org/wiki/Test_Day:2013-04-23_Intel). Wednesday 2013-04-24 will be [Nouveau Test Day](https://fedoraproject.org/wiki/Test_Day:2013-04-24_Nouveau). And Thursday 2013-04-25 will be [Radeon Test Day](https://fedoraproject.org/wiki/Test_Day:2013-04-25_Radeon).

As always, we'll be looking to test out the widest possible range of hardware and see how well it works with the very up-to-date graphics stacks in Fedora 19. As Fedora uses very recent builds of the relevant components and sends all its work upstream, contributing to these Test Days can help out all other distributions, not just Fedora - so please, even if you're not a Fedora user, consider coming and contributing your testing! We provide comprehensive instructions and live images for testing, so you won't need to replace your current distribution or do a permanent installation of Fedora at all if you don't want to. You can easily [write a Fedora live image to a USB stick](https://fedoraproject.org/wiki/How_to_create_and_use_Live_USB), so you don't even have to waste a DVD.

We always want to get as much data as we can in these events, so please, if you have a few minutes, help us out and perform the tests for your system(s). If you can't make the correct date for your hardware, no problems - you can file results early or late and we'll still be able to use them. It's also fine to come to the IRC channel on the 'wrong day' and ask questions - we'll have folks in the channel all week who will answer your questions if they can. The testing is very easy, and if you don't have time to run through all the test cases, partial results are still very useful - if all you have time to do is boot the live image and check whether the desktop appears on your system, even that is useful.

As always, the full instructions and live images are on the Wiki pages: [Intel](https://fedoraproject.org/wiki/Test_Day:2013-04-23_Intel), [Nouveau](https://fedoraproject.org/wiki/Test_Day:2013-04-24_Nouveau), [Radeon](https://fedoraproject.org/wiki/Test_Day:2013-04-25_Radeon). Fedora QA team members and graphics developers will be hanging out in the #fedora-test-day channel on Freenode IRC to help out with testing and debugging any problems you come across, so please come join us there if you're taking part! If you're not sure what IRC is or how to use it, we have [instructions here](http://fedoraproject.org/wiki/How_to_use_IRC), and you can also simply [click here](http://webchat.freenode.net/?channels=fedora-test-day) to join the channel through a Web front end - all you need to know is that IRC is a chat system.

---

### Post by grahammechanical on 2013-04-23
I do not mind at all. In fact I might try Nouveau tomorrow. There are just a couple of little problems. I have just tried the test for Nvidia hardware. I ran the command and I get > bash: /sbin/lspci: No such file or directoryNo nVidia graphics hardware found.


I guess that lspci is not in the /sbin directory on Ubuntu. Yet it is on the system because lspci yields

> 01:00.0 VGA compatible controller: NVIDIA Corporation GT216 [GeForce GT 220] (rev a2)



The other little problem is that I am running Unity. And you do not allow for that. But, hey, what are these small differences among members of the same open source community. 

Don't forget to give credit to Ubuntu users. Don't claim it all for yourselves. Regards.

---

### Post by AdamWill on 2013-04-23
> **grahammechanical said:**
> I do not mind at all. In fact I might try Nouveau tomorrow. There are just a couple of little problems. I have just tried the test for Nvidia hardware. I ran the command and I get 

I guess that lspci is not in the /sbin directory on Ubuntu. Yet it is on the system because lspci yields




The other little problem is that I am running Unity. And you do not allow for that. But, hey, what are these small differences among members of the same open source community. 

Don't forget to give credit to Ubuntu users. Don't claim it all for yourselves. Regards.

Hi, Graham. Yes, that test command is pretty 'dumb', we've just been copy/pasting it from event to event forever. If I get five minutes I'll see if I can come up with a slightly more robust version. I don't really know what you mean about Unity - the point of the test event is to test the functionality of the driver stack itself, the desktop you run on top doesn't matter so much. We use GNOME for the tests just because it's the Fedora default, plus the fact that it requires 3D acceleration will tend to expose more bugs, which is handy. We do need you to use Fedora 19, either installed or from the live images, to run the tests - just because that's what the developers involved are familiar with, they know exactly what driver code is present there.

---

