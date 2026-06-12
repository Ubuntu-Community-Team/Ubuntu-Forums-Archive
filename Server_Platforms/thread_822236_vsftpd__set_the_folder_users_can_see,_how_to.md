---
title: "vsftpd : set the folder users can see, how to?"
date: 2008-06-08
forum: Server Platforms
---

### Post by MarioFromBelgium on 2008-06-08
Hi,

I have succesfullu installed vsftpd on my Ubuntu Hardy server. I can from another workstation from within firefox go to : [ftp://serveripadress](ftp://serveripadress)

I have two questions :
1° which folder do I get to see from default
2° how can i change this so I see another specific folder

Thx

---

### Post by RealPSL on 2008-06-08
1. It depends on your configuration. If you are signing in with a userid and password you will most likely see the home diectory of the user you signed in as. If you are signing in with anonymous you would be logged into the home directory of the ftp user.

2. You would need to edit the configuration file but without seeing it or understanding clearly what you are trying to accomplish.

---

### Post by P1N3R on 2008-06-09
I am looking to do something similar. I want to setup an FTP account for a user to upload websites to the /var/www directory where the websites are currently hosted from. Can you offer any indication on how I might do this?

Thanks,

Chris

---

### Post by RealPSL on 2008-06-09
This is a good place to get started: [https://help.ubuntu.com/8.04/serverguide/C/ftp-server.html]("https://help.ubuntu.com/8.04/serverguide/C/ftp-server.html")

I would recommend changing local_enable=yes. Create a user with the home directory of /var/www. Make sure the user has write permission to /var/www (the web server will need read).The user should be able to upload files to the location if you follow the remaining instructions in the link above. If you have more trouble just post the vsftpd.conf file and we will help you work it out.

---

