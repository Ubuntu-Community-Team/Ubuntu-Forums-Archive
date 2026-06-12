---
title: "Samba not installed by default?"
date: 2010-01-17
forum: The Cafe
---

### Post by user1397 on 2010-01-17
I just noticed yesterday that I did not have samba installed so I couldn't access my network until I sudo apt-get install'd it.

Shouldn't it be installed by default?  I thought I remember it being installed by default on older ubuntu releases.

---

### Post by CharlesA on 2010-01-17
You can choose to install it when you install the server OS.

I prefer installing it after I create all the users and crap, so I don't have to do more work. :P

---

### Post by sisco311 on 2010-01-17
You are prompted to install it when you try to share a file.

---

### Post by user1397 on 2010-01-17
Yea but shouldn't it be installed by default for users to be able to view shared files in their home networks?  When I went to Places > Network > Windows Network, it didn't prompt me to install samba it just gave me an error pop-up.

---

### Post by CharlesA on 2010-01-17
What was the error you got?

I've browsed to files on my network from a clean install of Ubuntu Desktop. No errors.

---

### Post by user1397 on 2010-01-17
> **CharlesA said:**
> What was the error you got?

I've browsed to files on my network from a clean install of Ubuntu Desktop. No errors.
this was the error:

"Unable to mount location
Failed to retrieve share list from server"

---

### Post by juancarlospaco on 2010-01-17
Unix dont need Samba, you can use SSH or NFS, 
*also SMB protocol creates a spamm on broadcast packages, eat bandwith.*

---

### Post by CharlesA on 2010-01-17
What OS are you trying to connect to?

---

### Post by user1397 on 2010-01-17
> **CharlesA said:**
> What OS are you trying to connect to?Windows and/or OS X

---

### Post by cariboo on 2010-01-17
Ubuntu connects to Windows by default, without having to install any extra software. You have problems elsewhere.

I would suggest you start a thread in the support forums, to get help solving the problem.

---

### Post by user1397 on 2010-01-17
> **cariboo907 said:**
> Ubuntu connects to Windows by default, without having to install any extra software. You have problems elsewhere.

I would suggest you start a thread in the support forums, to get help solving the problem.I don't have any problems, I was just wondering why samba isn't installed by default. And how can ubuntu connect to windows so magically without samba?

---

### Post by Morbius1 on 2010-01-17
The samba package is a server package. It's purpose is for you to serve your folders to others on your network. It can however control certain aspects of a client and should be there by default.

Anyone who has ever gotten this error:
> Server requested LANMAN password (share-level security) but 'client lanman auth' is disabledwhen trying to access a remote share knows the only fix is to add:
> client lanman auth = Yes 
lanman auth = Yes  to the smb.conf [COLOR=Blue]**of the client**[/COLOR] and restart the samba service. Comes up mostly with NAS devices.


So I agree with you that it should be installed by default but not for the reason you stated.

---

### Post by humphreybc on 2010-01-17
Samba probably isn't installed by default due to size:

samba is 18.3MB

samba-common is 733kB

samba-common-bin is 14.3MB

That is a LOT of space when you're trying to fit an entire OS and a library of applications on a 700MB CD.

---

### Post by Cuddles McKitten on 2010-01-17
The server shouldn't be installed by default for security reasons if nothing else.  Open ports = bad.  Open ports that can allow remote access to hard drive when misconfigured = very bad.

The client, on the other hand, probably should be installed by default.  I'm guessing the size reason mentioned above is one of the main factors.

---

### Post by Icehuck on 2010-01-17
Out of the box nautilus will connect to samba shares.

---

### Post by cariboo on 2010-01-17
Smbclient is in the default Ubuntu installation allowing you to connect to Windows shares.

---

