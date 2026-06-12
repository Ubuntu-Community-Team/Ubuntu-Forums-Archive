---
title: "Index a Samba Server?"
date: 2011-11-03
forum: The Cafe
---

### Post by hambone79 on 2011-11-03
I have a file server at home running Samba and about 10 years worth of files. The files include images, video, documents, and lots of CAD data. I have tried my best to keep the server organized, but I still find it hard to find files sometimes. Right now I generally ssh into the server and use the "locate" command to find a file I'm looking for, but this is very inconvenient for computers on my network that are not running Linux. 

Right now I have a few ideas of how to solve this problem:
1. Index the entire file server using a desktop search tool on each of my computers.
2. Create a common index that each of the computers on the network can access.

I want to avoid option 1 since it creates alot of unnecessary traffic, but I don't know of a cross platform solution for option #2.

Anyone out there have any ideas?

---

### Post by BrokenKingpin on 2011-11-03
> **hambone79 said:**
> Right now I generally ssh into the server and use the "locate" command to find a file I'm looking for, but this is very inconvenient for computers on my network that are not running Linux.
What other OSs are we talking about here, Windows? If so why can you not just a search through Explorer on the samba share? I also have a lot of files on my file server, but I haven't had issues searching the samba shares from Linux or Windows.

If you issues is that it searches too slow you could right a script to generate an index (text file or DB), and have that run in a cron job every night to keep it updated. If you keep the index on the server then you could just search the index for the file location. This is a pretty dirty solution though.

You may just want to spend some time and reorganize the file server so you can limit your searches to a smaller set of directories if you have a general idea of what you are looking for.

---

