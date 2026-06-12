---
title: "ubuntu servers for small business - what should I do?"
date: 2011-04-29
forum: Server Platforms
---

### Post by abandonedthe_mulletator on 2011-04-29
I recently acquired a sun server rack with 4 blades.  I want to use it to imporve my workplace.  We have 4 employees and do lots of GIS and CAD work.  I want the servers to run on Ubunutu, I have a personal Ubuntu server at home and love it.

I want the servers to act primarily as centralized data server.  What is the best way to go about this and what additional hardware do I need?  I think we need a SAN hard drive blade and I want to set up a raid array.  I'm new to this kind of stuff so correct me if I'm wrong.  Most of my co-workers use windows so the data server must be able to work with windows.

I think one blade should be able to handle the data serving, I'd like to cluster the other three somehow to use for heavy GIS software.  I have no idea how to do that.  Any ideas?

---

### Post by matthew.parlette on 2011-04-29
> **the_mulletator said:**
> I think one blade should be able to handle the data serving, I'd like to cluster the other three somehow to use for heavy GIS software.  I have no idea how to do that.  Any ideas?

Unfortunately I can't really help you that much, but I have been interested in clustering servers, and started reading through this thread, which may be a good place for you to start:
[http://ubuntuforums.org/showthread.php?t=1030849]("http://ubuntuforums.org/showthread.php?t=1030849")

---

### Post by MBybee on 2011-04-29
I think there are some additional pieces of info needed to help provide recommendations:

1) What OS are the client workstations?
2) What kind of clustering are you looking to do - HA, Failover, etc
3) What sort of data are you serving? Is this flat file storage, or more like a wiki/documentation server type of thing?

---

### Post by dtfinch on 2011-04-29
This might be a silly question, but are the Sun blades x86 or SPARC?

---

