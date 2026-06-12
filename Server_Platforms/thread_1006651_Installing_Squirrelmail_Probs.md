---
title: "Installing Squirrelmail Probs"
date: 2008-12-09
forum: Server Platforms
---

### Post by Mucker212 on 2008-12-09
Hi,

I followed instructions on installing squirrelmail on my dedicated server. I installed fine but when I goto the webpage to access the webmail I get this error in my browser.

```
Warning: Unknown: open_basedir restriction in effect. File(/usr/share/squirrelmail/index.php) is not within the allowed path(s): (/tmp:/home/default/gozbox.com) in Unknown on line 0

Warning: Unknown: failed to open stream: Operation not permitted in Unknown on line 0

Warning: Unknown: Failed opening '/usr/share/squirrelmail/index.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0
```

Anyone know what I need to do to fix this?

---

### Post by Mucker212 on 2008-12-09
Damn this Unmanaged dedicated server!:confused:

---

### Post by Mucker212 on 2008-12-10
Anyone?

---

### Post by MJN on 2008-12-10
Have you Googled for this error and followed any potential fixes?
 
I have, and would suggest the following:
 
i. Check your open_basedir directive in php.ini and either remove the restrictions or add /use/share/squirrelmail/
 
or ii. Move your Squirrelmail PHP code into a sub-directory of an allowable path (e.g. /home/default/gozbox.com/mail/) and reconfigure Apache to use that as the DocumentRoot for Squirrelmail
 
Mathew

---

### Post by Mucker212 on 2008-12-10
Ive tried both these options but no Joy.

Also my base_dir has no restrictions in place. And when I try option i.) you suggested (which I found through googleing) IT still doesnt work. I also restarted apache.

Im lost

---

### Post by MJN on 2008-12-10
Post the error you get having followed (ii).
 
Mathew

---

### Post by Mucker212 on 2008-12-10
Ok, im actually a bit of a newb and dont know how to do ii.)

:(

Also would this mean I would have to install it on each domain for it to work on all emails?

---

### Post by MJN on 2008-12-10
Firstly, as a newb you should learn quickly that if you lie about having tried things people have suggested then they may be inclined to not bother with further help.

I've never installed Squirrelmail via the package manager before so do not know where/how it hooks into Apache. Notwithstanding this we could try adding a symbolic link from inside your web directory to the SM location. For example, if your web root was [http://gozbox.com](http://gozbox.com) (and this corresponded to /home/default/gozbox.com in the filesystem) and you wanted [http://gozbox.com/mail](http://gozbox.com/mail) to be your webmail then do the following:

```
mkdir /home/default/gozbox.com/mail
ln -s /usr/share/squirrelmail /home/default/gozbox.com/mail
```If you now ran **ls -l /home/default/gozbox.com** you should find the very same files as in /usr/share/squirrelmail. Furthermore, hopefully Apache's PHP module will do also.

Mathew

---

### Post by Mucker212 on 2008-12-11
It just gives me the same error as above.

:(

---

### Post by MJN on 2008-12-11
Can you post the exact error?
 
Mathew

---

### Post by Mucker212 on 2008-12-11
yes it is exact;y the same as my first post

```
Warning: Unknown: open_basedir restriction in effect. File(/usr/share/squirrelmail/index.php) is not within the allowed path(s): (/tmp:/home/default/gozbox.com) in Unknown on line 0

Warning: Unknown: failed to open stream: Operation not permitted in Unknown on line 0

Warning: Unknown: Failed opening '/usr/share/squirrelmail/index.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0
```

---

### Post by MJN on 2008-12-11
Oh, right, it seems to be spotting the true destination of the symlink (I was hoping it would be unaware of it).
 
To be honest I'm not sure what to suggest. My experience of PHP configuration is minimal, and certainly not up to fault-finding someone else's setup.
 
Perhaps someone else can provide some input?
 
Mathew

---

### Post by Mucker212 on 2008-12-11
I'll keep my fingers crossed, but you are one of two people only to ever help me out.

Thanks Anyway

---

### Post by Mucker212 on 2008-12-12
No response yet.

My main reason for webmail is so I can train spamassassin.

I only have pop3 email all my emails from this server come into my outlook mail client. I thought If i done webmail I would beable to train spamassassin.

Is there an easy way for me to do this?

---

### Post by lukeyduke on 2008-12-22
I find that Squirrelmail is very buggy and boring, but I found a much better alternative!

I have recently upgraded to a fantastic webmail client, Atmail. They are a commercial email server appliance and webmail provider, however they have recently released a free version of their software, called atmail open. The biggest advantage is that I can now access my emails from anywhere in the world from the same fantastic interface every time. I find it is a much faster, simpler, better looking interface than any other, such as hotmail and gmail.

You can find an tutorial for installing it on there website here --> [http://atmail.com/kb/2008/installing-atmail-open-webmail-client-on-ubuntu/]("http://atmail.com/kb/2008/installing-atmail-open-webmail-client-on-ubuntu/")

---

### Post by spiderbatdad on 2008-12-22
this guide worked for me [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)
it includes
postfix
courier
mysql
squirrelmail
clamav
amavis
spamassassin
postgrey
but honestly took a few days of trouble shooting errors to get everything working.

---

### Post by nicolasdiogo on 2008-12-23
hi,

did you have a look at this article?

i have installed squirrelmail following this and almost everything works - only attachments give me problem - but still worth having a look.

Nicolas

---

