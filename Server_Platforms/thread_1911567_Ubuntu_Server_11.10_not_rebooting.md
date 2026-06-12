---
title: "Ubuntu Server 11.10 not rebooting"
date: 2012-01-19
forum: Server Platforms
---

### Post by blues_1pt on 2012-01-19
Dears,
 
I am new at Ubuntu. Since some days ago, I tried to install Ubuntu Server 11.10 and all instalation worked ok.
However, When I tried the command reboot as root, the server start the shutdown and then it iced.
The server says that he is rebooting, but at the end he never lefts this state.
can you please tell me how can I fix this reboot issue?
 
Thanks a lot.

---

### Post by jerrrys on 2012-01-20
Assumingthat you can still cold boot.
[B]
sudo [/B]**dpkg --configure --pending**  If dpkg quits with an error while [FONT=FIXED]apt-get install, upgrade, or dist-upgrade[/FONT]ing try running this to configure the packages that were already unpacked. Then try [FONT=FIXED]apt-get install, upgrade, or dist-upgrade -f[/FONT], and then try [FONT=FIXED]apt-get install, upgrade, or dist-upgrade[/FONT]  again. Repeat as needed. This usually resolves most dependency problems  (also, if it mentions a specific package for some reason, you might  want to try installing or removing that package)

also can try:  sudo dpkg --configure -a

I really don't expect this to fix the problem, but it may spit out errors and give you a clue as to what is going on.

---

### Post by CharlesA on 2012-01-20
Check the logs to see if it's hanging on a process.

Do you have console access or just ssh access?

---

### Post by blues_1pt on 2012-01-23
Indeed, I am connected via SSH:
 
After asking the server to reboot:

[EMAIL="root@blues1pt"]root@blues1pt[/EMAIL]:~# reboot
Broadcast message from [EMAIL="root@blues1pt"]root@blues1pt[/EMAIL]
        (/dev/pts/0) at 11:13 ...
The system is going down for reboot NOW!

It stays here eternally.
I tried the dpkg --configure -a, but no result and no outpu was given.
 
Am I the only one that has a reboot issue on server? Since this is a new version.
 
Thanks a lot guys.

---

### Post by CharlesA on 2012-01-23
Does the connection time out after that?

Is this a physical server or one hosted somewhere? Does the system log have any errors in it?

---

### Post by blues_1pt on 2012-01-23
Yes, indeed the SSH gives me a time out.
The server is installed in a desktop.
 
The server itself, when I do a reboot, he seems to be shutdown, but the processor is working, no display is shown.
 
It's weird.
Thanks.

---

### Post by CharlesA on 2012-01-23
Can you do the reboot from the console and see if it throws any error messages?

Try these as well:

```
sudo halt
```
```
sudo shutdown -r
```

---

### Post by blues_1pt on 2012-01-24
Dear,
 
indeed what is happening is that even the shutdown is not recognizable:
 
shutdown: time expected
Try `shutdown --help' for more information.
 
I wonder if this happens with other Ubuntu server versions.
Thanks a lot.

---

### Post by plasmafusion on 2012-01-24
sudo shutdown -r now (to reboot right away)
sudo shutdown -h now (to shutdown right away)
sudo shutdown -r 60 (to reboot in 60 minutes)
sudo shutdown -h 60 (to shutdown in 60 minutes)
and so on...

---

### Post by blues_1pt on 2012-01-24
Dear,
 
I tried the commands shutdown now and the result is the same.
I'll try to catch what is printed on the screen and put here.
Thanks.

---

### Post by blues_1pt on 2012-01-25
Dears,
 
when I ask for a reboot, this is the printed screen:
 
Stopping Web server apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for Servername
      Waiting...                                   [OK]
*Stopping Virtualbox kernel modules  [OK]
*VirtualBox additions disabled, not in a Virtual Machine...
*Asking all remaining process to terminate [OK]
*All processes ended within 2 seconds  [OK]
*Deconfiguring network interfaces... [OK]
*Deactivating swap... [OK]
*Unmounting local filesystems   [OK]
*Will now restart  [OK]
[57930.088761] Restarting system..
 
 
Then it stays blocked here forever.
Thanks.

---

### Post by CharlesA on 2012-01-25
Try booting off a livecd and seeing if it will reboot from that.

---

### Post by blues_1pt on 2012-01-26
Dears,

I am going to change of machine.
After installation I'll let you know.
Thanks a lot for your help.

---

### Post by kevdog on 2012-01-26
What happens when you type:
sudo init 6

Just curious if this produces any different behaivor -- (this commands shutsdown the computer as well).

---

### Post by blues_1pt on 2012-01-26
Unfortunatly the result was the same when it start shutding down it crash...

---

### Post by blues_1pt on 2012-01-29
Dears,

I have changed computer. In a real server it works. Maybe this is a computer issue.
Thanks a lot to everyone.

---

