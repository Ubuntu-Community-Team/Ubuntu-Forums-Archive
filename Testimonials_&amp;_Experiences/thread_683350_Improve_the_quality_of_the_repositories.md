---
title: "Improve the quality of the repositories?"
date: 2008-01-30
forum: Testimonials &amp; Experiences
---

### Post by Robvdl on 2008-01-30
Ok, I'm not sure if this is the right title for what I am about to explain.

I have been running Ubuntu since dapper, and love it. One thing I have noticed that comes up more and more however, is it fails to do sudo apt-get update properly, and you either get a BADSIG error, or the server cant be contacted at all.

This can be a bit annoying, as when you do updates, you get warnings that the packages you are about to install cannot be trusted, yet they come from the official Ubuntu repositories. The thing is, the servers pretty much always seem to give me BADSIG errors lately, why?

Doing sudo apt-get update continuously always plays up on the exact same server lines (usually universe or security). Now I have similar problems with the NZ servers, as well as the US servers. Although the US servers appear to be more reliable at current.

Another thing, is during Gutsy setup, if for some reason it fails to contact one or more of the servers (or if you install in offline mode), your /etc/apt/sources.list entries will be automatically commented out, and the file is full of these:

# line commented out, because the server could not be contacted.
# deb ....

If possible, if something could be done to improve the servers, so you do not always get BADSIG errors would be great.

But most importantly, during setup, if any servers could not be contacted, no lines should be commented out of /etc/apt/sources.list at all, because it's a new installation anyway. This really confused my dad when he tried installing Ubuntu offline, and I had to help him fix the /etc/apt/source.list file up straight after a clean install, but this shouldn't need to be done, you should be able to install Ubuntu offline.

---

### Post by wolfen69 on 2008-01-30
i guess different people have different experiences. i have NEVER had a problem with the repos or my sources list. i think if this was a big problem, it would be well known and talked about more. i read **alot** of posts everyday, and really dont hear of the problem you describe.

btw, i hear windows doesnt have this problem. check it out. :-)

---

### Post by matthewcraig on 2008-01-31
There's this fantastic feature that I only just discovered.  Not sure how long it's been there... In your repository configuration, you can choose a different repository and there is a button to find the fastest one to your computer.  Click the Download From... -> Other to access it.

Truth be told, however, I tried a different server and it ended up not having a certain package I needed.  I switched back to the default primary, which did have the package.  That may have just been a rare event though.

Bottom line is change your server if it isn't working for you!  :)

---

### Post by Robvdl on 2008-01-31
> **wolfen69 said:**
> btw, i hear windows doesnt have this problem. check it out. :-)

I don't think so, Windows is only for games is it not :) Plus try developing with Python on Windows, installing all those different packages is a real pain in Windows.

Anyway, I am not sure why this happens, it seems to be something to do with a bad GPG key on the server. I try re-synching the server several times, try both the US and NZ servers and same thing happens.

I do see the option, where you can find the best server, I will have to try it out.

It doesn't bother me personally too much, because I know I can stil install and update software, by ignoring the BADSIG warnings.

The thing is other people have asked me about it (it scared them initially), my dad, several of my friends. Come to think of it, I am pretty sure they were all on TelstraClear cable connections. I don't normally have problems with my cable connection, but maybe it's something with TelstraClear?

---

