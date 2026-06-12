---
title: "My 16-month old nephew hacked Lucid"
date: 2011-02-23
forum: The Cafe
---

### Post by P1C0 on 2011-02-23
I usually let my nephew play with the keyboard because it makes him very happy.
So today, as I normally do, I press ctrl + alt + L to lock the screen and I go in the kitchen for just a moment.

I come back and I see he has gone into text terminal mode, but the scary part is that in the password prompt I see sth like:
> [AAAAAAAAAAAAAAAAAAAAAAAAAAAAA[SIZE="5"]**mypasswordhere**[/SIZE]AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA

My password is >7 figures long with numbers and capital letters and stuff so obviously he did not press the buttons randomly, but somehow it came up in the terminal.
I honestly don't know how.

I found it hard to believe and unfortunately I did not take a picture of it. I'm trying to reproduce it, but I can't.

Is it possible? :popcorn:

---

### Post by cgroza on 2011-02-23
Thats how brute force attacks work.:)

---

### Post by eriktheblu on 2011-02-23
Copied to your clipboard perhaps?

---

### Post by whiskeylover on 2011-02-23
He's being controlled by the Matrix.

---

### Post by P1C0 on 2011-02-23
> **eriktheblu said:**
> Copied to your clipboard perhaps?No chance! Thinking about it, it was more than a crashed down graphical interface of the login screen that the proper text terminal mode you get by pressing ctrl + alt + f1 etc.
Additionally he could not have pressed a combination like ctrl + alt + f1 cause his hands are to small.

I tried to get back to the login screen with ctrl + alt + f7, but it was unresponsive (none of the f[1-7] did anything).
So I gave the username, the password, I did a sudo reboot and it was fine again. 

I will check the logs actually and see if it is any help.

---

### Post by P1C0 on 2011-02-23
auth.log:
```
Feb 23 13:10:40 machine login[9420]: pam_unix(login:auth): check pass; user unknown
Feb 23 13:10:40 machine login[9420]: pam_unix(login:auth): authentication failure; logname=LOGIN uid=0 euid=0 tty=/dev/tty2 ruser= rhost= 
Feb 23 13:10:43 machine login[9420]: FAILED LOGIN (1) on '/dev/tty2' FOR 'UNKNOWN', Authentication failure
Feb 23 13:10:52 machine login[9420]: pam_unix(login:session): **session opened for user auser** by LOGIN(uid=0)

```

kern.log:
```
Feb 23 13:10:28 machine kernel: [428192.107840] atkbd.c: Unknown key pressed (translated set 2, code 0xd7 on isa0060/serio0).
Feb 23 13:10:28 machine kernel: [428192.107848] atkbd.c: Use 'setkeycodes e057 <keycode>' to make it known.
Feb 23 13:10:28 machine kernel: [428192.244897] atkbd.c: Unknown key released (translated set 2, code 0xd7 on isa0060/serio0).
Feb 23 13:10:28 machine kernel: [428192.244905] atkbd.c: Use 'setkeycodes e057 <keycode>' to make it known.
Feb 23 13:10:28 machine kernel: [428192.884594] atkbd.c: Unknown key pressed (translated set 2, code 0xc4 on isa0060/serio0).
Feb 23 13:10:28 machine kernel: [428192.884601] atkbd.c: Use 'setkeycodes e044 <keycode>' to make it known.
Feb 23 13:10:28 machine kernel: [428192.999832] atkbd.c: Unknown key released (translated set 2, code 0xc4 on isa0060/serio0).
Feb 23 13:10:28 machine kernel: [428192.999839] atkbd.c: Use 'setkeycodes e044 <keycode>' to make it known.
Feb 23 13:10:29 machine kernel: [428193.134995] atkbd.c: Unknown key pressed (translated set 2, code 0xd7 on isa0060/serio0).
Feb 23 13:10:29 machine kernel: [428193.135001] atkbd.c: Use 'setkeycodes e057 <keycode>' to make it known.
Feb 23 13:10:29 machine kernel: [428193.250288] atkbd.c: Unknown key released (translated set 2, code 0xd7 on isa0060/serio0).
Feb 23 13:10:29 machine kernel: [428193.250295] atkbd.c: Use 'setkeycodes e057 <keycode>' to make it known.
Feb 23 13:10:29 machine kernel: [428193.454283] atkbd.c: Unknown key pressed (translated set 2, code 0xc3 on isa0060/serio0).
Feb 23 13:10:29 machine kernel: [428193.454291] atkbd.c: Use 'setkeycodes e043 <keycode>' to make it known.
Feb 23 13:10:29 machine kernel: [428193.613264] atkbd.c: Unknown key released (translated set 2, code 0xc3 on isa0060/serio0).
Feb 23 13:10:29 machine kernel: [428193.613271] atkbd.c: Use 'setkeycodes e043 <keycode>' to make it known.
Feb 23 13:10:30 machine kernel: [428194.145827] atkbd.c: Unknown key pressed (translated set 2, code 0xc2 on isa0060/serio0).
Feb 23 13:10:30 machine kernel: [428194.145834] atkbd.c: Use 'setkeycodes e042 <keycode>' to make it known.
Feb 23 13:10:30 machine kernel: [428194.261260] atkbd.c: Unknown key released (translated set 2, code 0xc2 on isa0060/serio0).
Feb 23 13:10:30 machine kernel: [428194.261267] atkbd.c: Use 'setkeycodes e042 <keycode>' to make it known.
Feb 23 13:10:30 machine kernel: [428194.450364] atkbd.c: Unknown key pressed (translated set 2, code 0xc1 on isa0060/serio0).
Feb 23 13:10:30 machine kernel: [428194.450372] atkbd.c: Use 'setkeycodes e041 <keycode>' to make it known.
Feb 23 13:10:30 machine kernel: [428194.543911] atkbd.c: Unknown key released (translated set 2, code 0xc1 on isa0060/serio0).
Feb 23 13:10:30 machine kernel: [428194.543917] atkbd.c: Use 'setkeycodes e041 <keycode>' to make it known.
Feb 23 13:10:30 machine kernel: [428194.700890] atkbd.c: Unknown key pressed (translated set 2, code 0xc0 on isa0060/serio0).
Feb 23 13:10:30 machine kernel: [428194.700895] atkbd.c: Use 'setkeycodes e040 <keycode>' to make it known.
Feb 23 13:10:30 machine kernel: [428194.799772] atkbd.c: Unknown key released (translated set 2, code 0xc0 on isa0060/serio0).
Feb 23 13:10:30 machine kernel: [428194.799777] atkbd.c: Use 'setkeycodes e040 <keycode>' to make it known.
Feb 23 13:10:30 machine kernel: [428194.942214] atkbd.c: Unknown key pressed (translated set 2, code 0xbf on isa0060/serio0).
Feb 23 13:10:30 machine kernel: [428194.942221] atkbd.c: Use 'setkeycodes e03f <keycode>' to make it known.
Feb 23 13:10:31 machine kernel: [428195.079265] atkbd.c: Unknown key released (translated set 2, code 0xbf on isa0060/serio0).
Feb 23 13:10:31 machine kernel: [428195.079273] atkbd.c: Use 'setkeycodes e03f <keycode>' to make it known.
Feb 23 13:10:31 machine kernel: [428195.769854] atkbd.c: Unknown key pressed (translated set 2, code 0xbe on isa0060/serio0).
Feb 23 13:10:31 machine kernel: [428195.769861] atkbd.c: Use 'setkeycodes e03e <keycode>' to make it known.
Feb 23 13:10:31 machine kernel: [428195.906920] atkbd.c: Unknown key released (translated set 2, code 0xbe on isa0060/serio0).
Feb 23 13:10:31 machine kernel: [428195.906927] atkbd.c: Use 'setkeycodes e03e <keycode>' to make it known.
Feb 23 13:10:32 machine kernel: [428196.349766] atkbd.c: Unknown key pressed (translated set 2, code 0xbd on isa0060/serio0).
Feb 23 13:10:32 machine kernel: [428196.349773] atkbd.c: Use 'setkeycodes e03d <keycode>' to make it known.
Feb 23 13:10:32 machine kernel: [428196.508696] atkbd.c: Unknown key released (translated set 2, code 0xbd on isa0060/serio0).
Feb 23 13:10:32 machine kernel: [428196.508704] atkbd.c: Use 'setkeycodes e03d <keycode>' to make it known.
Feb 23 13:10:32 machine kernel: [428196.646007] atkbd.c: Unknown key pressed (translated set 2, code 0xbc on isa0060/serio0).
Feb 23 13:10:32 machine kernel: [428196.646013] atkbd.c: Use 'setkeycodes e03c <keycode>' to make it known.
Feb 23 13:10:32 machine kernel: [428196.783202] atkbd.c: Unknown key released (translated set 2, code 0xbc on isa0060/serio0).
Feb 23 13:10:32 machine kernel: [428196.783209] atkbd.c: Use 'setkeycodes e03c <keycode>' to make it known.
Feb 23 13:10:32 machine kernel: [428196.962016] atkbd.c: Unknown key pressed (translated set 2, code 0xbb on isa0060/serio0).
Feb 23 13:10:32 machine kernel: [428196.962023] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
Feb 23 13:10:33 machine kernel: [428197.120989] atkbd.c: Unknown key released (translated set 2, code 0xbb on isa0060/serio0).
Feb 23 13:10:33 machine kernel: [428197.120995] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
Feb 23 13:10:34 machine kernel: [428198.973288] atkbd.c: Unknown key pressed (translated set 2, code 0xbb on isa0060/serio0).
Feb 23 13:10:34 machine kernel: [428198.973296] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
Feb 23 13:10:35 machine kernel: [428199.132244] atkbd.c: Unknown key released (translated set 2, code 0xbb on isa0060/serio0).
Feb 23 13:10:35 machine kernel: [428199.132251] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
Feb 23 13:10:35 machine kernel: [428199.333211] atkbd.c: Unknown key pressed (translated set 2, code 0xbc on isa0060/serio0).
Feb 23 13:10:35 machine kernel: [428199.333218] atkbd.c: Use 'setkeycodes e03c <keycode>' to make it known.
Feb 23 13:10:35 machine kernel: [428199.479342] atkbd.c: Unknown key released (translated set 2, code 0xbc on isa0060/serio0).
Feb 23 13:10:35 machine kernel: [428199.479349] atkbd.c: Use 'setkeycodes e03c <keycode>' to make it known.
Feb 23 13:10:35 machine kernel: [428199.680000] atkbd.c: Unknown key pressed (translated set 2, code 0xbd on isa0060/serio0).
Feb 23 13:10:35 machine kernel: [428199.680008] atkbd.c: Use 'setkeycodes e03d <keycode>' to make it known.
Feb 23 13:10:35 machine kernel: [428199.839019] atkbd.c: Unknown key released (translated set 2, code 0xbd on isa0060/serio0).
Feb 23 13:10:35 machine kernel: [428199.839027] atkbd.c: Use 'setkeycodes e03d <keycode>' to make it known.
Feb 23 13:10:35 machine kernel: [428199.996865] atkbd.c: Unknown key pressed (translated set 2, code 0xbe on isa0060/serio0).
Feb 23 13:10:35 machine kernel: [428199.996873] atkbd.c: Use 'setkeycodes e03e <keycode>' to make it known.
Feb 23 13:10:36 machine kernel: [428200.177674] atkbd.c: Unknown key released (translated set 2, code 0xbe on isa0060/serio0).
Feb 23 13:10:36 machine kernel: [428200.177681] atkbd.c: Use 'setkeycodes e03e <keycode>' to make it known.
Feb 23 13:10:36 machine kernel: [428200.400174] atkbd.c: Unknown key pressed (translated set 2, code 0xbf on isa0060/serio0).
Feb 23 13:10:36 machine kernel: [428200.400181] atkbd.c: Use 'setkeycodes e03f <keycode>' to make it known.
Feb 23 13:10:36 machine kernel: [428200.559128] atkbd.c: Unknown key released (translated set 2, code 0xbf on isa0060/serio0).
Feb 23 13:10:36 machine kernel: [428200.559135] atkbd.c: Use 'setkeycodes e03f <keycode>' to make it known.
Feb 23 13:10:36 machine kernel: [428200.738017] atkbd.c: Unknown key pressed (translated set 2, code 0xc0 on isa0060/serio0).
Feb 23 13:10:36 machine kernel: [428200.738024] atkbd.c: Use 'setkeycodes e040 <keycode>' to make it known.
Feb 23 13:10:36 machine kernel: [428200.896982] atkbd.c: Unknown key released (translated set 2, code 0xc0 on isa0060/serio0).
Feb 23 13:10:36 machine kernel: [428200.896989] atkbd.c: Use 'setkeycodes e040 <keycode>' to make it known.
Feb 23 13:10:37 machine kernel: [428201.075834] atkbd.c: Unknown key pressed (translated set 2, code 0xc1 on isa0060/serio0).
Feb 23 13:10:37 machine kernel: [428201.075841] atkbd.c: Use 'setkeycodes e041 <keycode>' to make it known.
Feb 23 13:10:37 machine kernel: [428201.239790] atkbd.c: Unknown key released (translated set 2, code 0xc1 on isa0060/serio0).
Feb 23 13:10:37 machine kernel: [428201.239798] atkbd.c: Use 'setkeycodes e041 <keycode>' to make it known.
Feb 23 13:10:37 machine kernel: [428201.571580] atkbd.c: Unknown key pressed (translated set 2, code 0xc2 on isa0060/serio0).
Feb 23 13:10:37 machine kernel: [428201.571587] atkbd.c: Use 'setkeycodes e042 <keycode>' to make it known.
Feb 23 13:10:37 machine kernel: [428201.735787] atkbd.c: Unknown key released (translated set 2, code 0xc2 on isa0060/serio0).
Feb 23 13:10:37 machine kernel: [428201.735793] atkbd.c: Use 'setkeycodes e042 <keycode>' to make it known.
Feb 23 13:10:57 machine kernel: [428221.579161] atkbd.c: Unknown key pressed (translated set 2, code 0xc4 on isa0060/serio0).
Feb 23 13:10:57 machine kernel: [428221.579169] atkbd.c: Use 'setkeycodes e044 <keycode>' to make it known.
Feb 23 13:10:57 machine kernel: [428221.738189] atkbd.c: Unknown key released (translated set 2, code 0xc4 on isa0060/serio0).
Feb 23 13:10:57 machine kernel: [428221.738196] atkbd.c: Use 'setkeycodes e044 <keycode>' to make it known.
Feb 23 13:10:57 machine kernel: [428222.007174] atkbd.c: Unknown key pressed (translated set 2, code 0xd7 on isa0060/serio0).
Feb 23 13:10:57 machine kernel: [428222.007181] atkbd.c: Use 'setkeycodes e057 <keycode>' to make it known.
Feb 23 13:10:58 machine kernel: [428222.144319] atkbd.c: Unknown key released (translated set 2, code 0xd7 on isa0060/serio0).
Feb 23 13:10:58 machine kernel: [428222.144326] atkbd.c: Use 'setkeycodes e057 <keycode>' to make it known.
Feb 23 13:10:58 machine kernel: [428223.026258] atkbd.c: Unknown key pressed (translated set 2, code 0xd7 on isa0060/serio0).
Feb 23 13:10:58 machine kernel: [428223.026265] atkbd.c: Use 'setkeycodes e057 <keycode>' to make it known.
Feb 23 13:10:59 machine kernel: [428223.163362] atkbd.c: Unknown key released (translated set 2, code 0xd7 on isa0060/serio0).
Feb 23 13:10:59 machine kernel: [428223.163369] atkbd.c: Use 'setkeycodes e057 <keycode>' to make it known.
Feb 23 13:10:59 machine kernel: [428223.350245] atkbd.c: Unknown key pressed (translated set 2, code 0xc4 on isa0060/serio0).
Feb 23 13:10:59 machine kernel: [428223.350251] atkbd.c: Use 'setkeycodes e044 <keycode>' to make it known.
Feb 23 13:10:59 machine kernel: [428223.487316] atkbd.c: Unknown key released (translated set 2, code 0xc4 on isa0060/serio0).
Feb 23 13:10:59 machine kernel: [428223.487324] atkbd.c: Use 'setkeycodes e044 <keycode>' to make it known.
Feb 23 13:10:59 machine kernel: [428223.622502] atkbd.c: Unknown key pressed (translated set 2, code 0xc3 on isa0060/serio0).
Feb 23 13:10:59 machine kernel: [428223.622509] atkbd.c: Use 'setkeycodes e043 <keycode>' to make it known.
Feb 23 13:10:59 machine kernel: [428223.759713] atkbd.c: Unknown key released (translated set 2, code 0xc3 on isa0060/serio0).
Feb 23 13:10:59 machine kernel: [428223.759718] atkbd.c: Use 'setkeycodes e043 <keycode>' to make it known.
Feb 23 13:11:00 machine kernel: [428224.113341] atkbd.c: Unknown key pressed (translated set 2, code 0xc2 on isa0060/serio0).
Feb 23 13:11:00 machine kernel: [428224.113348] atkbd.c: Use 'setkeycodes e042 <keycode>' to make it known.
Feb 23 13:11:00 machine kernel: [428224.258229] atkbd.c: Unknown key released (translated set 2, code 0xc2 on isa0060/serio0).
Feb 23 13:11:00 machine kernel: [428224.258235] atkbd.c: Use 'setkeycodes e042 <keycode>' to make it known.
Feb 23 13:11:00 machine kernel: [428224.440052] atkbd.c: Unknown key pressed (translated set 2, code 0xc1 on isa0060/serio0).
Feb 23 13:11:00 machine kernel: [428224.440060] atkbd.c: Use 'setkeycodes e041 <keycode>' to make it known.
Feb 23 13:11:00 machine kernel: [428224.577259] atkbd.c: Unknown key released (translated set 2, code 0xc1 on isa0060/serio0).
Feb 23 13:11:00 machine kernel: [428224.577266] atkbd.c: Use 'setkeycodes e041 <keycode>' to make it known.
Feb 23 13:11:00 machine kernel: [428224.787938] atkbd.c: Unknown key pressed (translated set 2, code 0xc0 on isa0060/serio0).
Feb 23 13:11:00 machine kernel: [428224.787946] atkbd.c: Use 'setkeycodes e040 <keycode>' to make it known.
Feb 23 13:11:00 machine kernel: [428224.925150] atkbd.c: Unknown key released (translated set 2, code 0xc0 on isa0060/serio0).
Feb 23 13:11:00 machine kernel: [428224.925157] atkbd.c: Use 'setkeycodes e040 <keycode>' to make it known.
Feb 23 13:11:01 machine kernel: [428225.151966] atkbd.c: Unknown key pressed (translated set 2, code 0xbf on isa0060/serio0).
Feb 23 13:11:01 machine kernel: [428225.151973] atkbd.c: Use 'setkeycodes e03f <keycode>' to make it known.
Feb 23 13:11:01 machine kernel: [428225.274701] atkbd.c: Unknown key released (translated set 2, code 0xbf on isa0060/serio0).
Feb 23 13:11:01 machine kernel: [428225.274709] atkbd.c: Use 'setkeycodes e03f <keycode>' to make it known.
Feb 23 13:11:01 machine kernel: [428225.497213] atkbd.c: Unknown key pressed (translated set 2, code 0xbe on isa0060/serio0).
Feb 23 13:11:01 machine kernel: [428225.497221] atkbd.c: Use 'setkeycodes e03e <keycode>' to make it known.
Feb 23 13:11:01 machine kernel: [428225.638275] atkbd.c: Unknown key released (translated set 2, code 0xbe on isa0060/serio0).
Feb 23 13:11:01 machine kernel: [428225.638283] atkbd.c: Use 'setkeycodes e03e <keycode>' to make it known.
Feb 23 13:11:01 machine kernel: [428225.817034] atkbd.c: Unknown key pressed (translated set 2, code 0xbd on isa0060/serio0).
Feb 23 13:11:01 machine kernel: [428225.817041] atkbd.c: Use 'setkeycodes e03d <keycode>' to make it known.
Feb 23 13:11:01 machine kernel: [428225.978073] atkbd.c: Unknown key released (translated set 2, code 0xbd on isa0060/serio0).
Feb 23 13:11:01 machine kernel: [428225.978080] atkbd.c: Use 'setkeycodes e03d <keycode>' to make it known.
Feb 23 13:11:02 machine kernel: [428226.156937] atkbd.c: Unknown key pressed (translated set 2, code 0xbc on isa0060/serio0).
Feb 23 13:11:02 machine kernel: [428226.156943] atkbd.c: Use 'setkeycodes e03c <keycode>' to make it known.
Feb 23 13:11:02 machine kernel: [428226.315999] atkbd.c: Unknown key released (translated set 2, code 0xbc on isa0060/serio0).
Feb 23 13:11:02 machine kernel: [428226.316004] atkbd.c: Use 'setkeycodes e03c <keycode>' to make it known.
Feb 23 13:11:02 machine kernel: [428226.612831] atkbd.c: Unknown key pressed (translated set 2, code 0xbb on isa0060/serio0).
Feb 23 13:11:02 machine kernel: [428226.612839] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
Feb 23 13:11:02 machine kernel: [428226.728160] atkbd.c: Unknown key released (translated set 2, code 0xbb on isa0060/serio0).
Feb 23 13:11:02 machine kernel: [428226.728167] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
Feb 23 13:11:04 machine kernel: [428228.955251] atkbd.c: Unknown key pressed (translated set 2, code 0xbb on isa0060/serio0).
Feb 23 13:11:04 machine kernel: [428228.955258] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
Feb 23 13:11:05 machine kernel: [428229.092286] atkbd.c: Unknown key released (translated set 2, code 0xbb on isa0060/serio0).
Feb 23 13:11:05 machine kernel: [428229.092293] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
Feb 23 13:11:05 machine kernel: [428229.358532] atkbd.c: Unknown key pressed (translated set 2, code 0xbc on isa0060/serio0).
Feb 23 13:11:05 machine kernel: [428229.358538] atkbd.c: Use 'setkeycodes e03c <keycode>' to make it known.
Feb 23 13:11:05 machine kernel: [428229.476948] atkbd.c: Unknown key released (translated set 2, code 0xbc on isa0060/serio0).
Feb 23 13:11:05 machine kernel: [428229.476955] atkbd.c: Use 'setkeycodes e03c <keycode>' to make it known.
Feb 23 13:11:05 machine kernel: [428229.687193] atkbd.c: Unknown key pressed (translated set 2, code 0xbd on isa0060/serio0).
Feb 23 13:11:05 machine kernel: [428229.687200] atkbd.c: Use 'setkeycodes e03d <keycode>' to make it known.
Feb 23 13:11:05 machine kernel: [428229.846181] atkbd.c: Unknown key released (translated set 2, code 0xbd on isa0060/serio0).
Feb 23 13:11:05 machine kernel: [428229.846186] atkbd.c: Use 'setkeycodes e03d <keycode>' to make it known.
Feb 23 13:11:05 machine kernel: [428230.051308] atkbd.c: Unknown key pressed (translated set 2, code 0xbe on isa0060/serio0).
Feb 23 13:11:05 machine kernel: [428230.051316] atkbd.c: Use 'setkeycodes e03e <keycode>' to make it known.
Feb 23 13:11:06 machine kernel: [428230.232066] atkbd.c: Unknown key released (translated set 2, code 0xbe on isa0060/serio0).
Feb 23 13:11:06 machine kernel: [428230.232072] atkbd.c: Use 'setkeycodes e03e <keycode>' to make it known.
Feb 23 13:11:06 machine kernel: [428230.847820] atkbd.c: Unknown key pressed (translated set 2, code 0xbf on isa0060/serio0).
Feb 23 13:11:06 machine kernel: [428230.847827] atkbd.c: Use 'setkeycodes e03f <keycode>' to make it known.
Feb 23 13:11:06 machine kernel: [428231.006886] atkbd.c: Unknown key released (translated set 2, code 0xbf on isa0060/serio0).
Feb 23 13:11:06 machine kernel: [428231.006893] atkbd.c: Use 'setkeycodes e03f <keycode>' to make it known.
Feb 23 13:11:07 machine kernel: [428231.279156] atkbd.c: Unknown key pressed (translated set 2, code 0xc0 on isa0060/serio0).
Feb 23 13:11:07 machine kernel: [428231.279162] atkbd.c: Use 'setkeycodes e040 <keycode>' to make it known.
Feb 23 13:11:07 machine kernel: [428231.459965] atkbd.c: Unknown key released (translated set 2, code 0xc0 on isa0060/serio0).
Feb 23 13:11:07 machine kernel: [428231.459972] atkbd.c: Use 'setkeycodes e040 <keycode>' to make it known.
Feb 23 13:11:07 machine kernel: [428231.619108] atkbd.c: Unknown key pressed (translated set 2, code 0xc1 on isa0060/serio0).
Feb 23 13:11:07 machine kernel: [428231.619114] atkbd.c: Use 'setkeycodes e041 <keycode>' to make it known.
Feb 23 13:11:07 machine kernel: [428231.821832] atkbd.c: Unknown key released (translated set 2, code 0xc1 on isa0060/serio0).
Feb 23 13:11:07 machine kernel: [428231.821839] atkbd.c: Use 'setkeycodes e041 <keycode>' to make it known.
Feb 23 13:11:08 machine kernel: [428232.839880] atkbd.c: Unknown key pressed (translated set 2, code 0xc2 on isa0060/serio0).
Feb 23 13:11:08 machine kernel: [428232.839888] atkbd.c: Use 'setkeycodes e042 <keycode>' to make it known.
Feb 23 13:11:08 machine kernel: [428233.005647] atkbd.c: Unknown key released (translated set 2, code 0xc2 on isa0060/serio0).
Feb 23 13:11:08 machine kernel: [428233.005654] atkbd.c: Use 'setkeycodes e042 <keycode>' to make it known.
Feb 23 13:11:09 machine kernel: [428234.036470] atkbd.c: Unknown key pressed (translated set 2, code 0xc3 on isa0060/serio0).
Feb 23 13:11:09 machine kernel: [428234.036477] atkbd.c: Use 'setkeycodes e043 <keycode>' to make it known.
Feb 23 13:11:10 machine kernel: [428234.173650] atkbd.c: Unknown key released (translated set 2, code 0xc3 on isa0060/serio0).
Feb 23 13:11:10 machine kernel: [428234.173656] atkbd.c: Use 'setkeycodes e043 <keycode>' to make it known.
Feb 23 13:11:10 machine kernel: [428234.330625] atkbd.c: Unknown key pressed (translated set 2, code 0xc4 on isa0060/serio0).
Feb 23 13:11:10 machine kernel: [428234.330631] atkbd.c: Use 'setkeycodes e044 <keycode>' to make it known.
Feb 23 13:11:10 machine kernel: [428234.467820] atkbd.c: Unknown key released (translated set 2, code 0xc4 on isa0060/serio0).
Feb 23 13:11:10 machine kernel: [428234.467827] atkbd.c: Use 'setkeycodes e044 <keycode>' to make it known.
Feb 23 13:11:10 machine kernel: [428234.587876] atkbd.c: Unknown key pressed (translated set 2, code 0xd7 on isa0060/serio0).
Feb 23 13:11:10 machine kernel: [428234.587883] atkbd.c: Use 'setkeycodes e057 <keycode>' to make it known.
Feb 23 13:11:10 machine kernel: [428234.773336] atkbd.c: Unknown key released (translated set 2, code 0xd7 on isa0060/serio0).
Feb 23 13:11:10 machine kernel: [428234.773343] atkbd.c: Use 'setkeycodes e057 <keycode>' to make it known.
Feb 23 13:11:11 machine kernel: [428235.607414] atkbd.c: Unknown key pressed (translated set 2, code 0xd7 on isa0060/serio0).
Feb 23 13:11:11 machine kernel: [428235.607421] atkbd.c: Use 'setkeycodes e057 <keycode>' to make it known.
Feb 23 13:11:11 machine kernel: [428235.773484] atkbd.c: Unknown key released (translated set 2, code 0xd7 on isa0060/serio0).
Feb 23 13:11:11 machine kernel: [428235.773490] atkbd.c: Use 'setkeycodes e057 <keycode>' to make it known.
Feb 23 13:11:13 machine kernel: [428237.239261] atkbd.c: Unknown key pressed (translated set 2, code 0xd7 on isa0060/serio0).
Feb 23 13:11:13 machine kernel: [428237.239269] atkbd.c: Use 'setkeycodes e057 <keycode>' to make it known.
Feb 23 13:11:13 machine kernel: [428237.376986] atkbd.c: Unknown key released (translated set 2, code 0xd7 on isa0060/serio0).
Feb 23 13:11:13 machine kernel: [428237.376992] atkbd.c: Use 'setkeycodes e057 <keycode>' to make it known.
Feb 23 13:11:13 machine kernel: [428237.533860] atkbd.c: Unknown key pressed (translated set 2, code 0xc4 on isa0060/serio0).
Feb 23 13:11:13 machine kernel: [428237.533868] atkbd.c: Use 'setkeycodes e044 <keycode>' to make it known.
Feb 23 13:11:13 machine kernel: [428237.649612] atkbd.c: Unknown key released (translated set 2, code 0xc4 on isa0060/serio0).
Feb 23 13:11:13 machine kernel: [428237.649620] atkbd.c: Use 'setkeycodes e044 <keycode>' to make it known.
Feb 23 13:11:13 machine kernel: [428237.771211] atkbd.c: Unknown key pressed (translated set 2, code 0xc3 on isa0060/serio0).
Feb 23 13:11:13 machine kernel: [428237.771217] atkbd.c: Use 'setkeycodes e043 <keycode>' to make it known.
Feb 23 13:11:13 machine kernel: [428237.940842] atkbd.c: Unknown key released (translated set 2, code 0xc3 on isa0060/serio0).
Feb 23 13:11:13 machine kernel: [428237.940849] atkbd.c: Use 'setkeycodes e043 <keycode>' to make it known.
Feb 23 13:11:14 machine kernel: [428238.347123] atkbd.c: Unknown key pressed (translated set 2, code 0xc2 on isa0060/serio0).
Feb 23 13:11:14 machine kernel: [428238.347131] atkbd.c: Use 'setkeycodes e042 <keycode>' to make it known.
Feb 23 13:11:14 machine kernel: [428238.462500] atkbd.c: Unknown key released (translated set 2, code 0xc2 on isa0060/serio0).
Feb 23 13:11:14 machine kernel: [428238.462507] atkbd.c: Use 'setkeycodes e042 <keycode>' to make it known.
Feb 23 13:11:14 machine kernel: [428238.597658] atkbd.c: Unknown key pressed (translated set 2, code 0xc1 on isa0060/serio0).
Feb 23 13:11:14 machine kernel: [428238.597666] atkbd.c: Use 'setkeycodes e041 <keycode>' to make it known.
Feb 23 13:11:14 machine kernel: [428238.741086] atkbd.c: Unknown key released (translated set 2, code 0xc1 on isa0060/serio0).
Feb 23 13:11:14 machine kernel: [428238.741093] atkbd.c: Use 'setkeycodes e041 <keycode>' to make it known.
Feb 23 13:11:14 machine kernel: [428238.832462] atkbd.c: Unknown key pressed (translated set 2, code 0xc0 on isa0060/serio0).
Feb 23 13:11:14 machine kernel: [428238.832467] atkbd.c: Use 'setkeycodes e040 <keycode>' to make it known.
Feb 23 13:11:14 machine kernel: [428238.949549] atkbd.c: Unknown key released (translated set 2, code 0xc0 on isa0060/serio0).
Feb 23 13:11:14 machine kernel: [428238.949556] atkbd.c: Use 'setkeycodes e040 <keycode>' to make it known.
Feb 23 13:11:15 machine kernel: [428239.062782] atkbd.c: Unknown key pressed (translated set 2, code 0xbf on isa0060/serio0).
Feb 23 13:11:15 machine kernel: [428239.062788] atkbd.c: Use 'setkeycodes e03f <keycode>' to make it known.
Feb 23 13:11:15 machine kernel: [428239.178085] atkbd.c: Unknown key released (translated set 2, code 0xbf on isa0060/serio0).
Feb 23 13:11:15 machine kernel: [428239.178092] atkbd.c: Use 'setkeycodes e03f <keycode>' to make it known.
Feb 23 13:11:15 machine kernel: [428239.356897] atkbd.c: Unknown key pressed (translated set 2, code 0xbe on isa0060/serio0).
Feb 23 13:11:15 machine kernel: [428239.356903] atkbd.c: Use 'setkeycodes e03e <keycode>' to make it known.
Feb 23 13:11:15 machine kernel: [428239.460902] atkbd.c: Unknown key released (translated set 2, code 0xbe on isa0060/serio0).
Feb 23 13:11:15 machine kernel: [428239.460909] atkbd.c: Use 'setkeycodes e03e <keycode>' to make it known.
Feb 23 13:11:15 machine kernel: [428239.582945] atkbd.c: Unknown key pressed (translated set 2, code 0xbd on isa0060/serio0).
Feb 23 13:11:15 machine kernel: [428239.582952] atkbd.c: Use 'setkeycodes e03d <keycode>' to make it known.
Feb 23 13:11:15 machine kernel: [428239.698386] atkbd.c: Unknown key released (translated set 2, code 0xbd on isa0060/serio0).
Feb 23 13:11:15 machine kernel: [428239.698393] atkbd.c: Use 'setkeycodes e03d <keycode>' to make it known.
Feb 23 13:11:15 machine kernel: [428239.811711] atkbd.c: Unknown key pressed (translated set 2, code 0xbc on isa0060/serio0).
Feb 23 13:11:15 machine kernel: [428239.811718] atkbd.c: Use 'setkeycodes e03c <keycode>' to make it known.
Feb 23 13:11:15 machine kernel: [428239.912726] atkbd.c: Unknown key released (translated set 2, code 0xbc on isa0060/serio0).
Feb 23 13:11:15 machine kernel: [428239.912732] atkbd.c: Use 'setkeycodes e03c <keycode>' to make it known.
Feb 23 13:11:15 machine kernel: [428240.026085] atkbd.c: Unknown key pressed (translated set 2, code 0xbb on isa0060/serio0).
Feb 23 13:11:15 machine kernel: [428240.026093] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
Feb 23 13:11:16 machine kernel: [428240.141435] atkbd.c: Unknown key released (translated set 2, code 0xbb on isa0060/serio0).
Feb 23 13:11:16 machine kernel: [428240.141442] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
Feb 23 13:11:16 machine kernel: [428240.683155] atkbd.c: Unknown key pressed (translated set 2, code 0xbb on isa0060/serio0).
Feb 23 13:11:16 machine kernel: [428240.683162] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
Feb 23 13:11:16 machine kernel: [428240.809011] atkbd.c: Unknown key released (translated set 2, code 0xbb on isa0060/serio0).
Feb 23 13:11:16 machine kernel: [428240.809018] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
Feb 23 13:11:16 machine kernel: [428240.966062] atkbd.c: Unknown key pressed (translated set 2, code 0xbc on isa0060/serio0).
Feb 23 13:11:16 machine kernel: [428240.966069] atkbd.c: Use 'setkeycodes e03c <keycode>' to make it known.
Feb 23 13:11:17 machine kernel: [428241.103145] atkbd.c: Unknown key released (translated set 2, code 0xbc on isa0060/serio0).
Feb 23 13:11:17 machine kernel: [428241.103152] atkbd.c: Use 'setkeycodes e03c <keycode>' to make it known.
Feb 23 13:11:17 machine kernel: [428241.223245] atkbd.c: Unknown key pressed (translated set 2, code 0xbd on isa0060/serio0).
Feb 23 13:11:17 machine kernel: [428241.223252] atkbd.c: Use 'setkeycodes e03d <keycode>' to make it known.
Feb 23 13:11:17 machine kernel: [428241.360871] atkbd.c: Unknown key released (translated set 2, code 0xbd on isa0060/serio0).
Feb 23 13:11:17 machine kernel: [428241.360877] atkbd.c: Use 'setkeycodes e03d <keycode>' to make it known.
Feb 23 13:11:17 machine kernel: [428241.496064] atkbd.c: Unknown key pressed (translated set 2, code 0xbe on isa0060/serio0).
Feb 23 13:11:17 machine kernel: [428241.496072] atkbd.c: Use 'setkeycodes e03e <keycode>' to make it known.
Feb 23 13:11:17 machine kernel: [428241.676790] atkbd.c: Unknown key released (translated set 2, code 0xbe on isa0060/serio0).
Feb 23 13:11:17 machine kernel: [428241.676798] atkbd.c: Use 'setkeycodes e03e <keycode>' to make it known.
Feb 23 13:11:18 machine kernel: [428242.161501] atkbd.c: Unknown key pressed (translated set 2, code 0xbf on isa0060/serio0).
Feb 23 13:11:18 machine kernel: [428242.161508] atkbd.c: Use 'setkeycodes e03f <keycode>' to make it known.
Feb 23 13:11:18 machine kernel: [428242.276760] atkbd.c: Unknown key released (translated set 2, code 0xbf on isa0060/serio0).
Feb 23 13:11:18 machine kernel: [428242.276767] atkbd.c: Use 'setkeycodes e03f <keycode>' to make it known.
Feb 23 13:11:18 machine kernel: [428242.411943] atkbd.c: Unknown key pressed (translated set 2, code 0xc0 on isa0060/serio0).
Feb 23 13:11:18 machine kernel: [428242.411950] atkbd.c: Use 'setkeycodes e040 <keycode>' to make it known.
Feb 23 13:11:18 machine kernel: [428242.527222] atkbd.c: Unknown key released (translated set 2, code 0xc0 on isa0060/serio0).
Feb 23 13:11:18 machine kernel: [428242.527229] atkbd.c: Use 'setkeycodes e040 <keycode>' to make it known.
Feb 23 13:11:18 machine kernel: [428242.755241] atkbd.c: Unknown key pressed (translated set 2, code 0xc1 on isa0060/serio0).
Feb 23 13:11:18 machine kernel: [428242.755248] atkbd.c: Use 'setkeycodes e041 <keycode>' to make it known.
Feb 23 13:11:18 machine kernel: [428242.870602] atkbd.c: Unknown key released (translated set 2, code 0xc1 on isa0060/serio0).
Feb 23 13:11:18 machine kernel: [428242.870608] atkbd.c: Use 'setkeycodes e041 <keycode>' to make it known.
Feb 23 13:11:18 machine kernel: [428243.007386] atkbd.c: Unknown key pressed (translated set 2, code 0xc2 on isa0060/serio0).
Feb 23 13:11:18 machine kernel: [428243.007393] atkbd.c: Use 'setkeycodes e042 <keycode>' to make it known.
Feb 23 13:11:19 machine kernel: [428243.125631] atkbd.c: Unknown key released (translated set 2, code 0xc2 on isa0060/serio0).
Feb 23 13:11:19 machine kernel: [428243.125638] atkbd.c: Use 'setkeycodes e042 <keycode>' to make it known.
Feb 23 13:11:19 machine kernel: [428243.874905] atkbd.c: Unknown key pressed (translated set 2, code 0xc3 on isa0060/serio0).
Feb 23 13:11:19 machine kernel: [428243.874912] atkbd.c: Use 'setkeycodes e043 <keycode>' to make it known.
Feb 23 13:11:19 machine kernel: [428244.012037] atkbd.c: Unknown key released (translated set 2, code 0xc3 on isa0060/serio0).
Feb 23 13:11:19 machine kernel: [428244.012044] atkbd.c: Use 'setkeycodes e043 <keycode>' to make it known.
Feb 23 13:11:20 machine kernel: [428244.147133] atkbd.c: Unknown key pressed (translated set 2, code 0xc4 on isa0060/serio0).
Feb 23 13:11:20 machine kernel: [428244.147139] atkbd.c: Use 'setkeycodes e044 <keycode>' to make it known.
Feb 23 13:11:20 machine kernel: [428244.262498] atkbd.c: Unknown key released (translated set 2, code 0xc4 on isa0060/serio0).
Feb 23 13:11:20 machine kernel: [428244.262504] atkbd.c: Use 'setkeycodes e044 <keycode>' to make it known.
Feb 23 13:11:20 machine kernel: [428244.397649] atkbd.c: Unknown key pressed (translated set 2, code 0xd7 on isa0060/serio0).
Feb 23 13:11:20 machine kernel: [428244.397654] atkbd.c: Use 'setkeycodes e057 <keycode>' to make it known.
Feb 23 13:11:20 machine kernel: [428244.534811] atkbd.c: Unknown key released (translated set 2, code 0xd7 on isa0060/serio0).
Feb 23 13:11:20 machine kernel: [428244.534818] atkbd.c: Use 'setkeycodes e057 <keycode>' to make it known.
Feb 23 13:11:21 machine kernel: [428245.810141] atkbd.c: Unknown key pressed (translated set 2, code 0xd7 on isa0060/serio0).
Feb 23 13:11:21 machine kernel: [428245.810148] atkbd.c: Use 'setkeycodes e057 <keycode>' to make it known.
Feb 23 13:11:21 machine kernel: [428245.913438] atkbd.c: Unknown key released (translated set 2, code 0xd7 on isa0060/serio0).
Feb 23 13:11:21 machine kernel: [428245.913444] atkbd.c: Use 'setkeycodes e057 <keycode>' to make it known.
Feb 23 13:11:22 machine kernel: [428246.114016] atkbd.c: Unknown key pressed (translated set 2, code 0xc4 on isa0060/serio0).
Feb 23 13:11:22 machine kernel: [428246.114023] atkbd.c: Use 'setkeycodes e044 <keycode>' to make it known.
Feb 23 13:11:22 machine kernel: [428246.237659] atkbd.c: Unknown key released (translated set 2, code 0xc4 on isa0060/serio0).
Feb 23 13:11:22 machine kernel: [428246.237665] atkbd.c: Use 'setkeycodes e044 <keycode>' to make it known.
Feb 23 13:11:22 machine kernel: [428246.375384] atkbd.c: Unknown key pressed (translated set 2, code 0xc3 on isa0060/serio0).
Feb 23 13:11:22 machine kernel: [428246.375390] atkbd.c: Use 'setkeycodes e043 <keycode>' to make it known.
Feb 23 13:11:22 machine kernel: [428246.517556] atkbd.c: Unknown key released (translated set 2, code 0xc3 on isa0060/serio0).
Feb 23 13:11:22 machine kernel: [428246.517562] atkbd.c: Use 'setkeycodes e043 <keycode>' to make it known.
Feb 23 13:11:23 machine kernel: [428247.242467] atkbd.c: Unknown key pressed (translated set 2, code 0xc2 on isa0060/serio0).
Feb 23 13:11:23 machine kernel: [428247.242475] atkbd.c: Use 'setkeycodes e042 <keycode>' to make it known.
Feb 23 13:11:23 machine kernel: [428247.345735] atkbd.c: Unknown key released (translated set 2, code 0xc2 on isa0060/serio0).
Feb 23 13:11:23 machine kernel: [428247.345742] atkbd.c: Use 'setkeycodes e042 <keycode>' to make it known.
Feb 23 13:11:23 machine kernel: [428247.551749] atkbd.c: Unknown key pressed (translated set 2, code 0xc1 on isa0060/serio0).
Feb 23 13:11:23 machine kernel: [428247.551756] atkbd.c: Use 'setkeycodes e041 <keycode>' to make it known.
Feb 23 13:11:23 machine kernel: [428247.667018] atkbd.c: Unknown key released (translated set 2, code 0xc1 on isa0060/serio0).
Feb 23 13:11:23 machine kernel: [428247.667025] atkbd.c: Use 'setkeycodes e041 <keycode>' to make it known.
Feb 23 13:11:23 machine kernel: [428247.845707] atkbd.c: Unknown key pressed (translated set 2, code 0xc0 on isa0060/serio0).
Feb 23 13:11:23 machine kernel: [428247.845714] atkbd.c: Use 'setkeycodes e040 <keycode>' to make it known.
Feb 23 13:11:23 machine kernel: [428247.949932] atkbd.c: Unknown key released (translated set 2, code 0xc0 on isa0060/serio0).
Feb 23 13:11:23 machine kernel: [428247.949939] atkbd.c: Use 'setkeycodes e040 <keycode>' to make it known.
Feb 23 13:11:24 machine kernel: [428248.095580] atkbd.c: Unknown key pressed (translated set 2, code 0xbf on isa0060/serio0).
Feb 23 13:11:24 machine kernel: [428248.095587] atkbd.c: Use 'setkeycodes e03f <keycode>' to make it known.
Feb 23 13:11:24 machine kernel: [428248.232807] atkbd.c: Unknown key released (translated set 2, code 0xbf on isa0060/serio0).
Feb 23 13:11:24 machine kernel: [428248.232814] atkbd.c: Use 'setkeycodes e03f <keycode>' to make it known.
Feb 23 13:11:24 machine kernel: [428248.420320] atkbd.c: Unknown key pressed (translated set 2, code 0xbe on isa0060/serio0).
Feb 23 13:11:24 machine kernel: [428248.420327] atkbd.c: Use 'setkeycodes e03e <keycode>' to make it known.
Feb 23 13:11:24 machine kernel: [428248.537693] atkbd.c: Unknown key released (translated set 2, code 0xbe on isa0060/serio0).
Feb 23 13:11:24 machine kernel: [428248.537700] atkbd.c: Use 'setkeycodes e03e <keycode>' to make it known.
Feb 23 13:11:24 machine kernel: [428248.672810] atkbd.c: Unknown key pressed (translated set 2, code 0xbd on isa0060/serio0).
Feb 23 13:11:24 machine kernel: [428248.672817] atkbd.c: Use 'setkeycodes e03d <keycode>' to make it known.
Feb 23 13:11:24 machine kernel: [428248.797364] atkbd.c: Unknown key released (translated set 2, code 0xbd on isa0060/serio0).
Feb 23 13:11:24 machine kernel: [428248.797370] atkbd.c: Use 'setkeycodes e03d <keycode>' to make it known.
Feb 23 13:11:24 machine kernel: [428248.910671] atkbd.c: Unknown key pressed (translated set 2, code 0xbc on isa0060/serio0).
Feb 23 13:11:24 machine kernel: [428248.910677] atkbd.c: Use 'setkeycodes e03c <keycode>' to make it known.
Feb 23 13:11:24 machine kernel: [428249.030245] atkbd.c: Unknown key released (translated set 2, code 0xbc on isa0060/serio0).
Feb 23 13:11:24 machine kernel: [428249.030252] atkbd.c: Use 'setkeycodes e03c <keycode>' to make it known.
Feb 23 13:11:25 machine kernel: [428249.209035] atkbd.c: Unknown key pressed (translated set 2, code 0xbb on isa0060/serio0).
Feb 23 13:11:25 machine kernel: [428249.209042] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
Feb 23 13:11:25 machine kernel: [428249.346255] atkbd.c: Unknown key released (translated set 2, code 0xbb on isa0060/serio0).
Feb 23 13:11:25 machine kernel: [428249.346261] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.

```

---

### Post by Tristam Green on 2011-02-23
I bet he used Tracer T.  That's a killer hack.

---

### Post by Charlietje on 2011-02-23
> **cgroza said:**
> thats how brute force attacks work.:)

+1 :p

---

### Post by elliotn on 2011-02-23
lol my 2 years old son always wanna play NFS and he knows how to start windows and choose the NFS icon, I bet one day he will know how to hack

---

### Post by amsterdamharu on 2011-02-23
I don't know if this works on default Ubuntu install but can't anyone with local access to your computer gain root quite easily.

1. boot into recovery and drop to root shell, since Ubuntu didn't set password for root no password is asked (but I could be wrong because I set password for root).
2. Create an admin group user and log in as that user, now with sudo and gksu you have access to all (except encrypted folders/partitions I guess).

Ok, so a 16 month child could not do it but it still is quite simple. There are grub settings that would prevent you from tempering with the menu and or not allow you grub command which would not allow someone to gain full control without knowing the password.

Could anyone confirm this or am I wrong and do you need to give password when going to root console in recovery menu?

---

### Post by NightwishFan on 2011-02-23
Security wise if someone gets on your machine physically it really is all over anyway. (Unless you have encryption). The "recovery mode" not asking for my password lets me reset my family members passwords if they forget them. It has come in handy! :)

---

### Post by forrestcupp on 2011-02-23
So your real password was actually typed on the screen in the middle of random letters?  That *is* kind of scary.

I thought the characters aren't shown when you're entering a password in the console.

---

### Post by P1C0 on 2011-02-23
> **NightwishFan said:**
> Security wise **if someone gets on your  machine physically it really is all over anyway**. (Unless you have  encryption). The "recovery mode" not asking for my password lets me  reset my family members passwords if they forget them. It has come in  handy! :smile:I believe so too, but to see my password on the screen, having left my desktop locked for less than a minute (you can see that in the logs) is crazy :P

> **forrestcupp said:**
> So your real password was actually typed on the screen in the middle of random letters?  That *is* kind of scary.

I thought the characters aren't shown when you're entering a password in the console.Yes and you know you don't get to physically see your password on a machine (if ever), so when I saw it I thought "Wow look it looks cool actually ..but ..WTF!".

---

### Post by FoxEWolf on 2011-02-23
That is Brilliant!! Hackers start young now.... Kind of cool, but scary at the same time.

---

### Post by MaxIBoy on 2011-02-23
Might your password be some sequence of keys in order, i.e. "qwerty" or "1q2w3e4r5t6y" or some other easily-rederived pattern?

---

### Post by Old_Grey_Wolf on 2011-02-23
I have had computers in my home for over 30 years. There are not a lot of things that surprise me anymore. 

I let my children play with my computers when they were young, and now I let my grandchildren play with them. It is amazing what happens when they have physical access to the computer, dragging files and folders around; such as, into the trash, and entering random stuff on the keyboard. 

I have computers set up for my grandchildren to play with, and don't let them play with my production computers.

They can really F-up a computer. 

:lolflag:

I must say that it doesn't happen nearly as often as it did with Microsoft Windows.

---

### Post by Old *ix Geek on 2011-02-23
Too bad you've already closed everything. I'd have loved to have seen what scrolling back through the baby's input (with the up arrow key) would have shown. Of course there's no way to know now, but it probably wasn't anything as mysterious as we're all thinking it was.

---

### Post by Khakilang on 2011-02-24
He can read your mind and your brain don't have any password. Scary!

---

### Post by piquat on 2011-02-24
Maybe they should change the name to the "Infinite Baby Theorem"?

---

### Post by P1C0 on 2011-02-24
> **MaxIBoy said:**
> Might your password be some sequence of keys in order, i.e. "qwerty" or "1q2w3e4r5t6y" or some other easily-rederived pattern?Oh no, it's an alphanumeric with both upper and lower case letters. It's not the most difficult password in the world, but surely not one you can create by bashing the keyboard :)

---

### Post by Tristam Green on 2011-02-24
> **MaxIBoy said:**
> Might your password be some sequence of keys in order, i.e. "qwerty" or "1q2w3e4r5t6y" or some other easily-rederived pattern?

> **P1C0 said:**
> Oh no, it's an alphanumeric with both upper and lower case letters. It's not the most difficult password in the world, but surely not one you can create by bashing the keyboard :)


In reality:

[img]http://img501.imageshack.us/img501/1792/sb1ff0.jpg[/img]
Roland: One.
Dark Helmet: One.
Colonel Sandurz: One.
Roland: Two.
Dark Helmet: Two.
Colonel Sandurz: Two.
Roland: Three.
Dark Helmet: Three.
Colonel Sandurz: Three.
Roland: Four.
Dark Helmet: Four.
Colonel Sandurz: Four.
Roland: Five.
Dark Helmet: Five.
Colonel Sandurz: Five.
Dark Helmet: So the combination is... one, two, three, four, five? That's the stupidest combination I've ever heard in my life! The kind of thing an idiot would have on his luggage!

---

### Post by Exodist on 2011-02-24
> **Tristam Green said:**
> In reality:
 
[IMG]http://img501.imageshack.us/img501/1792/sb1ff0.jpg[/IMG]
Roland: One.
Dark Helmet: One.
Colonel Sandurz: One.
Roland: Two.
Dark Helmet: Two.
Colonel Sandurz: Two.
Roland: Three.
Dark Helmet: Three.
Colonel Sandurz: Three.
Roland: Four.
Dark Helmet: Four.
Colonel Sandurz: Four.
Roland: Five.
Dark Helmet: Five.
Colonel Sandurz: Five.
Dark Helmet: So the combination is... one, two, three, four, five? That's the stupidest combination I've ever heard in my life! The kind of thing an idiot would have on his luggage!
 
 
LMAO..
 
Mel Brooks: (come to the ships bridge) So did we get the combination?
Helmet: 1,2,3,4,5 Sir!
Brooks: 1,2,3,4,5! Dear god thats the same combination I have on my luggage!

---

### Post by Tristam Green on 2011-02-24
> **Exodist said:**
> LMAO..
 
Mel Brooks: (come to the ships bridge) So did we get the combination?
Helmet: 1,2,3,4,5 Sir!
Brooks: 1,2,3,4,5! Dear god thats the same combination I have on my luggage!

sir, have some cheesecake.

[img]http://www.arizonafoothillsmagazine.com/taste/wp-content/uploads/cheesecake.jpg[/img]

---

### Post by Ctrl-Alt-F1 on 2011-02-24
You be trollin son.

---

### Post by thundaboom on 2011-02-24
Your nephew is getting back at you for those cookies you stole from him. ;)

Try 'history'

---

### Post by P1C0 on 2011-02-26
> **thundaboom said:**
> Your nephew is getting back at you for those cookies you stole from him. ;)

Try 'history'I enjoyed the humorous posts :D I've come to the conclusion that -even if I rarely do so and don't remember doing so- I copied the password to the clipboard.

This makes sense in many ways like:

[LIST]
[*]Passwords are stored encrypted in the system
[*]I reboot my machine every 2-3 weeks or so and I can't be sure of how I used my passwords, for example if I copied one to fill the box for another site or whatever
[*]My nephew mostly tampers with the bottom left part of the keyboard and presses Ctrl a lot, so a combination like Ctrl + V is possible
[/LIST]

BUT just in case, I take the batteries out now :p

---

### Post by giddyup306 on 2011-02-26
If your nephew has enough time to hack into your box you need to get him a play date. :lol:

---

### Post by Megaptera on 2011-02-26
You could perhaps let your nephew play with linux designed for kids on a live CD such as DouDou or Qimo.

[http://maketecheasier.com/doudoulinux-a-fun-linux-distro-for-kids/2010/11/26](http://maketecheasier.com/doudoulinux-a-fun-linux-distro-for-kids/2010/11/26)

[http://www.qimo4kids.com/page/What-is-Qimo.aspx](http://www.qimo4kids.com/page/What-is-Qimo.aspx)

---

### Post by walt.smith1960 on 2011-02-26
Your newphew is the kid in the Etrade commercials

(only makes sense if you're in Yankeestan (u.s.))

---

### Post by ki4jgt on 2011-02-26
Some how my siblings had gotten my panels to show, while the screen saver was on. When I came back to type in my password, I have about 7 programs running&#8253; Been there. They basically love leaving me notes while I'm away from my computer. Usuaully ones with random key combos for some reason like:

> lsdjad;fjf;kosdfjsjfso;okefnsdla;dklnvkd;jfosfjslfj

but sometimes I get the:
> I love you!
That one makes it half way better :-(

---

### Post by NightwishFan on 2011-02-26
Yes, I have had some odd issues with the screensaver. It might be due to compiz.

---

### Post by P1C0 on 2011-02-26
> **Megaptera said:**
> You could perhaps let your nephew play with linux designed for kids on a live CD such as DouDou or Qimo.

[http://maketecheasier.com/doudoulinux-a-fun-linux-distro-for-kids/2010/11/26](http://maketecheasier.com/doudoulinux-a-fun-linux-distro-for-kids/2010/11/26)

[http://www.qimo4kids.com/page/What-is-Qimo.aspx](http://www.qimo4kids.com/page/What-is-Qimo.aspx)This looks great, thanx! I am downloading DouDou at the moment to try it out. If its so easy to use as stated I'll definitely make a copy for the parents too.
:KS

edit://Ok I tried it out, played a bit with the games, its so nice! Love it :) Thanx again for pointing it out.

---

### Post by Megaptera on 2011-02-27
> **P1C0 said:**
> This looks great, thanx! I am downloading DouDou at the moment to try it out. If its so easy to use as stated I'll definitely make a copy for the parents too.
:KS

edit://Ok I tried it out, played a bit with the games, its so nice! Love it :) Thanx again for pointing it out.

You (and your nephew!) are welcome!!

---

### Post by sanderella on 2011-02-27
There is no end to the inventiveness and destructiveness of a toddler! They can wreck anything. 8)

---

### Post by Rachel_Eliason on 2011-02-27
Every parent knows the answer to this. Nothing is ever truly baby proof. I'll bet that kid will be awesome some day.:P

---

### Post by t0p on 2011-02-27
Can the lad also twist his head all the way round without the fracturing vertebra bothering him?

Sorry for asking such a *diabolical* (hehe) question; but concerned viewers Need To Know!

---

