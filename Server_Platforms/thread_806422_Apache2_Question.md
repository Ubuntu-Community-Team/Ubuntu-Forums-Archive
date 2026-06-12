---
title: "Apache2 Question"
date: 2008-05-24
forum: Server Platforms
---

### Post by dvsjr on 2008-05-24
Long time listener first time caller.

Last night I installed ubuntu desktop edition 8.04 for learning/home use. After the install, I used Synaptic Package manager (which I really like) to install Apache2. I added a software repository for webmin, and then used Synaptic to install webmin 1.410.

Webmin is working great (I'm using it to help me get things done, as I'm learning) but I have a strange question I hope someone can explain. When I try to "start apache" in Webmin using the apache2 Module, it gives an error apache error:

Failed to start apache :

 * Starting web server apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:88
no listening sockets available, shutting down
Unable to open logs
   ...fail!

However, if I look at System/Administration/Services it shows Apache2 is started and a web browser pointed to [http://localhost](http://localhost) shows the "It Works!" page.

I assume this must have something to do with a non-standard installation but I'm not having any luck finding info on how to correct this. 

thanks

---

### Post by dvsjr on 2008-05-24
Hi again

First, yes I know that I just posted this question and here I am posting the fix, but its been bugging me for two days. (mostly because I'm working on this at night) I changed my search to focus on webmin users with this error, and found the answer.

To help others, I wanted to post the answer with relevant links to give others the reading material as well.

Links: [http://tinyurl.com/5653mf](http://tinyurl.com/5653mf) and [http://tinyurl.com/5praot](http://tinyurl.com/5praot)

from the second link: "It's gotta be the pid file. That's how Webmin knows whether Apache is running or not. Make sure it points to the right place" clicking module config, and adding the path to the PID fixed the issue.

hope this helps.

dvsjr

---

