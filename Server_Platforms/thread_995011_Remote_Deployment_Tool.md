---
title: "Remote Deployment Tool"
date: 2008-11-27
forum: Server Platforms
---

### Post by Dark_Neo on 2008-11-27
At my work we have a local Ubuntu dev server, and a dedicated Ubuntu server as our main webserver.

Before we brought our local dev server, we made a script on the dedicated server 'deployfile' which would allow us to diff/replace/merge files from the dev virtual hosts to the live ones.

Now we're developing locally, our script won't work across the network, so we're looking for a replacement, preferably with a web interface (so the boss can use it too :p) does anyone have any suggestions?

It would have to compare files across the network, and allow us to deploy (both ways for restoration), and most importantly be simple to use - even version control systems like CVS/SVN are too complicated for my boss to want to use.

---

### Post by Philio on 2008-11-27
SVN is very easy to use if you use Tortoise (Windows) or WebSVN.

---

