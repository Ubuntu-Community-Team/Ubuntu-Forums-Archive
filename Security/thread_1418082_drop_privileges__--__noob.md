---
title: "drop privileges  --  noob"
date: 2010-02-28
forum: Security
---

### Post by brusegadi on 2010-02-28
After updating my system, I temporarily have super user privileges.  If I start firefox right after updating my system, does firefox start as superuser?  How do I drop these privileges?  I remember that at some point a pair of keys used to show up on my panel, and I could drop the privileges by clicking on those keys.... but now that does not happen anymore, and I'd love to find a way to do just that (its kinda like a graphical version of sudo with the k option) Thanks,  B

---

### Post by ajgreeny on 2010-02-28
No, I don't think that you will be starting Firefox with sdmin privileges just because you used the terminal or synaptic to update; only that terminal or that synaptic would have superuser status, no other GUI application.

I have looked at Linux Mint recently and seem to remember that had the keys icon to loose superuser status, but I don't remember seeing it in ubuntu, but perhaps I'm wrong about that.  However, you can change the time that sudo remains actice by following the info here:-
[https://help.ubuntu.com/community/RootSudoTimeout](https://help.ubuntu.com/community/RootSudoTimeout)

---

### Post by brusegadi on 2010-02-28
> **ajgreeny said:**
> No, I don't think that you will be starting Firefox with sdmin privileges just because you used the terminal or synaptic to update; only that terminal or that synaptic would have superuser status, no other GUI application.

I have looked at Linux Mint recently and seem to remember that had the keys icon to loose superuser status, but I don't remember seeing it in ubuntu, but perhaps I'm wrong about that.  However, you can change the time that sudo remains actice by following the info here:-
[https://help.ubuntu.com/community/RootSudoTimeout](https://help.ubuntu.com/community/RootSudoTimeout)

I have the impression that that setting only affects sudo, and not the GUI super-user status.  I say this because I have tried updating, opening a terminal, saying sudo with the -k option, and I still had super-user status on the GUI after doing that.  I may try to play around with the time-stamp and seeing how it interacts with the GUI.  Thanks!

B

---

### Post by Bachstelze on 2010-02-28
> **brusegadi said:**
> After updating my system, I temporarily have super user privileges.  If I start firefox right after updating my system, does firefox start as superuser?

No. In order to have superuser privileges in a program, you *must* start that program with [font=monospace]sudo[/font] or [font=monospace]gksudo[/font]. Root privileges are given on a per-program basis, not to a user as a whole.

> **brusegadi said:**
> I say this because I have tried updating, opening a terminal, saying sudo with the -k option, and I still had super-user status on the GUI after doing that.

What makes you think that?

---

### Post by Agent ME on 2010-02-28
> **brusegadi said:**
> I have the impression that that setting only affects sudo, and not the GUI super-user status.  I say this because I have tried updating, opening a terminal, saying sudo with the -k option, and I still had super-user status on the GUI after doing that.
So you started a program like Synaptic (which required you to enter your password), ran "sudo -k" in a terminal, and then noticed Synaptic still had superuser powers?

That's correct. Once a program is started as superuser, it stays as superuser. Running "sudo -k" just makes it so you need to enter in your password to start another program as superuser.

---

### Post by Baneblade on 2010-02-28
"Those Keys" still show as far as i know when you are running a GUI app with sudo privs. You should just be able to click on them to remove the temporary privs.

There is no need to worry about it accidently starting other apps as root however, as apps are granted root privs only when authorised by the user.

---

### Post by rookcifer on 2010-03-01
OP, the only way for what you described to happen would be if you created a separate root account and logged into it and then opened firefox (or whatever other app).

---

### Post by ajgreeny on 2010-03-01
Just to clarify the situation, I do not see those keys in ubuntu at all as far as I'm aware, though I have seen them somewhere, Mint 8, I think.  How is it that some do and I don't?

---

### Post by brusegadi on 2010-03-02
I get it now.  Thanks.  Oh, and about the keys... I saw them when I first installed, and eventually they stopped showing up.  I see something similar in my Mandriva installation.  Oh, and no, I would not create a root account in Ubuntu :)  Thanks everyone.  B

---

