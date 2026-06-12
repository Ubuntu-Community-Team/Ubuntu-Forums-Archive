---
title: "Up arrow and down arrow don't work in vmware console"
date: 2009-04-05
forum: Server Platforms
---

### Post by dugh on 2009-04-05
I installed vmware server, created a virtual machine and attached the jaunty server install cd.

The up and down arrow keys don't work in the web-based vmware console interface.

None of the fixes I've seen work.  Any of them work for you?
[http://nthrbldyblg.blogspot.com/2008/06/vmware-and-fubar-keyboard-effect.html](http://nthrbldyblg.blogspot.com/2008/06/vmware-and-fubar-keyboard-effect.html)

This pretty much makes vmware completely unusable unless there is a fix.

---

### Post by .nedberg on 2009-04-05
I have also had this problem with VMWare and tried all the fixes with no result. IIRC the keypad arrows works, but that is sub-optimal.

I "solved" it by using ssh and VNC.

---

### Post by TwiceOver on 2009-04-05
I have the same problem with Windows XP in a VM.  So this must be a VMWare issue and not directly related to the installed OS.

---

### Post by Xipher on 2009-04-05
This is a VMware bug, try this fix
[http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=kc&externalId=1007439](http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=kc&externalId=1007439)

---

### Post by dugh on 2009-04-05
> **Xipher said:**
> This is a VMware bug, try this fix
[http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=kc&externalId=1007439](http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=kc&externalId=1007439)

Yeah that page suggests the same fixes that I linked to, which didn't work.

---

### Post by fornix on 2009-05-03
Try this

```
$ echo "xkeymap.nokeycodeMap = true" >> ~/.vmware/config
```

This worked for me!

---

### Post by Highway on 2009-06-16
I was having the same issue while using my laptop to connect to the vmware admin page and opening a console of a virtual machine.  
I tried the keymap stuff mentioned here and in the vmware kb above, but it didn't work.

I finally noticed that holding down my FN key (dell latitude laptop) while using the keys i, j, k,l,m worked fine.  These are intended to mimic the numeric keypad of a fullsize keyboard, and they did the trick perfectly.

Might be useful to someone. 

Highway.

---

### Post by Cheesemill on 2009-06-16
> **fornix said:**
> Try this

```
$ echo "xkeymap.nokeycodeMap = true" >> ~/.vmware/config
```This worked for me!

Remembering of course to do this on the machine you're running the Remote Console on and **not** the server (and for the correct user). This has caught me out a couple of times :)

---

### Post by sldunn05 on 2009-07-03
$ echo "xkeymap.nokeycodeMap = true" >> ~/.vmware/config


This worked splendidly for me right off the bat.

---

### Post by dslink on 2009-10-12
thanks

---

### Post by tomvanbraeckel on 2009-11-17
This worked for me too. Thanks for pointing out that the command has to be run on the client, not on the server !

---

### Post by mattduguid on 2011-01-14
Still having some issues with the keyboard problem,
 
Setup:
Windows 7 x64 client, running VMware player 3.1.3 build-324285, with virtual machine running Ubuntu Server 10.10 with Vmware tools installed.
 
Problem:
Same keyboard issues experienced by people in this forum post and various URL's posted below. 
 
[http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=kc&externalId=1007439](http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=kc&externalId=1007439)
 
[http://www.vmware.com/support/ws55/doc/ws_devices_keymap_linux_longer.html](http://www.vmware.com/support/ws55/doc/ws_devices_keymap_linux_longer.html)
 
[http://www.nalinmakar.com/2008/11/12/vmware-player-and-ubuntu-810-keyboard-mapping-issues/](http://www.nalinmakar.com/2008/11/12/vmware-player-and-ubuntu-810-keyboard-mapping-issues/)
 
[http://blogs.unbolt.net/index.php/brinley/2008/11/12/vmware-server-2-0-breaks-keyboard-mappin-10](http://blogs.unbolt.net/index.php/brinley/2008/11/12/vmware-server-2-0-breaks-keyboard-mappin-10)
 
I've tried most mentioned fixes without resolution including,
 
[FONT=Courier New]Added following keycode mappings...[/FONT]

xkeymap.nokeycodeMap = true 
xkeymap.keycode.111 = 0x148 # Up
xkeymap.keycode.116 = 0x150 # Down
xkeymap.keycode.113 = 0x14b # Left
xkeymap.keycode.114 = 0x14d # Right
 
[FONT=Courier New]...to following paths...[/FONT]
 
[FONT=Courier New]~/.vmware/config [/FONT]
[FONT=Courier New]/etc/vmware/config[/FONT] 
 
Any further ideas would be appreciated.

---

### Post by arrrghhh on 2011-01-14
> **mattduguid said:**
> Any further ideas would be appreciated.

Use VirtualBox?  *Shrugs*

---

### Post by mattduguid on 2011-01-20
Cheers will check it out but still interested in solutions under this virtualisation technology if anyone has any :)

---

### Post by jahwork on 2012-02-17
> **Highway said:**
> I was having the same issue while using my laptop to connect to the vmware admin page and opening a console of a virtual machine.  
I tried the keymap stuff mentioned here and in the vmware kb above, but it didn't work.

I finally noticed that holding down my FN key (dell latitude laptop) while using the keys i, j, k,l,m worked fine.  These are intended to mimic the numeric keypad of a fullsize keyboard, and they did the trick perfectly.

Might be useful to someone. 

Highway.

Thanks for the trick, I confirm this on a Dell Latitude D620
with little variant :

Up => Fn + 8 
Down => Fn + 2 (the blue one => k)
Left => Fn + 4 (the blue one => u)
Right => Fn + 6 (the blue one => o)

---

