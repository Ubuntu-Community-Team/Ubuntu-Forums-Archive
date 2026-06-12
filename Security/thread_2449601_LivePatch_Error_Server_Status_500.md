---
title: "LivePatch Error: Server Status 500"
date: 2020-08-30
forum: Security
---

### Post by vkweb on 2020-08-30
I installed Ubuntu 20.04 LTS a few days back. Initially, live patch was working absolutely fine. But the next day there I saw an internal error so I refreshed using ```
sudo canonical-livepatch refresh
``` but that too didn't fix my problem. So I Googled. People on StackOverflow suggested to disable the livepatch, get a new auth token and then re-enable. I did that exactly but up on doing it i.e.:

```

sudo canonical-livepatch disable

sudo canonical-livepatch enable <auth_token>

```

Then I tried using the GUI client but still the same error:
[img]https://i.imgur.com/bZncn3Q.png[/img]

Any help on this?

Thanks and happy coding.

---

### Post by EuclideanCoffee on 2020-08-30
You retrieved a new auth token, correct and not simply recycled the one that gave you the 500 error?

---

### Post by vkweb on 2020-08-30
I got the token from: [https://auth.livepatch.canonical.com/](https://auth.livepatch.canonical.com/) and applied it on ```
sudo canonical-livepatch enable <auth token>
```

Why the error is saying machine token already exists even though I disabled it before getting a token from the said URL.

---

### Post by EuclideanCoffee on 2020-08-30
Are you using LivePatch correctly? It is meant for servers that cannot reboot for any reason. This supplies a new kernel update without a reboot requirement.

I think I may be confused, so please be patient with my questions.

If you disabled the machine token (I'm not sure how you do this), I would suspect to receive a 500 error using the same auth token... I'm not sure how you disable it because I can only generate one token. This token has a limited use, and if I've used it elsewhere, I would expect a 500 error. If you need more tokens, you can buy more here: [https://buy.ubuntu.com/](https://buy.ubuntu.com/)

---

### Post by vkweb on 2020-08-30
LivePatch is not limited to just servers running Ubuntu. We can use it on Desktop Ubuntu too. I am on Desktop Ubuntu 20.04 LTS.

I disabled it via: `sudo canonical-livepatch disable`. 

Yes there's only one token on my Ubuntu One Account. 

But you see if I have disabled the livepatch on my system then no one should be using that token on this planet right? Then why I see that 500 error. Don't you think it's weird?

---

### Post by EuclideanCoffee on 2020-08-30
I say so because LivePatch isn't really a security concern for you as a desktop user. If you think it's a big problem, you can contact Canonical for customer support for your token. We're community support, so we can provide some security advice while using Ubuntu.

There are a lot of factors, so I'm not so sure if it's weird. Especially if you sign up with desktop that asks if you want livepatch enabled. You may have done it then and have forgotten now.

---

### Post by rnrralston on 2020-08-31
When I did the refresh it told me how to check what's going on.  Looks like an applied patch caused an issue.  Below is what I found.  Won't help with your current issue, unfortunately.

-Rich

MySystem:~$ sudo canonical-livepatch refresh
checking for patches
nothing to apply
kernel: 5.4.0-42.46-generic
patch state: &#10007; the application caused a crash last time it was applied, check system logs with `journalctl -f -t canonical-livepatch`
patch version: 70.3

MySystem:~$ journalctl -f -t canonical-livepatch
-- Logs begin at Tue 2020-03-17 19:26:23 PDT. --
Aug 31 18:24:46 MySystem canonical-livepatch[968]: Client.Check
Aug 31 18:24:46 MySystem canonical-livepatch[968]: error in livepatch check state: check-failed
Aug 31 18:24:46 MySystem canonical-livepatch[968]: Module may have caused kernel crash! Not inserting module.
Aug 31 18:24:46 MySystem canonical-livepatch[968]: To override this warning, remove /var/snap/canonical-livepatch/common/locks/livepatch_Ubuntu_5_4_0_42_46_generic_70_70.3
Aug 31 18:24:46 MySystem canonical-livepatch[968]: during refresh: multiple failures
Aug 31 18:24:46 MySystem canonical-livepatch[968]: during refresh: cannot check: apply-failed
Aug 31 18:24:46 MySystem canonical-livepatch[968]: during refresh: cannot apply patches: lock file "/var/snap/canonical-livepatch/common/locks/livepatch_Ubuntu_5_4_0_42_46_generic_70_70.3" already exists
Aug 31 18:24:46 MySystem canonical-livepatch[968]: error in livepatch check state: check-failed
Aug 31 18:24:46 MySystem canonical-livepatch[968]: failure when getting status: apply-failed
Aug 31 18:24:46 MySystem canonical-livepatch[968]: failure getting status after refresh: apply-failed

---

### Post by vkweb on 2020-09-02
> **EuclideanCoffee said:**
> I say so because LivePatch isn't really a security concern for you as a desktop user. If you think it's a big problem, you can contact Canonical for customer support for your token. We're community support, so we can provide some security advice while using Ubuntu.

There are a lot of factors, so I'm not so sure if it's weird. Especially if you sign up with desktop that asks if you want livepatch enabled. You may have done it then and have forgotten now.

Umm, ya it's not much of a secutiry concern though. 

Btw just for some more clarity, I hope all security, kernel, ubuntu related updates are collected via `sudo apt update` && `sudo apt full-upgrade`...?

Thanks for your constant support @EuclideanCoffee :) I will keep this report open for devs to see and fix if non-trivial.

---

### Post by deadflowr on 2020-09-11
So bumping this as a new livepatch has come through for the first time in a long while.
If you check
```
sudo canonical-livepatch status --verbose
```
is it still erring out or does it show the patch was applied?

>  I will keep this report open for devs to see and fix if non-trivial.
For the devs to know of problems you need to file bug reports:
[https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs")
The devs don't usually come around these parts, willingly at least.

---

