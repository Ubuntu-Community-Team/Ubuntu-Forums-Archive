---
title: "Creating a RAID1 disk"
date: 2020-08-22
forum: Server Platforms
---

### Post by richieserver on 2020-08-22
I am trying to create a RAID 1 disks but something didn't go quite right

When I booted up today it didn't list the complete setup of the raid, I typed 
```

lsblk


```

and all the drives seemed to not show the RAID 1 configuration

as in MD1 and RAID 1 in the list

I edited the fstab configuration file and put in the correct UUID number before I shut down the server

The only difficulty I encountered was when I put in

```

sudo mount /dev/md1 /mnt/raid1

```

when the error said that there were multiple filesystems on the RAID configuration

I got rid of the problem when I used
```

sudo wipefs --all --force /dev/md1


```

and preceded to format the disks using
```

sudo mkfs.ext4 /dev/md1

```

Can anyone tell me why it never mounted the RAID 1 drive on start up?

Also, do I use CTRL+C to stop watching /dev/md1?

```

sudo watch --detail /dev/md1

```

---

### Post by TheFu on 2020-08-22
What settings and data would we need to see to know what failed?
Maybe post those?

Saying what you typed, without the output, is like asking someone blind from birth to describe "blue-green".
Help us see, please.

---

### Post by richieserver on 2020-08-22
> **TheFu said:**
> What settings and data would we need to see to know what failed?
Maybe post those?

Saying what you typed, without the output, is like asking someone blind from birth to describe "blue-green".
Help us see, please.


I think I've messed things up, and have to re-install the server again

I don't know what you mean by what settings you want, sorry but I am new to this

---

### Post by TheFu on 2020-08-22
When you run commands to gather information, perhaps showing the output from each to us would be helpful?
When you modify a config file to mount something, perhaps showing the contents of that config file would be helpful?
Would be useful to see the supporting data that lead to the entries in the config file too, right?

Perhaps?

We can't read your mind or guess everything about the system setup.  You are doing a good job at saying something is wrong, but not so good at showing anything useful to get help.

```
lsblk -e 7 -o name,size,type,fstype,mountpoint
more /etc/fstab
blkid
more /proc/mdstat
```
For starters.  If you don't understand a command, you can look it up. Be certain to understand the options too. All of those above don't change anything. They just show data so decisions can be made using facts.

---

### Post by richieserver on 2020-08-22
Thanks, but at the moment I have re-installed server, but it's causing all sorts of problems now, not related to this unfortunately, so can't check or redo the raid attempt

---

### Post by richieserver on 2020-08-24
I found a simpler solution the problem

I've installed Webmin, and marking this thread as Solved

---

