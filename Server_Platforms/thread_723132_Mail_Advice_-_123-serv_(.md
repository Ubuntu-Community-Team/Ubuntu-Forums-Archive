---
title: "Mail Advice - 123-serv :("
date: 2008-03-13
forum: Server Platforms
---

### Post by kaiten101 on 2008-03-13
Hi
 I have a server from the wonderfully cheap, (albeit terrible) 123-serv.co.uk  I'm trying to set it up as a mail server but they appear to be running a process outside of my control on port 25, seems to be tcpserver / qmail prcoess that I cant kill off

If I kill tcpserver or qmail process they simply respawn, nowhere on the box can I locate these files, so my 'root' access is definatly not true root access.

What I'm after is any suggestions (other than a new ISP) of how I can either kill off these process, or how I can best make use of them and route mail out over there processes using my own.  I got as far as installing the following before realising that I wasnt truly root on the box.

/etc/init.d/courier-imap-ssl
/etc/init.d/courier-imap
/etc/init.d/courier-authdaemon
/etc/init.d/postfix
/etc/init.d/postgrey
/etc/init.d/amavis
/etc/init.d/spamassassin
/etc/init.d/clamav-daemon
/etc/init.d/clamav-freshclam


It all sems to work, however postfix of course has been beaten to port 25 by a process that wont die :(


Any ideas welcomed!

Thanks

---

### Post by SpaceTeddy on 2008-03-13
```
killall -9 postfix
/etc/init.d/postfix stop
```

would be my guesses... but you tried them already ?

---

### Post by kaiten101 on 2008-03-14
Yup, tho I want to use postfix, its tcpserver and qmail I cant killall :( - just keeps respawning from its hidden area on the server.



qmaild    8976  0.0  0.0    124    44 ?        S    Mar13   0:00 tcpserver -v -R -l 0 -x /etc/qmail/tcp.smtp.cdb -c 20 -u 71 -g 71 0 smtp qmail-smtpd smtp.donhost.co.uk /var/qmail/bin/smtpcheckpasswd.pl /bin/true
qmaild    8980  0.0  0.0    124    48 ?        S    Mar13   0:00 tcpserver -v -R -l 0 -x /etc/qmail/tcp.qmqp.cdb -c 20 -u 71 -g 71 0 628 qmail-qmqpd
root     13462  0.0  0.0    120    40 ?        S    Mar13   0:00 tcpserver -vDRHl0 -x /usr/local/djbdns/var/axfr.access.cdb -- 0 53 /usr/local/bin/axfrdns

---

### Post by hyper_ch on 2008-03-14
uninstall qmail

---

### Post by kaiten101 on 2008-03-14
Can't as the supposed root isnt really root (chroot ??) I cant access the qmail install

---

### Post by leewilson78 on 2008-03-23
Did you figure this out, I too have a 123-reg serv, I want to do away with qmail and run postfix.

Lee

---

### Post by leewilson78 on 2008-03-23
Ok, been scratching my head over this for hours, came to the conclusion that 123-reg want full control over the email side of things, probably to encourage you to purchase their own spam filter.

Trying to make good of a bad situation and trying to add spam filters to qmail.

---

### Post by ikonia on 2008-03-23
FYI: 

qmail runs from inittab so every time you kill qmail/tcp server it will re-spawn. to disable it qmailctl stop should stop it - not remove it, or remove the "supervise" entries from your iniittab.

---

### Post by Rmantingh on 2008-03-29
You're right that you are not running as 'true' root. You're in a so-called chroot-jail which runs a 'virtual' system from a sub-directory.
I'm not an expert here so don't ask me too many difficult questions but there are ways to 'break' out of jail - as it were.
Just do a search on the internet.

DISCLAIMER: Doing so may break the terms of your contract with your hosting provider! It's probably better to address the issue with them first and see whether they are willing to give you 'full' root access.

---

### Post by Oldsoldier2003 on 2008-03-30
Of course you do realize that if you do this and get caught you will very likely be terminated. No service provider is likely to look kindly upon circumventing security on their system

If you do this i hope you haven't got a lot of time left on your contract because in effect you've just told them "cancel my hosting contract without a refund please."  :)

---

### Post by leewilson78 on 2008-03-30
Hi all, 

I have since received a response to a ticket to 123-reg about the matter, they say they can provide true root access for me, but that they will then not provide any software support or updates.... seems fair to me.

Thanks for the help.

Lee

---

### Post by Oldsoldier2003 on 2008-03-30
> **leewilson78 said:**
> Hi all, 

I have since received a response to a ticket to 123-reg about the matter, they say they can provide true root access for me, but that they will then not provide any software support or updates.... seems fair to me.

Thanks for the help.

Lee

Yep, but honestly any help you get from them would be easily replaced by help from these forums :) Well other than flipping the power switch...

---

### Post by Rmantingh on 2008-03-30
> **Oldsoldier2003 said:**
> Of course you do realise that if you do this and get caught you will very likely be terminated. No service provider is likely to look kindly upon circumventing security on their system

If you do this i hope you haven't got a lot of time left on your contract because in effect you've just told them "cancel my hosting contract without a refund please."  :)

Of course if that happens I would sue them!
In the contract it says that once I've requested 'root access' I'm on my own anyway and will be responsible for my own security and maintenance of the system. How can I do that without having access to the full system? No, I don't think they have a case.
My jailed system is already upgraded to Gutsy but the 'outside world' - if you like - is still based on Dapper and I have already had to do done an upgrade on that one.
I will ask them about the situation though. I agree that it's best done with mutual consent.

---

### Post by Oldsoldier2003 on 2008-03-30
> **Rmantingh said:**
> Of course if that happens I would sue them!
In the contract it says that once I've requested 'root access' I'm on my own anyway and will be responsible for my own security and maintenance of the system. How can I do that without having access to the full system? No, I don't think they have a case.
My jailed system is already upgraded to Gutsy but the 'outside world' - if you like - is still based on Dapper and I have already had to do done an upgrade on that one.
I will ask them about the situation though. I agree that it's best done with mutual consent.

yes their AUP states that any attempt to breach the security of any of their machines will result in termination. I don't know what they consider breaking chroot jail, but I would think they could use that as a justification to breach your contract.

---

### Post by birdwes on 2008-07-23
I can confirm that the method on [http://www.bpfh.net/simes/computing/chroot-break.html](http://www.bpfh.net/simes/computing/chroot-break.html) works on the 123-reg servers.

We did this on the last day of the contract to ensure that the box was left free from our data.

I am sure that it would leave you in an unsupported position if you do this though.  It's easier to move to another server provider.

---

