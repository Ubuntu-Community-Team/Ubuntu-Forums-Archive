---
title: "Debian users come here!!!"
date: 2010-04-05
forum: The Cafe
---

### Post by Laxman_prodigy on 2010-04-05
Hi.

After using Ubuntu for awhile now, I thought of trying Debian lenny.

However, I think Debian has not much loyal followings(correct me if I am wrong) in their forums. And I cannot find any books written on Debian while Amazon is filled with Ubuntu books.

After installing the first thing I noticed was the good speed of Debian. I am very itching to go beyond but I can't find good stickies in the forums and no books as I see it.

I cannot make my 4.1 Creative box working yet through my Soundblaster. How do I do that in lenny?

Can I compile any latest software in lenny?

Please suggest me and give me good directions on my Debian journey.:lolflag:

---

### Post by cariboo on 2010-04-05
There are lots of Debian resources on line. Have a look [here]("http://www.debian.org/doc/"). Ubuntu is based on Debian, so almost all commands work in both distributions.

---

### Post by koenn on 2010-04-05
> **Laxman_prodigy said:**
> 
However, I think Debian has not much loyal followings(correct me if I am wrong) in their forums. And I cannot find any books written on Debian while Amazon is filled with Ubuntu books.

Debian has a very large community - they just don't have the noisy forums Ubuntu has. They traditionally use mailing lists rather than forums. 

[http://www.debian.org/doc/FAQ/ch-support.en.html#s-onlineresources](http://www.debian.org/doc/FAQ/ch-support.en.html#s-onlineresources)

That, and they have all that online documentation cariboo907 pointed you to, so there's far less need for books.

---

### Post by NightwishFan on 2010-04-05
Check the link in my sig for some Debian tutorials. I am working with the site owner to expand our size of tutorials and forums. So for the discussion forums only have 3 members, but feel free to join!

---

### Post by Psumi on 2010-04-05
There is also [http://forums.debian.net](http://forums.debian.net)

---

### Post by Zoot7 on 2010-04-05
> **Laxman_prodigy said:**
> Hi.

After using Ubuntu for awhile now, I thought of trying Debian lenny.

However, I think Debian has not much loyal followings(correct me if I am wrong) in their forums. And I cannot find any books written on Debian while Amazon is filled with Ubuntu books.

After installing the first thing I noticed was the good speed of Debian. I am very itching to go beyond but I can't find good stickies in the forums and no books as I see it.

I cannot make my 4.1 Creative box working yet through my Soundblaster. How do I do that in lenny?

Can I compile any latest software in lenny?

Please suggest me and give me good directions on my Debian journey.:lolflag:
I suggest you read the Debian FAQ:
[http://www.debian.org/doc/manuals/debian-faq/](http://www.debian.org/doc/manuals/debian-faq/)
There's a whole waft of useful information there about pretty much all the topics anyone will be concerned about.

As for compiling more up to date software on Lenny, the following thread is a great guide on the various stages you should take when compiling stuff from source:
[http://forums.debian.net/viewtopic.php?f=16&t=38976](http://forums.debian.net/viewtopic.php?f=16&t=38976)
Leading on from that, what's also well worth a read when it comes to building .debs from source is the Debian New Maintainters guide, it's probably a lot more information than you'll need, but it gives a very good description of what's involved.
[http://www.debian.org/doc/maint-guide/ch-start.en.html](http://www.debian.org/doc/maint-guide/ch-start.en.html)

Lastly, for the soundblaster, if it's an X-Fi, you'll need a version of Alsa greater than or equal to 1.0.21, or a kernel version of 2.6.32 or newer. Lenny has neither (Kernel version is 2.6.26). I myself am running an X-Fi Xtremegamer with Debian Lenny with the 2.6.27.45 kernel and Alsa 1.0.22, both of which I compiled myself.

---

### Post by Laxman_prodigy on 2010-04-05
> **Zoot7 said:**
> I suggest you read the Debian FAQ:
[http://www.debian.org/doc/manuals/debian-faq/](http://www.debian.org/doc/manuals/debian-faq/)
There's a whole waft of useful information there about pretty much all the topics anyone will be concerned about.

As for compiling more up to date software on Lenny, the following thread is a great guide on the various stages you should take when compiling stuff from source:
[http://forums.debian.net/viewtopic.php?f=16&t=38976](http://forums.debian.net/viewtopic.php?f=16&t=38976)
Leading on from that, what's also well worth a read when it comes to building .debs from source is the Debian New Maintainters guide, it's probably a lot more information than you'll need, but it gives a very good description of what's involved.
[http://www.debian.org/doc/maint-guide/ch-start.en.html](http://www.debian.org/doc/maint-guide/ch-start.en.html)

Lastly, for the soundblaster, if it's an X-Fi, you'll need a version of Alsa greater that or equal to 1.0.21, or a kernel version of 2.6.32 or newer. Lenny has neither (Kernel version is 2.6.26). I myself am running an X-Fi Xtremegamer with Debian Lenny with the 2.6.27.45 kernel and Alsa 1.0.22, both of which I compiled myself.

After netinstall of lenny with minimum gnome-core packages, I have no sound. Now, I have 4.1 speakers. How should I configure the sound?

---

### Post by Zoot7 on 2010-04-05
> **Laxman_prodigy said:**
> After netinstall of lenny with minimum gnome-core packages, I have no sound. Now, I have 4.1 speakers. How should I configure the sound?
Does the command **aplay -l** throw up anything of interest?

I'm guessing you've an X-Fi, so as I said you're going to need either a newer version of Alsa or a newer kernel. I suppose the easiest thing for you to do is to use the Lenny Backports repo to install the 2.6.32 kernel (which was recently added).

For instructions on using the backports repo have a look here:
```
http://www.backports.org/dokuwiki/doku.php?id=instructions
```

---

### Post by wojox on 2010-04-05
Here's what I use [Debian Reference]("http://www.debian.org/doc/manuals/reference/")

---

### Post by Psumi on 2010-04-05
> **Laxman_prodigy said:**
> After netinstall of lenny with minimum gnome-core packages, I have no sound. Now, I have 4.1 speakers. How should I configure the sound?

apt-get install alsa-utils

then in terminal, type alsamixer and hit enter, unmute everything you think is what you use.

Also: Device volume should be lower than master volume, otherwise you'll get noise.

---

