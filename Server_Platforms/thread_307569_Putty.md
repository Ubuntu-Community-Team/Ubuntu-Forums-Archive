---
title: "Putty"
date: 2006-11-26
forum: Server Platforms
---

### Post by fernando_lopes_jr on 2006-11-26
I want to know if there is a way I can make my computer run the software I want even after I close putty. For example I use rtorrent to download torrents if I run it locally it stays running but If I do the same throw putty when I exit it the program stops.I would like rtorrent to keep running.

---

### Post by NetworkGuy on 2006-11-26
try starting the command with a & after it.

```
rtorrent &
```

---

### Post by fernando_lopes_jr on 2006-11-26
how does & work could you explain?

---

### Post by stickboy2642 on 2006-11-27
& will tell the program to run in the background and return control of the shell back to the user.  So you can run 'rtorrent &' and while that is running, you can run other commands.  I think that you can also exit out of PuTTY and it will keep running, but I have never really tested that.  Might be worth a try.

---

### Post by fernando_lopes_jr on 2006-11-27
I'am going to try it out as soon as I get home.Thanks for the help.

---

### Post by konsole on 2006-11-27
> **fernando_lopes_jr said:**
> I'am going to try it out as soon as I get home.Thanks for the help.

using & is unsuitable because you cannot see any output, and if you fg the job you cannot background it again without stopping it.

Check out the program: screen. 

Briefly, set up an alias something like: alias torrent='screen rtorrent' then start rtorrent by typing torrent. Detach from the session by typing Ctl A-D and attach to the session with screen -r. 

Too easy. Check out the man pages for full details. 8)

---

### Post by fernando_lopes_jr on 2006-11-27
Konsole could you explain better with commands I don't understand how I'am supposed to do that.

---

### Post by konsole on 2006-11-28
> **fernando_lopes_jr said:**
> Konsole could you explain better with commands I don't understand how I'am supposed to do that.

OK this is what you do. Type the command ```
dpkg-query -l screen
```

This will tell you if the "screen" program is installed. You should see something like:

 ii  screen   4.0.2-4.1ubuntu5.6.06     a terminal multiplexor with VT100/ANSI terminal emulation

If not, install the latest version of screen using aptitude, apt-get or whatever you use to install software.

Add the following line to your .bashrc
```
alias torrent='screen rtorrent'
```
You do this so you are not starting an uneccessary bash process and wasting resources.

Type ```
man bash
``` and read up on aliases.
Type ```
. .bashrc
``` to execute your .bashrc

Now when you ssh into your box you just type ```
torrent
```

This will start rtorrent in a virtual tty and connect you to it.

Do your torrent stuff and when finished type ```
Ctl-A + D
``` to detach from the virtual tty.

Type ```
ps auxf
``` and you will see the screen process as well as rtorrent running within the screen session.

You can now logout and rtorrent will continue to run within screen.

Alternatively type ```
screen -r
``` to reattach to your screen session and do more torrent stuff.

In it's simplest form "Ctl-A + D" detachs from screen, while "screen -r" resumes that screen session.

Type "man screen" and read up on it for more detail.

That's more than enough to get you going.

k.

---

### Post by mssever on 2006-11-28
> **konsole said:**
> using & is unsuitable because you cannot see any output, and if you fg the job you cannot background it again without stopping it.I'm not familiar with rtorrent, but in most programs, you can stop a program with Ctrl+Z. Then, you can background it with bg. This is equivalent to using &, but you can switch back and forth as many times as you want.

---

### Post by soleblaze on 2006-11-28
just remember, most backgrounded apps will die when you logoff.  screen is the better solution.

---

### Post by konsole on 2006-11-28
> **mssever said:**
> I'm not familiar with rtorrent, but in most programs, you can stop a program with Ctrl+Z. Then, you can background it with bg. This is equivalent to using &, but you can switch back and forth as many times as you want.

...and what happens when you bg the job and disconnect the ssh session? You may want to read the OP's question fully.

---

### Post by mannheim on 2006-11-29
You can simply use "nohup" for this. The name "nohup" means  "no hang-up" (or something like that). From a putty session, do something like
```

nohup ***command*** &

```
to start a command (rtorrent maybe). You can then close your putty session (logout) and the command will continue to run. Output from the command, which would normally go to the console, is appended to a file "nohup.out".

nohup is a tool which is already part of your system.

---

### Post by fernando_lopes_jr on 2006-12-01
Thanks konsole I did exactly what you wrote and It worked fine

---

### Post by MJN on 2006-12-01
Something to bear in mind with nohup, particularly when used with a torrent engine that will continue to seed, is that the command cannot be brought back into the 'foreground' and hence could run and run if it doesn't terminate itself.
 
Hence, in this case, you may find your torrent is still being seeded unless of course you've rebooted or manually killed the process! **ps aux** will show you what's running (or even **ps aux |grep rtorrent**).
 
MAthew

---

