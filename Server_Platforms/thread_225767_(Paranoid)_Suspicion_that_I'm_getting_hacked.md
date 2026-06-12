---
title: "(Paranoid?) Suspicion that I'm getting hacked"
date: 2006-07-30
forum: Server Platforms
---

### Post by manimani on 2006-07-30
Hi! I was surfing the web yesterday, having a terminal and x-chat and some other programs open. Suddenly all programs crashed, and from that moment my processor activity applet shows a pattern of barely notable activity approximately once per second, which wasn't there before. I.e. even when no programs are running. 

I was just revealing some not very pleasing information about some ill-meaning people on the web. So that's one reason that the thought appeared in my head that I'm being hacked in retaliation. But unfortunately I know nothing about computer security.

Some background information:
I'm still using  Breezy Badger, and I've set the Ubuntu updates so that I only get to update every tenth day. Firefox is version 1.0.8. My root password is pretty simplistic.

---

### Post by johnnymac on 2006-07-31
So here's some questions BUT FIRST UNPLUG YOUR SYSTEM FROM THE INTERNET

1.  Do you have a firewall or router, or are you just plugged into the net?
2.  Do you have any antivirus installed or root-kit hunter?
3.  What does dmesg say?  Take a look at /var/log/messages as well.

JN

---

### Post by Shay Stephens on 2006-07-31
Do you have a network printer setup?  Once I set up a cups printer, I started getting small amounts of network traffic like you describe.

---

### Post by manimani on 2006-07-31
(writing from an even older ubuntu installation on another partition)

The requested files can be read here: [sudo_dmesg_output.txt](http://chinoiserie.atspace.com/sudo_dmesg_output.txt),
[var_log_messages.txt](http://chinoiserie.atspace.com/var_log_messages.txt) (I hope that revealing these files to the world isn't itself a security risk :^o ). Unfortunately I'm not capable of interpreting them myself. The "mystical processor activity" started to appear sometime in the late evening of July 29 or perhaps in the early night of July 30, Swedish time (GMT+1). I'm not sure whether the logs are in local time.

I have no firewalls or routers, and no antivirus programs or root-kit hunters that I know of, just a straight Breezy Badger home desktop installation (but of course with many extra programs installed whereof several are unofficial ones). And I have no printer. 

The "mystical activity" continues to appear even when the internet is "unplugged".

Javascript was on in Firefox 1.0.8, which makes the whole setup sort of fit with this latest security notice: [http://www.ubuntu.com/usn/usn-327-1](http://www.ubuntu.com/usn/usn-327-1) 

Now that the weekend is over I'm going to go buy some backup memory (I stupidly don't have enought memory atm to do a complete backup) and then reinstall the operating system from scratch. That is, unless you can tell me that this is something completely normal and nothing suspicious. 

Thanks a lot for your help!

---

### Post by skylark on 2006-08-01
Yes, if you have any doubts, backup and reinstall.

If you don't have firewall protection (via a router) then you might consider installing offline. Before connecting to the internet install and setup a firewall (at least on your local computer). Note though I've found installing Ubuntu from CD offline often takes a bit longer (it "hangs" for a few minutes at various steps while it tries to find an internet connection, but maybe I do something wrong).

There are some simple but effective paranoid steps you can take though.

* If you browse the web using Firefox with Macromedia Flash player installed, consider installing something like [FlashBlock]("http://flashblock.mozdev.org/") which by default disables flash movies, but allows you to click and watch those you do want to see. Also consider disabling Javascript by default except for certain web-sites you trust.

* Obviously be careful opening any media files and documents that you receive via email or download. In some cases you might consider using more unusual programs to view these files (eg AbiWord instead of OpenOffice for MS Word documents) since any malicious payload is likely to be targeted at mainstream applications.

* If you are in an environment where others may have access to your computer (eg a college dormitory) then take measures to increase the physical security of the box, and check for keyloggers etc.

* Really paranoid individuals may go to the length of viewing all untrusted content in a virtual machine... currently this is quite inconvenient though, but I believe it is ultimately where we should be going.

---

