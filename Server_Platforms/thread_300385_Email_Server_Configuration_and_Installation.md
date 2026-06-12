---
title: "Email Server Configuration and Installation"
date: 2006-11-15
forum: Server Platforms
---

### Post by tim.n9puz on 2006-11-15
I would like to set up an Ubuntu based email server for an organization of about 30 users. I've looked at some of the howto's, etc. but I'd really like to know some things in addition to what's typically covered in them. ](*,) 

First, we have a domain name but what needs to be done as far as configuring mx records, installing DNS, etc. so I end up with a working system and an address like mail.ourdomain.com to use in the user's client programs?

Second, is there anything like a "Ubuntu Email Server for Newbies" or something similar? The tutorials and howto's are nice but the ones I've read so far leave me without much of an idea what to look for if I type the suggested commands and don't get the response/effect indicated by the author.

I'm not expecting a response that details all these answers and I have some Linux experience with web servers, MySQL, Samba file servers, etc. There's just a lot of pieces to a mail server to get your arms around all at once. I'm hoping for pointers to a good book, web site or series of articles.

Thanks in advance!

Tim

---

### Post by jimcooncat on 2006-11-15
Some DNS tips -- I'll leave email itself to others and the howtos you've found.

For incoming mail, I farm out my dns services instead of running my own bind. Your ISP or domain name provider might provide you these services. I use zoneedit.com, and have been happy with them -- there are others out there as well.

For outgoing mail, you can use your ISP's DNS servers. It's the same ones you plug into your internet connection setup. If they give you a lot of "name not found" errors, then find some other DNS servers to use.

You'll also want to set up the Sender Police Framework. In your DNS setup, add a TXT record. Mine's similar to:

"v=spf1 mx a:dslrouter.jimcooncat.com a:mymachine.myhouse.us ~all"

And ask your ISP to give you a reverse DNS record. They put this record in their setup, you don't put anything in yours. This shows your ip address (185.22.156.63) belongs to "dslrouter.yourcompany.com".

Both of these things are preliminary to the hoops that AOL will put you through when you try to send mail to any of their members. So have them in place before you start. I've only need to do this for AOL, but I suspect more companies will be jumping on the SPF bandwagon soon -- maybe not ban incoming mail outright, but use it to help with spam filtering anyway.

Reference: [http://en.wikipedia.org/wiki/Sender_Policy_Framework](http://en.wikipedia.org/wiki/Sender_Policy_Framework)

---

