---
title: "Goodbye Windows Server Hi Ubuntu Server"
date: 2008-02-05
forum: Server Platforms
---

### Post by hombert on 2008-02-05
Hi All,

I' am sure this question is posted too many times, and sorry of it is. Could not find any topics who helped me out on this.

**My situation:**

I' am on Windows Small Business Server R2, but after i used the desktop version of ubuntu i' am addicted to the system stability and functions.

So i decided to get our business over to 2 Ubuntu Servers. The server now is as said an SBS server with exchange working.

**New Situation:**

I want to install 2 new servers that will take the role of my old server. 1 Server who does Domain/DHCP/Print server controller. And one witch will function as mail server. These to need a connection between because the mail server must be into the domain.

*I' ve read several tutorials how to set up a simple OpenLDAP+Samba server but this does not cover the whole thing. And as said is a simple tutorial witch could not be compared to a fully working SBS server.*

Then second thing is we have people working outside the company, the people need to read their mail.

*Also did research and i know this could be done with squirrel or Roundcube, also tutorials for this is basic.*


Can somebody help me out because i really want to use ubuntu in company! Maybe some can reffer me to a good tutorial/topic or even a book witch covers this all!

Thanks in advance peeps and hopefully this community is as good as they say they are!!! :lolflag:

Regards,

/hombert

---

### Post by jonabyte on 2008-02-05
Here is my advice/opinion.

Try setting up Ubuntu as a file/print server first. Play around with it until you are comfortable, all the while keeping the sbs server as the domain and email server.
Then, try and "convert" the Ubuntu server to act as the domain server. You may encounter some issues with the sbs, but I have seen this work.
Lastly, when you are comfortable with the domain server, try to migrate the email server to whichever version of mail server you prefer.

The reason I suggest you do this in steps is based on my experience with migrations. It is much easier on you and your users to move one step at a time. 

BTW, if you haven't "tried" Ubuntu Server, its default install is without a desktop, all command line...which isn't a bad thing, but does tend to shock some people.


Good luck.

---

### Post by UbuWu on 2008-02-05
[https://help.ubuntu.com/ubuntu/serverguide/C/index.html](https://help.ubuntu.com/ubuntu/serverguide/C/index.html)

---

