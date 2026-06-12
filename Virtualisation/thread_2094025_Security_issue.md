---
title: "Security issue?"
date: 2012-12-12
forum: Virtualisation
---

### Post by conradin on 2012-12-12
Hi all, 
I was just working on a windows 98 VirtualBox VDI, when I went off to take lunch. I cam back, and started working on it a half hour later.
I was having keyboard issues and some I/O problems. So I closed the VM and was thrown back to the login screen that I should have gotten when I returned from lunch. Instead of locking my screen, like I would have hoped, as a function of the screen-saver, the VM remained open and active, even when the host OS was in a "locked" Mode. 

Maybe stuff like that is common, I thought it was odd, and just wanted to make note of it here.

---

### Post by grahams on 2012-12-22
I've seen the same issue with other hypervisors and also with rdp sessions. To be secure, click back into your linux desktop and make sure your screen is locked.

---

### Post by Paddy Landau on 2012-12-23
Interesting. I haven't had that problem. What distro and version is your host OS, is it 32-bit or 64-bit, which version is your VirtualBox, and did you install the Oracle Guest Additions into your guest?

---

### Post by nishant1234 on 2012-12-24
linux is one of the secure plateforms of the world.. don't worry???

---

### Post by Paddy Landau on 2012-12-24
> **nishant1234 said:**
> linux is one of the secure plateforms of the world.. don't worry???
I think you missed the OP's point. He was away from his desk, and the screen-lock should have kicked in to prevent others in the area from getting onto his computer. This is a security issue.

Incidentally, you can press Ctrl+Alt+L to immediately lock your screen without waiting for the automated screen-lock.

---

### Post by grahams on 2013-01-02
> **Paddy Landau said:**
> I think you missed the OP's point. He was away from his desk, and the screen-lock should have kicked in to prevent others in the area from getting onto his computer. This is a security issue.

Incidentally, you can press Ctrl+Alt+L to immediately lock your screen without waiting for the automated screen-lock.

When your keyboard & mouse are captured by Virtualbox or RDP etc. a Ctrl+Alt+L will not lock your X screen as the Ctrl+Alt+L was sent to your VM (or RDP session) not your desktop. You need to click outside of the Virtualbox window then lock your screen.

---

### Post by conradin on 2013-01-03
> **Paddy Landau said:**
> Interesting. I haven't had that problem. What distro and version is your host OS, is it 32-bit or 64-bit, which version is your VirtualBox, and did you install the Oracle Guest Additions into your guest?

No guest addons available for windows 98 guest, the host is Ubuntu 10.04, kernel 2.6.32.45-generic.

anyhow, I was disturbed because I was locked out, and not locked out. I would figure that host OS lock out would trump guest OS any behaviour, but that wasnt the case. Maybe i should pass a note on to oracle.

---

