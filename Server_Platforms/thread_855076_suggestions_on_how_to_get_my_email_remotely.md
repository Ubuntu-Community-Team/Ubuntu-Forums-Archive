---
title: "suggestions on how to get my email remotely?"
date: 2008-07-10
forum: Server Platforms
---

### Post by beaker15 on 2008-07-10
Hello
I have an ubuntu server with postfix running as a mail server on it. Basically i want to be able to get my emails from home and thought someone must have done this before and could help me with the best way to achieve it. Currently the mail in the postfix mailboxes is downloaded to the users thunderbird profile (also stored on the server), but i'm open to suggestions if there is a better way. Is there a way to do it via a web browser? (like MS Outlook web access)

thanks

---

### Post by carcdrcdr on 2008-07-10
Well it depends on how you want to do this ;)  We can go one or all of 2 routes:
- Do it via SSH
- Do it via HTTP(S)

To do it via SSH:
If you do not have OpenSSH Server installed already install it now.
```
sudo apt-get install openssh-server
```

Then install a text based mail client.  My fave is alpine.  I dont think I could ever use another mail client ever again (it kills me to have to touch outlook).

To install that:
```
sudo apt-get install alpine
```

Now just ssh to your sever and type:
```
alpine
```

Vola!  Keep in mind that to use SSH you must have port 22 open to the outside world on your router and your local machine.

You could also install mutt... but Im not much of a fan.  There is also the standard "mail" and "mailx" commands too.  If you do some searching you will find others.

I suggest keeping a copy of PuTTY on a USB drive so you can check your mail on public terminals and such.

-------

> Is there a way to do it via a web browser? (like MS Outlook web access)

Well no there is a better way, MS Outlook web access is a joke ;)

As for doing it over the web I recommend squirrel mail.
Squirrel mail is light weight, but hey it ain't no stinking oUtl00k.

Full instrucions on setting up Squireel ail can be found: [https://help.ubuntu.com/community/Squirrelmail](https://help.ubuntu.com/community/Squirrelmail)

---

### Post by highonv8splash on 2008-07-10
we use horde for webmail, it's a great webmail app. If you're interesting in testing around for what you like best, [http://roundcube.net/](http://roundcube.net/) is a really cool piece of software too, but still in earlier stages of development.

---

### Post by k_grdn on 2008-07-10
Hi,

Safest option:
 
Depending you have ssh or putty on the connecting client:

smtp:
ssh -L 25:127.0.0.1:25 your_mail_server_ip

pop:
ssh -L 110:127.0.0.1:110 your_mail_server_ip

imap:
ssh -L 143:127.0.0.1:143 your_mail_server_ip


Or your could always allow postfix to accept connections from your remote client sasl over tls.

Regards,

k_grdn

---

### Post by beaker15 on 2008-07-15
thanks for the replies. The webmail approach is looking less like an option because I need to be using thunderbird on my machine and when i click 'get mail' it gets my messages. I tried making a putty tunnel through to the remote network and after a while mangaged to connect to the samba share where I have the Thunderbird profiles. Then in Thunderbird's settings, pointed to that share for the profile location. This seemed to me like a great idea and did work at first but it didn't work very well. Any more suggestions? a text based/ command line solution is not an option either

---

