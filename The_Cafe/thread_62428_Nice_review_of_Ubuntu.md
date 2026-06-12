---
title: "Nice review of Ubuntu"
date: 2005-09-04
forum: The Cafe
---

### Post by front243 on 2005-09-04
And he talks good about this forum as well:

[Ubuntu Review](http://www.flexbeta.net/main/articles.php?action=show&id=108&perpage=1&pagenum=1)

---

### Post by Knome_fan on 2005-09-04
I agree, nice review, though a few things weren't really, ehm, accurate, to say the least, for example hist take on sudo.

But overall, very nice.  :grin:

---

### Post by YourSurrogateGod on 2005-09-04
I like how he criticized the OS constructively, that can help developers in the future. Always good to have constructive criticism.

---

### Post by xequence on 2005-09-04
It is quite good, but some parts arent true...

> While the default applications that come with the distribution are somewhat minimal 

Windows gives you... Notepad, wordpad, paint, solitaire and some system utilities. Ubuntu gives you a full office suite, a professional grade art program, etc. Almost everything you would need to quickly start doing whatever you want to do.

> (after all, the distribution's target is the new Linux user market,) 

I didnt know that... I always considered it an all purpose everything but a server type of OS.

> Still, Human is anything but a nice color schemes 

Looks alot better then the flashing ad on the side of that page telling me I won a tv ;)

> The system itself is fast and responsive. I've run it on everything from a Celeron 667 to an Athlon XP 1800+, and it ran nicely on both. However, GNOME does require a bit of RAM, so if you don't have at least 256 megabytes you might want to consider another window manager, like xfce. As it is, though, everything seemed to run fine.  

Yep, gnome is slow in 192 MB RAM ;) XFCE is fast but not as customizable...

> This is because Ubuntu comes set with no root account—in order to do things as root, you have to use sudo. The problem with sudo, however, is that it uses the current user's password, 

Ubuntu has a root account... Just its not enabled to be logged in to. Ubuntu guide tells you how to change that. Not everyone can sudo as far as I know... Root sets permissions.

But its good that person said good things ;) And is trying linux.

---

### Post by sapo on 2005-09-04
and thats the best part, talking about us  :grin: 

> Ubuntu has what is, quite possibly, the friendliest Linux user community of any distribution I've ever tried. Their forums are home to thousands of users, many of them completely new to Linux. Any question you could possibly have has probably already been asked and answered there.

Another neat thing about their forums is the absolutely enormous HOWTO forum, where people post methods on doing everything from enabling composting to installing XFCE. If you've ever had a problem doing something, you might find your answer in the HOWTO forum.

---

### Post by matthew on 2005-09-04
Nice article. For those wondering, it is possible to make user accounts without superuser (su, sudo) abilities fairly easily...even a gui for it in System-Administration->Users_and_Groups. I didn't see an email address to tell the author that, or to thank him for his complements. Hopefully he will see this.

---

### Post by YourSurrogateGod on 2005-09-04
[QUOTE=sapo]and thats the best part, talking about us  :grin:[/QUOTE]
I wonder where he got the idea that we're friendly ;) ?

[size=1]/i keed, i keed...[/size]

---

### Post by npaladin2000 on 2005-09-04
> **xequence]Windows gives you... Notepad, wordpad, paint, solitaire and some system utilities. Ubuntu gives you a full office suite, a professional grade art program, etc. Almost everything you would need to quickly start doing whatever you want to do.[/QUOTE]

Compared to most Linux distributions, it's true that Ubuntu comes with a limited software selection.  That's one of the stated goals...don't get all defensive.  said:**
> Yep, gnome is slow in 192 MB RAM ;) XFCE is fast but not as customizable...

Actually XFCE is pretty good, there's just not as much "stuff" for it.  Luckily, the standard these days is at least 256 megs. ;)

And actually, I agree with his take on the Human theme...I don't like it either.  Nor do I like WinXP's default theme. Human started off OK with me, but didn't grow on me at all...I got tired of all the brown everywhere, and realized I like more life-filled colors like blue or green.  I will say one thing though, at least the brown is subdued, unlike WinXP's garishness by default.  Garish is bad. But my favorite is Fedora's default theme.

And after seeing the brown-with-raw-sewage water all over New Orleans on the news, I'm even less fond of brown. ;)  I'd like to see Ubuntu go to a nice lush green.

Oh, he also makes a good point about user access levels. The way Ubuntu is set up, everyone has superuser access through sudo.  It might be desirable to have the ability to create USER-level users that would not be in the sudoers group (Like, say, when dad wants to create an account for his kids, but don't want the kids messing around installing apps and all).

---

### Post by poofyhairguy on 2005-09-04
[QUOTE=npaladin2000]
Oh, he also makes a good point about user access levels. The way Ubuntu is set up, everyone has superuser access through sudo.[/QUOTE]

Just like Apple. This is Apple's idea, but I have never seen anyone go on about it in a Tiger review.

---

### Post by npaladin2000 on 2005-09-05
[QUOTE=poofyhairguy]Just like Apple. This is Apple's idea, but I have never seen anyone go on about it in a Tiger review.[/QUOTE]

Making everyone an admin by default is such a (normally) bad idea even Microsoft doesn't do it. The kings of insecure. ;)

and incidentally, I've only seen one Tiger review...PC Mag I believe.  And I'm hoping they fix it there too.  Right now Ubuntu is the ONLY Linux distro that makes every user an admin user by default; most others create an actual root user, but make the "user" users actual "user" users...you have to manually make them sudoers.

Now, I know there's a way in Ubuntu to make sure a user is not a sudoer when it's created.  But it's a pain, and involves modifying the /etc/sudoers file, rather than just making sure they're not in the "sudo" or "wheel" group.  That makes it HARD (well, a pain at least) to make a user with limited access, which isn't exactly a good thing for security purposes.

---

