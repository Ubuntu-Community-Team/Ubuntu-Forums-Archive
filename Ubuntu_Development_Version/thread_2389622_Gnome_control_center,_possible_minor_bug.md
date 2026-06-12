---
title: "Gnome control center, possible minor bug"
date: 2018-04-19
forum: Ubuntu Development Version
---

### Post by Jay_Dogg on 2018-04-19
Hi ):P,

I probably encountered a minor bug and just wanted to check if the "Settings" (gnome-control-center) in 18.04 misbehaves on computers other than my own. Go to the "Users" page in Details and click "Unlock" and then cancel without typing in your password. The application then crashes and will crash every time I click the "Unlock" button after that. Does this happen on your computers? 

The terminal produces this:

(gnome-control-center:6457): GLib-GIO-CRITICAL **: 11:44:17.484: g_permission_acquire_finish: assertion 'G_IS_PERMISSION (permission)' failed
Segmentation fault (core dumped)

---

### Post by PaulW2U on 2018-04-19
> **Jay_Dogg said:**
> I probably encountered a minor bug and just wanted to check if the "Settings" (gnome-control-center) in 18.04 misbehaves on computers other than my own.
Yes, I see exactly the same. 

As I was presented with a prompt to report the issue I went ahead and reported the problem to Launchpad:- [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1765353](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1765353)

As the bug report is marked private at present you won't be able to look at it or mark it as affecting you too. Sorry.  :)

---

### Post by dino99 on 2018-04-19
@Paulw2U

can you switch from 'private' to 'public' for your report please  ;)

---

### Post by PaulW2U on 2018-04-19
> **dino99 said:**
> can you switch from 'private' to 'public' for your report please  ;)
Sorry for delay.  Now posting from mobile sat outside in the glorious UK sunshine. :)

Bug now set for public viewing.

---

### Post by dino99 on 2018-04-19
Get the same issue too.

---

### Post by corradoventu on 2018-04-19
Same for me, see [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1765353](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1765353)

---

### Post by mc4man on 2018-04-19
I think you'll find that after doing this any subsequent use of pkexec will fail until a log out/in is done.

In fact this is not really gnome-control-center bug per se, any app that calls pkexec will show same behavior if the dialog is canceled before password is entered.
So bug is likely either a gnome-shell or something related one.
Behavior is not seen in an unity session.

Edit: if after causing this to happen if gnome-shell is restarted then ability to call pkexec is restored (alt+F2 > r

---

### Post by PaulW2U on 2018-04-19
> **mc4man said:**
> In fact this is not really gnome-control-center bug per se, any app that calls pkexec will show same behavior if the dialog is canceled before password is entered.
So bug is likely either a gnome-shell or something related one.
Thanks for the information mc4man. You are indeed correct.

I just dismissed the authorisation dialog when starting synaptic. There was no crash but synaptic couldn't be started until gnome-shell had been restarted.

---

### Post by dino99 on 2018-04-19
@mc4man

Looks like a missing event management for such a case (which is not supposed to happen so often, but should be managed).
Then the problem is to point to the faulty app/lib, which can be different than g-c-c indeed.

---

### Post by mc4man on 2018-04-19
> **dino99 said:**
> @mc4man

Looks like a missing event management for such a case (which is not supposed to happen so often, but should be managed).
Then the problem is to point to the faulty app/lib, which can be different than g-c-c indeed.
It's from the latest gnome-shell upgrade, if one was to revert to previous then this does not occur.

---

### Post by mc4man on 2018-04-21
A fix has been proposed to merge in  gnome-shell, should eventually find way into 18.04.
Till then best to avoid cancelling any pkexec auth. If inadventantly done alt+F2 > r will for the most part reset the pkexec table.

---

### Post by PaulW2U on 2018-04-23
Looking through the IRC logs, and specifically [https://irclogs.ubuntu.com/2018/04/23/%23ubuntu-desktop.html](https://irclogs.ubuntu.com/2018/04/23/%23ubuntu-desktop.html), it seems the issues raised here, the crash and the cancelling of the authorisation dialog, might be fixed for the 18.04 release. At least the developers are talking about it. :D

---

