---
title: "Ubuntu 18.04 32-bit | VMware ESXi 6.7 | Web Server Application becomes Unresponsive"
date: 2020-10-27
forum: Virtualisation
---

### Post by fstephane on 2020-10-27
My company distributes a local web server that runs on an Ubuntu 18.04 32-bit VM.

One client has this running on VMware ESXi 6.7 and our software goes down periodically (every couple of weeks - hard to tell because it's not used every day).
We have many instances installed on VMware and none of them have this issue.

The VM is still running and shows this output:

[B]First Instance
[/B][ATTACH=CONFIG]287239[/ATTACH]
[B]
Second Instance
[/B][ATTACH=CONFIG]287240[/ATTACH]

The Client's IT has been able to resolve this by just restarting the VM. But that's not a long-term solution

I don't have direct access to the VM so I can't tinker with it anytime, but I can set up a session with their IT to dig into this.
However I'm not very experienced with Ubuntu or VMware so I'm having trouble making sense of this output or determining whether it's indicative of our main issue.

If anyone could help me shed some light on this or guide my troubleshooting I would be very grateful!

---

### Post by TheFu on 2020-10-27
A few ideas.  We stopped using VMware stuff about 10 yrs ago.

Appears that someone setup the VM to support memory ballooning.  Don't allow that.

BTW, 32-bit version of Ubuntu are EoL with 18.04. 20.04 doesn't have 32-bit support, so your company needs to move to a 64-bit solution in the next few years.

Part of troubleshooting is to take error messages and do a google search for them.  When images are posted, we can't easily do that. Please don't post images of text pages.  Post text.  If your terminal can't copy/paste text ... get a better terminal 
or
use normal output redirection for stdio and stderr.

Are there any other errors or warnings in the system log files? Use grep to find them ... then look at 5 lines above/below the errors - that's an estimate. The timestamps on each line should make it clear which lines aren't too old/new to be related.

---

