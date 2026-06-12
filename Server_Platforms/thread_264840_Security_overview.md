---
title: "Security overview"
date: 2006-09-25
forum: Server Platforms
---

### Post by toasted on 2006-09-25
I have just set up a lamp server for the first time. It is seen from the internet and works ok. It is a sub domain running on an alternate port other than 80. Then I clamped off the port until such time as I can determine what security I need. 

I'm rather new to linux but have been running the desktop for a few months and have had a win2000 server running for a few years. This is nothing mission critical, only a personal site and a couple for friends. 

I have been looking around and reading up but it seems that with Linux I would be sitting at the screen running tests and scans non-stop. That is no fun.... it really can't be that intense or that difficult, can it? I don't want intrusions.... but im not willing to commit my entire life to stop them either. 

My mail is handled by the win box and I will not have FTP running so those holes are not there. I have webmin and usermin installed and working. I installed tripwire to check it out but this seems like one of the time consuming things that I really don't want to deal with. I havent really figured it out though. To be honest I dont have a clue what I need or want, other than to be protected.

In a nutshell I guess the questions are... should I pursue webserving in Linux? Will it demand more of me than I am willing to give? (that is not much either, and it has to be simple and nearly automatic)

---

### Post by toasted on 2006-09-25
One interesting thing I found was this:
[http://linux.cudeso.be/linuxdoc/portsentry.php#config](http://linux.cudeso.be/linuxdoc/portsentry.php#config)

I installed it and added the port i'm using to the list. Web pages are still served (checked from outside my network) and this is supposed to block scans so the port looks invisible to the scanner. Sounds like a good scenario if it works....

---

### Post by MrHorus on 2006-09-26
> **toasted said:**
> I installed tripwire to check it out but this seems like one of the time consuming things that I really don't want to deal with. 

If you can;t be bothered taking the time to secure your box then don't come complaining when you get cracked :)

---

### Post by toasted on 2006-09-26
> **MrHorus said:**
> If you can;t be bothered taking the time to secure your box then don't come complaining when you get cracked :)

Oh gee, well, ummm, thanks a lot for taking the time to write that

---

### Post by MrHorus on 2006-09-26
> **toasted said:**
> Oh gee, well, ummm, thanks a lot for taking the time to write that

Well you make some suggestions like Tripwire but then you say you can't be bothered taking the time to learn how to set up up, so what do you expect?

---

### Post by toasted on 2006-09-26
> **MrHorus said:**
> Well you make some suggestions like Tripwire but then you say you can't be bothered taking the time to learn how to set up up, so what do you expect?

Dude, I never said I couldnt be bothered. I have already commited nearly 2 days to this with no success. What I need is something that will not require me to commit my entire life to it. That is what I said. 

If you don't want to help, and simply want to be critical, then just go away.

---

### Post by skymt on 2006-09-27
Properly set up, a Linux server can be automatic and mostly trouble-free. Here's a few pieces of advice:

* Stick with a mostly-default configuration. Most servers are secure by default, and many security holes are caused by misconfiguration. Only change what you need to, in order to make it work.
* Enable security and updates repositories, and update regularly.
* Remove Usermin and Webmin. They're security nightmares. Don't believe me? Just try running Nessus on your server with both enabled. If you really need them, set them up to only allow connections from trusted hosts and you should be okay (unless an attacker manages to spoof one of those hosts).

---

### Post by toasted on 2006-09-27
Thanks for the reply. I have formatted and installed Win2000 server now since I could not make MySql work, and im having the very same trouble on windows that I had on linux. Its been 3 days now and ive about had it. Should not be this hard to do, or this hard to get help.....    I'm sure its just something stupid but its got me down...  way down....

---

### Post by skymt on 2006-09-27
> **toasted said:**
> Thanks for the reply. I have formatted and installed Win2000 server now since I could not make MySql work, and im having the very same trouble on windows that I had on linux. Its been 3 days now and ive about had it. Should not be this hard to do, or this hard to get help.....    I'm sure its just something stupid but its got me down...  way down....

I don't really like MySQL. I've found PostgreSQL much less problematic. Also, it comes with one of the best manuals I've seen with an open-source product.

EDIT: Note that this is a completely subjective opinion. Postgre works better *for me*.

---

