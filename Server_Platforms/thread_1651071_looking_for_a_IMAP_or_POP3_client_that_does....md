---
title: "looking for a IMAP or POP3 client that does..."
date: 2010-12-22
forum: Server Platforms
---

### Post by carisch on 2010-12-22
I am looking for a IMAP or POP3 client (IMAP prefered) that when a new message is recived it would save it as a plain text file and pass it to a bash script. 

I think fetchmail may have to potential to solve the following problem, however i need guidance.  


this will be run from a text based server, so no applications needing X.


--Carisch

---

### Post by SeijiSensei on 2010-12-22
If you have access to the server, you can use [procmail]("http://www.procmail.org/") for this task.  See "man procmail", "man procmailrc", and "man procmailex" for help.  It's installed by default as the "mail delivery agent" on most distributions.

---

### Post by carisch on 2010-12-23
> **SeijiSensei said:**
> If you have access to the server, you can use [procmail]("http://www.procmail.org/") for this task.  See "man procmail", "man procmailrc", and "man procmailex" for help.  It's installed by default as the "mail delivery agent" on most distributions.


thanks, i will look in to this tonight. 



Will procmail handle downloading the messages?

---

### Post by elico on 2010-12-24
you can also just use the regular mail system with procmail defaults and not the Maildir/ functions.

---

### Post by Girya on 2010-12-24
use fetchmail as a cronjob to download email to local server then procmail to process the emails according to recipes you create. below is a portion of my .procmailrc file. 

the first recipe that starts "* ^From.*5555555555.*" executes a shell script when I send a sms to my email address from my cell phone.

```
# Recipes

:0:
* ^From.*5555555555.*
|/home/user/bin/some_script.sh

:0:
* ^TO.*blfs.*
blfs

:0:
* ^From.*Netflix.*
Netflix

```

the best way to start is to search the web for .procmailrc file examples and then adapt one that seems close to what you want to do.

you need to be able to write a regular expression that will match some line in the email you want to save as a text file.

---

