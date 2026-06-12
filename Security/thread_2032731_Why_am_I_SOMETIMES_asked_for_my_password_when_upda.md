---
title: "Why am I SOMETIMES asked for my password when updating?"
date: 2012-07-24
forum: Security
---

### Post by nrundy on 2012-07-24
Since I think Oneiric the software update security policy has changed. I no longer have to ALWAYS enter my password when the Updater has updates.

But sometimes I am still asked for my password. In an effort to understand why I am asked for my password sometimes and not other times, can anyone educate me?

I have 2 repositories active: Main & Universe. I have two update channels active: Security & Recommended Updates. I have no 3rd party stuff installed on my box. Everything is from Main & Universe.

So today I had updates that needed installing. And I was asked for my password. Yet the last updates that needed installing did not ask for my password. Why is this not consistent? 

I want to understand what causes Ubuntu to ask for my password when updating software.

Thanks.

---

### Post by Jimmyfj on 2012-07-24
I'm **not** at all sure but I think it has to do with the way Linux works in general. Technically you have two layers in the OS: Kernel-space and User-space. I can see some logic in the way the updates are performed since I have the same experience on my own 12.04-system. I think that when ever the updates are anchored in Kernel-space you need root-permission to perform any operation on the files on that level, but you do not need those permissions in User-land-software.

As I said, I'm NOT AT ALL sure that this is the answer, but from my experience it makes some kind of sense. Since I first experienced this difference in updates I have kept an eye on what files are in the update. Every time I've seen files belonging to Kernel-space I've been prompted for the root-password. But I can be wrong.

---

### Post by qamelian on 2012-07-24
When an update is only updating existing packages, you won't be prompted for your password. When new packages are required, such as when there is a change in dependencies for an installed package or when a new kernel version is added, then you need to provide your password.

---

### Post by nrundy on 2012-07-24
Yeah, that does seem like it makes some sense.

I like to understand when my password will be asked for for security reasons. Because the software updates sometimes ask for password and sometimes dont, I feel like this actually hurts security.

I almost feel like I should file a bug report about it. User's should be able to tell/understand what prompts a password or any security the security password prompt provides is useless. If some malware prompts for the password and user robotically inputs it, you're done.

---

### Post by cariboo on 2012-07-24
> **nrundy said:**
> Yeah, that does seem like it makes some sense.

I like to understand when my password will be asked for for security reasons. Because the software updates sometimes ask for password and sometimes dont, I feel like this actually hurts security.

I almost feel like I should file a bug report about it. User's should be able to tell/understand what prompts a password or any security the security password prompt provides is useless. If some malware prompts for the password and user robotically inputs it, you're done.

This was a change made in 12.04. This change was made in the name of ease-of-use. I personally use synaptic for installation of packages, and updates, and I'm always asked for a password, when I start the program.

---

### Post by nrundy on 2012-07-25
> **cariboo907 said:**
> This was a change made in 12.04. This change was made in the name of ease-of-use. I personally use synaptic for installation of packages, and updates, and I'm always asked for a password, when I start the program.

how do you use synaptic for updates? Do you disable the Software Updater program? Could you describe how to use synaptic to update?

---

### Post by cariboo on 2012-07-25
I personally find update manager annoying, so I set it to never check for updates.

I'm running Quantal, so I normally update a couple of times a day. The first time I run synaptic after installation, I click the status button, which gives me what is displayed in the screenshot. I then click the reload button, if there are updates available, the will be a heading called updates in the left-hand pane.

I just updated my system, so it isn't showing any available updates.

---

### Post by CharlesA on 2012-07-25
> **nrundy said:**
> how do you use synaptic for updates? Do you disable the Software Updater program? Could you describe how to use synaptic to update?
Just install synaptic and use that instead.

I use apt-get even on my desktop boxes..

---

### Post by nrundy on 2012-07-25
> **cariboo907 said:**
> I then click the reload button, if there are updates available, the will be a heading called updates in the left-hand pane.


Do you mean the left-hand pane will say "Installed (upgradable)"? 

Does using Synaptic to update necessarily mean that user must manually update? Or is there a way to have Synaptic check in the background once a day and report if updates are available--just so you know you need to perform an update?

---

### Post by cariboo on 2012-07-25
Synaptic does check for updates automagically, but because I use a development release, I have it manually check for updates a couple of times a day. I personally want to check change logs before committing to any updates.

---

### Post by nrundy on 2012-07-25
but can synaptic check for updates without being started first? like how update manager just appears when there's updates to inform you they are available for download & install?

---

### Post by cariboo on 2012-07-26
> **nrundy said:**
> but can synaptic check for updates without being started first? like how update manager just appears when there's updates to inform you they are available for download & install?

Yes it does, I just used it to update my much ignored 12.04 install, and found 312 updates waiting.

---

### Post by nrundy on 2012-07-26
> **cariboo907 said:**
> Yes it does, I just used it to update my much ignored 12.04 install, and found 312 updates waiting.

So how do you make it tell you updates are available? Does it just happen automatically when you disable update manager? Or is there a setting I need to switch?

How do you "check change logs"? Are these logs available from within Synaptic?

---

### Post by cariboo on 2012-07-27
Update manager and synaptic both use software-properties-gtk for their settings, even with update-manager disabled, the settings still work with synaptic.

To view a change log, just click on a package, and you'll see in the bottom right pane a button to click to view the change log.

---

### Post by nrundy on 2012-07-27
I'm still not clear  on this.

If I go into Update Manager and change Automatically Check for Updates to NEVER, will I continue to be alerted when new updates are available for download and install (it will just be Synaptic causing the alert)?

I'd like for Ubuntu to check for updates Daily and alert me when new ones are available for download. I would then open synaptic when I'm ready to deal with the updates, check the Change Log, and then install the new updates. So what steps should I take to set this up? This is how you do it right?

---

### Post by cariboo on 2012-07-27
> **nrundy said:**
> I'm still not clear  on this.

If I go into Update Manager and change Automatically Check for Updates to NEVER, will I continue to be alerted when new updates are available for download and install (it will just be Synaptic causing the alert)?

I'd like for Ubuntu to check for updates Daily and alert me when new ones are available for download. I would then open synaptic when I'm ready to deal with the updates, check the Change Log, and then install the new updates. So what steps should I take to set this up? This is how you do it right?

Synaptic won't notify you of new updates.

---

