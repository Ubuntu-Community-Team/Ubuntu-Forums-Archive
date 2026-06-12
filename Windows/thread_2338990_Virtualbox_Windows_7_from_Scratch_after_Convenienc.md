---
title: "Virtualbox Windows 7 from Scratch after Convenience rollup was released"
date: 2016-10-03
forum: Windows
---

### Post by ipguru99 on 2016-10-03
Hello all,

I recently had a customer want a laptop completely erased and not have an image used to put Windows back on. Since there are approximately a million updates (yes, I know there aren't a million, just feels that way), I was not excited, as I knew this meant hours of finding something else to do, but also having to babysit a Windows installation. 

In the past few weeks (as of September 2016), I had done this same thing on my Ubuntu 16.04 desktop and 14.04 laptop (inside Virtualbox), so I thought I would put it all down here (obviously there are differences in those versions of Virtualbox, but this proves Virtualbox was not the problem)

Turn Windows Update off at install

Install [Windows 7 with SP1]("https://www.microsoft.com/en-us/software-download/windows7") already in it (requires a valid key).. or just install fresh Windows 7, manually install SP1 (say no if you reboot after the first update into a custom window that says you should upgrade to windows 10 or install win7 sp1)

[April 2015 Service Stacking Update]("https://support.microsoft.com/en-us/kb/3020369") (it is ~9MB) (Rollup will not apply unless this is installed)

Windows 7 SP1 (KB976932)

[Windows]("http://download.windowsupdate.com/d/msdownload/update/software/updt/2016/05/windows6.1-kb3125574-v4-x64_2dafb1d203c8964239af3048b5dd4b1264cd93b9.msu") 7 SP1 Convenience Rollup

[Windows]("https://www.microsoft.com/EN-US/DOWNLOAD/confirmation.aspx?id=30653") 7 .NET Framework 4.5 Full

Turn Auto updates back on

After waiting 24 hours, I had given up (I tried to run the Windows Update Diagnostics cab file and it just sat there spinning). 

I set the date to three days in advance and waited an hour (I was also using some Windows only software that had a date issue, so I thought I would test it out) <--Not a joke.. I think this is what did the trick... 

I went to shut down the machine and there were 104 updates waiting and then were installed. 

I have used Ubuntu since 5.04.. I can't imagine having to use Windows on a daily basis (or have Microsoft so obviously want you to upgrade to Windows 10). Thanks Ubuntu!!

---

### Post by howefield on 2016-10-04
Thanks for posting, not really an Ubuntu thread so moved to the "Windows" sub forum.

---

