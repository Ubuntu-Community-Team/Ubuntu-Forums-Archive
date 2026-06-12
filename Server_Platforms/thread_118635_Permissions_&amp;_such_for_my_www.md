---
title: "Permissions &amp; such for my /www"
date: 2006-01-17
forum: Server Platforms
---

### Post by ixus_123 on 2006-01-17
Hello :)

After much hair pulling & self doubt, I have finally got apache, php4, mysql, & wordpress (blogging software) intalled on my Ubuntu machine

It works but I think my permissions are all over the place but don't really know what they should be or how to fix.

I have one user account on my system called "admin" - wordpress was untared to admin's home floder & then moved to /www with
```
sudo mv /home/admin/wordpress /var/www
```

I think that even though I moved it, it's still owned by admin as I can save themes etc in there.  Is this safe or should it be changed to something like chmod 666 / 777 / 755 ? (don't know the difference between all of these btw).

I tried to upload pictures to my blog & it moans that /uploads is not writable by server - would that be apache or mysql?  Would changing everything to chmod 666 sort this??

How have you set your system up, what's typical?

Or should I be making a group ( I don't know how to that either) & doing thngs that sort of way.

Sorrry for being such a beginner & needing so much hand-holding.  I don't mind RTFM if someone can point me to something that lays it out in begginer terms.  I don't really get it reding from the consoles man feature & online documention just seems to overwhelm me with the depth - MySQL documentation is a good example of this.

Thanks

---

### Post by darth_vector on 2006-01-18
you can change the owner of the files by doing something like[code:]chown -r root /var/www[/code]

there is an easier way to change permissions (at least i think so) than using the numbercs.

chmod user_def change_in_permissions

where userdef is one of a (all users), o (owner), g (group of the owner), and change in permissions is something like +w (to allow writing), -r (to dissalow reading), +rx (to allow writting and executing) and so on.

check out the manpage for chmod.

---

### Post by derelict on 2006-01-19
[QUOTE=ixus_123]Hello :)
chmod 666 / 777 / 755 ? (don't know the difference between all of these btw).I don't mind RTFM if someone can point me to something that lays it out in begginer terms.[/QUOTE]

Check this out: [http://catcode.com/teachmod/](http://catcode.com/teachmod/)
As to the numbers, there's an easier way, like vector said:
"u" means "user" (the file owner), "g" means "group", "o" means "others" (everybody else). So "chmod u+r myFile" gives the owner permission to read myFile and "chmod u-r myFile" removes that permission. "chmod g+w myFile" gives the group permission to write to that file. "chmod o+x myFile" gives everybody (others) permission to execute the file.

---

### Post by LordHunter317 on 2006-01-20
[QUOTE=ixus_123]It works but I think my permissions are all over the place but don't really know what they should be or how to fix.[/quote]You shouldn't be playing with them in the first place and for most server installs, you never have to.

> I think that even though I moved it, it's still owned by admin as I can save themes etc in there.That's fine.  As long as www-data (the Apache user) can *read* the files, you're OK.  It doesnt' need ownership.  In fact, whoever will be changing the files should own them.

>   Is this safe or should it be changed to something like chmod 666 / 777 / 755 ? (don't know the difference between all of these btw).666 and 777 **are very dangerous.**  Don't ever use them.  If something/one tells you to use them, they are wrong in 99.9% of situations.  Don't follow their advice.

> I tried to upload pictures to my blog & it moans that /uploads is not writable by server - would that be apache or mysql?You need to give that particular directory write access to the www-data user.  I would personally do:```
sudo chgrp www-data uploads
sudo chmod g=rwx
``` to give it access.  You may be able to strip the read bit depending on the application.

> Or should I be making a group ( I don't know how to that either) & doing thngs that sort of way.You could, but unless you need specific ownership or behaviors of the uploaded files, it's unnecessary.

---

### Post by furtivefelon on 2006-01-21
to my experience, 755 is the most common one.. it gives owner full access (read, write, execute), group read and execute, nobody read and execute, is often used in public folders where other people could access with a browser..

---

### Post by ixus_123 on 2006-01-24
Thanks very much for your help guys :)

Sorry I've been so long to reply myself.  Currently the server computer is running without a monitor & due to a tidyup, my network cable woudn't reach my main PC (bought a longer one now).

I've managed to get hold of a Linux+ certification book that I'm hoping will help me better understand all of things.  Flicking through it, it would seem that I know most of the stuff through prctical experience but there are plenty of gaping holes I need to fill.

Thank-you again for your time & efforts :)

---

