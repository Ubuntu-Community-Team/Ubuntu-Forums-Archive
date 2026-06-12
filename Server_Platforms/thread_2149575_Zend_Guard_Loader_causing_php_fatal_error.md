---
title: "Zend Guard Loader causing php fatal error"
date: 2013-05-29
forum: Server Platforms
---

### Post by XaaL on 2013-05-29
Hi!
I'm running debian7 with kde, but because it's almost the same with kubuntu, i'd like to try post my issue here- since i have nowhere else to go. I've already tried debian, zend, and apache support- however most of them are playing deaf and blind to my questions.

The problem is: i've transfered data from old, old (8yrs) debian server (due to its hdd problems, like screeching, and general age of machine), installed debian7, php5.4, apache 2.2.22, mysql [COLOR=#393939][FONT=arial]5.5.31 and everything was running pretty smooth, untill i tried to access the main page after transfer. It prompted me with:
[/FONT][/COLOR]> Zend Optimizer not installedThis file was encoded by the Zend Guard. In order to run it, please install the Zend Optimizer (available without charge), version 3.0.0 or later. 


Seeing this message instead of the website you expected?
This means that this webserver is not configured correctly. In order to view this website properly, please contact the website's system administrator/webmaster with the following message:


The component "Zend Optimizer" is not installed on the Web Server and therefore cannot service encoded files. Please download and install the Zend Optimizer (available without charge) on the Web Server.


Note: Zend Technologies cannot resolve issues related to this message appearing on websites not belonging to Zend Technologies. 
What is the Zend Optimizer?
The Zend Optimizer is one of the most popular PHP plugins for performance-improvement, and has been available without charge, since the early days of PHP 4. It improves performance by scanning PHP's intermediate code and passing it through multiple Optimization Passes to replace inefficient code patterns with more efficient code blocks. The replaced code blocks perform exactly the same operations as the original code, only faster. 


In addition to improving performance, the Zend Optimizer also enables PHP to transparently load files encoded by the Zend Guard. 


The Zend Optimizer is a free product available for download from Zend Technologies. Zend Technologies also developed the PHP scripting engine, known as the Zend Engine.


[COLOR=#393939][FONT=arial]

So i installed (after several attempts) Zend Guard Loader - since zend optimizer doesn't exist anymore on its own- i got the same error on the site, but after checking 
# php -v
i get
[/FONT][/COLOR]> PHP Fatal error: [Zend Guard Loader] Extension "Zend Guard Loader" cannot be loaded twice in Unknown on line 0[COLOR=#000000][FONT=Times New Roman]
[/FONT][/COLOR]
there was quite similar thread already in here [http://ubuntuforums.org/showthread.php?t=1740748](http://ubuntuforums.org/showthread.php?t=1740748) , but it's closed, so i have to open a new one, hoping since then someone who knows what is it all about will read this and reply.

I was following this: [http://www.debiantutorials.com/installing-zend-optimizer/](http://www.debiantutorials.com/installing-zend-optimizer/)
then
I've tried this [http://forums.olm.net/showthread.php?t=926](http://forums.olm.net/showthread.php?t=926) but it didn't do the trick in my case (unless i did something wrong)

Cheers!

---

