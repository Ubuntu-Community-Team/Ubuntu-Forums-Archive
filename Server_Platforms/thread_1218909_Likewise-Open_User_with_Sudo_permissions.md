---
title: "Likewise-Open User with Sudo permissions?"
date: 2009-07-21
forum: Server Platforms
---

### Post by NewbieNik on 2009-07-21
Hi everypeeps, I am hoping somebody here can help me.
I have Ubuntu 9.04 32bit running on a Win2K3 AD site. I have install Likewise-open5 with the lsas and gui modules (Also Vr5)
I have joined the domain and can see my Ubuntu box in AD. I have had to edit the krb5.conf file to include the realm (Not to sure why, would have thought that would be as standard) and I can log on as my Windows user by either using DOMAIN\username or [email]username@domain.com[/email]. Great!!!

Unfortuantely I cannot make any config changes as this user, in particular apt-get update or dpkg -i.
I have tried adding the user to sudoers by both methods above, but the @ method causes parsing errors.
I have added the user to root and admin groups by:-

Su
adduser DOMAIN\name admin
adduser [email]name@domain.com[/email] admin

These all seem successful, but running sudo tells me I don't belong to sudoers or I don't have permission to lock the apt-get file.  The AD users obviously do not appear in the Users list so I cannot add them to the groups there. 
Due to the networks ISA servers, I need to be able to run sudo as myself as running SU passes the root credentials which the ISA server rejects....

Any helpful advice would be greatly appreciated.

---

### Post by bacil on 2009-07-21
add yourself to /etc/sudoers

---

### Post by NewbieNik on 2009-07-21
> **bacil said:**
> add yourself to /etc/sudoers

Uhhh...I have. Like I said in the original post, I have added myself to the sudoers list as both DOMAIN\name and name@domain, but the @ entry causes parsing errors and the domain\name entry still gets the :-

not a member of sudoers 

message....

Next? (And please read the post before responding...thanks)

---

### Post by NewbieNik on 2009-07-21
Sorry, that was out of order. 
Just get a little irked when you explain stuff and people ask you to do something you already explained...I do appreciate your help.

Forgive my short-temperedness

---

### Post by bacil on 2009-07-21
sorry it was my fault i havent read that properly.

#Members of the Admin group may gain root privileges and do the following:
%(domain)\\(group) ALL=(ALL) ALL

from this i guess you need to add yourself to group first and group to sudoers

athis might help aswel

			 			     				/etc/samba/lwiauthd.conf: add line &#8220;winbind use default domain = yes&#8221; 
 

```
sudo /etc/init.d/likewise-open restart
```


 then you can log in as &#8220;USER&#8221; instead of &#8220;DOMAIN\USER&#8221;

---

### Post by NewbieNik on 2009-07-21
> **bacil said:**
> sorry it was my fault i havent read that properly.

#Members of the Admin group may gain root privileges and do the following:
%(domain)\\(group) ALL=(ALL) ALL

from this i guess you need to add yourself to group first and group to sudoers

athis might help aswel

			 			     				/etc/samba/lwiauthd.conf: add line &#8220;winbind use default domain = yes&#8221; 
 

```
sudo /etc/init.d/likewise-open restart
```


 then you can log in as &#8220;USER&#8221; instead of &#8220;DOMAIN\USER&#8221;

OK, looking at the system, Samba is not running the show. There is no Winbind installed. There is also no lwiauthd.conf file anywhere.
As far as I can tell Likewise-open uses the Kerberos ticket system, but I cannot see anywhere in the conf files to set what group Likewise users should belong to. 
As I can't see the users, I cannot add them to any groups, so I'm kinda stuck in a Catch22 situation

Also tried the sudoers group add using:-
%Domain\user ALL=(ALL) ALL

But that still won't let me sudo...any thing else I can try or anyone else had this issue?

---

### Post by NewbieNik on 2009-07-21
AARRGGHHH....
OK, added sudoer by using:-
%DOMAIN\\Group ALL=(ALL) ALL    (notice the double\)

And that now lets me sudo. Unfortunately I get blocked at the ISA server again so it's obviously not passsing my credentials through by using sudo.
Thanks again for your help so far. One big leap foward however, I am going to beat networking over the head with my Ubuntu box to see if that helps

---

### Post by HermanAB on 2009-07-21
Howdy,

You should define a Primary Group in Active Directory for all Linux users.  This primary group should NOT contain any spaces.  Sudo cannot handle spaces in group names and the default MS Windows group is something like "Domain Users" which of course has a space in it - then you can add previleges in the /etc/sudoers file to the Linux groups assigned by ADS.

---

### Post by NewbieNik on 2009-07-21
> **HermanAB said:**
> Howdy,

You should define a Primary Group in Active Directory for all Linux users.  This primary group should NOT contain any spaces.  Sudo cannot handle spaces in group names and the default MS Windows group is something like "Domain Users" which of course has a space in it - then you can add previleges in the /etc/sudoers file to the Linux groups assigned by ADS.

Herman,
Thanks for this. Unfortunatly I have already tried it and it doesn't give me the right access. However you are correct about the spaces.....Good tip! (People, avoid spaces, dots and weird characters in your Groups!)

What I found is that adding the user as DOMAIN\\User in sudoers does give you sudo rights (It HAS to be a double backslash). I also found setting the proxy in Firefox allowed internet access through the ISA server.
What wuldn't work is any BASH access through the ISA (Even Synaptic failed) Ubuntu would not pass my credentials to the ISA server for some reason.

After an hour or two of discussions with our networking team they gave up, but I'm like a ferret (Not furry with big teeth..persistant)

I installed NTLMaps. This asked for my credentials and the ISA server details. I now have the proxy settings in Ubuntu and Firefox pointing to Localhost 5268 and that seems to send credentials OK, although it is VERY slow, it works...just.

Thanks for all your help guys, any additional details or tips to help will still be tried and commented on.

---

### Post by jhjessup on 2010-04-02
I just finished setting this up under 10.04 beta. I've given sudo permissions to members of "DOMAINNAME\Domain Admins" by adding the following line to the sudoers file:

```
%DOMAINNAME\\domain^admins ALL=(ALL) ALL

```

It appears that spaces in domain group names can be replaced with carats.

(Of course, you'll need to replace DOMAINNAME with your own domain name)

---

