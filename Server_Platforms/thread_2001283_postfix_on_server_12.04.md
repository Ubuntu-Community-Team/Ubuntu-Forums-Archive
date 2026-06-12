---
title: "postfix on server 12.04"
date: 2012-06-10
forum: Server Platforms
---

### Post by timothylegg on 2012-06-10
Hello all,

I have Ubuntu 12.04 server install.  I have been following a wonderful document for teaching myself about postfix (and courier):

[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

But there is possibly an error in the document that actually has me stuck.  

"Instruct Postfix to use Maildirs instead of Mboxes:"

I follow the instructions to execute:
```
sudo postconf -e "home_mailbox = Maildir/"
```and then I restart postfix.  I then am given three commands to enter.  "fmaster" is a test account created earlier in the instructions

```

su - fmaster
MAIL=/home/fmaster/Maildir
mail

```but I get a file called /home/fmaster/Maildir instead of a directory.  Need I mention, further steps have dubious results.

So what went wrong with my following of this document?

Thank you all very much!

---

### Post by chienpo on 2012-06-10
> **timothylegg said:**
> Hello all,

I have Ubuntu 12.04 server install.  I have been following a wonderful document for teaching myself about postfix (and courier):

[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

That document was last edited (see the very bottom of the page):

> PostfixBasicSetupHowto  (last edited 2011-04-27 12:37:01 by [marjo-mercado]("https://launchpad.net/%7Emarjo-mercado"))So, it was probably edited and tested on an older version of Ubuntu. No, according to the timestamp, it **was** edited with an older version of Ubuntu in mind (nothing newer than 11.04).

Sometimes as Ubuntu and the packages included in it are updated, the set of default configuration values for various packages are changed. Guides that have you follow step-by-step instructions might not work (as you discovered) for versions that it wasn't specifically tested against.

Specifically...

> **timothylegg said:**
> But there is possibly an error in the document that actually has me stuck.  

"Instruct Postfix to use Maildirs instead of Mboxes:"

I follow the instructions to execute:
```
sudo postconf -e "home_mailbox = Maildir/"
``` and then I restart postfix.  I then am given three commands to enter.  "fmaster" is a test account created earlier in the instructions

```

su - fmaster
MAIL=/home/fmaster/Maildir
mail

``` but I get a file called /home/fmaster/Maildir instead of a directory.

The instruction to set the "home_mailbox" configuration directive to "Maildir/" is correct. You can verify this by checking out the official [Postfix Documentation]("http://www.postfix.org/documentation.html") for this directive here:

[http://www.postfix.org/postconf.5.html#home_mailbox](http://www.postfix.org/postconf.5.html#home_mailbox)

As it says, any value for "home_mailbox" that ends in a slash ("/") will direct postfix to use the qmail-style "Maildir" format. However, note that the documentation also shows a list of configuration parameters, in a prioritized order, that all collectively determine the ultimate delivery of a message destined for a local address. The default values for any of these may have changed since that document was last created. Or, the defaults may have been changed by the postfix package maintainer between versions.

> **timothylegg said:**
> Need I mention, further steps have dubious results.

So what went wrong with my following of this document?

Thank you all very much!

If you have a fresh install and followed the document verbatim (I've been assuming no deviation or error on your part), then it's likely a case of that document just being out-of-sync with your version of Ubuntu. Especially if many steps don't work.

Now, to specifically test what postfix currently thinks the value of the "home_mailbox" configuration parameter is, you can issue the command ```
sudo postconf home_mailbox
``` and it'll tell you. This is the best way to verify that your setting changes are actually being used.

You can also directly edit the configuration file. The file is, by default, located at ```
/etc/postfix/main.cf
``` and can be edited with any text editor (through "sudo" of course, such as ```
sudo <my-editor> /etc/postfix/main.cf
```).

Now, if you'd like help getting postfix to work a specific way, let us know. Also, if you intend to run a postfix email server in production, you'll need to eventually dive in and really get into the nitty-gritty details. The official postfix docs are the best place to get the final word:

[http://www.postfix.org/documentation.html](http://www.postfix.org/documentation.html)

After all, you don't want to accidentally open up an open SMTP relay for spammers to use. Good luck!

---

### Post by timothylegg on 2012-06-14
Thank you very much.  The documentation they have has been helpful, despite the number of dead links in their library.

I verified the setting of the home_directory, and it is set according to my expectations.  I do get a zero-size file in the home directory for the user.

```
# postconf home_mailbox
home_mailbox = Maildir/

```

So why is it creating a file instead of a directory?


So since the document expects an older version of Ubuntu, maybe I should downgrade to a version that has more documentation...  I don't just want a recipe to set it up, I also want to understand what the software is doing at a lower level, but I have to begin somewhere.  I had hoped the documentation would be relevant to the current stable version of Ubuntu.

So what is the most recent version of Ubuntu that is still well documented?  I won't be using X on a server, so I have no problem using newer versions of Ubuntu.  For my laptop though, I'm still running 10 until I find a GUI that I can use effectively.

---

### Post by chienpo on 2012-06-14
**TL;DR**

[LIST=1]
[*]Don't bother downgrading your OS. Instead, find a different guide.
[*]Consider (safely) posting your postfix config files here so we can better help you.
[/LIST]
> **timothylegg said:**
> Thank you very much.  The documentation they have has been helpful, despite the number of dead links in their library.

I verified the setting of the home_directory, and it is set according to my expectations.  I do get a zero-size file in the home directory for the user.


Yes, as I said, your value for this setting is correct.

> **timothylegg said:**
> ```
# postconf home_mailbox
home_mailbox = Maildir/

``` So why is it creating a file instead of a directory?


Without actually seeing your postfix config files I couldn't tell you for sure. You might consider posting your "/etc/postfix/main.cf" file (and possibly other files in the same directory) on the forum ***after*** redacting any sensitive information out of them (like credentials).

That said, I will reiterate what I attempted to say earlier. The problem is likely because some *other* setting is superseding "*home_directory*". Not because "*home_directory*" is incorrect. But, as I said, I just don't know without seeing actual config files.

> **timothylegg said:**
> So since the document expects an older version of Ubuntu, maybe I should downgrade to a version that has more documentation...  I don't just want a recipe to set it up, I also want to understand what the software is doing at a lower level, but I have to begin somewhere.  I had hoped the documentation would be relevant to the current stable version of Ubuntu.

So what is the most recent version of Ubuntu that is still well documented?  I won't be using X on a server, so I have no problem using newer versions of Ubuntu.  For my laptop though, I'm still running 10 until I find a GUI that I can use effectively.

I suspect that postfix hasn't actually changed much since the guide you're referencing was last updated. Are you sure you followed it exactly?

It is also possible that guide just contains an error. I'd have to set up a VM and go through the guide myself to be able to say for sure. I'll actually be updating my personal Debian Squeeze server to Ubuntu 12.04 in a little while. It is my personal mail server and runs postfix so perhaps I'll compare the guide's instructions with my own knowledge when I do it and contribute any fixes and/or updates to the guide when I do. If I do, I'll update this thread too.

As for deliberating whether to downgrade your OS, I'd instead just try to find another guide online. Lots of bloggers have created similar guides through the years and many of them aren't quite so formulaic. I like those ones because then you can use them even if your environment is slightly different (different versions or entirely different base OS). They also teach you more.

Whatever route you go, good luck and be sure to update this thread for posterity!

---

### Post by CharlesA on 2012-06-14
> **chienpo said:**
> **TL;DR**

[LIST=1]
[*]Don't bother downgrading your OS. Instead, find a different guide.
[*]Consider (safely) posting your postfix config files here so we can better help you.
[/LIST]

+1.

> 
I suspect that postfix hasn't actually changed much since the guide you're referencing was last updated. Are you sure you followed it exactly?

I figure you are right. I used a tutorial for setting up postfix as a gmail relay that had my do all sorts of random stuff like creating an SSL cert among other things. Other tutorials told you an easier way to do it.

> It is also possible that guide just contains an error. I'd have to set up a VM and go through the guide myself to be able to say for sure. I'll actually be updating my personal Debian Squeeze server to Ubuntu 12.04 in a little while. It is my personal mail server and runs postfix so perhaps I'll compare the guide's instructions with my own knowledge when I do it and contribute any fixes and/or updates to the guide when I do. If I do, I'll update this thread too.

Aye. I always test stuff on a VM before moving it into production. Snapshots ftw! ;)

> As for deliberating whether to downgrade your OS, I'd instead just try to find another guide online. Lots of bloggers have created similar guides through the years and many of them aren't quite so formulaic. I like those ones because then you can use them even if your environment is slightly different (different versions or entirely different base OS). They also teach you more.

+1. See here too! [http://woodel.com/](http://woodel.com/)

---

