---
title: "Ubuntu Server 20.04 on Core2 laptop dies if lid/display is closed"
date: 2020-06-22
forum: Server Platforms
---

### Post by mikecolley on 2020-06-22
Newbie to Ubuntu, old timer linux user. I want to close the laptop lid and have the display turn off on this Ubuntu Server 20.04 and have it keep/stay running.

I'm creating a web and e-mail server for only me(myself one person) on my own domain so I think I will try Ubuntu Server on this old HP EliteBook 8730W laptop core2duo.  Loaded just fine from [64-bit ARM (ARMv8/AArch64) legacy server install image]("http://cdimage.ubuntu.com/ubuntu-legacy-server/releases/20.04/release/ubuntu-20.04-legacy-server-arm64.iso") at [http://cdimage.ubuntu.com/ubuntu-legacy-server/releases/20.04/release/](http://cdimage.ubuntu.com/ubuntu-legacy-server/releases/20.04/release/)  I loaded it onto USB Flash so I can move it to different computers and also make a mirror image backup(I've been doing this for years).  This is my first serious venture into Ubuntu.

I want to close the laptop lid because 1) the laptop takes up too much space with the lid open, 2) the keys get dusty with the lid open and 3) the display gets dark with years being on and aged.  

So I closed the laptop lid and the Ubuntu Server quit working; and when I opened it,  it didn't come back to life ( I pressed the on switch but only the display came on, no response ).  I want Ubuntu Server to keep running all the time no matter if the lid is open or closed or opened ( opened back up again ), I don't want Ubuntu Server to stop, I want it to stay running continuously.  I want it to keep running even if I don't log-in.  Servers shouldn't quit.  (Am I beating a dead horse here)

REQUEST  #1: How do I fix this?  Ubuntu Server is a command line OS and _I don't know what file to edit/change to fix the problem_.  

--> This didn't work: I've already tried removing the pound/hash/number symbol from #LidSwitchIgnoreInhibited=yes in /etc/systemd/logind.conf, doing that didn't work.

In the future I will make a Related separate Request #2: How do I get the display to automatically turn off and keep the laptop Ubuntu Server running after 30 minutes (so the display won't age)?  Right now the display just stays on forever.

I appreciate all you folk who are helping, smiles and thank you.

Thanks All - Mike  (I'll be back much later today)

---

### Post by ajgreeny on 2020-06-22
Thinking about that LidSwitchIgnoreInhibited line I think you're  right to remove the # but surely the line should end with no not yes; it's  one of those double negative lines that can easily catch you out.

Worth trying I believe!

---

### Post by cmcanulty on 2020-06-22
those options are in power manager

---

### Post by LHammonds on 2020-06-22
I have never run server on a laptop so I'm in the dark here but here are my best guesses:

You can access the manual with this command:
```

man logind.conf

```

The default entries in /etc/systemd/logind.conf that are commented out are how it is configured right now.  Partial example on 20.04:
```

#HandleSuspendKey=suspend
#HandleHibernateKey=hibernate
#HandleLidSwitch=suspend
#HandleLidSwitchExternalPower=suspend
#HandleLidSwitchDocked=ignore
#PowerKeyIgnoredInhibited=no
#SuspendKeyIgnoredInhibited=no
#HibernateKeyIgnoredInhibited=no
#LidSwitchIgnoreInhibited=yes
#IdleActionSec=30min

```

If you only uncomment the lines, nothing will change because that is how the system is already running.  Once you uncomment a line and change the value, you can make the changes take effect with this command:

```
sudo systemctl restart systemd-logind
```

For an always-on laptop server, this is what I would set:
```

HandleSuspendKey=ignore
HandleHibernateKey=ignore
HandleLidSwitch=ignore
HandleLidSwitchExternalPower=ignore
IdleAction=ignore
HandleLidSwitch=ignore

```

As for turning off the monitor, I'm not sure about that.  I've seen use of the "setterm" command but that is a user space command and may not affect anything if not logged in.  Many other articles I have read were related to a GUI which is not applicable in this scenario.  I have tried setting the "blankscreen" in grub to 1 minute and it works on my virtual machine but I have no idea if that actually powers off the monitor.  I suspect it does not but it is something you can try:

```
sudo vi /etc/default/grub
```

Find this:
```
GRUB_CMDLINE_LINUX_DEFAULT=""
```
Change to:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet consoleblank=1"
```

Then update grub:
```
sudo update-grub
```

Reboot your system for the changes to take effect and let me know if that actually turns off power to the monitor or if it just blacks out the screen.  This also might only blank the console if it is just presenting the login...it may not affect it if you login.

LHammonds

---

### Post by mikecolley on 2020-06-22
Hi LHammonds, THANK YOU LHammonds!!!

Excellent results so far, not finished.

Action: Create-copy files: logind.conf-Original-From-Apache and grub-Original-From-Apache     Results: I have original files backed up.
Action: Made all the changes you suggested.  Powered down.  Powered up.  Lid is open (can't turn laptop on with closed lid), lid still open.
   Results: Blank-black screen with the screen lamp ON (looking at the lower edge of the screen to see if the laptop screen lamp is on).
Action: SSH into the Ubuntu Server box from another computer,     Results: SSH remote session works normally, just fine.
Action: Close the lid,     Results: SSH remote session stays connected and laptop works and the screen lamp goes out (!!! Fantastic GOOD Results).
Action: Open the lid,     Results: SSH remote session stays connected and laptop works and the screen lamp comes on with blank-black display and server working.
Action: Make this post, correct it several times, lid still open,     Results: SSH remote session and server working but screen lamp is on.
Action: Close the lid, update this post, make corrections again,     Results: SSH remote session and server working and screen lamp is off.

Results: WOW, one out of two requests successful ( the important one ), that is an awesome good result!!!  THANK YOU LHammonds for your very clear, exact and knowledgeable directions.  Now I'm debating whether to work on request #2 and get the laptop display working again -- I think the fix is simple to copy grub-Original-From-Apache and run sudo update-grub.  I will be back after a long break starting now.

THANK YOU LHammonds!!!

---

### Post by TheFu on 2020-06-22
a) if this problem is solved, please help the community out by marking it _SOLVED_ using the **Thread Tools** button at the top of the page.

b) laptop cooling can become an issue when the lid is closed since some heat does exit through the keyboard too, not just out the back. I'd watch the different temperatures to ensure overheating doesn't become a problem with the lid closed.

---

### Post by mikecolley on 2020-06-23
Solution

Edit the file /etc/systemd/logind.conf

Find the lines similar to below and change them to match this, leave the other lines in the file alone:
```
HandleSuspendKey=ignore
HandleHibernateKey=ignore
HandleLidSwitch=ignore
HandleLidSwitchExternalPower=ignore
IdleAction=ignore
HandleLidSwitchDocked=ignore
```

Now I can push the power-on and close the lid right away and the server boots up and works just fine and the lid display lamp is out.

Side Note and good suggestion: TheFu said that "laptop cooling can become an issue when the lid is closed" and I did check it.  The keyboard was pretty warm, but the fan on the laptop didn't speed up, so I'm probably going to leave the lid/display cracked about 1/2 inch.  I will set the laptop on the top shelf so it collects less dust.

_THANK YOU LHammonds for this solution_ and TheFu for the good suggestion.

Thank You All - Mike

---

### Post by TheFu on 2020-06-24
> **thefu said:**
> a) if this problem is solved, please help the community out by marking it _solved_ using the **thread tools** button at the top of the page.

solved?

---

### Post by mikecolley on 2020-06-30
Solved, thank you!  See second post above.  I finally did follow your directions and I pressed the "Thread Tools" button and marked this thread as solved.  Thanks! - Mike

---

