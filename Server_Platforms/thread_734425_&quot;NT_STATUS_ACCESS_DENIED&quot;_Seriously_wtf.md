---
title: "&quot;NT_STATUS_ACCESS_DENIED&quot; Seriously wtf?"
date: 2008-03-24
forum: Server Platforms
---

### Post by lenswipe on 2008-03-24
Hi there

im trying to start a samba domain controller, before you say that the problem resides with samba, it doesnt...


I type the command ```
net rpc user <<username here>> add -U root
``` 
(i am already root before i type this so sudo ISNT missing :))

terminal returns to me with "NT_STATUS_ACCESS_DENIED_"

and something about error connecting to 127.0.0.1 

i am nearly finished setting up my domain, all i need to do is add domain users however i cant join a machine to the domain until i have a user with privaliges to do that on the domain itself, and i cant do that till i get around that problem..

please help

-lenswipe

---

### Post by lenswipe on 2008-03-26
bump

---

### Post by koenn on 2008-03-26
> **lenswipe said:**
> 
im trying to start a samba domain controller, before you say that the problem resides with samba, it doesnt...
-lenswipe
so you're absolutely sure the problem isn't that you do not have a domain admin because in your samba config the part about 'domain admin users = root" is missing ?

'> **lenswipe said:**
> 
I type the command ```
net rpc user <<username here>> add -U root
``` 
(i am already root before i type this so sudo ISNT missing :))

terminal returns to me with "NT_STATUS_ACCESS_DENIED_"

and something about error connecting to 127.0.0.1 

i am nearly finished setting up my domain, all i need to do is add domain users however i cant join a machine to the domain until i have a user with privaliges to do that on the domain itself, and i cant do that till i get around that problem..

-lenswipe

you're doing this on the samba machine, right ?
how about using smbpasswd in stead if that 'net' compmand ?

---

### Post by lenswipe on 2008-05-26
> **koenn said:**
> so you're absolutely sure the problem isn't that you do not have a domain admin because in your samba config the part about 'domain admin users = root" is missing ?

'

you're doing this on the samba machine, right ?
how about using smbpasswd in stead if that 'net' compmand ?

i did and it says its done it but i cant join the domain with the account.

---

### Post by lenswipe on 2008-05-26
> **koenn said:**
> so you're absolutely sure the problem isn't that you do not have a domain admin because in your samba config the part about 'domain admin users = root" is missing ?

'

you're doing this on the samba machine, right ?
how about using smbpasswd in stead if that 'net' compmand ?

i did and it says its done it but i cant join the domain with the account.

---

