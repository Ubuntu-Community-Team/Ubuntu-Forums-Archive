---
title: "Creating an offline repository?"
date: 2005-07-05
forum: Repositories &amp; Backports
---

### Post by Aragorn992 on 2005-07-05
I do not have the internet at my PC where Ubuntu is installed and would like to have updates accessible. Is there a way to do this?

Could I possibly download the entire repository to a CD somewhow and then point the update manager to this CD when I get back to my PC?

Im very new to this so please use simple terms...

Thanks.

---

### Post by UbuWu on 2005-07-05
Almost all of the updates are security updates. If you don't have internet access at your pc, most of these security issues will not affect you. So I don't think it is worth the efford.

---

### Post by GnomicGhost on 2005-07-07
[QUOTE=UbuWu]Almost all of the updates are security updates. If you don't have internet access at your pc, most of these security issues will not affect you. So I don't think it is worth the efford.[/QUOTE]
Not true!
I am in the same boat at times going between Uni and home, my computer is not able to be always connected to the internet but I still want to get things like codecs, players, games, software etc.  Why do you need to be connected to the internet to be 'worth the effort'...?!!!!

And yes it is possible to have a local repository but I don't remember where I saw how to do it.

---

### Post by RaymondQE on 2005-07-07
Here's the link to the offline repository discussion.

[http://www.ubuntuforums.org/showthread.php?t=7455&highlight=local+repository](http://www.ubuntuforums.org/showthread.php?t=7455&highlight=local+repository)

---

### Post by Aragorn992 on 2005-07-07
Awesome thanks!

---

### Post by UbuWu on 2005-07-11
[QUOTE=GnomicGhost] Why do you need to be connected to the internet to be 'worth the effort'...?!!!!
[/QUOTE]

I was only referring to the updates as that was the original question. Of course it can be useful to install new programs.

---

### Post by ozzie123 on 2005-07-15
Thanks a bunch! I also needed this.

---

### Post by hearty on 2008-02-11
I had a machine which was connected to Internet (broadband) 
I did following to gather all the packages which are being installed on it.

```
cp /var/log/dpkg* /tmp
cd /tmp
gunzip dpkg.log*.gz
apt-get install -d `cat dpkg.log |grep installed|grep -v half-installed|grep -v not-installed |cut -d' ' -f 5`
```

Copied /var/cache/apt to remote machine ( which has poor internet link )

moved to that folder and then

```
dpkg -i * 
```

It did many changes to system, like it installed many packages which were missing in default install CD of ubunut/dapper. 

But some thing went wrong in the end. 


What must have been the problem?

---

### Post by vildanovak on 2010-01-28
I really hate ubuntu today.
I wanted to do an offline repository for a computer I want to install plenty of software. It is different edition than I have on my laptop which is online. There's absolutely no way to just download an ubuntu release to a shared diskspace, if you don't have the same release on your computer! And with toying and trying to get the debmirror working, I realized there's a 3 years old bug with gpgv not recognizing the keys which are directly from ubuntu.!
Only thing I caused after trying to solve this for 5 hours was to brake the old ubuntu installation on the laptop, where synaptic obviously stopped working. Great.

It could be so simple, I just want to download all the .deb files! why tf is there a special tool for that which is not working at all???

---

### Post by Trespasser on 2010-01-28
If you haven't deleted all the updates that the computer with internet access has taken then try AptOnCD. I use it all the time. I have every update since Karmic was released plus packages I've downloaded and installed (like vlc, wine, etc.) nicely tucked away in an iso file. You can save it, like I do, or burn it to a CD (better yet a CDRW). With it you can do a fresh install and update quite fast.

Later...

---

### Post by PCA on 2010-01-29
The APTonCD doesn't seem to work for me. It crashes after reaching about 29% without displaying any list. But I have found a good way to build a local repository. I don't remember the link but it's called " Building a trusted local repository' here in the fourm. That really works. Check it out:D

---

