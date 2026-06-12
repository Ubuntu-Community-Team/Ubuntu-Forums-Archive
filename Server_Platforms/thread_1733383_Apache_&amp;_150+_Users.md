---
title: "Apache &amp; 150+ Users"
date: 2011-04-19
forum: Server Platforms
---

### Post by localfiend on 2011-04-19
I'm looking to build a website to host small secured files for at least 150 different users (each user will have their own set of files, and will not have access to the others).  I can think of several different ways to accomplish this but thought it might be a good idea to bounce ideas of someone else in case there's an easier way.

Right now I'm thinking that the best/easiest way would be to create a different directory (inside a web folder) for each user, a separate password file for each, and use httpd.conf to control access to the directories.

The above idea is simple, and I can get it done easily, there's just the small problem of setting things up so that I can have someone with less computer skills than me to be able to add/update users and passwords.

Are there any tools out there that would help out on the editing front?  Am I going about this the wrong way?  

I'm thinking that this is a pretty standard thing to do in the industry, but I'm not finding any good ways to make things easier on the less computer literate.

---

