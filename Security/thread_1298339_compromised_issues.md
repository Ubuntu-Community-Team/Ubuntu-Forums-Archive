---
title: "compromised issues"
date: 2009-10-22
forum: Security
---

### Post by yliu on 2009-10-22
Hello all,

My computer was compromised. The network security people told me that someone remotely connected to my computer and tried to attack other computers on the network. What should I do to avoid this type of problems in the future? Can I still remotely connect to my computer by ssh. I ssh from my laptop by putty to this computer if I work at home. Besides by setting strong password, what type of free software can keep safe? 

Thank you!
-Ying

---

### Post by ApEkV2 on 2009-10-22
install/configure fail2ban

---

### Post by Nepherte on 2009-10-22
There are a few ways to secure your ssh server:
[list]
[*]Do not use passwords, but authorize with public/private key pair
[*]Change default ssh port
[*]Limit maximum attempts to connect
[*]Do not allow root logins
[*]...
[/list]

---

### Post by yliu on 2009-10-22
Thank you ApEKV2 and Nepherte ! This is very helpful!

-Ying
[U]
[/U]

---

### Post by lovinglinux on 2009-10-22
> **Nepherte said:**
> There are a few ways to secure your ssh server:
[list]
[*]Do not use passwords, but authorize with public/private key pair
[*]Change default ssh port
[*]Limit maximum attempts to connect
[*]Do not allow root logins
[*]...
[/list]

+1 

Do not use passwords for ssh authentication. Use encrypted keys.

See:

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

BTW, a clean install would be nice, since would be hard to determine the extent of damages caused by the intruder.

---

### Post by yliu on 2009-10-22
Thank you lovinglinux! I am reinstalling everything...

-Ying

---

### Post by __p1n__ on 2009-10-23
> **yliu said:**
> Hello all,

My computer was compromised. The network security people told me that someone remotely connected to my computer and tried to attack other computers on the network. What should I do to avoid this type of problems in the future? ...

Boot the computer using a livecd containing your assessment tools.  Don't bring the network interface up until you've changed the MAC address and set the IP address to something bogus like 1.1.1.1.  Run wireshark on the interface and look at the traffic to determine the netmask typically in use.  At the same time have netdiscover and p0f listening passively on the interface and find out what hosts are up and what type of os that they're running.  You can then change the IP address of your nic to something not currently in use but valid given the subnet and begin to interact with the network then.

The critical thing is not to use the configured MAC address on your nic or your typical IP address.  A potential problem could arise if the lan admins have tied switch ports to specific MAC addresses.  If so then you will need to jack into someone else's lan port.

That should fix the noise from the network security people.

---

### Post by yliu on 2009-10-23
Thanks p1n! First time to hear the Wireshark, sounds really powerful. 

Cheers,
-Ying

---

### Post by ukripper on 2009-10-23
fail2ban is must have if you got SSH setup. And also i have AIDE up and running for intrusion detection [http://www.debuntu.org/intrusion-detection-with-aide](http://www.debuntu.org/intrusion-detection-with-aide)

And keep an eye on your logs. I use logwatch(in repos) for that purpose

---

