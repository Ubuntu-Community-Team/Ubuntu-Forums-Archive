---
title: "Help finding Home Inventory Software?"
date: 2007-04-25
forum: The Cafe
---

### Post by mroc on 2007-04-25
Hi.  I've been using GNU/Linux (Ubuntu specifically) exclusively for almost a year now and really appreciate the hard work of the developers and the community.  Also, the Ubuntu forums have been really helpful in answering a lot of questions.  So a thank you to everyone is in order.  (Switched most of my family over to Ubuntu as well).

This is my first time posting a question though, so here goes:

My parents are looking to do an inventory of their home (mostly for insurance purposes).  My first thought was "with all the great open database software out there, someone must have written a good program for doing home insurance inventories."  I've searched around a bit, but haven't come up with much.

So, any advice on a (simple-to-use) open source home inventory program?  I'm hoping to find something that will associate multiple images and things like serial numbers with items and is contained as a single database file (since it would make backups much simpler).

Thanks for any input!

---

### Post by ssodhi on 2007-04-26
Hiya,
I can't think of anything off hand, but if you are at all acquainted with MySQL, or better yet Oracle (Yay for proprietary stuff! SQL/Plus is a beauty for reports), you may wish to look into writing yourself some reports queries, and setting up a basic application solely in your chosen RDBMS. You'd really just need a number of tables for the different categories (Actually, you don't, but it would be easier for you), and to assign each item a serial number and description, and manually go through and enter the data. You don't seem to need anything overly advanced.

If you'd like further help, feel free to drop me a PM and I can help you out with getting MySQL installed and setting up your Schema.

-Sanjay Sodhi

---

### Post by mroc on 2007-04-27
Hi,

Thanks for the reply.  I appreciate the offer to help and, if I had a bit more time on my hands, I would likely take you up on the offer.  The end of the semester is approaching very quickly, however, and I don't expect to have any time in the near future to invest in learning things the right way.

I was hoping someone had created a neat little program for this, but it sounds like if such a project does exist, it is not well known.  My goal of finding an open source program was mostly motivated by the lack of flexibility in some of the "Shareware" programs I found.  My experience has been that open source programs, while often in heavy development, tend to include more useful features than the "Shareware" programs.

Anyone else have a less involved solution?  (Something with not-as-steep a learning curve?)

Thank you again for your suggestion.

---

