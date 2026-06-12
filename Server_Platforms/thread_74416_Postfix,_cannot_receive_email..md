---
title: "Postfix, cannot receive email."
date: 2005-10-11
forum: Server Platforms
---

### Post by smsmasters on 2005-10-11
I have installed postfix and I can send emails fine with my email client, but cannot receive.

I get this message from the "Mail Delivery System":

> This is the Postfix program at host localhost.localdomain.

I'm sorry to have to inform you that your message could not be
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to <postmaster>

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

The Postfix program

<admin@elitehost.ath.cx>: unknown user: "admin"

I'm not sure what to edit in the config files, I am using webmin also. Can someone please help me to get this working?

---

### Post by wrtrdood on 2005-10-12
Hoo boy..

  I've been pounding on this a lot over the last couple of weeks and there are as many differing ways to set up Postfix as there are opinions about which one is the best.  There's a lot of stuff on how to set up a virtual environment configure spam tools, block ugly stuff and what have you.  It really depends on your needs.
  The message you show is rather generic and there's a lot of things that could be wrong.  My suggestion is to follow a good HOWTO for the Postfix setup you want to use.  For a very basic setup that works well take a look at these articles:

[http://www.unixreview.com/documents/s=9772/ur0505k/](http://www.unixreview.com/documents/s=9772/ur0505k/)
[http://www.unixreview.com/documents/s=9811/ur0506m/](http://www.unixreview.com/documents/s=9811/ur0506m/)

Very basic setup and it works well.

---

