---
title: "Splashtop Streamer is available for 12.04"
date: 2012-11-28
forum: The Cafe
---

### Post by donniezazen on 2012-11-28
Hello,

Splashtop is available for Ubuntu 12.04.

[http://www.splashtop.com/streamer/linux](http://www.splashtop.com/streamer/linux)

Has anyone tried it? It is not available for 12.10 yet. [libx264-120]("http://packages.ubuntu.com/precise/libx264-120") is required to run it on 12.10 which is not available on 12.10.

Thanks.

UPDATE:- Runs well on 12.10 after i installed libx264-120. Resolution is not perfect but I didn't see any speed lag.

---

### Post by CptanPanic on 2012-11-28
12.10 has libx264-123, I wonder what the difference is?

---

### Post by Holmen on 2012-11-28
Yeah, I would also very much like to know. I want to install it now and give it a go!

Update: I just installed the previous versionof libx264 and am know writing this frm my android tb via my laptop, so it works great!

---

### Post by donniezazen on 2012-11-28
> **Holmen said:**
> Yeah, I would also very much like to know. I want to install it now and give it a go!

Update: I just installed the previous versionof libx264 and am know writing this frm my android tb via my laptop, so it works great!

How is your resolution? Mine is chopped on both laptop and tablet in landscape mode. It would be great if they had it running like a background service, so, you never have to worry about it.

---

### Post by deeemster on 2012-11-28
What am I doing wrong on installation?  I'm running
./configure
make
sudo make install
everything seems fine (maybe I browsed past a error??)
How do I run it?  I see nothing in the menus and can't find a splash* on the system.  Also don't have the directory .config/splasthtop*

I do have the latest libx264-120

---

### Post by donniezazen on 2012-11-29
> **deeemster said:**
> What am I doing wrong on installation?  I'm running
./configure
make
sudo make install
everything seems fine (maybe I browsed past a error??)
How do I run it?  I see nothing in the menus and can't find a splash* on the system.  Also don't have the directory .config/splasthtop*

I do have the latest libx264-120

Why are you building it yourself? Are you not on Ubuntu? There are debs available for 12.04 32 and 64 bit systems. It is also available in [12.04 Ubuntu Software Center]("https://apps.ubuntu.com/cat/applications/splashtop-streamer/").

---

### Post by deeemster on 2012-11-29
> **donniezazen said:**
> Why are you building it yourself? Are you not on Ubuntu? There are debs available for 12.04 32 and 64 bit systems. It is also available in [12.04 Ubuntu Software Center]("https://apps.ubuntu.com/cat/applications/splashtop-streamer/").

Well shoot I didn't even try the software center.  I downloaded from the site.  Idiot sometimes, thanks.

---

### Post by Newuser007 on 2013-01-11
This may be a noob question but how do you install the previous version of libx264-210??

---

### Post by donniezazen on 2013-01-11
> **Newuser007 said:**
> This may be a noob question but how do you install the previous version of libx264-210??

Just download the package and double click. Ubuntu Software Center or gdebi will install in automatically.

---

### Post by dannyboy79 on 2013-01-11
just by it's name I thought it was a streaming type software where it would stream certain video out audio input to sites like twitch.tv, justin.tv, or ustream. But apparently it doesn't do that. Darn, I am looking for a linux app thats something like xsplit or wirecast.

---

