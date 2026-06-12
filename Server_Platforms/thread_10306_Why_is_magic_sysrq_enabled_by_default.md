---
title: "Why is magic sysrq enabled by default?"
date: 2005-01-06
forum: Server Platforms
---

### Post by jdong on 2005-01-06
Why is magic sysrq enabled in Ubuntu's default kernels?

For those with physically locked Linux boxes, Magic Sysrq is very bothersome to deal with -- and they're forced to recompile a kernel JUST to get rid of magic sysrq.

---

### Post by daniels on 2005-01-06
I couldn't live without Magic SysRq -- and if someone has access to your keyboard, sorry, but you are already absolutely screwed; it doesn't gain you anything, security-wise.

---

### Post by nocturn on 2005-01-07
I mostly agree with jdong on this, it should be disabled by default.  In any case, users that understand and need this will be able to enable it (recompiling).

If people have access to your console, this is obviously not going to stop them from getting in,  there is nothing that can stop someone with enough determination from getting in if they have physical access.

Some thing do matter however to make the time it takes someone to gain control as long as possible (increasing their exposure and thereby the chance of getting caught):
- BIOS password (lock boot to HD only)
- Grub/LILO password to only allow booting the normal config

---

### Post by daniels on 2005-01-07
All it offers you is a false sense of security -- if they actually want your data, they'll just take out a screwdriver or something and take the drive.  Again, if they have physical access, it doesn't even slow them down, because if you're going for the power, why not just go straight to pulling the plug?

---

### Post by nocturn on 2005-01-07
[QUOTE=daniels]All it offers you is a false sense of security -- if they actually want your data, they'll just take out a screwdriver or something and take the drive.  Again, if they have physical access, it doesn't even slow them down, because if you're going for the power, why not just go straight to pulling the plug?[/QUOTE]

You are right, if the objective is to obtain your data, that is the easiest solution.   Hell, they could even take the entire system.
Although this is easy enough, not to many people will revert to it because it will not take you long to discover that something happened and they have a greater chance of getting caught (a physical item is easier to track then data).

Take this scenario.  I used to have a server in a previous company (big company, yet I had no access to a secure server room because that was owned by an external company).  The machine was just in our office, but locked down as described above.

If someone stole the harddrive over lunch (which they perfectly could), they would risk one of us coming back at any moment.   If the got away with the drive before we spotted them (given that we where out to luch for 30 minutes we would not likely spot them), I would immediatly notice that on coming back.

The result would be that on returning, I would call security, have the grounds locked down and have the police coming in at the same time. 
Even if they had gotten out before the lockdown, they would have had to pass the security station and would have been forced to sign out  (using a company swipe card - logged -, or on official passport - even then, only accepted if they where on the visitors list -).

I would personally feel the risk to doing something physical like this much greater then going in,   gaining access through something like unsecured booting and copying what I want to a removable HDD and rebooting the machine.
It would leave little physical evidence and might even go unnoticed (the reboot could be attributed to hardware issues).

Again, no security measure if full-proof, but the more layers you add, the smaller the window-of-opportunity gets.

---

### Post by jdong on 2005-01-07
[QUOTE=daniels]All it offers you is a false sense of security -- if they actually want your data, they'll just take out a screwdriver or something and take the drive.  Again, if they have physical access, it doesn't even slow them down, because if you're going for the power, why not just go straight to pulling the plug?[/QUOTE]

Consider where we have a lab of 20 Linux workstations, nicely packed into untamperable cases. If somebody attempts to damage data on a workstation by removing the plug or any other physical means, the lab supervisors would obviously notice.

However, repetitive Magic SysRq still has the chance of screwing over the workstation.

---

### Post by ctt on 2005-02-07
[QUOTE=jdong]Why is magic sysrq enabled in Ubuntu's default kernels?

For those with physically locked Linux boxes, Magic Sysrq is very bothersome to deal with -- and they're forced to recompile a kernel JUST to get rid of magic sysrq.[/QUOTE]
As is explained in the kernel documentation, disabling sysrq involves nothing more than:

```
echo "0" > /proc/sys/kernel/sysrq
```
...if you need it off all of the time just throw it into an init script.

As has been already explained, though, if someone has physical access to your box, turning off sysrq will probably not help you much.  As sysrq can, at the very worst, put your system into a state where no one (including the person using sysrq) can use it until a reboot, it can be no more destructive than, say, yanking out the power cord.

- chris

---

### Post by jdong on 2005-02-08
Ooh, nice... can be disabled through sysctl. Very good for public workstations... Reaching for the plug is a pretty obvious thing for our clueless lab monitors to see.

Repeatedly resetting the system is not. Frankly, students have some sort of fascination for the RAID5 rebuilding process... ??

---

