---
title: "grub menu show on dirty shutdown"
date: 2011-03-09
forum: Server Platforms
---

### Post by thrantir on 2011-03-09
Hi people,
    I've my Ubuntu 9.10 has this behavior on dirty shutdown (for instance a power loss). On the next boot grub choose menu appear , even if the timeout is set to 0, rather there isn't a timeout, it stays until I press return. I think it's a kind of rescue procedure, is there a way to avoid it?

Thanks in advance

---

### Post by drs305 on 2011-03-09
Yes there is. 

Normally the timer doesn't count down because the 'recordfail' check found a problem and requires a manual selection. A 'dirty' shutdown normally wouldn't cause a recordfail event, but an aborted boot would. The recordfail flag should be cleared once Ubuntu completes a normal boot. In your case bypassing the 'recordfail' check may nevertheless solve your issue.

If you feel like you really need to disable the *recordfail* check you can modify the /etc/grub.d/00_header script. 
```
gksu gedit /etc/grub.d/00_header
```

The Grub2 recordfail section in *00_header* may be different in 9.10, but it should look something like this:
> 
if [ "\${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=${2}
fi

and change it to:
> 
**[COLOR="DarkRed"]#[/COLOR]**if [ "\${recordfail}" = 1 ]; then
**[COLOR="DarkRed"]#[/COLOR]**  set timeout=-1
**[COLOR="DarkRed"]#[/COLOR]**else
  set timeout=${2}
**[COLOR="DarkRed"]#[/COLOR]**fi


Update grub with "sudo update-grub" for the changes to take effect.

---

### Post by thrantir on 2011-03-09
yes the code is exactly the same, thank you!

---

### Post by K_Light2003 on 2011-03-18
Mine does the same sometimes, but my server is 10.10. Is there a way to do this with 10.10 & Grub2. I checked the ***/etc/grub.d/00_header*** and have a different code than the above post.
```

function recordfail {
  set recordfail=1
  if [ -n "\${have_grubenv}" ]; then if [ -z "\${boot_once}" ]; then save_env r$
}

```I'm very much a new Ubuntu user so don't want to edit the file in the wrong way. :-k

---

### Post by drs305 on 2011-03-18
> **K_Light2003 said:**
> Mine does the same sometimes, but my server is 10.10. Is there a way to do this with 10.10 & Grub2. 

I'm very much a new Ubuntu user so don't want to edit the file in the wrong way. :-k

Good that you asked.

While modifying the recordfail timeout isn't something that is normally necessary, if you want to disable it here is the section you want to modify. It's around line 240 in /etc/grub.d/00_header:

```

**#**if [ "\${recordfail}" = 1 ]; then
**#**  set timeout=-1
**#**else
  set timeout=${2}
**#**fi

```

Save the file and then run "sudo update-grub"

I should note that when your system is hanging on start there is a reason. Disabling the recordfail check is bypassing a Grub feature that is designed to help the user possibly prevent booting to a problem menuentry.

I understand why someone running a server would want to make sure the OS always reboots without user input, I just thought I'd mention it.  :-)

---

### Post by K_Light2003 on 2011-03-19
Thx for the prompt reply there **drs305**, I should have studied the*** /etc/grub.d/00_header*** in a little more detail.

I agree that modifying the recordfail timeout is not a good idea, but the amount of times I have had to lug the server box to connect to a monitor and keyboard while I learn the system & Linux has been ridiculous. 

I don't think that shutting down the system with ```
sudo shutdown now
``` helped much mind. I now use ```
sudo halt
``` which seems to prevent most "dirty" shutdowns.

I'll only be doing this as a temporary measure until I'm more confident using the system.

---

### Post by hackeron on 2011-06-07
This seems like a ridiculous default for a server distribution :/

Can someone name a single advantage to having a -1 timeout compared to maybe an, oh I donno, 10 second timeout?

I had to drive to the office and to a client on several occasions because the recordfail was triggered. To date, it was triggered by a power failure, by a kernel oops, by a remote force reboot, by a v4l driver, by user error, by some other unknown reasons. Every time, I had to plug in a keyboard, press enter and leave without changing a thing.

I cannot think of a single circumstance where a -1 timeout is a good idea on a server.

---

### Post by drs305 on 2011-06-08
> **hackeron said:**
> This seems like a ridiculous default for a server distribution :/

Can someone name a single advantage to having a -1 timeout compared to maybe an, oh I donno, 10 second timeout?

I cannot think of a single circumstance where a -1 timeout is a good idea on a server.

It the recordfail event is recorded *and it is accurate*, the system failed to boot. If the system failed to boot, doing the exact same thing the next time will almost invariably produce the same result. Continuously rebooting or waiting for user input will both lead to the same result - a non-working system.

I see your point, but I think that there would be better options than continuously rebooting for perhaps hours on end.

First, make the recordfail robust enough to ensure it means the system is really unbootable.

Other options might include booting an alternative kernel - this was being discussed but may not yet be implemented - or attempting to boot X number of times, and *only then* awaiting user input. 

An experienced user could modify the scripts to do these things - you'd have to ask the devs why these options aren't included in a 'server' version of Grub 2. And perhaps there are such options of which I'm just unaware.

---

### Post by hackeron on 2011-06-08
> **drs305 said:**
> It the recordfail event is recorded *and it is accurate*, the system failed to boot. If the system failed to boot, doing the exact same thing the next time will almost invariably produce the same result. Continuously rebooting or waiting for user input will both lead to the same result - a non-working system.

I see your point, but I think that there would be better options than continuously rebooting for perhaps hours on end.

First, make the recordfail robust enough to ensure it means the system is really unbootable.

Other options might include booting an alternative kernel - this was being discussed but may not yet be implemented - or attempting to boot X number of times, and *only then* awaiting user input. 

An experienced user could modify the scripts to do these things - you'd have to ask the devs why these options aren't included in a 'server' version of Grub 2. And perhaps there are such options of which I'm just unaware.

On the one hand you have the many legitimate, single time failure to boot scenarios I listed, on the other hand I had a system kernel panic and reboot endlessly because of a BTTV option in /etc/modprobe.d that didn't trigger recordfail - I couldn't even get into the grub menu as there is no timeout and hitting shift didn't work.

If the system failed to boot, unless you have kernel.panic = 0 or something in /etc/sysctl.conf, chances are it will hang. If for any reason it didn't and it was rebooted again, then there was some kind of intervention. Why just show the menu forever? - it makes no sense :/

Last night I installed Ubuntu server on a little headless mini PC with no moving parts I fitted inside an alarm system enclosure. I connected the power - then realised I needed a smaller fuse, so replaced the fuse and low and behold, no access :/ - Had to trip the tamper on the alarm to get to the PC, take it out, plug in a keyboard and press enter :/

I'm all up for a better solution to this like maybe a gradually increasing timeout until the 5th retry, then try the next non rescue boot option or something. But really just an option to disable this without modifying /etc/grub.d code and preferably this really needs to be disabled by default on the server version.

---

### Post by chrisstankevitz on 2011-08-02
> **hackeron said:**
> I cannot think of a single circumstance where a -1 timeout is a good idea on a server.

Well said.

---

