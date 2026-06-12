---
title: "VMWare Player broken on 11.04"
date: 2011-04-30
forum: Virtualisation
---

### Post by poldie on 2011-04-30
11.04 broke VMWare Player which has always worked fine on 10.04.  It just fails to start up.

I can see people discussing this online, and patches which people report not working.  I'd have thought that VMWare Player was the sort of high profile app that would be tested during Ubuntu's development, and that it's a little embarrassing that it's still broken.

Does anyone know of an official response to this, or, more pragmatically, a working patch in the meantime?

---

### Post by fjgaude on 2011-04-30
You need Player 3.1.4, the one that works with 10.10 and 11.04. You can download it from the VMware.com site.

---

### Post by poldie on 2011-04-30
> **fjgaude said:**
> You need Player 3.1.4, the one that works with 10.10 and 11.04. You can download it from the VMware.com site.

I got whatever the latest version is, and it just changed my problem from an error to it just stopping loading.

---

### Post by myth001 on 2011-04-30
[http://developers-developers-developers.blogspot.com/2011/04/ubuntu-1104-vmware-player-dies-when.html]("http://developers-developers-developers.blogspot.com/2011/04/ubuntu-1104-vmware-player-dies-when.html")

Quote:

To fix this, you have to tell VMWare Player to use its own glib: Insert the line

    export LD_PRELOAD=/usr/lib/vmware/lib/libglib-2.0.so.0/libglib-2.0.so.0

into the file /usr/bin/vmplayer - right after the copyright notice. The Beginning of the file should now look as follows:

    #!/usr/bin/env bash
    #
    # Copyright 2005-2008 VMware, Inc.  All rights reserved.
    #
    # Wrapper for the real 'vmplayer' binary. Ensure that the
    # binary will find all the shared libraries it needs. If a shared
    # library is not available from any of the standard system-wide
    # locations, we provide it from the location where the VMware software
    # is installed.
    #
    export LD_PRELOAD=/usr/lib/vmware/lib/libglib-2.0.so.0/libglib-2.0.so.0
    set -e


Save the file and restart VMWare player - you should be back in business.
Eingestellt von Christopher Staerkel um 04:22
Diesen Post per E-Mail versenden BlogThis! In Twitter freigeben In Facebook freigeben Freigeben in Google Buzz

---

### Post by Dngoins on 2011-05-02
Just what I needed thanks...

My issue was VMWare workstation not the player.
Thus I modified both the vmware and vmplayer in the /usr/bin

It worked like a charm!!!

---

### Post by cataboom on 2011-05-03
Hi all,

I still have issues with vmplayer 3.1.4 after upgrading to ubuntu 11.04 from 10.10.

I have a guest winXP. It usually loads until the login screen, but then...
VMware Player unrecoverable error: (vcpu-0)
NOT_REACHED /build/mts/release/bora-385536/bora/lib/user/dictionary.c:990
A log file is available in "/home/reve/vmware/winxp/vmware.log".  Please request support and include the contents of the log file.  

Does anybody has a clue?

Thanks a lot!

---

### Post by hnaether on 2011-05-04
Hi, 

I am occuring exactly the same problem with vmware player 3.1.4 and ubuntu 11.04 here. Anybody else?

best regards
Hans

---

### Post by garvinrick4 on 2011-05-04
sudo apt-get install aptitude
sudo aptitude update && sudo aptitude upgrade
before dist-upgrading:
*VM Player 3.1.4*
Was testing different styles of dist-upgrading in VMware and 
I was using 10.10 and just dist-upgraded the Debian way. It seemed
to list and correct any dependency issues. Told it to leave any conf. files
the way they are at any asking and went off with out a hitch. 
sudo perl -p -i.maverick -e 's/maverick/natty/' /etc/apt/sources.list
sudo aptitude install dpkg apt
sudo aptitude safe-upgrade
sudo aptitude full-upgrade
sudo aptitude dist-upgrade
sudo reboot
Came up to 11.04 in full working order and changed nothing myself. Do not know why
it liked the Debian version from days gone by really but just reporting the outcome.
Maybe it resolves dependencies better. If someone nows for sure chime in. All I can tell
you is it works in VMware from Maverick to Natty without a hitch.

---

### Post by Jarret on 2011-05-26
If someone ends up at this thread experiencing the issue with VMWare Workstation, you have to edit the file "/usr/bin/vmware" in addition to "/usr/bin/vmplayer" 

So add "export LD_PRELOAD=/usr/lib/vmware/lib/libglib-2.0.so.0/libglib-2.0.so.0" after the copyright notice in both and you should be good to go.

This problem was driving me nuts all day..

---

### Post by snempaa on 2011-06-30
I tried all the above options, but it didn't help a thing. Reinstalled vmware-workstation, no luck too. I was getting pretty annoyed at this time, especially since it's not free software, but at the end of the night I found out what was the cause of the problem. My hardware is Thinkpad Edge 11 and I had a tv connected through HDMI. 
I already disabled all other external hardware, but never thought an extra monitor would be the problem. So when I finally wanted to go to bed I disconnected the HDMI and all VM's booted like a charm! Tried it again with tv connected and it failed again. So... no more tv series while working in a VM for me!

---

### Post by McFarlander on 2011-07-10
Thanks so much for this thread; this has been vexing me for a while now!
> **snempaa said:**
> ...So when I finally wanted to go to bed I disconnected the HDMI and all VM's booted like a charm! Tried it again with tv connected and it failed again. So... no more tv series while working in a VM for me!
Thanks snempaa!  As crazy as this sounds, you are absolutely correct.  With an HDMI monitor, the VM's just do not work.  All kinds of crazy problems!  Remove the HDMI monitor, connect a VGA monitor, and magically, the Virtual Machines all work just fine.  Plug the HDMI monitor back in, and once again, the VM's quit working?

Does anyone have any idea why an HDMI monitor seems to break VMWare under Ubuntu 11.04?  Is there a known fix or workaround?

Should this be a new thread?  This is a little different than the initial:
 "export LD_PRELOAD=/usr/lib/vmware/lib/libglib-2.0.so.0/libglib-2.0.so.0"
issue.

---

### Post by need_help_ on 2011-08-03
> **myth001 said:**
> [http://developers-developers-developers.blogspot.com/2011/04/ubuntu-1104-vmware-player-dies-when.html]("http://developers-developers-developers.blogspot.com/2011/04/ubuntu-1104-vmware-player-dies-when.html")

Quote:

To fix this, you have to tell VMWare Player to use its own glib: Insert the line

    export LD_PRELOAD=/usr/lib/vmware/lib/libglib-2.0.so.0/libglib-2.0.so.0

into the file /usr/bin/vmplayer - right after the copyright notice. The Beginning of the file should now look as follows:

    #!/usr/bin/env bash
    #
    # Copyright 2005-2008 VMware, Inc.  All rights reserved.
    #
    # Wrapper for the real 'vmplayer' binary. Ensure that the
    # binary will find all the shared libraries it needs. If a shared
    # library is not available from any of the standard system-wide
    # locations, we provide it from the location where the VMware software
    # is installed.
    #
    export LD_PRELOAD=/usr/lib/vmware/lib/libglib-2.0.so.0/libglib-2.0.so.0
    set -e


Save the file and restart VMWare player - you should be back in business.
Eingestellt von Christopher Staerkel um 04:22
Diesen Post per E-Mail versenden BlogThis! In Twitter freigeben In Facebook freigeben Freigeben in Google Buzz
i am new to Ubuntu and have the same problem using VM player ... was trying to edit the file /usr/lib/vmware/lib/libglib-2.0.so.0/libglib-2.0.so.0 to insert the line mentioned above.. with gedit, office and did some online search but ended nowhere.. any help appreciated.. 

not sure if it is the right place to ask this basic Q! thanks

---

### Post by need_help_ on 2011-08-03
i think i found the issue myself.. as simple as this that.. i am not editing the right file..! it is the text file i need to edit and not the .SO file! need to read better next time...

---

### Post by dliouville on 2011-08-11
Hi,

I've exactly the same issue. I use a samsung 900x3a and the only external monitor capabilities is via HDMI output, I've a samsung F2380 with HDMI input and vmware refuse to boot when HDMI is connected. Everything work fine without HDMI connected.

Did you solve this issue ?

---

### Post by dliouville on 2011-08-11
> **McFarlander said:**
> Thanks so much for this thread; this has been vexing me for a while now!

Thanks snempaa!  As crazy as this sounds, you are absolutely correct.  With an HDMI monitor, the VM's just do not work.  All kinds of crazy problems!  Remove the HDMI monitor, connect a VGA monitor, and magically, the Virtual Machines all work just fine.  Plug the HDMI monitor back in, and once again, the VM's quit working?

Does anyone have any idea why an HDMI monitor seems to break VMWare under Ubuntu 11.04?  Is there a known fix or workaround?

Should this be a new thread?  This is a little different than the initial:
 "export LD_PRELOAD=/usr/lib/vmware/lib/libglib-2.0.so.0/libglib-2.0.so.0"
issue.

Hi,

I've exactly the same issue. I use a samsung 900x3a and the only  external monitor capabilities is via HDMI output, I've a samsung F2380  with HDMI input and vmware refuse to boot when HDMI is connected.  Everything work fine without HDMI connected.

Did you solve this issue ?

---

### Post by dcstar on 2011-09-23
VMWare Player 4 (free) is now available as part of the (non-free) VMWare Workstation 8 download.

You simply uninstall your old VMWare Player and then do the full Workstation install and ignore the Workstation by just running Player:

```
vmplayer
```

This may now fix some issues, give it a try.

---

