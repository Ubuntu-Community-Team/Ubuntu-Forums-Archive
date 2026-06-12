---
title: "nmap zenmap profile editor"
date: 2008-08-06
forum: Security
---

### Post by mentisafer on 2008-08-06
HI, I'm very new to Ubuntu, and checking the forums regarding security, appears like only a firewall and port scanner might be useful. So I got firestarter, and Nmap, with the front-end Zenmap (old Nmapfe). 
In the profile editor tab when you close it it get deleted. I deleted like 3 of them, and would like to have them back. The other thing is that when I scan the output shows that only one port is scanned; I'm a novice in this area too, but I read that you should at least scan the firs 1500 ports.
How do I do that with this application?
Well, thanks in advance for any input.

Mentisafer

---

### Post by The Tronyx on 2008-08-06
Hi Mentisafer.  First of all, welcome to Ubuntu.  Secondly, you don't need to run nmap as a GUI based tool.  I'll spare you the details but I don't find the ZenMap FE to be very comfortable or intuitive.  

If you'd like a good nmap command to scan your whole system, try this:

```
sudo nmap -sS -sV -O -p- -PI -PT 127.0.0.1
```

Good luck and if you have any questions, you can either post them here or read up on the program a bit more by checking out the [Nmap manual]("http://nmap.org/book/man.html").

For a bit more info on securing your Ubuntu system, check the link in my sig, "Ubuntu Security."

---

### Post by mentisafer on 2008-08-07
Thankyou 2point0 for your help.
I did it and it gave this output

"Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-08-07 15:49 CDT
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 3.354 seconds".

Is this like every port is closed and safe, or rather that scan failed?
I actually read the manual and couldn't figure it out, that's why I tried the GUI. Any advice here is appreciated.
Oh, I'm assuming the command you suggested should be modified, changing the number 127.0.0.1 for my IP, right? Anyways I tried the command you gave me and also I did it again with my own IP adress, and gave out the same output.
ThANKS

---

### Post by Titan8990 on 2008-08-08
127.0.0.1 is known as a "loopback". It is a special address that is always your local machine. This is true with any computer using ethernet, no matter what the OS is.

Nmap recommended you try a -PN scan. Did you try that?

---

### Post by mentisafer on 2008-08-09
yes I did

sudo nmap -PN 127.0.0.1

the output read all 1700 ports were filtered; so then I stoped firestarter and scanned again, and got the same result. 
Is that good? Should I just leave it like that?

---

### Post by Titan8990 on 2008-08-11
This is good. It means you have nothing listening on a port that can be potentially compromised.

---

