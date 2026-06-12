---
title: "Samba in 10.04 RC - Start or Restart?"
date: 2010-04-28
forum: Server Platforms
---

### Post by kamlapati on 2010-04-28
I am setting up a simple home server using Ubuntu Server 10.04 RC. When I try to restart Samba after a config change, I get the message:

sudo: /etc/init.d/samba: command not found

Sure enough, if I do a find, it's not there:

home@server:~$ sudo find / -type f -name "samba"
/etc/cron.daily/samba
/etc/default/samba
/etc/ufw/applications.d/samba
/etc/apparmor.d/abstractions/samba
/etc/bash_completion.d/samba
/etc/pam.d/samba
/etc/dhcp3/dhclient-enter-hooks.d/samba
/etc/logrotate.d/samba
/usr/share/lintian/overrides/samba

How else can I restart Samba? Should I try to directly start nmbd and smbd? If so, what's the exact syntax? Is there a better way?

---

### Post by frodemt on 2010-04-29
I got the same problem. It is simply gone in 10.04 LTS....:confused:

---

### Post by radoi on 2010-04-29
try
```
service smbd restart
```

---

### Post by kamlapati on 2010-04-29
Thanks radoi, will do.

Any reason why it has moved from it's previous location?

---

### Post by frodemt on 2010-04-29
I would love to have the choice to use /etc/init.d/samba for service control when all other services are controled from here. Why make mess?

---

### Post by redmk2 on 2010-04-29
> **frodemt said:**
> I would love to have the choice to use /etc/init.d/samba for service control when all other services are controled from here. Why make mess?

This is not something new.  Ubuntu has been moving away from init scripts for some time now. Upstart is replacing them.  See [**_here _**]("http://www.linux.com/archive/feature/125977")and [**_here_**]("http://ubuntuforums.org/showthread.php?t=1439418").

---

### Post by CharlesA on 2010-04-29
Kinda offtopic, but is there a list of everything that has been converted to upstart?

---

### Post by kamlapati on 2010-04-29
Thanks, Red. I'll resarch upstart and get used to it. I had faith that the all wise Ubuntu developers knew something that I didn't.

---

### Post by whyameye on 2010-05-10
$sudo service smbd restart
returns

restart: Unknown instance:

---

### Post by mondo1287 on 2010-05-10
Use just restart, so
> restart smbd

---

### Post by web032009 on 2010-05-10
sudo restart smbd

---

### Post by ojobson on 2010-05-15
Not working for me?!

Just upgraded to 10.04, samba is running, but when trying the following commands I get:

 sudo /etc/init.d/samba restart
     /etc/init.d/samba: command not found
 service smdb restart
     smdb: unrecognized service
 sudo service smdb restart
     smdb: unrecognized service
 restart smdb
    restart: Unknown job: smdb
 sudo restart smdb
    restart: Unknown job: smdb 

I know samba is running as I can access shares from my mac using smb...
Should i reinstall samba?
Confused!!

---

### Post by ojobson on 2010-05-15
Oh my god.

major balls up here. Would really help if I got the letters in the right order. I've been starring at my screen for so long that the letters all look the same.

I would really hate to be dyslexic and trying to do this.

Still can't create new shares using the GUI. For some reason if I create a share via the GUI I get 30MBps read speeds. If I define a share in smb.conf then I only get 7MBps read speeds.

---

### Post by CharlesA on 2010-05-15
Shouldn't matter if you create the shares in a GUI or manually, as long as the parameters are the same.

What are you using the create the shares?

---

### Post by Morbius1 on 2010-05-15
> Still can't create new shares using the GUI. For some reason if I create a share via the GUI I get 30MBps read speeds. I admit I get confused easily but ... what?

Can you or can you not create a share using "the GUI".
> If I define a share in smb.conf then I only get 7MBps read speeds.Here's my guess for what it's worth. By GUI do you by any chance mean Nautilus?

Why not post the output of the following commands. It will tell us what method of samba sharing you are using:

```
net usershare info
sudo net usershare info
testparm -s
```

---

### Post by Nelly1 on 2010-05-18
Hello,

I just found this thread. As far as I see, it is not solved!
I have about the same problem.
using ¨sudo service smbd restart" or ¨sudo restart smbd¨ I get as reaction: ¨restart: Unknown instance:¨

I asked for ¨sudo net usershare info¨. This was empty.

The strange thing is that I have used the command ¨sudo service smbd restart"  several times, and it worked. I made some changes in my smb.conf file, to see if that helped with some other problem, and then, suddenly, the command ¨sudo service smbd restart"  stopped to work. Replacing my smb.conf file with an older version didn´t solved the problem.

Trying to locate smbd in my computer gives no hit.
ps -ef | grep mbd 
only showed the process nmbd. smbd is not running.

When I was trying this, I tried sudo start smbd, and this seemed to work.
This indicates that ¨restart¨ can only be used with a running process (in &.10 it could also be used for dormant processes)

---

### Post by CharlesA on 2010-05-18
You need to use this command to restart smbd:

```
sudo restart smbd
```

---

### Post by lineofaborder on 2010-05-26
My problem is i cannot restart samba due to the following error:

service smbd restart
restart: Rejected send message, 1 matched rules; type="method_call", sender=":1.60" (uid=1000 pid=2344 comm="restart) interface="com.ubuntu.Upstart0_6.Job" member="Restart" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

---

### Post by CharlesA on 2010-05-26
What happens if you run this command:

```
sudo restart smbd
```

---

### Post by Sven6210 on 2010-05-26
When entering:
       sudo restart smbd

I get the result:
    restart: Unknown instance:

---

### Post by Sven6210 on 2010-05-26
sudo smbd restart

is doing the job for me

---

### Post by strangeintp on 2010-06-01
> **lineofaborder said:**
> My problem is i cannot restart samba due to the following error:

service smbd restart
restart: Rejected send message, 1 matched rules; type="method_call", sender=":1.60" (uid=1000 pid=2344 comm="restart) interface="com.ubuntu.Upstart0_6.Job" member="Restart" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

you need to run it as root/admin; i.e. "sudo service smbd restart" or "sudo restart smbd"

---

### Post by strangeintp on 2010-06-01
> **Sven6210 said:**
> When entering:
       sudo restart smbd

I get the result:
    restart: Unknown instance:

The service may be stopped or never started; you can also "sudo start smbd"

---

