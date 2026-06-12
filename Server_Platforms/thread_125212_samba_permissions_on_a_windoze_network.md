---
title: "samba permissions on a windoze network"
date: 2006-02-03
forum: Server Platforms
---

### Post by jezjones on 2006-02-03
Hi there everyone,

I use samba at home to provide a file server on my lan, which has been fine with only one or two users.

I have now had to set up a development web server at work, which has gone well so far, I have all the pieces on there and working but i am having problems getting the right permissions for samba.

There is a small group of people (5 or less) who need to connect to this machine and use it to store their work, apache is exposing user directories so that people can test.
The box is on a large corporate domain with its own domain controllers but i just want to ignore those as i will likely face difficulties getting info about them.

I am happy to maintain the users on the server so that they have a local unix account and HOST/~username works for the web, but i need to know how to set the permissions within samba to allow this.
I also have one share that i want them all to access in addition to their own folders.

So far i have the unix users and have created the samba users, i have set the security within the smb.conf to be USER

When i try and access the shares it prompts for a password but then doesnt accept the password.

Any hints would be greatly appreciated.

Jez

---

### Post by LordHunter317 on 2006-02-03
To enable Samba access, you need to give them a Samba password via:```
sudo smbpasswd -a <user>
``` for each user.

The best way to control the group share is to add them all to a group, then give that group ownership over all files and directories in the share.  Add the 'setgid' bid to all existing directories:```
sudo find /srv/example -type d -print0 | xargs sudo chmod g+s
```Finally, force Samba to propogate the bit forwards by adding these lines to the share defintion:```
directory mask = 2770
create mask = 660
```

---

### Post by jezjones on 2006-02-03
Thanks for that info, I have done that now.

I think it is putting me in the right direction but i think that the problem is how i am telling samba to do the authentication.

I am still having problems with access, it does not seem to accept my password, although i have checked and reset it to make sure i am putting in the right one.

By having the security set as USER, that should prompt for a username / password pair when you try and access any share.
The username and password it is looking for are the linux user account name and password that i have set up and done an smbpasswd -a <user> on.

Is this right ? or does it look somewhere else for these details?

Thanks

---

### Post by LordHunter317 on 2006-02-03
YEs, it was your UNIX system account name and the smbpasswd.

You need ot make sure you have permissions to access the share (i.e., filesystem permissions).  If you don't, you'll still get 'Access Denied' after authenticating.  If your login is rejected, you'll just get prompted for it a second time.

---

### Post by Iowan on 2006-02-03
[QUOTE=jezjones]When i try and access the shares it prompts for a password but then doesnt accept the password. [/QUOTE] Just a thought - albeit probably a bad one...
By"doesn't accept" you DO mean it gives an error of some sort - not just no echo with asterisks?

Never mind... you DID say is is on a windoze network.

---

### Post by jezjones on 2006-02-05
Thanks i will try the file permissions.


When i say not accepted, i mean that you put in the username / password pair and then the box appears again blank as though the details are not correct.

---

### Post by jezjones on 2006-02-06
OK the file permissions are all correct, but still it just returns an empty username - password dialog box and prompts me to enter my details again.

I understand the unix user stuff, what i am having problems with is the samba stuff... 

It is confusing because there seems to be unix users, samba users and then i have my windows users aswell. I dont understand which user accounts are being checked and when.

Is it ok for the users who are accessing this machine to only have a unix account on the actual machine.. i.e. their windows login on the network is completely different and managed by an LDAP server, which is why i dont want to muddy the waters by getting involved with it.

---

### Post by LordHunter317 on 2006-02-06
[QUOTE=jezjones]It is confusing because there seems to be unix users, samba users[/quote]There's not.  There are UNIX users.  What there are is **two passwords**.

A UNIX password, and a Samba one.  You **must** use your Samba password, the one you gave for that user when prompted with 'smbpasswd -a user'.

You won't login with anything else.

> Is it ok for the users who are accessing this machine to only have a unix account on the actual machine..They must have one, or they won't be able to login in, peroid.

>  i.e. their windows login on the network is completely different and managed by an LDAP server, which is why i dont want to muddy the waters by getting involved with it.Why?  That would be far better for the users because it would be transparent, and it would be easy to setup, if by LDAP you mean Active Directory.

---

### Post by jezjones on 2006-02-09
Ok I have it working now, it was down to the group configuration. For some reason the first users i created was in the users group but the second was put a group called staff. So once i made them both users and got rid of this new group staff it worked, as the file permissions had the group set to users.

Thankyou for the explanation about the different users, I see what you mean, and i was confused because i was setting the unix and samba passwords as the same thing and then thinking of them as separate user accounts.

The LDAP or Active Directory side of things is outside of my control and i only know what a colleague told me which was '..an LDAP server ..' 
I agree it would have made it more transparent for the users.

Thanks again.

Jez

---

