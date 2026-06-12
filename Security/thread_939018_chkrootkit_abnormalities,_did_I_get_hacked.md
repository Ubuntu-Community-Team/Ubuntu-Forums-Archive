---
title: "chkrootkit abnormalities, did I get hacked?"
date: 2008-10-05
forum: Security
---

### Post by Kinetic Being on 2008-10-05
```
Searching for anomalies in shell history files... /usr/bin/find: //home/matt/.gvfs: Permission denied
Warning: `//home/matt/.local/share/Trash/files/sysbackup092808/home/matt/.civserver_history
//home/matt/.local/share/Trash/files/sysbackup092808/home/matt/Desktop/sysbackup092808/home/matt/.civserver_history
//home/matt/.civserver_history' file size is zero
/usr/bin/find: //home/matt/.gvfs: Permission denied
Checking `asp'... not infected
Checking `bindshell'... not infected
Checking `lkm'... chkproc: nothing detected
Checking `rexedcs'... not found
Checking `sniffer'... lo: not promisc and no packet sniffer sockets
eth0: PACKET SNIFFER(/sbin/dhclient3[5761])
Checking `w55808'... not infected
Checking `wted'... chkwtmp: nothing deleted
Checking `scalper'... not infected
Checking `slapper'... not infected
Checking `z2'... user matt deleted or never logged from lastlog!

```

The first part, where the file name is 4 lines long (at least that's what I think it is) is because I started a backup, stopped it, then started another, and ended that, so that's why it's got the really long file name. At least, I think that's why, it looks like that's the reason.

But, I don't know why its empty, is the freeciv server file supposed to be empty? I've gone onto servers and observed before, but never actually played online.

Also, I don't know what the z2 thing is. From what I could find out, it says that the user "matt" was created since the last time I ran chkrootkit, which it wasn't, that was the one I started Ubuntu with, and I never created any other users.

And the thing that worries me most is the **eth0: PACKET SNIFFER(/sbin/dhclient3[5761])** line.

Everything else before this section came up nothing found.


I am worried about a rootkit because last night I was trying to set up tor to use some proxies from a howto on this forum, and I was trying to see if the ip's on the list worked. I "ping"'ed them, which in foresight might not have been the best idea, but I thought it would tell me if they were up and fast or not. I think someone mistook that for a malicious attempt (BTW, none of them came back to me within a minute and I ctrl-c'd) and tried to exact revenge on me. My computer started acting up a bit, so I shut off the internet and ran chkrootkit. I didn't know what to do from there, so here I am. My computer so far has not been acting weird, and I ran chkrootkit again a few times and got the same results.

All help is appreciated, thanks,

Kinetic Being

---

### Post by cariboo on 2008-10-05
Dhclient3 is running in the background just in case your network connection gets dropped it can find you a new ip address. I would say there is nothing to worry about. Reagrding you name being deleted from lastlog, what are the results if you type:

```
last
```

in a terminal. If there are any names in the output that you don't recognize, report back here.

Jim

---

### Post by Kinetic Being on 2008-10-05
> **cariboo907 said:**
> Dhclient3 is running in the background just in case your network connection gets dropped it can find you a new ip address. I would say there is nothing to worry about. Reagrding you name being deleted from lastlog, what are the results if you type:

```
last
```

in a terminal. If there are any names in the output that you don't recognize, report back here.

Jim

nope, nothing but my user and reboot is in that list.
but there seems to be two instances of my user "matt" logged in at the same time.

```
matt@computer:~$ last
[B]matt     pts/0        :0.0             Sun Oct  5 10:39   still logged in   
matt     tty7         :0               Sun Oct  5 09:13   still logged in[/B]   
reboot   system boot  2.6.24-19-generi Sun Oct  5 09:12 - 15:08  (05:55)    
matt     pts/0        :0.0             Sun Oct  5 01:46 - 02:02  (00:15)    
matt     pts/1        :0.0             Sun Oct  5 01:03 - 01:03  (00:00)    
matt     pts/0        :0.0             Sun Oct  5 01:02 - 01:43  (00:41)    
matt     pts/0        :0.0             Sat Oct  4 22:09 - 22:16  (00:06)    
matt     pts/0        :0.0             Sat Oct  4 17:36 - 17:58  (00:22)    
matt     tty7         :0               Sat Oct  4 14:34 - 09:12  (18:37)    
matt     tty7         :0               Sat Oct  4 14:33 - 14:34  (00:00)    
reboot   system boot  2.6.24-19-generi Sat Oct  4 14:31 - 09:12  (18:40)    
matt     pts/0        :0.0             Sat Oct  4 11:45 - 11:45  (00:00)    
matt     tty7         :0               Fri Oct  3 21:18 - 12:14  (14:55)    
reboot   system boot  2.6.24-19-generi Fri Oct  3 21:18 - 12:14  (14:56)    
matt     tty7         :0               Thu Oct  2 18:42 - 16:43  (22:01)    
reboot   system boot  2.6.24-19-generi Thu Oct  2 18:13 - 16:43  (22:30)    
matt     tty7         :0               Thu Oct  2 14:46 - crash  (03:26)    
reboot   system boot  2.6.24-19-generi Thu Oct  2 14:46 - 16:43 (1+01:57)   
matt     tty7         :0               Wed Oct  1 19:47 - 22:37  (02:49)    
reboot   system boot  2.6.24-19-generi Wed Oct  1 19:46 - 22:37  (02:51)
```

---

### Post by snl2587 on 2008-10-05
Somebody please correct me if I'm wrong, but I think that the two entries marked "still logged in" correspond to the current terminal and the current terminal emulation (triggered when the GNOME Terminal or xterm or whatever is used).

For the record, my "last" output is identical to yours (except for the times, "crash", and my name isn't Matt).

---

### Post by Dave_Connor on 2008-10-06
Try "who" and see who is logged into the computer.

---

