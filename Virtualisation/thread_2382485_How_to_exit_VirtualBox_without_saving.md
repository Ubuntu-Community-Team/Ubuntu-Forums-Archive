---
title: "How to exit VirtualBox without saving?"
date: 2018-01-14
forum: Virtualisation
---

### Post by frappe792 on 2018-01-14
Hi all,

I have a profile saved with virtual box and loads exactly how I want it to everytime.

However when I shutdown - it's always prevented because VB ask's 

1. Save the machine state
2. Send the shutdown signal
3. Power off the machine

I simply want the application to ignore the shutdown command so the computer can continue to shut down and quickly. It's pretty annoying to have to wait to save the machine state. I simply want to start the same image everytime. No new changes in each session.

---

### Post by monkeybrain20122 on 2018-01-14
When you shut down VB from the menu (instead of shutting down from within the guest OS) it is like pressing power off in  a real computer so it may not be a clean exit. The VB is asking you what you want to do, you can just choose power off the machine.

---

### Post by frappe792 on 2018-01-14
> **monkeybrain20122 said:**
> When you shut down VB from the menu (instead of shutting down from within the guest OS) it is like pressing power off in  a real computer so it may not be a clean exit. The VB is asking you what you want to do, you can just choose power off the machine.


If I do that, it then wants to boot up like a normal pc. That's not what I want.

Currently I am using the command XKILL (I've setup a keyboard shortcut for it). I will kill VirtualBox so I don't have to wait for it.
Sure it's not a clean exit, but who cares? Every time I start saved profile to VirtualBox it resumes from the saved state and does it without any issues.

---

### Post by TheFu on 2018-01-15
> **frappe792 said:**
> If I do that, it then wants to boot up like a normal pc. That's not what I want.

Currently I am using the command XKILL (I've setup a keyboard shortcut for it). I will kill VirtualBox so I don't have to wait for it.
Sure it's not a clean exit, but who cares? Every time I start saved profile to VirtualBox it resumes from the saved state and does it without any issues.

So far.  Closing the host when a VM is running isn't safe.

I would take a snapshot and revert to that snapshot after closing.  [https://www.virtualbox.org/manual/ch01.html#snapshots](https://www.virtualbox.org/manual/ch01.html#snapshots)  When it comes to virtualbox stuff, I find going to the docs for virtualbox has the best, most complete, answers.

Think of snapshots as layers stored in different files. Any corruption in the last file, that you don't care about, just doesn't matter.

---

### Post by frappe792 on 2018-01-16
> **TheFu said:**
> So far.  Closing the host when a VM is running isn't safe.

What isn't safe about it? I have done it for ages, no issue.

---

### Post by TheFu on 2018-01-16
> **frappe792 said:**
> What isn't safe about it? I have done it for ages, no issue.

[http://novabackup.novastor.com/blog/top-6-data-loss-causes-and-top-10-preventions/](http://novabackup.novastor.com/blog/top-6-data-loss-causes-and-top-10-preventions/) - ref #5.  Shutting down a VM without letting it go through its normal shutdown procedures is like pulling the power plug.  That can lead to data corruption for any open files.

[https://ubuntuforums.org/showthread.php?t=2382612](https://ubuntuforums.org/showthread.php?t=2382612) is an example that could happen to the forced off VM.

---

### Post by frappe792 on 2018-01-19
> **TheFu said:**
> That can lead to data corruption for any open files.

You are only referring to files within the VB?

If so, I don't care for those.

---

