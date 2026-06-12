---
title: "After updates login now crashes"
date: 2015-11-23
forum: Ubuntu Development Version
---

### Post by Doug S on 2015-11-23
I have dual boot on my main Ubuntu test server. Yesterday, I did updates on the 16.04 version. However, I only did the updates as a tangent task while really wanting to update grub on the 16.04 version so that I could then gain access to a new kernel I had installed on the 14.04.3 partition, so I didn't actually boot into 16.04 again until today (which again I was really only wanting to update grub so that I could boot the 14.04.3 system into yet another new kernel I am wanting to try).

Now when I try to login (either on a local terminal or via SSH), there is some sort of error that flashes on the screen, too fast to read, and I am returned to the login screen.

If I boot the system into 14.04.3, then I can mount the disk partition with 16.04 on it and look at files. The information seems limited, but I did find a crash dump file:```
ProblemType: Crash
Architecture: amd64
Date: Mon Nov 23 08:31:54 2015
DistroRelease: Ubuntu 16.04
ExecutablePath: /bin/login
ExecutableTimestamp: 1437457457
ProcCmdline: /bin/login --
ProcCwd: /
ProcEnviron:
...
```I am not sure how to get my 16.04 system working again. Any suggestions?
Anybody else seeing this issue?

Meanwhile, I will try to figure out how to get the first grub that comes up to be the 14.03.3 one, with a secondary being the 16.04 one. (I have figured this out before, I just don't recall how at the moment.)

---

### Post by mc4man on 2015-11-23
> **Doug S said:**
> 

Meanwhile, I will try to figure out how to get the first grub that comes up to be the 14.03.3 one, with a secondary being the 16.04 one. (I have figured this out before, I just don't recall how at the moment.)
The is a reconfigure command you can run on grub from the install you want to be first listed.
Here I don't bother remembering the com., I just boot to install I want first & re-install the appropriate grub package
(in my case, grub-efi-amd64

---

### Post by QDR06VV9 on 2015-11-23
I have had good luck with Boot-Repair, But perhaps my Bios are not as complicated as some others.
Good Luck.
Kind Regards

---

### Post by matt_symes on 2015-11-23
Not seeing this crash after installing the daily iso.

I assume you can't get to a root shell from grub ? If not then your best bet maybe a chroot i suspect.

---

### Post by Doug S on 2015-11-24
Thanks for all the replies.

I think I am going down a rat-hole here and might have to start from scratch on my second HDD (the one with 16.04 on it).

I did finally manage to get get the 14.04.3 grub to update and can now at least access the test kernels I want to try. I can not seem to get my BOIS boot order to boot from the 14.04.3 HDD first, it always goes to the 16.04 HDD first.

My procedure (hokey):
1.) boot to 14.04.3, but recovery mode.
2.) update grub
3.) boot to 16.04, but recovery mode.
4.) update grub.
5.) re-boot and select the 14.04.3 advanced options, and now the new kernels appear and I can select the one I want.

I have made no progress on the 16.04 login crash issue. I'll get back to that later.

---

### Post by Doug S on 2015-12-04
> **Doug S said:**
> I think I am going down a rat-hole here and might have to start from scratch on my second HDD (the one with 16.04 on it).
I have made no progress on the 16.04 login crash issue. I'll get back to that later.Update: I gave up and started from scratch on the second HDD.
Now I am stuck at the select and install software step. It says there is a problem, and I can not seem to get past it. I have tried a few times now. I have also double checked the md5sum of the USB drive I am using for the Ubuntu 16.04 64 bit server daily iso I am using.

EDIT 1: I went back to the iso of 2015.10.30, which I know worked. It worked this time also. ... Oh ... I see there is already [a bug report]("https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/1517746").

EDIT 2: ... And then after doing updates, the login loop returned.

---

### Post by syntaxerror74 on 2015-12-05
> **Doug S said:**
> 
EDIT 2: ... And then after doing updates, the login loop returned.

There are many possible reasons for it: some more significant error in your .profile, and soon you may be finding yourself in a fix!

Other than that...I've once managed to read the flashy message by running into **recovery mode**. Give that GRUB option another try perhaps.
Either you get warped into that (insanely stupid) emergency mode (then use *sysctl default* after root login), or you will get the ncurses (?) menu as usual.
With the latter, try to login as root, and then...
- either start your login GUI manually (I'm on Lubuntu with its LightDM, so you'll have to call the line accordingly)
- or just type *startx *and watch what'll happen on screen

Yet another possibility: 
If your user login fails, what about logging in as **root** via terminal after normal boot? (Ctrl-Alt-F1)
If this works, your .profile in /home/yourusername is at fault.

---

### Post by Doug S on 2015-12-05
Thanks for your posting.

> **syntaxerror74 said:**
> - either start your login GUI manuallyThis is a server installation, no GUI.
As far as I can determine, this issue is with the current 16.04 server edition.
I looked back as far as I could on the QA tracker, and nobody has succeeded with any recent daily 16.04 server installation (not that there is much data, really).

---

### Post by syntaxerror74 on 2015-12-08
Rats!

This is somewhat embarrassing...now that I see the *server* tag, everything falls into place...Presumably I wouldn't have posted, had I spotted the 'server' bit a little earlier.

---

### Post by Doug S on 2015-12-08
> **syntaxerror74 said:**
> Rats!

This is somewhat embarrassing...now that I see the *server* tag, everything falls into place...Presumably I wouldn't have posted, had I spotted the 'server' bit a little earlier.Truth be known, I only added the "server"tag after your posting. Thanks for chiming in anyhow.

Someone did complete a minimal server install a couple of days ago.

---

### Post by Cavsfan on 2015-12-08
I'm not sure if this is relevant but a while back several people beat this into me: :lol: And I'm glad they did. :lol:

Have your grub on one system and on the others put the grub on the PBR instead of the MBR.
You may already know this idk. When I installed 16.04 I installed it to the PBR (sda5) instead of the MBR (sda).

I have my grub on Arch controlling everything and don't have to worry about another system updating grub and then installing it there when I want the grub on Arch to be in control.

I have a custom grub setup on Arch and decided to customize grub on Xenial since it took soooo long to do an update-grub.
Maybe it's just os-prober finding Windows 10 that causes the delay but anyway I customized it then when I made sure everything booted like I wanted, 
I installed grub back on Arch **sudo grub-install /dev/sda** and on Xenial back on the PBR sda5.

Although it fought with me and gave me an error so I had to add the --force flag - **sudo grub-install --force /dev/sda5** if my memory serves me correctly.
It'll say something about using blacklists, and warning you but in the end it will say successful.

If this is not feasable then leave it as is, but if it is it works well.

---

### Post by Doug S on 2015-12-08
> **Cavsfan said:**
> I'm not sure if this is relevant but a while back several people beat this into me: :lol: And I'm glad they did. :lol:

Have your grub on one system and on the others put the grub on the PBR instead of the MBR.
You may already know this idk. When I installed 16.04 I installed it to the PBR (sda5) instead of the MBR (sda)....O.K. thanks for your post.
My grub issues have returned. I do not know how I fixed them, but they came back. I guess I better study all the suggestions and figure it out.

I tried the server 64 bit daily for today, and it still fails at the same place.

> **matt_symes said:**
> Not seeing this crash after installing the daily iso.Matt: was that the server edition?

---

### Post by Cavsfan on 2015-12-08
Glad I could help but, it sounds like a matter of do you want to maintain more than one grub and have to deal with this every time one of them updates to a new version?

Developmental versions update quite a bit. Stable releases, not so much on the grub updates.

---

### Post by Doug S on 2015-12-09
The daily **server** 64 bit iso of 2015.12.09.2 now completes the installation. However, the login loop still prevents actually using the system.
I have only done a VM install so far. I might try a physical install to a spare partition later.

EDIT: It is specifically selecting "Samba Server" at the select software step that will subsequently cause the login loop issue. Other installs, without "Samba Server", 3 others so far, have worked fine.

EDIT 2: I believe this is the [appropriate bug report]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1515207")

---

### Post by Doug S on 2015-12-11
> **Doug S said:**
> I have only done a VM install so far. I might try a physical install to a spare partition later.The saga continues...
Installation on real hardware, instead of a VM, works, but there is no network afterwards. [bug report]("https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/1525420")

---

### Post by cariboo on 2015-12-11
I ran into a login loop problem. after installing libpam-smbpass while setting up a shared directory on two Xenial desktop installations. Purging the package fixed the problem.

---

### Post by Doug S on 2015-12-11
> **cariboo said:**
> I ran into a login loop problem. after installing libpam-smbpass while setting up a shared directory on two Xenial desktop installations. Purging the package fixed the problem.Yes, thanks. The bug report has an entry saying the same thing. The problem is two fold: First, it is the testing tracker test case that fails, and that is all I was trying; I cann't get any access at all to then delete libpam-smbpass.

---

### Post by cariboo on 2015-12-11
I had to go into recovery mode and mount /root in rw mode in order to remove the package. Selecting networking from the menu is the easiest way

---

### Post by Doug S on 2015-12-12
> **cariboo said:**
> I had to go into recovery mode and mount /root in rw mode in order to remove the package. Selecting networking from the menu is the easiest wayO.K. thanks. I did that, and confirm that deleting the libpam-smbpass package thereafter allows login (which is no surprise, just confirming is all).

Still stuck with [no network]("https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/1525420"). This one seems to be a hardware dependent issue, as someone else ran the test case yesterday and it passed, and I can also run it fine on a VM.

As for the grub mess ups: Thanks for all the suggestions. I now (finally, after a couple of years of messing up) do this stuff without messing up my main 14.04.3 grub.

---

### Post by Doug S on 2015-12-13
> **Doug S said:**
> As for the grub mess ups: Thanks for all the suggestions. I now (finally, after a couple of years of messing up) do this stuff without messing up my main 14.04.3 grub.I spoke too soon. I still have issues, and they might be related to my attempts to leave my 14.04.3 boot clean, with it having the master grub.

I got suspicious after a sanity check test where I installed 15.10 64 bit server and ended up with the same mess after re-boot after installation.

After installing the daily 64 bit server ISO about 10 times today, it finally installed O.K., with network available after re-boot after installation.

---

### Post by Doug S on 2015-12-17
> **Doug S said:**
> The daily **server** 64 bit iso of 2015.12.09.2 now completes the installation.The inability to complete the installation has returned as of the server 64 bit daily of 2015.12.17. The daily of 2015.12.16 was fine (for completing installation, that is), but still had the login issue if samba was selected, even thou the bug report was set to "fix released".

---

### Post by Doug S on 2015-12-18
O.K. so today everything is O.K. The installation does not get stuck, and when samba is selected one can login after the post install re-boot.

My grub issues continue, but that is a different story, and I'll start a new thread for that if needed. Setting this one to solved.

---

