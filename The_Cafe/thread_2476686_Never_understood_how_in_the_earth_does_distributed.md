---
title: "Never understood how in the earth does distributed file system works?"
date: 2022-07-03
forum: The Cafe
---

### Post by rirelguvatbaohagh on 2022-07-03
Since DFS were originally built with UNIX system, I think this could be relevant here. I saw a DFS post in this forum so I'm here.
I am not talking about HDFS,GFS,but the basic DFS architecture.
[IMG]https://media.geeksforgeeks.org/wp-content/uploads/20220422212439/fileservicearch-660x539.png[/IMG]
How does this work actually? And what's the difference between networked hard disks all around the world vs distributed file system? I have already passed distributed system course in university 5 years ago. And I still have notes. But the notes were written by me so they don't mention the details. I just memorized  "text name->UFID", "implements operations" and few commands and passed with okish marks.
Teachers were non-existent, it was all our effort. But I don't think any teacher in any uni in world, taught this subject any better because of lack of proper resources for this. Every books I see say the same thing, every pdfs in internet say the same thing. It's annoying. Video courses are non-existent. There was one indian guy's video about DFS for system design but it said nth in 20 mins.

I'd want to learn how that architecture functions? I honestly don't know what question should I ask because I am not sure what I'm confused.

---

### Post by The Cog on 2022-07-03
I looked at ceph some years ago, but never got a chance to implement a cluster. This video explains some of the basics. [https://www.youtube.com/watch?v=c4sgV_FEb4I](https://www.youtube.com/watch?v=c4sgV_FEb4I)

Basically, distributed filesystem chops your stored data (files, disk images, whatever) into chunks and stores the chunks. For example, I think ceph stores 64MiB chunks, so a 1GiB file would need 16 chunks. The DFS will make duplicate copies of each chunk (perhaps 3 copies of each), and scatter them around the DFS nodes, taking care that all the copies of any chunk are on separate servers. This means that a failure of one server leaves you with 2 copies, and it will re-make a third copy to maintain redundancy. When you write a file, or read a file, you are not aware of the chunking and distributing - that's handled by the DFS. All you see as a client is a system that stores enormous amounts of data and doesn't lose any. E.g., for HDFS (which I have used), the command "[FONT=Courier New]**hdfs dfs get /logs/dns/2012/07/03/west-coast.txt**[/FONT]" will retrieve that log file. Of course, for a dfs, you would normally be running analytics programs, not fetching file content by hand. Ceph has the ability to store block device content (emulating giant hard disks rather than emulating a filesystem), if that's the way you want to go. Hope this helps.

---

