---
title: "Creating Virtual Disk with VirtualBox just hangs at 0% (Zero Percent) forever"
date: 2010-01-05
forum: Virtualisation
---

### Post by zappal on 2010-01-05
Hi ya'll,

I've searched all around and cant find anyone reporting this.

I have a Dual Core processor and its showing one processors running at 100% while I just sit here and wait for my 20GB virtual disk to be created. This creation of Virtual Disk always stays stuck at 0% no matter what size I try to create.

If I click to cancel creating the virtual disk, it just says cancelling and just hangs forever with one processor still showing 100%
I cant even kill the process VBoxSVC
Its showing as a Zombie

I'm just ending up rebooting my system.

Running:
Ubuntu 9.10 all updated as of Jan 5 2010
VirtualBox 3.1.2 r56127

---

### Post by gdonwallace on 2010-01-06
I am having the same problem with 3.1.2

So I uninstalled and re-installed 3.0.12, and am having the same issue.

I am running dual core cpu with 32 bit Ubuntu 9.10.

Uname -a reports a i686 arch on my system.  Zappal you might want to look at that too.  Because it is dual core, you may also be i686 instead of i386 which is what Virtualbox offers for download option. (Along with AMD64)

Just a thought.  Will continue to check into this.

---

### Post by snowch on 2010-01-30
Did you fix this? - I'm having the same problem, Sat 30th Jan.

---

### Post by jmdevil on 2010-05-07
Any news about this? I have the same problem using Lucid and Vbox 3.1.6

Regards,

-- jm

---

### Post by fideles on 2010-07-31
-

---

### Post by gdonwallace on 2010-08-04
Here is what I did to fix this problem.  I created a dynamic expanding disk, which I don't think really helped in fixing the problem.

What I found was that there is a known issue with Virtual Box and EXT4 file systems.  The workaround is this.  Go to the settings for the hard drive, there is a check box titled "Use Host I/O settings", make sure this is checked, and You should be able to create the VM that you want.

---

