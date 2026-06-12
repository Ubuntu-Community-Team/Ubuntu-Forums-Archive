---
title: "[HOWTO] Forward root's mail to your inbox"
date: 2004-12-06
forum: Tutorials
---

### Post by HungSquirrel on 2004-12-06
Occasionally, certain system daemons and utilities will send local Unix mail to root's local email inbox, /var/mail/root .  Well, it doesn't do you much good there!

If you want to read these system messages, you can always do *sudo mutt -f /var/mail/root* if you are familiar with mutt.  However, an easier and more efficient way to check this mail would be to have it forwarded to your user's local inbox, and then read it with your favorite email reader.

**Throughout this HOWTO, replace *username* with your account name.**

First, you need a mailbox, preferably with all of root's old mail already in it.

```
cd /var/mail
sudo cp root username
sudo chown username username
sudo chgrp username mail
```

That creates a mailbox for your username with the appropriate user and group permissions.  The contents of the mailbox are a copy of root's mailbox.

Now, it's time to forward all of root's incoming mail to your inbox.

```
sudo gedit /root/.forward
```

Put this line in the file:
```
username@localhost
```

Now, you will receive any mail sent to root.  To make things more convenient, let's set up Evolution to read the mail.

(Note: I use Thunderbird as my email client, and it required me to change the permissions of the /var/mail directory.  I don't know if Evolution also requires this.  If you get some sort of permission errors, you may need to *sudo chmod 777 /var/mail* , which is what Thunderbird wanted me to do.)

Open up Evolution.  In Tools -> Settings -> Mail Accounts, click Add.  Enter your Full Name if you wish, and your local mail address *username@localhost*, then click Forward.

For server type, select "Standard Unix mbox spool or directory."  For Path, enter /var/mail/username , then click Forward.

The options on the next screen are optional.  Moving right along!

On the next screen, select Sendmail for the Server Type, then click Forward.  Name the account however you wish.  I would recommend username@localhost, Local Mail, or something similar.  Now you're finished!

To test, compose a mail to root@localhost and send it.  Then click Send/Receive.  You should see the [new mail](http://hungsquirrel.org/images/rootmail.jpg) pop up in your inbox.


I am quite new to this, so if there are any errors in here, please feel free to tell me so I can edit this post for accuracy!

---

### Post by Cuber on 2005-05-11
[QUOTE=HungSquirrel]Occasionally, certain system daemons and utilities will send local Unix mail to root's local email inbox, /var/mail/root .  Well, it doesn't do you much good there!

If you want to read these system messages, you can always do *sudo mutt -f /var/mail/root* if you are familiar with mutt.  However, an easier and more efficient way to check this mail would be to have it forwarded to your user's local inbox, and then read it with your favorite email reader.

**Throughout this HOWTO, replace *username* with your account name.**

First, you need a mailbox, preferably with all of root's old mail already in it.

```
cd /var/mail
sudo cp root username
sudo chown username username
sudo chgrp username mail
```

That creates a mailbox for your username with the appropriate user and group permissions.  The contents of the mailbox are a copy of root's mailbox.

Now, it's time to forward all of root's incoming mail to your inbox.

```
sudo gedit /root/.forward
```

Put this line in the file:
```
username@localhost
```

Now, you will receive any mail sent to root.  To make things more convenient, let's set up Evolution to read the mail.

(Note: I use Thunderbird as my email client, and it required me to change the permissions of the /var/mail directory.  I don't know if Evolution also requires this.  If you get some sort of permission errors, you may need to *sudo chmod 777 /var/mail* , which is what Thunderbird wanted me to do.)

Open up Evolution.  In Tools -> Settings -> Mail Accounts, click Add.  Enter your Full Name if you wish, and your local mail address *username@localhost*, then click Forward.

For server type, select "Standard Unix mbox spool or directory."  For Path, enter /var/mail/username , then click Forward.

The options on the next screen are optional.  Moving right along!

On the next screen, select Sendmail for the Server Type, then click Forward.  Name the account however you wish.  I would recommend username@localhost, Local Mail, or something similar.  Now you're finished!

To test, compose a mail to root@localhost and send it.  Then click Send/Receive.  You should see the [new mail](http://hungsquirrel.org/images/rootmail.jpg) pop up in your inbox.


I am quite new to this, so if there are any errors in here, please feel free to tell me so I can edit this post for accuracy![/QUOTE]
 Can you explain how you have setup thunderbird to get this mail?

I do not wanna use two different mail clients :-D

---

### Post by gloups on 2005-06-05
see here: 
[http://ubuntuforums.org/archive/index.php/t-10019.html](http://ubuntuforums.org/archive/index.php/t-10019.html)

---

### Post by TheWizzard on 2006-06-15
hi 
i found this howto very useful. however, i want to forward the root mail to an external mail account (gmail). postfix seems to block this. 
has anyone any clue how to let postfix send mail to an external account?
cheers

---

### Post by jetpeach on 2006-06-17
thewizzart - i am also interesting in forwarding it to an external account.  since this thread is in warty i'll start a new thread in dapper.  if i can find an answer, i'll post a howto in the howtos section.  also, please let me know if you've found a solution.

---

### Post by carlos22 on 2007-06-17
Thanks a lot .. very clar and very simple.

---

### Post by TheWizzard on 2007-06-18
> **jetpeach said:**
> thewizzart - i am also interesting in forwarding it to an external account.  since this thread is in warty i'll start a new thread in dapper.  if i can find an answer, i'll post a howto in the howtos section.  also, please let me know if you've found a solution.

sorry i didn't reply to this earlier. 
i found something: 
- forward roots mail to gmail directly doesn't work
- forward roots mail to personal account and then forward to gmail works.

---

### Post by Robb987 on 2008-06-07
This post is a while ago, but I tried to get it to work in Ubuntu 8.04 and Evolution.

I found out there is no root emailbox in /var/mail on my pc, but I found my username emailbox filled with e-mail from root@localhost. 

So no need to chmod anything nor forward e-mail, it's my own mailbox ;-)

I configured evolution as told in the first post. It did not work. But I needed to change only one thing:

"For server type, select "Standard Unix mbox spool or directory.""
to:
For server type, select "local delivery."

That's all!

By the way, thanks for this nice howto!

---

### Post by MechaMechanism on 2009-05-03
Would this not be more simple if you used Exim4.

```
sudo aptitude install exim4
```There is no further set up required and the root mail is automatically delivered to the first user account.  Also for Thunderbird it's real easy.

```
sudo adduser **USERNAME** mail
```This will very nicely set up the proper permissions for Thunderbird.  Chown 777 is too ugly.

---

### Post by duceduc on 2012-03-12
I know it's an old thread, but I couldn't find my answer. How do I setup with thunderbird?

---

### Post by von Stalhein on 2012-03-13
> **duceduc said:**
> I know it's an old thread, but I couldn't find my answer. How do I setup with thunderbird?

Nice Lazarus job :D

I'm keen to know as well - I tried here [http://bit.ly/bNNOa](http://bit.ly/bNNOa) but failed at he first hurdle as there is no etc/aliases to modify on my system. 

I have created one, so I'll stuff around with it from there.

---

