---
title: "Man in the Browser"
date: 2012-10-04
forum: Security
---

### Post by mike acker on 2012-10-04
See: [http://www.csoonline.com/article/717979/man-in-the-browser-malware-scam-goes-universal](http://www.csoonline.com/article/717979/man-in-the-browser-malware-scam-goes-universal)

it is my understanding that for a "Man in the Browser" attack to succeed the attacker will need to compromise the victim's browser. Most likely by covertly installing a plug-in...

...these browser attacks may be the main reason I'm building me a new big hammer so I can switch my online activity to Linux

in Windows I have to run "WinPatrol" -- to detect and stop all these requests to update my browser... it is really UGLY

hopefully in Linux the browser, e.g. Firefox -- is actually running in "Userland" -- and cannot be updated without permission to install software -- and that would apply to "plug-ins" as well -- which -- in Windows -- UAC does not object to ... I think because such updates are updates to the browser -- and not to the system

please forgive me if I chew on too many of this type of question...

---

### Post by Hungry Man on 2012-10-04
All applications run userland. Updates are handled centrally by the operating system so you have the option to choose which ones you do or don't update. This won't stop a MitB attack though - it would probably make it easier if you're late on patching.

An attacker who exploits Firefox essentially controls Firefox - they are in the browser at that point in virtually every way (without getting too technical). Your best bet is to prevent attacks on the browser by using something like Apparmor. Apparmor confines the Firefox process capabilities, which will prevent many exploits from working. It will also stop any files from being written to without explicit permission - this is another way to help prevent an attacker from doing any type of MitB attack as they won't be able to write new extensions/plugins if you've set it up right. There is a guide to Apparmor at the top of the forum, a sticky.

There's no need to worry about asking too many questions.

---

### Post by mike acker on 2012-10-06
="All applications run userland."

cool: they should.

what this means to me: the executable code -- and its subroutine libraries -- run in RING1 or RING2 of the x86 model.  which means: we do not need to worry about a script -- running in the browser -- "injecting" a modification into the browser's executable code.  The x86 hardware prevents this.

however,-- a script -- which the browser is running -- might try to drop some sort of special instructions into the browsers start-up configuration files -- 
[B]
a hidden plug-in possibly?[/B]

recent reports on the latest "Man in the Browser" attack have me chewing on this.*2

This morning, new reading on C/Net discusses a>  suit, filed in May, accuses Facebook of violating user privacy by tracking which Web sites the users visit even when they're logged out of Facebook.  see [http://news.cnet.com/8301-1023_3-57527275-93/facebook-asks-court-to-dismiss-$15-billion-privacy-suit/](http://news.cnet.com/8301-1023_3-57527275-93/facebook-asks-court-to-dismiss-$15-billion-privacy-suit/)

I continue to think {uh-oh*} that the best way to Surf the Web using LINUX is to use a separate user account for General Surfing.  particularly for a n00b like me,-- i 'll learn AppArmor, but hold on fellas, -- i just got LibreOffice hooked up to MySQL last nite -- I had to sudo app-get install the java driver -- i didn't have to do that on the 32 bit distro but now that i have my new box up i'm on the 64 bit distro.
~~~
* thinking seems to be "cool" -- here in Linux Land :)
*2 e.g. see [http://www.scmagazine.com.au/News/318058,new-web-attack-immediately-siphons-stolen-data.aspx](http://www.scmagazine.com.au/News/318058,new-web-attack-immediately-siphons-stolen-data.aspx)

---

### Post by rookcifer on 2012-10-06
> **mike acker said:**
> ="All applications run userland."

cool: they should.

what this means to me: the executable code -- and its subroutine libraries -- run in RING1 or RING2 of the x86 model.  which means: we do not need to worry about a script -- running in the browser -- "injecting" a modification into the browser's executable code.  The x86 hardware prevents this.

It *should* but it doesn't always in practice.  There are ways around non-executable data regions.  If you're really technical (i.e. understand C, assembly, and programming at the most basic level), you might enjoy [this talk.]("https://www.youtube.com/watch?v=38Nu7YOt6lQ")  Basically he wrote a tool (a debugger of sorts) that scans binaries (and the shared libraries) and looks for memory corruption bugs. He shows how to brute-force stack canaries (defeat FORTIFY_SOURCE) as well as get around full ASLR/PIE and NX.  He says it will work against Grsecurity kernels too.  He demonstrates this on an Ubuntu 10.10 box and gets a root shell with his exploits at least twice.

> however,-- a script -- which the browser is running -- might try to drop some sort of special instructions into the browsers start-up configuration files -- 
[B]
a hidden plug-in possibly?[/B]

This could be prevented with a good AppArmor policy.

---

### Post by Hungry Man on 2012-10-06
All userland means is that it isn't part of the kernel. That's separate from being able to inject code into a process. If an attacker exploits a page they inject ASM code and get 'shell' in the browser process. I think you're thinking more NX then x86. But there's always ways around NX.

Yes, a script may try to drop instructions. Malicious Javascript could be planted on the homepage for example. Apparmor can prevent these writes to the disk and prevent the exploit to begin with.

Facebook tracking happens in scripts, it's different from a MitB attack. Facebook loads up little 'Like' icons on various pages. It can 'see' those pages because of that and track anyone on those pages whether they're logged in or not. You can only stop this by blocking the 'Like' icons.

---

