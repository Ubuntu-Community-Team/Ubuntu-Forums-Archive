---
title: "Citadel and Squirrelmail not fully getting along"
date: 2009-08-16
forum: Server Platforms
---

### Post by dwasifar on 2009-08-16
As a possible alternative to wrestling with postfix and courier, I'm trying out Citadel for a mail server.  I have it set up and operating, along with Squirrelmail.  Mostly everything works, but I have two problems:

1) Squirrelmail is dog slow to come up, especially the left panel.

2) Squirrelmail users are unable to change a message status to "Read," either manually or by actually reading it.  The option is there, and it seems to be trying to do something, but the message status stays "Unread."

Bonus question for Citadel users - how do you install Webcit themes?  The instructions I have found say to put them in /usr/share/citadel-webcit/static.local, but that doesn't seem to work.

Citadel v7.38
Squirrelmail v1.4.15
32-bit Jaunty

Thanks if anyone can help.

---

### Post by HermanAB on 2009-08-16
Citadel themes:
If you installed with Easy Install, then put the Blue Theme here:
/usr/local/webcit/static.local/
Then restart Webcit

Squirrel is is even more fugly than the default Webcit theme.  If you want something pretty, use Roundcube!

---

### Post by windependence on 2009-08-17
Herman, doesn't Citadel come with it's own web client? I didn't think you had to install anything else for webmail access. Zimbra has it's own rather fully functional web client.

-Tim

---

### Post by dwasifar on 2009-08-17
You mean that for me?  Yes, Citadel does have its own web interface, but it's ugly as a dog's butt, and I'm used to squirrelmail.  :)

---

### Post by HermanAB on 2009-08-17
The Citadel web interface Webcit is good with the Blue Theme:
[http://icoss.net/citadel/blue/blue_citadel_theme.tgz](http://icoss.net/citadel/blue/blue_citadel_theme.tgz)

Citadel dates back to 1985 and the default theme is rather ancient.

---

### Post by dwasifar on 2009-08-17
> **HermanAB said:**
> The Citadel web interface Webcit is good with the Blue Theme:
[http://icoss.net/citadel/blue/blue_citadel_theme.tgz](http://icoss.net/citadel/blue/blue_citadel_theme.tgz)

Citadel dates back to 1985 and the default theme is rather ancient.

I've tried about four times to make that theme work and nothing happens.  I installed Citadel from the repos, so the theme folder is in /usr/share/citadel-webcit.  Putting a static.local folder in that same location does nothing.  Copying the contents of the blue theme to the existing /usr/share/citadel-webcit/static folder results in errors.  I have tried it in /usr/local/webcit, usr/local/share/webcit, no luck.

Also, I don't think the problem with the read/unread status of emails is squirrelmail's problem.  I see them the same way on webcit.

---

### Post by HermanAB on 2009-08-18
Uhmm, are you sure that you restarted Webcit after downloading and unzipping the theme files?

On my system (Redhat) I do:
service citadel restart 
service webcit restart

After which the theme works.

(It is not really necessary to restart citadel, but it illustrates the difference between the two servers.  The one is the mail server, the other one is Apache!)

---

### Post by dwasifar on 2009-08-18
> **HermanAB said:**
> Uhmm, are you sure that you restarted Webcit after downloading and unzipping the theme files?

On my system (Redhat) I do:
service citadel restart 
service webcit restart

After which the theme works.

(It is not really necessary to restart citadel, but it illustrates the difference between the two servers.  The one is the mail server, the other one is Apache!)

I was doing /etc/init.d/webcit restart, but I tried it your way, and lo and behold...

...nothing happened.  :(

It's not really that important, it's just an annoyance.

---

### Post by dwasifar on 2009-08-19
The IMAP speed issue doesn't seem like anyone on the Citadel side much cares to resolve it.  I went looking for other solutions.  After trying out Kolab and having it hose my apache install, I was forced to restore from backups.  

I really didn't need a full groupware server, so I decided to bite the bullet, and spent two days putzing around with postfix and courier to set up a conventional mail server instead of making do with Citadel.  .  So now I've got postfix, courier, mysql, squirrelmail, amavisd, spamassassin, and postgrey all working more or less happily together.

I hope one day Citadel gets a facelift.  Seems like a pretty robust groupware server, but man is it hard to look at.  Feels like Windows 3.1.

Changing thread title to [solved] because I no longer have the problem, and it seems like it was not a squirrelmail issue in the first place.

---

