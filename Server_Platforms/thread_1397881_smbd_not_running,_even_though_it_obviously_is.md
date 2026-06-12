---
title: "smbd not running, even though it obviously is"
date: 2010-02-03
forum: Server Platforms
---

### Post by will_in_houston on 2010-02-03
Here's the background info -- I recently installed Ubuntu server 8.04 on TWO machines that are exactly identical.

On one machine, all seems perfect.  On the other, when I execute "/etc/init.d/samba status" it always shows that smbd is NOT running.

But it would seem that it IS running, since I can access the shares I've set up without difficulty either from smbclient on the server or from the windows boxes on the network.

ps ax lists smbd as a process as well.

The log tells me nothing -- it just reports that samba started.  No errors.  Not much of anything in there.

And if I execute smbstatus, that works just like you'd expect.

Confused about the source of this, since the two machines are identical (and I mean exactly the same), and only one is doing this.

I guess I should be happy since they both work (seemingly perfectly).  But it still bothers me that I'm getting the message that smbd isn't running on one of them.

Anyone else seen this?  I tried uninstalling samba and reinstalling it on the machine giving me the erroneous (?) status message.  But that changed nothing.

Right now there's no data on the machine, and it's not in production, so just doing a bare metal reinstall of the OS is an option.  But I'd like to understand what's happening.

Any help?

---

### Post by ant2ne on 2010-02-03
I gotta ask.. can you access the samba shares?

---

### Post by capscrew on 2010-02-04
> **will_in_houston said:**
> Here's the background info -- I recently installed Ubuntu server 8.04 on TWO machines that are exactly identical.

On one machine, all seems perfect.  On the other, when I execute "/etc/init.d/samba status" it always shows that smbd is NOT running.

But it would seem that it IS running, since I can access the shares I've set up without difficulty either from smbclient on the server or from the windows boxes on the network.

ps ax lists smbd as a process as well.

The log tells me nothing -- it just reports that samba started.  No errors.  Not much of anything in there.

And if I execute smbstatus, that works just like you'd expect.

Confused about the source of this, since the two machines are identical (and I mean exactly the same), and only one is doing this.

I guess I should be happy since they both work (seemingly perfectly).  But it still bothers me that I'm getting the message that smbd isn't running on one of them.

Anyone else seen this?  I tried uninstalling samba and reinstalling it on the machine giving me the erroneous (?) status message.  But that changed nothing.

Right now there's no data on the machine, and it's not in production, so just doing a bare metal reinstall of the OS is an option.  But I'd like to understand what's happening.

Any help?

I'll bet it is [**_[COLOR="Navy"]this bug[/COLOR]_**]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=488275").

---

### Post by will_in_houston on 2010-02-04
In reply to ant2ne -- yes I can access the shares.  Everything is working perfectly.  Just the status is being reported incorrectly.

In reply to Capscrew -- Thanks, that bug looks like a definite possibility as the cause of this.  Right now I don't have anything that requires a correct response for the status, so this might not be a big deal.

But I'll investigate some more to determine is that bug is in fact the cause.

Thanks for your help!

Will

---

### Post by Iowan on 2010-02-04
FWIW, I just checked my 8.04 Samba server - sure enough, **/etc/init.d/samba status** yields "* SMBD is not running".

---

### Post by will_in_houston on 2010-02-04
Iowan --

Ok, so it's not just my machine.

But if it's a bug in 8.04, I guess I'm puzzled why it's only affecting one of the machines I installed on -- identical hardware, same install options, same install media (CD).

Strange.

Clearly it's just an error in reporting the status.

I'll keep investigating and see if I can come to a definite conclusion/solution.

When I figure it out, I'll post back and let you all know what I came up with.  Sounds like the bug linked to in a previous post, but I haven't yet had a chance to really dissect that info yet.

Thanks for everyone's interest and help.

Will

---

