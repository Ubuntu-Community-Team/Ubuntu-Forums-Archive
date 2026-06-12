---
title: "TCP security threat"
date: 2016-08-09
forum: Security
---

### Post by Bike To Australia on 2016-08-09
University of California, Riverside posted a description and fix for a security threat to all Linux systems. It is posted in Phys.org, titled "Study highlights serious security threat to many internet users" on August 9th, 2016 with this link: [http://phys.org/news/2016-08-highlights-threat-internet-users.html](http://phys.org/news/2016-08-highlights-threat-internet-users.html)

I tried "Qian recommends the following temporary patch that can be applied to both client and server hosts. It simply raises the `challenge ACK limit' to an extremely large value to make it practically impossible to exploit the side channel. This can be done on Ubuntu, for instance, as follows: 1. Open /etc/sysctl.conf, append a command "/net.ipv4/tcp_challenge_ack_limit = 999999999".
 2. Use "sysctl -p" to update the configuration."

In Terminal, but got error messages.

---

### Post by mike.s on 2016-08-11
Get rid of the leading slash... it should be like this:

# Fix for TCP attack
net.ipv4.tcp_challenge_ack_limit = 999999999

---

### Post by Habitual on 2016-08-11
in terminal:
```
sudo echo "net.ipv4/tcp_challenge_ack_limit = 999999999" >> /etc/sysctl.conf
sudo sysctl -p
```
done.

---

### Post by cogset on 2016-08-27
Is there an Ubuntu security notice for this? Has it been fixed yet?

---

### Post by howefield on 2016-08-27
[https://people.canonical.com/~ubuntu-security/cve/2016/CVE-2016-5696.html](https://people.canonical.com/~ubuntu-security/cve/2016/CVE-2016-5696.html)

---

### Post by ephesians88 on 2016-08-29
I know this might be a bit far-fetch and based on my ignorance on how Linux update systems works, but does anyone think this can effect Ubuntu updates? If I applied the work around to [COLOR=#000000]/etc/sysctl.conf[/COLOR] only after running "apt-get update" and "apt-get dist-upgrade" do I have anything to worry about? It is reassuring that Debian and Ubuntu both prioritize this issue with a medium rating though.

---

### Post by deadflowr on 2016-08-29
> **ephesians88 said:**
> I know this might be a bit far-fetch and based on my ignorance on how Linux update systems works, but does anyone think this can effect Ubuntu updates? If I applied the work around to [COLOR=#000000]/etc/sysctl.conf[/COLOR] only after running "apt-get update" and "apt-get dist-upgrade" do I have anything to worry about? It is reassuring that Debian and Ubuntu both prioritize this issue with a medium rating though.

They'd need to replace the keys you and the repos both have in order to break the update mechanism.
Otherwise your system would simply ignore or warn you of untrustworthiness if the updates if they somehow came to you corrupted.

Perhaps a little night reading:
[https://help.ubuntu.com/community/SecureApt#Validation_of_Release_File_and_Packages]("https://help.ubuntu.com/community/SecureApt#Validation_of_Release_File_and_Packages")

---

### Post by ephesians88 on 2016-08-30
thank you

---

