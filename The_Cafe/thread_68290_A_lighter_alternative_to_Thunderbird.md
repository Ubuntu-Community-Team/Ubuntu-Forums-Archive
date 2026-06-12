---
title: "A lighter alternative to Thunderbird"
date: 2005-09-22
forum: The Cafe
---

### Post by darthsabbath on 2005-09-22
Hi, all... I posted this in the Support section, and it seems to have gotten lost in the shuffle... I probably should've posted here anyway, as it's not so much a support question as it is an opinion/discussion question.

I've been looking for a fairly light email solution that offers a few necessities I'm having a hard time giving T-bird up for, namely the excellent junk filters and the option of leaving my mail on the server for x days before deleting. I check mail from multiple computers, and as such, it helps to have a local copy of mail saved before it's deleted from my ISP's mailserver. 

As far as the actual email client goes, I really like Pine. I used it at University, and it just feels right.  I've tried Opera mail and Sylpheed-Claws, and they just... no. :D

I'm sure Spamassassin would be the way to go as far as junk filtering goes, and I'm sure I can get it set up myself.

The problem comes to actually moving the mail from my server to the box I'm on. Fetchmail provides an option of leaving the mail on the server, but if I delete it locally, Fetchmail just redownloads it. Does anyone know of an MTA that will simply download once to the local machine, then delete the files on the server after an arbitrary number of days?

Thanks for any help.

Phil

---

### Post by KingBahamut on 2005-09-22
This comes down to a huge argument by most. 

SpamAssassin is relatively easy to setup, I aggree with you there. If you want a light and configureable MTA , Id recommend Exim or Qmail. Unfortunately I havent compiled either of these on Ubuntu yet, So I wouldnt be able to speak on their success. I believe that Exim is on the repos , so that installation would be easy. 

Then you could use pine to your hearts content.

---

### Post by Pixel on 2005-09-22
I'd try out [Columba](http://columba.sourceforge.net/index.php?option=com_content&task=view&id=18&Itemid=77), It's a really nice and lightweight java email client, layout is similar to outlooks and thunderbird, and comes in a variety of different formats for your OS.

---

### Post by topcop on 2005-09-22
if you're after a GTK2 client try Balsa

---

### Post by xlyz on 2005-10-08
check sylpheed or sylpheed-claws

check also bogofilter as spam filter

---

### Post by HungSquirrel on 2005-10-08
[QUOTE=Pixel]I'd try out [Columba](http://columba.sourceforge.net/index.php?option=com_content&task=view&id=18&Itemid=77), It's a really nice and lightweight java email client, layout is similar to outlooks and thunderbird, and comes in a variety of different formats for your OS.[/QUOTE]
It's got nice features and it's portable, but I would hardly call any program whose widgets are rendered by Java 'light'.  ;)

I am with the original author.  I want a light graphical email client with a few nice features such as spam filtering.  Most clients I've used are too light and featureless, or RAM-clogging monstrosities.

---

### Post by darkmatter on 2005-10-08
[***Sylpheed***](http://sylpheed.good-day.net/en/)

is a well established, stable and fast email client.

---

### Post by webwalker1 on 2005-10-09
How about kshowmail? I use it with Xandros and it works great for removing all spam mail before downloading to your email client. Only problem is I don't know how to install it on Ubuntu. I've never installed a tar.gz before.:(  I'm new to Ubuntu, but it's very similar to Xandros, except it's free.:) Maybe they will add it to Adept later on.

---

