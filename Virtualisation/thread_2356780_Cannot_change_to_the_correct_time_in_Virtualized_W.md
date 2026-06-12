---
title: "Cannot change to the correct time in Virtualized Windows XP"
date: 2017-03-27
forum: Virtualisation
---

### Post by AbleTassie on 2017-03-27
I am running Windows XP Professional as a virtual machine in Virtualbox (Graphical User Interface Version 5.0.32_Ubuntu r112930) with Lubuntu 16.04.2 as the host.[SIZE=2] [FONT=arial][COLOR=black][COLOR=black][FONT=&quot][FONT=Arial, Helvetica, sans-serif]I cannot set the time in Windows XP to the correct time, it is still on Pacific Standard Time, _**not**_ Daylight Savings Time. So it is an hour behind the correct time. 

When I try to set it to the correct time using the Windows Date and Time Properties Dialogue Box (see screenshot), the time change only lasts a few seconds. When I try to set the time by sychronizing with an internet time server, I get an error message.[/FONT][/FONT][/COLOR][/COLOR][/FONT][/SIZE]

I think this  incorrect time may be causing me to be unable to download audiobooks through my local public library using the Overdrive App. The Overdrive App is installed in the Windows virtual machine, Overdrive does not run on Linux. 

Is the inability to set the correct time due to the virtualization? Can the time be corrected?

Thanks,

A.

[ATTACH=CONFIG]274314[/ATTACH]

---

### Post by ajgreeny on 2017-03-27
From the dialogue box you show in your screenshot go to the Time zone tab and there you should see "Automatically adjust clock for daylight saving changes".
That should do it; it does in my VM of XP.

I am uncertain about the correct choice to make at installation when choosing Local time or UTF, but I think I chose whatever is the default when I installed the VM; it is too long ago now for me to remember.

PS:
For security's sake make sure you keep a clean snapshot of your XP so that should the running version be compromised as a result of XP's lack of support, you can quickly get back to a clean version.

---

### Post by AbleTassie on 2017-03-27
> **ajgreeny said:**
> From the dialogue box you show in your screenshot go to the Time zone tab and there you should see "Automatically adjust clock for daylight saving changes".
That should do it; it does in my VM of XP.

I am uncertain about the correct choice to make at installation when choosing Local time or UTF, but I think I chose whatever is the default when I installed the VM; it is too long ago now for me to remember.

PS:
For security's sake make sure you keep a clean snapshot of your XP so that should the running version be compromised as a result of XP's lack of support, you can quickly get back to a clean version.

Thanks AJ,

Unfortunately I have the "Automatically adjust clock for daylight saving changes" box checked. It was already checked when I took the last screenshot. So I am not sure what to do. 

Regarding security I do have a clean snapshot of the machine in case of problems.

A.

---

### Post by AbleTassie on 2017-03-29
I figured out that this is because there was a lack of an official Microsoft update to Windows that adjusted for the changes in Daylight savings time laws.    See [https://support.microsoft.com/en-us/help/955839](https://support.microsoft.com/en-us/help/955839) and Update for Windows XP (KB955839). I downloaded and installed the patch and that corrected the problem, but it did not correct the problem I am having with Overdrive.

So this is a problem with Windows, not virtualization.

Thanks,

A.

---

