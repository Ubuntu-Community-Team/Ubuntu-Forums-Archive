---
title: "Information incorrectly leaking from host to guests?"
date: 2024-05-08
forum: Virtualisation
---

### Post by undecidable on 2024-05-08
Whenever I select text with the mouse in a host, each guest running in that hosts gets many system log / journald log messages:

```
localhost spice-vdagent[1039]: vdagent_clipboard_data: sel_id=1: no corresponding request found for type=1, skipping
```
and
```
localhost spice-vdagent[1039]: message repeated 92 times: [ vdagent_clipboard_data: sel_id=1: no corresponding request found for type=1, skipping]
```
Note the 92 times!

Key points:
[LIST=1]
[*]  Happens when select I text in a window in the host, even if on a different virtual desktop to the guest;
[*]  *The messages appear immediately in all guests that are running at the time;*
[*]  It only happens when I select text in gtk apps (eg gedit, mousepad, zim) not qt apps (eg kwrite).
[*]  It doesnt happen when select text in a guest - the message doesnt appear in the host or in other guests.
[/LIST]

I have set, but it makes no difference.
	<filetransfer enable='no'/>
Of course setting clipboard copypaste to no will kill the messages but also the funtionality:
	<clipboard copypaste="no"/> 

I'm using Xubuntu 22.04, guest kernel 6.5.0-28, host kernels 6.5.0-28 and 5.15.0-105,
qemu-system-x86 6.2, libvirt 8.0.0, libspice-vdagent 0.22.1, spice-client-gtk-3.0-5
	
My main concern is that anything I select in the host* is being leaked from the host to all the guests*,
when in fact the information selected should only be made available to the guest when the cursor moves to 
and is captured by the guest, and only to that guest, not all guests.  
The guests should not be watching the host.

A less important issue is that my system logs / journalctl are being filled with these messages
and it is obviously an error of some form.

Is anyone else seeing the same problem?

---

### Post by MAFoElffen on 2024-05-08
Is this when interacting with your VM locally, or remotely?

I don't know that "that" is really a problem, per-say...

The open-vm-tools provide sharing services between the VM and where you are viewing it from with your viewer. That would cause log entries.

But then again, repeated 92 times would be considered as spam entries, rather than just a simple notification... Maybe you should gather your data, and report it as a Bug Report, for LaunchPad to look into it further. Remember to stress noting it as "spam entries" into the logs. Maybe even in the Title of the Bug Report, so that it catches their attention.

That would be the right thing to do... That is what I would do.

Post the link to the Bug Report here. When I get back tonight, I test it on mine, and if I can recreate it, I'll join the report, as also affected. That will toggle the status from 'new' to 'confirmed' and give it more weight.

---

### Post by undecidable on 2024-05-09
> Is this when interacting with your VM locally, or remotely?
I only use local access.  

> I don't know that "that" is really a problem, per-say...
hmm, seems all these years I've misunderstood the security profile of the clipboard.
I had assumed that the contents of the host / guest clipboard
would only be visible to the guest / host 
when the cursor entered the others territory and it gained focus.  

From your remarks, and some more testing I did this morning
it seems it really is a "shared clipboard" with unrestricted access. 

> But then again, repeated 92 times...
So the only remaining issue is the multiple messages - sometimes >100 in sequence.
The fact that they only occur with GTK apps, and from host to guest
suggests strongly it is a bug.

**Bug Report**
I'm usually reluctant to file a bug unless I see others have it
and I've exhausted all my own mis-configuration possibilities.  
(I did report a bug yesterday for the Daily Crashes issues, 
as I saw others had it and I had tested many config alternatives). 

A search on this error message runs up nothing - 0. 

If someone somewhere on the planet could confirm they have it, 
I'll file a bug report, otherwise I'll test a few more days
to see if I have done anything else wrong.

_Key information latest on when the messages spill out:_
[LIST=1]
[*]Happens when I select text in a window in the host, even if on a different virtual desktop to the guest;
[*]The messages appear in all guests that are running at the time;
[*]It only happens when I select text in gtk apps (eg gedit, mousepad, zim) not QT apps (eg kwrite), though mouse selection / middle click paste works fine in QT apps.;
[*]It doesn't happen when I select with the kbd (ctrl-shift-right_arrow);
[*]It doesnt happen when select text in a guest - the message doesnt appear in the host or in other guests.
[/LIST]


btw, its much easier to see in a journalctl window 
```
journalctl -f
```
rather than a
```
tail -F /var/log/syslog
```
as syslog combines them with a "message repeated 96 times"
whereas journalctl spills them 1 by 1.

---

### Post by undecidable on 2024-05-14
Logged a launchpad bug here:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-qxl/+bug/2065653](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-qxl/+bug/2065653)

title:
text selection in host spawns multiple error messages in guests

---

