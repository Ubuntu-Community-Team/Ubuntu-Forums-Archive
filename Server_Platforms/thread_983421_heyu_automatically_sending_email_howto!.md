---
title: "heyu automatically sending email howto?!?"
date: 2008-11-15
forum: Server Platforms
---

### Post by three_jeeps on 2008-11-15
Hi:
I've installed heyu on my ubuntu server and it is working fine, both locally and over the web.  I've read through the heyu man page and trundled through the code to get an idea of  how it works. Basically, one can send commands to turn things on/off via the CL, or one can combine the commands into a script file that can get executed when an event occurs.
So he is the issue:

I'd like to have an event, such as the turning on of an module (either directly using the X10 palm controller, or by using the MS16a motion sensor) send a mail message to a number of addresses. 

It seems that I have enough of the pieces, but can't quite figure out the best (any?) way to achieve this.

I have configured and am running: postifix mta, mysql, spamassin, and apache2.  Mail works fine..I can send/receive within my LAN, as well as through my domain.

I can construct the event detection with the script language but not sure how to fire off an email message.  There is a script to send a message to stdout.  Perhaps a way to redirect to the postfix queue?

Any suggestions/pointers would be appreciated......any explicit how-tos even more appreciated.

Thanks!
J

---

### Post by lcw on 2009-02-25
Did you ever get the answer you were looking for?  I found this link which included comments from Mr. Sullivan and thought it may help.

Regards 

[http://forums.x10.com/index.php?PHPSESSID=a799034fce785cb34cf974c98c4a9c9a&topic=9880.new](http://forums.x10.com/index.php?PHPSESSID=a799034fce785cb34cf974c98c4a9c9a&topic=9880.new)

---

### Post by three_jeeps on 2009-02-25
> **lcw said:**
> Did you ever get the answer you were looking for?  I found this link which included comments from Mr. Sullivan and thought it may help.

Regards 

[http://forums.x10.com/index.php?PHPSESSID=a799034fce785cb34cf974c98c4a9c9a&topic=9880.new](http://forums.x10.com/index.php?PHPSESSID=a799034fce785cb34cf974c98c4a9c9a&topic=9880.new)
Hello...no, I haven't received any replies.  Thanks for the pointer.  I forgot that a email message can be launched from the CL.  
I sort of got side tracked looking at a port conflict problem with heyu and hylafax.  Then December came and my free time evaporated.
I appreciate the help.
Thanks again...
J

---

### Post by OmahaVike on 2009-08-03
when i had my heyu up and running, i used mutt (a command line email program) to send out messages when a module fired.  it's a very basic command line email program that works really nicely with heyu's scripting abilities.

what i did was set up some shell scripts, so when a module was tripped, heyu would execute the shell script, which would send out an email.

---

### Post by three_jeeps on 2009-08-03
> **OmahaVike said:**
> when i had my heyu up and running, i used mutt (a command line email program) to send out messages when a module fired.  it's a very basic command line email program that works really nicely with heyu's scripting abilities.

what i did was set up some shell scripts, so when a module was tripped, heyu would execute the shell script, which would send out an email.

Thank you!  Just to clarify...the shell scripts you set up were contained in x10.config?  The current version of heyu (v2.7) allows scripts to be launched based on a trigger (e.g. an x10 module turning 'on' with an embedded 'sendmail' command with the 'To' field and the 'Message' field filled in.  I am assuming that is what you used and did not 'roll your own.'
-J

---

### Post by OmahaVike on 2009-08-04
right.  well, sorta.

i first set up a basic shell script and threw it into a directory (let's say, /home/heyu/A1Tripped.sh) which looks like this

```

echo "This is the body of the email" | mutt -s "A1 Tripped!" threejeeps@wherever.com

```

if you google around enough, you'll find out that mutt is pretty powerful for stuff like this -- heck you can send your x10 logs to yourself to really see what's going on.

then, i changed that file to be executable.  i ran the script just to make sure i had all of my mutt settings configured appropriately (POP/SMTP/etc).

once i was sure that the shell script worked, then i pointed my x10.conf script settings to my /home/heyu/A1Tripped.sh file (must include the full path) to fire off whenever A1 was turned on.

hope your patience has been rewarded.  looks like you've been waiting around for an answer for a while.

---

### Post by daqron on 2010-12-17
Still working on this project? What did you end up with?

I've been working on something similar recently. I'm curious to see what others have done. X-10 is old technology by now, but no less fun to play with than it was 15 years ago. 

I am pretty sure there's an iPhone app that lets you do everything remotely now, but who the hell wants some shiny user-friendly program with "features" and whatnot when you can hack together semi-reliable perl scripts with bubble gum and duct tape?

---

