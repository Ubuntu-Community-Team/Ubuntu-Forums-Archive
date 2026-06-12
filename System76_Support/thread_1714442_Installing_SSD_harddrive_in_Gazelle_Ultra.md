---
title: "Installing SSD harddrive in Gazelle Ultra?"
date: 2011-03-25
forum: System76 Support
---

### Post by gknaddison on 2011-03-25
Hello,

I've got a Gazelle Ultra that appears to be a Gazu1 vintage machine though the lid looks different (centered silver ubuntu circle logo instead of the off-center red/yellow logo).

I've noticed recently that I'm spending a lot of time with the CPU waiting on disk IO. I started a terminal with "vmstat 5" running in the background and whenever I sense a slowdown I look at the output and see a %wait times of 40%, 60% etc.

So, I'm thinking of replacing the current hard drive with an SSD.

Has anyone done this? Were the benefits worth it? Is there a specific SSD model you suggest?

According to lspci the current drive is a SATA drive, but I'm not sure if it's SATA I or SATA II. 

The relevant line is:

```
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)

```

---

### Post by isantop on 2011-03-25
By far, I think the best brand of SSD will probably Intel. We sell and test with them, and we've found other brands to be a lot less reliable.

Your GazU1 should support SATA II.

---

### Post by gknaddison on 2011-04-12
I just got it installed and the difference is absolutely wonderful! I guess there's no surprise there.

The  drive I got was "Intel X25M 120 GB Solid State Drive with Internal SATA  and Power Cables MLC SSDSA2MH120G2K5 Intel." I looked at my drive usage  (originally I had a 320GB drive) and only really needed about 60GB of  space right now so this gives me some room to grow before I have to  start being judicious about my drive use. It was handy to have the cables to install it in a desktop. I popped out the original drive, used the cables/adapter tray to put it in an old desktop, installed the new drive, put Ubuntu on the new drive, and then did a big rsync to pull over my original home directory and configurations from /etc/ (e.g. mysql, php, and apache configuration files)

Bootup and shutdown  times are basically half of what they used to be. The BIOS is one of the  slowest parts of bootup. I now send it to hibernate a lot more instead  of standby because coming out of hibernate is about as fast as coming  out of standby used to be.

I do a lot of work with large  databases and large website codebases (e.g. 270MB of php code in one  site I'm working on) so having a fast disk means that my IDE can read  that more quickly. This is definitely a worthwhile upgrade to keep my  Gazelle fast enough for me to use it as my main working machine for  another year or two.

---

