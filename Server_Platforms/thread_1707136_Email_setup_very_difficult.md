---
title: "Email setup very difficult"
date: 2011-03-14
forum: Server Platforms
---

### Post by Robert the Kat on 2011-03-14
I have been searching for some time now on setting up incoming and outgoing email on my Ubuntu 10.10 server.  95% of the tutorials I have found are "old info."  One that was about two years old had so many lines you had to enter, one wondered if the mail would ever be set up.  I gave that one a try and it was following what the tutorial showed but about 3/4 of the way through, it failed.  So that ended the "install."
 
  I can't see why someone has not setup a simple program that would load everything you need with some adjustments you would need to make after it was set up.
 
  Is there any one somewhat simple solution to getting email to work or IS it that big of a problem?
 
RK

---

### Post by volkswagner on 2011-03-14
> **Robert the Kat said:**
> ...
 
  I can't see why someone has not setup a simple program that would load everything you need with some adjustments you would need to make after it was set up.
 
  Is there any one somewhat simple solution to getting email to work or IS it that big of a problem?
 
RK

Email server setup is a complex animal.  If you want dead simple, try [Citadel]("http://www.citadel.org/doku.php").  It even has webmail!  It does work best on it's own server, but it can live side by side with Apache2.

---

### Post by stmiller on 2011-03-14
There are many guides out there for postfix. Email is a little difficult to setup as it requires a good grasp of DNS, mail routing, storage, account management, and security in Linux.


:/

This is good for starters:

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

---

### Post by Robert the Kat on 2011-03-15
Thanks, I will look into all this when I find some more time.
 
RK

---

### Post by HermanAB on 2011-03-15
Robert, save yourself a lot of hair and use Citadel...

---

### Post by Kozley on 2011-03-15
If you don't understand to use Citadel. Here's a [tutorial]("http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-10.10") for virtual users of mailserver by howtoforge with security configuration. I do have same configuration to my ubuntu 10.04 and it works perfectly.

---

### Post by jmacgowan on 2011-03-15
> **Robert the Kat said:**
> 
I can't see why someone has not setup a simple program that would load everything you need with some adjustments you would need to make after it was set up.
 
Citadel is the answer that you're looking for, and it's extremely simple to set up and use.
 
E-mail can be a very complicated thing, and the reason is simple: understanding.  I actually just finished setting up a mail server and it was quite the bear at first because I was following tutorial after tutorial and just copying and pasting things instead of understanding what was happening and why.
 
Understanding what Postfix does, understaning what Dovecot does, understanding where to look when things go wrong and what the error messages actually mean make setting this stuff up easier.
 
If it wasn't for the fact that I wanted the "trial-by-fire" experience from doing it, I would have just stuck with Citadel -- it really is a great program.

---

### Post by Robert the Kat on 2011-03-15
> **stmiller said:**
> There are many guides out there for postfix. Email is a little difficult to setup as it requires a good grasp of DNS, mail routing, storage, account management, and security in Linux.
 
This is good for starters:
 
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)
 
  I gave this one a try.  The tutorial looked familiar.  I was correct.  It was the one I tried and it failed.
I got to: Generate certificates to be used for tls encryption and/or certificate authentication.
The command:
Openssl reg -new -key smtpd.key -x509 -days 3650 -out smtpd.crt # has prompts
 
I received the message:
openssl : error  'reg' is an invalid command.
 
So that is where I stopped.
 
RK

---

### Post by Robert the Kat on 2011-03-15
> **jmacgowan said:**
> Citadel is the answer that you're looking for, and it's extremely simple to set up and use.
 
E-mail can be a very complicated thing, and the reason is simple: understanding. I actually just finished setting up a mail server and it was quite the bear at first because I was following tutorial after tutorial and just copying and pasting things instead of understanding what was happening and why.
 
Understanding what Postfix does, understaning what Dovecot does, understanding where to look when things go wrong and what the error messages actually mean make setting this stuff up easier.
 
If it wasn't for the fact that I wanted the "trial-by-fire" experience from doing it, I would have just stuck with Citadel -- it really is a great program.
 
I have to agree.  It all has to do with what you know or can guess your way out of the problem.  That was where the luck came along when I was able to set up the Ubuntu desktop and XP on two different drives on a different computer.
 
RK

---

### Post by Robert the Kat on 2011-03-15
> **Kozley said:**
> If you don't understand to use Citadel. Here's a [tutorial]("http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-10.10") for virtual users of mailserver by howtoforge with security configuration. I do have same configuration to my ubuntu 10.04 and it works perfectly.
 
Thanks for all the info.  I will give Citadel a try and see just what happens with that setup.
 
(and maybe I will remember on how to get three quotes into one post.  I could at one time on a different forum)
 
RK

---

### Post by wongo888 on 2011-03-15
I use google hosted gmail. It works great. I rarely see spam.

[http://www.google.com/apps/intl/en/group/index.html](http://www.google.com/apps/intl/en/group/index.html)

---

### Post by jmacgowan on 2011-03-15
The reason it's tossing an error is because you're using 'reg' instead of 'req'.
 
Try this:
```
openssl req -new -key smtpd.key -x509 -days 3650 -out smtpd.crt
```
 
It's very important when following HOW-TOs to be very, very careful of what you type especially when you don't fully understand the command.  I'm not trying to be mean or scare you off, but it is possible to do some serious damage to your system if you're not careful.

---

### Post by Robert the Kat on 2011-03-15
> **jmacgowan said:**
> The reason it's tossing an error is because you're using 'reg' instead of 'req'.
 
Try this:
```
openssl req -new -key smtpd.key -x509 -days 3650 -out smtpd.crt
```
 
It's very important when following HOW-TOs to be very, very careful of what you type especially when you don't fully understand the command. I'm not trying to be mean or scare you off, but it is possible to do some serious damage to your system if you're not careful.
 
Well, blow my socks off!  I can understand that STUPID error with my old glasses, but no excuse with the new ones!
 
I tried what should have been an "easyinstall" of Citadel from easyinstall.citadel.org.  Only needed to type in one line and the program would/should do most of the work.  It stated it would take a long time and it did.  That is until an error poped up and the install ended!
 
Guess I will go back and try the other program again and watch what I type.  Maybe just best to forget it all.
 
RK
 
P.S.  Ok if I kill the server, I can just reinstall it.  Only thing on that 'puter.

---

### Post by SeijiSensei on 2011-03-15
> I received the message:
openssl : error 'reg' is an invalid command.

So that is where I stopped.
When a command fails it's often helpful to try "man command" to get the"**man**ual page" and "command --help" as well.  Typing "man openssl" shows there are a number of "STANDARD COMMANDS," one of which is "req" (short for "request").  You can search the results of the man command by typing a / and entering the string you wish to search for.  Searching for "/reg" takes me to an irrelevant entry at the end of the man page.

I'll just mention in passing that there are good reasons why e-mail is not trivial to set up.  It's very easy to mis-configure a mail server so that it becomes an [open relay]("http://en.wikipedia.org/wiki/Open_mail_relay").  I've had it happen twice, both a decade or more ago now.  Spammers use robots that search the Internet looking for exploitable servers. An open relay is immensely more valuable than Grandma's Windows PC sitting over in the corner of the spare room trying to send porn spam.  It's likely her ISP won't let her machine talk to the SMTP port (25) on remote servers.  A Linux mail server usually has no such limitations, making it a much more attractive target for exploitation.

---

### Post by Robert the Kat on 2011-03-15
SeijiSensei,
 
   Very interesting about the Email being ripped off and misused.  This server is more of an experiment than something that would be running 24/7 so I would hope there would not be any problems.
 
RK

---

### Post by HermanAB on 2011-03-16
> I tried what should have been an "easyinstall" of Citadel from easyinstall.citadel.org. Only needed to type in one line and the program would/should do most of the work. It stated it would take a long time and it did. That is until an error poped up and the install ended!

So what was the error?

Anyhoo, Citadel is in the software repos too, so you could use the software wizard to install it in a few clicks.

---

### Post by lisati on 2011-03-16
After over a year of using Postfix I want to encourage you not to give up, even if you settle on something other than postfix. It took me a few tries to get things working.....

---

### Post by jmacgowan on 2011-03-16
> **lisati said:**
> After over a year of using Postfix I want to encourage you not to give up, even if you settle on something other than postfix. It took me a few tries to get things working.....
Especially if this is just a recreational box.  Make mistakes.  Learn how to troubleshoot what went wrong and why.  Learn how to read error logs and determine what it even means.  All these things will help you with -everything- you do in Ubuntu.  Never give up!  Never surrender!

---

### Post by Robert the Kat on 2011-03-16
> **HermanAB said:**
> So what was the error?
 
Anyhoo, Citadel is in the software repos too, so you could use the software wizard to install it in a few clicks.
I wrote it down somewhere. Can't find. Does not matter now since I decided that the current install of the 10.10 server was so full of "junk" a re-install would help. It did. Citadel installed without any errors.
I read in another post that some one stated if they wanted a person that knows a great deal about Citadel, they should locate HermanAB.
If they were correct, maybe you can help with another problem. When I log into Webcit it did not find the administrators name. I was VERY CAREFUL during setup to double and triple check the name and password for the administrator. When I log in to webcit the summary page, about server shows "your system administrator is and that is where the "funny stuff" is. There is a small square box, the character "[" and the letter "C" repeated four times, then the correct adm name is shown. ?????
Is there any way to reset the Administrator?
 
RK

---

### Post by Robert the Kat on 2011-03-16
> **lisati said:**
> After over a year of using Postfix I want to encourage you not to give up, even if you settle on something other than postfix. It took me a few tries to get things working.....
 
> **jmacgowan said:**
> Especially if this is just a recreational box. Make mistakes. Learn how to troubleshoot what went wrong and why. Learn how to read error logs and determine what it even means. All these things will help you with -everything- you do in Ubuntu. Never give up! Never surrender!
 
   Yes, when I find the time.  Citadel set up after a re-install of 10.10 server.  The email is not working but that is something to keep looking into.
 
RK

---

