---
title: "Time sync without hardware at GMT"
date: 2010-10-09
forum: System76 Support
---

### Post by andrewdied on 2010-10-09
I'm trying to find a way to keep ubuntu from changing my hardware clock to GMT when I set the time.  Specifically linux likes to keep the hardware clock on GMT and then apply the time zone offset (say, MST) on top of it. 

The issue I have is my System76 laptop dual boots Windows XP.  XP needs the hardware clock to be set to local time and can't really play the GMT/MST games that linux can.  Once upon a time in another distro I was able to specify it that the hardware clock should be on local time, too.

---

### Post by Dave_L on 2010-10-09
In my distro (not Ubuntu but a similar one), the hardware clock is set in the script /etc/init.d/hwclock.sh, using the command "hwclock". There are a couple of environment variables that determine whether the option --localtime or --utc is passed to the hwclock command.  The manual page for hwclock explains all the parameters.

---

### Post by HotShotDJ on 2010-10-09
Or, you could fix Windows: [http://weblogs.asp.net/dfindley/archive/2006/06/20/Set-hardware-clock-to-UTC-on-Windows-_2800_or-how-to-make-the-clock-work-on-a-Mac-Book-Pro_2900_.aspx](http://weblogs.asp.net/dfindley/archive/2006/06/20/Set-hardware-clock-to-UTC-on-Windows-_2800_or-how-to-make-the-clock-work-on-a-Mac-Book-Pro_2900_.aspx)

---

### Post by andrewdied on 2010-10-10
> **Dave_L said:**
> In my distro (not Ubuntu but a similar one), the hardware clock is set in the script /etc/init.d/hwclock.sh, using the command "hwclock". There are a couple of environment variables that determine whether the option --localtime or --utc is passed to the hwclock command.  The manual page for hwclock explains all the parameters.

An excellent lead.  In ubuntu the magic is in /etc/init/rcS.  There is a variable called "UTC" that is set to yes by default, and I set it to no.  When I rebooted into windows the time was the same.  Wunderbar.

I thought about the windows registry change, but since windows really isn't made to handle it, who knows what changes would cascade through.  Linux has a fine text file to change, and all the programs behave the way they're supposed to!  Thanks for all the help.

---

### Post by isantop on 2010-10-12
I've attached a .reg file. Simply download it in windows and double-click on it to apply the registry modifications automatically. 

Having the hardware clock on UTC is better for a few reasons. It will mean less modifications to the hardware time in the event of crossing a timezone border, or in the case of daylight savings time. Plus, most operating systems expect the time on the hardware clock to be set to UTC, and not all of them allow you to change it.

---

### Post by alphaamanitin on 2011-03-16
I would like some independent verification that the .zip file is fine before I use it.  No offense, but best to be safe online.

AlphaA

---

### Post by andrewdied on 2011-03-17
> **alphaamanitin said:**
> I would like some independent verification that the .zip file is fine before I use it.  No offense, but best to be safe online.

AlphaA

I fixed it on the linux side and didn't use the zip file.

---

### Post by alphaamanitin on 2011-03-17
I also fixed my problem on the linux side.

AlphaA

---

### Post by drewbenn on 2011-03-17
> **alphaamanitin said:**
> I would like some independent verification that the .zip file is fine before I use it.  No offense, but best to be safe online.

Here is what I did after I saved the file.  As you can see, it only contains a short text file; you could apply that registry change yourself if you wanted (I have no idea what it actually does, but I could make some educated guesses based on the replies in this thread).  Though I don't know why you would trust me over @isantop, the official System76 representative on this forum!

```
$ unzip Windows_Time_Fix.zip 
Archive:  Windows_Time_Fix.zip
  inflating: WindowsTimeFixUTC.reg   
$ cat WindowsTimeFixUTC.reg 
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\TimeZoneInformation]
     "RealTimeIsUniversal"=dword:00000001
$ 
```

---

### Post by isantop on 2011-03-17
That registry entry controls how Windows interprets the time from the system clock. If it's set to default, Windows assumes the clock is set to your local time. If it's set as in the patch, then it will assume it's set to UTC, which is default for most operating systems other than windows.

---

### Post by alphaamanitin on 2011-03-17
It is not a matter of trusting one person over another, more of a matter that the more people that look at something to tell me if a command could be harmful the more unlikely it is that if the command is harmful no one will mention it.  I didn't really want to download it and unzip it because, though I may be wrong, I thought it might be possible to get malware to run automatically on unzipping a file.  

I do know a wee bit (not wee bit as in actually lots) about the registry and that seems to make perfect sense to me.  I could do this manually actually, and I assume that if I look at the reg value in question it will currently have all zeros.  

Thanks guys.

AlphaA

---

