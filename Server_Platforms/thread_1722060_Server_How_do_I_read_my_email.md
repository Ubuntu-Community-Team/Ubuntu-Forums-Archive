---
title: "Server: How do I read my email ?"
date: 2011-04-05
forum: Server Platforms
---

### Post by highspider on 2011-04-05
/var/mail/root
/var/mail/www-data 

I know I have email but I can't figure out how to read it.
[COLOR=Red]  What is the Ubuntu Server 10.10 default email client for reading mail?[/COLOR]
  
Tired net search: ends up talking about setting up a new mail server or post fix or forwarding.
  nothing for just reading existing email messages.

tried "cant find it"
dpkg -l | grep mail

---

### Post by Grenage on 2011-04-05
Don't you just type *mail*?  I do on all mine.

---

### Post by SeijiSensei on 2011-04-05
I don't recall if it's installed by default, but **alpine** is my choice.

---

### Post by highspider on 2011-04-05
```

xxx@Server:~$ mail
The program 'mail' can be found in the following packages:
 * heirloom-mailx
 * mailutils
Try: sudo apt-get install <selected package>
xxx@Server:~$  alpine
The program 'alpine' is currently not installed.  You can install it by typing:
sudo apt-get install alpine

```neither one is is installed.  
 "alpine or mail"

I know freebsd is just mail and works default.
  Do I have to install one?
    I don't  mind; but, I usually like to use the default one's stuff comes with. 
     and didn't want a one floating around that i don't use or know about.

I used the default free-bsd one like [Grenage]("http://ubuntuforums.org/member.php?u=263074")
```

[COLOR=Red][COLOR=Black]sudo apt-get install heirloom-mailx

mail -f /var/mail/root
mail -f /var/mail/www-data
[/COLOR] [/COLOR]
```[http://www.freebsd.org/cgi/man.cgi?query=mail&sektion=1](http://www.freebsd.org/cgi/man.cgi?query=mail&sektion=1)

[COLOR=Red]Im going to leave this post opened for a two days- 
in case [COLOR=Black]"there is or isn't" [/COLOR]a default one that comes with server 10.10 install please reply

[/COLOR]

---

### Post by SeijiSensei on 2011-04-05
Distro maintainers have to decide which packages are necessary for that distribution's purposes and which left for later download.  These decisions often have little or nothing to do with the quality of the software involved.  In the case of Ubuntu, where most releases are designed to fit on a single CD, these decisions are especially difficult ones.  There are lots of programs on that CD that you won't "use or know about," too. 

Most people running servers rarely read mail on the same machine, so there aren't email clients packaged with Ubuntu Server. Just install alpine from the repositories; you'll be happy you did.

I actually find it very useful when I need to do mail administration to have a copy of alpine on the server.  Here's an example.  I had a client who had some POP3 users (the Chairman and President in particular) who used the "leave mail on server" feature of POP3.  Over time their mailboxes grew enormously, but they were unaware of the fact since they only ever saw the new messages in their inboxes.  Every six months or so something would happen that would desync the local copy of the mailbox and the copy in /var/spool/mail on the server.  Suddenly they'd start getting all their hundreds of messages again because they appeared new.  With alpine I could select messages by age, size, etc., and clean things up so the problem wouldn't recur (for a while).  Try deleting only messages whose attachments are greater than, say, 100 MB, by using emacs to edit their mbox files.

In short, if I were packaging the server version of Ubuntu, the two programs I'd definitely want to add to the current distro are alpine and bsd-mailx.  The latter I use mostly for testing email services from the command line and to send notices from routine scripts running from cron.

---

### Post by Grenage on 2011-04-06
> **SeijiSensei said:**
> I don't recall if it's installed by default, but **alpine** is my choice.

Hah, I'd not used Alpine before; it's brilliant.

---

### Post by HermanAB on 2011-04-06
Mutt.

Otherwise, if you are a hard core command line fanatic, use telnet.

---

### Post by SeijiSensei on 2011-04-06
> **Grenage said:**
> Hah, I'd not used Alpine before; it's brilliant.

Thank the nice folks at the University of Washington who wrote it, along with the UW-IMAP server, to provide mail services on campus in the mid-1990's.  Then it was called Pine; it was renamed somewhere in the process of be re-released under the GPL.

---

### Post by highspider on 2011-04-06
> **SeijiSensei said:**
> Distro maintainers have to decide which packages are necessary for that distribution's purposes and which left for later download. 
...
[COLOR=RoyalBlue]In short, if I were packaging the server version of Ubuntu, the two programs I'd definitely want to add to the current distro are alpine and bsd-mailx[/COLOR].  The latter I use mostly for testing email services from the command line and to send notices from routine scripts [COLOR=Red]running from cron[/COLOR].

[COLOR=Red]RED[/COLOR]| With Cron filling up --- /var/mail/root && /var/mail/www-data  and only "so much" I can find out with tail -f /var/log/syslog...  ahha what does that message say.  Great new server. (and myself server newbie)  no way to read it.
(why asked for help -- note: its solved now)

[COLOR=Blue]BLUE[/COLOR]| agreed!  
heirloom-mailx (bsd mailx) [COLOR=Blue]is 717kB[/COLOR] and alpine [COLOR=Blue]is 6,586kB[/COLOR]
(IDK compressed or not size) this was size with apt-get After this operation, SIZE used

> **HermanAB said:**
> Mutt.
Otherwise, if you are a hard core command line fanatic, use telnet.
Yeap I sure Am - just for fun
```
 
[FONT=Arial][SIZE=2][COLOR=Black]telnet alt4.gmail-smtp-in.l.google.com 25
[B]helo mailhost
[/B][B]mail from: [EMAIL="lonleylinuxguy@google.com"]lonleylinuxguy@wishfulthinking.com[/EMAIL]
[/B][B]rcpt to: [EMAIL="mygirlfreind@hopefullysomeday.com"]mygirlfreind@hopefullysomeday.com[/EMAIL]
[/B][/COLOR][/SIZE][/FONT][B][FONT=Courier New][COLOR=Black][FONT=Arial][SIZE=2]data
  When I see you. Your not like my other girls. Your real,
 and so not like animated pixels light on my monitor
.[/SIZE][/FONT]
[/COLOR][/FONT][/B]
```**[FONT=Courier New][COLOR=Black]message sent[/COLOR][/FONT]**
warning for other readers - you can really [FONT=Arial][SIZE=2][COLOR=Black]telnet alt4.gmail-smtp-in.l.google.com 25[/COLOR][/SIZE][/FONT] 
and the commands would work.  its safe to use for fun but messages will most likely
end up getting dropped as spam by rcpt. I think my commands or correct.  port 25 out from my home is blocked by my ISP. so I couldn't verify it.  (not block at work server)

thank U guys

---

