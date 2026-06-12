---
title: "Cant uninstall sun virtualbox"
date: 2009-08-27
forum: Virtualisation
---

### Post by datboy on 2009-08-27
Hey guys im having a major problem i cant uninstall vb.Its not listed in sources i tried to remove it in the terminal and it says its not installed i tried to purge it but no luck im running ubuntu 9 thanks

---

### Post by tuxxy on 2009-08-27
[FONT=monospace]Did you install the .deb from virtualbox website, try this;

[/FONT]```
sudo dpkg -r VirtualBox
```

---

### Post by datboy on 2009-08-27
yes i installed it from their site i tried the code you stated this is the message i got
dpkg - warning: ignoring request to remove virtualbox which isn't installed.

---

### Post by datboy on 2009-08-27
Anyone else out there can help

---

### Post by andrea000 on 2009-08-27
It should show up in synaptic so you could try there.
You can also try this in the terminal
> sudo apt-get --purge remove virtualbox

---

### Post by datboy on 2009-08-28
Tried it but to no avail........

---

### Post by andrea000 on 2009-08-28
it does not show up in synaptic?

---

### Post by Perryg on 2009-08-31
Type ```
dpkg -l virtual*
``` in terminal and see if it lists virtualbox.  If so you should be able to remove it using dpkg.  
If you see it there and then it says it is not installed when you try to remove it you are not typing the complete name.  
You can try to use a wild-card and see if it finds it or type the complete name.  ```
sudo dpkg -r virtualbox*
```

---

### Post by Dedoimedo on 2009-09-01
VirtualBox package goes with capital V,B, so you might want to check this one too. Likewise, try VirtualBox3, virtualbox3.
Maybe try via Synaptic, search for virtualbox and see what it offers you.

Dedoimedo

---

### Post by hatsch on 2009-10-20
i have the same problem here. none of the described solutions worked.
any ideas?

---

### Post by renkinjutsu on 2009-10-20
sure you installed from the deb file and not the run file?

---

### Post by moz44 on 2010-03-27
I have Sun Virtual Box version 3.0 installed in my Karmic Koala box. To uninstall it I just typed in the command line:

> sudo dpkg -r  virtualbox-3.0

---

### Post by pcrat on 2010-05-01
yep ive tried it all also.. I downloaded the deb file from there site.. installed it by clicking the deb file. thats it its installed.. now theres no way to get rid of this? i got vmware which is better so now got to figure out how to get rid of this...

wish i seen this thread before i installed virtual box lol.

---

### Post by phi2go on 2010-05-30
I'd got the same problem and I solved it with using the option --purge

sudo dpkg --purge virtualbox-3.1

do it for all virtual* you had.

---

### Post by TheFu on 2010-05-30
Whatever you do, don't go and delete any files manually. You'll be in &quot;APT-Hell&quot; from now on if you do. You'll have to learn much more about APT that you really want to know in that case to clean up the database.  On my 10.04 Server install, the package names from 

$ sudo dpkg -l virtual*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  virtualbox     <none>         (no description available)
un  virtualbox-2.0 <none>         (no description available)
un  virtualbox-2.1 <none>         (no description available)
un  virtualbox-2.2 <none>         (no description available)
un  virtualbox-3.0 <none>         (no description available)
un  virtualbox-gue <none>         (no description available)
ii  virtualbox-ose 3.1.6-dfsg-2ub x86 virtualization solution - base binaries
ii  virtualbox-ose 3.1.6-dfsg-2ub x86 virtualization solution - kernel module 
ii  virtualbox-ose 3.1.6-dfsg-2ub x86 virtualization solution - Qt based user 
un  virtualbox-ose <none>         (no description available)

---

### Post by mercvrivs on 2011-04-14
Try

```
sudo apt-get purge virtualbox-ose virtualbox-ose-dkms
```

---

