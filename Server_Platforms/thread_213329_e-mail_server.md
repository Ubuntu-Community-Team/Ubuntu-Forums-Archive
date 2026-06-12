---
title: "e-mail server"
date: 2006-07-11
forum: Server Platforms
---

### Post by Isoss on 2006-07-11
Hello

This might look like a big question but at least I need to go a level up in my "humble servers knowledge". I am a php programmer, and I have a very simple "e-mail client" ( or at least that's how I'd like to call it ) which retrieves the information submitted by users through the contact us form in my website and replies back using mail function in php. my "e-mail client" which I have access to it through my special admin page really looks like an ordinary e-mail inbox, which displays the sender, subject, date, read, unread and has a reply back and delete and some other funcitons. So it's so simple, but since I have it like a client "which has no server" because it only retrieves info from db that's all! I mean there is no [email]user@server.com[/email] to recieve emails from other e-mail clients or forms. So, this made me wanna ( not neccesserily create ) but more to know about how e-mail servers work and protocols and what should one have or do in order to create one. I mean, how [email]user@server.com[/email] can recieve sent info and place them in the DBs and so when [email]user@server.com[/email] signs in can display the sent info ... 

Please consider me knowing nothing so I hope if someone's there to explain   I hope he/she'd start from ABC. And I'll also appiciate it if you'd recommend some HOWTO to try something like that on linux machines on a local network.

Thanks.

Isos

---

### Post by thingy on 2006-07-11
This may not be the step by step info. you want, but it might be interesting to you:

[http://www.devshed.com/c/a/PHP/Building-A-PHPBased-Mail-Client-part-1/](http://www.devshed.com/c/a/PHP/Building-A-PHPBased-Mail-Client-part-1/)

By the way, did you want to create an e-mail server? or an e-mail client...I assumed client hence the link above.

---

### Post by venzen on 2006-07-11
Well, ye, this is a big question because you want to develop (from scratch) an email server and client relationship. I think this is very interesting altho' I know very little about this particular topic. I would recommend that you look at an existing mail server such as postfix which has a MySQL module - which I believe stores emails in the MySQL database - which then makes manipulation via PHP possible. So maybe you should study postfix's use MySQL (google for this and also check [http://tldp.org]("http://tldp.org") for a HOWTO) and then write some PHP code to retrieve, display and manipulate mails.

Could you post a screenshot of your client window? This would help readers see what you're talking about.

---

