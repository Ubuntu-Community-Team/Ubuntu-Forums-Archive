---
title: "Ubuntu on Virtualbox says the disk is full but it isn't"
date: 2019-01-19
forum: Virtualisation
---

### Post by luxocrypto on 2019-01-19
Hi,

Since a couple of days my Ubuntu VM says its disk space is almost full, except it isn't. I have just created that VM a few weeks ago and I hardly used it. 

When I run Disk Usage it says there 9.1 GB free out of 100. But when I look a the disk usage > "Size" column, it seems to me there's only 6 or 7 GB used.

I also noticed the /proc folder is 140.7 TB. Yes, TB! But I googled it and this shouldn't be a problem (it's like temp files that don't count).

I'm a bit lost. Any suggestions?

---

### Post by ajgreeny on 2019-01-19
What does terminal command ```
df -hT
``` show you as output?

Please use **Code-Tags** for terminal output to show that text in a more readable format, the same as it is in the terminal, not as plain text. See my signature below for a **How-to**

---

### Post by luxocrypto on 2019-01-19
Thank you @ajgreeny for helping me.

It show this:

```
$ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  1,9G     0  1,9G   0% /dev
tmpfs          tmpfs     395M  1,6M  393M   1% /run
/dev/sda1      ext4       94G   90G     0 100% /
tmpfs          tmpfs     2,0G     0  2,0G   0% /dev/shm
tmpfs          tmpfs     5,0M  4,0K  5,0M   1% /run/lock
tmpfs          tmpfs     2,0G     0  2,0G   0% /sys/fs/cgroup
/dev/loop1     squashfs   15M   15M     0 100% /snap/gnome-logs/37
/dev/loop8     squashfs   35M   35M     0 100% /snap/gtk-common-themes/319
/dev/loop4     squashfs   15M   15M     0 100% /snap/gnome-logs/45
/dev/loop12    squashfs  2,3M  2,3M     0 100% /snap/gnome-calculator/260
/dev/loop5     squashfs  3,8M  3,8M     0 100% /snap/gnome-system-monitor/57
/dev/loop6     squashfs   90M   90M     0 100% /snap/core/6130
/dev/loop0     squashfs   13M   13M     0 100% /snap/gnome-characters/103
/dev/loop10    squashfs   87M   87M     0 100% /snap/core/4917
/dev/loop11    squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/74
/dev/loop13    squashfs  3,8M  3,8M     0 100% /snap/gnome-system-monitor/51
/dev/loop3     squashfs  2,4M  2,4M     0 100% /snap/gnome-calculator/180
/dev/loop7     squashfs   13M   13M     0 100% /snap/gnome-characters/139
/dev/loop9     squashfs   35M   35M     0 100% /snap/gtk-common-themes/818
/dev/loop2     squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/70
vmshare        vboxsf    1,8T  318G  1,5T  18% /media/sf_vmshare
tmpfs          tmpfs     395M   28K  395M   1% /run/user/121
tmpfs          tmpfs     395M   36K  395M   1% /run/user/1000

```

The vmshare is a Virtualbox Shared Folder on the host (so the 318G used is on the host, it's not on the VM).

---

### Post by luxocrypto on 2019-01-19
Correction: just checked the vmshare folder on the host. It's empty. So why does it say 318G?

---

### Post by The Cog on 2019-01-19
Looky here:
```
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda1      ext4       94G   90G     0 100% /
```
It is almost full. I believe that some space is reserved for root in order to prevent system crashes when users fill it up, so you probably can't create any more files as a normal user. Most of the stuff is probably in /home (the system stuff normally uses maybe 10G). This command should give you a good idea:
```
sudo du -sh /home
```

---

### Post by luxocrypto on 2019-01-19
Thank you, The Cog.

I saw that. But I just created that VM like a few weeks ago and I hardly used  it. It can't be full. No pictures at all, no videos, no documents, no backups, nothing there (yet).

Anyway, I can't login anymore. So can't give you that "du -sh" for now. Looks like I'm running out of options.

I'm getting this menu:
[https://www.howtogeek.com/wp-content/uploads/2014/09/xubuntu-14.04-recovery-mode-menu.png.pagespeed.gp+jp+jw+pj+ws+js+rj+rp+rw+ri+cp+md.ic.tJHIR7oEvc.png](https://www.howtogeek.com/wp-content/uploads/2014/09/xubuntu-14.04-recovery-mode-menu.png.pagespeed.gp+jp+jw+pj+ws+js+rj+rp+rw+ri+cp+md.ic.tJHIR7oEvc.png)

I tried just about everything. Doesn't really help much.

---

### Post by The Cog on 2019-01-20
I would hope you could use the option to drop to a root shell, and you should be able to run some commands from there (as I say, I think some space is reserved for root even if other users can't log in).
If so, try these two commands:
```
sudo du --summarize --si --one-file-system /
sudo du --max-depth=1 --si --one-file-system /
sudo du --summarize --si /home/*
```

---

### Post by luxocrypto on 2019-01-21
I can't login anymore. I see that Recovery Menu but even when I select to boot to root it just give me a black screen with:
```
anacron.service
NetworkManager-dispatcher.service
cups.service
colord.service
```

That's it. I will just reinstall the VM.

---

### Post by The Cog on 2019-01-21
At this point, that's probably the path of least resistance. When you get it working, it would be worth running **df -h** once a day just to keep an eye on disk usage. I wonder if something was filling your logs with error messages - hardware it's not really happy with perhaps.

---

