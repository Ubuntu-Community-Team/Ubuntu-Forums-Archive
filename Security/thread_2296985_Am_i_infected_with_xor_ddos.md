---
title: "Am i infected with xor ddos"
date: 2015-09-30
forum: Security
---

### Post by nir4 on 2015-09-30
I read recently about xor ddos.
I want to know if i am infected with this Trojan, and what can be done.
Thank you in advance.
Nir

---

### Post by nknwn on 2015-09-30
Are you running an SSH server?

Find out with this command: sudo /etc/init.d/ssh status


"To install the malware must first obtain root access to an SSH server by trying a brute force attack.  So unless to have a server configured by allowing a direct root access password and a weak password, the risk is zero."

[https://translate.google.co.uk/translate?hl=en&sl=fr&u=https://forum.ubuntu-fr.org/viewtopic.php%3Fid%3D1783131&prev=search](https://translate.google.co.uk/translate?hl=en&sl=fr&u=https://forum.ubuntu-fr.org/viewtopic.php%3Fid%3D1783131&prev=search)

---

### Post by brian-mccumber on 2015-09-30
Here is a link to the Symantic entry for xorddos. It shows the folders and file names that would be on your computer if it was infected. 

[https://www.symantec.com/security_response/writeup.jsp?docid=2015-010823-3741-99&tabid=2](https://www.symantec.com/security_response/writeup.jsp?docid=2015-010823-3741-99&tabid=2)

As long as you are not running your computer as root all the time, and you have a decent password, and are not participating in risky internet searches, or torrenting pirated software and running sh scripts that you do not fully understand I don't think you have much to worry about. Also turning on UFW(Uncomplicated Fire Wall) would help prevent infections from this type of thing.

Just because you are running Linux doesn't mean that your computers are automatically infected by this. In order for Linux to catch a virus it is usually the user who inadvertently allows it to execute in the first place by going places and doing stuff that they don't understand or probably shouldn't be doing in the first place.

---

### Post by coldraven on 2015-09-30
> **nir4 said:**
> I read recently about xor ddos.
I want to know if i am infected with this Trojan, and what can be done.
Thank you in advance.
Nir
It only affects servers and not desktops. Learn to give more information in your posts, we cannot help you with vague questions.
[http://www.theregister.co.uk/2015/09/29/linux_xor_ddos_botnet/](http://www.theregister.co.uk/2015/09/29/linux_xor_ddos_botnet/)

---

### Post by deadflowr on 2015-10-01
To ease your pain please read:
[http://blog.dustinkirkland.com/2015/09/ubuntu-and-xorddos-nothing-to-see-here.html](http://blog.dustinkirkland.com/2015/09/ubuntu-and-xorddos-nothing-to-see-here.html)

---

