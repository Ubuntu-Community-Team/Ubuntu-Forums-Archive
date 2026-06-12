---
title: "Should Everything in Root Directory Be Owned By Root?"
date: 2014-11-30
forum: Security
---

### Post by astarmathsandphysics on 2014-11-30
I have an unowned file at /root/apf-9.7-2/files/internals/rab.ports

Can I have this file owned by root?
Should it be owned by root?

---

### Post by papibe on 2014-11-30
Hi astarmathsandphysics.

By default the /root directory is empty (besides a few hidden config files).

It looks like you manually downloaded and unpacked the apf firewall in order to install it. If you trust the download source, it shouldn't be a problem.

However, I, personally, would at least remove the unpacked content in case there are binaries with the wrong (improper) permissions in there.

Just a thought. Let us know how it goes.
Regards.

---

### Post by astarmathsandphysics on 2014-11-30
Thanks for that. Actually I used ufw.
I diudn't know apf was a filewall.
I changed ownership to root.

This problem is solved

---

### Post by Bashing-om on 2014-11-30
astarmathsandphysics; Hi !

As I pass by:
You must be the one to mark this thread solved;
Doing so ->
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
See this tutorial:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]keep up your good work
[/INDENT][/INDENT]

---

