---
title: "so this is how you add a ppa"
date: 2010-04-13
forum: The Cafe
---

### Post by stmiller on 2010-04-13
Credit - saw this on the Shutter project page.

[http://shutter-project.org/downloads/](http://shutter-project.org/downloads/)

```
sudo add-apt-repository ppa:shutter/ppa
```

This command adds the repository, imports the key, and everything!

I'm not going to tell you all of the chaos I have been doing to add a ppa...

---

### Post by loell on 2010-04-13
didn't you know? ;)

---

### Post by dominiquec on 2010-04-13
Neat!

---

### Post by NightwishFan on 2010-04-13
I learned this later than I should have, but this is now news to me. For anyone that wants to know, you need to append the part of the ppa that is listed in bold on the ppa page. It works for all of them, and imports the key. :guitar:

---

### Post by toupeiro on 2010-04-13
Yeah I discovered this maybe a couple of months back and really like this method.

---

### Post by Uncle Spellbinder on 2010-04-13
Old school for me. I still prefer to do it manually by editing sources.list.

---

### Post by 3rdalbum on 2010-04-13
> **Uncle Spellbinder said:**
> Old school for me. I still prefer to do it manually by editing sources.list.

And then going to the PPA's website, getting the URL of the GPG key, using Curl to retrieve the contents of the keyfile and pipe it to apt-key. Too much work. Just use add-apt-repository!

---

### Post by ad_267 on 2010-04-13
And it nicely puts all the added repos in the sources.list.d directory rather than appending them to the source.list file. :)

---

### Post by madjr on 2010-04-13
ubuntu-tweak comes with lots of ppas

---

### Post by Uncle Spellbinder on 2010-04-13
> **3rdalbum said:**
> And then going to the PPA's website, getting the URL of the GPG key, using Curl to retrieve the contents of the keyfile and pipe it to apt-key. Too much work. Just use add-apt-repository!
I only us PPA's from Launchpad or Ubuntu Source List Generator. All that info is on one page. Very easy.

---

### Post by lovinglinux on 2010-04-13
Keep in mind that command only works for Karmic and Lucid.

---

### Post by Ric_NYC on 2010-04-13
What happened to this ppa?

sudo add-apt-repository ppa:**vlc**/ppa 

> Error reading [https://launchpad.net/api/beta/~vlc/+archive/ppa:](https://launchpad.net/api/beta/~vlc/+archive/ppa:) HTTP Error 404: Not Found


---

### Post by loell on 2010-04-13
> **Ric_NYC said:**
> What happened to this ppa?

sudo add-apt-repository ppa:**vlc**/ppa

that's because it's a none existent PPA URL,

you can search for PPA VLC builds or literally any PPA packages at [https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas) 

you can then add the correct PPA url with your desired packages.

---

