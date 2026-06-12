---
title: "Ubuntu Software Centre has no reload option??"
date: 2013-06-09
forum: Ubuntu, Linux and OS Chat
---

### Post by monkeybrain2012 on 2013-06-09
I always use synaptic, but I answered a thread and tried to tell someone a gui way to add a ppa, so I opened the Software Centre to have a look and man, there is no reload option?! so in the end you have to go to the terminal to do sudo apt-get update. I cannot believe that the USC's design would be so stupid, so I googled a bit and found this.

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/690938](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/690938)

It is marked as "won't fix" and the explanation

>                         Thanks for the report, Matt, and sorry for the slow response.

 There is nothing in this report  that states why a visible control to update the apt cache would be  useful or desirable. Adding a function to do that would be one possible  solution to several problems, for example, [bug 677076]("https://bugs.launchpad.net/bugs/677076"), [bug 574155]("https://bugs.launchpad.net/bugs/574155"), and [bug 782953]("https://bugs.launchpad.net/bugs/782953").  But it would be a poor solution, because most people would not  understand that they needed to do it. Fortunately, in each case, it is  possible for Ubuntu to be smart enough to update the cache  automatically, so a function to do it manually is not necessary.

              


??? What kind of rationale is that??  I am sure glad that I was not one of "most people" when I was newbie to Ubuntu a few years ago, or I wouldn't even know about synaptic.

**Edited**: Hey mods, there is an extranous "No" in the thread title, don't know how to edit it. Please remove the first "No" (so it should be "Ubuntu Software Centre has no reload option??" Thanks.

---

### Post by craig10x on 2013-06-09
What he is saying is that with the ubuntu software center, it reloads each time you open it, automatically and that is why there is no manual option....on synaptic package manager, i believe you always have to manually reload it...

---

### Post by deadflowr on 2013-06-09
> **craig10x said:**
> What he is saying is that with the ubuntu software center, it reloads each time you open it, automatically and that is why there is no manual option....on synaptic package manager, i believe you always have to manually reload it...

Is that why it opens soooooooooooooooo slowly?

---

### Post by MadmanRB on 2013-06-09
For me its a big hole as it doesnt see the repos, and it really doesnt reload.
Yeah software center is rather stupid methinks when it comes to this bit.

---

### Post by craig10x on 2013-06-09
@deadflowr: probably ;)  Although, just out of curiousity i just opened it...only took about maybe 7 to 8 seconds...if it's refreshing, that is not so bad...

---

### Post by oldos2er on 2013-06-09
> **craig10x said:**
> What he is saying is that with the ubuntu software center, it reloads each time you open it, automatically and that is why there is no manual option....on synaptic package manager, i believe you always have to manually reload it...

If I'm not mistaken Synaptic will prompt the user to reload the sources.list after any change in repositories has been made. Funny how this behavior was the default for a long time before Software Center existed, and didn't cause much if any confusion (that I can recall at least).

---

### Post by monkeybrain2012 on 2013-06-09
So to update your sources list you have to quit the USC and relaunch it instead of clicking a reload button? I can't see how it is more convenient or intuitive.

---

### Post by Copper Bezel on 2013-06-10
> **oldos2er said:**
> If I'm not mistaken Synaptic will prompt the user to reload the sources.list after any change in repositories has been made. Funny how this behavior was the default for a long time before Software Center existed, and didn't cause much if any confusion (that I can recall at least).
Theoretically, if Synaptic could respond to that change, then USC could simply update in the background automatically and add an item to "In Progress" to indicate that it's doing so.

If this is the answer to why USC takes so damned long to launch, though, it's both crazy (because there's not remotely enough time for it to be updating) and somewhat reassuring.

---

