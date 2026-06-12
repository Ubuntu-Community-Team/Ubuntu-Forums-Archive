---
title: "Advice for fileserver, disk spindown, partition, SAMB"
date: 2011-05-16
forum: Server Platforms
---

### Post by volkswagner on 2011-05-16
Greetings,

I am seeking advice/opinions on a fileserver build.

I'm utilizing an old Pent2box, 400MHz, 512MB RAM with a SATA card containing two 500Gig drives and two more available slots to expand.

I have Ubuntu 10.04 installed on a CF card with IDE to CF adapter.

I don't expect to have much traffic on the server so I want the two SATA disks to spin down.

Questions:
[LIST=1]
[*]If I mount one drive or partition on one of the SATA drives as /home, will this impact spindown just by user login?  I wanted to have SAMBA [home] shares for easy config, but spindown is more important, so I'd configure shares manually if need be.
[*]I'm concerned with '/' filling up since it is only a 2gig card filled to 50% after apt update.  How can I safeguard root file system from filling, keeping in mind spindown?  I think mounting /var to a SATA partition will have too much log activity and not spindown.
[*]At this time I don't have any swap configured, as I did not want to trash the CF, plus have limited space.  Any advice on handling swap in this instance?
[*]Is there any other advice do's, don'ts you'd like to offer?
[/LIST]

I have also added a sound card with the hopes of running MPD in the near or distant future.

I also added a Gigabit NIC, with hopes of creating a second subnet at home for wired clients with Gigabit cards.  As far as I know, I need to separate non-gigabit devices or they will bring down the speed.  Again future project would be to set this up with DHCP for the wired clients.

Thanks for taking the time.

---

### Post by gordintoronto on 2011-05-16
Can you boot from a SATA drive? The CF card seems like an awkward kludge. If not, perhaps you could pick up a 40 GB IDE hard drive for next to nothing.

You want to spin down to save power? An Atom-based Netop would probably pay for itself in a reasonable amount of time.

---

### Post by a2j on 2011-05-16
imho, that box is a little slow for the task. I don't think you're gonna get gigabit speeds.

---

### Post by volkswagner on 2011-05-16
> **a2j said:**
> imho, that box is a little slow for the task. I don't think you're gonna get gigabit speeds.


I'd be happy enough if my PCI bus became the bottleneck.

From my limited knowledge and a little guessing, I believe my PCI bus is more than capable of 100MBs.


> **gordintoronto said:**
> Can you boot from a SATA drive? The CF card seems like an awkward kludge. If not, perhaps you could pick up a 40 GB IDE hard drive for next to nothing.

You want to spin down to save power? An Atom-based Netop would probably pay for itself in a reasonable amount of time.

The machine with one IDE hard drive idled ~45watt's.  My Atom with One SATA drive idled in the 38watt range.  I know newer Atoms without the 945Video consume less.  I still may upgrade in the future, as this is a bit of a proof of concept/benchmark for the argument....  My future build would seek a sub 20watt board/cpu combo with some green drives, in a large quiet case.

Yes, the reason for CF is for power consumption.  At present time I'll be replacing a Gigabit Linkstation NAS device which is under 15watts.  I am trying to get more features with minimal increase in power consumption.

I must confess, this box is my first PC purchase from 1998... A little sentimental.   ;)

---

### Post by mikewhatever on 2011-05-16
I think you should keep the OS on the CF card and leave the hard drivers to samba shares. It's kind of expected for the first (after installation) update to be large, there has been lots of bug fixes in a year.
To reclaim the space, clean the cached packages:
```
sudo apt-get clean
```

...keep an eye on the space usage with 'df -h'.

---

### Post by volkswagner on 2011-05-16
> **mikewhatever said:**
> I think you should keep the OS on the CF card and leave the hard drivers to samba shares. It's kind of expected for the first (after installation) update to be large, there has been lots of bug fixes in a year.
To reclaim the space, clean the cached packages:
```
sudo apt-get clean
```

...keep an eye on the space usage with 'df -h'.


Thanks for the reminder.  I have used apt-get clean in the past.  On a WebDT366 with only 512MB hard drive I used it.  I ended up mounting /var/cache/apt on a USB and Deleting those files on the / drive.  It did become cumbersome, but got some much needed disk space.  I don't think I'll have to do this on my server for a few percent disk space.

I was uncertain if apt-get clean would only be temporary (until next apt-get update)... It sticks... 

Thanks, here is what it looked like for me to get 7% disk space back.

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             1.9G  981M  834M  55% /


sudo apt-get clean

eric@fileserver:~$ sudo df -h /
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             1.9G  862M  954M  48% /
```

---

### Post by mikewhatever on 2011-05-16
Another way to free space is to remove the unneeded old kernels and headers. You can check what versions are installed with the following:
```
dpkg -l | grep -e linux-image -e headers
```

You can easily automate 'apt-get clean' with a monthly cron job.

---

### Post by jongers on 2012-06-15
> **mikewhatever said:**
> I think you should keep the OS on the CF card and leave the hard drivers to samba shares. It's kind of expected for the first (after installation) update to be large, there has been lots of bug fixes in a year.
To reclaim the space, clean the cached packages:
```
sudo apt-get clean
```...keep an eye on the space usage with 'df -h'.

Good advice, the OS should be fine on the CF, it will provide an extra layer of stability when the drives spin down so there is minimal mechanical movement in the system.

[B]RE: Spin Down
[/B]**Installing and configuring hdparm**

I tested tools/modules like  laptop-mode-tools, pm-utils en noflushd. But these did not work well. I  had more success with hdparm. This command will not work on external  USB hard disks, via SATA it works perfect. Open the /etc/hdparm.conf  file and set the desired spindown time:
** # vi /etc/hdparm.conf** * /dev/sda { #spindown_time = 60  # 5 min #spindown_time = 240 # 20 min #spindown_time = 250 # 30 min #spindown_time = 280 # 1 hour spindown_time = 340 # 2 hours }*looks like it might be worth playing with if you have concerns about drive degradation and power consumption. (taken from [http://info4admins.com/tips-to-spindown-your-hard-disk-in-debian-or-ubuntu/](http://info4admins.com/tips-to-spindown-your-hard-disk-in-debian-or-ubuntu/) )

With the two 500GB drives in a file server, have you considered running an mdadm software raid.   If you haven't looked into this before, you could either use mirroring or add an additional drive with raid-5.  Which would give you redundancy if a drive fails (at the cost of available space).

---

### Post by nothingspecial on 2012-06-15
Please don't bump old threads to the top.

Closed.

---

