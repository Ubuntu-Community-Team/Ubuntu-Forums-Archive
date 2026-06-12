---
title: "GD Graphics Library in Ubuntu Server"
date: 2007-03-07
forum: Server Platforms
---

### Post by arst06d on 2007-03-07
Hi

I have installed the LAMP server edition of Ubuntu as a home web server, on which I am running Joomla the content management system.  One of the components I want to install in Joomla is a sucurity addon which generates CAPTCHA images on forms, and it needs the GD graphics library on the server.

I've run phpInfo() and have no sign of anything to do with GD.

I downloaded the GD tar and uploaded to the server using WebMin, so I now have an unpacked directory in /var/tmp.  Obviously it shouldn't stay there, but where do I have to move it to, and is there any other config required to get php to recognise it?

Many thanks

---

### Post by arst06d on 2007-03-11
Hi again
Can anyone advise on this?
I've read that there should be GD support bundled in PHP 4.3 and above.  The Ubuntu LAMP server install included PHP 5.1.6 but I have no GD.
Some help forums say I need to compile PHp with GD support, but I have no idea (or wish) to get this involved in the php core.

So, does the LAMP server install include GD support?  If not, why not?
Can I upgrade my php installation to a compiled version that contains GD support?  Can you tell me how?

Thanks

---

### Post by DraZtiK on 2007-03-11
Check [Here]("http://www.ubuntuforums.org/showthread.php?t=324685").

---

### Post by arst06d on 2007-03-11
.... and it's as simple as that!

You are a star - I am very grateful for your time.  I do find it odd that the LAMP install does not include this as it supposed to be bundled with php.

Thanks again.

---

