---
title: "trouble connecting to server after some time"
date: 2009-07-04
forum: Server Platforms
---

### Post by garsh0p on 2009-07-04
i have a headless machine with ubuntu server 9.04 that i use as a torrent/file server. i log in through ssh and use vncserver to run utorrent.

it works fine for about 3-4 days, and then i suddenly won't be able to log in through ssh or connect using a vncviewer. i have to go restart it and then it'll work fine for another 3-4 days.

so today after it become unresponsive, i decided to go connect a monitor and a keyboard to it and logged into it. after i logged in, i could ssh into it once again.

does anyone have any idea why it stops working? does it have anything to do with the fact that i'm not logged into the actual machine? thanks.

---

### Post by juancarlospaco on 2009-07-04
*Updates ...?  Logs ...?*

---

### Post by windependence on 2009-07-04
I was thinking logs myself. So many people here want to stop rotating logs for some reason, and they don't partition a separate /var either. That's bad news.

-Tim

---

### Post by garsh0p on 2009-07-04
which logs in particular?

---

### Post by windependence on 2009-07-04
Can you post the output of:

```
df -h
```

-Tim

---

### Post by garsh0p on 2009-07-04
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              55G   48G  4.5G  92% /
tmpfs                 565M     0  565M   0% /lib/init/rw
varrun                565M  192K  565M   1% /var/run
varlock               565M     0  565M   0% /var/lock
udev                  565M  128K  565M   1% /dev
tmpfs                 565M     0  565M   0% /dev/shm
lrm                   565M  2.2M  563M   1% /lib/modules/2.6.28-13-server/volatile
/dev/sdb1              74G   50G   21G  72% /media/drive

```

---

### Post by windependence on 2009-07-05
OK, your root filesystem is a bit full, although 4.5GB should be plenty of space to run on unless something is being created in /tmp that is filling the space. Can you try cleaning some stuff off the box to get some significant space (less than 80% full)?

-Tim

---

### Post by garsh0p on 2009-07-05
not quite sure that would be the issue, but i did it anyway

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              55G   40G   13G  77% /
tmpfs                 565M     0  565M   0% /lib/init/rw
varrun                565M  196K  565M   1% /var/run
varlock               565M     0  565M   0% /var/lock
udev                  565M  132K  565M   1% /dev
tmpfs                 565M     0  565M   0% /dev/shm
lrm                   565M  2.2M  563M   1% /lib/modules/2.6.28-13-server/volatile
/dev/sdb1              74G   58G   13G  83% /media/drive
```

i'll let you know if i still have the problem if it happens again.

---

### Post by diss3ntive on 2009-07-06
This potentially could be related to the same issue I am having:

[http://ubuntuforums.org/showthread.php?p=7568741#post7568741](http://ubuntuforums.org/showthread.php?p=7568741#post7568741) 

Let's keep the thread alive, I am still getting these sporadic lockups.

---

### Post by garsh0p on 2009-07-09
the issue has happened once again. any other suggestions? thanks.

---

### Post by windependence on 2009-07-09
So now what does your df -h report? Is the file system full again?

What is in /var/log/messages?

-Tim

---

### Post by garsh0p on 2009-07-10
here is df -h:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              55G   40G   13G  77% /
tmpfs                 565M     0  565M   0% /lib/init/rw
varrun                565M  196K  565M   1% /var/run
varlock               565M     0  565M   0% /var/lock
udev                  565M  132K  565M   1% /dev
tmpfs                 565M     0  565M   0% /dev/shm
lrm                   565M  2.2M  563M   1% /lib/modules/2.6.28-13-server/volatile
/dev/sdb1              74G   58G   13G  83% /media/drive
```here are some of the lines out of /var/log/messages

```
Jul  7 20:47:33 ivan-server kernel: [332581.138323] possible SYN flooding on port 50015. Sending cookies.
Jul  7 20:48:33 ivan-server kernel: [332641.330760] possible SYN flooding on port 50015. Sending cookies.
Jul  7 20:49:33 ivan-server kernel: [332701.584303] possible SYN flooding on port 50015. Sending cookies.
Jul  7 20:50:34 ivan-server kernel: [332762.392247] possible SYN flooding on port 50015. Sending cookies.
Jul  7 20:51:34 ivan-server kernel: [332822.572557] possible SYN flooding on port 50015. Sending cookies.
Jul  7 20:52:36 ivan-server kernel: [332884.259741] possible SYN flooding on port 50015. Sending cookies.
Jul  7 20:53:37 ivan-server kernel: [332944.998200] possible SYN flooding on port 50015. Sending cookies.
Jul  7 20:54:39 ivan-server kernel: [333006.982103] possible SYN flooding on port 50015. Sending cookies.
Jul  7 20:55:42 ivan-server kernel: [333070.803090] possible SYN flooding on port 50015. Sending cookies.
Jul  7 20:56:43 ivan-server kernel: [333130.976892] possible SYN flooding on port 50015. Sending cookies.
Jul  7 20:57:44 ivan-server kernel: [333192.055600] possible SYN flooding on port 50015. Sending cookies.
Jul  7 20:58:44 ivan-server kernel: [333252.091667] possible SYN flooding on port 50015. Sending cookies.
Jul  7 20:59:46 ivan-server kernel: [333314.666709] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:00:47 ivan-server kernel: [333375.402962] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:01:48 ivan-server kernel: [333436.098753] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:02:48 ivan-server kernel: [333496.645873] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:03:51 ivan-server kernel: [333558.918112] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:04:51 ivan-server kernel: [333619.297387] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:05:52 ivan-server kernel: [333679.956277] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:06:52 ivan-server kernel: [333740.655712] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:07:59 ivan-server kernel: [333807.629983] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:09:04 ivan-server kernel: [333872.395763] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:10:06 ivan-server kernel: [333934.279899] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:11:06 ivan-server kernel: [333994.397218] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:12:06 ivan-server kernel: [334054.547402] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:13:07 ivan-server kernel: [334115.828057] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:14:08 ivan-server kernel: [334176.304147] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:15:09 ivan-server kernel: [334237.339737] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:16:10 ivan-server kernel: [334298.075861] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:17:11 ivan-server kernel: [334359.132071] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:18:11 ivan-server kernel: [334419.857311] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:19:12 ivan-server kernel: [334480.292260] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:20:12 ivan-server kernel: [334540.471882] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:21:12 ivan-server kernel: [334600.589898] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:22:13 ivan-server kernel: [334661.153876] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:23:13 ivan-server kernel: [334721.397663] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:24:15 ivan-server kernel: [334783.330958] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:25:16 ivan-server kernel: [334843.931468] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:26:21 ivan-server kernel: [334909.581395] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:27:27 ivan-server kernel: [334975.294011] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:28:28 ivan-server kernel: [335036.381852] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:29:30 ivan-server kernel: [335098.371242] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:30:30 ivan-server kernel: [335158.856837] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:31:31 ivan-server kernel: [335219.452607] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:32:31 ivan-server kernel: [335279.558647] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:33:33 ivan-server kernel: [335341.680112] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:34:34 ivan-server kernel: [335402.288920] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:35:35 ivan-server kernel: [335463.147520] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:36:35 ivan-server kernel: [335523.185663] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:37:37 ivan-server kernel: [335585.117351] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:38:38 ivan-server kernel: [335646.763784] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:39:47 ivan-server kernel: [335715.030380] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:40:47 ivan-server kernel: [335775.231999] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:41:52 ivan-server kernel: [335840.523547] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:42:53 ivan-server kernel: [335900.900834] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:43:53 ivan-server kernel: [335960.923566] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:44:54 ivan-server kernel: [336022.108074] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:45:58 ivan-server kernel: [336086.852264] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:47:00 ivan-server kernel: [336148.472609] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:48:00 ivan-server kernel: [336208.750959] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:49:04 ivan-server kernel: [336272.782076] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:50:09 ivan-server kernel: [336337.348124] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:51:09 ivan-server kernel: [336397.487391] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:52:10 ivan-server kernel: [336458.657957] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:53:16 ivan-server kernel: [336524.104396] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:54:17 ivan-server kernel: [336585.134882] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:55:17 ivan-server kernel: [336645.877168] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:56:20 ivan-server kernel: [336708.108266] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:57:22 ivan-server kernel: [336770.010702] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:58:23 ivan-server kernel: [336831.057795] possible SYN flooding on port 50015. Sending cookies.
Jul  7 21:59:23 ivan-server kernel: [336891.518376] possible SYN flooding on port 50015. Sending cookies.
Jul  7 22:24:50 ivan-server -- MARK --
Jul  7 22:44:50 ivan-server -- MARK --
Jul  7 23:04:50 ivan-server -- MARK --
Jul  7 23:24:50 ivan-server -- MARK --
Jul  7 23:44:50 ivan-server -- MARK --
Jul  8 00:04:50 ivan-server -- MARK --
Jul  8 00:24:50 ivan-server -- MARK --
Jul  8 00:44:50 ivan-server -- MARK --
Jul  8 01:04:50 ivan-server -- MARK --
Jul  8 01:24:50 ivan-server -- MARK --
Jul  8 01:44:50 ivan-server -- MARK --
Jul  8 02:04:50 ivan-server -- MARK --
Jul  8 02:24:50 ivan-server -- MARK --
Jul  8 02:44:50 ivan-server -- MARK --
Jul  8 03:04:50 ivan-server -- MARK --
Jul  8 03:24:50 ivan-server -- MARK --
Jul  8 03:44:50 ivan-server -- MARK --
Jul  8 04:04:50 ivan-server -- MARK --
Jul  8 04:24:50 ivan-server -- MARK --
Jul  8 04:44:50 ivan-server -- MARK --
Jul  8 05:04:50 ivan-server -- MARK --
Jul  8 05:24:50 ivan-server -- MARK --
Jul  8 05:44:50 ivan-server -- MARK --
Jul  8 06:04:50 ivan-server -- MARK --
Jul  8 06:24:50 ivan-server -- MARK --
Jul  8 06:36:06 ivan-server syslogd 1.5.0#5ubuntu3: restart.
Jul  8 07:04:50 ivan-server -- MARK --
Jul  8 07:24:50 ivan-server -- MARK --
Jul  8 07:44:50 ivan-server -- MARK --
Jul  8 08:04:50 ivan-server -- MARK --
Jul  8 08:24:50 ivan-server -- MARK --
Jul  8 08:44:50 ivan-server -- MARK --
Jul  8 09:04:50 ivan-server -- MARK --
Jul  8 09:24:50 ivan-server -- MARK --
Jul  8 09:44:50 ivan-server -- MARK --
Jul  8 10:04:50 ivan-server -- MARK --
Jul  8 10:24:50 ivan-server -- MARK --
Jul  8 10:44:50 ivan-server -- MARK --
Jul  8 11:04:50 ivan-server -- MARK --
Jul  8 11:24:50 ivan-server -- MARK --
Jul  8 11:44:50 ivan-server -- MARK --
Jul  8 12:04:50 ivan-server -- MARK --
Jul  8 12:24:50 ivan-server -- MARK --
Jul  8 12:44:50 ivan-server -- MARK --
Jul  8 13:04:50 ivan-server -- MARK --
Jul  8 13:24:50 ivan-server -- MARK --
Jul  8 13:44:50 ivan-server -- MARK --
Jul  8 14:04:50 ivan-server -- MARK --
Jul  8 14:24:50 ivan-server -- MARK --
Jul  8 14:44:50 ivan-server -- MARK --
Jul  8 15:04:50 ivan-server -- MARK --
Jul  8 15:24:50 ivan-server -- MARK --
Jul  8 15:44:50 ivan-server -- MARK --
Jul  8 16:04:50 ivan-server -- MARK --
Jul  8 16:24:50 ivan-server -- MARK --
Jul  8 16:44:50 ivan-server -- MARK --
Jul  8 17:04:50 ivan-server -- MARK --
Jul  8 17:24:50 ivan-server -- MARK --
Jul  8 17:44:50 ivan-server -- MARK --
Jul  8 18:04:50 ivan-server -- MARK --
Jul  8 18:24:50 ivan-server -- MARK --
Jul  8 18:44:50 ivan-server -- MARK --
Jul  8 19:04:50 ivan-server -- MARK --
Jul  8 19:24:50 ivan-server -- MARK --
Jul  8 19:44:50 ivan-server -- MARK --
Jul  8 20:04:50 ivan-server -- MARK --
Jul  8 20:24:50 ivan-server -- MARK --
Jul  8 20:44:50 ivan-server -- MARK --
Jul  8 21:04:50 ivan-server -- MARK --
Jul  8 21:24:50 ivan-server -- MARK --
Jul  8 21:44:50 ivan-server -- MARK --
Jul  8 22:04:50 ivan-server -- MARK --
Jul  8 22:24:50 ivan-server -- MARK --
Jul  8 22:44:50 ivan-server -- MARK --
Jul  8 23:04:50 ivan-server -- MARK --
Jul  8 23:24:50 ivan-server -- MARK --

```
50015 is the port i run my torrent client on. other than that message and the syslogd one, there's nothing else of significance.

i currently have a monitor plugged into this machine. to be able to ssh into it, i just plugged in a keyboard and pressed an arrow key so the monitor wasn't sleeping anymore. is it possibly a power management thing? how do i change power management settings in ubuntu server?

---

### Post by dragos2 on 2009-07-10
here is what I think it happens:

Too many torrents -> kernel thinks it sees a syn flood and block many of the new 
connection attempts -> this is why you can connect from localhost(with attached monitor)

How to fix: increase the number of total connections supported by the kernel
using sysctl, also increase the network I/O buffers and very important switch off
the magic cookie from sysctl -> that way you will be able to log in any time if the
server is not under a real attack ;)

---

### Post by windependence on 2009-07-10
> **dragos2 said:**
> here is what I think it happens:

Too many torrents -> kernel thinks it sees a syn flood and block many of the new 
connection attempts -> this is why you can connect from localhost(with attached monitor)

How to fix: increase the number of total connections supported by the kernel
using sysctl, also increase the network I/O buffers and very important switch off
the magic cookie from sysctl -> that way you will be able to log in any time if the
server is not under a real attack ;)

Thanks dragos, you beat me to it. I knew there had to be something in the logs. 

To the OP, when you have a problem like this, if you see a constant message in the logs, you should copy it and google it for a solution. Usually someone else has had the problem.

-Tim

---

### Post by dragos2 on 2009-07-10
> **windependence said:**
> Thanks dragos, you beat me to it. I knew there had to be something in the logs. 

To the OP, when you have a problem like this, if you see a constant message in the logs, you should copy it and google it for a solution. Usually someone else has had the problem.

-Tim

Your welcomed ;)

---

### Post by garsh0p on 2009-07-10
> **dragos2 said:**
> here is what I think it happens:

Too many torrents -> kernel thinks it sees a syn flood and block many of the new 
connection attempts -> this is why you can connect from localhost(with attached monitor)

How to fix: increase the number of total connections supported by the kernel
using sysctl, also increase the network I/O buffers and very important switch off
the magic cookie from sysctl -> that way you will be able to log in any time if the
server is not under a real attack ;)
can you tell me how to do this specifically? thanks.

---

### Post by windependence on 2009-07-11
These parameters are controlled in your /etc/sysctl.conf file. Use an editor such as nano or VI to chaange them. You may want to try them first by changing them on the command line (this isn't permanent) so that if you hose the system, you can reboot and recover.

You can view your current config by doing:

```
sudo sysctl -a | sort | more
```

Try the change by doing:

```
sudo sysctl -w kern.maxfiles=10000
sudo sysctl -w kern.ipc.maxsockbuf=10485666
sudo sysctl -w kern.ipc.maxsockets=16424


```

I am NOT positive on these sysctl parameters, they could be FreeBSD since almost all my stuff is *BSD. Let's see if dragos suggests anything. You certainly could try this and see since you are using the -w option. If it works you would add it permanently to your /etc/sysctl.conf file like this:

```
kern.maxfiles=10000
kern.ipc.maxsockbuf=10485666[COLOR=#000000]
[/COLOR]kern.ipc.maxsockets=16424

```

**[COLOR=Red]NOTE: Messing with sysct.confl is risky. Make a backup of the file before you modify it.[/COLOR]**

-Tim

---

### Post by garsh0p on 2009-07-11
my server become unresponsive again this morning, so i checked my logs and saw this:

```
Jul 11 10:41:58 ivan-server kernel: [119159.462665] Clocksource tsc unstable (delta = 2902221570834 ns)
```

i googled it and found this

[http://www.linuxquestions.org/questions/fedora-35/clocksource-tsc-unstable-568932/](http://www.linuxquestions.org/questions/fedora-35/clocksource-tsc-unstable-568932/)

this guy has a problem with his server being unstable and disabled acpi. i went ahead and did that. i'll report back if i still have the issue.

---

### Post by yeaitsdark on 2009-07-11
Does it simply fail on ssh? Is the network timing out period? I had an issue a while back where for whatever reason the server didn't like getting it's address from dhcp and would be "unresponsive remotely".

Like someone said perhaps you are running a few too many torrents and it's more or less dropping additional requests? 

If so I suggest making it's address static if not already, binding the torrent server to a specific interface (if you have more than one) and then limiting said application to a specific port and number of open connections. Just my thinking, because well based on what you were saying if you can go there physically log in and be fine - makes me thing it's a network issue vs performance based on the logs.

---

