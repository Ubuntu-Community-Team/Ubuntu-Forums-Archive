---
title: "printing demands authentification"
date: 2010-01-12
forum: Security
---

### Post by ddavidd on 2010-01-12
My wife tried to print.
(Printer and driver are in order, have worked)
A box appeared "authentification required to print document"
(error message not exact, translated)
Entered password.
Nothing happened until much later a little error was printed "SPL-C error - incomplete session by timeout"
I logged on under my account(which seems to count as root in this installation)
Tried again.
Same problem.

Printer permissions are that anyone may print
Printer queue contains all the jobs with a notice like "held awaiting authentification"
We just want to be able to print, no security controls at all!

Can anyone help, please?
I find nothing in teh online documentation or the forums, which normally solve problems like this

---

### Post by quixote on 2010-01-13
I'm not sure what's going on, so I don't have any exact suggestions.  I'd recommend getting onto the CUPS (=printer admin) page and see how many things you can kick.  (Also, curse a bit ....)

That is accessed by opening your browser and typing this address in the address bar (URL bar) at the top: [http://localhost:631/](http://localhost:631/)  (I know.  Super-intuitive.)

There are several tabs, like "Jobs" and "Printers."  

In order to do much, it'll probably want you to login as root.  For CUPS that is the username "root" and the password for the main account on the system (ie ddavidd in your case).  At least that's the way it works for me. 

Then go to the Jobs tab and kill all the pending jobs.  Go to the Printers, stop and restart any that seem relevant.  

There's no logout, if I remember right.  Just close your browser, or that tab.

See if it prints.

If not, maybe also try turning both printer and computer off, and starting back up.  Or you could start with this step.  Maybe that would cure it by itself.  

I hope something works.  Printer trouble is maddening.

---

### Post by ddavidd on 2010-01-14
Thanks very much for the suggestions, quixote!

I didn't even know how to access the browser configuration page, it's very useful.
It works again now, and what the logs show is that it simply didn't work on the 12th.
I certainly should have restarted everything, always the first try, but the children always want to print out the homework NOW before going to bed!
Error message: */usr/lib/cups/backend/mfp failed
Probably only means failed authentifcation.

Perhaps we will never know why it wanted authentification!

---

### Post by quixote on 2010-01-14
*Perhaps we will never know why it wanted authentification!*  Probably not.  Who knows what goes on in the tiny minds of printers.  Glad to hear it's working again!

---

