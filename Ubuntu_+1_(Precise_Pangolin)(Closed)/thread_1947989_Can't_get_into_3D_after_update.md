---
title: "Can't get into 3D after update?"
date: 2012-03-27
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by neu5eeCh on 2012-03-27
I'm not positive about this, but I notice that I have no compiz options in Ubuntu Tweak, and that my dash button is solid; and that I've lost some general functionality related to compiz.

Is there a way to force 3D?[B]

Edit:[/B] Ok. I'm definitely not able to get into 3d. Something got mucked up.

---

### Post by rtalcott on 2012-03-27
Same here but 2d is fine...however this is on an AMD board...my Intel laptop is fine.
rt

---

### Post by ratcheer on 2012-03-27
I couldn't go into 3D when I had the fglrx 12.2 driver in Precise (it worked fine in Oneiric), no matter what I tried. I finally got back to 3D when they put a newer driver in the repo a few days ago (12.3 or 12.4, whatever it is).

Tim

---

### Post by neu5eeCh on 2012-03-27
This is on an Intel Board. I'm trying to file a bug report but keep getting an unspecified error from launchpad. Frustrating.

---

### Post by neu5eeCh on 2012-03-27
[https://bugs.launchpad.net/unity/+bug/966504](https://bugs.launchpad.net/unity/+bug/966504)

Got it. The mistake was on launchpad's part. Apparently, it didn't like something about the tags that were applied but ubuntu-bug.

**Edit:** I've also got a second USB mouse that's acting up - like my first one. This makes me think there's a kernel or video driver conflict somewhere.

---

### Post by mc4man on 2012-03-27
It may be related to this (the error seen her when trying to get compiz to restart
[https://bugs.launchpad.net/ubuntu/+source/compizconfig-backend-gconf/+bug/932125](https://bugs.launchpad.net/ubuntu/+source/compizconfig-backend-gconf/+bug/932125)

Kinda surprising that they released all these glib, gtk3, compiz, gtk2 packages today 

Got 3d back here by reverting all of the above, not sure yet where the offending was exactly

---

### Post by rtalcott on 2012-03-27
I did some updates and tried again...I can get in but it's slow...maybe a minute before it moves from the login screen.
rt

---

### Post by neu5eeCh on 2012-03-27
> **mc4man said:**
> It may be related to this (the error seen her when trying to get compiz to restart
[https://bugs.launchpad.net/ubuntu/+source/compizconfig-backend-gconf/+bug/932125](https://bugs.launchpad.net/ubuntu/+source/compizconfig-backend-gconf/+bug/932125)

Kinda surprising that they released all these glib, gtk3, compiz, gtk2 packages today 

Got 3d back here by reverting all of the above, not sure yet where the offending was exactly

Can you explain how you reverted those - using Synaptic? That's not something I've done before.

---

### Post by mc4man on 2012-03-27
> **VTPoet said:**
> Can you explain how you reverted those - using Synaptic? That's not something I've done before.
There may not be any need to - give me a few
On my other install trying to break - 
Do you have the proposed repo enabled?

---

### Post by neu5eeCh on 2012-03-27
> **mc4man said:**
> There may not be any need to - give me a few
On my other install trying to break - 
Do you have the proposed repo enabled?

No, I've been playing it fairly straight.

**Edit:** The latest series of updates to Ubuntu Beta (as of April 2012) appear to have solved this issue. Marking the thread solved.

---

### Post by neu5eeCh on 2012-03-27
> **rtalcott said:**
> I did some updates and tried again...I can get in but it's slow...maybe a minute before it moves from the login screen.
rt

I noticed that compiz updated this morning. I just upgraded again, right before writing this, but still can't load 3D. 

Rats.

---

### Post by mc4man on 2012-03-27
Not sure what happened - definitely lost 3d this morning after updating, though on that install was using proposed.

On my straight up install just went ahead & updated all (no proposed), all was fine. 
Added proposed & updated all  - no problems

Went back to the other install where I'd downgraded & updated all inc. proposed, now it's fine??

The only other thing I did on the previously borked install was when it sent me to 2d I ran compiz --replace a couple of times (caused the crash I linked) & ran unity --replace once

So maybe try

---

### Post by neu5eeCh on 2012-03-27
Interesting, just tried compiz --replace (why didn't I think of that?) and got the following error:

compiz crashed with SIGSEGV in GLib::Source:: prepare_vfunc()

---

### Post by mc4man on 2012-03-27
> **VTPoet said:**
> Interesting, just tried compiz --replace (why didn't I think of that?) and got the following error:

compiz crashed with SIGSEGV in GLib::Source:: prepare_vfunc()

That was the error I was seeing, maybe try a unity --relace, then restart & try an ubuntu (3d) login again

---

### Post by neu5eeCh on 2012-03-27
> **mc4man said:**
> That was the error I was seeing, maybe try a unity --relace, then restart & try an ubuntu (3d) login again

Yeah... none of it is working for me. If you could visit the bug report and add a note, that might get someone's attention. In the meantime, I'll keep fiddling with this.

---

### Post by WorLord on 2012-03-27
There's already a bug filed with a ton of heat on it.

The fix is committed, but hasn't yet been built.  

I installed packages from the "unity-staging" repo, and that fixed the issue, so the very next time compiz/unity/nux is released to the actual repos, the issue will be resolved.

---

### Post by neu5eeCh on 2012-03-27
> **WorLord said:**
> There's already a bug filed with a ton of heat on it.

The fix is committed, but hasn't yet been built.  

I installed packages from the "unity-staging" repo, and that fixed the issue, so the very next time compiz/unity/nux is released to the actual repos, the issue will be resolved.

Can you give a link to the bug? I can mark mine as a duplicate that way. Right now I'm trying out the Cairo Session. They've made some nice changes.

---

