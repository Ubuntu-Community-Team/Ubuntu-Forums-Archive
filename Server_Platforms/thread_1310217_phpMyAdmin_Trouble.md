---
title: "phpMyAdmin Trouble"
date: 2009-11-01
forum: Server Platforms
---

### Post by Tristan Tonks on 2009-11-01
Hi Guys, I'm having some real trouble setting up phpMyAdmin. Below is a screenshot of my www/ folder to help anyone who knows identify the problem.

[IMG]http://stormie.no-ip.info/images/phpMytrouble.png[/IMG]

Hope you can help me.
cheers guys :)

---

### Post by Thirtysixway on 2009-11-01
Can you describe the problem you're having?  A screenshot of ls isn't going to help unless you can tell us what's going on.  Is phpmyadmin 404'ing? Is it a white blank page?  Is it in the wrong folder?

---

### Post by mrsteveman1 on 2009-11-01
You're going to have to post your apache or other http server configuration, assuming its running. Is it?

---

### Post by Tristan Tonks on 2010-02-03
Hi guys,
Thanks for your posts, I worked our what was wrong. What was happening was I could not get MyAdmin to load in the browser, Sometimes it came up with 404 and sometimes it came up with php errors like "function not found". 
Basically the version I downloaded had be slightly reconfigured by someone to protect the location of the login interface. I found the file view_create.php was the new name of the 'GUI' and that a number of the other files were no longer seeing it thanks to the name change.

I suppose the moral of the story is to double check downloads against other mirrors and check for inconsistencies. This is a good idea for security reasons but also to pick-up on file_name changes too.
Thanks for your time anyway. :)

---

