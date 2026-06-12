---
title: "how can I manage spamassassin using  dovecot+postfix+mysql"
date: 2009-05-29
forum: Server Platforms
---

### Post by kustomjs on 2009-05-29
Hi Guys
I need to know how to manage spamassassin using  dovecot+postfix+mysql is there a GUI or something I can use to manage it?

---

### Post by Michael R on 2009-05-29
Webmin might do what you want. I'm not sure as I'm still doing this myself.

---

### Post by kustomjs on 2009-05-29
see I already have webmin but I dont know to configure it for spamassassin.

---

### Post by LepeKaname on 2009-05-29
Do you mean like a GUI? I'm not sure there is one..., but you can read some links about how to tune spamassassin manually, here is one:

[http://linuxgazette.net/105/youngman.html](http://linuxgazette.net/105/youngman.html)

---

### Post by kustomjs on 2009-05-29
there is a couple out there for gui but how do you configure them.

---

### Post by kustomjs on 2009-05-31
anybody?

---

### Post by windependence on 2009-05-31
Well, I would just suggest Zimbra since it has all this stuff integrated into it and controlled by the web GUI, but I know you have already seen it and obviously there was a reason you didn't want to go that route. If you do decide to try it, I would be glad to help you. I know it's not 100% GPL, but if you're a purist, I can't help you. It does integrate postfix, spamassassin, clamav, LDAP, and some more I can't remember, but here is the screenshot gallery to take a look at. It's really a nice product for no cost.

[http://www.zimbra.com/products/screenshots.html](http://www.zimbra.com/products/screenshots.html)

-Tim

---

### Post by kustomjs on 2009-05-31
I already have a working email server and I just need to figure out away to configure spamassassin on it. I dont need to replace it with something else that is ready have it in there. I just need to know how to configure it into already working email server.

---

### Post by kustomjs on 2009-05-31
over 75 views and still no help?

---

### Post by kustomjs on 2009-06-05
I figured by now I would get help after 134 views.

---

### Post by kustomjs on 2009-06-08
can somebody really help me out here?

---

### Post by drave99 on 2009-06-08
there is no GUI , you have to do it all by hand on the individual apps. 
major pain the a@#, that may be worth it if your an ISP with thousand of clients, but not for small places. 
there are integrated servers on linux,i think
but ive been using(cough)windows

---

### Post by noway2 on 2009-06-08
For general email server management of a virtual host database using MySQL, postfixadmin works quite well.

You keep asking about spamassassin, and quite honestly, I don't really understand your problem.  What exactly do you mean by configure it?

Spamassassin is relatively straight forward and if you really have gotten all the other components, e.g. postfix, dovecot, mysql, etc working you should have little trouble with it.

The key to using Spamassassin to use Amavis.  Amavis ties Clamav and Spamassassin together.  Once you have these installed, you set a line in master.cf as the first item, redirecting incoming and outgoing mail to a different port where amavis picks it and resends it pack via the smtp port once it passes clean.

Once installed, the setup and configuration for spamassasin is minimal and it automatically does its thing.  Once you have a collection of about 200 spam and 200 ham mails, you can tell it to scan them and learn the difference which will improve the functionality (I haven't gotten there yet, but this is what I read).  The other thing you can do is filter through some RBLs, real time black lists.

For greater detail on installing and using amavis, try one of the many howtos on this subject.  For proof that it is working, you can send yourself a test string that will flag as spam.  Similarly you can send yourself a copy of eicar.com and prove that your anti virus is working.  As a note, Amavis has a built in virus checker, but it isn't as powerful as Clamav.

Lastly, I suggest using sieve to filter any mail with the spam tag to a directory where it will get saved.  This way once you have accumulated enough of it, you can easily use it to teach spamassassin to improve its filtering.

---

### Post by kustomjs on 2009-06-08
hey drave99 there is GUI for  spamassassin look on there site under wiki.

pretty much what I want to do is put spamassassin under GUI or something so the users can manage the spam that is what I looking for.

also I want to know how can I put spamassassin under mysql.

> **drave99 said:**
> there is no GUI , you have to do it all by hand on the individual apps. 
major pain the a@#, that may be worth it if your an ISP with thousand of clients, but not for small places. 
there are integrated servers on linux,i think
but ive been using(cough)windows

---

