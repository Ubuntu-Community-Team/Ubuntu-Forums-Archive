---
title: "Webmin Help"
date: 2008-12-21
forum: Server Platforms
---

### Post by spynappels on 2008-12-21
Hi Guys,

 Can anyone tell me where to look for documentation or a tutorial on how to use Webmin? The official Wiki does not seem to work, I just get time out messages, and I'd like to know how to start the service and access it from another computer etc. Searching did not throw up too many clear replies either.

 Thanks, Stefan.

---

### Post by windependence on 2008-12-21
[http://www.lesbell.com.au/Home.nsf/504ca249c786e20f85256284006da7ab/97e8323a9cb248beca256caf0019668c?OpenDocument](http://www.lesbell.com.au/Home.nsf/504ca249c786e20f85256284006da7ab/97e8323a9cb248beca256caf0019668c?OpenDocument)

[http://maketecheasier.com/how-to-manage-unix-linux-systems-using-webmin/2008/12/18](http://maketecheasier.com/how-to-manage-unix-linux-systems-using-webmin/2008/12/18)

Looks like doxfer is down at the moment.

Webmin should be working after you install it. Just go to port 10000 on your server box like this:

[https://IP_address_of_your_server:10000](https://IP_address_of_your_server:10000)

Don't forget the 's' in https.

You might want to consider learning the command line (I know, I know, you don't want to ) for administration and then use PuTTY from Windows or a terminal from some other 'nix box. You will not regret learning it, and you may find it faster and easier than using a GUI tool. Also, if your GUI tool fails you will be lost and may end up losing your work or paying someone to fix it. In the long run, it's better to admin servers the way they were intended, through the CLI.

-Tim

---

### Post by spynappels on 2008-12-21
Thanks for that, I'll get a chance to read through those links today.

I have a server up and running and I've been administering it from the CLI through SSH, but I want to be aware of the other options out there and how easy they are to use in practise. I'm by no means a CLI advanced user, and I am still learning, but it is nice to have  a few different ways of doing things.

Regards,  Stefan.

---

### Post by Iowan on 2008-12-21
> **spynappels said:**
>  Can anyone tell me where to look for documentation or a tutorial on how to use Webmin?  Is [this]("https://help.ubuntu.com/community/WebMin") what didn't work, or is it another source?
Here's [another]("http://ubuntuforums.org/showthread.php?t=7507") - although somewhat dated.

---

