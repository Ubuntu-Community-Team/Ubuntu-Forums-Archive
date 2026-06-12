---
title: "Network System Update"
date: 2017-10-21
forum: Server Platforms
---

### Post by slkamath on 2017-10-21
Hi,

We have nearly 50 Ubuntu Desktop's & Laptop's with 12.04, 14.04, 16.04 systems.

I just wanted to know how to update all the systems from single system (like windows server can download the important updates and it can push updates to client system)? 

Else I have to go to each system and make the system up-to-date.

Please let me know any solution is there for this.

Thanks in advance.

Lokesh Kamath

---

### Post by darkod on 2017-10-21
You can create a local centralized repository where you will download the updates, and then you can set up something like periodic automated update on all systems that will use that repository as source. Although using full automation like that can sometimes cause problems if some update breaks something and you apply it to big number of systems.

And don't forget that 12.04 is out of support now...

---

### Post by slkamath on 2017-10-21
> **darkod said:**
> You can create a local centralized repository where you will download the updates, and then you can set up something like periodic automated update on all systems that will use that repository as source. Although using full automation like that can sometimes cause problems if some update breaks something and you apply it to big number of systems.

And don't forget that 12.04 is out of support now...

Thank you.
Any other alternatives for updation? Coz we are not provided any internet in many systems. Can you suggest any best solution for this?

Lokesh Kamath

---

### Post by LHammonds on 2017-10-23
No Internet connection?  ouch.  I immediately understand your pain.

I have not designed a scenario like this so I have no practical knowledge.  The use of image technology may be an option depending on how independent these machines are...such as many different locations, few PCs at each verses few locations with many PCs at each.

With imaging, the basic idea is to make sure workstation "data" is stored on a server so that all the workstations can be treated like easy-to-replace dumb terminals.

When you need an update, deploy a new workstation image via CD-ROM, USB or whatever.

Problems can arise with diverse hardware (Dell vs IBM vs HP, etc.) when working with images.  Other issues can be related to software differences like going from OpenOffice to LibreOffice or just a much newer version which might require re-education for end-users.

Keep in mind that a "server" does not have to be some big, expensive machine.  I could be a Raspberry Pi with an external USB hard drive depending on usage requirements.

But no matter the solution, you must 1st consider your options on backup and restore.  As darkod mentioned, even doing an in-place upgrade might not work so well depending on the applications installed.  The "apt-get upgrade" tends to work with very few issues when it is just having to deal with the OS by itself.  But that is rarely the case, especially with desktops.  You need to make sure you can restore the system in the event of a disastrous upgrade.  The more diverse the workstations are, the less you can predict how well the upgrades will work.

Good luck with your upgrade and I hope you can get everyone on the same version of the platform.  It certainly was much easier for me to maintain my servers once I got all of them upgraded from 12.04 and 14.04 to 16.04.

LHammonds

---

### Post by slkamath on 2017-10-23
> **LHammonds said:**
> No Internet connection?  ouch.  I immediately understand your pain.

I have not designed a scenario like this so I have no practical knowledge.  The use of image technology may be an option depending on how independent these machines are...such as many different locations, few PCs at each verses few locations with many PCs at each.

With imaging, the basic idea is to make sure workstation "data" is stored on a server so that all the workstations can be treated like easy-to-replace dumb terminals.

When you need an update, deploy a new workstation image via CD-ROM, USB or whatever.

Problems can arise with diverse hardware (Dell vs IBM vs HP, etc.) when working with images.  Other issues can be related to software differences like going from OpenOffice to LibreOffice or just a much newer version which might require re-education for end-users.

Keep in mind that a "server" does not have to be some big, expensive machine.  I could be a Raspberry Pi with an external USB hard drive depending on usage requirements.

But no matter the solution, you must 1st consider your options on backup and restore.  As darkod mentioned, even doing an in-place upgrade might not work so well depending on the applications installed.  The "apt-get upgrade" tends to work with very few issues when it is just having to deal with the OS by itself.  But that is rarely the case, especially with desktops.  You need to make sure you can restore the system in the event of a disastrous upgrade.  The more diverse the workstations are, the less you can predict how well the upgrades will work.

Good luck with your upgrade and I hope you can get everyone on the same version of the platform.  It certainly was much easier for me to maintain my servers once I got all of them upgraded from 12.04 and 14.04 to 16.04.

LHammonds

Thank you.

In this case we cant replace any system like that coz all the user data is kept in the desktop system and backup is happening on daily basis.

Few systems are very old and in the present situation we cant replace that system so we installed 12.04 like that which is having good configuration we kept latest version. Majorly our concern is they are in different locations and many system dont have internet connections.

Lokesh Kamath

---

### Post by LHammonds on 2017-10-24
> **slkamath said:**
> Majorly our concern is they are in different locations and many system dont have internet connections.
I assume this also means you have no connectivity between the sites?

If that is the case, setting up a centralized update server would serve no purpose since the remote sites cannot access it...same problem you have now with Ubuntu's update repository.

However, if you can make a portable machine (laptop) a repository and just bring that machine to each site, you might be able to do your upgrades that way.  For example, you could add a DNS entry like "updateserver.mydomain.com" that points to your laptop server at each site (depending on your network, you may need to use a different IP for each site).  Then add that domain as a repository on each of your workstations (which is just a DNS entry to your local laptop while it is there at that location) and then do an "add-apt-repository" "apt-get update" "apt-get upgrade" and "apt-get dist-upgrade"

Sounds like you would need the 12.04, 14.04 and 16.04 repositories mirrored to that portable machine.

Disclaimer: I have no hands-on experience creating a local repository.

LHammonds

---

### Post by slkamath on 2017-10-24
> **LHammonds said:**
> I assume this also means you have no connectivity between the sites?

If that is the case, setting up a centralized update server would serve no purpose since the remote sites cannot access it...same problem you have now with Ubuntu's update repository.

Sounds like you would need the 12.04, 14.04 and 16.04 repositories mirrored to that portable machine.

Disclaimer: I have no hands-on experience creating a local repository.

LHammonds

Thank you.

We do have connectivity with P2P link. But we have not provided internet in major system, so currently we are doing apt-get update && apt-get upgrade in all the system ( changing the ip address while upgrading). This is very lengthy process, so I am checking with centralised network upgrade process.

Lokesh Kamath

---

