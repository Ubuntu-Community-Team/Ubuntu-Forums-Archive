---
title: "Server Choices"
date: 2011-06-07
forum: Server Platforms
---

### Post by throese on 2011-06-07
What (from personal experience) do you, community members of this site feel are some really good options as server machines?

I've seen these two thus far:

1) Ubuntu Server 10.04 LTS

2) Zentyal

Anymore suggestions and reasons as to why the two above were suggested the most in other topics?

Thanks for all the help! =)

---

### Post by spynappels on 2011-06-07
They are essentially the same thing, but Zentyal has GUI tools and wizards to accomplish basic and common tasks. They both have their place, Zentyal is easier to set up for people new to Linux or coming from a Windows server background.

FWIW, I prefer Ubuntu Server edition as I learned how to accomplish most tasks from the command line. I have used Zentyal as well, and it works very well, I just prefer using the CLI.

---

### Post by arrrghhh on 2011-06-07
Last post is dead-on.

Zentyal has some more advanced wizards to help guide you thru the setup of complicated things - but anything you can achieve on Zentyal, you can achieve on Ubuntu Server.

I think if you have admins that aren't comfortable with CLI, or if you want to hand off support ever, Zentyal would be a good choice.  Really depends on your environment, and your requirements - you didn't really mention anything related to those topics!  Please elaborate, perhaps we can provide more precise advice...

---

### Post by throese on 2011-06-07
arrrghhh: Well, what do you mean by environment? As for requirements, they are as follows:

File Server - Share files between my Linux laptop and all of the Windows towers in the house
Backup Server - To backup all important files/directories and other important things
Web Server - Web Development

What's the purpose of the following or how are they used:

Mail Server - Purpose?
SSH - How is it used and set up?

Will post more if others cross my mind.

---

### Post by arrrghhh on 2011-06-07
> **throese said:**
> Mail Server - Purpose?

Most people use them to send and receive email?  Like if you had your own domain name..

> **throese said:**
> SSH - How is it used and set up?

You should search a little before posting...  No offense, but we're here to help, not handhold.

[SSH Ubuntu Community Doc](https://help.ubuntu.com/community/SSH) would be a good place for you to start...

---

### Post by throese on 2011-06-08
Well, I know a LITTLE about SSH, taking a networking class, but never actually used it. Sorry and thanks arrrghh

---

### Post by Lars Noodén on 2011-06-08
> **throese said:**
> Well, I know a LITTLE about SSH, taking a networking class, but never actually used it. Sorry and thanks arrrghh

To make up for the network class that somehow skipped using SSH you can get an overview of what it can do from the wikibook on [OpenSSH](http://en.wikibooks.org/wiki/OpenSSH).  I've also put together a [presentation on OpenSSH](http://www.bsdly.net/~lars/Lectures/Server-03-Secure-Remote-Shell.odp)

---

### Post by Lars Noodén on 2011-06-08
If you can become proficient in using the shell instead of GUI wizards then the different systems (say Debian vs Ubuntu Server LTS) will seem more alike.  You can re-use more knowledge that way as well as work faster / get more done with less effort.

---

### Post by blind2314 on 2011-06-08
> **throese said:**
> arrrghhh: Well, what do you mean by environment? As for requirements, they are as follows:
 
File Server - Share files between my Linux laptop and all of the Windows towers in the house
Backup Server - To backup all important files/directories and other important things
Web Server - Web Development
 
What's the purpose of the following or how are they used:
 
Mail Server - Purpose?
SSH - How is it used and set up?
 
Will post more if others cross my mind.
 
If those are your only requirements (as of now), then go with Ubuntu Server 10.04. It'll handle those tasks just fine, and learning to use the CLI for some tasks will only serve to help you in the future (as others have said).

---

### Post by throese on 2011-06-08
Thank you all very much for the help you've all given me so far! =)

---

