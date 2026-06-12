---
title: "LTSP clients"
date: 2009-09-05
forum: Server Platforms
---

### Post by asai on 2009-09-05
Hi,
I have installed a LTSP server in my network. The installation went very well and I started the thin client. I get to the login picture, and type in username and password. I have tested the username and password from a SSH login, and it works fine. However, in the login from the thin client it doesn't work. After the password is typed, the screen goes blank for a few seconds, until the login screen appears again.
I have checked messages and auth.log for errors, but everything looks OK there.
The server is Dapper...

Any suggestions?

PS! I have tested the suggestions from this tread: [http://ubuntuforums.org/showthread.php?t=261441]("http://ubuntuforums.org/showthread.php?t=261441")

---

### Post by asai on 2009-09-06
Found something possible wrong with the installation:
When I try ltsp-update-sshkeys, there is no failure. But when I try to run ltsp-update-image, it says command not found. Why does this happend?

---

### Post by smaclean on 2009-09-08
Try restarting the dhcp3 server, then update sshkeys, then update the image.

1. restart dhcp3
> 
sudo /etc/init.d/dhcp3-server restart
You may see a FAIL for the stopping but as long as you see an OK for the start, you're good.

2. update the ssh keys
> 
sudo ltsp-update-sshkeys
3. now update the image
> 
sudo ltsp-update-image


---

### Post by asai on 2009-09-09
Thanks for your reply, but in my setup I have a dedicated dhcp server. It's not a standalone installation.

---

### Post by smaclean on 2009-09-11
There are several possible reasons that could cause this. The fact that you cannot run the update-image command would seem to indicate a problem maybe with the client image. Have you tried rebuilding the client image?

> 
sudo ltsp-build-client


You can also optionally use the --arch - distro option at the end of the above statement.

---

### Post by asai on 2009-09-13
Did not resolve the issue...
When I look in the auth.log file, it seems to go OK.
It says that the users password is accepted and the session is opened.
Is there another log file that have more information?

---

### Post by smaclean on 2009-09-16
Do you have 2 nic cards installed in your LTSP server?

---

