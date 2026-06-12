---
title: "No internet with Ubuntu, but internet with Windows."
date: 2017-10-12
forum: Virtualisation
---

### Post by msmith40 on 2017-10-12
I installed Ubuntu17 onto my Win7 laptop – connected to a LAN cable.
Ubuntu is installed within VirtualBox.
After install, Windows connects to the internet.
Ubuntu does not.
Connection is DHCP.
This is my 3[SUP]rd[/SUP] time installing onto same laptop.

The network setting show I'm connected at 1000mbs.

I actually had it connected (LAN cable) yesterday and was installing updates for Wi-Fi.
So I know that it is possible to access the internet (wired) with this laptop/Ubuntu combo.
But after updates installed, Ubuntu merely opened to a black screen…………

So I uninstalled/re-installed.........and here we are.

Thanks!

---

### Post by wildmanne39 on 2017-10-12
*Thread moved to **Virtualisation for better support**.*

---

### Post by ajgreeny on 2017-10-12
Are you trying to use a bridged or NAT connection in your VM of Ubuntu?

Assuming that your Windows host is connected there is no reason why a NAT connection should not work as far as I'm aware, as that in effect uses the Windows connection.

---

### Post by msmith40 on 2017-10-12
> **ajgreeny said:**
> Are you trying to use a bridged or NAT connection in your VM of Ubuntu?

Assuming that your Windows host is connected there is no reason why a NAT connection should not work as far as I'm aware, as that in effect uses the Windows connection.

Much Thanks for your reply!
I'm pretty sure I've tried both.
(Heck, I probably tried all of them!)

And, like I'd mentioned, I *WAS* able to access the internet yesterday and was downloading updates.
I don't recall changing any specific settings though.

I was thinking of installing same (VBox & Ubuntu) onto my desktop.
If that works (and I have connectivity) I'll see what those settings are and mimic on my laptop.

It's been a frustrating 2 days......believe me.......

Mike

---

### Post by msmith40 on 2017-10-12
OK..................

Successfully installed VirtualBox onto my 64-bit Windows 8.1 desktop.
Tried to install Ubuntu.......no good.
I have to enable virtualization.
So I go into the BIOS and take care of that.

Now I have to make sure that Hyper-V is enabled.
But I don't have Hyper-V.
This is Windows 8.1.........not Pro.
So............that's that.

This is really a pain.

Mike

---

### Post by msmith40 on 2017-10-13
Found the answer!

[https://www.youtube.com/watch?v=2hEeYgE0pT0](https://www.youtube.com/watch?v=2hEeYgE0pT0)

Thank-You, Youtube!

Mike

*EDITED TO ADD*

As I didn't have Hyper-V on my desktop, I removed VirtualBox and used VMWare Player.
That allowed me to install Ubuntu, but it did not resolve the internet access problem.
The Youtube video resolved the internet problem.

Mike

---

### Post by ajgreeny on 2017-10-13
Brilliant!
I could not have helped with your Windows host as I no longer run Windows except as a guest in my Xubuntu host.

Please mark as Solved from the Thread Tools menu at the top of the Thread.

---

