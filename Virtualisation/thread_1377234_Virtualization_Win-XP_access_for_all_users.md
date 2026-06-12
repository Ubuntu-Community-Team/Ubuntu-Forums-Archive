---
title: "Virtualization Win-XP access for all users"
date: 2010-01-10
forum: Virtualisation
---

### Post by kannanjagadeesan on 2010-01-10
Hi Experts,

I have installed Win-XP in Virtual Box under Ubuntu Jaunty Jackalope for User SMART. The Virtual Box Files, folders & sub folders are hidden and not visible. Now, I want other users also to use Win-XP. 

How can I provide access to other users and make them use Win-XP?

Kindly provide me the required steps to do it.

Thanks in advance,
With kind regards,
Kannan

---

### Post by LinuxRules1 on 2010-01-10
you could create a folder in the /media folder so all users can access the files.

Step 1: Go to terminal

Step 2: type sudo mkdir /media/winxp

Step 3: type sudo chmod 777 /media/winxp

Step 4: copy the virtual hard drive to /media/winxp

Step 5: tell all the users on the system to setup a winxp VM and use the virtual hard drive located in /media/winxp

hope this helps:)

---

