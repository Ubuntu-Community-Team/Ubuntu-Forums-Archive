---
title: "Need a simple mail server (postfix?)"
date: 2008-04-05
forum: Server Platforms
---

### Post by Blednik on 2008-04-05
Hello.

I've done some searching on this topic, but couldn't quite find all the answers or perhaps I failed to understand them all. I have *some* linux experience, but I'm rather a newbie when it comes to setting up mail servers. There were a number of good threads I found while searching and certain really gave me some insight. I'd like to ask for some help to clarify things and I'll try to provide as much info as I can.

I am using an old Pentium2 PC with Ubuntu server 7.10 as my gateway at home. It has basic LAMP installation plus a firewall script that does DNAT between two network cards (one goes to a switch, which is my home lan, other is connected to a DSL modem). The server already acts as a webserver and has a static IP address and a registered domain (we'll call it mydomain.com). Recently I've installed a phpBB system on it and so came the need for a working mail system. Now I'm not quite sure what software to use (I have installed postfix, but gave up on its configuration) so I'll just describe my needs and hopefully I can get some suggestions.

Basically I need a SMTP server. I would like to use something to send email (which should appear to be from let's say "info@mydomain.com" to outside users) as well as receive mail back in case someone decides to reply to it. Also, the board should be able to use this mail system to send mails (like activation mail) from the same account via SMTP ([see here](http://img138.imageshack.us/img138/2428/smtpphpbb3ex1.gif)). Logically, I'll also need a way to check the received email. I do not plan to use any more than two or three mail accounts.

Thanks.

Can I hope for Mr. C. to pop up in here?
He did some really nice explanations. :)

EDIT: Typos, link.

---

### Post by Dr Small on 2008-04-05
I just very recently setup a Postfix for my simple mailserver. I wrote an easy guide about it too. You can read it here:
[http://php.8ez.com/drsmall/blog/?p=243](http://php.8ez.com/drsmall/blog/?p=243)

Dr Small

---

### Post by Blednik on 2008-04-06
Hello, thanks for the reply. Nice guide, but unfortunately it doesn't say much about postfix configuration.

I have already installed postfix and mailx, but I'll probably want to use something more crispy to check mail. I'm not sure if it's a good idea to go installing all that courier imap/pop stuff (assuming you need that, if you want to check mail with outlook or thunderbird). Since I'm running LAMP, I thought the best way would be simply to use webmail.

Also, I do have my own domain ;)

---

### Post by Dr Small on 2008-04-06
Ah, ok. Well if you figure the IMAP/POP stuff out, give me a call, because I want to get that configued too :D
Sorry for not being very helpful :(

Dr Small

---

### Post by Blednik on 2008-04-06
I've managed to get postfix working and now I can send/receive mail. The logs in /var/log can sometimes be of great help. I've figured my network was not properly set. It was 127.0.0.1/8 where it should have been 127.0.0.0/8.

The only problem is that my mail gets caught by spamblockers. I'll have to address this at some point. Also, is it a good idea to setup sasl?

Cheers.

---

### Post by smileypaul on 2008-04-07
Thanks dr. small..

also checked out your blogs, good stuff, i'll continuously read them as you update. Sorry to hear you are switching back to Vista.. although i agree, it appears to be much more "professional" , and compatible, it does have its short comings as well. My parents use it on their computer, and have  yet to have it up for more than 3 days. Coming out of hibernate it constantly crashes :( hopefully this is fixed for me in SP1.

I also remember when we first installed it about a year ago, I was trying to burn a DVD.. it quoted me on 676 days to  complete burning, and of course the application froze.. and then windows.. although everything was responsive, i couldnt kill the process, or log out of windows.. I had to hard - reboot.. upon completion, Windows had encountered a critical error.. and i had to do a "repair" windows isntallation ... :anger:

anyways, im sure these are just isolated problems, best of luck.

---

### Post by Dr Small on 2008-04-07
> **smileypaul said:**
> Thanks dr. small..

also checked out your blogs, good stuff, i'll continuously read them as you update. Sorry to hear you are switching back to Vista.. although i agree, it appears to be much more "professional" , and compatible, it does have its short comings as well. My parents use it on their computer, and have  yet to have it up for more than 3 days. Coming out of hibernate it constantly crashes :( hopefully this is fixed for me in SP1.

I also remember when we first installed it about a year ago, I was trying to burn a DVD.. it quoted me on 676 days to  complete burning, and of course the application froze.. and then windows.. although everything was responsive, i couldnt kill the process, or log out of windows.. I had to hard - reboot.. upon completion, Windows had encountered a critical error.. and i had to do a "repair" windows isntallation ... :anger:

anyways, im sure these are just isolated problems, best of luck.
Dear Sir, please check the date on the post that you speak of :D
It has a hidden meaning ;)

---

### Post by smileypaul on 2008-04-07
Of course.. April Fools.. glad to see you didtn leave :)

take care

---

### Post by hyper_ch on 2008-04-08
> **Dr Small said:**
> Ah, ok. Well if you figure the IMAP/POP stuff out, give me a call, because I want to get that configued too :D
Sorry for not being very helpful :(

Dr Small

I user courier-imap and and procmail with postfix for local delivery.

---

### Post by nkassi on 2008-04-08
I setup dovecot last night for imap support and it was pretty much painless. 

Postfix's setup was easy and done by debconf (the prompt that came up after apt-get postfix) I choosed internet site.

Only change after installation I had to make was change postfix to send email to Maildir (should have done that anyway). This is easily done by just appending this line to your /etc/postfix/main.cf file: 
```
home_mailbox = Maildir/
```
And then I pointed dovecot to it by uncommenting this line in /etc/dovecot/dovecot.conf:
```
mail_location = maildir:~/Maildir
```

For authentication I'm using the system accounts. 

I don't currently use my postfix server as my outgoing smtp server yet but I will soon.

---

### Post by zazuge on 2008-04-24
it's beter to setup you postfix and understand step by step as you make the setup evolve litile by little so i recommend you start from [www.postfix.com](www.postfix.com) and use the basic setup.

---

