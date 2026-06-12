---
title: "Back|Track and Ubuntu"
date: 2010-02-11
forum: Security
---

### Post by running_rabbit07 on 2010-02-11
I have tried Back|Track 4 and I am wondering what would be some cool tools to have on Ubuntu for penetration testing and doing things with wireless that are in the Ubuntu repository. I would prefer to run Ubuntu instead of BT's KDE.

Thanx,
Ronnie

---

### Post by CharlesA on 2010-02-11
I don't know how much of the stuff in BT4 are in the repos, but I doubt it's much.

You will probably have to go to each site and either install from source or see if there is a deb to install.

---

### Post by Joe Ker1086 on 2010-02-11
well for the most basic penetration of wirless you can get both aircrack-ng and macchanger from the repository.... not sure what else is there but that should at least get you started :D The nice thing is that most of the penetration tools that are useful are run from terminal so you wont have any conflicts with the KDE aspect

---

### Post by running_rabbit07 on 2010-02-11
Got aircrack and macchanger installed now. Between those wireshark and nmap, I think I have enough toys to play with to get me through my NIDS classes.

Thanks,
Ronnie

---

### Post by mkvnmtr on 2010-02-11
There are quite a few of the pen testing tools in the repositories. A few you can download from the sites themselves. A few seem to be windows tools that are running in wine and a few are free versions of paid software. Also there seem to be some that are skripts to use programs in a certian way. While BT4 is a great distro for what it is designed for it is not one I would want to run as a desktop. There are loads of fine tools you can add to your desktop Ubuntu to get the practice to use Back Track when it is needed.

---

### Post by Sarmacid on 2010-02-12
You can add the BT repos to Ubuntu and download the tools, this is however not supported by the BT team.

---

### Post by Jekshadow on 2010-02-13
> **Sarmacid said:**
> You can add the BT repos to Ubuntu and download the tools, this is however not supported by the BT team.

From [http://www.backtrack-linux.org/faq/:](http://www.backtrack-linux.org/faq/:)
> We recommend against this action because Backtrack tools are built with many custom features and libraries.

It would be easier to add the Ubuntu repos to a Backtrack install and install the ubuntu-desktop package.

---

### Post by 26venger on 2010-02-15
i thought it would be interesting to try nubuntu. i think its basicly the same as ubuntu but with pen testing tools

---

### Post by uRock on 2010-02-15
I have been playing with Zenmap which is a GUI front end for NMAP and I must say that I like it. I set it running on one of my other machines to scan my production system with and without UFW and I watched it all on Wireshark. Without the wireshark, I was seeing the ICMP replies to the UDP packets and thought it was wild, then when I turned on UFW and ran it again, all you could see were the incoming packets with no response. I am really impressed. Tomorrow I plan to run the same tests against Windows 7 and see how that turns out. I will post the outcome [here]("http://ubuntuforums.org/showthread.php?p=8833517#post8833517").

---

