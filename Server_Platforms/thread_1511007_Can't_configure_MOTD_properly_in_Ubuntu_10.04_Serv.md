---
title: "Can't configure MOTD properly in Ubuntu 10.04 Server (update-motd command not found)"
date: 2010-06-16
forum: Server Platforms
---

### Post by RugerRedhawk on 2010-06-16
I had a default install recently of 10.04 server, and I modified /usr/share/pyshared/landscape/sysinfo/landscapelink.py

To remove the canonical URL from the MOTD. Not sure what else happened because now all that I see the following when I log in:

> Linux hostname 2.6.32-22-server #36-Ubuntu SMP Thu Jun 3 20:38:33 UTC 2010 x86_64
Last login: Wed Jun 16 09:06:00 2010 from 192.168.2.147


I don't seem get my 'reboot required' or updates needed or any messages like that. I did apt-get install update-motd and it installed, but when I type 'update-motd' it says it can't find the command. 

I also tried this procedure ([https://help.ubuntu.com/10.04/serverguide/C/pam_motd.html](https://help.ubuntu.com/10.04/serverguide/C/pam_motd.html)) exactly and I don't get the weather when I login either... not that I need that, just wanted to see if I could change the MOTD.

Any ideas? Thanks

---

### Post by RugerRedhawk on 2010-06-17
Any ideas? Is there a particular cron job that should be there that I could see?

---

### Post by RugerRedhawk on 2010-06-24
One more bump.... how can I get this to work?

---

### Post by WinstonChurchill on 2010-06-24
update-motd is actually much better in 10.04 with the PAM functionality - used to, there was a cron job that would update the MOTD every so often; now, it just generates the MOTD immediately when you log in, and displays it for you.

The MOTD is generated from the scripts in /etc/update-motd.d/. The numbers in the front of the script (xx-scriptname) tell update-motd in what order to run them.

If you're logging in on the physical TTY (Keyboard and monitor plugged straight into the server), this should just happen automatically. If you're logging in over SSH, you need the following options set in sshd_config for it to work properly:```
UsePAM yes
PrintMotd no
```With UsePAM enabled, PAM will automatically update the MOTD and print it for you when you log in. You have to disable PrintMOTD or SSH will print it as well, so you'll see it twice, which is annoying. Also, if you only use public key authentication (like you should), the UsePAM option won't change that.

Here's the script I use for my MOTD, in case you find it useful:
```

#!/bin/bash
realusernum=`ps -t ? S | grep "priv" -c`
hostn=`hostname`
echo "You have just connected to the one, the only, $hostn"
echo "--------------------------------------------------------------------------------"
date +"%A %B %d %I:%M %p %Z (%:z) %Y [%s]"
uptime
echo "--------------------------------------------------------------------------------"
weather-util -c dallas -s TX -f -n
echo "--------------------------------------------------------------------------------"
echo "Current SSH Sessions: $realusernum"
echo "PID   TTY (?)  STAT   CPU  USERNAME@PROCESS"
ps -t ? S | grep ssh | grep "@"
echo "Login sessions with an active shell:"
echo "USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT"
w -h
echo "--------------------------------------------------------------------------------"
df -t ext4 -T -h 
echo "--------------------------------------------------------------------------------"
free -m -t
echo "--------------------------------------------------------------------------------"
echo "Network Status:"
netstat -s | grep 'connections established'
ifconfig eth1
echo -n "--------------------------------------------------------------------------------"

```

---

### Post by RugerRedhawk on 2010-06-28
Thanks for the tips. Something definitely seems strange with my setup. I modified sshd config so that pam is turned on and motd off.... however the scripts in /etc/update-motd/ don't seem to be displaying. I added a new script in there 05-test changed permissions and added a line to echo "hello", it doesn't show up on login though. Neither does the weather, which I installed following the instructions I linked to above.

---

### Post by Huufarted on 2010-07-21
I see the exact same behavior you are describing.  Since the binary update-motd is no longer part of the update-motd package, I can't get it to update, either.  There's no binary for cron to execute, but the default Ubuntu motd is displayed instead of the new motd that should be generated during each login from update-motd.

---

### Post by dadofaayan on 2010-12-10
I'm having the same issue in 10.10.  There's no /usr/sbin/ executable file, and my update-motd isn't running as scheduled.  I have found that I can go into /var/run and replace motd with motd.new, but that kinda loses the point of the automation.

---

### Post by dadofaayan on 2010-12-10
OK... quick fix, at least on my system... (10.10)

update-motd seemed to be writing a new "motd.new" each time.  So, i ran two commands -

sudo rm /var/run/motd
sudo ln -s /var/run/motd.new motd

Seems to be updating, now.  I hope this helps.

---

### Post by luciform on 2011-08-30
You can use command
```
sudo apt-get source update-motd
```to download source packages with the update-motd binary and startup script.

Works for Ubuntu-server 10.04.

---

### Post by UXICO on 2012-06-20
> **WinstonChurchill said:**
> update-motd is actually much better in 10.04 with the PAM functionality - used to, there was a cron job that would update the MOTD every so often; now, it just generates the MOTD immediately when you log in, and displays it for you.

The MOTD is generated from the scripts in /etc/update-motd.d/. The numbers in the front of the script (xx-scriptname) tell update-motd in what order to run them.

If you're logging in on the physical TTY (Keyboard and monitor plugged straight into the server), this should just happen automatically. If you're logging in over SSH, you need the following options set in sshd_config for it to work properly:```
UsePAM yes
PrintMotd no
```With UsePAM enabled, PAM will automatically update the MOTD and print it for you when you log in. You have to disable PrintMOTD or SSH will print it as well, so you'll see it twice, which is annoying. Also, if you only use public key authentication (like you should), the UsePAM option won't change that.

Here's the script I use for my MOTD, in case you find it useful:
```

#!/bin/bash
realusernum=`ps -t ? S | grep "priv" -c`
hostn=`hostname`
echo "You have just connected to the one, the only, $hostn"
echo "--------------------------------------------------------------------------------"
date +"%A %B %d %I:%M %p %Z (%:z) %Y [%s]"
uptime
echo "--------------------------------------------------------------------------------"
weather-util -c dallas -s TX -f -n
echo "--------------------------------------------------------------------------------"
echo "Current SSH Sessions: $realusernum"
echo "PID   TTY (?)  STAT   CPU  USERNAME@PROCESS"
ps -t ? S | grep ssh | grep "@"
echo "Login sessions with an active shell:"
echo "USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT"
w -h
echo "--------------------------------------------------------------------------------"
df -t ext4 -T -h 
echo "--------------------------------------------------------------------------------"
free -m -t
echo "--------------------------------------------------------------------------------"
echo "Network Status:"
netstat -s | grep 'connections established'
ifconfig eth1
echo -n "--------------------------------------------------------------------------------"

```

     Hi there.

     Sorry to "bump" this old thread, but it helped me and since my solution to this problem was a bit different I decided to post.

     To me what seems to have fixed this problem was actually modify the *sshd_config* file, but instead of *PrintfMotd no* use *yes*. I don't know if the *motd *will be updated as expected nor if not using *ssh* wil cause the *motd* to be outdated.

     I am using Ubuntu Server 12.04 LTS. This could explain the difference too. :/

     Hope this gives a light on the subject.

---

### Post by lisati on 2012-06-20
Back to sleep, old thread.

---

