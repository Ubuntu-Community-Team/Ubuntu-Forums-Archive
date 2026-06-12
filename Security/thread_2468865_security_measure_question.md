---
title: "security measure question"
date: 2021-11-12
forum: Security
---

### Post by Old Jimma on 2021-11-12
Hi Forum Folks:

I've read that among the best ways of keeping your computer secure is by disconnecting it from the internet.

I want to know how I can disconnect if from the internet, while keeping it on my home network.

Thanks,
Old

---

### Post by slickymaster on 2021-11-12
*Thread moved to **Security**.*

---

### Post by TheFu on 2021-11-12
Unplug all the routers.
Do not allow any routing to the internet. Block all external DNS. Basically, this requires having multiple subnets - one for when you need internet and the other, commonly called a "Home lab", which cannot access anything outside the local subnet. Just putting some systems on the same LAN switch without any router won't make them magically work.  A router makes this really easy and if it will never be connected to the internet, a used $10 router would be fine.

There are 500,000+ different ways to accomplish these things.  My home lab is in a virtual network using a virtual router with everything running inside virtual machines.

Also be certain you have methods to validate nothing is leaking in either direction.  That includes the knowledge to use them correctly and understand the results.  If your networking knowledge is minimal, that's the place to start.

---

### Post by Doug S on 2021-11-12
I think these iptables rules, written as a script, would do it:

```
#!/bin/sh
FWVER=0.01
#
# block_internet 2021.11.12 Ver:0.01
#       Block internet access.
#       Flushes OUTPUT chain, in case of re-run.
#       Assumes default policies of ACCEPT.
#
echo "block internet access. $FWVER..\n"

# The location of the iptables program
#
IPTABLES=/sbin/iptables

# Set some stuff
# Adjust these values for your system.
#
EXTIF="br0"
UNIVERSE="0.0.0.0/0"
LAN="192.168.111.0/24"

# Clear old OUTPUT table rules
#
$IPTABLES -F OUTPUT

# loopback interface is valid.
#
$IPTABLES -A OUTPUT -o lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT

# Allow LAN access
#
$IPTABLES -A OUTPUT -o $EXTIF -d $LAN -j ACCEPT

# If this computer uses DHCP, then allow broadcast BOOTP
#
$IPTABLES -A OUTPUT -o $EXTIF -p udp --sport 68 --dport 67 -j ACCEPT

# Block anything else
#
$IPTABLES -A OUTPUT -o $EXTIF -j DROP
```You might have to figure out how to merge this into any existing iptables rules you already have. And after awhile, on my test server, I have:

```
doug@s19:~/iptables/misc$ sudo iptables -xvnL
Chain INPUT (policy ACCEPT 285 packets, 19720 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
       2      100 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0
     187    26063 ACCEPT     all  --  *      br0     0.0.0.0/0            192.168.111.0/24
       0        0 ACCEPT     udp  --  *      br0     0.0.0.0/0            0.0.0.0/0            udp spt:68 dpt:67
      22     1816 DROP       all  --  *      br0     0.0.0.0/0            0.0.0.0/0
```

---

### Post by Old Jimma on 2021-11-13
TheFu wrote:

> If your networking knowledge is minimal, that's the place to start. 

Hmm. How does that TheFu  accurately read minds just by looking over forum posts? Some sort of sorcery, probably.

Well, I've got a place to start, and that's good.

Hey, TheFu: thanks for your suggestions on using a pi with rsync for a backing thngs up. It works very well and has pulled my cookies out of a burning oven a few times already.

You might like to know that
[LIST]
[*]the most recent version of Ubuntu on a pie doesn't work well enough to use as a solid backup platform with a pi,
[*]Pi OS is solid
[*]rsync syntax can be slightly different depending on what platform you are using
[*]rdiff-backup version for pi and ubuntu are different. Differences were enough to make me run away from rdiff-backup.
[*]

Thanks for outlining my backup project.

Stranger in a strange land,
Old
[/LIST]

---

### Post by Old Jimma on 2021-11-13
Thank you, Doug.

Sincerely,
Old

---

### Post by TheFu on 2021-11-13
> **Old Jimma said:**
> 
Hmm. How does that TheFu  accurately read minds just by looking over forum posts? Some sort of sorcery, probably.

Well, I've got a place to start, and that's good.

Hey, TheFu: thanks for your suggestions on using a pi with rsync for a backing thngs up. It works very well and has pulled my cookies out of a burning oven a few times already.

You might like to know that
[LIST]
[*]the most recent version of Ubuntu on a pie doesn't work well enough to use as a solid backup platform with a pi,
[*]Pi OS is solid
[*]rsync syntax can be slightly different depending on what platform you are using
[*]rdiff-backup version for pi and ubuntu are different. Differences were enough to make me run away from rdiff-backup.
[/LIST]Thanks for outlining my backup project.
Stranger in a strange land,
Old


How do I *know*?  I don't.  But every clock is correct twice a day. Once in a while, a blind squirrel finds a nut.  Same for me - plus guessing. ;)
I've never used Ubuntu on any raspberry pi hardware and I've been using them for stuff about 5 yrs. I tend to run purpose-build Pi distros, since the hardware isn't really meant to be used as a general purpose server and I must have stronger hardware for other needs, so having a Pi as well, doesn't make sense to me.  That's what virtual machines and Linux containers (that we build ourselves) are good at.

By PiOS, I assume you mean Raspian?  It is mostly like Debian, just lighter and customized for Pi hardware. No need to have 500 NIC drivers when there are only 5 possible NICs on a Pi.

I'm fairly sure that rsync options and behavior don't differ by platform, but the version definitely matters.
The same applies to rdiff-backup.  Version 1.x of rdiff-backup was created using python2.  Version 2.x of rdiff-backup was created using python3.  The files in the backup sets are 100% compatible (in my testing), but if there is a client and server, the versions need to match.  Before 2016, this was due to protocol still maturing, but after that, it is due to python2 and python3 serialization changes. No python2 client is compatible with any python3 serialization.  Sometimes life is like that.  I've posted that I ported the python2 rdiff-backup to 20.04 and I've been using that for my 20.04 clients so an 18.04 backup server can "pull" backups.

To me, rsync just doesn't provide a sufficient backup tool. But for anyone using rsync who wants easier versioning, there are tools which behave as expected using rsync and hardlinks.  These tools are in the ubuntu repos, **rsnapshot**, **rbackup** and **back-in-time** each use it.  BTW, rdiff-backup also uses librsync, along with rdiff and the python-based rdiff-backup.  There are flaws with using rsync and hardlinks, but using rsync alone is so much worse for versioned backups (too much storage/time required), that even with the flaws that hardlinks cause, I'd much rather see people use rsnapshot compared to any other tools besides rdiff-backup.  But every admin needs to pick the best tool for their needs.

Some good rsnapshot links:
[Https://popey.com/blog/2020/12/straightforward-linux-backups-with-rsnapshot/](Https://popey.com/blog/2020/12/straightforward-linux-backups-with-rsnapshot/)
[Https://www.cyberciti.biz/faq/linux-unix-apple-osx-bsd-rsync-copy-hard-links/](Https://www.cyberciti.biz/faq/linux-unix-apple-osx-bsd-rsync-copy-hard-links/)

If you need a GUI, Back-In-Time is basically a slick rsnapshot that runs hourly, then selectively removes older backup-sets (really just hardlinks for files that are unchanged, but copies of the files that did change) over time.  The closer to "now" we are, the more "backup sets" back in time has.  After a few days, the hourly sets are deleted to keep just a daily backup set.  Over a few weeks, the daily backups are removed to keep just the weekly.  Longer than a month and only 1 set is retained/month.  For every year, only 1 set is retained.  It is pretty swift, especially for capturing backups of user data. I've never used it for system-wide backups. GUIs get in the way of that for me. They've probably solved that. I setup Back-in-Time for my Mom to use around 2010. She was happy it was there. Restoring a specific version of a specific file was something she did herself.

It is possible to create your own rsnapshot/rbackup/back-in-time using a little scripting and rsync, if you like. In the 1990s, almost every Unix book had a script created by the author just for that purpose. I'd be surprised if those scripts weren't still being used inside 1000+ companies somewhere.

But we can just **sudo apt install rsnapshot** and read the guides above ... or at help.ubuntu.com for this tool. No need to reinvent the wheel.

---

### Post by Old Jimma on 2021-11-14
Hi TheFu:

Very grateful for your reply. Yes, sometimes a squirrel finds a nut that it had buried, and sometimes the Atlanta Braves win the World Series. So, it is possible to be right.

Here are responses to some of your comments.

PI OS:       [https://www.raspberrypi.com/software/](https://www.raspberrypi.com/software/)

> I'm fairly sure that rsync options and behavior don't differ by platform, but the version definitely matters.

The options don't differ by platform, but the options that are required seem to depend on platform. I think this is suggested in a brief phrase on the man page. 

For example, for the PI OS, you've gotta specify the password along with a few other things that don't seem to be required if you are running 20.04 on a real (non-pi) computer. For example, here is what works for the pi:

> **sshpass -p 'passwird' **rsync --delete -az -e **ssh** [email]machine1@ip.addres[/email]s.1:/home/directory/ /mnt/wherever 

Stuff in bold doesn't seem to b required if are running a true 20.04 OS on a real (non-pi) computer. However, if you are running PI OS on a pi, these tweaks allow rsync to work in my experience.

> To me, rsync just doesn't provide a sufficient backup tool.
Yes, rsync has limitations... but can sort of be overcome by "versioning" backups in folders that are associated with calendar dates.... good if you have huge reliable hard drives. It is clumsy, but works well enough. 

rdiff_backup was my software of choice but gave me the willies because of the different versions available depending on operating systems. Seemed like I could expect a train wreck at the least convenient time because of that with between-platform rdiff-backup differences caused by differences in versions.

I don't wanna use gui because of the versioning issue described above, and greater flexibility and greater chance of standardization with command line. Also, it may be possible to run gui jobs with crontab, but I'm lazy and don't want to figure that out. Using command line stuff is challenging and "**fun-fulled**" enough. There are alot of security measures I want to implement that I think are best implemented using crontab with a command line shell script... for all I know, and that isn't much. I just know that it is something that does work.

GTG. Got to figure out why my ISP changed ip addresses for a few of my machines last night.

Tired Old Man from the Old Country

---

### Post by TheFu on 2021-11-14
ssh with keys doesn't seem to have issues with rsync or rdiff-backup going from my backup server (18.04 Ryzen) to a raspberry pi v3+.  Something must not be setup correctly there. My pi3 is a client, never a server.  It is a Kodi/mpd system, but doesn't have any local data.  This works:

```
$ rsync -avz osmc7491@pi3:/home/ /backups/pi3/
```

I don't have an rdiff-backup command to post because my "pull" setup has some complications that aren't easily answered without a book. But I bet 
```
$ rdiff-backup  --exclude-special-files   osmc7491@pi3::/home/  /backups/pi3/
```
will work fine.  Yep. It does.  So the issue is likely an ssh setup problem there.

Do you not use a ~/.ssh/config file?  Those will change your world, just as much as ssh-copy-id does.

Every 4-6 yrs, rdiff-backup has incompatible versions for a release.  When you looked, was in that time where the version transition was happening. That sucks.
I only mentioned the GUI for people who care about that.  I don't want a GUI for backup tools either.  Servers don't have GUIs and cron shouldn't work with any GUI program. I consider that a feature, no something lacking from cron.

I'm confused.  Why would your ISP have any control over LAN IP addresses?

To create ssh and push those keys: [Https://ubuntuforums.org/showthread.php?t=2433034&p=13916386#post13916386](Https://ubuntuforums.org/showthread.php?t=2433034&p=13916386#post13916386)
The "create" step is only needed once (per security type). Just run the ssh-copy-id command for each server system you want setup to access from that client.  Of course, when sudo is used, then the keys need to be from the root account, not the normal end-user account. There are security considerations in using root, so I add some other layers by creating a 'root-equiv' account just for backups. Being really good at knowing which userid is being used on which system for which program is mandatory for this added complexity.

---

### Post by Old Jimma on 2021-11-23
Hi TheFu:

I hope you'll find this follow-up. I found time to reply this morning.

I've wondered if I've got my client and server set up right.

Here are the hardware pieces that I have:[LIST]
[*]a rasberry pi with PI OS (formerly referred to as raspian, I think) operating system,
[*]4 other computers, each running 20.04. **I'll refer to these computers as A, B, C, and D**.
[*]
[/LIST]

Here is what my pi looks like:
[LIST]
[*]6 external hard drives mounted to it, 
[*]powered from powered SATA 3 USB hubs. 
[*]This works well... no shortage of electrical power going to the pi.
[/LIST]

Here is my goal
[LIST]
[*] back up **A, B, C, and D** to the **pi** according to a schedule that I specify in the pi's crontab.
[/LIST]

All machines have **ssh** installed. 

After generating the ssh key on the pi, I shared with with **A, B, C, and D**, e.g., 

> ssh-copy-id A@AsIPaddress


It all works nicely, except that **on the pi **I have to specify the password for **A, B, C, and D** in the "ssh rsync" command:


> sshpass -p 'Apassword' rsync --delete -az -e ssh A@AsIPaddress:/home/A/ /mnt/driveforA # /mnt/driveforA is mounted on the pi
[B]
I thought that the point of ssh was not having to use passwords![/B]

Then, I use a similar command for computers** B, C, and D**

Have I envisioned this wrong? The fact that I'm required to use passwords in the ssh command is a hint that I've got things set up wrong. Within the context of what I have, I've thought of the pi as the server and A, B, C and D as clients.

Your comments are welcome.

Sincerely,
Old

---

### Post by Old Jimma on 2021-11-23
TheFu:

I re-read your link. I'll try using different ssh-key for each client computer, and tell you how it goes.

Oldest
.. of the Cranky Old Ubuntinos

---

### Post by TheFu on 2021-11-23
The client machine changes based on where ssh is running.
If you create keys on A, B, C, and D then push those keys to the pi using ssh-copy-id - that's great. A, B, C, D each can connect to the pi without prompting for a password - you may need to unlock the ssh-key however.  But the transfer of keys from A --> pi doesn't mean that ssh from the pi --> A doesn't need a password.  You'd need to create an ssh-key on the pi, then use ssh-copy-id from the pi to each of A, B, C, D so connections in that direction work.

Please be very clear for which direction you want the backups to flow and from which system you want to initiate those commands.  I use "pull" backups, for security reasons. I also use a root-equivalent account to perform those backups because normal user accounts don't have access to all the files that need to be backed up in my situation.  And because using a root-equiv account is dangerous, I mitigate which client is allowed to connect using that account from which specific system(s).

When setup correctly, there is no mention at all of "ssh" in the rsync command.  It is just as I posted above.  Also, I did test that rdiff-backup command and it worked too, exactly as posted.  Both rdiff-back and rsync use ssh without us having to do anything extra. It has been the default for over a decade - probably over 15 yrs.

---

