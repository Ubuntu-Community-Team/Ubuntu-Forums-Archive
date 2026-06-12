---
title: "Running Server Programs Using Webpage"
date: 2013-11-25
forum: Server Platforms
---

### Post by Lewis Arthurton on 2013-11-25
Hello 

I  want to host a website from my server where if I click a hyperlink on the webpage, it initiates a program/script on the server; for example:

I login to a webpage hosted on the server and click the hyperlink/button shutdown, the server would then shutdown. etc 

How would I go about creating this? 

Thanks 

Lewis :p

---

### Post by Kirboosy on 2013-11-25
Hi, There is actually a project out there called [webmin]("http://www.webmin.com/") that would do everything you mentioned above and save you the hassel of writing everything from scratch.

They even have a [demo]("http://virtualmin-demo.virtualmin.com/") (username: root, password: demo) of the product so you can play with it before you ever install it on your own box!

Hope that helps!
~Caboose

EDIT: Link to the Shutdown/reboot module on webmin: [BootupandShutdown Webmin]("http://doxfer.webmin.com/Webmin/BootupAndShutdown?sortcol=table;up=#Rebooting_or_shutting_down_your")

---

### Post by Lewis Arthurton on 2013-11-25
> **Caboose885 said:**
> Hi, There is actually a project out there called [webmin]("http://www.webmin.com/") that would do everything you mentioned above and save you the hassel of writing everything from scratch.

They even have a [demo]("http://virtualmin-demo.virtualmin.com/") (username: root, password: demo) of the product so you can play with it before you ever install it on your own box!

Hope that helps!
~Caboose

EDIT: Link to the Shutdown/reboot module on webmin: [BootupandShutdown Webmin]("http://doxfer.webmin.com/Webmin/BootupAndShutdown?sortcol=table;up=#Rebooting_or_shutting_down_your")

Thanks for your reply carboose885, I was aware of webmin but I was hoping of running other scripts/programs other than those affecting server management? I just gave the poweroff as an example :)

Thanks

---

### Post by Kirboosy on 2013-11-25
Would the [Custom Commands]("http://doxfer.webmin.com/Webmin/CustomCommands?sortcol=table;up=#Creating_a_new_command") of Webmin not be enough for you?

~Caboose

---

### Post by ian-weisser on 2013-11-25
One way to do it is using a rather clever webserver.
The server parses the URL request, and different URLs mean different commands.

[http://my.server/foo](http://my.server/foo)   could trigger, for example, a poweroff.
DON'T parse and execute commands embedded in the URL - that would be a big security hole
Indeed, careful security planning is essential. You don't want just anyone randomly powering off your system.

One example, with python code but lacking built-in authentication: [http://www.dreamsyssoft.com/blog/blog.php?/archives/6-Create-a-simple-REST-web-service-with-Python.html](http://www.dreamsyssoft.com/blog/blog.php?/archives/6-Create-a-simple-REST-web-service-with-Python.html)

---

