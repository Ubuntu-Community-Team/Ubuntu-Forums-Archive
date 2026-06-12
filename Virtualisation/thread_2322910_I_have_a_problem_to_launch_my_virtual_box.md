---
title: "I have a problem to launch my virtual box"
date: 2016-05-01
forum: Virtualisation
---

### Post by Thunder-Jellyfish on 2016-05-01
Hello, I'm on Ubuntu 15.10. I use virtual box to launch a windows 10.

But since an update, the virtual box cannot launch the windows 10 and I have this message:

 The device helper structure version has changed.
 If you have upgraded VirtualBox recently, please make sure you have terminated all VMs and upgraded any extension packs. If this error persists, try re-installing VirtualBox. (VERR_PDM_DEVHLPR3_VERSION_MISMATCH).
 

 [TABLE]
[TR]
[TD] Code d'erreur : [/TD]
[TD] NS_ERROR_FAILURE (0x80004005)[/TD]
[/TR]
[TR]
[TD] Composant : [/TD]
[TD] ConsoleWrap[/TD]
[/TR]
[TR]
[TD] Interface : [/TD]
[TD] IConsole {872da645-4a9b-1727-bee2-5585105b9eed}[/TD]
[/TR]
[/TABLE]


Help would be appreciated :)

PS: I might have wrote mistakes since english isn't my native language, also sorry for the dyslexia problem in the title

---

### Post by jim_deadlock on 2016-05-01
> **Thunder-Jellyfish said:**
> If you have upgraded VirtualBox recently, please make sure you have terminated all VMs and upgraded any extension packs. If this error persists, try re-installing VirtualBox.

Did you do that?

---

### Post by DuckHook on 2016-05-01
*Your thread has been moved to **Virtualisation** as the forum more suited to your issue.*

---

### Post by Ze Ha on 2016-05-01
What are you talking about when you say "since an update"? What did you update? Win10 guest or the Virtualbox? If the Virtualbox, then after upgrading Virtualbox, have you upgraded the Extension pack too?

---

### Post by Thunder-Jellyfish on 2016-05-02
I updated ubuntu, and I don't know how to upgrade the extension pack (I'm an ubuntu newbie)

---

### Post by Ze Ha on 2016-05-02
You can download the Extension Pack from virtualbox.org, but watch out that you download the correct version.
To install the downloaded pack, start VirtualBox GUI as root, then select File, Preferences, Extensions, remove the installed Extension Pack, and install the new one!

---

### Post by DuckHook on 2016-05-02
* It is not necessary to start VB as root.* Don't do that! VB must never be run as root. There be dragons. When extension pack installs, it will ask you for your password one time. Provide it for that one time only and extension pack will install.

Remember: never, ever run VB as root. Ever.

---

### Post by DuckHook on 2016-05-02
> **Thunder-Jellyfish said:**
> I updated ubuntu, and I don't know how to upgrade the extension pack (I'm an ubuntu newbie)[This wiki page]("https://help.ubuntu.com/community/VirtualBox/Installation") should help. It is short, but the key is to follow the links to other resources that will explain things in much greater detail.

---

### Post by Ze Ha on 2016-05-04
I'm sorry... you could be right. I've used linux as host of Virtualbox a very long time ago. On Windows host Virtualbox requires administrator privileges to install the Extension Pack and installation can fail sometimes if I try to do it as a non-privileged user.
And I agree: never use VB as root, it is the default.

---

### Post by MAFoElffen on 2016-05-04
The extension pack is a vbox file type, so opens from inside of virtualbox and installs. No elevated permissions needed. Yes the extension pack needs to be the same version as Virtualbox.

The reason they are separated is a licensing issue between opensource code and their still free, but proprietary code.

---

