---
title: "email server... Which to use?"
date: 2008-07-01
forum: Server Platforms
---

### Post by chuck jessup on 2008-07-01
postfix, sendmail, qmail and i hear tell of others, personally which would be the best to install if i want to set up webmail... such as mail.domain.com to a login screen and to the inbox (kind of like yahoo mail and hotmail...) it would be nice... do these other mail servers do this? if so which are the easiest to set up and add and manage users. any advice would be wonderful! Thanks In aAdvance :D

Jesse Fender

---

### Post by cdenley on 2008-07-01
I like zimbra. It has a bunch of common linux server applications bundled with it like postfix and apache. It is an entire collaboration suite, very easy to install, configure, and maintain. It is not officially supported for hardy yet, but I haven't had any problems with the community build.

[https://sourceforge.net/project/showfiles.php?group_id=224243](https://sourceforge.net/project/showfiles.php?group_id=224243)

I think everything you listed is an MTA, which is just for delivering mail. It's only part of the solution you're looking for.

---

### Post by hyper_ch on 2008-07-01
postfix :)

---

### Post by windependence on 2008-07-02
> **cdenley said:**
> I like zimbra. It has a bunch of common linux server applications bundled with it like postfix and apache. It is an entire collaboration suite, very easy to install, configure, and maintain. It is not officially supported for hardy yet, but I haven't had any problems with the community build.

[https://sourceforge.net/project/showfiles.php?group_id=224243](https://sourceforge.net/project/showfiles.php?group_id=224243)

I think everything you listed is an MTA, which is just for delivering mail. It's only part of the solution you're looking for.

I second this, and here's a great tutorial on getting it going:

[http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu](http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu)

-Tim

---

### Post by chuck jessup on 2008-07-02
> **cdenley said:**
> I think everything you listed is an MTA, which is just for delivering mail. It's only part of the solution you're looking for.

huh? what then should i look for in the whole solution?

BTW thanks for the advice... i will look into them when i get back from Montana

Jesse Fender

---

### Post by cdenley on 2008-07-02
> **chuck jessup said:**
> huh? what then should i look for in the whole solution?

Zimbra! You can also look at citadel, but I didn't like it.

---

### Post by amenszer on 2008-07-02
I use courier+postfix and squirrelmail as the webmail interface.
Squirrelmail is not as fancy as some of the others, but its simple to set up and easy to use...which is a more important need than advanced functionality in my particular setting.

---

### Post by hyper_ch on 2008-07-02
I love squirrelmail... it's fast and it works... I have just added 2 or 3 addons for it ;)

---

### Post by Dr Small on 2008-07-02
> **hyper_ch said:**
> postfix :)
+1 for Postfix.
And I am using SqWebmail for webmail.

---

### Post by hyper_ch on 2008-07-03
postfix, courier-imap, procmail and squirrelmail ;)

---

### Post by mrpeenut24 on 2008-07-03
+1 to postfix, courier, squirrelmail

---

### Post by MJN on 2008-07-03
I also endorse the split solution (e.g. Postfix/Dovecot/SquirrelMail/SpamAssassin/etc).

Sure, it's a lot more to learn and it doesn't all just pop out of the box together 'working' but it makes for a far better system given that each product is tailored to its own specific job well and, if integrated together properly can give you a much more effective, flexible and rebust solution.

I think it depends on exactly what you want to achieve, ranging from a solution that 'just works' to something you want to learn about and tweak/expand over time. Whichever way you go you won't go too far wrong as all the suggestions have got their own loyal followings.

Mathew

---

### Post by Hazardr on 2008-07-03
Kolab Rules

---

### Post by coutts99 on 2008-07-03
Postfix, courier-imap, spamassassin, dspam, clamav, roundcube

---

### Post by cdenley on 2008-07-03
> **coutts99 said:**
> Postfix, courier-imap, spamassassin, dspam, clamav, roundcube

This is what I meant when I said postfix is just part of the solution. Either install all the services you need and configure them to work together correctly, or install an all-in-one software suite such as zimbra.

---

### Post by chuck jessup on 2008-07-11
well due to the local fires i havent really been able to do much as i have been evac'ed - so you guys are sugesting postfix and courrier, and squirrel(sp) for my mail server? are these installible/ easy to get on ubuntu server (i have debating whether to move on to opensuse or sitcking ubuntu out a little longer... i have fellows at work who run suse servers and hate that ubuntu is locked down... 

and i will take a look at the mail server when the evac is lifted in town... (I HATE FIRE!)
Thank You All for the Imput

Jesse Fender

---

### Post by chuck jessup on 2008-07-14
> **windependence said:**
> I second this, and here's a great tutorial on getting it going:

[http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu](http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu)

-Tim

-- just to let you know zimbra is supporting an older version of the ubuntu server.... will this be a problem to install it on 8.04?

Jesse Fender

---

### Post by windependence on 2008-07-14
I have not tried it on 8.04, but I do have one running on 7.10.

FYI, just because a version is out doesn't mean it's the "best" or even "stable". 6.06 or 6.10 is still a very usable system and after it's installed and you do the updates, it's really as functional as the new version, one nice benefit of a debian based distro.

-Tim

---

### Post by cdenley on 2008-07-15
> **chuck jessup said:**
> -- just to let you know zimbra is supporting an older version of the ubuntu server.... will this be a problem to install it on 8.04?

Not a problem at all. I linked to the community builds for ubuntu 8.04. That's what I'm running right now. It's not officially supported, but I don't think you get any support with the open-source edition anyway.

[https://sourceforge.net/project/showfiles.php?group_id=224243](https://sourceforge.net/project/showfiles.php?group_id=224243)

If you are going to buy the network edition, then I would use a supported distribution like ubuntu 6.06 or debian etch 32-bit.

> 
FYI, just because a version is out doesn't mean it's the "best" or even "stable". 6.06 or 6.10 is still a very usable system and after it's installed and you do the updates, it's really as functional as the new version, one nice benefit of a debian based distro.

Newer versions will be supported longer and can support newer hardware.

---

