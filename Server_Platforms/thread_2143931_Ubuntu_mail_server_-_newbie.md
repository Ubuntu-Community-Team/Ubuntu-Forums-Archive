---
title: "Ubuntu mail server - newbie"
date: 2013-05-10
forum: Server Platforms
---

### Post by CatorAde on 2013-05-10
hi all,

how is everyone? im new to ubuntu, i took the plunge about a week ago on my main PC, bye to win 7 and went over to Zorin, which i absolutly love, because of this i thought i would setup my server with ubuntu also.
the server so far has been setup with 2 domains hosted on it, and all is going well, so my next step is to get a mail server installed, after a lot of searching and about a day of reading tutorials, im still at a loss,
i want emails for multiple domains (which are being hosted, theres 2 atm but i will be hosting a 3rd shortly)

ive gone through a couple of the tutorials ive read and they havent worked, either files are missing or they are not very clear on where to insert new code in conf files, 

has any one done what im trying to do? if so could someone point me in the direction of a good working tutorial :)

many thanks in advance 

Ade :)

---

### Post by CatorAde on 2013-05-10
[COLOR=#000000]hi all,[/COLOR]

[COLOR=#000000]how is everyone? im new to ubuntu, i took the plunge about a week ago on my main PC, bye to win 7 and went over to Zorin, which i absolutly love, because of this i thought i would setup my server with ubuntu also.[/COLOR]
[COLOR=#000000]the server so far has been setup with 2 domains hosted on it, and all is going well, so my next step is to get a mail server installed, after a lot of searching and about a day of reading tutorials, im still at a loss,[/COLOR]
[COLOR=#000000]i want emails for multiple domains (which are being hosted, theres 2 atm but i will be hosting a 3rd shortly)[/COLOR]

[COLOR=#000000]ive gone through a couple of the tutorials ive read and they havent worked, either files are missing or they are not very clear on where to insert new code in conf files, [/COLOR]

[COLOR=#000000]has any one done what im trying to do? if so could someone point me in the direction of a good working tutorial [/COLOR]:smile:

[COLOR=#000000]many thanks in advance [/COLOR]

[COLOR=#000000]Ade [/COLOR]:smile:

---

### Post by darkod on 2013-05-10
There are "prepared solutions" like Zimbra or iRedmail which will install all for you. iRedmail will even install OpenLDAP for the user data. But if you already have apache2 running live websites on the same machine, I don't know if the install process will touch some of your existing apache2 settings.

For example, if I'm not wrong iRedmail install instructions recommend it's best to run it on a "brand new" server, without anything else already installed.

[http://www.zimbra.com/](http://www.zimbra.com/)
[http://www.iredmail.org/](http://www.iredmail.org/)

Note that they both have commercial paid versions, but also free oepn source versions.

Apart from that, if you want to give postfix with virtual domains and virtual mailboxes a shot, this is one tutorial that I recently followed and it worked more or less as it is:
[http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-12.04-lts](http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-12.04-lts)

The mailbox quota part I skipped since there was still no patch for the latest postfix version but if you don't care about that it doesn't matter.

---

### Post by linuxtechguy on 2013-05-10
You should start here [https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)

---

### Post by sandyd on 2013-05-10
Ive used both iRedMail and Zimbra (which im using right now).

I dont use Zimbra and apache on the same server because I use VMs (KVM) with my server, so I dont have experience setting up Zimbra and apache on the same server, but here is a nice guide on how to accomplish this -> [http://wiki.zimbra.com/wiki/ZimbraApache](http://wiki.zimbra.com/wiki/ZimbraApache)

iRedMail will need a bit of tuning to get working with Apache.
Initially, iRedMail adds a alias in /etc/apache2/conf.d (which affects ALL Apache VirtualHosts). Unless you want roundcube/iredadmin to be openable with every virtual host, ou will have to migrate that so that it is in the VHost that you want to use for mail administration

---

### Post by sandyd on 2013-05-10
Oh, and **Threads Merged**
Please do not create multiple threads on the same topic as it dilutes community effort.

Thanks!

---

### Post by CatorAde on 2013-05-11
> **sandyd said:**
> Oh, and **Threads Merged**
Please do not create multiple threads on the same topic as it dilutes community effort.

Thanks!
Hiya,
sorry for double post, i wasn't sure which forum to post in.

i would like to do things myself, but ive spent 2 days on it now and cannot really spend anymore time on it, as i want to do more with my server.

# iredmail or Zimbra
will these have a web-based login?

many thanks for your replies :)

---

### Post by darkod on 2013-05-11
If you mean webmail, yes, they do have it. They also have web based administration interface. You can administer the accounts/mailboxes that way.

---

### Post by CatorAde on 2013-05-11
ok thanks, after another 4 hours of not seeming to get anywhere (with installing manually) im trying to install iRedMail
does anyone know how to do this on apache2?

---

### Post by darkod on 2013-05-11
As we already mentioned, iredmail requires installation on brand new OS. It will probably trash your existing apache anyway. It will install everything it needs.
 
If you intend to keep the apache you have working, I'm not sure how to do that. Your google search will be as good as mine I guess.

---

### Post by CatorAde on 2013-05-12
hi guys,
i tried iredmail, and yes it did trash my apache, so i reinstall ubuntu server and the iredmail, but with still no luck :/, i also followed the howtoforge tutorial, but again to no avail :/ i have followed several tutorials, but nothing, is the mail server that difficult to setup then?
or does anyone know of any other tutorials or packages i could try?
many thanks
Ade

---

### Post by darkod on 2013-05-12
I can't speak about iredmail since I haven't tried it yet. I am getting ready to try it in a few weeks. But their instructions seem very simple.

I did use that howtoforge tutorial I posted about a month ago and it worked first time. Is there a particular thing not working for you? Particular problem?

Mailserver is not difficult to set up at all. If you don't need virtual domains and virtual mailboxes you don't even need that howtoforge tutorial. Simply installing postfix and dovecot in most cases makes a working mail server by default. I have also tried that with a local domain (not a public one). But it worked right away.

---

### Post by CatorAde on 2013-05-12
maybe im over thinking it :/
what i want to do is host multiple websites on my server (my work one and my hobby one, and maybe a blogging 1 etc)
ive followed some tutroials and have setup webserver nicely, and using virtual hosting, seems like i can host as many as i want,

maybe i will try that tutorial again, maybe i missed something (sounds about right for me haha)

do you think that tutorial will allow me to have multiple users depending on domain
eg [email]ade@cfa.co.uk[/email] and [email]ade@rcnitro.co.uk[/email]?

thanks again :)
gotta say, even though im having troubles, i still prefer ubuntu to windows :)

---

### Post by darkod on 2013-05-12
Yes, that's the point of using postfix with so-called virtual domains and virtual mailboxes. Plus all mailboxes are separate. For example, you can have [EMAIL="user1@domain1.com"]user1@domain1.com[/EMAIL], [EMAIL="user2@domain1.com"]user2@domain1.com[/EMAIL], [EMAIL="user1@domain2.com"]user1@domain2.com[/EMAIL] and [EMAIL="user2@domain2.com"]user2@domain2.com[/EMAIL]. The mails get delivered to separate mailboxes not simply to the same user1 but also to different mailboxes according to the domain. So, it's easy to have them separate and reply to received emails with the same address they were sent to.
Also you can caonfigure forwardings and catch-all mailboxes to help you organize the flow of mails the way you want it.

---

### Post by CatorAde on 2013-05-12
aahh right, interesting :)
update:- im following the tutorial link you sent me at the beginning of this thread, and alot more seems to be happening this time round, not sure how, maybe i missed out a vital line of code or something!? fingers crossed :)

---

### Post by snathan99 on 2013-05-13
Here is my setup: [http://tech.snathan.org/tech/linux/mail_server_setup](http://tech.snathan.org/tech/linux/mail_server_setup)

I took a bit to get it all together when I reinstalled ubuntu 12.04 (migrating from 8).  This has been running well for a while now.  You could tone down the spam protection if you like, but other than that, this should work great.

---

