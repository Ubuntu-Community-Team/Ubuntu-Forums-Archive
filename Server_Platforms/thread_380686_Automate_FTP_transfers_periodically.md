---
title: "Automate FTP transfers periodically"
date: 2007-03-09
forum: Server Platforms
---

### Post by muz1 on 2007-03-09
Hey there.
I was wondering if anyone knew of a really cool way to automatically syncronise folders of files between my local computer and a remote server (running linux of course).
More info:
I do web development and I really want to do daily backups of all of the files and am looking for a way to do it.
Initially I thought a php script mixed with a cron job would be best but I am also thinking of automated ftp packages which I know of none.

So if I can find something that will daily or at set intervals kick something off and syncronise files, that would be such a life saver. This is Ubuntu after all. I am sure there would have to be someway of doing it.

Hope to hear from you soon.
Cheers
muz :)

---

### Post by Nikron on 2007-03-10
This thread show basically tell you how to automate a bash script on a cronjob that uploads/downloads automatically.


Here's the single post with the post info, read its thread for detail..

[http://www.ubuntuforums.org/showpost.php?p=1366778&postcount=9](http://www.ubuntuforums.org/showpost.php?p=1366778&postcount=9)

---

### Post by joselin on 2007-03-10
Have a look at unison.
[http://www.cis.upenn.edu/~bcpierce/unison/]("http://www.cis.upenn.edu/%7Ebcpierce/unison/")

---

### Post by Mr. C. on 2007-03-10
man rsync

---

### Post by nix4me on 2007-03-10
man lftp

lftp can do this easily.


nix4me

---

### Post by MJN on 2007-03-11
Rather than add yet another solution (as you can probably imagine there are many ways to skin this cat) I will second the suggestion of **rsync**. A brilliant tool for this task ( and many more besides) that has a well deserved place in your toolbox.

Some of the key requirements you should be after (which rsync of course provides, as do many of the other suggestions) are:

- Secure - At the very least you want your authentication encrypted, and preferably also your traffic (rsync runs over SSH so no problems there)
- Fast - No point transferring files that don't need transferring (indeed rsync even just transfers the *parts* of files that have changed!)
- Flexible - No point learning the skills for a tool that will only fit this one solution - rsync is very general purpose and, just as importantly, quite ubiquitous in its use so you'll be in good company using it.

Mathew

---

### Post by muz1 on 2007-03-11
WOW!!!!!
Thanks everyone so much for all of the information.
I knew it could be done and I really appreciate the community giving me a hand.
Am going to look at all of these solutions and even if I don't use it, I am sure I will learn alot through the experience.

Thanks again.
muz

---

