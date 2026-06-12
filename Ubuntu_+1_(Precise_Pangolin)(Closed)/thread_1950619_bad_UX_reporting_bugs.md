---
title: "bad UX reporting bugs"
date: 2012-04-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Skaperen on 2012-04-01
> **Ubuntu +1 (Precise Pangolin)**
 This  forum is for the discussion of the development of the next version of  Ubuntu (Precise Pangolin). Precise is in development and will be  released in April 2012. Please note: Ubuntu Developers do not usually  read the forums, to report a problem found in Precise please report the  bug in [Launchpad]("https://launchpad.net/ubuntu/+filebug").Does Launchpad still try to get you to run a scan on the system you are running the browser on to access Launchpad?  It has done this to me all previous times, and it always gets info about the system I'm browsing from, not the system I'm reporting about.

I can read about bugs on Launchpad, but I quit reporting any until that bad UX is fixed.  So the best I can do is report bugs here until then.

---

### Post by MacUntu on 2012-04-01
I don't quite understand.

A. You click on the "Report a bug" link in LP and report the bug. On the affected machine run ```
apport-collect <BUG_NR>
```

B. You got a crash. Then there's a file in /var/crash. Copy that file to the machine you use to report the bug and run ```
ubuntu-bug foo.crash
```

---

### Post by Skaperen on 2012-04-01
> **MacUntu said:**
> I don't quite understand.

A. You click on the "Report a bug" link in LP and report the bug. On the affected machine run ```
apport-collect <BUG_NR>
```B. You got a crash. Then there's a file in /var/crash. Copy that file to the machine you use to report the bug and run ```
ubuntu-bug foo.crash
```

There's the problem.  I was unable to run that on the affected machine.

Quite many bugs I find are in the installer.  How does one get /var/crash when the machine freezes up?

---

