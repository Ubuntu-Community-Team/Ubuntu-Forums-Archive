---
title: "Open Source Licensing. What to consider?"
date: 2009-05-11
forum: The Cafe
---

### Post by WinterWeaver on 2009-05-11
I have written a django application for adding streaming video to small websites.

Now, I want to make it freely available under a open source license and give everyone the chance to use it and contribute to it. Unfortunately I do not have much experience or knowledge on this, and I noticed that there are many out there to choose from, hence this thread.

Let me explain what I want the licence to provide.

**Firstly**, I want people to be able to freely distribute the app.

**Secondly**, and there may be some discussion on this matter, I cannot decide whether I want a licence that forces people to make definitive works open source/free. I dont like the idea of forcing them. In other words, if some company makes a derivative work, they should be free to decide if they want to close the source, or make it available again. What do you guys think? 

**Thirdly**, because the applicaiton is a Django application, how would I know if the licence of my choice will be compatible with django's (or python even) licensing model?

I would be greatfull for any input :)

Thanks,

WW

---

### Post by fatality_uk on 2009-05-11
Goo bedtime reading
[http://www.opensource.org/licenses/alphabetical](http://www.opensource.org/licenses/alphabetical)

---

### Post by WinterWeaver on 2009-05-12
hmm... I think I'll stick with the BSD Licence for this one. Django uses it, and from what I could make out, it's perfectly suited for my use case.

---

### Post by WinterWeaver on 2009-05-12
Am I supposed to put the Licence into the top of every python script, Just the package __init__.py, or in the folder as a text file?

---

### Post by mister_pink on 2009-05-12
Different projects use different standards. Some are quite picky. The usual thing is to have a file called "COPYING" with the licence in it, and copyright notices in all the scripts, maybe saying which licence is used and to see the "COPYING" file for more details.

---

### Post by WinterWeaver on 2009-05-12
Thanks, I'll do it that way then, :)

---

