---
title: "mail server help"
date: 2007-02-22
forum: Server Platforms
---

### Post by compudude86 on 2007-02-22
im trying to get a mail server set up on my ubuntu box, and its become extremely frustrating. i have to use sendmail, because its the only one i can get to work with my DSL. ive tried to install and configure several other imap-pop3 servers for the receiving end, such as dovecot and courier for example. currently i have courier installed from apt-get, and i dont know how to configure it to authenticate. i also want to set it up to spamfilter and virus scan with clamAV. ive heard something about it using "maildir", but i have no clue what that it. any help would be appreciated.

---

### Post by Fíona on 2007-02-22
Have you tried the many good how to's that are available. I'm in the process of setting up a mail server and admit it's not that simple, there's a lot to learn.

Here are some links to how to's; sorry if they're already known to you.



[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

[https://help.ubuntu.com/ubuntu/serverguide/C/email-services.html](https://help.ubuntu.com/ubuntu/serverguide/C/email-services.html)

[http://postfix.wiki.xs4all.nl/index.php?title=Virtual_Users_and_Domains_with_Courier-IMAP_and_MySQL](http://postfix.wiki.xs4all.nl/index.php?title=Virtual_Users_and_Domains_with_Courier-IMAP_and_MySQL)

[http://www.howtoforge.com/taxonomy_menu/1/78](http://www.howtoforge.com/taxonomy_menu/1/78)

Good luck and a lot of patience is a help!

---

### Post by compudude86 on 2007-02-22
no, i have not seen that. my one problem is that i use apt-get for a lot of my mail programs, and the howtos are for source... thanks for the links

---

### Post by Fíona on 2007-02-23
I'm not sure about what you mean. 
I also use (only use) apt-get install for everything!

---

### Post by compudude86 on 2007-02-23
im sorry, i shouldve been more clear, i was talking about the tutorials ive seen online before, they all ask you to build from source, i didnt realize these tutorials were apt-get friendly

---

### Post by Fíona on 2007-02-23
I hope the other howto's are more helpful, even if you do see instructions to compile from binary, try apt-get install anyway, you never know...

---

### Post by compudude86 on 2007-02-25
well, i guess ill have to try it another time, i found deep*o*fix, and ive already launched two servers. it seems to have everything rolled into one simple install-and-go package. theres another post on it(The groupware server we were waiting for (integrated LDAP auth anyone?)), id definitely give it a try, its worked great for me :)

---

