---
title: "Recommended sudo policy templates? Share!"
date: 2019-03-25
forum: Ubuntu, Linux and OS Chat
---

### Post by thatrandomguy+ on 2019-03-25
Hello,

I've been tuning in to discussions and topics on critical things some  think Linux might suffer in. One of those topics happened to be how  Ubuntu sets up or uses sudo/root.

This thread is **not** intended to discuss or debate on why or who does what better than them but rather to *invite* those who might have stuff that work for them for which everyone can benefit from.

Since I am not intimately familiar with how Ubuntu sets up sudo or how  that affects other parts of the system by default, I am willing to side  with the notion that solely leaving users to rely on sudo for everything  leads to bad practice.

While this might come off as a needless endeavor, I would like to  welcome those who feel like participating to share their policies or  templates for what they think would accommodate basic/common usage on a  system running Ubuntu.

Attempts to "educate" others by posting links to related threads or wikis are welcome but will be ignored by me. My *intent* is to see what others have and build off of that. The *idea* is to share.

---

### Post by TheFu on 2019-03-26
> I am willing to side with the notion that solely leaving users to rely on sudo for everything leads to bad practice.
Agreed.  

Ubuntu has been moving towards using **pkexec**, but people will find websites with instructions that have sudo in them for the next 30+ yrs.
 
Use **sudoedit** to edit system files.

---

### Post by Tadaen_Sylvermane on 2019-03-27
At home I only give sudo to myself, none of the other users here. I figure that if I was running a business or something with multiple users requiring sudo I would make use of groups with different commands they can execute as sudo. I would not give them blind sudo access to everything. That would be maintained by me, maybe a partner if I was set up that way. Yes I would use Ubuntu for my business needs unless something forces me otherwise.

I'll never understand other distros avoidance of sudo, Debian in particular. Either one can lead to total system destruction with a keystroke if you don't know what you are doing. I don't see how either one is safer than the other.

---

### Post by Frogs Hair on 2019-03-27
Playing around in the root file system with uncertainty or lack of knowledge can be dangerous regardless of how you get there. My file manger offers a graphicical open as root option so no need for commands. I do not open graphical applications with sudo and use the sudo -H command for gedit if needed.

---

### Post by yetimon_64 on 2019-03-27
> **Frogs Hair said:**
> ...I do not open graphical applications with sudo and use the **sudo -H command** for gedit if needed.

+1 for sudo -H, if graphical apps are involded.

I remember a few postings here, of years past, where not using the -H switch rendered desktops unbootable. Mixing root in using the users home settings was quite a pain for a bit back then. The "-H" switch stops such negative affects, keeping root to its own home folder for settings etc.

> Playing around in the root file system with uncertainty or lack of knowledge can be dangerous regardless of how you get there...Definitely, +1.

---

