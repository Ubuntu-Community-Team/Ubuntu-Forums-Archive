---
title: "Script waiting for serial inputs (RS232)"
date: 2009-08-04
forum: Server Platforms
---

### Post by weryl on 2009-08-04
Hello

I have an old computer that's used to play mp3 with MPD (music player daemon). I've already added a basic script in /etc/init.d to play music on startup but I'd like it to constantly wait for serial inputs and then launch other scripts/actions. Do I need to program a daemon for that? If so how?

For example if "shutdown" is received on the serial port I'd like the computer to do something like "shutdown -h now" (the scripts will need root privileges).

I'll probably use a bit of bash and python for my scripts so either is fine. I've already found several serial port loggers but I'm not sure it'd be good for what I'm trying to do. Could someone give me some help?

Thank you!

---

### Post by weryl on 2009-08-05
bump

---

### Post by weryl on 2009-08-05
Oh well I found some info elsewhere. I think these examples/explanations will be enough to figure out how to do it:

[http://www.linuxquestions.org/questions/programming-9/daemon-to-read-from-com-ports-617482/]("http://www.linuxquestions.org/questions/programming-9/daemon-to-read-from-com-ports-617482/")
[http://www.linuxboxadmin.com/articles/tools-and-utilities/a-bourne-again-daemon.html]("http://www.linuxboxadmin.com/articles/tools-and-utilities/a-bourne-again-daemon.html")
[http://www.linuxjournal.com/article/2335]("http://www.linuxjournal.com/article/2335")

---

