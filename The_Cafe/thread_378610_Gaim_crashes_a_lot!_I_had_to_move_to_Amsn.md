---
title: "Gaim crashes a lot! I had to move to Amsn"
date: 2007-03-07
forum: The Cafe
---

### Post by Gargamella on 2007-03-07
I like very much Gaim because of its support for many networks (as irc,msn and yahoo at the same time for example), 

anyway it often crashes me when some msn contacts chat with me. Does it happen also to you?

I had to move to Amsn, it has a lot of functions but I think I like more Gaim (more likely, and better GTK integration).


What do you think about it?

---

### Post by futz on 2007-03-07
> **Gargamella said:**
> I like very much Gaim because of its support for many networks (as irc,msn and yahoo at the same time for example), 

anyway it often crashes me when some msn contacts chat with me. Does it happen also to you?

I had to move to Amsn, it has a lot of functions but I think I like more Gaim (more likely, and better GTK integration).


What do you think about it?
Odd. I don't think it's ever crashed for me, and I use it quite a bit. Try a newer/older version? I always run the newest one.

---

### Post by Gargamella on 2007-03-07
> **futz said:**
> I always run the newest one.

Me too, but I always had that problem when using it in each version by a year

---

### Post by Bragador on 2007-03-07
I'm running the version that comes with Edgy and I have absolutely no problem speaking with friends on the MSN messenger network.

I'm not sure what's going on here but ask them what they were doing while you were crashing. Perhaps it's a certain animation or option that makes your client crash...

---

### Post by Onyros on 2007-03-07
A few users have had that very problem, while chatting with Messenger Live contacts.

It happened to me as well, until I upgraded to GAIM 2.0.0beta6 and it never happened again!

So try it out, don't quit on GAIM yet :)

---

### Post by compwiz18 on 2007-03-07
I believe it will crash if you are talking to or have any "bots" on your contact list...I used to have this problem, and removing the "bots" fixed it.

---

### Post by IYY on 2007-03-07
It happened on our school workstations when we were using the old version. The latest beta fixed it.

---

### Post by uantuzri on 2007-03-08
I have the same problem, both with MSN and IRC. I also tried another version, but that didn't fix it. Now I use amsn and konversation. Two aps, but at least they don't crash...

---

### Post by RAV TUX on 2007-03-08
> **Gargamella said:**
> I like very much Gaim because of its support for many networks (as irc,msn and yahoo at the same time for example), 

anyway it often crashes me when some msn contacts chat with me. Does it happen also to you?

I had to move to Amsn, it has a lot of functions but I think I like more Gaim (more likely, and better GTK integration).


What do you think about it?
GAIM has never crashed on me but I prefer Kopete.

---

### Post by RAV TUX on 2007-03-08
> **uantuzri said:**
> I have the same problem, both with MSN and IRC. I also tried another version, but that didn't fix it. Now I use amsn and konversation. Two aps, but at least they don't crash... I exclusively use Konversation for IRC and it has never crashed on me. I highly recommend Konversation.

---

### Post by Pikestaff on 2007-03-08
Gaim crashes on me a lot too :???: Certain plugins crash it; and even when not using any of the plugins it will just randomly quit on me, mid-conversation.  I'm using the newest version as far as I know.

I might be switching to Kopete, I'm not a huge fan of the interface but hopefully it won't crash like Gaim.

---

### Post by karellen on 2007-03-08
gaim works perfect for me, and I have quite a couple of accounts :D (3 yahoo, one gmail, 1 aim, 1 msn)

---

### Post by OneST8 on 2007-04-10
Gaim worked flawlessly for me until my recent Edgy upgrade from Dapper. Now, MSN (and only MSN) causes a segfault frequently.

I cannot stand the other IM clients out there and prefer my nicely [GNOME] integrated IM client. Plus, the 2.0beta is really nice and I'd rather not revert to 1.5 though I may just do that to test if it's functional or not.

I just installed gaim-dbg and ran it in gdb... here's the backtrace of a crash if it can help anyone help us poor gaim addicts.

```
$ gdb gaim
GNU gdb 6.4.90-debian
Copyright (C) 2006 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".

(gdb) run
Starting program: /usr/bin/gaim 
[Thread debugging using libthread_db enabled]
[New Thread -1220737360 (LWP 25030)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1220737360 (LWP 25030)]
0xb75e66a8 in strcmp () from /lib/tls/i686/cmov/libc.so.6
(gdb) bt
#0  0xb75e66a8 in strcmp () from /lib/tls/i686/cmov/libc.so.6
#1  0xb691f0ab in msn_session_find_slplink (session=0x8520d68, 
    who=0x8a07590 "fakename@hotmail.com")
    at ../../../../src/protocols/msn/slplink.c:138
#2  0xb691f2ec in msn_session_get_slplink (session=0x8520d68, 
    username=0x8a07590 "fakename@hotmail.com")
    at ../../../../src/protocols/msn/slplink.c:150
#3  0xb691cd95 in msn_p2p_msg (cmdproc=0x86e6b18, msg=0x8a248d0)
    at ../../../../src/protocols/msn/slp.c:741
#4  0xb690c623 in msn_cmdproc_process_msg (cmdproc=0x86e6b18, msg=0x8a248d0)
    at ../../../../src/protocols/msn/cmdproc.c:248
#5  0xb6920d74 in msg_cmd_post (cmdproc=0x86e6b18, cmd=0x8644198, 
    payload=0x8701804 "MIME-Version: 1.0\r\nContent-Type: application/x-msnmsgrp2p\r\nP2P-Dest: onest8@hotmail.com\r\n\r\n", len=1345)
    at ../../../../src/protocols/msn/switchboard.c:734
#6  0xb690c6dd in msn_cmdproc_process_payload (cmdproc=0x86e6b18, 
    payload=0x8701804 "MIME-Version: 1.0\r\nContent-Type: application/x-msnmsgrp2p\r\nP2P-Dest: onest8@hotmail.com\r\n\r\n", payload_len=1345)
    at ../../../../src/protocols/msn/cmdproc.c:223
#7  0xb691b928 in read_cb (data=0x863ab78, source=18, cond=GAIM_INPUT_READ)
    at ../../../../src/protocols/msn/servconn.c:433
#8  0x080fafe3 in gaim_gtk_io_invoke (source=0x863aec8, condition=G_IO_IN, 
    data=0x863dc50) at ../../src/gtkeventloop.c:74
---Type <return> to continue, or q <return> to quit---
#9  0xb78f6c8d in g_io_channel_unix_get_fd () from /usr/lib/libglib-2.0.so.0
#10 0xb78cd802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#11 0xb78d07df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#12 0xb78d0b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#13 0xb7c02574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#14 0x0810fd0c in main (argc=846686051, argv=0xbfdd1624)
    at ../../src/gtkmain.c:764

```

---

### Post by compwiz18 on 2007-04-11
> **OneST8 said:**
> Gaim worked flawlessly for me until my recent Edgy upgrade from Dapper. Now, MSN (and only MSN) causes a segfault frequently.

I cannot stand the other IM clients out there and prefer my nicely [GNOME] integrated IM client. Plus, the 2.0beta is really nice and I'd rather not revert to 1.5 though I may just do that to test if it's functional or not.

I just installed gaim-dbg and ran it in gdb... here's the backtrace of a crash if it can help anyone help us poor gaim addicts.

```
$ gdb gaim
GNU gdb 6.4.90-debian
Copyright (C) 2006 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".

(gdb) run
Starting program: /usr/bin/gaim 
[Thread debugging using libthread_db enabled]
[New Thread -1220737360 (LWP 25030)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1220737360 (LWP 25030)]
0xb75e66a8 in strcmp () from /lib/tls/i686/cmov/libc.so.6
(gdb) bt
#0  0xb75e66a8 in strcmp () from /lib/tls/i686/cmov/libc.so.6
#1  0xb691f0ab in msn_session_find_slplink (session=0x8520d68, 
    who=0x8a07590 "fakename@hotmail.com")
    at ../../../../src/protocols/msn/slplink.c:138
#2  0xb691f2ec in msn_session_get_slplink (session=0x8520d68, 
    username=0x8a07590 "fakename@hotmail.com")
    at ../../../../src/protocols/msn/slplink.c:150
#3  0xb691cd95 in msn_p2p_msg (cmdproc=0x86e6b18, msg=0x8a248d0)
    at ../../../../src/protocols/msn/slp.c:741
#4  0xb690c623 in msn_cmdproc_process_msg (cmdproc=0x86e6b18, msg=0x8a248d0)
    at ../../../../src/protocols/msn/cmdproc.c:248
#5  0xb6920d74 in msg_cmd_post (cmdproc=0x86e6b18, cmd=0x8644198, 
    payload=0x8701804 "MIME-Version: 1.0\r\nContent-Type: application/x-msnmsgrp2p\r\nP2P-Dest: onest8@hotmail.com\r\n\r\n", len=1345)
    at ../../../../src/protocols/msn/switchboard.c:734
#6  0xb690c6dd in msn_cmdproc_process_payload (cmdproc=0x86e6b18, 
    payload=0x8701804 "MIME-Version: 1.0\r\nContent-Type: application/x-msnmsgrp2p\r\nP2P-Dest: onest8@hotmail.com\r\n\r\n", payload_len=1345)
    at ../../../../src/protocols/msn/cmdproc.c:223
#7  0xb691b928 in read_cb (data=0x863ab78, source=18, cond=GAIM_INPUT_READ)
    at ../../../../src/protocols/msn/servconn.c:433
#8  0x080fafe3 in gaim_gtk_io_invoke (source=0x863aec8, condition=G_IO_IN, 
    data=0x863dc50) at ../../src/gtkeventloop.c:74
---Type <return> to continue, or q <return> to quit---
#9  0xb78f6c8d in g_io_channel_unix_get_fd () from /usr/lib/libglib-2.0.so.0
#10 0xb78cd802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#11 0xb78d07df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#12 0xb78d0b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#13 0xb7c02574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#14 0x0810fd0c in main (argc=846686051, argv=0xbfdd1624)
    at ../../src/gtkmain.c:764

```
Try gaim 2.0.0beta6 - I think it fixes the problem.

---

### Post by LookTJ on 2007-04-11
No, it never happens to me. Maybe it's because I don't use MSN? or...you're using Dapper?

---

### Post by 3rdalbum on 2007-04-11
I was using Gaim beta 4 on Dapper, but that often crashed while talking to MSN contacts.

So I switched to Kopete from the Dapper repos, and although it doesn't crash as much, *it crashes at the exact same time as another Kopete user on my MSN list*.

I'll try Gaim beta 6 if it installs, and see if that works.

---

### Post by Gargamella on 2007-04-11
I am an Edgy user with a Msn account and I also use IRC (just for #ubuntuforums ;D)
as told Pikestaff it quits often mid-conversation.

Don't know why it did it also in Dapper sometimes anyway I hope it is just a beta problem

---

### Post by EdThaSlayer on 2007-04-11
I don't like to use GAIM for that main reason, crashes once in a while if I'm logged into 2 networks. Thats why I use Amsn for MSN, and it also supports webcam along with many other nice goodies(plugins). :)

---

### Post by uggeli on 2007-04-11
I allso have similar problems with gaim (version in edgy) when I'm chatting in msn network. Usually gaim crashes when someone is sending me custom smiley. So nowdays I have amsn allso installed, but it looks damn ugly and doesn't integrate to gnome very well. I hope newer versions of gaim/pidgin have solved these problems (like it seems to be when reading these comments), but I check that out in feisty.

---

