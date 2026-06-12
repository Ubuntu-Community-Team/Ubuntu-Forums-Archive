---
title: "Virtualbox startup and repair problems"
date: 2010-12-11
forum: Virtualisation
---

### Post by parminides on 2010-12-11
A couple of years ago I got virtualbox running a 64 bit Vista guest in a 64 bit Linux host (Fedora back then, now Ubuntu 10.04). The Virtualbox Vista is from vmdk files, not a separate Vista partition.

It's been a workhorse for the very rare occasions that I need it. Everything worked fine until this afternoon. 

I put my laptop in suspend mode to carry it to another room. The battery jiggled loose, and the laptop lost power while virtualbox was running.

Now the Vista guest won't run. If I try to startup, I get a message that says "Windows failed to start. A recent hardware or software change might be the cause."

The messages further say that if power was interrupted during startup, Start Windows Normally. If I try that, the Vista window just disappears.

The other suggestion is to "Launch Startup Repair," which means to insert the Vista installation disk and restart computer (i.e., the virtual machine).

If I try that, I get a message that "This PC is not supported by the System Recovery Discs. You will not be able to recover this system with these discs."

Is there any way to recover my previous virtual machine? I spent a few hours recently uninstalling software to save space and speed things up.

If there's a relatively painless way to restore the previous state, I'd rather not start from scratch. I don't even remember how I set up the vmdk files a couple of years ago. Thank you for your attention.

---

### Post by HermanAB on 2010-12-13
Howdy,

You can try writing the VM to a spare hard disk using dd, then running the Microsoft repair CD and finally converting it back to a VM again, but that would be hugely time consuming.

---

### Post by CharlesA on 2010-12-13
Got a recent snapshop?

---

### Post by parminides on 2010-12-13
I don't have a recent snapshot. I didn't know about that feature but will study how it works.

Like I said, I recently spent many hours uninstalling loads of stuff to try to speed it up, and I was hoping there was a quick and painless way to fix my problem.

I gave up and opted for the slow and painful (but not too bad).

I don't really write files to the VM. I mainly use for an email program that was used where I used to work.

Also, I had backed up the VM to an external drive several months ago.

Since I didn't have to worry about losing files, I ended up just replacing my broken VM with the backup and spending several more hours re-uninstalling everything.

Then I made a snapshot. :)

Thanks for your suggestions. Others may have a similar problem, but the matter is closed for me.

---

### Post by CharlesA on 2010-12-13
Glad you got it sorted. Don't forget to mark the thread as solved from thread tools. :)

---

