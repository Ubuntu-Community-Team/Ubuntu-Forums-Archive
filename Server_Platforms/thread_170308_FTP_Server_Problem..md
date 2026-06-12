---
title: "FTP Server Problem."
date: 2006-05-04
forum: Server Platforms
---

### Post by Katocan on 2006-05-04
Ok so, I've tried setting up PureFTPd, But when I click 'Manage Users'.
A box pops up promting me to create a password file.
[IMG]http://www.katocan.com/Screenshot.png[/IMG]

When I select 'Yes' an error comes up displaying
[IMG]http://www.katocan.com/Screenshot2.png[/IMG]

Anyone got any idea what I could do to make it work?

---

### Post by Katocan on 2006-05-04
Anyone think they could help?

---

### Post by hagen00 on 2006-05-05
Seems like a permission problem to me. It seems you don't have permissions to create the password file. I don't user the GUI much, but maybe you can somehow open the GUI under sudo?

I would do the configuring by going to the conf file and not through the GUI, but that's just me.

---

### Post by Katocan on 2006-05-05
The file permissions are 777, so I dont think its that :(, anyone got any other advice, and thanks for the reply hagen00

---

### Post by hagen00 on 2006-05-05
> The file permissions are 777, so I dont think its that , anyone got any other advice, and thanks for the reply hagen00
What file are you referring to. I think it's a permission problem with the FOLDER that it's trying to create the file in. My guess is that when it tries to create the password file, it doesn't have permission to write to that folder. 

So instead of checking file permissions, check *folder permissions*, altought i have no idea in what folder the application will try to create the password file.

---

### Post by Katocan on 2006-05-05
It trys to create it in /etc/

---

### Post by Katocan on 2006-05-05
Hmm weird, I chmodded the files and the folder with terminal and its still got the same error :(

---

### Post by hagen00 on 2006-05-05
If you chowned the /etc/ folder to the right user or even made it 777, then the application should be able to create the file there...However not a good idea at all to have etc owned by someone other than root and also it should not be 777!

I would say, go into /etc and open up the ftp conf file using ```
sudo vi
```. These conf files are quite easy to understand very often..It might just want you to create an allowed_users file in /etc, which you can then easily do manually. Basically, i'm saying, try not use the GUI but the terminal. I'm sure there are many HowTos that can help you out.

---

### Post by Katocan on 2006-05-05
Well how would I change it from the root user?

---

### Post by hagen00 on 2006-05-05
Sorry Katocan, but I don't know what exactly you're asking. 

I would do the following now.

1. Get your /etc folder back to how it should be
```
sudo chown root. /etc
sudo chmod 755 /etc
```

2. Find a howto on PureFTPd and if you can't find one, open up the pureftp conf file (should be in /etc) and see if you can't manually edit it or manually create the files such as allowed_users (or something like that) that it needs.

---

### Post by Katocan on 2006-05-05
anyone think they could help ?

---

### Post by Katocan on 2006-05-05
[QUOTE=hagen00]Sorry Katocan, but I don't know what exactly you're asking. 

I would do the following now.

1. Get your /etc folder back to how it should be
```
sudo chown root. /etc
sudo chmod 755 /etc
```

2. Find a howto on PureFTPd and if you can't find one, open up the pureftp conf file (should be in /etc) and see if you can't manually edit it or manually create the files such as allowed_users (or something like that) that it needs.[/QUOTE]
Woah lol close reply.

---

