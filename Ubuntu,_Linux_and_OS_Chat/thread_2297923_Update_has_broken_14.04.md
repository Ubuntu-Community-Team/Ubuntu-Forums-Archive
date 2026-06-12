---
title: "Update has broken 14.04"
date: 2015-10-07
forum: Ubuntu, Linux and OS Chat
---

### Post by mikebailey-u on 2015-10-07
Naming this kernel "Trusty" was deliciously ironic. Somebody around here has an awesome sense of humor. The one thing I dread most in my life is the latest Trusty LTS update, which honestly just makes me wish I was back in combat again.

---

### Post by howefield on 2015-10-07
Moved from support areas and to own thread.

---

### Post by deadflowr on 2015-10-07
Seems the breakage seen today is from having -proposed enabled in the repository sources.

Since the 3.13.0-66 is only available in there.
Sometimes proposed should be nicknamed prepare, as you need to be prepared that these packages still need testing.

edit: Seems the lts-vivid kernel 3.19.0-31 is also still in proposed.
current bug report on that one here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1503647](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1503647)

---

### Post by pauljw on 2015-10-07
> **mikebailey-u said:**
> Naming this kernel "Trusty" was deliciously ironic. Somebody around here has an awesome sense of humor. The one thing I dread most in my life is the latest Trusty LTS update, which honestly just makes me wish I was back in combat again.

It's not that big of a deal, select advanced options from the grub menu, pick the previous kernel and boot with it until the fixed kernel is available.  You'll need to make that choice each time you boot the machine unless you go thru reverting back to the earlier kernel permanently.  Before you ask, I don't know that procedure off the top of my head.

---

### Post by thanais on 2015-10-12
Is this the reason I had a system with no Unity after login, with only a background picture and 30 "Report problem" windows? 

I was able to have a functioning system by booting in a previous kernel (3.13.0-65 and back) but with major slowdown and graphics problems.

Finally I re-installed Ubuntu without losing data and programs following this [http://ubuntuforums.org/showthread.php?t=2057342](http://ubuntuforums.org/showthread.php?t=2057342).

---

### Post by monkeybrain20122 on 2015-10-12
Why is "proposed" enabled? It should not be by default and you should never install from proposed unless you are a tester.

---

### Post by coffeecat on 2015-10-13
The OP managed to register, post and log out all within 12 minutes, and has not been back in the 5 days that have ensued, which makes me wonder about their motivation for posting.

@mikebailey-u, you have been given the most likely explanation for the problem you have observed, namely enabling the proposed repository. If you did indeed enable the proposed repository, blaming Ubuntu for your self-induced problem is hardly constructive. Do you have anything constructive to say? If not, I'll close the thread.

---

### Post by pauljw on 2015-10-13
It was a real problem, I was affected by it.  I wasn't aware that I had checked the proposed box so I have now unchecked it.  :)  Always good when I learn from my experience good or bad.  Thanks.

---

### Post by coffeecat on 2015-10-15
> **coffeecat said:**
> Do you have anything constructive to say? If not, I'll close the thread.

And more than 48 hours later, seemingly not. I'll close the thread then.

---

