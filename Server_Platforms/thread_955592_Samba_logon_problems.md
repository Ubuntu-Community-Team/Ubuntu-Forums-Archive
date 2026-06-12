---
title: "Samba logon problems"
date: 2008-10-22
forum: Server Platforms
---

### Post by Buntubailey on 2008-10-22
Hello,

I have been trying to set up my server and have managed to create a RAID5 array and install the server with samba, open ssh and print server, then I installed webmin. I am trying to configure it so when I access the shares from a windows machine it asks for user and password, I have managed to make it do this but for some reason the only username and password it will accept to access the shares is the root(administrator). When I try to log in with any of the users I have created windows tells me logon failed or I don't have sufficient priveliges. I have made sure that the unix users and samba users are the same, and in webmin, I have set in the samba section that all users should be able to connect with their username and password. It even says in the samba share list that all the shares are read/writable to everyone but I am finding when I try to connect from a windows machine that it rejects me everytinme unless I logon with root credentials.

Is there anyone who could help me out on this matter I am pulling my hair out,

Thanks in advance,

Buntubailey.

---

### Post by smileypaul on 2008-10-22
I'm not familiar with webmin.

But generally, make sure you have set samba passwords

sudo smbpasswd -a username

and also, make sure the users have group or owner permissions of the share you are sharing.

orr... do the non-secure way, and just blow the thing wide open.

sudo chmod 777 ./directory   (not safe!)

It could also be restricted in the smb.conf file, generally there is a "Valid Users" section defined udner each share.. it may be set to "Valid Users = Root" .

Just a few things to check, sorry, hopefully someone with webmin experience can chime in.

Best of Luck..

Paul

---

### Post by Buntubailey on 2008-10-22
Thankyou smileypaul you have hit the nail on the head, as soon as I set smbpasswd it worked, I just assumed that this was automatically done when converting unix users to samba users. obviously I was wrong but so pleased it is working now, now my only problem is restricting certain users to certain shares, do you know which part of the smb conf lets certain users in to write and not others, i thought i could do this through webmin but now i'm not so sure.

Thanks again

Buntubailey

---

### Post by Buntubailey on 2008-10-22
Aaarrrggg! Just noticed that I can now logon with valid users to each of the shares but I can't write anything to the shares, just when I thought I was getting the hang of this :-(

---

### Post by lykwydchykyn on 2008-10-22
Click on the file share in webmin, and go to "security and access control" for that share.  Make sure "writeable" is set to "yes".  It defaults to "no" for security reasons.

---

