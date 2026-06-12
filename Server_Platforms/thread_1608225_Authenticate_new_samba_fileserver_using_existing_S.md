---
title: "Authenticate new samba fileserver using existing Samba ldap PDC."
date: 2010-10-28
forum: Server Platforms
---

### Post by davidg121 on 2010-10-28
Current setup.... Existing Domain controller which uses ldap to auth users, running 10.04. Works perfectly...


I want to add a file server using samba that auths to the same ldap server, i have googled around looking, but haven't found too much current and relevant information. Any help would be appreciated.

---

### Post by david.garceau on 2010-10-28
bump, (not sure why i have two accounts...) lol

---

### Post by david.garceau on 2010-10-29
53 views and nothing :(

---

### Post by luvshines on 2010-10-31
Have you checked, samba.org
They have detailed explanation of smb.conf parameters and steps to perform

Just one question, you want Samba to authenticate to LDAP server directly, right ?
I didn't get this part, 'Current setup.... Existing Domain controller which uses ldap to auth users'

---

### Post by david.garceau on 2010-10-31
correct, my current domain controller has an ldap backend. 

So i need to get my new fileserver to use the same backend to authenticate users to the fileserver. This way i can track who accesses what.

---

### Post by luvshines on 2010-10-31
Gud!! The steps for Samba + LDAP are very simple, have a look at samba.org

---

### Post by david.garceau on 2010-10-31
Hmm, been doing a lot of reading... Do i need to install ldap on the fileserver? I seem to be having a hard time grasping the concept on this one :\

Do you have any helpful hints for me haha.

---

### Post by luvshines on 2010-11-01
This link is good:
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/passdb.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/passdb.html)

No, you don't need an LDAP server on the fileserver

You'll just need to set some LDAP parameter in smb.conf:
```

ldap admin dn = <value>
ldap ssl = <value>
passdb backend = <value>
ldap user suffix = <value>
ldap group suffix = <value>
ldap suffix = <value>

```

Also need to store LDAP admin password on the fileserver, smbpasswd -W command

Get an SID for you netbios name, getlocalsid

Add Samba objectclass to the users on LDAP server, set Samba attributes and its done, simple ;)

---

### Post by david.garceau on 2010-11-01
seems like there is a bit more to it than that unless i am reading incorrectly... Please do correct me if im wrong...

It seems that i need to "replace" /etc/passwd, using LDAP NSS and PAM module. Reason being is that i dont want to manually add the usernames and passwords into /etc/passwd nor do i want to have one specific password to access the fileserver.

---

### Post by luvshines on 2010-11-02
> **david.garceau said:**
> seems like there is a bit more to it than that unless i am reading incorrectly... Please do correct me if im wrong...

It seems that i need to "replace" /etc/passwd, using LDAP NSS and PAM module. Reason being is that i dont want to manually add the usernames and passwords into /etc/passwd nor do i want to have one specific password to access the fileserver.

Ah!! The steps I told you are pertaining to Authenticate Samba fileserver to existing LDAP server only, since that was the initial query, right ?? :D

**NSS and PAM LDAP will provide additional functionalities with LDAP users on the client side, but these are not necessary for 'Authentication of Samba server with LDAP' [ie access Samba server with LDAP users]**

Adding LDAP to /etc/nsswitch.conf (will also require configuring /etc/ldap.conf file) --- To resolve LDAP users on the client machine (id command will start working for LDAP users)

Adding pam_ldap.so may provide, su, sshd etc and other services for LDAP users

---

### Post by david.garceau on 2010-11-02
Lol i have no idea why i am so confused right here... okay, i dont know what i need to do... here is my goal... Once i am finished with this i am definitely posting up a tutorial for this lol. I feel that this is something that a lot of people are looking to do but most have a hard time doing. 


1. I want people to logon to their machines in the morning
2. They decide that they need to get a file on the fileserver, so they go into the fileserver that is mapped using THE same account that they logged on in the morning, so they only have one account that they need to remember.
3. I want to be able to see what user 1, user 2, and user 3 have accessed in the samba logs. As of right now they are using a single generic username and password. 
4. I also need to be able to set permissions on the fileserver to different ldap users.

---

### Post by luvshines on 2010-11-02
The machine on which ppl log on in the morning is the fileserver itself, or is it an external entity ?

---

### Post by david.garceau on 2010-11-02
External, domain controller and file server is seperate.

---

### Post by luvshines on 2010-11-02
> **david.garceau said:**
> External, domain controller and file server is seperate.

Ok, that gives some clarity now ;)
So ppl actually logon to the Domain Controller ?
2 questions:
1. What kind of DC is it ?
2. Of the 4 requirements you have listed,:D, which ones are working ?

---

### Post by david.garceau on 2010-11-02
It is running ubuntu 10.04 with samba, with an openldap backend. They can login to the domain controller fine, but they cannot access the fileserver with their normal username and password, they would have to use an account that i set up example admin-password. Everyone using the same account. So that automatically cancels out the rest of the numbers, i cannot see who does what because they all use the same account, and i cannot set permissions to different people unless i manually create different accounts.

---

### Post by david.garceau on 2010-11-02
Just wanted to take a quick moment to thank you for all the help luvshines. Your being a great help.

---

### Post by luvshines on 2010-11-03
> **david.garceau said:**
> It is running ubuntu 10.04 with samba, with an openldap backend. They can login to the domain controller fine, but they cannot access the fileserver with their normal username and password, they would have to use an account that i set up example admin-password. Everyone using the same account. So that automatically cancels out the rest of the numbers, i cannot see who does what because they all use the same account, and i cannot set permissions to different people unless i manually create different accounts.

Still a bit confusing for me :(

Let me put it the way I understand:
You have a Samba DC with LDAP backend on Ubuntu 10.04. Users logon to this Ubuntu 10.04 machine, with their credentials stored in LDAP server.
You have an external fileserver(at present accessible with only one account) which you want to integrate with same LDAP server so that users can access that with their own username/passwd.

Is my understanding correct ?

---

### Post by david.garceau on 2010-11-03
Perfect in every way, sorry about that.

---

### Post by luvshines on 2010-11-03
> **david.garceau said:**
> Perfect in every way, sorry about that.

If that is the case, then I guess you just need the authentication backend (which will be the LDAP server) for your fileserver, right ?

Since the users' regular login is already controlled by Samba PDC as LDAP backend.
How did you configure Samba DC with LDAP ?

---

### Post by david.garceau on 2010-11-03
i loosely followed 
[http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html](http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html)

and 

[https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html](https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html)

---

### Post by s1nch4n on 2010-11-04
> **david.garceau said:**
> i loosely followed 
[http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html](http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html)

and 

[https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html](https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html)
so.. do u want to set up fileserver in another pc? right?

i think u don't need to set up LDAP anymore...
just put these lines in your fileserver smb.conf

and change [FONT=Courier New]ldapsam:ldap://hostname[/FONT] with your existing LDAP server..

or u can use your existing smb.conf from your existing samba+ldap server...

i think it should be work...

>    passdb backend = ldapsam:ldap://hostname
   ldap suffix = dc=example,dc=com
   ldap user suffix = ou=People
   ldap group suffix = ou=Groups
   ldap machine suffix = ou=Computers
   ldap idmap suffix = ou=Idmap
   ldap admin dn = cn=admin,dc=example,dc=com
   ldap ssl = start tls
   ldap passwd sync = yes


---

### Post by luvshines on 2010-11-04
> **david.garceau said:**
> i loosely followed 
[http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html](http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html)

and 

[https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html](https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html)

After asking you lots of question, hunting around the bush, wasting your time :)
I would again go back to comment #8(as mentioned by s1nch4n too) and suggest that you don't need PAM and nsswitch configurations, just the LDAP + Samba config on your fileserver with the appropriate values

---

### Post by david.garceau on 2010-11-04
Getting this error on the fileserver when i go to do the net getlocalsid

```
net getlocalsid
[2010/11/04 19:02:42,  0] lib/smbldap.c:690(smb_ldap_start_tls)
  Failed to issue the StartTLS instruction: Protocol error
[2010/11/04 19:02:43,  0] lib/smbldap.c:690(smb_ldap_start_tls)
  Failed to issue the StartTLS instruction: Protocol error
[2010/11/04 19:02:44,  0] lib/smbldap.c:690(smb_ldap_start_tls)
  Failed to issue the StartTLS instruction: Protocol error
[2010/11/04 19:02:45,  0] lib/smbldap_util.c:310(smbldap_search_domain_info)
  smbldap_search_domain_info: Adding domain info for NJ-FS failed with NT_STATUS_UNSUCCESSFUL
SID for domain NJ-FS is: S-1-5-21-1482077221-1978466973-40240
```

---

### Post by luvshines on 2010-11-04
Have you set```

# Make sure you have TLS setup on LDAP server if you are using this
ldap ssl = start tls
```

If you don't have TLS on LDAP server, change it```

ldap ssl = off

```

Then restart the service and again give it a try

Also, post output for ```

testparm -s

```

---

### Post by david.garceau on 2010-11-04
That did the trick... 

Question...
In the samba config file, exactly how would i set permissions for people.... if the person logs in using testacct1 to the domain controller... In the smb.conf do i use testacct1 in the valid users, under a share?

---

### Post by s1nch4n on 2010-11-05
> **david.garceau said:**
> That did the trick... 

Question...
In the samba config file, exactly how would i set permissions for people.... if the person logs in using testacct1 to the domain controller... In the smb.conf do i use testacct1 in the valid users, under a share?
i'm using ACL to set directory/folder permissions, not from smb.conf ...

in smb.conf i only put something like this
 [FONT=&quot]
[/FONT]
[FONT=Courier New][SIZE=2]create mask = 0775
[/SIZE][/FONT]   [FONT=Courier New][SIZE=2]directory mask = 0775

[/SIZE][/FONT]     [FONT=Courier New][SIZE=2][Accounting Shared]
[/SIZE][/FONT]   [FONT=Courier New][SIZE=2]path = /our_shared_dir/accounting/
[/SIZE][/FONT]   [FONT=Courier New][SIZE=2]read only = no
[/SIZE][/FONT]   [FONT=Courier New][SIZE=2]guest = no

[/SIZE][/FONT]      [FONT=Courier New][SIZE=2][Engineer Shared]
[/SIZE][/FONT]   [FONT=Courier New][SIZE=2]path = /our_shared_dir/engineer/
[/SIZE][/FONT]   [FONT=Courier New][SIZE=2]read only = no
[/SIZE][/FONT]   [FONT=Courier New][SIZE=2]guest = no[/SIZE][/FONT]
  

and in the parent directory from samba share 
[SIZE=2]
[/SIZE]  [FONT=Courier New][SIZE=2]# chmod 775 /our_shared_dir/[/SIZE]
[/FONT]   
and retrieve gid

 [FONT=Courier New][SIZE=2]# wbinfo --group-info “Accounting”

[/SIZE][/FONT]      [FONT=Courier New][SIZE=2]Accounting:*:3000012:[/SIZE]
[/FONT]   
and then
[FONT=Courier New]
[/FONT]  [FONT=Courier New][SIZE=2]# chown root:3000012 /our_shared_dir/accounting/[/SIZE][/FONT]

---

### Post by david.garceau on 2010-11-05
Im all screwed up now... Do you think we could start from step 1...


Setup ldap server. 

What steps inside [https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)
need to be done? Are there any additional steps...

Setup fileserver...

Basic install of samba, setup the smb.conf file with 
passdb backend = ldapsam:ldap://hostname
ldap suffix = dc=example,dc=com
ldap user suffix = ou=People
ldap group suffix = ou=Groups
ldap machine suffix = ou=Computers
ldap idmap suffix = ou=Idmap
ldap admin dn = cn=admin,dc=example,dc=com
ldap ssl = start tls
ldap passwd sync = yes

Do i need SSL in order for this to work?

---

### Post by david.garceau on 2010-11-05
s1nch4n,
It also seems as if you are using winbind too. Do i need to set this up on my fileserver also?

---

### Post by luvshines on 2010-11-07
> **david.garceau said:**
> Im all screwed up now... Do you think we could start from step 1...


Setup ldap server. 

What steps inside [https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)
need to be done? Are there any additional steps...

Setup fileserver...

Basic install of samba, setup the smb.conf file with 
passdb backend = ldapsam:ldap://hostname
ldap suffix = dc=example,dc=com
ldap user suffix = ou=People
ldap group suffix = ou=Groups
ldap machine suffix = ou=Computers
ldap idmap suffix = ou=Idmap
ldap admin dn = cn=admin,dc=example,dc=com
ldap ssl = start tls
ldap passwd sync = yes

Do i need SSL in order for this to work?

Back to square one ?? LDAP server setup :)

Any success ? I always use slapd.conf thing, no cn=config stuff [you may call me orthodox :D ]

You don't need SSL for normal working of LDAP server and ldap ssl = off in smb.conf with no SSL.

**Also, never use winbind with LDAP. This is what I have learnt from my past experience**

---

### Post by s1nch4n on 2010-11-07
> **david.garceau said:**
> s1nch4n,
It also seems as if you are using winbind too. Do i need to set this up on my fileserver also?
ups... my mistake... i was using samba 4 as a DC...

but it should be no different... the only thing that u need is a SID or GID... :)

if you want to set share permission from smb.conf, first you need to set directory share permission to all user and group...

in smb.conf put these lines

[FONT=Courier New][SIZE=2][Accounting Shared]
valid users = Accounting
[/SIZE][/FONT]   [FONT=Courier New][SIZE=2]path = /our_shared_dir/accounting/
[/SIZE][/FONT]   [FONT=Courier New][SIZE=2]read only = no
[/SIZE][/FONT]   [FONT=Courier New][SIZE=2]guest = no[/SIZE][/FONT]

---

### Post by david.garceau on 2010-11-08
Ok the only way i got this to work was with winbind also, Luvshines, why exactly do you say not to use winbind?

---

### Post by luvshines on 2010-11-08
> **david.garceau said:**
> Ok the only way i got this to work was with winbind also, Luvshines, why exactly do you say not to use winbind?

You had to switch on winbind for LDAP authentication as backend on external fileserver ?

Winbind won't bring you the information from LDAP server.
So if you are configuring your external fileserver with LDAP authentication, you should switch off winbind.
Since nscd is generally recommended with LDAP, to cache data, and winbind maintains its own cache, one can run into some hard to find bugs when the caching clashes (**this generally happens when smb.conf is misconfigured to use both**)

Don't know whether it will be same in your case, but I always keep winbind off with LDAP authentication

---

### Post by david.garceau on 2010-11-09
Hmm, well see... what i had to do was install winbind, and on my fileserver i changed the nsswitch.conf to have files winbind under passwd and group. As for the passdb backend i still have it using my ldap server, and all of the ldap stuff in the smb.conf is there. Is this acceptable? If not what is the other way to get this to work? I mean it definitely appears that my ldap server is working correctly, i just need to figure out the correct way to get the fileserver to use the accounts.

---

### Post by luvshines on 2010-11-09
> **david.garceau said:**
> Hmm, well see... what i had to do was install winbind, and on my fileserver i changed the nsswitch.conf to have files winbind under passwd and group. As for the passdb backend i still have it using my ldap server, and all of the ldap stuff in the smb.conf is there. Is this acceptable? If not what is the other way to get this to work? I mean it definitely appears that my ldap server is working correctly, i just need to figure out the correct way to get the fileserver to use the accounts.

If you remove winbind from nsswitch.conf, what exactly breaks ?

---

### Post by s1nch4n on 2010-11-10
i think you don't need winbind, since winbind is only used for Samba - Windows PDC or DC integration...

take a look at this... [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/winbind.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/winbind.html)

---

### Post by david.garceau on 2010-11-10
Without winbind, how do i get sids and gids from the domain controller in order to set permissions?

---

### Post by s1nch4n on 2010-11-10
> **david.garceau said:**
> Without winbind, how do i get sids and gids from the domain controller in order to set permissions?
as far as i know... you can use getent command to retrieve uid and gid...

take a look at this... [http://wiki.samba.org/index.php/Samba_&_LDAP](http://wiki.samba.org/index.php/Samba_&_LDAP)

---

### Post by david.garceau on 2011-03-22
Going to resurrect this i have still not been able to get this all to communicate at all... Anyone have any good sources of info?

---

