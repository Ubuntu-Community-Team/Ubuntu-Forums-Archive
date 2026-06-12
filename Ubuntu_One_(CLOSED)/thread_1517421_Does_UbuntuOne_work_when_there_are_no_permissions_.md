---
title: "Does UbuntuOne work when there are no permissions for OTHERS  at its directory?"
date: 2010-06-25
forum: Ubuntu One (CLOSED)
---

### Post by patchhenk on 2010-06-25
Hi all, 

this post is my first step on this international ground! 8)



To hide the homedirectorys for other users I did: 

```
(echo; echo "umask 027") | tee --append ~/.bash_profile >> ~/.profile
chmod -R o-rwx $HOME
chmod o+x $HOME 
sudo sed -ie 's/^umask.*$/umask 027/' /etc/profile
sudo dpkg-reconfigure adduser 
```Is this a Problem for Ubuntu One working properly? 
Is there any risk of dataloss? 

Thanks for any tips! 

patchhenk

---

### Post by VH-BIL on 2010-06-25
Welcome...

I have found Ubuntu One to be a bit buggy. I use [*_dropbox_*]("https://www.dropbox.com/") which will run on Windows, MacOSX, Linux, iPhone, Android, web application, and proberbly others. It is stable and I have not had trouble with it.

---

### Post by duanedesign on 2010-06-26
I think if there was to be an issue you would notice it right away. The directory would not sync.

---

### Post by patchhenk on 2010-06-28
> **duanedesign said:**
> I think if there was to be an issue you would notice it right away. The directory would not sync.

Ok, I'll try it. My apprehension was that something could work uncorrect (not recognising it at first) and I could lose data. 

Thanks, 

patchhenk


PS.: What happend with the reply I got first? The member was talking about dropbox... 
Not interesting for me because I was asking about Ubuntu One, but I wonder why the reply disapeared.

---

