---
title: "Java dpkg error"
date: 2015-12-06
forum: Ubuntu Development Version
---

### Post by owen9 on 2015-12-06
Hi everyone its me again, i am getting the error:
dpkg (subprocess): unable to execute installed post-installation script (/var/lib/dpkg/info/libsvn-java.postinst): Exec format error
dpkg: error processing package libsvn-java (--configure)

I get these errors when creating a re master in chroot , following the Ubuntu From Scratch guide, can anyone help?

---

### Post by zika on 2015-12-06
If You were to give us content(s) of [COLOR=#000000]/var/lib/dpkg/info/libsvn-java.postinst [/COLOR]it would be much easier.

---

### Post by owen9 on 2015-12-06
Hmm i havent got one, strangely there is not one, this is obviously the error but how do i fix it?

---

### Post by owen9 on 2015-12-07
Can you reply please?

---

### Post by zika on 2015-12-07
> **owen9 said:**
> Hi everyone its me again, i am getting the error:
dpkg (subprocess): unable to execute installed post-installation script (/var/lib/dpkg/info/libsvn-java.postinst): Exec format error
dpkg: error processing package libsvn-java (--configure)

I get these errors when creating a re master, following the Ubuntu From Scratch guide, can anyone help?

> **zika said:**
> If You were to give us content(s) of [COLOR=#000000]/var/lib/dpkg/info/libsvn-java.postinst [/COLOR]it would be much easier.

> **owen9 said:**
> Hmm i havent got one, strangely there is not one, this is obviously the error but how do i fix it?

> **owen9 said:**
> Can you reply please?It is not a custom here to bump a thread in this way. I might be wrong... We are not sitting in front of a page with this forum opened all day long, sorry...
What is the question you beg us to reply to?
If that machine were mine and I were sure that this file is nonexistant I would try```
sudo touch [COLOR=#000000]/var/lib/dpkg/info/libsvn-java.postinst[/COLOR]
```[COLOR=#000000]but that is only me, I would have a bit better insight in what is going on if that were my machine than here, after reading Your post(s). So, do give us a bit more insight and answer might come, I do not promise... ;)
Are You sure that You did not mix architecture for some packages/files involved? Which shell are You running because zsh would object if (as I suggested) file is of 0 length, etc... Many unknowns and...[/COLOR]

---

### Post by owen9 on 2015-12-07
I have this file in [COLOR=#000000]/var/lib/dpkg/info/libsvn-java.postinst its the chroot were this file is missing, i will try to touch the chroot version of [COLOR=#000000]/var/lib/dpkg/info/libsvn-java.postinst[/COLOR][/COLOR]

---

### Post by zika on 2015-12-07
> **owen9 said:**
> I have this file in [COLOR=#000000]/var/lib/dpkg/info/libsvn-java.postinst its the chroot were this file is missing, i will try to touch the chroot version of [COLOR=#000000]/var/lib/dpkg/info/libsvn-java.postinst[/COLOR][/COLOR]Just what I was writing about. Looking thorugh clogged keyhole You've provided, where on Earth could we suppose that You've been writing about chroot? Over&out.

---

### Post by owen9 on 2015-12-09
Don't mean to be rude but you haven't helped at all, i finally provided the info about this being an error in chroot, but you didn't exactly help!

---

### Post by cariboo on 2015-12-10
We are all volunteers here, so you will have to make things as easy as possible for us to be able to help you, Please create a post with as much detail as possible, just saying you are having a problem installing java in a chroot doesn't help. at least post the error message you you are getting. Another thing to include is which java package are you trying to install, the Oracle version, or openjdk.

---

### Post by owen9 on 2015-12-10
I did post the error on the first post!

---

### Post by cariboo on 2015-12-10
> **owen9 said:**
> I did post the error on the first post!

I guess I missed it because you didn't use quotes, so it didn't stand out. 

You're still not giving us the kind of information we need to help you. Please explain what you are trying to do with screenshots and links if possible.

---

### Post by owen9 on 2015-12-10
Ok i am trying to create a re master for an open source os ( the linux schools project - client version ), the script made to do this is based of the link:
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

So when it is creating the chroot environment it fails because of java packages, i need to get this fixed for a new release for the client os however i cant because of this.

---

