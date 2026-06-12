---
title: "Stuck at &quot;Starting up ...&quot;"
date: 2008-11-18
forum: Server Platforms
---

### Post by stkrzysiak on 2008-11-18
Hi everyone, 
    Any help on this matter would be appreciated.  Also, I am posting it here for the purpose of someone saving themselves some grief if they ever encounter this in the future.
    I setup an Ubuntu 8.04 LAMP server on a Shuttle [KPC 45]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856101064").  Everythign was working great, and I had several websites running for a month or so.  Then yesterday, the server was down.  This is where some background info is needed.
    I had previously built an Ubuntu LAMP server(different distro i think, but dont recall which one) on this same PC, and the server crashed.   I had never seen the symptoms it was spitting out to me, and the entire server was built with new parts except the hard drive, so I decided to replace the hard drive and rebuild.  Which brings us to the current setup, all new parts, Ubuntu 8.04 LAMP server.
   Anywho,  I could not get terminal access after I hooked up a monitor/keyboard, so I did a reboot.  At that point, I would get the Shuttle splash and then the Grub menu. Everything seems in check, but then it freezes at the "Starting up ..." screen.   I rebooted, edited out the 'quite splash' from the grub line, and proceeded with a boot.  The same thing happened, just the black screen with 'Starting up ...'
    
    Has anyone ever seen this?  I am going to try a live cd tomorrow,  and if that works I can check dmesg(or I can do this from the grub command line), but what would I be looking for?
    I saw a post somewhere earlier that said this could be a BIOS communicating with Grub issue(the premise for this being that it doesnt load the kernel at all?), is this possible?  I doubt I have the most updated firmware, I can try that route if need be...

Any help of course would greatly be appreciated, and I will post my updates on this.  I will go as far as buying the exact same KPC and processor just to rule out those as potential culprits(or single them out), but in the meantime let me know if you have any suggestions....  

Thank you, 
Steve

---

### Post by cdenley on 2008-11-18
> **stkrzysiak said:**
> Hi everyone, 
    Any help on this matter would be appreciated.  Also, I am posting it here for the purpose of someone saving themselves some grief if they ever encounter this in the future.
    I setup an Ubuntu 8.04 LAMP server on a Shuttle [KPC 45]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856101064").  Everythign was working great, and I had several websites running for a month or so.  Then yesterday, the server was down.  This is where some background info is needed.
    I had previously built an Ubuntu LAMP server(different distro i think, but dont recall which one) on this same PC, and the server crashed.   I had never seen the symptoms it was spitting out to me, and the entire server was built with new parts except the hard drive, so I decided to replace the hard drive and rebuild.  Which brings us to the current setup, all new parts, Ubuntu 8.04 LAMP server.
   Anywho,  I could not get terminal access after I hooked up a monitor/keyboard, so I did a reboot.  At that point, I would get the Shuttle splash and then the Grub menu. Everything seems in check, but then it freezes at the "Starting up ..." screen.   I rebooted, edited out the 'quite splash' from the grub line, and proceeded with a boot.  The same thing happened, just the black screen with 'Starting up ...'
    
    Has anyone ever seen this?  I am going to try a live cd tomorrow,  and if that works I can check dmesg(or I can do this from the grub command line), but what would I be looking for?
    I saw a post somewhere earlier that said this could be a BIOS communicating with Grub issue(the premise for this being that it doesnt load the kernel at all?), is this possible?  I doubt I have the most updated firmware, I can try that route if need be...

Any help of course would greatly be appreciated, and I will post my updates on this.  I will go as far as buying the exact same KPC and processor just to rule out those as potential culprits(or single them out), but in the meantime let me know if you have any suggestions....  

Thank you, 
Steve

Have you tried using the irqpoll option in grub?
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/123617](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/123617)
Or you can try others like noacpi.
[https://help.ubuntu.com/community/BootOptions#Kernel%20Options](https://help.ubuntu.com/community/BootOptions#Kernel%20Options)

---

### Post by stkrzysiak on 2008-11-19
cdenley, 
Thank you for the advice.  I finally made it back to the site just now(this server is not what you would call crucial) and it was still down.  I was unable to see what was on the screen before I rebooted, but when I did reboot so that I could try the other grub options, it worked fine!  This reminds me of what happened with this same PC several months back.  It froze up, I didnt have time to fix it, when I went to go fix it a few weeks later, it booted fine.  The server is never really hot, so I am not sure what the problem is.  I will update this thread when it comes back, which I am sure it will.  Thanks again!

---

