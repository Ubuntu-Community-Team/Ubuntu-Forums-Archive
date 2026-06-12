---
title: "New admin account with no commands."
date: 2009-08-20
forum: Server Platforms
---

### Post by Johndo1 on 2009-08-20
I could of sworn I already posted this but I cannot find the thread... Maby I only clicked preview... Anyhow if any1 finds the previous thread sorry about reposting :confused: . Anyways on to the problem.

I created an account useing the following commands:

adduser blah

adduser blah admin

reboot

Once that was complete I logged on and had root access but it seems I could not execute many commands. I couldn't even logout. So i restarted it and logged into my usual account. 

I have webmin and created a user with root access but it seems the same thing happened. Any help would be helpfull :)
Thanks.

---

### Post by cariboo on 2009-08-21
Bascally if you added a user called root, it is not the same as the disabled root user that is setup by default. Unfortunately it is against forum policy to tell you how to do enable the root account, and it against forum policy to tell you to check google without giving you specific instructions. 

You really don't need a root account. have a look at this [wiki]("https://help.ubuntu.com/community/RootSudo") page that explains the rational behind Ubuntu's security model.

---

### Post by Iowan on 2009-08-21
See if anything [here]("http://www.psychocats.net/ubuntu/fixsudo") helps.

---

