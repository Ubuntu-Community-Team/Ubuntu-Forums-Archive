---
title: "AHK-like Virus"
date: 2009-11-20
forum: Security
---

### Post by Xog on 2009-11-20
There's a large plethora of virii out there in cyberspace, and I was wondering if at all there was a virus that could penetrate the ubuntu.. sure there's different effects, semi-harmful and non-harmful, as i've read from several discussions past. But then I thought.. AutoHotKey..

AutoHotKey is a simple program that generates keystrokes it's scripted to send. For instance, it's as simple as:

```
{
Send sudo rm -rf /
}
```

So I was thinking(i should really stop doing that) what if a virus included the process to generate key strokes like that?

Would a simple
```
{
Send [Whatever shortcut Keys are used to open up the linux version of windows' "Start -> Run"]
pause 02000 ;waits 2 seconds
Send [Whatever the command is to open up a terminal]
Send [Enter]
pause 02000 ;waits 2 seconds
Send sudo rm -rf /
Send [Enter]
}
```

really work? Or would Wine generally not allow keyboard shortcuts to things like pressing ALT, then an arrow to access your top panel?

Is there a difference between these if the Desktop emulation is turned on/off?

---

### Post by jessiebrownjr on 2009-11-20
> **Xog said:**
> There's a large plethora of virii out there in cyberspace, and I was wondering if at all there was a virus that could penetrate the ubuntu.. sure there's different effects, semi-harmful and non-harmful, as i've read from several discussions past. But then I thought.. AutoHotKey..

AutoHotKey is a simple program that generates keystrokes it's scripted to send. For instance, it's as simple as:

```
{
Send sudo rm -rf /
}
```So I was thinking(i should really stop doing that) what if a virus included the process to generate key strokes like that?

Would a simple
```
{
Send [Whatever shortcut Keys are used to open up the linux version of windows' "Start -> Run"]
pause 02000 ;waits 2 seconds
Send [Whatever the command is to open up a terminal]
Send [Enter]
pause 02000 ;waits 2 seconds
Send sudo rm -rf /
Send [Enter]
}
```really work? Or would Wine generally not allow keyboard shortcuts to things like pressing ALT, then an arrow to access your top panel?

Is there a difference between these if the Desktop emulation is turned on/off?

As far as i know, stuff in wine can only affect the fake C directory thats provided because its in a virtual machine. Im not a coder though so im not 100% sure.. Also, you'd have to enter your password for it to go into effect because of the sudo command. Thats why you are told to only install software from trusted sources.

---

### Post by Agent ME on 2009-11-21
> **jessiebrownjr said:**
> As far as i know, stuff in wine can only affect the fake C directory thats provided because its in a virtual machine. Im not a coder though so im not 100% sure.. Also, you'd have to enter your password for it to go into effect because of the sudo command. Thats why you are told to only install software from trusted sources.
Wine isn't an emulator or virtual machine - the programs run can access the system like a regular linux program.


There's no need for a virus to send key codes and open a program on your screen to do something destructive. It can just run the commands itself.

---

### Post by Xog on 2009-11-21
> **Agent ME said:**
> Wine isn't an emulator or virtual machine - the programs run can access the system like a regular linux program.


There's no need for a virus to send key codes and open a program on your screen to do something destructive. It can just run the commands itself.

so basically it can be programmed to log keys until it sees 'sudo' and then waits for the Enter key, then records the next line until the next enter key and stores it as the sudo password? that's a little too easy.. there's got to be a way that it can't do this

---

### Post by Xog on 2009-11-21
The virus runs a keylogging program that watches until you type "sudo" and then starts logging keys after pressing Enter, then stops when it presses Enter again and stores it as the sudo password.
This program runs in the background, and monitors the user's computer usage, waiting for the user to stop. Once the user stops, it waits for 5 minutes. When the timer is up, presses the hotkey combination to open up a terminal, types in sudo rm -rf / (enter) password (enter) and bye bye computer?

what would stop this program from running?

---

### Post by falconindy on 2009-11-24
How would a Windows based Virus running in the context of the Windows API (via Wine) have any possible effect on Linux? There's no possible way it could run sudo anything. Furthermore, giving Wine write access to your Linux filesystem outside the drive_c directory would be a foolish maneuver.

In short, if you fell victim to something like this, you earned it. Wine is only as "dangerous" as the user makes it.

---

### Post by Agent ME on 2009-11-24
> **falconindy said:**
> How would a Windows based Virus running in the context of the Windows API (via Wine) have any possible effect on Linux? There's no possible way it could run sudo anything. Furthermore, giving Wine write access to your Linux filesystem outside the drive_c directory would be a foolish maneuver.
Wine programs can modify files outside of the drive_c directory just like a linux program. Wine programs can also launch linux executables and shell programs just like a linux program. This is easily provable if you try out a Wine program that can launch programs and write to files.

Nothing stops a virus being run in Wine from infecting an Ubuntu system other than the fact that most are only programmed to infect Windows systems.

---

### Post by falconindy on 2009-11-24
> **Agent ME said:**
> Wine programs can modify files outside of the drive_c directory just like a linux program. Wine programs can also launch linux executables and shell programs just like a linux program. This is easily provable if you try out a Wine program that can launch programs and write to files.

Nothing stops a virus being run in Wine from infecting an Ubuntu system other than the fact that most are only programmed to infect Windows systems.
Like I said, if Wine has permission to write outside of its 'drive_c' directory, its because you, the user, foolishly allowed it.

---

### Post by Agent ME on 2009-11-24
Wine programs run just like regular linux programs. I just tested on a freshly installed virtual Ubuntu 9.10 system. I installed the wine package from the repository, ran the included notepad.exe clone, and it could edit any file I could. There is no setting to prevent them from writing outside of the drive_c folder.

---

