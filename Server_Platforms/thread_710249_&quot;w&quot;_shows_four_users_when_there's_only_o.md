---
title: "&quot;w&quot; shows four users when there's only one"
date: 2008-02-28
forum: Server Platforms
---

### Post by davidshere on 2008-02-28
I push "w" and it says there's four users.  There's only one.  What gives?

```
david@warthog:~$ w
 09:24:53 up 7 days, 14:25,  4 users,  load average: 0.00, 0.00, 0.04
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
david    pts/0    raptor           08:58    1.00s  0.94s  0.02s w
david@warthog:~$ 

```

---

### Post by craigp84 on 2008-02-29
The w utility is just reading utmp / wtmp to figure out who's currently logged in and who they are.

Either someone's been editing the file... do you have someone on the system that doesn't want to be known? Is this host accessible from the net? Do you see them in a "/bin/ps" (important you specify the full path right now) ? Can you compare the md5sum of your /bin/ps with another system of the same build / updates?

Or, a prog which writes to wtmp has created the login entries, but died before being able to write the logout entries... had any issues with anything core dumping recently?

Hope it helps,

-c

---

### Post by Mr. C. on 2008-02-29
How many Terminal Windows or TTY windows have shells running on them?

MrC

---

### Post by davidshere on 2008-02-29
At the terminal, I'm unable to get a login; I tried Alt-F1 Through Alt-F8 and the screen does not change.  I'm sure if I reset I'll get it back.  I had gnome running but I did a Ctrl-Alt-F7 to get a TTY session.  I got to a text only screen but couldn't get anything after that.  I've stopped gnome.

```
david@warthog:~$ /bin/ps
  PID TTY          TIME CMD
25703 pts/0    00:00:01 bash
26159 pts/0    00:00:00 ps
david@warthog:~$ 

```

When I do /bin/ps ax I get these:
```
 3958 tty4     Ss+    0:00 /sbin/getty 38400 tty4
 3959 tty5     Ss+    0:00 /sbin/getty 38400 tty5
 3966 tty3     Ss+    0:00 /sbin/getty 38400 tty3
 3975 tty6     Ss+    0:00 /sbin/getty 38400 tty6

```

Not sure how to tell if there's a login there.

The server is available by SSH over the internet, but at a non-standard port.  Telnet is off.

---

### Post by astrotech226 on 2008-02-29
What's the output of this?

```
ps -ef | grep pts
```

---

### Post by davidshere on 2008-02-29
```
david@warthog:~$ ps -ef | grep pts
david     6695  6693  0 10:27 ?        00:00:00 sshd: david@pts/0
david     6696  6695  0 10:27 pts/0    00:00:00 -bash
david     6721  6696  0 10:33 pts/0    00:00:00 ps -ef
david     6722  6696  0 10:33 pts/0    00:00:00 [grep]

```

warthog is a machine at home.  My machine here at work shows the "correct" user count:
```
david@raptor:~$ w
 10:34:36 up 2 days, 21:08,  3 users,  load average: 0.20, 0.31, 0.29
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
david    tty7     :0               Tue13    0.00s  4:48   1.26s x-session-manager
david    pts/0    :0.0             10:34    0.00s  0.17s  0.00s w
david    pts/2    :0.0             08:24    2:07   5.66s  5.48s ssh hornet.davidshere.com

```

My other machine at home, though, does not:

```
david@lancer:~$ w
 10:37:34 up 6 days, 13:44,  4 users,  load average: 0.32, 0.22, 0.18
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
david    tty1     -                Mon19    3days  0.06s  0.04s -bash
david    tty9     :0               Mon19    3:41  34:26m  0.38s x-session-manager
david    pts/0    raptor           10:37    1.00s  0.01s  0.00s w

```

Am I worrying about nothing?

---

### Post by astrotech226 on 2008-02-29
> **davidshere said:**
> 
Am I worrying about nothing?

Probably.  It's never happened to me, but I've read the utmp and wtmp files can become corrupted.  I'm not sure what the correct procedure is to fix it, but you could maybe do a:

sudo sh -c "cat /dev/null > /var/log/utmp"
sudo sh -c "cat /dev/null > /var/log/wtmp"

Reboot and see what happens.  Logging out and back in didn't seem to help because the system seems to be caching the "w" information even when the log files are zeroed out.  I just tried it on one of my lab servers and it didn't break anything.  The user counts are also correct.

---

### Post by davidshere on 2008-02-29
I tried that and it still shows 4.

I did notice that I have a wtmp.1 file in my /var/log directory:

```
david@warthog:/var/log$ more utmp
david@warthog:/var/log$ more wtmp
david@warthog:/var/log$ more wtmp.1
~~~reboot2.6.22-14-generic
<}&#65533;G&#65533;&#65533;^L%tty44LOGIN
<}&#65533;G
&tty55LOGIN
<}&#65533;G2~~~runlevel2.6.22-14-generic
<}&#65533;G&#65533;
)tty22LOGIN
<}&#65533;G3tty11LOGIN
<}&#65533;G
4tty66LOGIN
<}&#65533;G*tty33LOGIN
<}&#65533;G
&#65533;tty7:0david:0
a~&#65533;&#65533;tty7:0:0
m&#65533;&#65533;G
~~~reboot2.6.22-14-generic
N&#65533;&#65533;Ge
&#65533;tty44LOGIN
N&#65533;&#65533;G&#65533;tty55LOGIN
N&#65533;&#65533;G
2~~~runlevel2.6.22-14-generic
N&#65533;&#65533;GBtty33LOGIN
N&#65533;&#65533;G
tty11LOGIN
N&#65533;&#65533;Gtty66LOGIN
N&#65533;&#65533;G
&#65533;tty22LOGIN
N&#65533;&#65533;G~~~reboot2.6.22-14-gen
ric*&#65533;&#65533;G

2~~~runlevel2.6.22-14-generic
*&#65533;&#65533;G¤^L  &#9500;&#9500;&#8804;4                            4   LOGIN
                                                                                                            *ƒ¢G
                                          î  &#9500;&#9500;&#8804;5                            5   LOGIN
                                                                                                                           *ƒ¢G                           ø  &#9500;&#9500;&#8804;3                            3   LOGIN
                                                                                                            *ƒ¢G
                                          û  &#9500;&#9500;&#8804;1                            1   LOGIN
                                                                                                                           *ƒ¢G                           ü  &#9500;&#9500;&#8804;6                            6   LOGIN
                                                                                                            *ƒ¢G
                                          ð  &#9500;&#9500;&#8804;2                            2   LOGIN
                                                                                                                           *ƒ¢G                           E  &#9500;&#9500;&#8804;7                            :0  &#9229;&#9618;&#9524;&#9227;&#9229;                           :0
                                                                                                            Jƒ¢G
                                          Õ+  &#9147;&#9500;&#9149;/2                           /2  &#9229;&#9618;&#9524;&#9227;&#9229;                           :0.0
                                                                                                                           È‰¢G¹³                              &#9147;&#9500;&#9149;/2                           /2  &#9229;&#9618;&#9524;&#9227;&#9229;
                                                                                                            ÷‰¢G
€                                       E  &#9500;&#9500;&#8804;7                            :0                                  :0
                                                                                                                           £÷¢G                           62  ·                               ··  &#9148;&#9508;&#9532;&#9484;&#9226;&#9524;&#9226;&#9484;                        2.6.22-14-±&#9226;
&#9226;&#9148;&#9227;&#9228;                                                                                                            £÷¢G
                                            ·                               ··  &#9148;&#9226;&#9225;&#9146;&#9146;&#9500;                          2.6.22-14-±&#9226;&#9532;&#9226;&#9148;&#9227;&#9228;
                                                                                                                           ø¢G¡ö
                          š  &#9500;&#9500;&#8804;4                            4   LOGIN
                                                                                                            ø¢G
                                          ›  &#9500;&#9500;&#8804;5                            5   LOGIN
                                                                                                                           ø¢G                           2   ·                               ··  &#9148;&#9508;&#9532;&#9484;&#9226;&#9524;&#9226;&#9484;                        2.6.22-14-±&#9226;
&#9226;&#9148;&#9227;&#9228;                                                                                                            ø¢G
                                        ¥  &#9500;&#9500;&#8804;3                            3   LOGIN
                                                                                                                           ø¢G                           ¨  &#9500;&#9500;&#8804;1                            1   LOGIN
                                                                                                            ø¢G
                                          ©  &#9500;&#9500;&#8804;6                            6   LOGIN
                                                                                                                           ø¢G                             &#9500;&#9500;&#8804;2                            2   LOGIN
                                                                                                            ø¢G

&#9229;&#9618;&#9524;&#9227;&#9229;@&#9516;&#9618;&#9148;&#9500;&#9252;&#9146;±:/&#9524;&#9618;&#9148;/&#9484;&#9146;±$ 

```

I can reboot, nobody depends on this server but me... I'm just trying to learn how to solve problems without rebooting.

---

### Post by Mr. C. on 2008-02-29
Let's clarify.

The **w** command uses the information that comes from the **utmp** database.  That database is updated *if* a terminal session, ftp session or other sessions is configured to log information about the login.  Some programs log this information, some don't, some use the PAM database, others don't.

The man page for utmp explains this:
> 
man 5 utmp

The file allows one to discover information about who is currently using the
system.  There may be more users currently using the system, because not
all programs use utmp logging.

Don't rely on w to give you a list of users connected to terminals.  Rather, it gives you partial information about processes that are running *that logged information into utmp*.

This also requires that the disconnect occurs.  Sometimes a remote ssh is dropped, but the server side sshd handler has not detacted, or users kill their session and utmp entry removal calls were not made.  In these cases, what's in w tmp at best reflects only partial information.  Frankly, it is not a very useful command anymore, and really never was.

Use **ps** to see how many interactive, login shells are running at any given time, and also look at **last** and **users** if you are interested.

Don't bother trying to nuke your utmp.  It doesn't get corrupted on its own, and you'll end up doing more harm than good if a) you don't know what your doing - it is a binary database, and b) confuse other programs that may depend on information there.

MrC

---

### Post by Mr. C. on 2008-02-29
> **davidshere said:**
> 
I can reboot, nobody depends on this server but me... I'm just trying to learn how to solve problems without rebooting.

You haven't shown that there was a problem yet.  I see only misunderstanding and misinterpretation of the data.

Those files, as I mentioned, are binary data; not readably by ASCII viewers.  And the system rotates out previous version periodically.  That is what the .1 versions are.

MrC

---

### Post by astrotech226 on 2008-02-29
The wtmp.1 file is simply from your log rotation so you don't need to worry about that.

---

### Post by davidshere on 2008-02-29
well I've already hosed the file... but I haven't rebooted yet.

```
david@warthog:~$ last
david    pts/0        raptor.steelerub Fri Feb 29 11:09   still logged in   

wtmp begins Fri Feb 29 11:08:35 2008
david@warthog:~$ users
david

```

---

### Post by astrotech226 on 2008-02-29
> **Mr. C. said:**
> 
This also requires that the disconnect occurs.  Sometimes a remote ssh is dropped, but the server side sshd handler has not detacted, or users kill their session and utmp entry removal calls were not made.  In these cases, what's in w tmp at best reflects only partial information.  Frankly, it is not a very useful command anymore, and really never was.

MrC

I guess I never understood this correctly.  I was assuming this was a little more reliable like the entries in the /proc directory.

---

### Post by astrotech226 on 2008-02-29
> **davidshere said:**
> well I've already hosed the file... but I haven't rebooted yet.


You shouldn't have to reboot.  If you open a new terminal, you'll see the information update like it should.  But your user count will be higher than the display until you reboot.

Like MrC said, it probably doesn't matter much anyway.

---

### Post by Mr. C. on 2008-02-29
> **astrotech226 said:**
> I guess I never understood this correctly.  I was assuming this was a little more reliable like the entries in the /proc directory.

Sorry, it never has been.

Early you asked about the "getty" entries.  Those are the processes running on TTYs  (real, or simulated); they spawn login's for those TTYs and wait for you to enter your usename/password, which then replace themselves with the login shell.  Getty's don't modify the utmp/wtmp databases - the login process will, after successful login.

---

### Post by davidshere on 2008-02-29
My question is "If this is a problem, how do I fix it without rebooting?"... if it's not a problem, that's fine.

---

### Post by astrotech226 on 2008-02-29
> **Mr. C. said:**
> 
Early you asked about the "getty" entries.  Those are the processes running on TTYs  (real, or simulated); they spawn login's for those TTYs and wait for you to enter your usename/password, which then replace themselves with the login shell.  Getty's don't modify the utmp/wtmp databases - the login process will, after successful login.

I don't think I asked about the ttys.  I asked for the ps list grepping out the pts.  Which come from telnet or sshd sessions, correct?  I was curious to see if there were any remote users logged in.

---

### Post by Mr. C. on 2008-02-29
> **astrotech226 said:**
> I don't think I asked about the ttys.  I asked for the ps list grepping out the pts.  Which come from telnet or sshd sessions, correct?  I was curious to see if there were any remote users logged in.

Upon showing a listing of getty's, you asked "Not sure how to tell if there's a login there." 

 If there is a getty running on that TTY, there by definition cannot be a login, since getty is what replaces itself with login, and thence a shell.  getty == not logged in on that tty.

---

### Post by Mr. C. on 2008-02-29
FYI: [https://bugs.launchpad.net/upstart/+bug/183729](https://bugs.launchpad.net/upstart/+bug/183729)

---

### Post by astrotech226 on 2008-02-29
> **Mr. C. said:**
> Upon showing a listing of getty's, you asked "Not sure how to tell if there's a login there."

Man...  You have me thoroughly believing that I've lost my marbles.  I could swear I didn't ask that!  I went back and checked and it wasn't me.  I'm doing a lot of studying at the same time so it was entirely possible. :)

---

### Post by Mr. C. on 2008-02-29
s/you/davidshere/g

---

