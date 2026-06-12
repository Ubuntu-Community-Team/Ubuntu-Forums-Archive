---
title: "[Howto] Setup irssi and join #ubuntu on Freenode"
date: 2008-12-14
forum: Tutorials
---

### Post by andrew.46 on 2008-12-14
I am both a student and a huge fan of the Internet Relay Chat (IRC) program irssi. This brief guide aims to give just a *starting point* for any like me who are keen to explore this amazing program. I shall do this by demonstrating how to install irssi and some scripts, connect to Freenode with SSL and then access the #ubuntu channel. The guide has most recently been tested with irssi 0.8.15 and Natty Narwhal but should work, perhaps with some small modifications, for most Ubuntu releases.

**Getting started ...**

One important point in this guide is that where you are required to fill in your *own* details for such things as passwords, email addresses etc I will mark the area this way: **[COLOR="Red"]<password>[/COLOR]**. Change this for your *own* details and *omit the brackets* in all cases. First let us download some required files from the repository using the following *single* command:

```

sudo apt-get -y install irssi irssi-scripts ca-certificates \
libcrypt-blowfish-perl libcrypt-dh-perl libcrypt-openssl-bignum-perl \
libmath-bigint-gmp-perl

```

This will only be a small download, now start the program as follows:

```
irssi 
```

You should then see the following screen:

```

10:24 -!- Irssi: Looks like this is the first time you've run irssi.
10:24 -!- Irssi: This is just a reminder that you really should go read
10:24 -!- Irssi: startup-HOWTO if you haven't already. You can find it
10:24 -!- Irssi: and more irssi beginner info at http://www.irssi.org
10:24 -!- Irssi: 
10:24 -!- Irssi: For the truly impatient people who don't like any automatic
10:24 -!- Irssi: window creation or closing, just type: /MANUAL-WINDOWS
10:24 -!- Irssi: 
10:24 -!- Irssi: For Ubuntu specific help type "/connect irc.ubuntu.com"
10:24 -!- Irssi: and "/join #ubuntu" (without the quotes) and ask your
10:24 -!- Irssi: question.

```

Well that never makes a great first impression does it? Never fear we are now going to make things a little friendlier:

**Connecting to Freenode and #ubuntu ... **

No doubt like most people (including me) you will ignore the polite note in this opening window encouraging you to first read some of the irssi documentation. At some stage I would suggest that this would be an excellent idea and perhaps sooner rather than later. So to start we need to set a nick, usually a pithy and fairly cool one, and your real name, don't forget to use your own details for <nick> and <Real Name>:

```

/set nick **[COLOR="Red"]<nick>[/COLOR]** 
/set real_name **[COLOR="Red"]<Real Name>[/COLOR]**
 
```

Then manually connect to Freenode as follows:

```
/connect irc.freenode.net 8001 
```

This connects and then to manually join #ubuntu simply run the following:

```
/join #ubuntu 
```

And there you are in the thick of it, a very busy channel and a little chaotic too. For the moment we will leave this channel:

```
/leave Put your witty parting shot here!! 
```

This closes the active channel but leaves us still connected to Freenode so we can complete the setup.

** Register with Freenode ... **

It is a very good idea to formally register your nick with Freenode and it is easy enough to do. Don't forget to substitute your own details here:

```

/msg nickserv REGISTER **[COLOR="Red"]<password> <email>[/COLOR]**

```

NickServ will send an email to your email address with copy and paste instructions to verify you nick details. So your email address is not obvious to all users (although this setting is usually the default) then issue the following command:

```
/msg NickServ SET HIDEMAIL ON 
```

It is not mandatory but often a good idea to create an alternate nick and then *group* this with your account. So while logged on with your primary nick run the following:

```

/nick **[COLOR="Red"]<alternate_nick>[/COLOR]** 
/msg nickserv group

```

Finally check your setup with the following command:

```

/msg nickserv info

```

And that is the basics of our dealings with Freenode registration, although I would suggest that after 4 weeks you go to #freenode and ask for an [unaffiliated cloak]("http://freenode.net/faq.shtml#cloaks") to shield your IP details from the curious. But now to automate the irssi connection and both connect with SSL and secure your password exchange with SASL.

** Automatically connect with SSL/SASL ... **

For the most secure connection it is best to connect with SSL and then shield the password verification with SASL. First to setup the Freenode sasl perl script with the following *single* command:

```

mkdir -pv $HOME/.irssi/scripts/autorun && cd $HOME/.irssi/scripts && \
wget http://freenode.net/sasl/cap_sasl.pl && \
cd autorun && ln -sv ../cap_sasl.pl

```

Now load the script manually and add in the required settings:

```

/script load cap_sasl.pl
/sasl set Freenode [COLOR="Red"]**<primary-nick> <password>**[/COLOR] DH-BLOWFISH
/sasl save
/save

```

Finally set irssi to automatically make an SSL connection to Freenode on startup and then automatically log on to #ubuntu:

```

/network add Freenode
/server add -auto -ssl -ssl_verify -ssl_capath /etc/ssl/certs -network Freenode irc.freenode.net 7000
/channel add -auto #ubuntu Freenode
/save
/exit

```

Perhaps you should also cross your fingers when you restart irssi? If all is well you will see +Zi in the bar at the base of the irssi window and in the irssi connection dialogue you should also see something like the following:

```

10:51 -!- Irssi: SASL authentication successful

```

If all is not well retrace your steps and see if you can spot a problem. If however all is well close your chat windows with */leave*, close irssi using the */exit* command and continue on as we add a few scripts to make life a little more pleasant with this great irc application.

** Add a few more scripts ... **

I will now demonstrate how to automatically load scripts both from the Ubuntu script pack as well as from external sources. Two great scripts are 'scriptassist.pl', which enables easy installation and upgrade of scripts, and 'mouse.pl' which allows some use of mouse in irssi. These are part of the Ubuntu script pack and can be automatically loaded using the following *single* command:

```

cd $HOME/.irssi/scripts/autorun && \
ln -sv /usr/share/irssi/scripts/scriptassist.pl && \
ln -sv /usr/share/irssi/scripts/mouse.pl

```

The syntax for scriptassist can be seen by typing in '/scriptassist help' in the opening irssi window. Plenty more scripts to explore in this script pack! I demonstrate also how to download a couple of external scripts. 'adv_windowlist.pl' allows easier navigation of multiple channel windows while 'hack-whois-in-current-window.pl' shows the '/whois' window in the current window. The following is a *single* command:

```

cd $HOME/.irssi/scripts && \
wget http://anti.teamidiot.de/static/nei/*/Code/Irssi/adv_windowlist.pl && \
wget http://dgl.cx/irssi/hack-whois-in-current-window.pl && \
cd autorun && \
ln -sv ../adv_windowlist.pl && \
ln -sv ../hack-whois-in-current-window.pl

```

Details of well-written scripts can be seen by opening them with your favourite text editor and following the instructions printed within. Plenty of scripts to explore and perhaps you might even consider writing a few yourself?

** And in conclusion ... **

Experienced users of irssi and IRC know that I have omitted many, many areas that enhance the experience of using this great program. However hopefully I have furnished a strong starting point for inexperienced users who will subsequently explore the program a little more fully. Please feel free to ask questions in this thread if there are problems or suggestions for improvement with this guide. And remember "Have Fun!!".

Andrew Strong
March 18, 2011

---

### Post by Voorhees1979 on 2008-12-17
Is there a blow fish for this?

---

### Post by andrew.46 on 2008-12-17
Hi Vorhees,

> **Voorhees1979 said:**
> Is there a blow fish for this?

Lots of discussion here:

[http://fish.sekure.us/forum/viewforum.php?f=3](http://fish.sekure.us/forum/viewforum.php?f=3)

but this is a little beyond the scope of this short guide.

All the best,

  Andrew

---

### Post by Lividity on 2008-12-23
great guide andrew ty very much

---

### Post by andrew.46 on 2008-12-24
Hi Lividity,

> **Lividity said:**
> great guide andrew ty very much

It is my pleasure! I hope to see you on irc :-).

  Andrew

---

### Post by kevdog on 2008-12-24
Do not like #ubuntu, but other forums are great.

---

### Post by andrew.46 on 2009-03-23
Hi Voorhees,

> **Voorhees1979 said:**
> Is there a blow fish for this?

Looks like a script has appeared on [the irssi website]("http://scripts.irssi.org/") called 'bl**job.pl' (my apologies for the name where I have substituted '**' for 'ow'!):

> 
Crypt IRC communication with blowfish encryption. Supports public #channels, !channels, +channel, querys and dcc chat. Roadmap for Version 1.0.0 is to get some feedback and cleanup. Join #blowtest on freenode (irc.debian.org) to get latest stuff available. Note to users upgrading from versions prior to 0.8.5: The blowjob.keys format has changed.


Would this be what you are after?

Andrew

---

### Post by ayeizajedi on 2009-04-03
Thanks for the post, been a while since i used irssi and your post really helped.

---

### Post by andrew.46 on 2009-04-03
Hi ayeizajedi,

> **ayeizajedi said:**
> Thanks for the post, been a while since i used irssi and your post really helped.

My pleasure :-).

Andrew

---

### Post by andrew.46 on 2009-06-24
Having been prompted by a pleasant gentleman on #ubuntu-irc I modified my *own* irssi setup to include an alternate nick and then grouped the nicks. Subsequently altered this guide to include these details :-).

Andrew

---

### Post by andrew.46 on 2009-07-11
Added a few details concerning picking up an *unaffiliated* cloak from Freenode.

Andrew

---

### Post by Jaraxle on 2009-09-24
Excellent guide! I set up irssi and am loving it.

---

### Post by andrew.46 on 2009-09-24
Hi Jaraxle,

> **Jaraxle said:**
> Excellent guide! I set up irssi and am loving it.

Great news! Once irssi is all setup and you have learned a few basic commands I suspect you will wonder why you did it any other way :).

Andrew

---

### Post by Soul-Sing on 2010-02-07
Hi Andrew how to set up irssi with SSL support, i understand you have to install a perl script to makes this work on irssi?
(cap_sasl pl)
i tried: ```
/server add -auto -ssl -network freenode irc.freenode.net 7000
```
but with no succes.

---

### Post by andrew.46 on 2010-02-09
Hi leoquant,

> **leoquant said:**
> Hi Andrew how to set up irssi with SSL support, i understand you have to install a perl script to makes this work on irssi?
(cap_sasl pl)

Not the most straightforward thing to do as it turns out, but I have managed it on SLackware and now on Ubuntu. I will spare you the horrors of the Slackware installation as I had to download, compile and install several perl modules and hunt around for a cert pack..... But for Ubuntu the SSL connection is pretty straightforward. First you will need the ca-certs:

```
sudo apt-get install ca-certificates
```

and then the command to logon to the Freenode ssl port as well as check the certificate is:

```
/server add -auto -ssl -ssl_verify -ssl_capath /etc/ssl/certs -network freenode irc.freenode.net 7000
```

This will give you the SSL connection (and the +Zi) but if you want to get an sasl connection for your password to go to nickserv it gets a little thornier. First you will need the additional perl modules I had to painfully scrape together with cpan2tgz:

```
sudo apt-get install libcrypt-blowfish-perl libcrypt-dh-perl libcrypt-openssl-bignum-perl libmath-bigint-gmp-perl
```

and then grab the perl script from Freenode:

```

$ cd $HOME.irssi/scripts/
$ wget http://freenode.net/sasl/cap_sasl.pl
$ cd autorun
$ ln -s ../cap_sasl.pl

```

Then load up irssi again and run:

```

/sasl set freenode <primary-nick> <password> DH-BLOWFISH
/sasl save
/save

```

making the obvious substitution for *<primary-nick> <password>*. Next login should show something like:

```

19:09 -!- Irssi: Looking up irc.freenode.net
19:09 -!- Irssi: SASL: auth loaded from /home/andrew/.irssi/sasl.auth
19:09 -!- Irssi: Connecting to irc.freenode.net [130.237.188.200] port 7000
19:09 -!- Irssi: Connection to irc.freenode.net established
19:09 !lindbohm.freenode.net *** Looking up your hostname...
19:09 !lindbohm.freenode.net *** Checking Ident
19:09 !lindbohm.freenode.net *** Found your hostname
19:09 !lindbohm.freenode.net *** No Ident response
19:09 -!- Irssi: CLICAP: supported by server: identify-msg multi-prefix sasl 
19:09 -!- Irssi: CLICAP: requesting: multi-prefix sasl
19:09 -!- Irssi: CLICAP: now enabled: multi-prefix sasl  
19:09 -!- andrew_50!andrew@unaffiliated/andrew50/x-1857826 andrew_50 You are 
          now logged in as andrew_50.
**[COLOR="Blue"]19:09 -!- Irssi: SASL authentication successful[/COLOR]**
19:09 -!- Welcome to the freenode Internet Relay Chat Network andrew_50

```

and that should be it :). This is a little too complex for the body of this guide, in particular because Freenode may change all of this soon or the next version of irssi might have native sasl support...

All the best,

Andrew

---

### Post by Soul-Sing on 2010-02-10
Thank you so much, after some testing i managed to get this to work, which is great.
(I had to do some/little modifications in ./irssi)

---

### Post by andrew.46 on 2010-02-10
Hi leoquant,

> **leoquant said:**
> Thank you so much, after some testing i managed to get this to work, which is great.
(I had to do some/little modifications in ./irssi)

Excellent news :). Now we just have to hope for native sasl support for irssi!

Andrew

---

### Post by andrew.46 on 2010-03-09
I have renovated this guide and tested on Karmic. More importantly I have added in all the necessary details for an SSL connection with Freenode + sasl encryption for the password exchange. Please let me know if any typos or inaccuracies have crept in :).

Andrew

---

### Post by Soul-Sing on 2010-03-19
> **andrew.46 said:**
> I have renovated this guide and tested on Karmic. More importantly I have added in all the necessary details for an SSL connection with Freenode + sasl encryption for the password exchange. Please let me know if any typos or inaccuracies have crept in :).

Andrew

It works also on 8.04.4. and Jaunty :)

---

### Post by andrew.46 on 2010-03-19
Hi leoquant!!!!

> **leoquant said:**
> It works also on 8.04.4. and Jaunty :)

I suspected as much but I have always preferred to only document what I have personally tested :).

Andrew

---

### Post by lukjad on 2010-03-23
> **andrew.46 said:**
> And there you are in the thick of it, a very busy channel and a little chaotic too. For the moment we will leave this channel and set things up a little better:

```
/leave Put your witty parting shot here!! 
```

This closes the active channel and leaves us to complete the setup.

Just a thought, shouldn't it be:

```
/leave #ubuntu Put your witty parting shot here!! 
```

Since that's the channel you want to part?

---

### Post by andrew.46 on 2010-03-23
Hi lukjad007!!!

Well you can certainly do that, although you note that I have specified the *active* window. Using the default irssi config /leave is actually an alias for the /part command, the help info for this command shows:

```

PART [<channels>] [<message>]
 
Parts from the current or specified channel. Depending on your settings, 
closes the corresponding window, too.

```

So either way is fine...

All the best,

Andrew

---

### Post by andrew.46 on 2010-04-16
Hi,

> **andrew.46 said:**
>  I will spare you the horrors of the Slackware installation as I had to download, compile and install several perl modules and hunt around for a cert pack..... 

Actually I have just written this up, so you are not spared after all :).

irssi and Slackware: Connecting to Freenode with SSL/SASL
[http://www.andrews-corner.org/irssi.html](http://www.andrews-corner.org/irssi.html)

Andrew

---

### Post by HpZ on 2010-06-19
hi, i don't use freenode or #ubuntu and i tried to set it up replacing freenode and #ubuntu with rizon and #NEWS but it didn't work. i get this error ```
Irssi: warning SSL handshake failed: unknown protocol

```

Help?

---

### Post by Soul-Sing on 2010-06-19
Freenode comes with this "protocol", not all other servers.

---

### Post by andrew.46 on 2010-06-20
Hi HpZ,

> **HpZ said:**
> hi, i don't use freenode or #ubuntu and i tried to set it up replacing freenode and #ubuntu with rizon and #NEWS but it didn't work. i get this error ```
Irssi: warning SSL handshake failed: unknown protocol

```

If you use the existing setup in this guide you should be able to make an SSL connection as I have done with the following:

```
/connect -ssl irc.rizon.net 9999
```

I attach a screenshot of my own ssl connection to rizon...

Andrew

---

### Post by syaoran87 on 2010-08-02
Hi andrew, I have followed your instructions to setting up irssi and it was really helpful! I'm very new to ubuntu and new to irssi as well. With regard to the ssl, must I download or create any script to enable ssl on rizon server? Also, I would like to ask how do you configure your dcc send, set up your trusted user list to allow trusted users to send stuff to you. Thanks a million!

---

### Post by andrew.46 on 2010-08-03
Hi syaoran,

> **syaoran87 said:**
>  With regard to the ssl, must I download or create any script to enable ssl on rizon server? 

I have not used that server except to test the connection and I did not have to use any script to do so.

> Also, I would like to ask how do you configure your dcc send, set up your trusted user list to allow trusted users to send stuff to you.

I have to disappoint you a little here as I have rarely used dcc and unfortunately I have no idea how to set up these :(. If nobody on this thread can help perhaps a question on #irssi might be in order?

Sorry,

Andrew

---

### Post by syaoran87 on 2010-08-03
Hi andrew,

It's no problem, I will check out with the people in #irssi. Thanks for the help!

---

### Post by andrew.46 on 2010-10-15
Good news I have just tested this guide under Maverick and it all works very well :). Might rewrite it over the next week or so as it was not terribly clear in places...

Andrew

---

### Post by daveg2 on 2011-01-21
Thanks for the tutorial, particularly the setup of SSL.  I take it without SSL that I'm <shudder> sending my password in plain text across the Internet?  Still thinking about changing the writeup a bit for Maverick?  If so, here's one that will appreciate it.  Thanks in advance!

---

### Post by andrew.46 on 2011-01-28
Hi daveg2,

> **daveg2 said:**
> Thanks for the tutorial, particularly the setup of SSL.  I take it without SSL that I'm <shudder> sending my password in plain text across the Internet?  Still thinking about changing the writeup a bit for Maverick?  If so, here's one that will appreciate it.  Thanks in advance!

I had thought that this guide had been forgotten so I was very pleased t see your message :). Rewrite is still pending, I am currently without an Ubuntu installation but that may change soon. SSL encrypts the connection between yourself and the irc server, sasl looks after the password exchange. I gather you can use SASL without the SSL setup but I have not experimented with this.

Andrew

---

### Post by norlane on 2011-03-01
Thankx for this guide and the effort
would be nice to see what default irssi 
settings you chane if any ie: [B]
Queries, [/B]**User information, ****Appearance, Statusbar **etc,

---

### Post by Soul-Sing on 2011-03-02
Hi andrew whats the difference between sasl and SSL,
i have three clients running via sasl now. Is nickserv in no way involved in the auth. proces?
how does freenode keeps the/your account alive after 60 days with no identif. to nickserver?

---

### Post by andrew.46 on 2011-03-05
> **norlane said:**
> Thankx for this guide and the effort
would be nice to see what default irssi 
settings you chane if any ie: [B]
Queries, [/B]**User information, ****Appearance, Statusbar **etc,

This guide has actually been somewhat neglected of late and in need of a rewrite, but it is good to see it has been useful to you :). I have to disappoint you I am afraid my copy of irssi is pretty unmodified... I have altered a theme a while back so the colours look ok and not really changed much else although I use a few scripts. I add a screenshot to demonstrate.

---

### Post by andrew.46 on 2011-03-05
Hey leoquant, good to hear from you again :).

> **leoquant said:**
> Hi andrew whats the difference between sasl and SSL,
i have three clients running via sasl now. Is nickserv is no way involved in the auth. proces?
how does freenode keeps the/your account alive after 60 days with no identif. to nickserver?

Indeed you made me a little worried as I have been connecting with SSL / SASL for quite some time now and the Freenode docs [are quite clear]("http://freenode.net/faq.shtml#userexpirations") about the possibilities of nicks being dropped after 60 days of non-use. However I believe that nickserv still *does* register your logon when using SSL / SASL in the manner that I have shown in this guide even though with irssi a nickserv window does not open. Proof can be seen by issuing the command:

```
/msg nickserv info <nick>
```

On my own system the results are:

```

19:58 <andrew_46> info andrew_46
19:58 >>> NickServ!NickServ@services.: Information on andrew_46 (account andrew_46):
19:58 >>> NickServ!NickServ@services.: Registered : Mar 18 02:51:30 2008 (2 years, 50 weeks, 2 
          days, 06:04:58 ago)
19:58 >>> NickServ!NickServ@services.: Last addr  : ~andrew@pdpc/supporter/active/andrew-46
19:58 >>> NickServ!NickServ@services.: vHost      : pdpc/supporter/active/andrew-46
**[COLOR="Red"]19:58 >>> NickServ!NickServ@services.: Last seen  : now[/COLOR]**
19:58 >>> NickServ!NickServ@services.: Logins from: andrew_46
19:58 >>> NickServ!NickServ@services.: Nicks      : andrew_46 andrew_47
19:58 >>> NickServ!NickServ@services.: Email      : xxxxxxxxxxxx (hidden)
19:58 >>> NickServ!NickServ@services.: Flags      : HideMail, EMailMemos
19:58 >>> NickServ!NickServ@services.: Language   : default
19:58 >>> NickServ!NickServ@services.: *** End of Info ***

```

So you can see that nickserv has registered the login that I have just made (in the 'Last Seen' field). Easy enough to check on your own nick, as I have just done :).

As for SSL and SASL, SSL is used for the connection itself to Freenode, SASL is used to authenticate your nick and password against the nickserv database. I believe therefore that you can connect with SSL *without* using SASL for nickserv but I have not experimented with this...

Andrew

---

### Post by Soul-Sing on 2011-03-05
Thanks very much andrew.
I did the: ```
/msg nickserv info <nick>
```
and indeed the account is still registered by nickserv. and "up-to-date".

---

### Post by Soul-Sing on 2011-03-05
A nice linkage for OTR ( off the record messaging ) via IRC: xchat/irssi.
: [https://github.com/dertalai/cryptochati/](https://github.com/dertalai/cryptochati/)
Very easy to set up.
there were some questions bout encryption in this thread.(blowjob on irssi) FISH is the common/best known prog.(not easy the set up)
Busy to get it up and running via irssi. xchat is easy and working.

---

### Post by jbicha on 2011-03-15
irssi-scripts includes cap_sasl.pl so you can take out a few lines from your instructions.

```

$ mkdir -pv $HOME/.irssi/scripts/autorun
ln -s /usr/share/irssi/scripts/cap_sasl.pl $HOME/.irssi/scripts/autorun/cap_sasl.pl
```

---

### Post by andrew.46 on 2011-03-15
> **jbicha said:**
> irssi-scripts includes cap_sasl.pl so you can take out a few lines from your instructions.

You are perfectly correct, I see from the changelog that this occurred in May 2010:

```

irssi-scripts (20100506) unstable; urgency=low

  [ martin f. krafft ]
  * Update chanact to 0.5.12, thereby obsoleting
    chanact-comma-instead-of-colon.diff, thanks to a very fast upstream.

  [ Ryan Niebur ]
  * Updated: niq.pl, nm.pl, challenge.pl, twtopic.pl, chanact.pl
  * remove linkshort.pl, removed upstream
  * update my email address
  * move myself to Maintainer
  * add a use Irssi::TextUI to bitlbee_join_notice.pl, thanks Jan Braun
    (Closes: #565702)
**[COLOR="Red"]  * add cap_sasl.pl (Closes: #574991)[/COLOR]**
  * use a new upstream for tinyurl.pl (Closes: #555376)
  * add twirssi.pl, despite not getting tested (Closes: #580468)
  * lintian happiness
    - fix spelling of information in d/copyright
    - Standards-Version: 3.8.4
    - misc:Depends
    - debian/source/format

 -- Ryan Niebur <ryan@debian.org>  Fri, 07 May 2010 17:06:25 -0700

```

which just goes to show that I am getting old and slow :). I shall alter the lines as you have suggested and still plan to rewrite the guide when I install beta 1 Natty Narwhal.

---

### Post by harrykar on 2011-03-15
> **andrew.46 said:**
> You are perfectly correct, I see from the changelog that this occurred in May 2010:

```

irssi-scripts (20100506) unstable; urgency=low

  [ martin f. krafft ]
  * Update chanact to 0.5.12, thereby obsoleting
    chanact-comma-instead-of-colon.diff, thanks to a very fast upstream.

  [ Ryan Niebur ]
  * Updated: niq.pl, nm.pl, challenge.pl, twtopic.pl, chanact.pl
  * remove linkshort.pl, removed upstream
  * update my email address
  * move myself to Maintainer
  * add a use Irssi::TextUI to bitlbee_join_notice.pl, thanks Jan Braun
    (Closes: #565702)
**[COLOR=Red]  * add cap_sasl.pl (Closes: #574991)[/COLOR]**
  * use a new upstream for tinyurl.pl (Closes: #555376)
  * add twirssi.pl, despite not getting tested (Closes: #580468)
  * lintian happiness
    - fix spelling of information in d/copyright
    - Standards-Version: 3.8.4
    - misc:Depends
    - debian/source/format

 -- Ryan Niebur <ryan@debian.org>  Fri, 07 May 2010 17:06:25 -0700

```which just goes to show that I am getting old and slow :). I shall alter the lines as you have suggested and still plan to rewrite the guide when I install beta 1 Natty Narwhal.

Firstly let me compliment about your guide :) . I must notice(i just check it and don't exist in /usr/share/irssi/scripts/) here **[COLOR=Red]cap_sasl.pl is absent in lucid repos.[/COLOR]** As you can see from screenshot link result broken.Probably previous instructions were better
Regards 
Harry

---

### Post by andrew.46 on 2011-03-17
I had forgotten about older Ubuntu versions, or perhaps blindly assumed that such changes would be backported :(

**Edit:** And thanks K.Mandla for the award of ['Tutorial of the Week']("http://ubuntuforums.org/showpost.php?p=10568530&postcount=75") :).

Andrew

---

### Post by harrykar on 2011-03-17
> **andrew.46 said:**
> I had forgotten about older Ubuntu versions, or perhaps blindly assumed that such changes would be backported :(
Andrew
Np [here]("http://ubuntuforums.org/archive/index.php/t-1010780.html") exist a backup of your post. Anyway 10.04(Lucid lynx) LTS is not really a "old" release only a bit more stable ;). 

PS: in repos exist irssi v0.8.14. If one want the latest  v0.8.15 maybee worth install[ Y PPA manager]("http://www.getdeb.net/software/Y%20PPA%20Manager") from getdeb and there find v0.8.15 (and in one PPA the latest irssi scripts package) availability on more PPA's

Regards
Harry

---

### Post by andrew.46 on 2011-03-17
Hi Harry,

Thanks for that although you may have noticed that I have changed the guide back last night :). I have a fresh VM of Maverick at my disposal so I will be tidying up the guide over the next few days.

Andrew

---

### Post by harrykar on 2011-03-17
> **andrew.46 said:**
> Hi Harry,

Thanks for that although you may have noticed that I have changed the guide back last night :). I have a fresh VM of Maverick at my disposal so I will be tidying up the guide over the next few days.

Andrew
Hi Andrew 
IMHO is better to write about either steps: the newest first and if that not work the earliest. ;-)

Furthermore after /set realname  is not bad add */set alternate_name* and */set user_name*(help IRC server build our "hot mask" if we --as usually-- don't run a ident daemon)
```
/set nick <nick> 
/set real_name <Real Name>
/set alternate_name <alternate Name>
/set user_name <user Name(can be the same as our registered nickname)>
```[B][COLOR=Red]
[/COLOR][/B]About the names rules we can say:
1. for privacy reasons as realname we can fill that field with our site url or a comment or a fake name o anything else and 
2.  realname(or ircname) permits blanks and more characters than nickname(--depend of the IRC server we connect-- nickname can be truncated up to 9 --or  sometimes more-- characters). 
3. Valid characters for a nickname are:
  a) the first character can't be a number or "-"
  b) the other characters must be in [a-z, A-Z, 0-9, \, ^, -, |, _, `] (blanks are not permitted)
  c) the  following pair of characters  [],{}, |\ correspond to the same character (upper-lowercase) in Scandinavian(IRC is born there) keyboard and because IRC is case insensitive every pair of characters is considered to be a single character.
[COLOR=Red]
[COLOR=Black]PS: [/COLOR][/COLOR]would[COLOR=Red][COLOR=Black] useful for users if you [/COLOR][/COLOR]tried[COLOR=Red][COLOR=Black] to extend your guide and write the basics about each irssi script starting from the most useful like adv_windowlist, nicklist, scriptassist etc 

Regards
[/COLOR] [COLOR=Black]Harry[/COLOR]
[/COLOR]

---

### Post by andrew.46 on 2011-03-17
OK rewrite is done and works solidly on Maverick, should be ok on other Ubuntu versions as well. I have deliberately kept it to the basics in the hope that the guide will furnish a *starting* point rather than an encyclopaedic reference to irssi usage. 

Andrew

---

### Post by harrykar on 2011-03-18
> **andrew.46 said:**
> OK rewrite is done and works solidly on Maverick, should be ok on other Ubuntu versions as well. I have deliberately kept it to the basics in the hope that the guide will furnish a *starting* point rather than an encyclopaedic reference to irssi usage. 

Andrew
Probably you're right my olistic view is not always appropriate. For  a encyclopedic reference to irssi usage is necessary  another one post for intermediate-power users

i see (furtively) your rewrite and is better than earlier :). Only few annotations about:
1: maybe would better if a user -- if he's newbie for him is the same ;-) -- learn first irc server cmds instead a client alias -- every client as you know use the proper aliases. Here's not a standard -- because server cmds change rarely respect clients aliases. I mean is better use /PART instead /LEAVE or /QUIT instead /DISCONNECT etc
2. As you report  about hide email address "(although this setting is usually the default)... etc" maybe a newbie can do without SET HIDEMAIL ON cmd

Great post. IMO Hit the intended target so Keep it high ;)
Harry

---

### Post by harrykar on 2011-03-23
Hi Andrew. I'm intended to write a post about irssi(not for newbies) to my [blog. ]("http://harrykar.blogspot.com/")
Can use part of your post here?
TIA

---

### Post by andrew.46 on 2011-03-23
> **harrykar said:**
> Hi. I'm intended to write a post about irssi(not for newbies) to my [blog. ]("http://harrykar.blogspot.com/")
Can use part of your post here?

Of course :)

---

### Post by harrykar on 2011-03-26
> **andrew.46 said:**
> Of course :)
Thank you :) . You will be my first revisor ;) .I just start it If u want take a glance regularly and express your opinion there (when i finish it or when u want).  :)
Regards
Harry

---

### Post by bcbc on 2011-06-02
Great guide. Thanks.

---

### Post by andrew.46 on 2011-06-02
> **bcbc said:**
> Great guide. Thanks.

My pleasure :)

---

### Post by andrew.46 on 2011-06-11
I have belatedly set irssi on Natty using this guide and all works well :).

---

### Post by frank cox on 2011-06-26
<snip>

---

### Post by Elfy on 2011-06-26
@frank cox - if you've got issues with irc staff in #ubuntu take it to #ubuntu-ops

---

### Post by frank cox on 2011-06-26
Thanks I will do that to say I did not shirk my responsibility but  first I will give him a chance to recant and end the problem with out causing him any harm.
I did not realize that was a staff person. if so maybe I would probably do well to ditch the system . If they give a person like that authority it does not say much for the claim Ubuntu is interested in promoting open source. . 
The image of Linux as being strictly for arrogant geeks who consider non geeks dogs to be kicked will never change until those who consider themselves supporters of the idea take the responsibility to challenge those whose actions justify that image.
It is your prerogative to pass the buck but a lofty goal such as this requires a team effort. 
Of course that is assuming you share that goal. I do appreciate your letting me know how this works and although I  am pretty sure I have now offended you that is not my intent nor does it benefit me  . I do not believe in political corrrectness and I say what I  think is right regardless . If everyone did that this guy would have either learned not to do this long ago or never given the authority to push people around in the first place.
Truth is everything and when someone is condemned without cause silence is siding with the one who condemns. 
That is my humble opinion anyway.

---

### Post by andrew.46 on 2012-01-11
I have finally installed Oneiric to a partition on my drive rather than running with increasingly frustrating VMs. In a longer term project I have started slowly working through many of the guides I support on these Forums to make sure they are all optimised for the latest release of Ubuntu. Good news is that this guide works beautifully on Oneiric and I hope to see a few more irssi users on either #ubuntu or #ubuntu-beginners :).

---

### Post by starscalling on 2013-06-28
the guide works for me, and for the blowjob.pl script for irssi, just install libcrypt-cbc-perl.

---

### Post by andrew.46 on 2013-07-02
Good to hear that this now quite old guide still works :)

---

