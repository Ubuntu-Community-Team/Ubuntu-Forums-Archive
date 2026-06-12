---
title: "I can't install VirtualBox guest extensions on 22.04"
date: 2022-08-28
forum: Virtualisation
---

### Post by Paddy Landau on 2022-08-28
EDIT: I meant Guest Extensions, not Guest Additions.

On Ubuntu 20.04, I had no problem keeping my VirtualBox up to date using the instructions from the [VirtualBox website]("https://www.virtualbox.org/wiki/Linux_Downloads").

However, on Ubuntu 22.04, these instructions don't work properly. VirtualBox 6.1.36 installs fine, but not the Guest Additions. When I go to my virtual machine, VirtualBox complains that Guest Additions isn't installed.

I have no idea how to solve this. I've been at this for over an hour already, installing, uninstalling, reinstalling&#8230;

How do I correctly install the latest VirtualBox on Ubuntu 22.04, please?

---

### Post by &amp;KyT$0P# on 2022-08-28
How does it complain?  I've never seen such complaint.

Could you please be more specific what happens when you run the Guest Additions installer?  Maybe post the terminal output?

---

### Post by Paddy Landau on 2022-08-29
> **halogen2 said:**
> I've never seen such complaint.
It's a first for me, too.
> **halogen2 said:**
> Could you please be more specific what happens when you run the Guest Additions installer?
The guest machine already has Guest Additions installed; it has been moved to a new host. It's the host that's complaining.

When I open the settings for the guest, it warns of invalid settings detected because there's no extension pack; when I try to run the guest anyway, it gives the same error. See the two attached screenshots.
> **nodperson said:**
> [FONT=Verdana]I have the same issue too…[/FONT]
Yours is a different error. Please start a new thread.

---

### Post by Paddy Landau on 2022-08-29
I found the solution!

I have just realised that I need to download the latest VirtualBox Extensions Pack separately from VirtualBox itself. The version is 6.1.36, but the version in the Ubuntu repository is 6.1.34, which doesn't help.

However, on the VirtualBox website, there's a link to download the extensions pack. I downloaded it, opened it, which caused VirtualBox to prompt me to add it, and boom, it's done!

Thank you for your time. I'll mark this thread as solved.

I don't know why Oracle doesn't just include the extensions as part of the VirtualBox package!

---

### Post by ajgreeny on 2022-08-29
That's because the Extensions pack is not open source whilst the VBox application itself has been for a few years now.

---

### Post by Paddy Landau on 2022-08-29
> **ajgreeny said:**
> That's because the Extensions pack is not open source whilst the VBox application itself has been for a few years now.
Ah.

It's a bit strange, though. Once the extension pack is installed, each time VirtualBox is updated, it automatically also updates the extension pack — albeit with a ridiculous seven prompts for confirmation, including reaffirming that you accept the license agreement.

I wonder why it doesn't just allow you to install it directly from VirtualBox, presumably with the same seven prompts?

---

### Post by &amp;KyT$0P# on 2022-08-29
Wait, what happened here?? :confused: The thread title and initial post describe a problem with Guest Additions.  But the rest of the thread, including the solution post, is about an Extension Pack related issue (one which I *have* previously seen on my system) and seems to have nothing whatsoever to do with Guest Additions???

---

### Post by Paddy Landau on 2022-08-29
> **halogen2 said:**
> Wait, what happened here?? :confused: The thread title and initial post describe a problem with Guest Additions.  But the rest of the thread, including the solution post, is about an Extension Pack related issue (one which I *have* previously seen on my system) and seems to have nothing whatsoever to do with Guest Additions???
I did not realise the difference in terminology until I came across something, I forget what.

So, please accept my apologies. I'll amend the title now.

---

