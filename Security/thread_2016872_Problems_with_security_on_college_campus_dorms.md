---
title: "Problems with security on college campus dorms"
date: 2012-07-04
forum: Security
---

### Post by Towlie on 2012-07-04
A little while ago a friend of mine had the Windows partition of his Windows/Ubuntu dual booting PC hacked by another student in the dorm we both lived in and had a variety of data stolen from it. He said he knew the IP address of the computer that hacked it was from the dorm but neither of us were able to find out where in the dorm it was located at. I too dual boot Windows and Ubuntu but at the time the hacker was active I had left Ubuntu running, and probably because it was just some script kiddie using only windows affecting scripts, my PC was untouched. Several other people in the dorm reported similar attacks and such.

My question is this: 
How can I collect evidence if such an attack were to happen again that would be sufficient to be able to either report the hacker to the university or if that were to fail, go to his room and hack his face using my fist? O:)

Note: Each person is given a couple of cat5 ports in their room designated to them only as well as a static ip the first time they utilize these ports. The university only scans for torrents and pornography, not security, so we are left to fend for ourselves. The hacker mentioned above was never caught.

---

### Post by spynappels on 2012-07-05
> **Towlie said:**
> 
Note: Each person is given a couple of cat5 ports in their room designated to them only as well as a static ip the first time they utilize these ports. The university only scans for torrents and pornography, not security, so we are left to fend for ourselves. The hacker mentioned above was never caught.

If your friend had the cracker's IP address, he should have taken that to the the Uni's IT people, they could have dealt with that.

In any case, the only real evidence you can gather is on your own machines, it could be breaching Uni rules for you to attempt any sort of "offensive" investigation or evidence gathering. I'm not sure how easy this is on Windows systems without the exhaustive logging built in to Linux.

As a general rule, harden your systems as much as you can, and keep a constant watch for unexplained activity.
The Security stickies at the top of the Security sub-forum are extremely helpful in this regard.

---

### Post by sudodus on 2012-07-05
Also have a look at this link [[COLOR="Red"]_https://wiki.ubuntu.com/BasicSecurity_[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")
which contains a lot of tips how to protect your computer.

---

### Post by samiux on 2012-07-06
> **Towlie said:**
> A little while ago a friend of mine had the Windows partition of his Windows/Ubuntu dual booting PC hacked by another student in the dorm we both lived in and had a variety of data stolen from it. He said he knew the IP address of the computer that hacked it was from the dorm but neither of us were able to find out where in the dorm it was located at. I too dual boot Windows and Ubuntu but at the time the hacker was active I had left Ubuntu running, and probably because it was just some script kiddie using only windows affecting scripts, my PC was untouched. Several other people in the dorm reported similar attacks and such.

My question is this: 
How can I collect evidence if such an attack were to happen again that would be sufficient to be able to either report the hacker to the university or if that were to fail, go to his room and hack his face using my fist? O:)

Note: Each person is given a couple of cat5 ports in their room designated to them only as well as a static ip the first time they utilize these ports. The university only scans for torrents and pornography, not security, so we are left to fend for ourselves. The hacker mentioned above was never caught.

You, your classmates and hacker are in the same subnet.  Hacker can easily to obtain valuable information by poisoning the gateway/router of the subnet.  You can refer to this [link]("http://ubuntuforums.org/showthread.php?t=2017608") for more details.

Basically, the IP address of the hacker may be faked.  However, you can check the logs to see if the hacker hide his IP or not.  Sometimes, the IP of the hacker will be 127.0.0.1 or other IP address that in other country or a string instead.  That means, the IP address of the hacker has been hidden.

The evidence of the attack can be found from the logs if the hacker did not delete it or change it.

The hacker can gain access to your computer (no matter which OS is) in various methods.  The hacker can get the highest privilege of your computer, such as root and administrator.  That means, the hacker can do what he want to do.

If the offensive method to locate the hacker in your campus dorms is not allowed, you may consider to install honey pot to capture the activities of the hacker so you can investigate his activities offline.  However, you need some knowledge of hacking for this matter beforehand; otherwise, you will not know what he is doing on the honey pot.

In addition, you may take some hacking courses, such as [C|EH]("http://www.eccouncil.org/courses/certified_ethical_hacker.aspx"), [CISSP]("https://www.isc2.org/cissp/default.aspx"), [OSCP]("http://www.offensive-security.com/information-security-certifications/oscp-offensive-security-certified-professional/") and else to enrich your knowledge on the topic of hacking.

Samiux

---

