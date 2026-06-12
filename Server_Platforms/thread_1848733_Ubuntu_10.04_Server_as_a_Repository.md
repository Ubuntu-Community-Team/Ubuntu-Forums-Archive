---
title: "Ubuntu 10.04 Server as a Repository?"
date: 2011-09-23
forum: Server Platforms
---

### Post by RevPhil06 on 2011-09-23
Yeah, I know-there's tons of threads like this-I've looked at many guides, much googling, and nothing is quite accomplishing what I need it to do, or either I'm not realizing they would. 

First off, I volunteer for a local non-profit organization that donates computers to low-income families and recycles computers. We are wanting to set up a server (it's a Supermicro 1U, with a 160 GB IDE HD, don't remember the rest of the specs) to pull in the updates so we can update the computers we donate. The server already has Ubuntu 10.04 LTS Server on it and we install Ubuntu 10.04 LTS on the machines we give out. We've configured the server to be connected to the internet so that way we can keep it up-to-date. 

We don't need anything like Apache, SQL, etc., we just want to have the updates and such on our own server while being able to update the server via the internet, but have yet to find anything for this specific purpose. I don't know if that would in effect be a local mirror, but all the instructions for a mirror I've found include stuff like Apache and so on, and we really don't need or want that. 

I figure this would also be a good way for me to get some better experience with the command line. 


UPDATE: Got the server up and running, it successfully mirrored the repositories and was able to update my Acer Aspire One netbook with it. Only took the server from about 5:00 PM (Eastern, GMT -5:00) Friday night to 4:30 AM Monday morning (Eastern, -5:00 GMT) to mirror.

---

