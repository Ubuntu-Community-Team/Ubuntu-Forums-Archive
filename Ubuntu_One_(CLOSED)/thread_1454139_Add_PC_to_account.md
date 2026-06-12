---
title: "Add PC to account?"
date: 2010-04-14
forum: Ubuntu One (CLOSED)
---

### Post by candtalan on 2010-04-14
New clean install of 9.10 and updated, however I cannot see how to add the newly installed machine into my existing U1 account.

I have clicked
applications>internet>ubuntu one
and clicked connect
it now says 'connecting'

I see the applet with an exclamation mark in it

I have signed into my U1 account on the web, I see the expected content (approx 11 GB of stuff).
I click on 'account' and see correctly that there are no machines allocated and to add a machine I must look at the install U1 pages, which I look at and see that in my 9.10 U1 is pre installed.

OK, so how do I add a machine?

In system>preferences 
I see no ubuntu one listed

Using synaptic it looks as if ubuntu one is in fact installed, but I am not exactly sure what details to look for

---

### Post by candtalan on 2010-04-14
Thanks to rye on irc this is solved. 

The syncdaemon needed to be stopped,  although this seemed very reluctant to stop. When restarted via a termional things started to work and I was invited via a browser window to accept the machine into my account after I clicked on the applet.

---

