---
title: "&quot;Hacker Attack!!!&quot;"
date: 2006-01-19
forum: Server Platforms
---

### Post by Bil-E-daKid on 2006-01-19
Greetings,

This morning, I recieved an email from my Ubuntu system at home which had a subject of "Hacker Attack!!!" and a single letter in the body - 'm'.

Can anyone tell me what generated this and why it would do such a thing?

Thanks!

Bil-E-daKid

---

### Post by LordHunter317 on 2006-01-19
A spammer, likely.  As to why?  Who knows?  The amount of spam I get that makes no sense whatsoever greately dwarfs the amount of spam I get that makes any sense whatsoever.

---

### Post by Bil-E-daKid on 2006-01-19
*grin* Yes - I know what you mean about the Spam. It's like, I know the words are english but all strung together like that it doesn't even try to sell anything. What's with that?

I had wondered if it was spam, but the from address is actually my machine name (ubuntu@<machinename> is the actual address).  It appears to have been sent by the system itself - and I do remember configuring something somewhere to send alert messages to my pop account but I'm no longer certain of where that was.

Do you know if there is a postfix/sendmail (or whatever the MTA is) log of all sent mail?

Regards

---

### Post by curuxz on 2006-01-19
Do you live with anyone who would have access to your computer besides you?

Sounds like a pratical joke from someone...

---

### Post by Bil-E-daKid on 2006-01-19
No - other users yes, but noone else who would access to do crazy things - or would now how to.

It does sound strange though doesn't it?

---

### Post by LordHunter317 on 2006-01-20
Can you post the complete text of the email?

---

### Post by aysiu on 2006-01-20
[QUOTE=Bil-E-daKid]
This morning, I recieved an email from my Ubuntu system at home which had a subject of "Hacker Attack!!!" and a single letter in the body - 'm'.[/QUOTE] What do you mean by "from my Ubuntu system at home"? What was the email address is was sent from?

---

### Post by Bil-E-daKid on 2006-01-20
The email is still at work so I'll post the entire thing later today - including headers.

The email was addressed from 'ubuntu@josiah' - my machine name at home is josiah.  That's why I figured it was my home machine.

I'm doing a search for anything containing the email address that the email was sent to in the hopes that will show up a config file somewhere. I'm sure I've enter that in somewhere as the account to send notifications too - I just can't recall what!  ;-)

---

### Post by Bil-E-daKid on 2006-01-20
Ok - the search tool didn't find anything with my email address in it (I ran it as root as well, just to make sure).

Is there a way I can do the same thing from the command line somehow using a recursive cat and grep or something?

---

### Post by earobinson on 2006-01-20
this sounds like a joke, even if your computer did detect a hacker and did send you an email, the subject would not be Hacker Attack!!! so you are fine

---

### Post by LordHunter317 on 2006-01-20
This is false reasoning: expecting braggart attacks to be rational is rather silly.

---

### Post by earobinson on 2006-01-20
[QUOTE=LordHunter317]This is false reasoning: expecting braggart attacks to be rational is rather silly.[/QUOTE]
Im not sure I understand that?

---

### Post by LordHunter317 on 2006-01-20
While I doubt he's actually been attacked, saying that it's unlikely he's been attacked because the messages said "Hacker Attack" is silly.  All sorts of viruses in history of had rather nonsensical bragging messages when they go off, from "HAHA YOU HAVE A VIRUS" to anything else you can imagine.

---

### Post by towsonu2003 on 2006-01-20
isnt it weird that he got the mail from josiah@ubuntu? does the OP run email servers or something (any servers)? or is this a regular home ubuntu installation (check emails, web browsing, text typing etc)?

---

### Post by earobinson on 2006-01-20
probaly a prank

---

### Post by Bil-E-daKid on 2006-01-20
Here's a screenshot of the email in Thunderbird - I've turned on the headers so you can see the whole thing.

I'd say I have a fairly standard installation. I've added a bunch of things after the stock install but nothing 'crazy'. I have SSH and FreeNX running - they're the only server type things as far as I am aware.

I've also attached a log file of all the install/config changes I do (so it makes it easy if I need to reinstall for some reason - then I know what I've done).

---

### Post by LordHunter317 on 2006-01-20
I can't read that message and see all the relevant details, but from what I can see, it looks like it came externally.  Please save the email as text and post that so I can verify.

---

### Post by Bil-E-daKid on 2006-01-20
Sure thing - here you go. I noticed that, with the text file in my previous post, I couldn't just click and see it, I had to download it and then open it in gedit.

Thanks for looking though guys - I appreciate it.  

I've had a look around things (like the events listed in Firestarter) and there don't appear to be any nasty things listed there.

My ADSL router forwards a different port to the SSH server on 22 but that's [apparently] the only way in to my machine - and I've got that configured so only my login has access to that.

---

### Post by invalid on 2006-01-20
Try checking to see if anyone has recently been on from a source you do not recognize:
```
last
```
(the newest logins are at the top)

If they are all local "(:0.0)" then it is probably someone pulling a joke on you.

---

### Post by LordHunter317 on 2006-01-20
I think something is screwing up rewriting emails, as by looking at the Recieved headers, it looks like it is definetely external.

---

### Post by Bil-E-daKid on 2006-01-20
Kewl - just learned a new command.  ;-)

All the user names look ok - except an instance of 'root' which is odd because that's disabled.

They seem to vary between :0.0, :20.0 and unix:1000.0 (or unix:1001.0) - with the occasional SSH login from my works external IP - or a home network IP.

---

### Post by Bil-E-daKid on 2006-01-20
Ok - I guess I read them wrong as it looks to me like its sent from the local machine out to my ISP's smtp server (via their spamassassin relay) and into my POP mailbox.

I someone sent that message externally, I wonder how they figured out what my local machine name was? 

LordHunter317, do you know of a way to scan my hard disk looking for a text string in a file? From the command line?

Thanks again.

---

### Post by Shadyman on 2006-01-20
[QUOTE=Bil-E-daKid]Ok - I guess I read them wrong as it looks to me like its sent from the local machine out to my ISP's smtp server (via their spamassassin relay) and into my POP mailbox.

I someone sent that message externally, I wonder how they figured out what my local machine name was? [/QUOTE]

Are you running Samba? Do you have websites hosted on your machine, even locally, that link off somewhere else? That would list your machine as the referring URL :confused:

---

### Post by Bil-E-daKid on 2006-01-20
Hey there Shadyman,

Nope - no samba or web servers locally. The only servers I have running (that aren't there from a default install) are SSH and FreeNX.

---

### Post by MJN on 2006-01-24
What's your IP? 203.89.166.120? That's where it came from...

---

### Post by Bil-E-daKid on 2006-01-24
Hey there MJN,

It may very well have been at the time though its not now.

That subnet is one owned by my ISP so it would have looked to the ISP's mailserver that the email was coming from that IP address if my machine sent it.....

---

### Post by venzen on 2006-01-29
Looking at the screenshot of the email in Thunderbird I notice 2 things:

1) The originating mail account is called 'ubuntu@josiah' with an alias 'test'
2) It mailed to your address 'wmg@maxret.co.nz' as you had configured yourself.

These settings are in your system somewhere - you just have to find them - as you admit you cannot remember where exactly you had configured the 'ubuntu@josiah' ... 

Firstly, I would check my mail clients (Thunderbird, Evolution, etc - anything you might have used since install) and look for an account called 'test' associated with address 'ubuntu@josiah'.

Secondly, have you installed postfix? If you have you should look through its configuration files in /etc and search for 'test' and 'josiah' (see below).

Next, use the command line to do a deep trawl of your system files for the search terms 'test', 'ubuntu' - even 'ubuntu@josiah'... here's how you do it:

Use 'grep' with the options 'lsri' , your search term and finally the directory in which to look. Like this

```
grep -lsri 'test' /home
```

The options '-lsri' will force grep to output any files in the /etc directory (and its sub-directories) that contain the pattern 'test' (or 'Test' or 'TEST' and so forth). Whatever grep outputs, I suggest you open the files one-by-one in 'gedit' and use its search function to locate 'test' (or whatever term you grepped). grep is powerful and you should read its man page...

BTW: it is worth also grepping as the superuser, since some files are not readable by regular users

```
sudo grep -lsri 'ubuntu@josiah' /var/log
```

---

### Post by Bil-E-daKid on 2006-01-30
Thanks venzen - that's fantastic.

While starting a grep -lsri, I had a thought and looked in my ADSL router configuration. There is a setting on the 'Reporting' page where I had configured the router to send alerts to my email address and the return address is ubuntu@josiah.

There you go - problem solved - apparently my Linksys router was alerting me of a 'Hacker Attack!!!'. Still not quite sure why but at least I know where the message came from now.

And I got to learn how to do a recursive directory grep which is also extremely useful!

Thanks guys!
Bil-E-daKid

---

### Post by jubalj on 2008-04-23
yes i can confirm seems to be a linksys router related issue..  not sure what to do about it though.. I've got a WAG54v2 with pluto (auz/nz) firmware. 

[http://forums.linksys.com/linksys/board/message?board.id=DSL&message.id=852](http://forums.linksys.com/linksys/board/message?board.id=DSL&message.id=852)

---

