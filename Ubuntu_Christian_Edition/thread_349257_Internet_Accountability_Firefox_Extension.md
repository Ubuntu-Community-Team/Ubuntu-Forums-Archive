---
title: "Internet Accountability Firefox Extension"
date: 2007-01-29
forum: Ubuntu Christian Edition
---

### Post by bsalt on 2007-01-29
With ads, commercials, and TV nowadays, it is easy to fall into the trap of pornography, and without God's help, it is impossible to crawl out of the trap. Two of the best ways to overcome any addiction/recurring problem  is to seek prayer and help from God, and then also keep an accountability with another Christian who will help keep the person on track.

I know in Windows and OS X, there exist many great programs, such as [www.x3watch.com](www.x3watch.com) and [www.covenanteyes.com](www.covenanteyes.com). But there are no accountability programs for Linux. (I'm strictly talking about accountability, not filtering - this would be a program the user would want to install to overcome the problem)

I think it'd be great if there was a simple Firefox extension that simply grabbed a link of each web URL visited, compiled it to a list, and sent it via .txt file to an accountability partner(s) e-mail address(es). This program would almost sound like a trojan - except it would only grab the web URL's, and then the accountability partner's discrimination will be needed. It would also be nice if the accountability partner set it up on the person's computer, and created their own password for it, so the main user could not change the settings or turn it off.


Would somebody want to help me in writing this extension? I have no clue where to start, I just know there is a need.


God bless,
Jon

---

### Post by tonhou on 2007-01-31
There is a very useful Firefox extension called "Slogger" that keeps a log of all sites visited and it is also able to be customised in different ways.

It has a nice tidy output to an xml file. The file can of course get quite large - even with just 30 mins browsing.

Your idea has merit and could be easily implemented. Of course it depends on the honest embracing of it by both guys involved (one could just use another browser).

[https://addons.mozilla.org/firefox/143/](https://addons.mozilla.org/firefox/143/)

--Tony

---

### Post by bsalt on 2007-01-31
Well, the whole purpose for accountability in the first place is honesty - to bring into the light what is done in darkness.

I did look at that Slogger extension, and I've got it installed right now. But I am still thinking about writing an extension that would be for accountability reasons - and then maybe I could find other coders who could write an add-on to IE7 and Safari that would be a port of this extension.

---

### Post by shane2peru on 2007-02-01
I don't know if this would be easier, but why not make a script that automatically emails the text file of the dan's guardian denied list, to the accountability person on a daily basis?  That would/could be incorporated into Dan's Guardian to make it even better.  Just a thought.  :D 

Shane

---

### Post by yoyoned on 2007-02-01
> **shane2peru said:**
> I don't know if this would be easier, but why not make a script that automatically emails the text file of the dan's guardian denied list, to the accountability person on a daily basis?  That would/could be incorporated into Dan's Guardian to make it even better.  Just a thought.  :D 

Shane

What about making something like this part of the GUI?

---

### Post by bsalt on 2007-02-01
That sounds like a good idea shane2peru. I was trying to stay away from using a proxy, so that way a list of blocked and unblocked stuff is found. I wasn't looking for a way to block something, but rather a way to report something moreso than the former. But whatever works. It would add a great deal of use to dansguardian.

I am no developer, not yet, at least. So mention this to the dansguardian people, or whoever is doing the gui for it.

---

### Post by shane2peru on 2007-02-01
> **bsalt said:**
> That sounds like a good idea shane2peru. I was trying to stay away from using a proxy, so that way a list of blocked and unblocked stuff is found. I wasn't looking for a way to block something, but rather a way to report something moreso than the former. But whatever works. It would add a great deal of use to dansguardian.

I am no developer, not yet, at least. So mention this to the dansguardian people, or whoever is doing the gui for it.

I'm about 90% sure that Jereme has written the gui for Dan's Guardian.  I think it would be a useful tool.  I think you have to say his name to get him to read the thread ;)  .  Just kidding Jereme.  We appreciate the great work you've done.  

Shane

---

### Post by yoyoned on 2007-02-01
> **bsalt said:**
>  I wasn't looking for a way to block something, but rather a way to report something moreso than the former. But whatever works. It would add a great deal of use to dansguardian.


An option could be to set Dansguardian  to "Warn Only" so no filtering will take place, but requests for "bad" sites will still be logged.  Even though I know this is possible, I don't know exactly how.

---

### Post by mhancoc7 on 2007-02-01
> **shane2peru said:**
> I'm about 90% sure that Jereme has written the gui for Dan's Guardian. I think it would be a useful tool. I think you have to say his name to get him to read the thread ;) . Just kidding Jereme. We appreciate the great work you've done. 
 
Shane
 
HaHa! :D 
 
Actually I have been watching this thread rather closely. I had been toying with the idea of adding an option to the GUI to do just this. I have just not had time to completely think it through.
 
It should be easy. It could be some sort of toggle on and off for "accountability". Then have it ask for the email address of the person that you would like to be accountable to and have it set up a cron job to email the denied list out.
 
My question is if the cron job is set to run daily, what if the person is not online will it email out as soon as the next available connection or will it just skip a day or until the computer is online when the cron job runs? This is probably a silly question, but I just was not sure. Also is there an easy way to email from the command line so it could easily be put into the script?
 
God Bless, Jereme

---

### Post by bsalt on 2007-02-01
Yeah, my question is that how would it be sent out if one does not have a mail server (like myself) or a non-poppable email account (i.e. Hotmail/Windows Live Mail). The litle things I never think about with something like X3Watch or Covenant Eyes go a long way.

---

### Post by yoyoned on 2007-02-02
I've had some success.
```

apt-get install mailx
```
It will install postfix (mail server) as a dependancy.
dpkg will ask some config questions for postfix.
The first option I selected Internet Server, and from then on I used the defaults.

then the following comand (ran as root) will mail a list of denied sites 

```

grep -i denied /var/log/dansguardian/access.log|mail -s Acountability_Log_$(date +%m%d%y) user@email.com 

```

I hope this is a good starting place.

---

### Post by mhancoc7 on 2007-02-02
Yes, this is a great place to start. 

Now I just need to decide if I want to delay the release of Ubuntu CE v2.1 so this can be included. 

God Bless, Jereme

---

### Post by shane2peru on 2007-02-02
> **mhancoc7 said:**
> 
My question is if the cron job is set to run daily, what if the person is not online will it email out as soon as the next available connection or will it just skip a day or until the computer is online when the cron job runs? This is probably a silly question, but I just was not sure. Also is there an easy way to email from the command line so it could easily be put into the script?
 God Bless, Jereme

Jereme,

    Those are some good questions.   People with broadband don't tend to think in that direction.  Is there anyway to make it run similar to the way the update manager runs?  (I don't know anything about how it runs)  I assume the update manager knows when you are connected to the web and not and when connected it checks for an update.  (This is a super nice feature that keeps me tied to Ubuntu.)  It is just a thought, I don't know how complex that would be or anything, but it is open source so you can look at the source and see what you think.  I had a brain surge for this one :D

Shane

---

### Post by yoyoned on 2007-02-02
If mail is generated while the computer is offline, Postfix will spool the message, and send it when the network connection is restored.

---

### Post by mhancoc7 on 2007-02-04
> **yoyoned said:**
> I've had some success.
```

apt-get install mailx
```It will install postfix (mail server) as a dependancy.
dpkg will ask some config questions for postfix.
The first option I selected Internet Server, and from then on I used the defaults.

then the following comand (ran as root) will mail a list of denied sites 

```

grep -i denied /var/log/dansguardian/access.log|mail -s Acountability_Log_$(date +%m%d%y) user@email.com 

```I hope this is a good starting place.

Ok, I started playing around with this and I believe I can use this to create the accountability feature fairly easily. One problem. When I tried the command it logged an error saying that my ip was blocked for some reason. Since I have no control over my ip I am not sure what to do. Is there a good way to do this same thing except anonymously. I tried mixmaster, but I could not get it to work.


> **yoyoned said:**
> If mail is generated while the computer is offline, Postfix will spool the message, and send it when the network connection is restored.

That's great!

God Bless, Jereme

---

### Post by yoyoned on 2007-02-04
I sent emails using the command in the previous posts to 2 addresses.  The it arrived  at my gmail account, but not my ISP (sbcglobal.net) email account.  

Some email servers do a reverse DNS look up on the emails it receives, and blocks the ones that don't match.  Example:  my username is todd and my computers hostname is "one", so when the email is sent from my machine, the "from" address is todd@one.  The receiving mail server checks to see if the IP of the sending machine matches it's hostname.  Since "one" is not a registered domain,  it will not match.  This is likely why you are getting the error. 

Some possible solutions:

1) Have you accountability partner get a gmail account.  Admittedly this is not a very good solution, but  if anyone wants a gmail account I have 99 invitations.

2) Use dynamic dns.  I have used dydns.org for several years. Change the postfix configuration file (/etc/postfix/main.cf) to match your dynamic dns account. 
```
myhostname = example.dyndns.org
``` So now the "from "address is "todd@example.dyndns.org" which will match the IP of my system.  This is a rather complicated solution, but this is how I got the mail to arrive at the ISP account that did not work before.  

3) Some other messaging service.  I don't know of anything that would work, but I am sure there is something that could send a message to a forum, BBS, chat room or something similar that works from the command line.   I'll continue to do some research into this option.

---

### Post by mhancoc7 on 2007-02-04
> **yoyoned said:**
> I sent emails using the command in the previous posts to 2 addresses.  The it arrived  at my gmail account, but not my ISP (sbcglobal.net) email account.  

Some email servers do a reverse DNS look up on the emails it receives, and blocks the ones that don't match.  Example:  my username is todd and my computers hostname is "one", so when the email is sent from my machine, the "from" address is todd@one.  The receiving mail server checks to see if the IP of the sending machine matches it's hostname.  Since "one" is not a registered domain,  it will not match.  This is likely why you are getting the error. 

Some possible solutions:

1) Have you accountability partner get a gmail account.  Admittedly this is not a very good solution, but  if anyone wants a gmail account I have 99 invitations.

2) Use dynamic dns.  I have used dydns.org for several years. Change the postfix configuration file (/etc/postfix/main.cf) to match your dynamic dns account. 
```
myhostname = example.dyndns.org
``` So now the "from "address is "todd@example.dyndns.org" which will match the IP of my system.  This is a rather complicated solution, but this is how I got the mail to arrive at the ISP account that did not work before.  

3) Some other messaging service.  I don't know of anything that would work, but I am sure there is something that could send a message to a forum, BBS, chat room or something similar that works from the command line.   I'll continue to do some research into this option.

Thanks, that is what I gathered after looking around a bit.

I want the solution to be the simplest possible for the end user. That is why I hope to be able to find a solution that would work anonymously.

God Bless, Jereme

---

### Post by Coffeebot on 2007-02-04
This looks like a great setup, but I don't have a tech-savvy accountability partner. How difficult are the log files to understand? 

Personally, I can look at my apache logs, and know exactly what's going on. My friends, on the other hand, can't.

Could someone kindly cut and paste an entry or two from theirs? If the logs are apache-esque, is there anything available that could interpret them? 

What it boils down to is that everyone I know uses Covenant Eyes, but I'm not quite willing to stoop to their level and use Windows (nor do I have $300 to drop on a copy of it).

Thanks in advance,
Nate

---

### Post by mhancoc7 on 2007-02-04
The dansguardian GUI that comes with Ubuntu CE makes it very easy to read the logs. You can read the access denied log for the current day in text mode with a single click. You can also read them in html mode very easily. Below are two screenshots of the html logs. There is more info included, but it includes some inappropriate language (reason for being blocked) so I did not make it visible.

---

### Post by Coffeebot on 2007-02-04
So, I assume then, that the file emailed contains more details than just the URL requested?

If you'd be willing, Jereme, could you email/pm me an uncensored copy of the file? I'd like to see the whole thing to know exactly what's being sent out. I don't want to take all of the effort of building a proxy server just to find it's not going to do what I want.

Thanks for your help :)

---

### Post by mhancoc7 on 2007-02-04
Ok, I got my ip unblocked by requesting it from cbl.org who had it blocked.

Now I can see how this could work. I just need to figure out how to ensure that the emails would not get blocked.

Once we get that figured out I could set it up so the user could enter their accountabiltiy partners email and it would set up a cron job to send the emails. Now if the user disables it then it would first send an email to the accountability partner to let them know that it had been turned off. At least that way the accountability partner would know that it had been disabled.

Now maybe someone can come up with a way to send the emails without getting blocked.

God Bless, Jereme

---

### Post by mhancoc7 on 2007-02-04
> **Coffeebot said:**
> So, I assume then, that the file emailed contains more details than just the URL requested?

If you'd be willing, Jereme, could you email/pm me an uncensored copy of the file? I'd like to see the whole thing to know exactly what's being sent out. I don't want to take all of the effort of building a proxy server just to find it's not going to do what I want.

Thanks for your help :)

Sure I will send it now!

Jereme

---

### Post by Coffeebot on 2007-02-05
Thanks again, Jereme.

Is the DG GUI available for download outside of Ubuntu CE?

---

### Post by mhancoc7 on 2007-02-05
> **Coffeebot said:**
> Thanks again, Jereme.

Is the DG GUI available for download outside of Ubuntu CE?

Yes.

Just go the the download page and select your version Edgy/Dapper and you will find a download for the dansguardian GUI. Just scroll down the page a bit. There are actually two downloads for it. One is the GUI only and the other will set up your system with the filtering that comes by default in Ubuntu CE.

FYI: I am going to be releasing the next version very soon. The new Danguardian GUI is much better. 

[http://www.mirror.christianubuntu.com/](http://www.mirror.christianubuntu.com/)

God Bless, Jereme

---

### Post by bsalt on 2007-02-05
Hey Jereme, when you release the update for the new GUI, will it update via the update-manager, or will I have to re-install it?

---

### Post by mhancoc7 on 2007-02-05
> **bsalt said:**
> Hey Jereme, when you release the update for the new GUI, will it update via the update-manager, or will I have to re-install it?

It will not update via the update manager because the GUI is not in the repos. However, you can download a simple script from the Ubuntu CE download page to upgrade to the newest version of Ubuntu CE or just the newest version of the GUI.

God Bless, Jereme

---

### Post by Coffeebot on 2007-02-06
Thanks for the link, Jereme, but it looks like it is very Ubuntu-only.

Is there a source version available so I can compile it on my home server? Ubuntu is great for desktop use, but I refuse to use anything but Slackware on my servers. Compiling my own software helps keep the system nice and trim, and I don't have to wonder where stuff gets installed.

Thanks again! Looks like I have a great solution brewing! (erm...no pun intended)

---

### Post by kvonb on 2007-02-06
This is all very well intentioned, but doesn't the person at the other end, the one who is doing the checking have to visit the sites in order to deem them bad?

That is subjecting that person to the "bad" things, surely that is not good!  Temptation is a constant nag and should not be given the slightest chance.

The real problem lies in the general ignorance and complacency of the average person, everyday people don't realise what is happening around them, the underlying decay of society and morality.

It's so easy to just accept it and get on with something else!

Porn is everywhere, magazines and TV promote very young girls as sex objects, cover them in makeup and revealing clothes in order to make them look older and more attractive, our daughters see this and want it.

This defies all logic!  Would you cover yourself in sheep's blood and dance in front of a hungry wolf, then be surprised when it attacks you?

The argument that is given is "but women should be allowed to show what they like", this is stupidity at it worst.  Why not make it a crime for gravity to kill people? People should be allowed to fall off cliffs and not get hurt!  That makes just as much sense!

Or to put that in a religious context: would you openly tempt the devil?  Would you say something like: "here I am Devil, do your worst, you cannot break me!".  What does the Christian Bible say about that sort of behaviour?

The Christian Bible also tells us that Jesus was tempted by the devil, and even he eventually asked if God had forsaken him!  These temptations are thrust at us whichever way we look!  Do you REALLY believe that you are stronger than Jesus Christ?

Try to go 1 day without seeing a revealing picture or sexual temptation of **any** kind, it is extremely hard to do!

Why should we have to be tempted constantly?  Doesn't it make more sense to remove the thorn from my finger, rather than trying to ignore it?

We (as in civilised and intelligent society) should be fighting this "devil", at the source, not wasting time on the symptoms.  In this case the "devil" is the purveyor and spreader of this decay, ie the TV stations/producers/magazines/newspapers etc' who benefit from creating and spreading this "cancer".

This is not intended to enflame/demean/enrage anybody (apart from the society underminers), just to hopefully provoke some thought!

Regards, Kev :)

---

### Post by mhancoc7 on 2007-02-06
> **Coffeebot said:**
> Thanks for the link, Jereme, but it looks like it is very Ubuntu-only.

Is there a source version available so I can compile it on my home server? Ubuntu is great for desktop use, but I refuse to use anything but Slackware on my servers. Compiling my own software helps keep the system nice and trim, and I don't have to wonder where stuff gets installed.

Thanks again! Looks like I have a great solution brewing! (erm...no pun intended)

The source is contained inside the folder that you download. You will need to show hidden files. Much of it is simply scripts that set the configuration up. The GUI is built with Gambas. You can extract the .deb package and inside you will find more scripts and such as well as the Gambas source package for the GUI.

Hope that helps.

God Bless, Jereme

---

### Post by doobit on 2007-02-06
Kev,
You need to do what your God given conscience tells you to do. As for me, it's a help to have a tool in my possession that will block things before I need to filter them myself.

---

### Post by thomasaaron on 2007-02-09
Hi, guys. Here is a python program I wrote as an accountability program. It translates firefox's mork history file into text and emails it wherever you want automatically.

If you hook it up to CRON, it works perfectly.

You will have to modify lines 7, 43, 48 to meet your own specifications.

Best,
Tom


[HTML]#!/usr/bin/env python
#Mork File Decoder

import smtplib

#Open Mork File
file = open('/home/thomasaaron/.mozilla/firefox/sw2mfywu.default/history.dat','r')

#Search line for "http"
note = ""
for line in file:
    
    markerA = 0
    markerB = 0
    if "http" in line:
        codedLine = line
        for posA in range(len(codedLine)):

            if codedLine[posA]+codedLine[posA+1]+codedLine[posA+2]+codedLine[posA+3]=="http":
                markerA = posA
                break

        for posB in range(len(codedLine)):
            if "com" in codedLine and codedLine[posB]+codedLine[posB+1]+codedLine[posB+2]=="com":
                markerB = (posB+3)
                break
            elif "net" in codedLine and codedLine[posB]+codedLine[posB+1]+codedLine[posB+2]=="net":
                markerB = (posB+3)
                break
            elif "org" in codedLine and codedLine[posB]+codedLine[posB+1]+codedLine[posB+2]=="org":
                markerB = (posB+3)
                break
            elif (posB+2)==len(codedLine):
                break

        decodedLine = codedLine[markerA:markerB]
##        print decodedLine

        #Create string containing all visited URL's
        note = note + decodedLine + "\n"

#Format and Send Message
msg = "From: copy@tbaaron.com\nSubject: Tom's Accountability Report\n\n%s" % note


server = smtplib.SMTP("smtp.mail.yahoo.com")
server.login("tbaaron16","seagal")
server.sendmail("copy@tbaaron.com",['copy@tbaaron.com','aaroncasa@yahoo.com'],msg)
server.quit()[/HTML]

---

### Post by mhancoc7 on 2007-02-11
> **thomasaaron said:**
> Hi, guys. Here is a python program I wrote as an accountability program. It translates firefox's mork history file into text and emails it wherever you want automatically.

If you hook it up to CRON, it works perfectly.

You will have to modify lines 7, 43, 48 to meet your own specifications.

Best,
Tom


[html]#!/usr/bin/env python
#Mork File Decoder

import smtplib

#Open Mork File
file = open('/home/thomasaaron/.mozilla/firefox/sw2mfywu.default/history.dat','r')

#Search line for "http"
note = ""
for line in file:
    
    markerA = 0
    markerB = 0
    if "http" in line:
        codedLine = line
        for posA in range(len(codedLine)):

            if codedLine[posA]+codedLine[posA+1]+codedLine[posA+2]+codedLine[posA+3]=="http":
                markerA = posA
                break

        for posB in range(len(codedLine)):
            if "com" in codedLine and codedLine[posB]+codedLine[posB+1]+codedLine[posB+2]=="com":
                markerB = (posB+3)
                break
            elif "net" in codedLine and codedLine[posB]+codedLine[posB+1]+codedLine[posB+2]=="net":
                markerB = (posB+3)
                break
            elif "org" in codedLine and codedLine[posB]+codedLine[posB+1]+codedLine[posB+2]=="org":
                markerB = (posB+3)
                break
            elif (posB+2)==len(codedLine):
                break

        decodedLine = codedLine[markerA:markerB]
##        print decodedLine

        #Create string containing all visited URL's
        note = note + decodedLine + "\n"

#Format and Send Message
msg = "From: copy@tbaaron.com\nSubject: Tom's Accountability Report\n\n%s" % note


server = smtplib.SMTP("smtp.mail.yahoo.com")
server.login("tbaaron16","seagal")
server.sendmail("copy@tbaaron.com",['copy@tbaaron.com','aaroncasa@yahoo.com'],msg)
server.quit()[/html]

Ok, that looks cool. I am not that familiar with sending emails via command line. I have a way to get the accountability program setup, but the issue that I keep running into is the emails get blocked for various reasons. Could you let me know if there is a fairly simple way to send a single email via command line without it getting blocked? 

Thanks, Jereme

---

### Post by thomasaaron on 2007-02-11
This program does not send email from the command line.
When you set it up on CRON, it runs behind the scenes.

First, this particular program is set up for yahoo pro (which has smtp support).
I've never tested it with other smtp providers, so I don't know how well it will work.
Somebody smarter than me will have to make it work with a different email provider.


Also, are you sure you correctly modified lines 7, 43, and 8.

7 should be:
file = open('<YOUR DIRECTORY/.mozilla/firefox/sw2mfywu.default/history.dat','r')
i.e. for me it is ('/home/thomasaaron/.mozilla..........................................','r')

43 should be:
msg = "<YOUR EMAIL ADDRESS>\nSubject: Tom's Accountability Report\n\n%s" % note

48 should be:
server.sendmail("<YOUR EMAIL ADDRESS",['<RECIPIENT EMAIL ADDRESS'],msg)

---

### Post by mhancoc7 on 2007-02-11
Ok, I see.

I did not actually try the program. I am just looking for a way to be able to include the accountability into the LiveCD by default with as little user configuration as possible.

I am starting to think that this might not be feasible.

Thanks again, Jereme

---

### Post by BenWilson on 2007-03-06
@ thomasaaron
> Also, are you sure you correctly modified lines 7, 43, and 8.

As a developer, I recommend you variablize those values then move the configuration into the top. Although, I think using :

At the top:

history_path = '/home/uname/.mozilla/.../history.dat
your_email = 'me@example.com'
other_email = 'him@example.net'
email_subj = "Tom's Accountability Report"

Line 7 would be:
file = open(history_path,'r')

Line 43 would be:
msg = "%s\nSubject: %s\n\n%s" % (your_email, email_subj, note)

Line 48 would be:
server.sendmail(your_email,other_email,msg)

@Jereme

What I would recommend you do to send email from the command line is an approach that authenticates the user through that user's ISP. That is, it uses mail.example.com as the SMTP server, and the username/password for that user. This should bypass the problem you are encountering with trying to send directly. This is similar to how Thunderbird authenticates. These URLs should help.

[http://docs.python.org/lib/module-smtplib.html](http://docs.python.org/lib/module-smtplib.html)
[http://www.eskimo.com/~jet/python/examples/mail/smtp1.html](http://www.eskimo.com/~jet/python/examples/mail/smtp1.html)
[http://docs.python.org/lib/SMTP-example.html](http://docs.python.org/lib/SMTP-example.html)

BTW, great OS idea.

Ben

---

### Post by mhancoc7 on 2007-03-06
> **BenWilson said:**
> @ thomasaaron


As a developer, I recommend you variablize those values then move the configuration into the top. Although, I think using :

At the top:

history_path = '/home/uname/.mozilla/.../history.dat
your_email = 'me@example.com'
other_email = 'him@example.net'
email_subj = "Tom's Accountability Report"

Line 7 would be:
file = open(history_path,'r')

Line 43 would be:
msg = "%s\nSubject: %s\n\n%s" % (your_email, email_subj, note)

Line 48 would be:
server.sendmail(your_email,other_email,msg)

@Jereme

What I would recommend you do to send email from the command line is an approach that authenticates the user through that user's ISP. That is, it uses mail.example.com as the SMTP server, and the username/password for that user. This should bypass the problem you are encountering with trying to send directly. This is similar to how Thunderbird authenticates. These URLs should help.

[http://docs.python.org/lib/module-smtplib.html](http://docs.python.org/lib/module-smtplib.html)
[http://www.eskimo.com/~jet/python/examples/mail/smtp1.html]("http://www.eskimo.com/%7Ejet/python/examples/mail/smtp1.html")
[http://docs.python.org/lib/SMTP-example.html](http://docs.python.org/lib/SMTP-example.html)

BTW, great OS idea.

Ben

Thanks for the links and the suggestions. I will definitely take a look.
Jereme

---

### Post by thomasaaron on 2007-03-07
I basically just made this program for my own use.
If someone creates a nifty modified version of it, could they please send it to me?

Thanks,
Tom

---

### Post by Elif Tymes on 2007-03-10
Hello!

I'm an employee at Covenant Eyes, and just happened to click this subforum because it caught my attention.

I'm really glad you guys understand theneed so much that you're looking for linux alternatives.

I wonder... is there any way we can monitor all traffic through the http protocol on a given linux machine?

Right now (as a sorta "on the side" thing, not an official CE application) I'm thinking about methods of using a proxy-like system to update a persons accountability logs to our server... Of course this would require someone to force all http/https traffic through a specified proxy... either through some sort of firewall or modifying the linux kernel...

Would something like that fulfill your needs?

---

### Post by thomasaaron on 2007-03-10
The strength of Linux is that it puts you in complete control of your computer. As such, it is difficult to police yourself. Anything you can implement, you can turn off or work around.

As accountability software, the above program only works because, if your accountability partner ceases to receive reports, they know something is up.

The obvious workaround is to download another browser (other than firefox) and use it to view porn.

I almost think that good accountability measures would have to be built into the kernel or something. But that's beyond my ability at the moment.

I'd love to hear some ideas about how to make my program more foolproof.

Best,
TOm

---

### Post by xilix on 2007-03-12
Hello,
I didn't read everythin in this thread, because I don't understand everything...

but I think **anacron** is made for what you want. It is a 'cron' that executes scripts later when not possible at the planned time...

Just my two cents
xilix

---

### Post by Elif Tymes on 2007-03-13
Well, yes, we would have to build a kernel extension, the problem with that though is if you're intelligent enough, you can remove the kernel extension...

What you would need in order to enforce accountability, would be to have a couple of watchdog programs, or potentially a root cronjob that would run a certain program every 5 minutes to make sure that the kernel extension is in, and if it's not, lock down internet....

Other options would be to set up an external firewall, and relay all http communication through a proxy that monitors and reports... This would require additional hardware in most churches, as well as an understanding of the methodology of doing so....

I'm talking with my supervisors about opening up our protocol for sending URL logs to our server, that way we could get an open source Linux Client that functions on the CE protocol, maybe even integrate it with your script thomas...

That way we could integrate CE like accountability (Reports/ Scored sites/Central Emails).... 

I wonder what we could do about logging all http/https traffic in linux....

---

### Post by bsalt on 2007-03-13
Elif, there actually is a program already out - called DansGuardian. Go to [www.christianubuntu.com](www.christianubuntu.com) - and bundled with this Christian verson of Ubuntu is the program. It is essentially everything you just mentioned. But like thomasaaron said, the primary linux user (which would be me) is in complete control to do anything on the computer - including changing what is filtered on the program. 

Something will be implemented eventually, I know that... but it will take time.

---

### Post by Elif Tymes on 2007-03-13
Yes, but that's a filter... Not accountability?


Also: Yes, you are in complete control of the system, which is why our company is so reluctant to put any resources into the program, because it means that someone will be able to very easily bypass it(theoretically) by merely knowing his stuff in the Linux enviroment.

However, I believe the Ubuntu CE edition is more geared for churches/christians who may not know all the deep underworkings of the Linux OS, who would actually not be able to simply bypass it. Throw in Linux's superior User Management system and you have a software program that requires root level access to circumvent, as well as a very good understanding of Linux...
> **bsalt said:**
> Elif, there actually is a program already out - called DansGuardian. Go to [www.christianubuntu.com](www.christianubuntu.com) - and bundled with this Christian verson of Ubuntu is the program. It is essentially everything you just mentioned. But like thomasaaron said, the primary linux user (which would be me) is in complete control to do anything on the computer - including changing what is filtered on the program. 

Something will be implemented eventually, I know that... but it will take time.

---

### Post by xtheblack9x on 2007-03-30
This is awesome!!!!! I have been wanting to use linux again for a long time :( but havn't because I couldn't find a program like what you guys are discussing.

---

### Post by mhancoc7 on 2007-03-30
> **xtheblack9x said:**
> btw: theres a Christian version of Ubuntu? if so where can i download this? SIGN ME UP lol

[www.christianubuntu.com](www.christianubuntu.com)

Jereme

---

### Post by xtheblack9x on 2007-03-30
thanks so much :). im downloading it now

---

### Post by xtheblack9x on 2007-03-31
I just joined the christian ubuntu team and I'm going to be working on a java program that will send the logs of DansGuardian or if you choose, all the sites visited(if possible) to the email of a Accountability partner. This program will have a GUI to Disable/Enable along with a few settings. I'm going to have to do a good amount of research though but i should be able to manage :).

Sorry i havn't introduced myself: Hello Forum im Russell Murray *Takes a bow

---

### Post by mhancoc7 on 2007-03-31
> **xtheblack9x said:**
> I just joined the christian ubuntu team and I'm going to be working on a java program that will send the logs of DansGuardian or if you choose, all the sites visited(if possible) to the email of a Accountability partner. This program will have a GUI to Disable/Enable along with a few settings. I'm going to have to do a good amount of research though but i should be able to manage :).

Sorry i havn't introduced myself: Hello Forum im Russell Murray *Takes a bow

Welcome to the Team Russell. I am really excited that someone has taken up the challenge of creating this feature. I look forward to watching its progress.

God Bless, Jereme

---

### Post by klabelkholosh on 2007-04-17
Hi guys :)

Isn't this.... [www.accountabilitypal.org](www.accountabilitypal.org)... what you're looking for?

---

### Post by Null_Pointer on 2007-05-05
AccountabilityPal DOES sound like a cool idea at first.  However, according to its intentional use, it seems limited.  I believe that the intended use is to have it running on a workstation or server that acts as a proxy for any number of other computers.  While this is all fine and dandy for stationary workstations, it doesn't bode well for laptop users.  Covenant Eyes is a very effective accountability solution for any Windows machine, even laptops, but there is nothing comparable for Linux.

I encourage Elif Tymes to continue persuading his employer to open up the Covenant Eyes protocol.  This would allow a world of possibilities for developers to create some useful accountability software for Linux.  With the large number of open-source savvy college graduates being churned out these days (who are eager to embrace Linux as a primary OS), Lord knows an accountability solution is needed.

---

### Post by johonbravo on 2009-02-03
@ Elif Tymes:

Have the people over a CE discussed opening that port? 

Have any of these ideas been developed further? I would love to see some of this be put to use for us linux users out ther.e

---

### Post by wildman4god on 2009-02-05
I vote for Covenant eyes to be ported to linux, an accountablity mode for that filter software would be good as well, also has anyone tried x3 or CE under wine? some where else in this forum was a project for a linux version of CE called net responsiblity, it was ran on cli and it also had blocking out going mail issues, my vote is that everyone working on both dansguardian and net responsiblity should work together on something like this.

---

### Post by JSuresh on 2009-02-24
Hey has there been any tangible progress on this stuff?  I'm currently at the point where if there's not a workable Firefox extension or x3watch/CE version for Linux, I'm switching back to Windows.  Accountability pal isn't great for personal computers, as mentioned before.  Similarly, net responsibility generates a gigantic, comprehensive email which is impossible to sort through for anyone keeping you accountable.

I really truly love Ubuntu but Christ warned us to flee sexual immorality, and I'm realizing that if there isn't anything working RIGHT NOW, switching back to Windoze is the step I personally need to take (at least until there is some viable alternative for linux).

---

### Post by JSuresh on 2009-04-06
I think this is bump-worthy

---

### Post by thomasaaron on 2009-04-06
Have you tried foxfilter? It's a firefox extension that is pretty configurable. You can filter on a whitelist or blacklist basis.

Works pretty well for my kids. They can't uninstall it.

---

### Post by Coffeebot on 2009-04-06
Hey Suresh -- I currently use Smoothwall with Dan's Guardian set as an invisible proxy. From there, I have a script that uploads the DG access log to my webserver which has a php script to parse it live on the web. It's not perfect, but it works pretty well. My wife controls the passwords on the smoothwall box, so it's not something I can turn off without her knowing it.

It's a bit of work to set up, but it's all running on a 10 year old PC, and I haven't rebooted it in over a year (only did so b/c we moved!) The biggest thing is finding the right settings for DG. For us, it was WAY too sensitive (it even kicks back alerts for Windows Update), and was returning a lot of false positives.

For me, it was well worth the effort. I've seen Covenant Eyes ruin too many computers, and with Smoothwall+DG, all of our computers run at full speed, with no visible network lag (unlike a PC with CE). Plus, there's no monthly fee :D

---

### Post by dpancoast on 2009-04-12
Hey Coffeebot. I'm looking to make the switch to Linux, preferably Ubuntu. I'm pretty good with a PC, but I don't have a lot of experience with Linux, however I am a fast learner. Your internet accountability setup sounds like something I've been waiting for in order to make the switch. Could you list some step by step instructions on how to complete your setup? Or point me to a link that would help me set this up?
Thanks!
Doug

---

### Post by Coffeebot on 2009-04-12
> **dpancoast said:**
> Hey Coffeebot. I'm looking to make the switch to Linux, preferably Ubuntu. I'm pretty good with a PC, but I don't have a lot of experience with Linux, however I am a fast learner. Your internet accountability setup sounds like something I've been waiting for in order to make the switch. Could you list some step by step instructions on how to complete your setup? Or point me to a link that would help me set this up?
Thanks!
DougUnfortunately, it's been about two years since I set it up, so I don't remember much of what I did (it was a fairly easy fire-and-forget setup).

If you head over to smoothwall.org and grab the latest ISO, and then look at the dansguardian.org site for instructions on getting it configured with Smoothy. Honestly from what I remember, there wasn't a whole lot of commandline stuff to deal with, and what there was to do, it was spelled out pretty clearly.

Also, you'll need to configure a way to pass the DG log file from the smoothwall box to another, in order to process it into an email. You can certainly do it all from smoothwall, but it would take a lot of work (smoothwall is a VERY limited linux install -- and rightfully so). If you'd like help with the scripting to make it automatically transfer the files, I'd be glad to lend a hand (we can switch to PMs or email, to avoid derailing the thread). But, they are fairly rudimentary shell scripts, so a little googling would quickly turn up answers, too.

The only potential head-scratcher is whether or not your ISP requires you to register your router/firewall with them. I use Cox Communications, and any time I attach a new cable modem or router, I have to call them to register the mac address with them. It's usually a 5 minute phone call (plus wait time). ymmv.

---

### Post by DustStuff on 2010-03-02
Those interested in internet accountability software for Linux could check out the [Net Responsibility website]("http://www.netresponsibility.com/") for the latest version of that software. It (as well as the website) is still in an alpha state, but the format of the emailed reports has improved, and the more people that are using it, the quicker bugs will be identified, etc., and it can gradually move towards being a more robust piece of software that meets the needs of Linux/Ubuntu users. Drop by the site to check it out and try the software, and let us know what you think!

---

### Post by kevorski on 2010-07-23
> **DustStuff said:**
> Those interested in internet accountability software for Linux could check out the [Net Responsibility website]("http://www.netresponsibility.com/") for the latest version of that software. It (as well as the website) is still in an alpha state, but the format of the emailed reports has improved, and the more people that are using it, the quicker bugs will be identified, etc., and it can gradually move towards being a more robust piece of software that meets the needs of Linux/Ubuntu users. Drop by the site to check it out and try the software, and let us know what you think!

This is awesome! Thanks much, just installed it and got it configured in like 2 minutes. Automatically sends out reports daily if you choose. Default is set for 7 days, Was working on getting cron to send it out like once every 6 hours but yeah didn't have much luck with that. If anyone knows anything about cron and is using this program let me know, would be awesome to get 6 hour intervals setup

---

