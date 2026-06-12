---
title: "How long can a 12.04 Server 64bit stay up?"
date: 2012-10-01
forum: Server Platforms
---

### Post by Jorel on 2012-10-01
Hi guys,

I have my 12.04 64-bit server running on a i-5 proc and 4gb ram for a month now and i'm just wondering, can it stay up as long as i wanted it to or it needed to be shutdown once in a while? is there any maintenance required? because all i know is to apt-get update manually and i have a doubt on doing a apt-get upgrade... and i know its not a big issue but i just noticed that whenever i log in via putty, my memory rise upto 15% now, but when i hit top everything is normal....

due that i had it running now for fileserver and printer server and in the coming months, i will include a web server, mail server and FTP server within it.  

thanks in advance...

---

### Post by CharlesA on 2012-10-01
It can stay up as long as you want. However, it is a good idea to run updates once a week or once a month unless you have it set to automatically install security updates.

The only time I reboot my server is to boot into a new kernel, or another update that is flagged as "restart required." Here's the current uptime of my 12.04 box (which was installed when 12.04 was released):

```
     #               Uptime | System                                     Boot up
----------------------------+---------------------------------------------------
     1    20 days, 07:08:27 | Linux 3.2.0-29-generic    Fri Aug 10 07:20:09 2012
     2    18 days, 22:27:01 | Linux 3.2.0-26-generic    Wed Jul  4 09:57:42 2012
     3    18 days, 21:22:01 | Linux 3.2.0-24-generic    Sat May 26 15:19:01 2012
     4    18 days, 20:13:03 | Linux 3.2.0-24-generic    Thu May  3 10:48:22 2012
     5    15 days, 23:55:08 | Linux 3.2.0-27-generic    Wed Jul 25 06:49:11 2012
     6    15 days, 09:01:05 | Linux 3.2.0-30-generic    Wed Sep  5 22:00:38 2012
     7    15 days, 00:13:54 | Linux 3.2.0-25-generic    Thu Jun 14 12:41:52 2012
->   8     9 days, 23:09:20 | Linux 3.2.0-30-generic    Fri Sep 21 07:02:34 2012
     9     6 days, 07:08:01 | Linux 3.2.0-29-generic    Thu Aug 30 14:29:27 2012
    10     4 days, 21:00:16 | Linux 3.2.0-26-generic    Fri Jun 29 12:56:35 2012
----------------------------+---------------------------------------------------
1up in     5 days, 01:04:35 | at                        Sat Oct  6 07:16:27 2012
no1 in    10 days, 07:59:08 | at                        Thu Oct 11 14:11:00 2012
    up   155 days, 10:15:54 | since                     Sat Apr 28 19:41:15 2012
  down     0 days, 00:14:45 | since                     Sat Apr 28 19:41:15 2012
   %up               99.993 | since                     Sat Apr 28 19:41:15 2012

```

Do you plan are having this server accessible from the internet? If so, I would recommend against running ftp on it, and use sftp (via ssh) instead.

---

### Post by LHammonds on 2012-10-01
The server by itself can stay up without a reboot for a very long time.  It is usually due to application performance and memory leaks that may require a reboot more often.  A file server can remain up for a very long time, a Minecraft server on the other hand will require a reboot almost on a daily basis.

As you know, there are updates to the OS which require reboots to complete so you have to weigh the risks of not applying security patches when they are released.

I use Nagios to monitor all my servers and it lets me know when there are updates.  I then upgrade my test servers and then production.  Reboots are very fast and can be scheduled at off-peak hours so I typically don't care about having a long-running uptime number.  It is more important to me to keep my systems updated and running at optimum performance.

LHammonds

---

### Post by ian dobson on 2012-10-01
Hi,

I only ever reboot my backend server when it says a reboot is required on login.

I have afew boxes that aren't connected to the internet and they have an uptime of almost 500days. So a linux box can have very high uptimes. In windows the uptime counter doesn't even go past 56 days :lolflag:

Regards
Ian Dobson

---

### Post by Jorel on 2012-10-02
Hi,

so is "apt-get update" enough for now or do i need to do "apt-get upgrade"? coz its set for manual update and im still studying on a security that i will add...

Thanks for the advise guys..

---

### Post by LHammonds on 2012-10-02
I don't think apt-get update will do anything other than refresh what the currently available packages are available to be updated.  It is kinda like opening WindowsUpdate on a Windows PC and closing it without installing anything.

The "apt-get update" command is what I do just before the "apt-get safe-upgrade" command.

---

### Post by houstonbofh on 2012-10-02
Refresh the repository lists and see what is new.

```
sudo apt-get update
```

Run a basic upgrade.

```
sudo apt-get upgrade
```

Run an upgrade that requires changing packages.  (Partial upgrade in Update Manager)

```
sudo apt-get dist-upgrade
```

You need all three to stay current.

As to the question, I went to a client one time and we had to track down a "service" that no one knew where it was.  Turns out there was a Linux machine in an old closet under at least 50 pounds of cable.  Uptime was over 6 years.  Also last update! :shock:

But I am a fan of rebooting servers whenever I can.  That way I know they will come up when the reboot unexpectedly!

---

### Post by Jorel on 2012-10-03
im just afraid to upgrade my system due that it might have different configurations and some incompatibilities...

---

### Post by SeijiSensei on 2012-10-03
Upgrades won't change your configurations.  They will simply replace the current software with its more recent versions.

You should always take security updates, especially if you have Internet-facing services like mail or HTTP.  One way to limit the upgrades to just security ones is to comment out all the lines in /etc/apt/sources.list with the exceptions of the entries that point to security.ubuntu.com.  Then run "sudo apt-get update; sudo apt-get upgrade".

Another approach is to run a parallel server, perhaps in a VirtualBox VM on your desktop.  Configure the VM to be the same as your actual server.  The simplest method to do this is to install 12.04 into the VM, then use rsync to make the VM copy a clone of the actual one.  Then run the updates on the VM server and see if they cause any problems.  If not, then you can run them on the real server as well.

---

### Post by Jorel on 2012-10-03
what i usually do is im trying it 1st at my ubuntu 12.04 desktop before deploying it in the 12.04 server... although desktop and server are way different, i still think that the effect are somehow the same. (and hope what i thought was right)

---

### Post by CharlesA on 2012-10-03
> **SeijiSensei said:**
> Upgrades won't change your configurations.  They will simply replace the current software with its more recent versions.

You should always take security updates, especially if you have Internet-facing services like mail or HTTP.  One way to limit the upgrades to just security ones is to comment out all the lines in /etc/apt/sources.list with the exceptions of the entries that point to security.ubuntu.com.  Then run "sudo apt-get update; sudo apt-get upgrade".

Yep. I have my server set to install security updates automatically via the unattended-upgrades package. I still have to make sure it is ok after rebooting into a new kernel as most of the time DKMS screws up the install of a third-party module, and I have to remake it.

> Another approach is to run a parallel server, perhaps in a VirtualBox VM on your desktop.  Configure the VM to be the same as your actual server.  The simplest method to do this is to install 12.04 into the VM, then use rsync to make the VM copy a clone of the actual one.  Then run the updates on the VM server and see if they cause any problems.  If not, then you can run them on the real server as well.

I was doing that but decided it was easier to just do the updates and fix anything that breaks because I could not replicate the hardware RAID card I have in the server itself inside the VM. So far I have not run into many problems but the number one problem so far is the building of the raid card's module via DKMS, which somehow doesn't do it right with the newer 3.2.x kernels.

> **Jorel said:**
> what i usually do is im trying it 1st at my ubuntu 12.04 desktop before deploying it in the 12.04 server... although desktop and server are way different, i still think that the effect are somehow the same. (and hope what i thought was right)

Updating is pretty much the same between the two. The server version has less packages to update usually, but that might not be the case all the time. There are people who install a GUI on top of the server edition, when they would be better off just installing the desktop version and then installing the services they want on it afterwords.

---

### Post by Jorel on 2012-10-04
> **SeijiSensei said:**
> Upgrades won't change your configurations.  They will simply replace the current software with its more recent versions.

You should always take security updates, especially if you have Internet-facing services like mail or HTTP.  One way to limit the upgrades to just security ones is to comment out all the lines in /etc/apt/sources.list with the exceptions of the entries that point to security.ubuntu.com.  Then run "sudo apt-get update; sudo apt-get upgrade".its a relief to hear this one, i will definitely do this.. 

> **CharlesA said:**
> Yep. I have my server set to install security updates automatically via the unattended-upgrades package. I still have to make sure it is ok after rebooting into a new kernel as most of the time DKMS screws up the install of a third-party module, and I have to remake it. this is what im worrying about, im still a newbie on this environment so im a bit cautious on everything especially on the kernels.

> 
Updating is pretty much the same between the two. The server version has less packages to update usually, but that might not be the case all the time. There are people who install a GUI on top of the server edition, when they would be better off just installing the desktop version and then installing the services they want on it afterwords. well this one really works for me, as like im building a "Practice Desktop" to act as a Server then once im satisfied with the results then i will deploy it to the Server...

thanks for the suggestions guys...

---

### Post by CharlesA on 2012-10-04
> **Jorel said:**
> this is what im worrying about, im still a newbie on this environment so im a bit cautious on everything especially on the kernels.

It is likely happening to me because it is having issues creating a new module for that device. The virtualbox modules build fine on the same box.

---

### Post by LHammonds on 2012-10-04
> **Jorel said:**
> this is what im worrying about, im still a newbie on this environment so im a bit cautious on everything especially on the kernels.
Then I suggest you review your backup process to ease the pain.  Restore a backup inside a VM as if you were trying to restore to a new machine and see if you can the server up-and-running.

This will verify your backup procedure / documentation.

If you cannot do this, it is a perfect time to update/create an effective backup/restore procedure.

Once you know that you can recover from a disaster, you will feel much better about the maintenance of your server(s).

I configured my servers to use LVM, have a bit of unallocated space in the LVM for snapshots and use a combination of rsync and FSArchiver to get a good backup of my /boot and LVM partitions.  I also have my restore process tested and documented (check my sig for how to install an Ubuntu server for details)

LHammonds

---

### Post by Jorel on 2012-10-10
i see then.. 

anyway thank you guys for the help, this thread somehow enlightened me on my doubts on the server staying up... so probably my next step is to secure the HDD performance...

Thanks

---

