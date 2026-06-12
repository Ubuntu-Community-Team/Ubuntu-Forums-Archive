---
title: "Do new security fixes introduced in latest Linux Kernels get Backported to LTS Kernel"
date: 2019-01-13
forum: Security
---

### Post by monkeyman2 on 2019-01-13
Hello, I'm on 18.04 LTS. I'm currently on the 4.15 Kernel that comes with it but have read that Kernel 4.20 comes with a slew of security fixes, including ones aimed at Specter and Meltdown. I was wondering how many of these fixes will get backported to 4.15? Are there some fixes that are too dependent on the architectural changes made in the new kernels that cannot be backported? I'm specifically interested in the speculative and side-channel attack fixes. Would it be better for me to keep 4.15 up to date as the team rolls out the security releases or would there be a benefit to trying out 4.20 once it's stable enough (installing it via debs from archive.ubuntu.com)?

---

### Post by TheFu on 2019-01-13
If your life depends on the results, then trust nobody and patch everything manually.

If you are a typical small business or home user, run **apt update && apt upgrade** weekly and be happy.  
If you want to move forward and can have older programs removed automatically when they are out of date, run  **apt update && apt full-upgrade** weekly.

There were threads about CPU bugs in the Security sub-forum.  I think they are sticky, so at the top with all the available answers.

---

### Post by monkeyman2 on 2019-01-13
Thanks you for your quick and colorful response  :). My life doesn't depend on it and I am a home user but I also like to know what I am running and don't necessarily want to just run apt update and forget about it.

If you're referring to the Meltdown and Spectre Discussion Sticky, I did read through it as much as possible but the information is a year out of date and doesn't really answer my questions.

---

### Post by TheFu on 2019-01-14
The sticky threads have links to other blogs from Canonical employees.  That's all the information available unless you want to look at the kernel changelog entries.

Maybe I missed it, but I don't recall seeing any Linux attacks in the wild for these things, only security researchers.  [https://www.tomshardware.com/news/meltdown-spectre-malware-found-fortinet,36439.html](https://www.tomshardware.com/news/meltdown-spectre-malware-found-fortinet,36439.html) says that I'm wrong.  All my Intel CPUs are over 5 yrs old, so Intel won't be providing fixes.
I understand that current browsers already include mitigation code that isn't dependent on the OS or firmware.

Both my AMD CPUs are less than 5 yrs old - 1 is 3 weeks old.  I expect firmware and OS updates to come from the Canonical repos, as discussed last year.

I pulled a 2009 Core i7 out of service about 3 weeks ago. Still have a 2010 Core i5 to retire.

Most desktop users are under much more attack risk just by allowing javascript in their browsers.

Assume you've read this already: [https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown) which was updated in July.

Canonical has a security patch policy for supported code which they follow. Nothing special about these issues.  If you have paid LTS support for 12.04, it will be patched.  Support for 14.04 ends in a few months, unless you have paid support. 16.04 support goes to 2021.  The specific lines of kernels supported in the LTS are listed.  [https://wiki.ubuntu.com/Kernel/Support](https://wiki.ubuntu.com/Kernel/Support)  Stay on the supported versions and be happy.  In general, stay with either the .0 or .1 released kernel to have the full 5 yrs of support.  If you install the .2, .3, .4, kernels, then you must upgrade to the next kernel release with the next point release.  The chart is clear.

---

### Post by monkeyman2 on 2019-01-14
Thanks for the info, TheFu. I'll have a read through it.

---

