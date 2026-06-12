---
title: "&quot;/var/www/sent is not a mailbox&quot; in Apache2 error.log"
date: 2013-05-08
forum: Server Platforms
---

### Post by noeffort on 2013-05-08
This just took me about 2 hours to figure out.. grrr.  So, I am posting not only so I can come back and find how I "fixed the glitch", but for any others out there who end up searching on that exact string and is driving them batty too!

Scenario:
Cinnamon Mint 14 (nadia) 
Apache2 
PHP
mutt/mail

After setting up my crisp new Cinnamon Mint Apache2/PHP5 server, I was attempting to port over a script that processed a form, that previously worked on Fedora.  This particular script runs ldap queries and then sends the results to a mail recipient provided in the form fields.  I had problems in the past, but its been so long I could not remember all the hurdles and jumps needed to get past when neither "mail" nor "mutt" would work correctly to send the results file, either as the mail itself, or the attachment.

The following line is the line in question:

[INDENT][PHP]`mutt -s "sending $outfile" $mailrcpt1 $mailrcpt2 -a $outfile < $outfile`;[/PHP][/INDENT]

At first I was seeing this error in /var/log/apache2/error.log:

[INDENT]```
/var/www/sent: Permission denied (errno = 13)
```[/INDENT]

This error was confusing because what it really should have said is that the directory doesn't exist... easy enough... by following the post found [here on Ubuntu forums]("http://ubuntuforums.org/showthread.php?t=1243547") I was able to get past that hiccup easily enough, as one poster stated:

"I then created new folder /var/www/sent, chown it to www-data:www-data and 755 permission"  <== in my case i had to chown to root:root (your mileage may vary)...  Check first who "owns" /var/www

Well...
That got me past the first error, but next came...

[INDENT]```
/var/www/sent is not a mailbox.
```[/INDENT]

The fix for this is to create the .muttrc file in the correct "user" directory.  For apache2 that is /var/www, so i "touch"ed a file called .muttrc and added the line to "set copy=no"

This note => add "set copy=no" to /etc/Muttrc to disable the e-mail copy feature. <= is from [http://www.mail-archive.com/nagios-users@lists.sourceforge.net/msg06536.html]("http://www.mail-archive.com/nagios-users@lists.sourceforge.net/msg06536.html")

Et voila!  All is well.

---

