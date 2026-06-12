---
title: "Server Email"
date: 2008-04-15
forum: Server Platforms
---

### Post by mattc908 on 2008-04-15
Anyone know or have a guide to: All I want is my server be able to send mail out. Thats all I want is that its able to send mail out, so for instance whensomeone signs up on my forum it can send out mail to them to give them there info. Nothing else. I dont need to be able to access it, just so it can send mail.
Thanks,
Mattc908

---

### Post by Dr Small on 2008-04-15
Sendmail should do the trick.

---

### Post by HermanAB on 2008-04-15
Sendmail - gawd, what did Matt do to you?

You can install Postfix, Qmail or Citadel.  However, if you really only wish to send mail and nothing more, then nullmailer may be all you need and will take a few seconds to set up, vs a few hours/days/weeks for the others.

---

### Post by mattc908 on 2008-04-15
Nullmailer, so it will allow programs on the server like wordpress to send out emails such as passwords for people signing up?

---

### Post by HermanAB on 2008-04-15
Google for it, it is really trivial and all it does is relay mail.  So you set it to relay outgoing mail to your ISP mail server.  I don't want to explain more, since it is quite pointless - just go the web site.

---

### Post by torry_loon on 2008-04-15
Have a look at this.

[https://help.ubuntu.com/community/MailServer]("https://help.ubuntu.com/community/MailServer")

---

### Post by mattc908 on 2008-04-15
Okay here is another question, the way my webserver is set up is through a dyndns linked to the .com name, so I am on a dynamic Ip not a static one, is it still possible to set up a mailserver witch I only want the server as stated above just be able to send out mail for things like wordpress and a forum.

---

### Post by koenn on 2008-04-16
mail servers usually work by hostnames (MX records) and use dns A records to resolve the names, so as long as your DNS is up to date it should work. This only matters for receiving mail anyway so there's no immediate problem. 

Some mail servers refuse to receive mail from mail servers with a dynamic address, cause they consider it an indication that you might be a spam relay.
The workaround to that is to have your mail server relay the mail to your ISP's mail server, who will accept it because they provide mail service to their customers / recognise the sender IP address as one of theirs, and then, the ISP mail server will relay your mail msgs to the recepients (' mail server).

---

### Post by HermanAB on 2008-04-16
You don't need a MX record for an outgoing mail server.  You don't need *any* DNS record for this.  Just Google for nullmailer.  You could have had this working hours ago already...

---

### Post by mattc908 on 2008-04-16
I googled for it and it did not produce anything beneficial about nullfier,
I'm not dumb I understand how to google, and I understand simple commands like:
sudo apt-get install nullmailer

Its jsut beyond once its installed how to make it operate correctly. I have it installed but can't seem to get it too mail.

---

### Post by Dr Small on 2008-04-16
Not trying to be rude or anything, as I have never used nullmailer and do not  know how to start and stop it, but if it was me, I would begin by reading the manual. They generally tell you most everything you need to know about it, right in there.

Dr Small

---

### Post by mattc908 on 2008-04-16
The only problem is I didnt find a manual, so I do not know how to work it exactly.

---

### Post by HermanAB on 2008-04-16
No  man page, README or INSTALL files?  I used it many moons ago and it was super easy.

Here is something:
[http://untroubled.org/nullmailer/HOWTO](http://untroubled.org/nullmailer/HOWTO)

---

### Post by mattc908 on 2008-04-16
Thanks, again none of those direction helped me or applied to me, maybe someone who feels like helping me out can give there say:
Set up your hostname in SYSCONFDIR[1]/nullmailer/me.  Usually this
   will be as simple as typing:
	/bin/hostname >SYSCONFDIR/nullmailer/me
   You may also wish to set up the defaultdomain and defaulthost
   configuration files.  See the man page for nullmailer-inject for more
   details.

That directory or file does not work.

mattc908@mattc908:~$ /bin/hostname >SYSCONFDIR/nullmailer/me
-bash: SYSCONFDIR/nullmailer/me: No such file or directory

---

### Post by MJN on 2008-04-17
I've never used Nullmailer but I imagine SYSCONFDIR is referring to your 'system configuration directory', most likely /etc/ in this case.
 
I was always under the impression that Nullmailer is extremely easy to get up-and-running largely by virtue of it being a simple application to do a simple task and so the length of this thread is making me wonder if something is being misunderstood here?
 
My advice would be to take this opportunity of hunting down the manual for this application and read it through at least several times. Documentation is one of the hardest aspects of software development to produce yet one of the most important - so please use it! You will learn nothing by someone giving the answer in here... (teach a man to fish and all that)
 
If you still get nowhere just shout and I'll install Nullmailer myself and see what's what.
 
Mathew

---

### Post by koenn on 2008-04-17
isn't SYSCONFDIR more of a RedHat thing ? 

anyway, if you havent tried ```
man nullmailer
``` yet, that's the first thing you should do.

If you can't get a man page, try looking online
[http://www.penguin-soft.com/penguin/man/7/nullmailer.html](http://www.penguin-soft.com/penguin/man/7/nullmailer.html)
[http://pwet.fr/man/linux/administration_systeme/nullmailer_send](http://pwet.fr/man/linux/administration_systeme/nullmailer_send)
[http://pwet.fr/man/linux/commandes/nullmailer_inject](http://pwet.fr/man/linux/commandes/nullmailer_inject)

I've never used this, but from the looks of it, just have a look at the config files to see if they make sense / have sensible defaults, then just try a those nullmailer-inject and nullmailer-send commands and see what happens. Probably it just works.

---

### Post by mattc908 on 2008-04-17
Im still having difficulty with it, I've been working on different mail clients trying to get them to work and no success can anyone step in who has done it on ubuntu to help me out here? I'm 16 and in highschool dont have much time to figure this out and lack the experience.

---

### Post by koenn on 2008-04-18
nullmailer quickstart guide

Install nullmailer
```
sudo apt-get install nullmailer
```

Run nullmailer-send in background so it will send out any queued mail immediately. Not sure if you need to run it as root, but I did.
```
sudo nullmailer-send -d
```


how to send a msg
```

n@nix:~$ nullmailer-queue <<eof
> bill.gates@microsoft.com
> spamvictim@aol.com
>
> Hi there, 
> We have a beautifull email sollution called Microsoft Outlook
> It works best in combination with Microsoft Exchange
> If you want software that Just Works, please reply to this
> message to receive a free evaluation copy
>
> eof
n@nix:~$

```
first line : sender address
2nd line : recipient address (multiple addresses -> use multiple line

blank line between addresses and msg body

end with eof 

help : 
```
man nullmailer-queue
```

---

### Post by mattc908 on 2008-04-18
Yeah, thanks but I need it to allow the server to send mail on tis own, when lets say a blog i have going when someone signs up it sends them their password. But it currently won't send them the information that it needs. How would I be able to accomplish this?

---

### Post by koenn on 2008-04-18
Hm. 
in that case you'd need to have your web server to create the contents of the email, and invoke nullmailer-queue. I have no idea how that's done. 

On the other hand, I'm quite sure that there are php or perl modules that were made specifically to do this sort of stuff on web servers :

something like this : 
[http://www.intermedia.net/support/kb/default.asp?id=869](http://www.intermedia.net/support/kb/default.asp?id=869)

---

### Post by netlogic on 2008-04-18
> **HermanAB said:**
> Sendmail - gawd, what did Matt do to you?

You can install Postfix, Qmail or Citadel.  However, if you really only wish to send mail and nothing more, then nullmailer may be all you need and will take a few seconds to set up, vs a few hours/days/weeks for the others.

Yea man... He is evil. Matt, I will send you a hammer. Don't use it on yourself. Kill the servers if you go insane.

---

### Post by mattc908 on 2008-04-18
So wait what should I install /do to allow my server to send mail on its own?

---

### Post by HermanAB on 2008-04-18
Depends...  A mail system is very complicated to configure from scratch and Ubuntu is a DESKTOP system.  Ubuntu doesn't have proper server wizards.  So, if you insist on using Ubuntu, then you are somewhat schrewed...

You can install Mandriva or Suse Linux and eventually click the mail server wizard to install Postfix for you.

You can go to [http://citadel.org](http://citadel.org) and run Easy Install.  This works, but Citadel is a full blown system, much more than you want.

You can go to [http://postfix.org](http://postfix.org) and read for two weeks, then give up and install Mandriva Linux and click the mail wizard.

You can figure out how to install Nullmailer.

You can figure out how to install Qmail.

...

Your choice.

Cheers,

Herman

---

### Post by koenn on 2008-04-19
some more choices (choice is good :) )

That blog, web page, online registration from,  whatever, ... that you would like to set up so that it can send mail : you need to find out (or decide) what technology it's using (php, perl, ... ), then make sure the corresponding module(s) to make it mail-enabled are installed, then have a server-side script that creates the mail msg you want to send using variables for destination address and password, and send it.

---

### Post by mattc908 on 2008-04-19
Im running ubuntu server edition, but you recommend Mandriva server edition for the mail wizard, second off this Ciadel can be installled and it would allow my server to send mail for what i explained before?

---

### Post by mattc908 on 2008-04-20
?

---

