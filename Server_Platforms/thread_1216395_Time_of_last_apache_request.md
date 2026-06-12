---
title: "Time of last apache request"
date: 2009-07-18
forum: Server Platforms
---

### Post by Andcor on 2009-07-18
Hi
I'm trying to make my mythtv-server shutdown automatically, but in order to make a good script that checks if anybody is connected to the server in any way, I need to find a way to find the time of the last apache request, so that I don't shut down the server while someone is using my homepage.

By the way, i am also making a cgi-script for my dd-wrt router which can power on the server if needed.

Do anybody know how to find the time of the last http request without passing all the apache logs (I have several logs since i have several pages).

Any help appreciated

---

### Post by wojox on 2009-07-18
You could just tail the access log.
Why do you have a log file for each page?

---

### Post by Andcor on 2009-07-18
Well, I actually don't have a log file for each page, but one for each site. I like it that way, because it is easier to find the relevant information when you are troubleshooting one of the sites.

---

