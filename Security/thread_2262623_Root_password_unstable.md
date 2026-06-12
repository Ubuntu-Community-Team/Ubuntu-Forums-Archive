---
title: "Root password unstable ?"
date: 2015-01-26
forum: Security
---

### Post by Dimitri_Bosiers on 2015-01-26
Hi to all,

This morning I had to reset my root password because 'su' wasn't working anymore.
Wish is pretty strange because technically I had no or crippled network.
There were some issues with wifi, I had an ip,netmask etc. but could not ping my router.
Thanks to the great support here the network-problem is fixed.

But now I'm a bit worried about the security, is there any way the root password can change without being hacked ?
Is there some kind of instability at work ?

---

### Post by ian-weisser on 2015-01-26
> **Dimitri_Bosiers said:**
> This morning I had to reset my root password because 'su' wasn't working anymore.
Wish is pretty strange because technically I had no or crippled network.

See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

> **By default, the Root account password is locked in Ubuntu.** This means that you cannot login as Root directly or use the su command to become the Root user.

The 'su' command is not the recommended way to reach a root prompt in Ubuntu.
Your root password, if any, has nothing to do with your networking.

---

### Post by Dimitri_Bosiers on 2015-01-27
I know my root password has nothing to do with networking :roll: but possible security breaches do. Furthermore i've been using 'su' for at least 5 days before the problem happened, so 'su' does work. As does 'sudo' but I like the former one because there is no timeout and it involves less typing.

---

### Post by Dimitri_Bosiers on 2015-01-27
anyway, I was'nt realy awake when it happended, it's still possible that I typed my password wrong for about 20 times, but I it happens again then I would like to know the possible causes. I'm thinking about running snort in the background and changing all my passwords. I don't like visitors that get in without knocking, althoug the system doesn't contain anything at this time.

---

### Post by ian-weisser on 2015-01-27
When you login, you password is hashed and compared to the hash in  /etc/shadow. If that hash has been changed or edited, then your password  will be rejected.
I have discovered no upstream bug report with a symptom of that hash occasionally and unexpectedly changing.
That would be a rather serious bug.

Possible causes for a change to that file include the mundane (user experiment), the annoying (disk corruption or failure), and the dangerous (you got hacked)...and everything in between.

There are easy ways to safely get to a root prompt without enabling the root account.

---

### Post by mastablasta on 2015-01-29
I think you can reduce or remove the timeout on sudo.

the "not recommended" features are not recommended usually precisely because they normally work but sometimes they cause a strange behavious. same as for example opening GUI programs with sudo. usually it works but just occasionally it can make a big mess in the OS which is why graphical sudo is the preferred method to do that.

---

