---
title: "Hard Drive Failure"
date: 2010-03-29
forum: Server Platforms
---

### Post by expatCM on 2010-03-29
My server just crashed.  The main hard drive is trash.  Sadly it was a complete surprise.

On the desktop versions there is the Disk Utility that monitors all drives and tells you in no uncertain terms if any drive is on the way out.  It works very well.  

Is there anything similar for the server platform so that a client machine gets a warning of a drive failure on the server?

---

### Post by the yawner on 2010-03-29
It's a bit of an advanced topic for me, but do try to check out for smartmontools.

---

### Post by Grenage on 2010-03-29
SMART is handy, but don't stake anything important on it.  I'm probably telling you how to suck eggs here, but still.

While SMART can tell you if the drive isn't operating within the parameters it was configured with, it can't predict a random hardware failure; that's what RAID arrays and backups are for.

---

### Post by expatCM on 2010-03-29
been looking at the smartmontools pages.  Cannot figure this out .....  is this to run on a server and remotely monitor from a client or does it send out warning messages or is it for use only on the server and you need to read the log files ... 

I need to put something in place though, too much pain in loss of the o/s and if I get some idea of fun things about to happen then at least I do some preparation........

---

### Post by fang0654 on 2010-03-29
For the actual monitoring, you can use a tool like nagios to monitor various pieces of hardware and let you know when something is going on.

I have it set up monitoring the RAID status on all of my servers, so I know immediately when a RAID fails, and I need to replace a hard drive.  

If you are running a production server, though, you have to have some kind of redundancy.  At the very least, set up a software RAID 1 to have a mirror.  That way, if one drive dies, you don't lose any data.

---

### Post by expatCM on 2010-03-29
What I am doing is running a home network.  The server is mainly to run squid since we have quite poor Internet and squid seems to help with the load.  The server also runs the printers .....  and a few other tasks such as client data backup ...

There are only two hdd's, one for the o/s and the other for data.  The one with the o/s just evaporated. 

So there is no raid, life is kind of simple there. 

Nagios ....  well ...  after digging a bit this does sound quite interesting.  I was very hesitant when I saw the home page though and then realized that it was my BAD Internet connection that was giving me only a partial page, when it eventually loaded it looked professional.
[http://www.nagios.org/](http://www.nagios.org/)

---

### Post by Grenage on 2010-03-29
Nagios is excellent, we use it here.  I actually just finished building a temperature array for it!

---

### Post by fang0654 on 2010-03-29
Good that you didn't lose the data!  

You would be better off putting the data and OS on the same physical drive (on separate partitions) and mirroring the two drives.  You can pick up new drives for very little cash, and the security is worth it.  If not, it changes from a question of if your server will go down to when it will go down.

---

### Post by lavinog on 2010-03-29
smartmontools can be configured to send you an email if it detects a problem, but as mentioned before, SMART is not really reliable in predicting hd failure.

Have a good backup plan.  A redundant backup plan too (I learned this the hard way when I lost my backup)

Assess the value of your data:  Many companies are offering free 2g of cloud storage (ubuntuone, dropbox, spideroak...)  Determine what data is the most important that can fit within the 2g limit.

Harddrives are cheap.  Replace any drive that is out of waranty.  Purchase drives based on their use: a backup drive doesn't need to be 10000rpm.

Invest in good power supplies.  SMART will not warn you when your power supply will toast your drive.  Backup batteries are also a good investment.  Active PFC power supplies practically pay for themselves when used in computers that are always on. Cheap passive pfc power supplies can typically consume 20W more than active pfc ones.

---

### Post by expatCM on 2010-03-29
> Replace any drive that is out of waranty. 

Well, that seems to make sense but ...  the drive that failed will be returned under warranty today....  :(

Warranty on hard drives is five years and I get the idea that it is not quite replace out of warranty but more upgrade.

---

### Post by lavinog on 2010-03-29
> **expatCM said:**
> 
Warranty on hard drives is five years and I get the idea that it is not quite replace out of warranty but more upgrade.

Depends on the purpose, not all computers need terrabytes of storage.
Some of the computers in my house have 60g drives.

Also some manufacturers are switching to 3 year warranties now.

---

### Post by expatCM on 2010-03-29
Three years .....  oh dear ....

I just completed the RMA to Seagate.  I see that they have modified their return process to ask that you enter the SeaTools exit code as part of the RMA.  Sadly SeaTools is a Windows program.  Perhaps Seagate will offer a Linux version in the future.  They will however let you enter a code saying that you do not have a machine to run SeaTools but I wonder how long that will be the case.

---

### Post by lavinog on 2010-03-29
> **expatCM said:**
> Three years .....  oh dear ....

I just completed the RMA to Seagate.  I see that they have modified their return process to ask that you enter the SeaTools exit code as part of the RMA.  Sadly SeaTools is a Windows program.  Perhaps Seagate will offer a Linux version in the future.  They will however let you enter a code saying that you do not have a machine to run SeaTools but I wonder how long that will be the case.

They should have a bootable cd.
I had to do that with my seagate drive.
EDIT: Download seatools for dos...its a bootable cd image: [http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=SeaTools&vgnextoid=720bd20cacdec010VgnVCM100000dd04090aRCRD](http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=SeaTools&vgnextoid=720bd20cacdec010VgnVCM100000dd04090aRCRD)




I am assuming that you pulled it out of the case.
What model is it and what firmware is listed.
The reason why I asked is that there was a recent issue (starting last year) with some seagate drives failing because of a faulty firmware.  The drives just fail to start when booted.

here is some info on the problem: [http://www.msfn.org/board/topic/128807-the-solution-for-seagate-720011-hdds/?](http://www.msfn.org/board/topic/128807-the-solution-for-seagate-720011-hdds/?)
Don't try to do the procedure unless you are really good with electrical components though.

---

### Post by expatCM on 2010-03-29
Just got back from the post office so I do not know what the firmware is.  Seagate should sort it out now ...........

I must say that is a very amazing msfn.org link ....  a huge amount of information with links, pictures and ....  well solutions ...

---

### Post by lavinog on 2010-03-29
> **expatCM said:**
> Just got back from the post office so I do not know what the firmware is.  Seagate should sort it out now ...........

I must say that is a very amazing msfn.org link ....  a huge amount of information with links, pictures and ....  well solutions ...

Yeah...it helped me out a bunch because I wound up in a position to do that procedure...fun stuff.

---

### Post by Grenage on 2010-03-30
> Sadly SeaTools is a Windows program

I always just select the option for a drive with no code (it's dead, Jim); I've returned hundreds of drives, and they've never taken issue with it.

Despite the the firmware issues on a couple of models last year, Seagate are still my manufacturer of choice; the drive quality and ease of return is excellent.

Mechanical drives can go wrong at any time, and in my experience, a brand new drive has about the same chance of failing as a drive on its 10th birthday.

---

### Post by lavinog on 2010-03-30
> **Grenage said:**
> 
Despite the the firmware issues on a couple of models last year, Seagate are still my manufacturer of choice; the drive quality and ease of return is excellent.
They at least had a solution for users to recover their data.  If you didn't want to do it yourself, they recognized that the issue was their problem and offered free recovery services.  I have to give them +10 for the way they handled the situation. Some users thought they took too long to respond, but given the large number of failures, it was understandable.

> 
Mechanical drives can go wrong at any time, and in my experience, a brand new drive has about the same chance of failing as a drive on its 10th birthday.
I think older drives were more rugged, and could handle more torture.
I had a couple of drives from 1998 that I finally retired. Not because they died, but because they were only 10g.  They are pretty noisy when idle compared to newer drives.  One of them didn't even support SMART.

---

### Post by Grenage on 2010-03-30
That's very true.  We have one last Compaq server that was bought in tha mid-late 90s.  None of the drives on them failed, but their capacity and speed makes them less desirable.

The fact that a new server pays for itself within a year, when looking at power savings, also helps!

---

### Post by jrssystemsnet on 2010-03-30
> **Grenage said:**
> The fact that a new server pays for itself within a year, when looking at power savings, also helps!

You either buy way cheaper servers than I do, or spend far, far more per KWH.

---

### Post by lavinog on 2010-03-30
> **jrssystemsnet said:**
> You either buy way cheaper servers than I do, or spend far, far more per KWH.

Have you measured energy consumption differences?
You can also consider the energy saved from the reduced cooling needed.

---

### Post by jrssystemsnet on 2010-03-30
> **lavinog said:**
> Have you measured energy consumption differences?
You can also consider the energy saved from the reduced cooling needed.The *entire* power bill for my 2,000 sq ft home + office, complete with several servers and workstations, a PS3, a roommate, a wife, and washing two loads of laundry a day just about adds up to the cost of a server, over the course of a year.

No, the cost difference in power consumption on a single server for a single year is not even going to come *close* to covering its cost. :)

---

### Post by Grenage on 2010-03-30
Really old servers cost, literally, hundreds of pounds in electricity - per year.  Spending about four grand on a decent server, it covers itself very quickly.  On unimportant, low-spec servers, you can spend as little as one grand (that includes redundancy and RAID) and recover the costs in no time at all.

---

