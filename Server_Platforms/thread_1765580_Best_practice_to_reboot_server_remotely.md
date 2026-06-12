---
title: "Best practice to reboot server remotely?"
date: 2011-05-23
forum: Server Platforms
---

### Post by lucacerone on 2011-05-23
Dear all,
I'm writing you to ask some help with administrating a  server remotely.
I have a machine I use remotely when I have to travel, some time for quite long periods like from one to three months.
Last time it happened to me that after upgrading I send the reboot command
and the machine didn't turn down, so I couldn't be able to access it.
My question is: how can I avoid such situations?
Is there any best practice to follow???
Thanks in advance, Cheers -Luca

---

### Post by HermanAB on 2011-05-23
Howdy,

Before you do maintenance on a remote server, first talk to the server farm help desk and ensure that they are able to get it going for you again, that they have your password and whatever else they need to know.  Then when the inevitable happens, you can call them and be up again in no time.

If there is nobody there - don't do it.  Leave it till you are back home.

---

### Post by arrrghhh on 2011-05-23
Yea, physical access (or some sort of a remote access controller...) is tantamount when doing upgrades/reboots.

However, if you're just looking for a command...```
sudo shutdown -r now
```Will reboot just fine.  However, I don't think that's your issue...

---

### Post by rubylaser on 2011-05-23
If you have a server with IPMI, you can access the machine even if there are problems with the OS loading.  Other than that, all of the previous suggestions are spot on.

---

### Post by lucacerone on 2011-05-23
Hi guys thanks for the advices.
Arghh I knew the command, but I wasn't aware of the -r option.
What is the main difference between reboot and "shutdown -r"???

Herman, your is a good advice, but the computer is in my office, is not
part of a corporation or industry, so unfortunately I have no persons
to reboot the machine for me.
Rubylaser, I guess I don't have IPMI... since mine it's a normal desktop machine I use as a server :)
Thanks a lot for your help guys!

For any other good practice advice, please just let me know :)
Cheers, -luca

---

### Post by arrrghhh on 2011-05-23
Honestly shutdown -r and reboot should do the same thing ;).  I'm just used to using the shutdown command for anything, there's many switches.

---

