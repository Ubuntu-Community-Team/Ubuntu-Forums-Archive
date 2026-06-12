---
title: "[SOLVED] SeamlessRDP opens the whole XP environment"
date: 2008-07-18
forum: Virtualisation
---

### Post by bmwman on 2008-07-18
Hello,

I have a VMware server and XP Pro as a guest machine inside Ubuntu Hardy 8.04. I'm trying to launch separate applications from the XP running in the background, but every time it opens up the whole XP desktop environment, instead of the individual application.

I try this ```
rdesktop -A -s "C:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" <IP of VM>:3389 -u <user> -p <pass>

``` and i've tried it with multiple programs. I have tried anything and everything i found in Google and still can't get it to work. I've used these
[https://help.ubuntu.com/community/Se...Virtualization](https://help.ubuntu.com/community/Se...Virtualization)
[https://wiki.ubuntu.com/SeamlessWindowsIntegration](https://wiki.ubuntu.com/SeamlessWindowsIntegration)
[http://www.cendio.com/seamlessrdp/](http://www.cendio.com/seamlessrdp/)

Any help is apreciated.
Thank you

---

### Post by dpj23 on 2008-07-18
you wont be able to launch just a single application from RDP session...  You can access the vm machine and then run the application from within that environment... 

There are products available to do what I believe you are trying to accomplish however, none that are free and all cost a lot of money...  Streaming applications is one of the new products that vm ware has just released...

---

### Post by bmwman on 2008-07-19
> **dpj23 said:**
> you wont be able to launch just a single application from RDP session...  You can access the vm machine and then run the application from within that environment... 

There are products available to do what I believe you are trying to accomplish however, none that are free and all cost a lot of money...  Streaming applications is one of the new products that vm ware has just released...

Yes you can launch individual applications from the VM running in the background. That's why it's called SeamlessRDP. I had it working the first time i tried but next day it wouldn't work anymore and just opens up a whole desktop environment, instead of just the application. There should be a tweak or something that i'm missing.

---

### Post by bmwman on 2008-07-19
I started over from scratch and it's working now. I followed this how to:
[https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)

Also check out this one, it allows you to run multiple apps at the same time.

[http://www.miguelfurtado.com/srdp.aspx](http://www.miguelfurtado.com/srdp.aspx)

---

