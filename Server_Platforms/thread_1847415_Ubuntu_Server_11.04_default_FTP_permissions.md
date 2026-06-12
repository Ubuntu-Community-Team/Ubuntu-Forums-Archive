---
title: "Ubuntu Server 11.04 default FTP permissions"
date: 2011-09-20
forum: Server Platforms
---

### Post by tangerine0469 on 2011-09-20
Hi everyone,
Once again i find myself stuck trying to make my server run correctly. Any and all help is greatly appreciated!

I am trying to run an email/web Hosting server. I have the email part up and running and all is fine on that end,  [http://workaround.org]("http://workaround.org") was a wonderful place to help me with that. The problem I am running into is that when my users(clients) ftp files into the server the permissions are defaulted so that others cannot access them. I can go in and chmod them my self but as I have a full time and very time consuming job its a bit unrealistic for me to be there every 2 seconds to do so.

I have searched around and maybe I am missing something but is there a way to have it set so that on ftp all files transferred in will be set to chmod 755?

P.S. Again thanks for any and all help you will/have given me! I am trying to watch new posts and pass on what I have learned so that I am not just a leach on the community, I just need to learn a bit more to be a decent help.

---

### Post by Dangertux on 2011-09-20
What FTP server are you using? 

In any case, dependant on your FTP server, you need to change the setting related to umask to 022. This should give all new files created permissions of 755 or alternatively (recommended) 027 which would yield permissions of 750.

---

### Post by tangerine0469 on 2011-09-24
vsftpd as per the setup guide on ubuntu.com, i just found the umask setting in the config file. thanks! i knew it was something small i was missing.

---

