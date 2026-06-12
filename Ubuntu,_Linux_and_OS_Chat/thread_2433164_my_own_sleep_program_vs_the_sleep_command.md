---
title: "my own sleep program vs the sleep command"
date: 2019-12-14
forum: Ubuntu, Linux and OS Chat
---

### Post by Skaperen on 2019-12-14
i wrote my own _sleep_ program and [COLOR=#808080][FONT=courier new]**bash**[/FONT][/COLOR] behaves different with it than it does with the sleep command.  could it be a secret built-in command?  the [COLOR=#808080][FONT=courier new]**bash**[/FONT][/COLOR] _man page_ has no references to "[COLOR=#808080][FONT=courier new]**sleep**[/FONT][/COLOR]" whatsoever.  the different behavior is when my program (named "[COLOR=#0000cd][FONT=courier new]**nsleep**[/FONT][/COLOR]") runs before another on one command line ("[COLOR=#0000cd][FONT=courier new]**nsleep 999999;date**[/FONT][/COLOR]") and _ctrl-[FONT=courier new]**C**[/FONT]_ is pressed.  with my [COLOR=#0000cd]**nsleep**[/COLOR] the [COLOR=#0000cd][FONT=courier new]**date**[/FONT][/COLOR] command is run anyway.  with the standard sleep command, [COLOR=#0000cd][FONT=courier new]**date**[/FONT][/COLOR] is not run.  [COLOR=#808080][FONT=courier new]**bash**[/FONT][/COLOR] is doing it different.  what causes this?  is [COLOR=#808080][FONT=courier new]**bash**[/FONT][/COLOR] getting a special signal?  is [COLOR=#808080][FONT=courier new]**bash**[/FONT][/COLOR] treating [COLOR=#0000cd][FONT=courier new]**sleep**[/FONT][/COLOR] differently?
```

lt2a/forums /home/forums 2> sleep 999999;date
^C
lt2a/forums /home/forums 3> nsleep 999999;date
^CSat Dec 14 20:17:40 EST 2019
lt2a/forums /home/forums 4>

```

---

### Post by sudodus on 2019-12-14
At least in 18.04.x LTS [FONT=Courier New]**sleep**[/FONT] is an executable program (compiled, ELF can be seen at the head of the file [FONT=Courier New]/bin/sleep[/FONT]. You find some details via

```

man sleep

```

and it is possible to find its source code. I guess there is nothing to trap the interrupt. You can compare with the shell built-in [FONT=Courier New]**read**[/FONT]

```

read -st5 -n1 ; date

```

that behaves like sleep för ctrl+C but differently if you stop it gracefully with for example Enter.

---

### Post by Skaperen on 2019-12-14
[COLOR=#0000cd][FONT=courier new]**sleep**[/FONT][/COLOR] has always been a binary executable in ever Unix/BSD/Linux system i have ever used on every architecture.  my [COLOR=#0000cd][FONT=courier new]**nsleep**[/FONT][/COLOR] is also a binary executable that has been built successfully, and run OK, on a few Linux distros and also on OpenBSD.  i have seen this behavior on Slackware Linux (32 bit and 64 bit), Timesys Linux on an ARM based eval board (32 bit only), and on Ubuntu Linux (64 bit only) (every LTS since 14.04.  i have not tried it on others for various reasons.

if i use [COLOR=#0000cd][FONT=courier new]**&&**[/FONT][/COLOR] instead of [COLOR=#0000cd][FONT=courier new]**;**[/FONT][/COLOR] then [COLOR=#0000cd][FONT=courier new]**date**[/FONT][/COLOR] does not run for both programs being interrupted.  i am considering writing a new version in Python3.

---

### Post by sudodus on 2019-12-15
I understand the different behaviour with regard to ctrl+C, but do not understand what you want, *why* you want your own [FONT=Courier New]**sleep**[/FONT]. Please explain.

---

### Post by Skaperen on 2019-12-15
the why of my own sleep command is another topic for another thread.

---

