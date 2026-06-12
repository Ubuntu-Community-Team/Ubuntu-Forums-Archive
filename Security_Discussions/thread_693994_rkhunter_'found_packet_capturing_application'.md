---
title: "rkhunter 'found packet capturing application'"
date: 2008-02-11
forum: Security Discussions
---

### Post by Richardinho on 2008-02-11
hi guys,

I was looking in /var/mail for the first time ever and I noticed various mails going back to September (!)
They included a subject of 'rkhunter Daily run' and included the message 'Warning! found packed capturing application please check the log file.
The files it flagged up were /dev/.static(directory)
/dev/.udev (directory) and /dev/.initramfs (directory)

I ran rkhunter from the command line and it flaged up those exact same directorys as 'Please inspect'.

I haven't noticed anything suspicious in my normal use and I have made various card transactions on my system over the net, so naturally I'm a bit concerned.

Any help appreciated.

Rich.

---

### Post by cgr1fatboyslim on 2008-02-12
Hi Rich,


I noticed that also in my box,even with a fresh install(ubuntu710)...and the latest definitions or updates for rkhunter...i get that same hidden files except now it added another hidden dir...."/dev/.tmp-2-0:block special(2/0)"

Those 3 hidden dir's that you mentioned,i have noticed since earlier versions of ubuntu...just cannt remenber which versions they were....
 
Frankly I'm as worried as you are,I hope someone can post a solution to our problem...

:(

---

### Post by k_grdn on 2008-02-12
Hi,

These are comon in ubuntu and can be safely ignored to stop the messages, uncomment:


#ALLOWHIDDENDIR=/dev/.udev


In /etc/rkhunter.conf

Regards,

k_grdn

---

### Post by Richardinho on 2008-02-12
Thanks K-grnd
That's basically all that I want to hear! 
I came to linux mainly because when I had Window ME, I suffered a serious security breach where basically my bank account was robbed of several hundred pounds. From what I have read, a rootkit is the most likely cause of such attacks. Happily my bank refunded this without any questions (although their apparent total disinterest in trying to pursue the perpetrators of this was somewhat disconcerting!)

I understood that linux is far more secure and less vulnerable to such attacks so I would be disappointed if it turned out that it wasn't!

---

