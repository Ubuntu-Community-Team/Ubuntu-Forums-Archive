---
title: "Suggested Ebox port"
date: 2009-10-15
forum: Server Platforms
---

### Post by mikebou on 2009-10-15
Hi all,

I am very inexperienced when it comes to setting up servers and services. At the moment I am in the process of setting up a home server. In the past when I have played with linux servers,I have used webmin as a 'gui' remote tool. I now see that maintainer support was reduced to 1 person and he has posted a bug to pull webmin from the repository. Ebox was suggested as an alternative. I am in the middle of the installation process and it is now asking me for and address/hostname to point to ebox and a port number if required. Is there a 'default' or suggested port to use?

Kindest regards,

Michael B

---

### Post by bab1 on 2009-10-15
> **mikebou said:**
> Hi all,

I am very inexperienced when it comes to setting up servers and services. At the moment I am in the process of setting up a home server. In the past when I have played with linux servers,I have used webmin as a 'gui' remote tool. I now see that maintainer support was reduced to 1 person and he has posted a bug to pull webmin from the repository. Ebox was suggested as an alternative. I am in the middle of the installation process and it is now asking me for and address/hostname to point to ebox and a port number if required. Is there a 'default' or suggested port to use?

Kindest regards,

Michael B

The hostname/IP address is for the entire host (machine).  The port numbers are for specific services you are running.  

[**_[COLOR="DarkSlateGray"]Here[/COLOR]_**]("http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers") is a list of services and the ports they run on.

---

### Post by mikebou on 2009-10-15
Thanks Bab1, I appreciate your help.:) I have added that page to my favs for future reference. Very handy indeed.
I understood that i needed to put my server's ip or hostname in and that the ports are for different services. The documentation for setting up Ebox offered no 'suggested' port durning the setup of ldap. It did say though that the port was optional. I was wary of this because I thought it might use port 80. As it is my eventual goal is to have an internet firewall, filter, samba server for my home network. So I also wanted to make sure my decission didn't effect future install/config of other services.
I see that ldap uses port 389, so i don't know why ebox was asking for an optional port other than changing the port that ldap traditionally runs on. As it is, i chose not to enter a port and the installation did default it to 389.

Again, many thanks for your help.

MikeB

---

### Post by bab1 on 2009-10-15
Mike,

Some people run the services on "non standard" ports.  I guess they feel it is more secure (it isn't).  I'll bet eBox (to their credit) allowed for choice.

When you set up Samba make sure that you do not leave those ports open to the public side.  It is insecure. Samba is a LAN technology only.

Good luck on the project.

BruceB

---

### Post by mikebou on 2009-10-15
Cheers mate, I'll keep that in mind.
:)

Mike B

---

