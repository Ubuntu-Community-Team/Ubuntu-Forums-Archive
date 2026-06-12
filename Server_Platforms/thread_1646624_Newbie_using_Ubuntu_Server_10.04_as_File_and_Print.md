---
title: "Newbie using Ubuntu Server 10.04 as File and Print server"
date: 2010-12-16
forum: Server Platforms
---

### Post by ITMANAGER on 2010-12-16
Newbie with Ubuntu Server but used Desktop before.
 
Buying a new server to take pressure off the SBS 2003 server. Director not happy to buy Server 2008 & licences.
 
Will assign new server with 10.04 File and Print server roles.

[LIST]
[*]Will 10.04 pick up the users list from SBS 2003 domain controller?
[*]Can the shared folders be mapped on the desktops like with SBS 2003?
[*]Could this ever be a secondary domain controller?
[/LIST]Thanks

---

### Post by arrrghhh on 2010-12-16
Ubuntu does not replace Windows Servers as domain controllers.

You can try to shoehorn it in, but I don't think you'll be happy with the results.  Samba4 is still in its alpha stage, and running even beta software in a production environment seems like a bad idea to me.

With that said, you should be able to set it up as a file & print server with Samba3 - I believe you can have it connect via LDAP to auth users, but I've never done it before.  I've seen a ton of threads on it tho, do a search.

---

### Post by elico on 2010-12-16
it depends on your needs.
if you have a small number of users or specific usage for the server.
how techie your users are..?
how secure this server must be?

samba (v3) is emulation\mutating  window NT server so in any case you want it to be an integrated part of your domain it must be windows NT servers native.

in any case the sbs 2003 will stay so in worst case you will put specific users with the right file permissions  on the ubuntu machine and through the SBS2003 GPO you can make specific group mount at startup the shares with whatever user you need.
its pretty simple to setup if you have about extra 3 hours insteas of the money and time to spend on migrating to SBS2008.

---

### Post by crashed111 on 2010-12-16
You probably dont want to be using Windows NT4 domains by todays standards they are pretty weak in architecture and you will loose things like direct DNS integration etc. 

You can integrate it with LDAP and Kerberos there are some good guides on the internet but if you have not used Linux before I will warn you it is quite complex to set up and when it goes wrong it goes very wrong. (Personal Experience talking)

---

### Post by ITMANAGER on 2010-12-17
> **elico said:**
> it depends on your needs.
if you have a small number of users or specific usage for the server.
how techie your users are..?
how secure this server must be?
 
samba (v3) is emulation\mutating window NT server so in any case you want it to be an integrated part of your domain it must be windows NT servers native.
 
in any case the sbs 2003 will stay so in worst case you will put specific users with the right file permissions on the ubuntu machine and through the SBS2003 GPO you can make specific group mount at startup the shares with whatever user you need.
its pretty simple to setup if you have about extra 3 hours insteas of the money and time to spend on migrating to SBS2008. 
 
Thank you for all your comments.
 
Currently there will only be 15 users but different users will have different rights eg only 2 users will have full access to the Finance folder for example. As long as I can set different access rights to different subfolders, fine. 
 
No one here is really techie, so want them to see the file server as a mapped drive in Windows.
 
With regards to security, we have a Smoothwall external Firewall.
 
I feel it is worth setting up with Ubuntu and if it doesn't work, clean install of Windows.
 
Thanks.

---

