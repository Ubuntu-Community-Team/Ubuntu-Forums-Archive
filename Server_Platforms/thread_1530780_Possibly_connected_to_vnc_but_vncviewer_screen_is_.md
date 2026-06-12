---
title: "Possibly connected to vnc but vncviewer screen is black"
date: 2010-07-14
forum: Server Platforms
---

### Post by yc2 on 2010-07-14
I regularly use Putty to vnc into my Ubuntu desktop, it works fine.

An elderly couple wants to learn Ubuntu and wants me to remote vnc into their desktop. (They use Lucid/vino-server, like I do.)

Settings for their remote desktop are the same as in my computer (allow others to control your computer, use password, do not require confirmation, show an icon when others log on ...)

SSH into their computer is fine.

I SSH with the appropriate settings for vnc (L5900 127.0.0.1:5900) and compression into their computer, this is OK.

When I open vncviewer (127.0.0.1) it seems like the password is accepted but I only see a black screen. I see the two pointers (the square and the lagging arrow) But all is black. (In vncviewer options I try to set the option "best color scheme")

(They have an ATI card. As I understand they seem to need proprietary drivers, otherwise resolution is low.)

On this occasion I only have access to Windows-Putty, so please give help according to this. (I once could try via Ubuntu terminal ssh and Ubuntu vnc-viewer, that time my impression was that pwd was maybe not accepted ???)

Very thankful for advice.


EDIT: I just had the opportunity to ssh from another Ubuntu system into my firends' computer, set up for vnc, I get some errors that may be helpful? (ssh then works, but vnc screen is black)
Please check this ssh logging, thanks.

$ ssh -L 5900:localhost:5900 [email]FOO@XXX.XXX.XXX.XXX[/email]
[email]FOO@XXX.XXX.XXX.XXX[/email]'s password: 
bind: Address already in use
channel_setup_fwd_listener: cannot listen to port: 5900
Could not request local forwarding.
Linux ubuntu 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
Ubuntu 10.04 LTS

---

### Post by yc2 on 2010-07-29
Finally got this one solved.

_Disabling desktop effects_ in the vino server Ubuntu system made vnc work.

Thread solved.

---

