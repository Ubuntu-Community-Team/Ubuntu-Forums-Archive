---
title: "New User Shell in Ubuntu 10.04"
date: 2010-11-30
forum: Server Platforms
---

### Post by iglablues on 2010-11-30
I'm seeing something curious that I've never seen before and wondering if it's a basic setting that I missed. I checked the Ubuntu Server Guide and saw no mention of this specifically. 

When I add a new user and SSH to my server as that new user, my command prompt is just a '$'. Tab completion doesn't work either. What I notice is that I get this:

Could not chdir to home directory /home/scaldwell: No such file or directory
$

Echo PS1 yields nothing. There is also nothing in /etc/skel. I didn't have to do anything special to get my initial user setup with the right prompt, and the second user has been added to the admin group as well. I have noticed that if I issue the command **sudo chsh -s /bin/bash** the account gets the correct prompt. What am I missing? 

TIA

---

### Post by papibe on 2010-12-07
still around?

How did you create the new user? Did you create it using the command line? The recommended command for that is adduser. There's a confusing command called useradd that do not create the user's home folder (unless explicitly requested).

Regards.

---

