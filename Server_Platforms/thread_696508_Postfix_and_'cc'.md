---
title: "Postfix and 'cc'"
date: 2008-02-14
forum: Server Platforms
---

### Post by drhiii on 2008-02-14
A simple issue but have not found an answer after much searching...

Have Postfix/Dovecot/Spamassassin et al installed and running dandy.  Issue is I and others are unable to send email to ourselves, for things like testing, or 'cc'.  The logs return a message stating the email 'loops back on itself' and simply disappears.  Not bounce, and never makes it to its destination which is of course, back to the sender.  'cc' being useful for some things...

Anyone have thoughts on how to unlock this 'cc' characteristic?

Ubuntu and this community rock...

tx a mil

---

### Post by MJN on 2008-02-14
Ignore the 'cc:' aspect - it's just another 'To:' as far as the mail server is concerned.
 
What happens if you attempt to send an e-mail to yourself? Does it loop? Can yuo receive e-mail from external sources okay? And send out too?
 
If so (or even if not), post the relevent seciton of your log (/var/log/mail.log) and your Postfix config and we can take a look.
 
Mathew

---

### Post by faulkes on 2008-02-14
Best option is to paste some log output here so we can see what postfix is doing when mail is sent.

Faulkes

---

### Post by drhiii on 2008-02-14
Folks, thank you very much for responding to my cry for help.  I have not touched the configuration in the last couple of days but on a retest of 'cc' to grab some log examples, it worked.  Ermmm, kinda like being sick but when you go to the doc's for help, the symptoms disappear by the time you get there. 

So, it appears to be working by some act of providence.  Or, I will try and figure out what may have changed that caused it to work...

But thank you for the responses.  Is why I have totally switched to Ubuntu for everything.  The community....

---

### Post by MJN on 2008-02-15
I like the doctor's analogy... so so true! (exactly the same thing with cars and mechanics...)

Mathew

---

### Post by drhiii on 2008-02-15
Ya... after obsessing over it a bit, then stepping away from it, on return, it worked.  Go figure.  The doc, if there was one, would have been just as perplexed as me...

I am just grateful for this community.  I was fiddling with installations of Microport installs on a 386 back in 1986 to give one an idea of how far back I go.  Ubuntu and its community are tops...


> **MJN said:**
> I like the doctor's analogy... so so true! (exactly the same thing with cars and mechanics...)

Mathew

---

