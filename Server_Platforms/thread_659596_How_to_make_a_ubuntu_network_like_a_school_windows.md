---
title: "How to make a ubuntu network like a school windows network?"
date: 2008-01-05
forum: Server Platforms
---

### Post by david_rapley on 2008-01-05
Hello helpers.

Ive made the change to ubuntu for good now and im thinking about creating a home network.

At school, we have a windows 2003 network. We all login with our own account and we are able to access our documents through 'the my documents' folder as if our account was stored on the workstation we are logged into. Though i havent figured out how this works, **im wondering how to make this type of server for my home.** , and possibly a cyber cafe later on.

I have alot of people living with me at home and user accounts gets confusing. Everyone works on one pc, saves it, then go on another pc the next day realising their work is on another pc which is in use. These PCs are XP but im looking to build UBUNTU Desktop systems if somebody can help me with below!!! \/ please read on...

So, as ive changed to ubuntu, is it possible to have people login with their own user account to a linux server and have all of their documents accessable in the 'home' folder? _Their documents will be stored on the server along with the user accounts._

Now, im kind of new to linux (havent deeply revised it in another word) [ive used it for a long time - ubuntu that is], so it would be helpful if there were tutorials in which i could follow to create the server i want and to configure ubuntu desktops to interact with the server (login and retrieve user documents).

I hope you understand what i mean, and im ready to answer any questions.

I know a bit about Ubuntu 7.10 Gusty (Desktop), and know nothing about server 7.10 ..

Any help would be VERY appreciated...


Thanks!

David

---

### Post by HermanAB on 2008-01-05
TIMTOWTDI

You can use LDAP to control login in a centralized fashion and use NFS to mount all user's home directories on a server.

You could also make diskless workstations and netboot everything off a server.

BTW there are special Linux builds for the Cyber Cafe problem that provides a turn key package including billing.

---

### Post by david_rapley on 2008-01-06
> **HermanAB said:**
> TIMTOWTDI

You can use LDAP to control login in a centralized fashion and use NFS to mount all user's home directories on a server.

You could also make diskless workstations and netboot everything off a server.

BTW there are special Linux builds for the Cyber Cafe problem that provides a turn key package including billing.

Diskless workstations?

Ive always thought this was impossible, how?

Are there any tutorials on this whole subject, because i havent a clue. :S

Please help...

---

### Post by Josh1 on 2008-01-06
If you want everyone to login using their own name and passwords, and the rest are windows, as far as I know you will need a Windows 2000/2003 server..

---

### Post by depele on 2008-01-06
You can also configure samba as an domain controller.

Once I followed a howto.
You are lucky I just found a howto for gusty
samba domain controller +openldap.

[http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10](http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10)

good luck

cya 

Arne

---

### Post by ugm6hr on 2008-01-06
> **Josh1 said:**
> If you want everyone to login using their own name and passwords, and the rest are windows, as far as I know you will need a Windows 2000/2003 server..

Would have thought so, but looks like someone has managed to do it with Ubuntu (sort-of):
[http://www.rrcomputerconsulting.com/articles/ubuntu_openldap_samba_domain-controller.html](http://www.rrcomputerconsulting.com/articles/ubuntu_openldap_samba_domain-controller.html)

---

### Post by HermanAB on 2008-01-06
"Diskless workstations?

Ive always thought this was impossible, how?

Are there any tutorials on this whole subject, because i havent a clue. :S

Please help..."

Edubuntu LTSP does that.

---

### Post by HermanAB on 2008-01-06
Here is a thread on Cafebuntu:
[https://wiki.ubuntu.com/Cafebuntu](https://wiki.ubuntu.com/Cafebuntu)

and Puppy Linux:
[http://www.murga-linux.com/puppy/viewtopic.php?t=12714](http://www.murga-linux.com/puppy/viewtopic.php?t=12714)

and Cyborg:
[http://sourceforge.net/projects/cyborg/](http://sourceforge.net/projects/cyborg/)

there are many more options.

---

### Post by david_rapley on 2008-01-07
Thanks everyone!

Im checking out all of the sites! :D

---

### Post by david_rapley on 2008-01-07
Uhm,

for home networking, edubuntu looks promising.

after reading cyberbuntu is based upon edubuntu.


which do you recommended for home network computing?

---

### Post by ugm6hr on 2008-01-07
> **david_rapley said:**
> which do you recommended for home network computing?

I think you need to clarify what OS the desktops are going to run.  Are they going to stick with Windows, or is everyone going to migrate to Linux / Ubuntu?

---

### Post by lespaul_rentals on 2008-01-07
> **Josh1 said:**
> If you want everyone to login using their own name and passwords, and the rest are windows, as far as I know you will need a Windows 2000/2003 server..

It seems like it would be so, but there are ways to do it with Linux.  openSuSE even has a setup option you can use if the server will be networked with Windows workstations, as a domain controller.

---

### Post by david_rapley on 2008-01-08
> **ugm6hr said:**
> I think you need to clarify what OS the desktops are going to run.  Are they going to stick with Windows, or is everyone going to migrate to Linux / Ubuntu?



The desktops are going to run linux, ubuntu hopefully. 

Why would i want windows if im asking on a ubuntu forum?
Windows sucks


So their going to run ubuntu.

---

### Post by ugm6hr on 2008-01-08
> **david_rapley said:**
> The desktops are going to run linux, ubuntu hopefully. 

Why would i want windows if im asking on a ubuntu forum?
Windows sucks


Sorry for the misunderstanding, but you may notice that all of the initial responses were about how to set up an LDAP server (on Ubuntu) with Windows workstations.

Edubuntu would be a sensible solution, since it is well supported with documentation etc, and you could potentially run it with (very cheap) thin clients.

---

### Post by tombutcher1990 on 2008-01-08
i think you will find you are wrong

if you setup a domain controller with something like SAMBA in ubuntu, it is infact much easier to connect a windows machine to them than a linux one.

all you do to connect a windows desktop to your linux server is right click on the my computer icon, and find the bit where you connect it to a domain, and input the name of your domain. sorted!

---

