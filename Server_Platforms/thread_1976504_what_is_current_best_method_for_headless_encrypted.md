---
title: "what is current best method for headless encrypted NAS?"
date: 2012-05-08
forum: Server Platforms
---

### Post by ijason on 2012-05-08
greetings.

i am trying to find out what the popular consensus is for the best method and emplimentation of a headless NAS with encryption is. i have read some great advice in some older threads on here, but haven't seen one newer than a few years ago that really addresses my question.

i have two needs for this : that my data is secure through the entire transmission process. and that my sensitive data is secured against physical theft.

my plan is to invest in a fairly robust secure router, and rely on it to handle my secure connection needs. either [[COLOR="Blue"]this model[/COLOR]]("http://www.amazon.com/ZyXEL-Internet-Security-Firewall-Gigabit/dp/B0042W7CAI/ref=sr_1_3?s=electronics&ie=UTF8&qid=1336520853&sr=1-3"), or similar  which will facilitate all VPN and firewall handling from within the router itself. PRESUMABLY restricting access to my NAS to only the correct people. of course, i am open to suggestion if the opinion is that i won't need a secure router if i set things up properly on the NAS machine itself.

i don't need the entire NAS machine to be encrypted, so i don't think i'll need to worry about encrypting the OS. i have used TrueCrypt for years and it is my first go-to idea for encryption needs, but this is where i want to find out what everyone here thinks :

is there a better/easier solution than the following : SSH thru my security appliance via public/private key, mount the encrypted drive, access files via SAMBA. ??? 

to me it sounds like the entire data transfer will be encrypted, and my information is secured from theft. but i have no idea if there is a more gracefull or simple or more fully-featured solution. another potential snag is i will be running all communications through a proxy, and i have no idea if that will cause problems.

suggestions, advice, all will be greatly appreciated :)

---

### Post by nothingspecial on 2012-05-10
*Thread moved to **Server Platforms**.*

---

### Post by Bushflyr on 2012-05-12
I'm a total n00b, so I may be way off base, but why not just create a user with an encrypted home directory on your NAS?

Then do whatever manipulation you need to do on your local machine, encrypt the file and drop it on your NAS.

No special hardware needed, and only one extra step on the local machine.

---

