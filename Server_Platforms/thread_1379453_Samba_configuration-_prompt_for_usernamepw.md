---
title: "Samba configuration- prompt for username/pw"
date: 2010-01-12
forum: Server Platforms
---

### Post by cmadooly on 2010-01-12
Hey guys,
 
I have a samba server running perfectly fine at the moment.
 
I'll explain the setup before asking the question.
 
I have 2 shares on it right now called "Accounting" and "Sales". The Accounting share is only open to users in the @accounting group and the Sales share is only open to users in the @sales group.
 
All users are on a Windows platform.
 
If a user from @accounting access the 'Accounting' folder, he is prompted for a username and password... if the credentials are accurate, he is able to log in. If he presses the BACK button and then goes back into the 'Accounting' folder, he is not prompted for a password as I'm sure windows stores it.
 
Now, if the same user from @accounting tries to access the "Sales" folder, he is prompted with a 'username and password' screen. Although this is accurate, where he doesnt have access to this share, I want the user to get an "Access is denied" prompt, rather than getting a prompt for his credentials.
 
Any idea what changes need to be added to the smb.conf files to do this?
 
Bottom question is- A user who tries to access a share he doesnt have access to is getting prompted for his password rather than getting an 'access is denied' prompt.
 
Any help is appreciated.

---

### Post by TwiceOver on 2010-01-12
I don't think what you are looking for is possible.  How would the share know if the incoming user has permission without asking first?

---

### Post by gobbledigook on 2010-01-13
hi!

I have thought about this issue myself about a year ago... didn't implement it as it was not necessary (only a home network ;) ) however i did remember something about using the MAC address to limit users access and capabilities. I'm at work right now... but a quick look on google shows us [**_this_**]("http://www.linuxquestions.org/questions/linux-networking-3/samba-how-to-restrict-access-to-server-via-mac-address-232458/") link which is a little old but look at the last post >

They suggest using iptables to link MAC's to IP's then you can set ip details in samba via ```
host allow [IP-address]
``` :)

I think i'm helping but as i haven't actually tried this i can't tell you what login error a host gets if their not listed with a valid ip/mac ?? I think they will just get a 404? or maybe a timeout?

---

### Post by CharlesA on 2010-01-13
They will just be asked for the username and password.

If you want the 'access is denied' message, you would have to lock down the file permissions so that they only allow the sales or accounting group access to their specific shares.

Like so:

```
drwxrwx--- 16 accounting accounting 4096 2010-01-11 12:47 /accounting
drwxrwx--- 16 sales sales 4096 2010-01-11 12:47 /sales

```

---

### Post by cmadooly on 2010-01-13
> **CharlesA said:**
> They will just be asked for the username and password.
 
If you want the 'access is denied' message, you would have to lock down the file permissions so that they only allow the sales or accounting group access to their specific shares.
 
Like so:
 
```
drwxrwx--- 16 accounting accounting 4096 2010-01-11 12:47 /accounting
drwxrwx--- 16 sales sales 4096 2010-01-11 12:47 /sales

```
 
hm.. I'll give this a shot. Thanks all!

---

