---
title: "Stuttering overall performance"
date: 2007-10-02
forum: Server Platforms
---

### Post by senorsalsa on 2007-10-02
Hi, I'm having trouble with my server's overall performance. It boots very slowly, hanging at the "Detecting hardware" stage. That's not the real problem, however. After everything is done loading and I can login and such, the system lags considerably. I often have to wait ~10 seconds just to log in, let alone actually try to do something. Just about everything is painfully slow. I also noticed that when transferring files to the server using proftpd the transfer operations constantly stutter. It transfers a few MB, pauses for about 500ms or so, and then resumes. The behavior is really strange, I've never seen anything like it before. 

I don't think it's a hardware limitation, because I recently had the newest version of IPCop loaded and these issues didn't turn up, including ftp transfers and logging in. At first I thought it might be an IDE driver issue, but hdparm returns a throughput of about 20mb/s, which seems about right. It's certainly not a load issue, as my load average is usually around 0.2. Free reports about 100mb of free memory, so that shouldn't be the problem either. All temps are reasonable as well.

The whole install is vanilla with the exception of proftpd and lvm2. I added those after the fact, but the login lag issue was present upon the first boot. 

I really don't know how else to approach this problem. Can anyone help me out? I'd be happy to spew whatever configuration information you desire.

General specs:
Ubuntu-server 7.10
linux-2.6.22-12-386

VIA C7 1Ghz
384MB PC133
SIS 5513 onboard IDE

---

### Post by peabody on 2007-10-02
There might be some network timeout issues going on here.  Check to make sure the ip of your server has a reverse dns name, has its loopback device setup properly, etc, etc.

---

### Post by senorsalsa on 2007-10-02
Wow, thanks for the super fast response. Would a network configuration error cause logging in to be slow? I'm talking about physical access to the machine. In any event, I'll check the network config.

---

### Post by peabody on 2007-10-02
> **senorsalsa said:**
> Wow, thanks for the super fast response. Would a network configuration error cause logging in to be slow? I'm talking about physical access to the machine. In any event, I'll check the network config.

Yes it could.  I experienced a bug once where it took over a minute for me to login because the loopback device was not configured correctly.  Some piece of software (I'll never know what) was trying to connect through the loopback with a large timeout, and with no loopback device configured I couldn't login until timeout ran out.

I administered a machine a very long time ago (1999) for a school that was being used for a UNIX class.  People who used net zero were complaining that it took forever to login to the machine.  I found out that netzero at the time, didn't have proper reverse dns for its ips.  Basically my server was trying to lookup the hostname of the connecting ip and wouldn't let them in until that timed out.

---

