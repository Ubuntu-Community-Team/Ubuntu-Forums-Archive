---
title: "Domain user into sudoers"
date: 2008-07-23
forum: Server Platforms
---

### Post by faust_ on 2008-07-23
Hi!
I'm using ubuntu server edition. And connecting to windows domain using Likewise open, but I can't use domain user as sudoer. I have added domain user into sudoers (using visudo):
domain\user ALL=(ALL) ALL
but when I use

sudo some command
it tells that user is not in sudoers list..

Help!

---

### Post by jdavis on 2008-07-23
The following post makes reference to using two slashes rather than one in sudoers.

so try:
domain\\user ALL=(ALL) ALL

rather than:
domain\user ALL=(ALL) ALL

[http://lists.likewisesoftware.com/pipermail/likewise-open-discuss/2008-February/000116.html](http://lists.likewisesoftware.com/pipermail/likewise-open-discuss/2008-February/000116.html)

---

### Post by faust_ on 2008-07-24
> **jdavis said:**
> The following post makes reference to using two slashes rather than one in sudoers.

so try:
domain\\user ALL=(ALL) ALL

rather than:
domain\user ALL=(ALL) ALL

[http://lists.likewisesoftware.com/pipermail/likewise-open-discuss/2008-February/000116.html](http://lists.likewisesoftware.com/pipermail/likewise-open-discuss/2008-February/000116.html)

that doesn't helped.. :(
he writes that user is not in sudoers list

---

### Post by jcbwalsh on 2008-08-07
I had the same problem and using the \\ worked perfectly for me.

---

### Post by likeWiseGuy on 2008-10-01
> **faust_ said:**
> that doesn't helped.. :(
he writes that user is not in sudoers list

Hi faust.

Are you still seeing this issue with sudoers? The recommended approach of using "\\" instead of "\" should do the trick for you. If it doesn't, let me know and maybe I can assist.

Thanks.

---

### Post by mdarden on 2008-10-27
likeWiseGuy,

I would like to do something similar, and have seen success with Domain\\username, but I need help with groups.  For example, I'd like all Domain Users to have sudo rights.  How do I do that?


Thanks,
     Marcus

---

### Post by mdarden on 2008-10-27
I figured it out!!

%DOMAIN\\domain^users ...

---

### Post by masterJanky on 2009-02-05
Does this only work on Domain Users?  I tried to throw the Domain Admins group in there, but no dice.  Anybody come across this?

---

### Post by brian mcgee on 2009-02-15
> **masterJanky said:**
> Does this only work on Domain Users?  I tried to throw the Domain Admins group in there, but no dice.  Anybody come across this?

Domain admins group works fine for me. Add:

```
%DOMAIN\\domain^admins ALL=(ALL) ALL
```Also, if you added:

```
winbind use default domain = yes
```To

```
/etc/samba/lwiauthd.conf
```You should be able to add a domain user as a sudoer by adding this to your sudoers file:

```
USER ALL=(ALL) ALL
```I don't need the "DOMAIN\\" prefix

---

### Post by pwebster25 on 2009-04-09
Also, if you added:

```
winbind use default domain = yes
```To

```
/etc/samba/lwiauthd.conf
```
If I do this will I be able to login to the machine itself or just into the domain?  What if I am working offline?  

Can I get the computer to adopt the user rights that are established on the domain?

---

### Post by brian mcgee on 2009-04-11
> **pwebster25 said:**
> Also, if you added:

```
winbind use default domain = yes
```To

```
/etc/samba/lwiauthd.conf
```If I do this will I be able to login to the machine itself or just into the domain?  What if I am working offline?  

Can I get the computer to adopt the user rights that are established on the domain?

You can still login with local accounts even with that change to /etc/samba/lwiauthd.conf -- if the domain controller can't be reached, the computer will used cached credentials if that user has ever successfully logged into that computer. I'm not sure I'm 100% clear on your question about user rights, but domain users can access samba shares (for example) with the same permissions their domain account is granted. Specifically, what are you wondering about?

---

### Post by Crinos512 on 2009-09-05
I have a laptop set up on a domain with the [COLOR="DimGray"]%DOMAIN\\domain^admins ALL=(ALL) ALL[/COLOR] in the visudo file.

Every thing works great! ...but whenever I take it home with me (ie. off the domain) I loose sudo rights.

(I currently get around this by using ssh to access the local machine as the local admin.)

Any ideas how I can fix this?

:popcorn:

---

### Post by brian mcgee on 2009-10-05
> **Crinos512 said:**
> I have a laptop set up on a domain with the [COLOR=DimGray]%DOMAIN\\domain^admins ALL=(ALL) ALL[/COLOR] in the visudo file.

Every thing works great! ...but whenever I take it home with me (ie. off the domain) I loose sudo rights.

(I currently get around this by using ssh to access the local machine as the local admin.)

Any ideas how I can fix this?

Not sure, maybe add the user to the sudoers file:

```
username ALL=(ALL) ALL
```

---

### Post by windowsconvert09 on 2011-08-02
> **jcbwalsh said:**
> I had the same problem and using the \\ worked perfectly for me.

Same here! Thanks!

---

### Post by linuxnoob09 on 2011-11-14
Maybe someone can help, I have had this same type of problem and have tried every conceivable combination to fix it.

Let's say I connect with a domain account

corp\me

The full domain name is corp.xxxxx.com

I really only want the corp\me account to have sudo rights.  I have tried seemingly every combination within visudo to make this happen, where am I going wrong?  Using 11.10 and connecting to domain with Centrify, although I am pretty sure that shouldn't matter in regard to this.

Do I add the user directly under the admin heading in visudo, to the end of the file???

---

### Post by chucktryon on 2013-04-05
We're on a large, distributed domain with multiple sites.  I've successfully joined the domain, but I can't just use "domain^admins" for the group name.  For reasons I won't try to go into here, our group names all have code for the office appended, like: "it admins (us)".  I understand using "^" for spaces, but is there a way to enter the "()" characters?  I tried the obvious "\(us\)", which doesn't give me a parsing error, but still doesn't work...   :-(

---

