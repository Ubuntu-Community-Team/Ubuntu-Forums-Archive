---
title: "Unknown issue some insight please"
date: 2010-09-12
forum: Security
---

### Post by Codecaine_21 on 2010-09-12
so i have 2 computers and they both got trashed by viruses and the whole package! but i reformatted one with Ubuntu and left the other one. While formatting the other i selected no automatic updates and install no server this time! so immediately after installation i got an update package screen that popped up. it was for perl client/server, some python stuff, open ssh server, and some other goodies. i dont think that should have popped upn because i opted to update my system myself, am i not right? and i think my system is being fed malware thru updates!! One reason to lead me to believe would be that the computer i did not format would has an updat package that popped up and it said it was a denial of service. Also the package updater appaers ever 30 minutes. So is this possible that it is happening on my freshly reformatted  comp also? If so how?

Any insight would be very appreciated!!
Thanks in advanced!!

---

### Post by bodhi.zazen on 2010-09-12
This is not windows and there are no known active viruses for Linux.

I suggest you read the security sticky.

Otherwise I have no idea what you did with your system or if it is even Ubuntu as openssh-server is NOT installed by default. I have no idea how you have managed updates either =)

---

### Post by Codecaine_21 on 2010-09-12
I know this is not windows, it is Ubuntu lol!! And who said it had to be a virus? But I i opted to manually update my system and i am still getting automatic updates for open ssh, Perl client/server sockets and a bunch of other ****. But yes you are right, open ssh does not come installed by defualt! And i did not install it, so it is not installed. But if you would have read my post more carefully, than you would have seen that it was requesting to be installed via auoto updates. Which i chose to not have and opted out for security purposes!. This is the problem i can not figure out!! It is ubuntu, i manually manage my updates! And i know what i am doing! Just because i am new to this forum dont assume i am a newbie lol 


   So to make this problem clear for everyone!!!!!! My issue is on the fresh instal i did, i chose to install no server!! i chose to manually manage security updates. But after building the desktop and re-booting, an automatic update popped up and wanted to install open ssh server, perl client/server sockets and libraries and some other goodies. i figured it was something i downloaded that could have been binded or had a trojan horse. and even after i re format it still comes back??? idk any help would be very much appreciated!!!  

            Thanks in advanced!

---

### Post by OpSecShellshock on 2010-09-12
A lot of that stuff is part of a default installation, so since you did a fresh install it's probably there. Nothing to worry about, though--it's not in use, it's just there. It's only the software that's not part of the default installation that you'd have to install yourself. That should answer the question of the updates as well, since what update manager was showing you is that there were updates available for those packages, which means the packages are already installed (but again, not necessarily in use).

Update manager won't install the available updates until you tell it to by hitting the Install button (if you've configured it to not auto-install). There are different classes of updates, however, and the ones classified as security updates will still cause update manager to open automatically when it finds them.

---

### Post by BkkBonanza on 2010-09-13
Select menu System, Administration and Update Manager.
Choose "Settings" button bottom left.
Now look at the settings.
You have choices about "checking for udpates", and other choices about what to do, "Install/Download/Notify". 
You probably have "check for updates", and set for "notify". Nothing wrong with that but if you don't want it to pop up and tell you then turn "Check for updates" off.

I usually leave "important security updates" on because I feel it's more important to get fixes then to worry that the Ubuntu update system has been compromised. It does use Signing Keys on all packages/repos. So the chances of you getting hacked updates is very small.

---

