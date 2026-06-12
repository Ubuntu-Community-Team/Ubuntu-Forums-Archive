---
title: "Upgrade from server 12.04 to 12.10"
date: 2013-02-12
forum: Server Platforms
---

### Post by bryan.sailer on 2013-02-12
I have been looking at other forums and I tried the basic commands:

bryan@Sailerhomeserver:~$ sudo do-release-upgrade
[sudo] password for bryan: 
Checking for a new Ubuntu release
No new release found

So I edited the /etc/update-manager/release-upgrade file 

Prompt= normal

I am still not able to upgrade to 12.10. What should I try next?

---

### Post by lovevn on 2013-02-12
> **bryan.sailer said:**
> I have been looking at other forums and I tried the basic commands:

bryan@Sailerhomeserver:~$ sudo do-release-upgrade
[sudo] password for bryan: 
Checking for a new Ubuntu release
No new release found

So I edited the /etc/update-manager/release-upgrade file 

Prompt= normal

I am still not able to upgrade to 12.10. What should I try next?
Why do you use Update Manager? It's easier to use.:)

---

### Post by bryan.sailer on 2013-02-12
There is no update manager on the server, I have no gui interface. I use Webmin to manage my server and that is showing up as no update available.

---

### Post by SeijiSensei on 2013-02-12
Unless there is some specific package or version of a package that is only available in 12.10, I don't see any reason to upgrade a server from a [version]("https://wiki.ubuntu.com/Releases") with long-term support, 12.04, to one for which support ends next year.

Why do you want to upgrade?

---

### Post by bubylou on 2013-02-12
edit your /etc/apt/sources.list file and change precise to quantal. Then run these commands.
sudo apt-get update
sudo apt-get dist-upgrade

Is there any particular reason for your upgrade? Not a big difference between 12.04 and 12.10, especially on a server. Its also a good idea to stick with a more stable LTS release.

---

### Post by bryan.sailer on 2013-02-12
No I was just trying to stay current. If you are saying with 12.04, which I have had no problems, is fine the I will hold off on the upgrade. Thank you for the assistance.

---

### Post by koenn on 2013-02-12
> **bubylou said:**
> edit your /etc/apt/sources.list file and change precise to quantal. Then run these commands.
sudo apt-get update
sudo apt-get dist-upgrade


This is a recipe for disaster if the upgrade involves more than simple replacing one package's version to another, especially if the new release implements major design changes of software selections -  which is not all that unusual in ubuntu releases.

---

### Post by thnewguy on 2013-02-12
I would recommend one of two actions:
1. Backup everything and perform a fresh install to avoid conflicts. Then restore your data and configuration files once the new version has been installed.

2. As someone else pointed out, unless there is a strong reason to upgrade to 12.10 it is better to stick with 12.04. The 12.04 release will be supported a lot longer and has had the benefit of more time and testing. I would recommend staying with 12.04 and then upgrading to the next LTS release (14.04) or (16.04) when the time comes.

---

### Post by koenn on 2013-02-12
> **bryan.sailer said:**
> 
Prompt= normal


you have a space in that line, it shouldn't be there

not saying this will fix the issue, but better rule it out anyway

---

### Post by lovevn on 2013-02-13
> **thnewguy said:**
> I would recommend one of two actions:
1. Backup everything and perform a fresh install to avoid conflicts. Then restore your data and configuration files once the new version has been installed.

2. As someone else pointed out, unless there is a strong reason to upgrade to 12.10 it is better to stick with 12.04. The 12.04 release will be supported a lot longer and has had the benefit of more time and testing. I would recommend staying with 12.04 and then upgrading to the next LTS release (14.04) or (16.04) when the time comes.
Hi Thnewguy, I haven't ever upgraded ubuntu, so how long did it take you to upgrade ubuntu? I'm using Ubuntu 12.04, and I don't want to upgrade to 12.10, but when 14.04 will have been released, certainly I will upgrade my Ubuntu. But I must upgrade to 12.10, 13.04, 13.10. Is it really trouble? I don't want to install it again, either. :(

---

