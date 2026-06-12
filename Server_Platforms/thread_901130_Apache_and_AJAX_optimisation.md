---
title: "Apache and AJAX optimisation"
date: 2008-08-26
forum: Server Platforms
---

### Post by asmith3006 on 2008-08-26
Hi,

I've developed an AJAX chat system for the company I work for which has a php/mysql backend to it for storing and administering. The system requests new posts from the server ever 2-4 seconds (random time to make it feel more 'live').

This is all the server does. The chat system itself is very very small. The page with the chat box is inserted into an iframe on a page that comes from another server. The chat page itself is about 4kb in size and then the system returns 12B of data if there is no new messages and about 4K per new message. I.e. very little data is actually passed.

I'm having problems with capacity. Last night we had over 150 users using the system and I hit the "MaxClients" variable on Apache. I've raised this temporarily but I think this is a bad idea.

Apache seems to use one thread per user and I think that the default for the "KeepAlive" is 15 seconds. First of all, does this mean that the system will wait 15 seconds, keeping the connection to each user open, to see if a user requests another page? If so, this is bad for my system isn't it? Should I turn off the "Keep Alive"? (can this be turned off using website.url.conf or does it have to be turned off in apache2.conf?)

Also, I've read that it's possible to run apache as a single thread rather than one thread per user. Would this be better for my situation?

Edit: Finally, is there a way to find out how many clients I have connected? (i.e. how many of the "MaxClients" value I've used?)

Thanks for any and all help.

Andrew.

---

### Post by de0xyrib0se on 2008-08-26
> **asmith3006 said:**
> Hi,

I've developed an AJAX chat system for the company I work for which has a php/mysql backend to it for storing and administering. The system requests new posts from the server ever 2-4 seconds (random time to make it feel more 'live').

This is all the server does. The chat system itself is very very small. The page with the chat box is inserted into an iframe on a page that comes from another server. The chat page itself is about 4kb in size and then the system returns 12B of data if there is no new messages and about 4K per new message. I.e. very little data is actually passed.

I'm having problems with capacity. Last night we had over 150 users using the system and I hit the "MaxClients" variable on Apache. I've raised this temporarily but I think this is a bad idea.

Apache seems to use one thread per user and I think that the default for the "KeepAlive" is 15 seconds. First of all, does this mean that the system will wait 15 seconds, keeping the connection to each user open, to see if a user requests another page? If so, this is bad for my system isn't it? Should I turn off the "Keep Alive"? (can this be turned off using website.url.conf or does it have to be turned off in apache2.conf?)

Also, I've read that it's possible to run apache as a single thread rather than one thread per user. Would this be better for my situation?

Edit: Finally, is there a way to find out how many clients I have connected? (i.e. how many of the "MaxClients" value I've used?)

Thanks for any and all help.

Andrew.

In your case turning keepalive off probably wouldnt make too much of a difference since 2-3 seconds later it would re-appear. Actually it is better to keep it on in your case as a fork causes more system overhead.

Also when you say a single thread, actually usually apache does not run multiple threads but rather multiple child forks which are independent of eachother, this one if one bombs out it doesnt take down the whole server. You can try running it as one thread and see how it runs, keep in mind this would not affect the maximum connections at all, if you reach that it would deny new requests regardless if in forked mode or single thread.

Raising the max clients is not as bad as you think, as your usage would peak at some point at say 200 connections or so, this wouldnt go up forever.

---

### Post by asmith3006 on 2008-08-26
Why do you say my usage wouldn't increase? We are predicting (hopeing) to have ~1000 users on the system soon. If it's 20MB per child fork then that'd a hell of a lot of RAM needed if each user is going to get its own fork (which they would if the keep alive keeps the link alive for each user), or have I mis-understood?

Sorry if I'm being a bit thick, I've never configured servers for the business world before (only my nice little home server).

---

