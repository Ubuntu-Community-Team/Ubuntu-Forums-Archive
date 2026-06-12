---
title: "Aircrack-ng and Dictionary Attack Not working"
date: 2015-12-30
forum: Ubuntu, Linux and OS Chat
---

### Post by kevinliu18 on 2015-12-30
Urgent: HI everyone, I am doing a class project for which I am  attempting a deauthetication attack  on my home network (WPA2) using the  Aircrack-ng suite. I captured the  4-way handshake with airodump-ng and  have it stored as a .cap file but when I run a dictionary attack on it  with aircrack-ng I ALWAYS get the message "passphrase not in  dictionary". Even when the passphrase is part of the dictionary txt  file, the "passphrase not in dictionary" message  comes up. Any ideas why?

*Note 1: I am running ubuntu on virtual box with windows 10 as host.
*Note 2: Aircrack-ng shows that the handshake was successfully captured, and  when I run sudo aircrack-ng -w password.lst -b 00:14:6C:7E:40:80 psk*.cap" it also shows  that a valid handshake (1) was capture and chooses the correct AP as  target.

Thank you in advance!

*Sorry if I posted this in the wrong spot, its my first time here :)

---

### Post by Irihapeti on 2015-12-30
Thread closed.

From the Forums Code of Conduct, which you agreed to when you signed up:
> Cracking: Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closed. 

---

