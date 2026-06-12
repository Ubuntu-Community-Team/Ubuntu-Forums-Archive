---
title: "How can I create an Email server?"
date: 2007-09-19
forum: Server Platforms
---

### Post by grs on 2007-09-19
I've got a network at school, where I work, using Windows Server 2003 on the network server and all the class rooms are use Windows XP with one slow internet access.
Some of the teachers would like to be able to send messages/information to the student via computers. How can I setup an email server?

There are some limitations due to our buget and internet provider so I would like to just keep it internal for now, that is there is no need for people to be able to recieve message from outside the school network.

I'm only new to network management and rather than tinkering with the hardware/software there and making a mess of it I was thinking I could make up a machine from old hardware and experiment. Is there anything Linux based that I can load into the machine to control and manage emails for 700 or so accounts?

I have a number of other qeustions, but I'll deal with this much first.

---

### Post by esaym on 2007-09-19
I would run postfix and dovecot:

[https://help.ubuntu.com/community/Postfix?highlight=%28postfix%29](https://help.ubuntu.com/community/Postfix?highlight=%28postfix%29)

[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/email-services.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/email-services.html)

With 700 users, you are probably going to have to set up postfix with virtual mailboxes so that the users can create their own user names and passwords because I am sure you don't want to sit at a computer and type 700 users worthy of info.

[https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto](https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto)

I have never done the virtual stuff, sorry I can't help you much there.

---

### Post by HermanAB on 2007-09-19
Hmm, Windows 2003 should have a SMTP and POP server built in.  So you could start that up.  It is nothing fantastic and has no spam or virus filters but it works.

Otherwise, I'd like to refer you to Citadel: [http://www.citadel.org](http://www.citadel.org).  This system is incredibly easy to install and it provides great features for a school.  It can work with standard mail clients like Outlook or Thunderbird, but it really comes into its own when used through a browser, since then you have chat, discussion boards, calendars and whatnot.

Here is a guide - but you almost don't need a guide: [http://aeronetworks.ca/citadel-howto.html](http://aeronetworks.ca/citadel-howto.html)

The only tricky part is installing SpamAssassin and ClamAV.  If you have trouble with that, drop me a line.

Cheers,

H.

---

### Post by HermanAB on 2007-09-19
BTW, a big advantage of Citadel is that it uses a Berkeley database to store the mail.  So if someone sends a message with a 100MB word file attached to the whole school, then you don't have to  run out to buy a new bigger disk drive, since it will only store ONE copy of the message!

Citadel is very efficient and can run happily on a low power machine.

Cheers,

H.

---

### Post by grs on 2007-09-20
I know about Win 2003's email ablity, I still have to look at it but I'm only new to network management so I didn't want to tinker with it too much by keeping it in a seperate machine.
I was also trying to keep the messaging server internal, our internet provider is very poor.
Do you need a static IP to run an email server correctly? I know about NoIP but do they allow business's to use there service for free?

---

