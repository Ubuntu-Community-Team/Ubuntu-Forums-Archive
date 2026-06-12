---
title: "filter apache2 logging into access.log?"
date: 2008-12-14
forum: Server Platforms
---

### Post by Phases on 2008-12-14
I would like to filter what is wrote to access.log

Like template entries for my website (every little image for my template) or, more importantly, a certain page within my website. It uses ajax to ping the log every second to tail the log, for real time monitoring while I test stuff but, obviously it's filling up with those pings.

Is this a difficult thing to accomplish? I'm hitting up google but thought I'd see if someone here could beat me to the solution.


Thanks in advance.

---

### Post by Phases on 2008-12-15
I've found documentation on apache's site about making custom logs but everything I try.. when I try to restart apache it fails till I remove what I've added.

Any advice appreciated. 
Thanks!

---

### Post by Phases on 2008-12-15
Please?

---

### Post by MJN on 2008-12-15
Does [this thread](http://ubuntuforums.org/showthread.php?t=678374) help?

Mathew

---

### Post by Phases on 2008-12-15
Thanks so much for the reply.. whether it helps or not I'm just happy to have someone offer help. Heading out of office now but will look at it in a bit. 

Thanks again!

---

### Post by MJN on 2008-12-15
No problem. Let me know if you struggle getting what you want out of it.

Mathew

---

### Post by Phases on 2008-12-15
Yay, you rock! 

I had to do a little debugging but what I ended up with was editing /sites-available/default and putting my entries above the CustomLog entry for access.log and then adding env=!dontlog at the end of the CustomLog /var/log/apache2/access.log line. 

SetEnvIf Request_URI "^robots\.txt$" dontlog
SetEnvIf Request_URI \.gif dontlog
SetEnvIf Request_URI /manage/ dontlog

CustomLog /var/log/apache2/access.log combined env=!dontlog

...basically I didn't want template gifs to be shown, or any url from my site that has /manage/ in it. Because that's just me doing work on the site - and I have two ajax pages that ping every second when I'm looking at them and it was filling that log fast!

I did robots for the hell of it, I saw that other guy did it and I have been noticing the log entry and figured why not.

If you see an issue with my syntax feel free to say but, it's working great. 

Thanks so much! 

(My problem before was I was putting them in httpd like I apparently thought I gathered from their website as what to do - but it seems directly in s-a/default is the way to go.)

Thanks again, I do appreciate it.

---

