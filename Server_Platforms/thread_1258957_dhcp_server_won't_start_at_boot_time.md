---
title: "dhcp server won't start at boot time"
date: 2009-09-05
forum: Server Platforms
---

### Post by irvken on 2009-09-05
I'm having trouble getting the dhcp-server to start on my ubuntu ltsp server on boot, I have to start it manually every time.

It appears there is a start up script in the right place for booting

/etc/rc5.d/S40dhcp3-server

?

---

### Post by cariboo on 2009-09-05
I have dhcp3-server in rc2.d, rc3.d, rc4.d and rc5.d.

Try removing dhcp3-server using:

```
sudo update-rc.d -f dhcp3-server remove
```

then adding it again:

```
sudo update-rc.d dhcp3-server defaults
```

---

### Post by philv123 on 2009-10-03
I have the same problem as the OP. I tried the above suggestion, but no dice. dhcp3-server still won't start on boot.

Here's what I did, and my current rc.d links:
```
$ sudo update-rc.d -f dhcp3-server remove
$ sudo update-rc.d dhcp3-server defaults
$ ls -l /etc/rc*.d/*dhcp*
lrwxrwxrwx 1 root root 22 2009-10-03 16:48 /etc/rc0.d/K20dhcp3-server -> ../init.d/dhcp3-server
lrwxrwxrwx 1 root root 22 2009-10-03 16:48 /etc/rc1.d/K20dhcp3-server -> ../init.d/dhcp3-server
lrwxrwxrwx 1 root root 22 2009-10-03 16:48 /etc/rc2.d/S20dhcp3-server -> ../init.d/dhcp3-server
lrwxrwxrwx 1 root root 22 2009-10-03 16:48 /etc/rc3.d/S20dhcp3-server -> ../init.d/dhcp3-server
lrwxrwxrwx 1 root root 22 2009-10-03 16:48 /etc/rc4.d/S20dhcp3-server -> ../init.d/dhcp3-server
lrwxrwxrwx 1 root root 22 2009-10-03 16:48 /etc/rc5.d/S20dhcp3-server -> ../init.d/dhcp3-server
lrwxrwxrwx 1 root root 22 2009-10-03 16:48 /etc/rc6.d/K20dhcp3-server -> ../init.d/dhcp3-server

```Any suggestsions? I'm going to try the following as a workaround. Add these lines to /etc/rc.local
```
/etc/init.d/dhcp3-server status
if [ "$?" -ne 0 ]; then
  echo "Starting dhcp3-server from rc.local"
  /etc/init.d/dhcp3-server start
fi
```Phil

---

### Post by philv123 on 2009-10-25
I figured out my problem. Posting the fix here in case this helps anyone else.
1) Change /etc/default/dhcp3-server. Got the hint to do this from [this post]("http://ubuntuforums.org/showthread.php?t=74925&highlight=dhcp3-server")
Find the line that says INTERFACES="" and change to INTERFACES="eth0" (or whatever is correct for you).

2) Change permissions of /etc/dhcp3/dhcpd.conf. I had it set to 
$ ls -l /etc/dhcp3/dhcpd.conf 
-rw-r----- 1 root root 5609 2009-09-14 21:08 /etc/dhcp3/dhcpd.conf

But dhcp3 runs as user/group dhcpd so 'sudo chgrp dhcpd /etc/dhcp3/dhcpd.conf' fixed it.

$ ls -l /etc/dhcp3/dhcpd.conf
-rw-r----- 1 root dhcpd 5609 2009-09-14 21:08 /etc/dhcp3/dhcpd.conf

After making the above 2 changes, dhcp3-server starts at boot for me. Hope this helps someone else.

Phil

---

### Post by milkfilk on 2010-02-12
> **philv123 said:**
> Hope this helps someone else.

This helped me a ton.  I work on so many distros and they all have their own place to put things.  I just wanted to get this service working again and your tip fixed it first time.  Same issue, same fix.  I don't know what the crap happened.

For a while, I had the rc.local hack in.  But now I can take that out.  Thanks!!

---

### Post by shaferwr on 2010-04-19
I had the same exact problem as you and I used your (philv123) fix and it worked perfectly for me.  Thanks a ton!
 
-Will

---

### Post by mfecteau on 2011-03-29
This fix didn't work for me.  The only thing that worked was to create a startup script that would sleep for 20 to 40 secondes before restarting the dhcp-server service.  So it would restart it at about the same time that I would start it manually.

---

### Post by ITJeff on 2011-12-31
Hi
 
I am VERY new to this, thought I needed a quick DHCP server and it is not working.
 
Works fine starting manually, but is not starting automatically, same as everybody else. Have been through philv123 notes and still telling me status - Not Running!
 
I am using Ubuntu 10.4, not sure what else will help to track the issue.
 
Thanks
 
Cracked It
 
My fault, using the workstation version (said I was new) and had not set the IP details in /etc/network/interfaces, had set in the GUID so was not configured until you log in !!!

---

