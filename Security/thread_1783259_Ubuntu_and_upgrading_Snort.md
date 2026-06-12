---
title: "Ubuntu and upgrading Snort"
date: 2011-06-15
forum: Security
---

### Post by Hopping_Ubu on 2011-06-15
I currently run Snort version 8.5.2.2 on Lucid Lynx (10.04) that was located in Ubuntu's repository. I would like to upgrade to the latest version so that I can get the latest rules for Snort. When installing Snort from Ubuntu's repositories, I am not familiar where it gets installed, so when I down load the current version 2.9.0.5, I really don't know where to install once I compile it. I used Bodhi Sazen's instructions using Postgresql and Base so there is the integration part that I know I have to be aware of while doing this. What would be the best method to upgrade? Uninstall Snort 8.5.2.2 and begin again with the latest version from Snort.org and compile/install in /etc/snort or uninstall everything and then compile and install? 

Thank you very much for any assistance that anyone can give.

---

### Post by AtesComp on 2011-06-24
This is kind of an odd place to find it, but look here:

[https://launchpad.net/~ebf0/+archive/gamelinux](https://launchpad.net/~ebf0/+archive/gamelinux)

I added the repo and all the required extras snort needs is there.

It says "lucid", but it worked for maverick, just keep/edit "lucid" in your repo list.

---

