---
title: "issue with sudo"
date: 2006-08-03
forum: Server Platforms
---

### Post by yohannmartineau on 2006-08-03
Hello I posted a response on the absolute beginner part of the forum about a problem with date modification on a server version 6.06.

Here is my problem :

I made a mistake while installing the ubuntu server : I choosed the wrong time. I let default GMT whereas I wanted to use GMT + 2.

That's why I changed the time to two hours earlier with the following command :
```
sudo date 08030944
```

But now when I try to run a command with sudo, here is the message I get :

sudo: timestamp too far in the future: Aug  3 11:44:14 2006

I followed instructions from the other thread about this issue, but no one worked. I do not have any graphical interface to change the time to later and come back to the real time.

A reboot is not enough because the timestamp is keeped in a file.

The only solution I found was to wait for the timestamp to be next to my real time.

But I don't think this is a reasonable solution.

I will activate the root account as soon as sudo will be available, to avoid such problems.

Thanks

---

### Post by ciscosurfer on 2006-08-03
Try```
sudo -K date *your_**date*
```

---

### Post by moma on 2006-08-03
You can kill sudo's timestamp
$ sudo -k 

or set new timestamp
$ sudo -v command

What about root prompt?
$ sudo -s

---

### Post by yohannmartineau on 2006-08-03
I tried the following commands:

```
martinyo@r-ccett55-520-29:~$ sudo -K
sudo: timestamp too far in the future: Aug  3 11:44:14 2006

martinyo@r-ccett55-520-29:~$ sudo -k
sudo: timestamp too far in the future: Aug  3 11:44:14 2006

martinyo@r-ccett55-520-29:~$ sudo -v date
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }

martinyo@r-ccett55-520-29:~$ sudo -v
sudo: timestamp too far in the future: Aug  3 11:44:14 2006

```

I did not try the sudo -s but I think it would not have worked. But now it's OK the time passed... but if anyone has the same problem and lives in japan... he will have to be quite patient...

---

### Post by ciscosurfer on 2006-08-03
You didn't include the date and the time you wanted to set it to.  Sudo -K *<command> <date_time*>, etc. all work just fine.

---

### Post by kebes on 2006-08-06
I just encountered this frustrating problem. sudo doesn't work, and tricks like "sudo -k" or "sudo -k" don't work. And "su" doesn't work. However I found that the suggested "sudo -s" does indeed let you enter a root console, from where you can change the time or do "sudo -k" as needed to clear the problem. Once the sudo timestamp and the clock match, everything is okay. So the short answer, at least for me, was to run:
```
$ sudo -s
```

---

### Post by lamego on 2006-08-06
You should fix the timezone by changing:
/etc/timezone
Changing the time is not a correct solution.

---

### Post by yohannmartineau on 2006-08-08
this file contains :
Europe/Paris

which corresponds to my timezone but I am not sure this timezone is (always) synchronized with the unix date.

I now have a second problem, after an alimentation interruption, my server came back to the previous time. Should I try a clean reboot to keep the date correctly configured ?

For the problem of date parameter to set the date, the command date passed without any parameter should have displayed the current date, shouldn't it ?

Thank you for your answers.

---

### Post by yohannmartineau on 2006-08-08
after a clean reboot (as real root), the date was correct.

---

### Post by xenon2000 on 2006-08-10
I just got this today. Odd thing is that my date shows the correct time and timezone. But several of my log files have a time several hours and min into the future. So no sudo command is working for me. And I mean no sudo commands.

Of course there is no root account available. Which I am going to activate if I ever get this fixed.

Of course my /etc/timezone file is correct. But even if I wanted to edit it, I can't overwrite it without sudo. I can't touch the log files to make them the right current system time without sudo either.

So what in the world am I suppose to do?

---

### Post by xenon2000 on 2006-08-10
Well, I couldn't use sudo at the cmdline. So I thought I would try a few things in my current X session. Such as look at the time. Time and zone was still correct. Entered network properties and it asked for password, that worked... then opened terminal again and now sudo works. Though I checked my log files again and most of them got corrected, but some are still a few hours into the future.

So I don't know if that is going to cause any other issues. And I know that this information doesn't help those having this issue when they can't start an X session. Anyways, now to activate the root account so I have root access for when I can't sudo. Personally, I don't see the harm of having the root account enabled for local use only. It still would not be available for ssh or other external login access. So I don't see the harm.

---

### Post by xenon2000 on 2006-08-10
final post... after I got partial sudo back, I used sudo to touch all the log files so that ALL the log files had the correct timestamp, rebooted and now sudo fully works again.

Though, again, this msot likely would not have worked if my X session did not have partial access. But if root account was active, I would have just logged in as root and touched the log files from there and rebooted.

---

