---
title: "Ubuntu newbie setting up web server"
date: 2008-12-03
forum: Server Platforms
---

### Post by rob4001 on 2008-12-03
I am thinking of setting up a backup web server at work so we can view uncompressed medical images and point modality's such as ultrasound etc to send images to it and get images from our servers which use redhat and use a DICOM linux viewer. I am not a computer engineer they don't let me in the server room :) this is managed by an off site company. As I said I am a newbie its a little project to get started and learn about networking and setting up a server.

What hardware would I need sufficient for a web server dealing with uncompressed images?

Would a core 2 or amd x2 and 2gb ram do the job.

I take it I need Apache, mysql & php.

OS i was thinking of ubuntu because I've just set it up and messed around with it on my desktop I don't know any command lines in linux so thought a gui interface might be better for me as I used windows all my life (Sorry!) would ubuntu work as a web server? Any Advice would be great.

Thanks

---

### Post by spiderbatdad on 2008-12-03
You don't need apache mysql php, though of course those programs could be made to suit your purpose. Apache is for hosting web pages and or indexes, mysql is a database query tool, and php is a language helpful in making html do cool things.

ssh as a secure means of ftp sounds like what you are looking for. Openssh is available via apt in a Ubuntu installation, and there are graphical tools preinstalled. If you plan on accessing with linux or mac X forwarding is also simple. And windows there is putty. ssh is also used to tunnel connections between various servers and clients. helpful for what you are talking about.

See the community docs on openssh.[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

It looks a little daunting at first, but it really isn't. Strong password access is easiest, but you would want to move into pub.key access eventually. Once you have accessed the server, if you want a graphical environment, just type the name of your file browser...nautilus, for example, in Ubuntu. This assumes you install a desktop configuration, and not the "server" edition. Or connect via sftp ( several gui's for this.) The server edition is strictly command line. Configure ssh to AllowUser AllowGroup, perhaps install fail2ban, and you'll have a pretty secure file server. Of course, doing it yourself puts you at some risk, and you need to constantly monitor logs and keep up with security...**for all I know it may be a violation of your states laws to run a server with private information unless you have qualified personnel monitoring the server.**  [http://www1.umn.edu/oit/security/standards/OIT__12647_REGION1.html](http://www1.umn.edu/oit/security/standards/OIT__12647_REGION1.html) for example.

---

