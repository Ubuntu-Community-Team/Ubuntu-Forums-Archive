---
title: "Can website accepts parameters from each other?"
date: 2013-01-04
forum: Server Platforms
---

### Post by kenweill on 2013-01-04
As the title said, "Can website accepts parameters from each other"?

Is it possible for a website (1st website) to pass a parameter to another website (2nd website)?

Say for example, 1st website pass $openthis to 2nd website and then 2nd website will perform actions based on the parameters received from 1st website.

Same as functions can send and receive parameters from other functions.

I'm wondering if websites can also send and receive parameters from other websites and can perform actions based on the received parameters.

---

### Post by lisati on 2013-01-04
*Thread moved to **Server Platforms**.*

One web **page** *can* call up another and pass paramaters. They don't necessarily have to be part of the same website, or even be hosted on the same server.

What sort of thing did you have in mind?

---

### Post by kenweill on 2013-01-04
> **lisati said:**
> *Thread moved to **Server Platforms**.*

One web **page** *can* call up another and pass paramaters. They don't necessarily have to be part of the same website, or even be hosted on the same server.

What sort of thing did you have in mind?

To be honest, I wanted to fake the referring website (or something like that) via the use of the 2nd website.

Lets say for example, 1st website have a link to open up yahoo.com. Clicking on the link, instead of opening up yahoo.com will open up 2nd website and seconds later from the 2nd website, opens up automatically yahoo.com. In this case, "yahoo.com" is the parameter sent to 2nd website. Also in this case, yahoo should think that the traffic came from or thinks that the referring URL is the 2nd website, instead of the 1st website.

Of course, 2nd website is also valid and working. Means when opened, it has content in it as if it has nothing to do with the 1st website. Which also means that 2nd website works normally, no redirection when opened directly from browser or if no parameter is passed.

---

