---
title: "Unsupported key algorithm in certificate?"
date: 2015-01-30
forum: Security
---

### Post by cogset on 2015-01-30
I've just seen these lines in auth.log ```
mate-keyring-daemon: unsupported key algorithm in certificate: 1.2.840.10045.2.1
```after digging in the logs looks like it occurs a few times in the last months (I can't say if it was there even before the last logs I have): what is this about? 

I think it is related to the alternative desktop I have, because I can also see this other message ```
gnome-keyring-daemon: couldn't register in session: The name org.gnome.SessionManager was not provided by any .service files
```and I suppose the two things are somewhat related.
What is going on here? Is it a real issue or can  I just ignore this messages?

---

### Post by cogset on 2015-02-03
Would I be better off asking this on the mate forums?
Generally speaking, what would this "*unsupported key algorithm in certificate" *be all about?

Does it look to you like a proper security issue or is just a warning?

---

### Post by bashiergui on 2015-02-03
Only because you haven't gotten any other responses...

I Googled a bit on the topic out of curiosity. Based on the responses I saw it looked like mate failed to handle the keyring hand off properly causing those errors. You might set up a script to notify you if the events are seen again, then you can figure out what application caused the errors. Based on the postings about this error message on the internet, this error message results in a failure to auth, so I can't get to excited about the error message. In other words some app that uses the keyring is throwing errors which might help you troubleshoot. The error message does not appear to indicate something necessarily nefarious is happening.

---

### Post by cogset on 2015-02-04
Thanks, I too googled that but couldn't find tell from the results what this message was about.
> You might set up a script to notify you if the events are seen again,  then you can figure out what application caused the errors.
That sounds interesting, if only I knew how to do it.

---

### Post by bashiergui on 2015-02-04
Or you could do it manually. Look for those error messages and then look in the other logs to see what was running at the same time. If you can find a recent event then hopefully you can also remember what you were doing at the time.

---

