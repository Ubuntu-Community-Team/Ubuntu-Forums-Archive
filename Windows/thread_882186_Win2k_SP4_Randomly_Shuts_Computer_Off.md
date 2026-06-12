---
title: "Win2k SP4 Randomly Shuts Computer Off"
date: 2008-08-06
forum: Windows
---

### Post by Bungo Pony on 2008-08-06
I've had this happen to me twice now. I rarely use Windows nowadays, but twice when I've been using it, it's completely shut the computer off. No warning, nothing. The screen just turns black, the drives spin down, and the computer is off. This NEVER happens when I'm booted into Ubuntu, so I know it's a software problem.

The first time I saw this problem was on my sis-in-law's Emachines PC running WinME. It was REALLY bad. You couldn't get ANYTHING accomplished for fear your computer would randomly turn off.

Now, I haven't installed the updates for Win2k yet, as I'm usually not booted into it long enough to bother. Was there a bugfix for this problem that I just haven't installed yet, or could it be something else?

---

### Post by angryfirelord on 2008-08-06
I'd say first check your cooling & airflow. I don't think win2k has CPU scaling enabled, so if your computer is in a tight spot, give it some air.

Then, I'd start playing with drivers. Update them if they're needed, otherwise start disabling some of them and see what happens.

---

### Post by kerry_s on 2008-08-06
> **Bungo Pony said:**
> I've had this happen to me twice now. I rarely use Windows nowadays, but twice when I've been using it, it's completely shut the computer off. No warning, nothing. The screen just turns black, the drives spin down, and the computer is off. This NEVER happens when I'm booted into Ubuntu, so I know it's a software problem.

The first time I saw this problem was on my sis-in-law's Emachines PC running WinME. It was REALLY bad. You couldn't get ANYTHING accomplished for fear your computer would randomly turn off.

Now, I haven't installed the updates for Win2k yet, as I'm usually not booted into it long enough to bother. Was there a bugfix for this problem that I just haven't installed yet, or could it be something else?

i would check your temps, then the settings->right click my computer> properties> advanced> startup and recovery, under "system failure" uncheck automatically reboot. see if you can get a error message, normally it would throw up a blue screen if something went wrong, so i think you could be overheating, right click the taskbar> task manager and see if anything is using cpu high, it should mostly be on system idle.

---

### Post by rockface on 2008-08-06
As stated in other posts, this could be a temperature issue. While I have no solution for your problem, there may be a simple explanation.

When the processor is idle the 'halt' command initiates an instruction set to cease activity and thus the processor cools down when not in use. I think this is why Ubuntu may keep functioning and why Windows 2000 does not.

Most operating systems carry the instruction set to control the 'halt' command. I don't think Windows 2000 did (I'm not sure about XP or Vista) and you used to be able to buy commercial programmes to do just this (CPUcool was /is one such product).

Others have suggested looking in the area of system cooling, I think this would be a good place to start.

---

### Post by kerry_s on 2008-08-06
> **rockface said:**
> As stated in other posts, this could be a temperature issue. While I have no solution for your problem, there may be a simple explanation.

When the processor is idle the 'halt' command initiates an instruction set to cease activity and thus the processor cools down when not in use. I think this is why Ubuntu may keep functioning and why Windows 2000 does not.

Most operating systems carry the instruction set to control the 'halt' command. I don't think Windows 2000 did (I'm not sure about XP or Vista) and you used to be able to buy commercial programmes to do just this (CPUcool was /is one such product).

Others have suggested looking in the area of system cooling, I think this would be a good place to start.


interesting, i'm running win2ksp4 on my laptop, it's on 24/7 and i don't have any problems with idle.

---

### Post by rockface on 2008-08-06
> **kerry_s said:**
> interesting, i'm running win2ksp4 on my laptop, it's on 24/7 and i don't have any problems with idle.

I guess I should consider explaining my 'utterences' in a more succinct manner.

On most systems with adequate cooling and air circulation initiating the 'halt' instruction set will do diddley squat.

If you already have heat related problems anyway, NOT initiating the 'halt' instruction set will exasperate an already bad situation.

The original poster's Ubuntu installation has the 'halt' capability built in   and he states clearly he has no problems when using Ubuntu. But a Windows 2000 on the same machine shuts down randomly.

As I did say 'there may be a simple explanation', 'may' being the operative word. Without direct access to the machine in question none of us will know for certain wherein the fault lies.

---

### Post by kerry_s on 2008-08-06
> **rockface said:**
> I guess I should consider explaining my 'utterences' in a more succinct manner.

On most systems with adequate cooling and air circulation initiating the 'halt' instruction set will do diddley squat.

If you already have heat related problems anyway, NOT initiating the 'halt' instruction set will exasperate an already bad situation.

The original poster's Ubuntu installation has the 'halt' capability built in   and he states clearly he has no problems when using Ubuntu. But a Windows 2000 on the same machine shuts down randomly.

As I did say 'there may be a simple explanation', 'may' being the operative word. Without direct access to the machine in question none of us will know for certain wherein the fault lies.

:lolflag: no worry's, i'm just being a prick today. it's always hard to figure out whether it's software or hardware.

---

