---
title: "Need help picking a UPS"
date: 2009-07-01
forum: The Cafe
---

### Post by Excedio on 2009-07-01
Hey All..I need help finding a UPS with an Auto-Shutdown feature. I know there are some out there, but I have no clue if they are compatible with Linux. Here is what I have found so far:

[ 						Belkin Home Office 375VA/200W UPS w/Auto Shutdown Software]("http://www.geeks.com/details.asp?invtid=F6H375-USB-DT&cat=UPS")

I also posted on [someone elses thread]("http://ubuntuforums.org/showthread.php?p=7547224#post7547224") that did not get any responses, however he did find a solution on his own. I am hoping that in the Cafe this may get some more attention, and to find out if there are other options than what the other person is using. Also, he got his working in Jaunty, I am running Intrepid, will there be a difference?

Any help?

---

### Post by MikeTheC on 2009-07-01
While I can't speak to Linux, my own experience with battery backups is that the shutdown function is totally based on the software used on the PC side of things. With Windows it can contend with different categories of battery backup hardware, and Mac OS X generally works with anything that communicates using one of the standard protocols. In fact, Mac OS X sees it as a kind of battery system and will then report charge levels, switch around operational modes, etc.

Does anyone else here know if Lixus handles it well?

---

### Post by cariboo on 2009-07-01
I have both a Belkin, and an APC. I gave up trying to get the Belkin to work with my system, So far I've been using the computer when the power went I and I just shut the system down normally.

The APC was so easy to setup, all I did was install acpupsd from the repositories, change two lines in the configuration file and it was done. Apcupsd is a command line utility, but apcaccess gives you all the information you need.

```

jim@willy:~$ sudo apcaccess
APC      : 001,040,1040
DATE     : Wed Jul 01 17:31:11 PDT 2009
HOSTNAME : willy
RELEASE  : 3.14.4
VERSION  : 3.14.4 (18 May 2008) debian
UPSNAME  : willy
CABLE    : Custom Cable Smart
MODEL    : Back-UPS XS  900 
UPSMODE  : Stand Alone
STARTTIME: Thu Apr 30 16:48:45 PDT 2009
STATUS   : ONLINE 
LINEV    : 124.0 Volts
LOADPCT  :  27.0 Percent Load Capacity
BCHARGE  : 100.0 Percent
TIMELEFT :  32.4 Minutes
MBATTCHG : 5 Percent
MINTIMEL : 3 Minutes
MAXTIME  : 0 Seconds
SENSE    : Medium
LOTRANS  : 088.0 Volts
HITRANS  : 139.0 Volts
ALARMDEL : Always
BATTV    : 26.9 Volts
LASTXFER : Low line voltage
NUMXFERS : 14
XONBATT  : Tue Jun 23 14:00:09 PDT 2009
TONBATT  : 0 seconds
CUMONBATT: 125 seconds
XOFFBATT : Tue Jun 23 14:01:42 PDT 2009
LASTSTEST: Wed Jun 10 14:32:47 PDT 2009
SELFTEST : NO
STATFLAG : 0x07000008 Status Flag
MANDATE  : 2008-04-25
SERIALNO : JB0817017004  
BATTDATE : 2099-00-38
NOMINV   : 120 Volts
NOMBATTV :  24.0 Volts
NOMPOWER : 540 Watts
FIRMWARE : 830.E6 .D USB FW:E6
APCMODEL : Back-UPS XS  900 
END APC  : Wed Jul 01 17:31:19 PDT 2009
```

---

### Post by Excedio on 2009-07-02
Thanks for the responses, I really appreciate it. Has anyone heard of CyberPower? They make surge protectors and UPS systems. They have some really good reviews on [Newegg.com]("http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16842102032"). Best of all,  they also seem to provide Linux support with their Auto-Shutdown feature. [Check it out.]("http://www.cyberpowersystems.com/products/management-software/ppl.html")

Here is the unit I'm thinking about getting:
[CP500HG]("http://www.cyberpowersystems.com/products/ups-systems/browse-by-category/soho-ups/cp500hg.html?selectedTabId=overview&imageI=#tab-box")

---

### Post by nmccrina on 2009-07-02
I saw this thread and couldn't help but think "What can brown do for you?". Which actually wouldn't be a bad Ubuntu slogan, now that I think about it. :lolflag: 

After figuring out what 'UPS' stood for, I then realized that I don't have anything relevant to contribute to this thread. :( But at least I know what a UPS is now!

---

### Post by Excedio on 2009-07-02
> **cariboo907 said:**
> UPSNAME  : willy


By the way, great name for your UPS. :lolflag:

---

### Post by Excedio on 2009-07-02
> **nmccrina said:**
> I saw this thread and couldn't help but think "What can brown do for you?". Which actually wouldn't be a bad Ubuntu slogan, now that I think about it. :lolflag: 

After figuring out what 'UPS' stood for, I then realized that I don't have anything relevant to contribute to this thread. :( But at least I know what a UPS is now!


I'm glad the thread helped you out. :-)

---

### Post by buttertoad on 2009-07-07
I just installed a CyberPower UPS the other day and I love it.
I got the [CP1500]("http://www.cyberpowersystems.com/products/ups-systems/browse-by-category/intelligent-lcd-ups/CP1500AVRLCD.html"). It was very easy to setup, I just downloaded PowerPanel for Linux from the CyberPower website, they even have an .deb package, and that was it. PowerPanel is a command line tool that will give you options based on power failure and when the battery reaches critical, it will even run scripts that you provide after each event. 

Just make sure the model you get is compatible with PowerPanel because I read that not all of their models are.

---

### Post by Excedio on 2009-07-07
> **buttertoad said:**
> I just installed a CyberPower UPS the other day and I love it.
I got the [CP1500]("http://www.cyberpowersystems.com/products/ups-systems/browse-by-category/intelligent-lcd-ups/CP1500AVRLCD.html"). It was very easy to setup, I just downloaded PowerPanel for Linux from the CyberPower website, they even have an .deb package, and that was it. PowerPanel is a command line tool that will give you options based on power failure and when the battery reaches critical, it will even run scripts that you provide after each event. 

Just make sure the model you get is compatible with PowerPanel because I read that not all of their models are.


Awesome. Glad to hear that the CyberPower has potential to work well.

---

### Post by Lateforgym on 2009-07-08
[edited] my experience is Windows environment

---

