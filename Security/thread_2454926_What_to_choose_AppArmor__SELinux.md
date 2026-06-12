---
title: "What to choose AppArmor / SELinux ?"
date: 2020-12-09
forum: Security
---

### Post by alekseypython on 2020-12-09
Kubuntu 20.10

I want the following: install a new system and roll up typical application restrictions for all applications. And then, as new programs are installed, I add new restriction profiles (it's desirable that there be some resource with these profiles, from where they can be downloaded and then edited for themselves).  

Those I absolutely DO NOT want to:      
1. After installing a new system, analyze which packages were installed, search / write rules for all of them and hope that I took everything and didn't miss anything.     
2. To write rules for all software, which I will additionally supply: there must be a database of these rules.  

Which of the two systems of security avoids the above two points?

---

### Post by linuxyogi on 2020-12-09
After the excellent tool called Firejail was released I never bothered with Apparmor or Selinux. Firejail has profiles for almost all popular apps. I use Firejail with Firefox, Google Chrome & Thunderbird.

---

### Post by EuclideanCoffee on 2020-12-09
SELinux works for what you want to do, but it's a challenge to maintain on Ubuntu. There have been significant improvements after a Debian specialty team completed a lot of work, but there's still more work to do. You're better off using RHEL or CentOS in this case. 

For AppArmor, you can accomplish all of this, but you will likely need to create a "general profile," which is essentially a wildcard. The problem here is that this profile may become active when you don't want to. And depending on restrictions, the restrictions may be too high and even cause your computer to crash. Regardless, it would require you to write your own app profiles.

Finally, I recommend you use virtualization or containers if this is just a personal computer. Why? Well, you can delete your containers and the data on them. Simply never give the container running access to your desktop. Snap was suppose to have a feature like this, but I don't think it quite works yet. Firejail may be your best choice for convenience. Or you may want to use VirtualBox, QEMU, etc.

---

### Post by alekseypython on 2020-12-09
[  ]("https://ubuntuforums.org/member.php?u=996859")Thanks [**[COLOR=#000000]linuxyogi[/COLOR]**]("https://ubuntuforums.org/member.php?u=996859") and [**[COLOR=#000000]EuclideanCoffee[/COLOR]**]("https://ubuntuforums.org/member.php?u=1943968")!

---

