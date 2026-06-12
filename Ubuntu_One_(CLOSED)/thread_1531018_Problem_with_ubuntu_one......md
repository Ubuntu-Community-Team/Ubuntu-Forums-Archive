---
title: "Problem with ubuntu one....."
date: 2010-07-14
forum: Ubuntu One (CLOSED)
---

### Post by runvar on 2010-07-14
My problem is that whenever i start Ubuntu one from System-Preferences-Ubuntu One, i get an error saying:
Authorization Error
Errno socket error] [Errno 110] Connection timed out


I am NOT behind a proxy server

Please help!

---

### Post by Pifilatakanemu on 2010-07-15
You might want to check out [Dropbox]("https://www.dropbox.com/referrals/NTIxNTQxNzg5") if the error persists. 

I switched to it because it's more advanced than Ubuntu One. It's cross platform and offers up to 10GBs through referrals. 

Ubuntu One still is beta. I might consider using it when it's working properly, but right now there are just to many errors.

---

### Post by runvar on 2010-07-16
Thank you. Will definitely try Dropbox...

---

### Post by Excedio on 2010-07-17
Before giving up on ubuntu one can you try this?
 
> try opening terminal and doing this:-

sudo -i

then enter your password..

u1sdtool -q; killall ubuntuone-login; u1sdtool -c

I then got a message saying the syncdaemon had stopped, but no browser. 

dont touch anything for a minute and you should get some weird error message. clear this, then try selecting the ubuntu one option from your name menu.[]("http://ubuntuforums.org/showpost.php?p=9597854&postcount=5")

---

