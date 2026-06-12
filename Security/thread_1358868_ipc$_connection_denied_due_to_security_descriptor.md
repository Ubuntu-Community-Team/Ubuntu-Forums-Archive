---
title: "ipc$ connection denied due to security descriptor"
date: 2009-12-18
forum: Security
---

### Post by chaudharyumesh on 2009-12-18
Hi All,
Recently i have installed Ubuntu server and configure the samba.
After that i am able to share the directories on windows system, i am able to join the windows system in samba domain but when i am going to login through samba users it is giving the error computer account not found..
i have check in logs, i found the error
transport endpoint is not connected
ipc$ connection denied due to security descriptor

i tried all the way but no luck i have not found any solution on this issue...Someone know this issue please help me out.........

Thanks

---

### Post by chaudharyumesh on 2009-12-19
I fed up becuase of this issue please help me out if anyone knows the solution

i am able to access share folders from windows.
i am able to join windows system to samba domain but i am not able to login on that system with samba user

---

### Post by bodhi.zazen on 2009-12-19
google search using those error messages. There are several posts on several mailing lists, but I do not understand windows.

Another possibility is that those error messages mean noting more then "permission denied", check your permissions on your shares.

---

### Post by chaudharyumesh on 2009-12-20
also when i am running command testparm -v ..then it is giving warning for netlogon share modes option is deprecated ...could you please help me out in this
 root@esmechsrv01:~# testparm -v
Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[netlogon]"
WARNING: The "share modes" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[HB Design]"
Processing section "[IT Data]"
Loaded services file OK.
Server role: ROLE_DOMAIN_PDC

---

### Post by bodhi.zazen on 2009-12-21
It appears as if that is a warning, that the option you are using is depreciated.

Can you post the RELEVANT portion of your config file, the few lines pertaining to section "[netlogon]" ?

---

### Post by chaudharyumesh on 2009-12-21
hi
netlogon portion in smb.conf is

[netlogon]
    writable = yes
    path = /home/samba/netlogon
    guest ok = yes
    comment = Network Logon Service
    public = yes
    share modes = no

---

### Post by bodhi.zazen on 2009-12-21
Is there a reason you have the "share modes = n" option ?

I am unfamiliar with that option, but from here:

[http://oreilly.com/catalog/samba/chapter/book/ch05_05.html](http://oreilly.com/catalog/samba/chapter/book/ch05_05.html)

> 
[accounting]
    share modes = no 

We highly recommend against disabling the default locking mechanism unless you have a justifiable reason for doing so. Most Windows and DOS applications rely on these locking mechanisms in order to work correctly, and will complain bitterly if this functionality is taken away.

---

### Post by chaudharyumesh on 2009-12-21
i am not able to understand share modes = no means oplocks is disabled
can you please tell me which option should i place

---

### Post by bodhi.zazen on 2009-12-21
I believe the default behavior here is share modes = yes , which is default.

You are over riding this behavior with share modes = no , and the page I linked indicated that doing so will cause problems.

It seems you do not know why you are over riding the defaults, so I suggest you eliminate that line altogether and go with the defaults.

---

