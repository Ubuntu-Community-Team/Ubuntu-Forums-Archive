---
title: "Transparency in VirtualBox 3.0 window."
date: 2009-07-02
forum: Virtualisation
---

### Post by irv on 2009-07-02
Is any one else having a problem with transparent window in VirtualBox 3.0. I am not sure how to turn it off or fix it? Here is a screen shot of my desktop.
[ATTACH]119745[/ATTACH]
See how bad it looks. It is hard to see anything in it because of my background on my desktop. Is there a way to turn the transparency off?
Thanks

---

### Post by bowens44 on 2009-07-02
that happened to me too after upgrading to 3.0 I rebooted my PC and it no longer happened. Not a great solution but it worked for me.

---

### Post by irv on 2009-07-02
> **bowens44 said:**
> that happened to me too after upgrading to 3.0 I rebooted my PC and it no longer happened. Not a great solution but it worked for me.

I've rebooted and it is still there. I am not sure if it has anything to do with CompizConfig settings, but I couldn't see anything there that would do this. And it is only the VirtualBox that is effected with transparency.

---

### Post by irv on 2009-07-02
The only work around I can find is if I make my background black. See screen shot.
[ATTACH]119752[/ATTACH]

---

### Post by Killerah on 2009-07-02
I had the same problem, here's how I fixed it: 
1. Open up ccsm (if you don't have it install it using "sudo apt-get install compizconfig-settings-manager")
2. Go to "Window Rules" (and make sure it's enabled)
3. In the "No ARGB Visuals" box put the following without quotes "class=VirtualBox"
4. Hit back, close ccsm, and open up VirtualBox.

It worked like a charm for me, hope it works for you too.

Nate

---

### Post by irv on 2009-07-02
> **Killerah said:**
> I had the same problem, here's how I fixed it: 
1. Open up ccsm (if you don't have it install it using "sudo apt-get install compizconfig-settings-manager")
2. Go to "Window Rules" (and make sure it's enabled)
3. In the "No ARGB Visuals" box put the following without quotes "class=VirtualBox"
4. Hit back, close ccsm, and open up VirtualBox.

It worked like a charm for me, hope it works for you too.

Nate
In step #3 "In the 'No ARGB Visuals'" I am not sure where this is.
I hope I don't sound to dumb!
Edit: Never mind, I figured it out. (Maybe not so dumb after all)

---

### Post by Killerah on 2009-07-02
Did it work for ya then?

---

### Post by slob_2006 on 2009-07-02
it worked for me! 

thank you! :)

---

### Post by irv on 2009-07-02
> **Killerah said:**
> Did it work for ya then?

Yes it did. Thanks you very much.  
I sent this fix to Full Circle Magazine, but I gave you credit for the fix.
Great fix, I hope it will help others.

---

### Post by Killerah on 2009-07-03
I hope so too, I can't take credit for it though, I got it from somewhere else out there on the internet (though I can't find it right now for some reason). So whoever you are that first figured this out, we're all thankful to you.

Nate

---

### Post by Daniel_le_Rouge on 2009-07-03
I have the same problem, but you solution via compiz manager did not work for me. I also installed the guest additions for the new version, but everything which was transparent is black right now.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=119874&stc=1&d=1246661925[/IMG]

Does anybody know a solution for this problem?

Thanks a lot!

---

### Post by irv on 2009-07-03
I have been on the VirtualBox forum and there are others having this same problem you are having. You may want to check it out:
Here is the link: [http://forums.virtualbox.org/viewforum.php?f=7]("http://forums.virtualbox.org/viewforum.php?f=7")

---

### Post by lsemmens on 2009-07-04
Worked a treat for me. Thanks!

---

### Post by Daniel_le_Rouge on 2009-07-04
Here we go for the fix: [http://forums.virtualbox.org/viewtopic.php?f=2&t=17823#p84267]("http://forums.virtualbox.org/viewtopic.php?f=2&t=17823#p84267")

---

### Post by benrb on 2009-07-04
What worked for me was to start VB from the command line like this:
```

export XLIB_SKIP_ARGB_VISUALS=1 && VirtualBox

```

How can one set the environment variable XLIB_SKIP_ARGB_VISUALS=1 for the menu item: Applications -> System Tools -> Sun VirtualBox so that you can start VB with a mouse click?

I tried editing the command by placing:
"export XLIB_SKIP_ARGB_VISUALS=1 && VirtualBox" (without quotes) into System -> Preferences -> Main Menu -> System Tools -> Sun VirtualBox -> Properties -> Command
... but no luck.

---

### Post by Daniel_le_Rouge on 2009-07-04
Hi!

I saved the following code into /opt/virtualbox.sh and replaced the command by "sh /opt/virtualbox.sh" (without quotes). This worked out fine!

```
!/bin/bash
export XLIB_SKIP_ARGB_VISUALS=1
VirtualBox
```

---

### Post by benrb on 2009-07-04
> **Daniel_le_Rouge said:**
> Hi!

I saved the following code into /opt/virtualbox.sh and replaced the command by "sh /opt/virtualbox.sh" (without quotes). This worked out fine!

```
!/bin/bash
export XLIB_SKIP_ARGB_VISUALS=1
VirtualBox
```

Excellent! Just what I was looking for. However, the first line should read:
#!/bin/bash

Thanks again for your help.

---

### Post by quiche on 2009-07-06
thanks :p

---

### Post by raynix on 2009-07-07
> **Killerah said:**
> I had the same problem, here's how I fixed it: 
1. Open up ccsm (if you don't have it install it using "sudo apt-get install compizconfig-settings-manager")
2. Go to "Window Rules" (and make sure it's enabled)
3. In the "No ARGB Visuals" box put the following without quotes "class=VirtualBox"
4. Hit back, close ccsm, and open up VirtualBox.

It worked like a charm for me, hope it works for you too.

Nate

It works for me too! Thanks!:p

---

### Post by felixnine on 2009-07-07
rock solid. thanks!

as a temporary workaround, just enable the remote desktop server on the vm (from virtualbox, not the os) and connect to it from your host. if you're using ubuntu's terminal server client, make sure you pick the rdpv5 protocol.

---

### Post by jeff419 on 2009-07-10
> **Killerah said:**
> I had the same problem, here's how I fixed it: 
1. Open up ccsm (if you don't have it install it using "sudo apt-get install compizconfig-settings-manager")
2. Go to "Window Rules" (and make sure it's enabled)
3. In the "No ARGB Visuals" box put the following without quotes "class=VirtualBox"
4. Hit back, close ccsm, and open up VirtualBox.

It worked like a charm for me, hope it works for you too.

Nate

Worked perfect for me, thanks!

---

