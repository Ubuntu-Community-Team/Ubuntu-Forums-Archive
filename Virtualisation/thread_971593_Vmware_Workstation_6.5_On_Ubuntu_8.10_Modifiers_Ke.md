---
title: "Vmware Workstation 6.5 On Ubuntu 8.10 Modifiers Keys Not Working"
date: 2008-11-05
forum: Virtualisation
---

### Post by tazpsychodad on 2008-11-05
Hello, 

i've just installed Ubuntu 8.10 and Vmware Workstation 6.5 and the modifiers keys do not work when I'm working on the guest machine. 

The end, home, delete, ... keys simply don't work. The arrow down key yields the start menu...

Help me!!!

TAzPsychoDad

---

### Post by paledread on 2008-11-05
> **tazpsychodad said:**
> Hello, 

i've just installed Ubuntu 8.10 and Vmware Workstation 6.5 and the modifiers keys do not work when I'm working on the guest machine. 

The end, home, delete, ... keys simply don't work. The arrow down key yields the start menu...

Help me!!!

TAzPsychoDad
Ditto with Ubuntu 8.10 and NXClient logging in to a remote machine. The keys work OK on the host machine.

On the remote machine under NXClient the end, home, delete and the up/down/left/right arrow keys are not working.

All was working well until the 8.10 upgrade.

---

### Post by sles on 2008-11-06
I have the same problem, and my colleagues too , but we don't know how to fix.. :-(

---

### Post by Steely1 on 2008-11-06
Same problem here-- it's so frustrating!  Also running (k)ubuntu 8.10 and VMWare Workstation 6.5.  I happen to be on an Intel iMac.  Have tried two different USB keyboards, an Apple Pro Keyboard and a generic Logitech 104-key.  

I will see if I can get any traction with VMWare support and post back here if I learn anything.

**UPDATE: **
Found the workaround on the VMWare forums [here]("http://communities.vmware.com/thread/177688"): 
> echo 'xkeymap.nokeycodeMap = true' > ~/.vmware/config

You can also (sudo) edit the global config at /etc/vmware/config for the change to affect all users.

The fix worked fine for me.

---

### Post by sles on 2008-11-06
Are there solution for nxclient or qtnx?

---

### Post by x001 on 2008-11-15
> **Steely1 said:**
> 

Found the workaround on the VMWare forums [here]("http://communities.vmware.com/thread/177688"): 

You can also (sudo) edit the global config at /etc/vmware/config for the change to affect all users.



This worked for me as well. Thank you.

---

### Post by Phkillah on 2008-11-16
I also fixed my arrow keys with this... However my Portuguese layout is all screwed :S

Any Portuguese guy has tested this? Algum Português testou isto? :)

Cheers

---

### Post by Freaky_Llama on 2008-11-18
This also affects the 2X application server client. Of all the config files I can find for 2X, I cannot find where to set keyboard maps.

It worked fine yesterday when I was still using 8.04. Today with 8.10 I have this issue.

I have tried all of the fixes out there remotely related to this issue. Since vmware was never installed or configured on this machine, there has to be either A) Somewhere that these other tsclients are pulling their configs from, or B) somewhere to define for the tsclients what the config is. 

I have also tried multiple versions of the appserverclient from 2x with no joy. 8.10 is as updated as I can get it. The issue doesn't exist in Ubuntu or via a regular Terminal Server Client connection, which points to a rogue system setting, or an application specific setting.

Here's the post I made at the 2X forums:

> Was working in Ubuntu 8.04 with 6.1.
Server: VMWare running Windows Server 2003 SP2 | Using appserver 6.1
Client: Dell Latitude D630 running Ubuntu 8.10.
Issue exists in Linux clients 4.3 and 6.1. Issue does not exist in 4.3 or 6.1 if using Ubuntu 8.04

Issue: Using the keyboard to navigate in any appserverclient applications (Outlook 2007, excel 2007, Internet Explorer 6, and desktop connection) the down arrow will either not do anything, or will open the start menu (if viewing desktop). The left arrow is "alt" and the up and right arrows do nothing. Keys that also do nothing: insert, delete, home, end, page up. Page Dn opens a menu of sorts, depending on the program.

All of the keys work inside of Ubuntu itself as well as through a non-2X Terminal Server Client app.

Right alt opens email in outlook.
Right ctrl jumps down 6 lines (page dn?).
Prnt Scrn deletes.

All letter, number, punctuation, and function keys work properly.

Plainly, I need to find out how/where 2X defines or retrieves its keyboard map.

---

### Post by jonofan on 2008-11-25
Fixed for me too. Only thing that doesn't work is the Caps Lock light on the keyboard. Caps lock button still works though.

---

### Post by tazpsychodad on 2008-11-26
Worked perfect for me, simple, elegant, efficient, ...

---

### Post by PilotJLR on 2008-11-29
[COLOR="DarkRed"]**WARNING**: The [FONT="Courier New"]'xkeymap.nokeycodeMap = true'[/FONT] configuration breaks the Unity feature![/COLOR]

As a solution... delete that line from whichever conf file you had modified, and instead add this:

```

xkeymap.keycode.108 = 0x138 # Alt_R
xkeymap.keycode.106 = 0x135 # KP_Divide
xkeymap.keycode.104 = 0x11c # KP_Enter
xkeymap.keycode.111 = 0x148 # Up
xkeymap.keycode.116 = 0x150 # Down
xkeymap.keycode.113 = 0x14b # Left
xkeymap.keycode.114 = 0x14d # Right
xkeymap.keycode.105 = 0x11d # Control_R
xkeymap.keycode.118 = 0x152 # Insert
xkeymap.keycode.119 = 0x153 # Delete
xkeymap.keycode.110 = 0x147 # Home
xkeymap.keycode.115 = 0x14f # End
xkeymap.keycode.112 = 0x149 # Prior
xkeymap.keycode.117 = 0x151 # Next
xkeymap.keycode.78 = 0x46 # Scroll_Lock
xkeymap.keycode.127 = 0x100 # Pause
xkeymap.keycode.133 = 0x15b # Meta_L
xkeymap.keycode.134 = 0x15c # Meta_R
xkeymap.keycode.135 = 0x15d # Menu

```

Then restart the vmware service...


After making this change, your modifier keys should work, and Unity should as well.

I had previously made this one-line change, but only today realized that Unity was no longer working. I can't take credit for this info... reference here:
[http://communities.vmware.com/thread/180137](http://communities.vmware.com/thread/180137)

Hope this helps.

---

### Post by johnswb on 2008-12-04
After doing  > echo 'xkeymap.nokeycodeMap = true' > ~/.vmware/config my arrow keys started working but now the "Unity" no longer works.  The start menu shows up but I'm unable to open anything nor can I exit out of "Unity".  I just get a blank screen when I bring the window up. Going to try PilotJLR suggestion.

---

### Post by johnswb on 2008-12-04
I give PilotJLR the any credit I have because I found yours first and it worked for me.  thx  

Now if I could only get compiz to work at the same time and not crash.

---

### Post by Magneto on 2008-12-06
> **Steely1 said:**
> Same problem here-- it's so frustrating!  Also running (k)ubuntu 8.10 and VMWare Workstation 6.5.  I happen to be on an Intel iMac.  Have tried two different USB keyboards, an Apple Pro Keyboard and a generic Logitech 104-key.  

I will see if I can get any traction with VMWare support and post back here if I learn anything.

**UPDATE: **
Found the workaround on the VMWare forums [here]("http://communities.vmware.com/thread/177688"): 

You can also (sudo) edit the global config at /etc/vmware/config for the change to affect all users.

The fix worked fine for me.
Thanks for that.

---

### Post by el_morsa on 2008-12-11
Thanks for the helpful post! A few additions for spanish latin american keyboards:

xkeymap.keycode.20 = 0x00c # apostrophe
xkeymap.keycode.21 = 0x0d # questiondown
xkeymap.keycode.61 = 0x035 # minus
xkeymap.keycode.34 = 0x01a # dead_acute
xkeymap.keycode.35 = 0x01b # plus
xkeymap.keycode.99 = 0x137 # Print_Screen


Cheers!

---

### Post by mie on 2009-01-21
and this is for fixing the "Print Screen" key on my German keyboard, which is mapped to the "Del" key, add this to your vmware config file (tested for /etc/vmware/config):

xkeymap.keycode.107 = 0x137 # Print Scrn

see:
[http://www.vmware.com/support/ws5/doc/ws_devices_keymap_linux_longer.html](http://www.vmware.com/support/ws5/doc/ws_devices_keymap_linux_longer.html)
[http://www.vmware.com/support/ws5/doc/ws_devices_keymap_vscan.html](http://www.vmware.com/support/ws5/doc/ws_devices_keymap_vscan.html)

---

### Post by prkos on 2009-01-21
thank you for the fix 
```
echo 'xkeymap.nokeycodeMap = true' > ~/.vmware/config 
```
worked for me, although not for croatian characters

---

### Post by prkos on 2009-03-11
> **PilotJLR said:**
> 
```

xkeymap.keycode.108 = 0x138 # Alt_R
xkeymap.keycode.106 = 0x135 # KP_Divide
xkeymap.keycode.104 = 0x11c # KP_Enter
xkeymap.keycode.111 = 0x148 # Up
xkeymap.keycode.116 = 0x150 # Down
xkeymap.keycode.113 = 0x14b # Left
xkeymap.keycode.114 = 0x14d # Right
xkeymap.keycode.105 = 0x11d # Control_R
xkeymap.keycode.118 = 0x152 # Insert
xkeymap.keycode.119 = 0x153 # Delete
xkeymap.keycode.110 = 0x147 # Home
xkeymap.keycode.115 = 0x14f # End
xkeymap.keycode.112 = 0x149 # Prior
xkeymap.keycode.117 = 0x151 # Next
xkeymap.keycode.78 = 0x46 # Scroll_Lock
xkeymap.keycode.127 = 0x100 # Pause
xkeymap.keycode.133 = 0x15b # Meta_L
xkeymap.keycode.134 = 0x15c # Meta_R
xkeymap.keycode.135 = 0x15d # Menu

```

Then restart the vmware service...

I just tried this instead of the one line solution in ~/.vmware/config and all my croatian keys work! I wish I had tried this earlier...

---

### Post by joeycbulk on 2009-03-24
> **PilotJLR said:**
> [COLOR="DarkRed"]**WARNING**: The [FONT="Courier New"]'xkeymap.nokeycodeMap = true'[/FONT] configuration breaks the Unity feature![/COLOR]

As a solution... delete that line from whichever conf file you had modified, and instead add this:

```

xkeymap.keycode.108 = 0x138 # Alt_R
xkeymap.keycode.106 = 0x135 # KP_Divide
xkeymap.keycode.104 = 0x11c # KP_Enter
xkeymap.keycode.111 = 0x148 # Up
xkeymap.keycode.116 = 0x150 # Down
xkeymap.keycode.113 = 0x14b # Left
xkeymap.keycode.114 = 0x14d # Right
xkeymap.keycode.105 = 0x11d # Control_R
xkeymap.keycode.118 = 0x152 # Insert
xkeymap.keycode.119 = 0x153 # Delete
xkeymap.keycode.110 = 0x147 # Home
xkeymap.keycode.115 = 0x14f # End
xkeymap.keycode.112 = 0x149 # Prior
xkeymap.keycode.117 = 0x151 # Next
xkeymap.keycode.78 = 0x46 # Scroll_Lock
xkeymap.keycode.127 = 0x100 # Pause
xkeymap.keycode.133 = 0x15b # Meta_L
xkeymap.keycode.134 = 0x15c # Meta_R
xkeymap.keycode.135 = 0x15d # Menu

```

Then restart the vmware service...


After making this change, your modifier keys should work, and Unity should as well.

I had previously made this one-line change, but only today realized that Unity was no longer working. I can't take credit for this info... reference here:
[http://communities.vmware.com/thread/180137](http://communities.vmware.com/thread/180137)

Hope this helps.


Thanks! This worked for me:p

---

### Post by geerm on 2009-05-14
> **Steely1 said:**
> Same problem here-- it's so frustrating!  Also running (k)ubuntu 8.10 and VMWare Workstation 6.5.  I happen to be on an Intel iMac.  Have tried two different USB keyboards, an Apple Pro Keyboard and a generic Logitech 104-key.  

I will see if I can get any traction with VMWare support and post back here if I learn anything.

**UPDATE: **
Found the workaround on the VMWare forums [here]("http://communities.vmware.com/thread/177688"): 

You can also (sudo) edit the global config at /etc/vmware/config for the change to affect all users.

The fix worked fine for me.

has anyone tried this on the vmware server/, i was having this problem, ran the command and i was prety hapy to be able to use the vm with all the keys.... but now the host machine modifiers are broken when vm is up. so that just switched the problem's location :frown:

---

### Post by noex869 on 2009-11-19
I have tried> **Steely1 said:**
> 
Found the workaround on the VMWare forums [here]("http://communities.vmware.com/thread/177688"): 

You can also (sudo) edit the global config at /etc/vmware/config for the change to affect all users.

The fix worked fine for me. on vmware server and it works for me, but occasionally it does break the hosts ability to use the ctrl key.  My quick fix is to goto system -> prefenses -> keyboard -> layout and change it to something random and change it back to my keyboard layout; gets my ctrl, shift, alt and caps lock working on the host and vms.  Again quick fix, I'm sure there is a better way to do this, Hope this helps

---

