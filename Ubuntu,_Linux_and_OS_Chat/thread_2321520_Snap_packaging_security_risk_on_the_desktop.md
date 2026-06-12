---
title: "Snap packaging security risk on the desktop?"
date: 2016-04-22
forum: Ubuntu, Linux and OS Chat
---

### Post by kansasnoob on 2016-04-22
According to Matthew Garrett, a well-known Linux kernel developer and security developer at CoreOS;

> Any Snap package you install is completely capable of copying all your private data to wherever it wants with very little difficulty.

To prove his point, he built a proof-of-concept attack package in Snap, which first shows an "adorable" teddy bear and then logs keystrokes from Firefox and could be used to steal private SSH keys. The PoC actually injects a harmless command, but could be tweaked to include a cURL session to steal SSH keys.

Garrett says **[COLOR="#FF0000"]the key reason Snap offers little security on Ubuntu desktop is that it uses the X11 window system[/COLOR]**.

[http://www.zdnet.com/article/linux-expert-matthew-garrett-ubuntu-16-04s-new-snap-format-is-a-security-risk/](http://www.zdnet.com/article/linux-expert-matthew-garrett-ubuntu-16-04s-new-snap-format-is-a-security-risk/)

[https://mjg59.dreamwidth.org/42320.html](https://mjg59.dreamwidth.org/42320.html)

So maybe it's best to wait for Mir and/or Wayland before getting all ***snappy*** :-k

---

### Post by sammiev on 2016-04-22
Hi,

Great read and Thanks.

---

### Post by QDR06VV9 on 2016-04-22
+1 Yes very sobering,  thanks kansasnoob

---

### Post by montag dp on 2016-04-22
From the article, it sounded to me like snap packages are not any less secure than regular debs, but they're not any more secure either. The insecure piece is X11, which is, of course, present in either case. Am I missing something?

---

### Post by kansasnoob on 2016-04-22
Another site weighs in:

[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Snap-Insecure-With-X11](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Snap-Insecure-With-X11)

This is getting enough attention that I'd almost bet Canonical will be issuing some public response sooner rather than later :)

---

### Post by kansasnoob on 2016-04-22
> **montag dp said:**
> From the article, it sounded to me like snap packages are not any less secure than regular debs, but they're not any more secure either. The insecure piece is X11, which is, of course, present in either case. Am I missing something?

Do Snap uploads have to pass the same level of security protocols that .debs uploaded to the official Debian/Ubuntu repos have to pass? I seriously don't know.

I'm always a bit skeptical of criticism, which is why I included a ? in my title.

---

### Post by grahammechanical on 2016-04-23
Snap packaging is not meant to fix the security vulnerabilities in the X sever. That is what Wayland compositors & the Mir compositors are supposed to do. And they do that be replacing the X server. It remains to be seen if there are any natural security vulnerabilities in the Wayland protocol and the protocol that is used in the design of Mir that the designers of the protocols have missed. There could also be security vulnerabilities from a flawed implementation of the protocol when crafting a compositor.

I do not think that snap packaging was meant to fix security vulnerabilities in Debian packaging either. If there are any. As always, a certain security comes from only installing applications from trusted sources. Install applications from the snap store (like installing from the click store) will bring a certain level of security protection. It is built into the requirements for getting an app accepted into the app store. 

The claim is made:

> The security mechanisms in snap packages allow us to open up the platform  for much faster iteration across all of our flavours **as snap  applications are isolated from the rest of the system**.


Unless of course you install a snap packaged application that has been crafted to access the rest of the system. But I do not think that you would get such an application from the snap store. This attack vector is also there in deb & rpm packages. Is that not true? Install from untrusted sources and who knows what you are getting. Is that not true?

On the Ubuntu phone click applications access the rest of the system by first communicating with the content hub which will either allow access, deny access or invite the user to grant access. Traditional Ubuntu with Unity 7 does not have such a thing as the content hub.

On snappy Ubuntu core everything is a snap. The kernel, the OS, the UI, the applications. A version of Ubuntu built on snappy core + Mir + Unity 8 + snaps will be more secure than any other traditional distribution. To allow the running of debs or X apps on this (future) version of Ubuntu we would have to install a snap called libertine that will install the deb app and run it in a Linux container. Now that is what I call a secure system!

Regards.

---

### Post by Geoffrey_Arndt on 2016-04-23
Graham . . . wonder what general time frame is envisioned by Canonical to implement Mir + Unity8 . . . tied to next LTS or Yakety Yak or Zany Zebra ?? . . . (or whatever the Z moniker will be).

---

### Post by QDR06VV9 on 2016-04-23
It's difficult to give precise dates, and they are changing all the  time. As it stands right now, two different versions of Ubuntu 16.04 LTS  will be provided, one with Unity 7 and one with Unity 8. The plan is to  have Unity 8 by default in Ubuntu 16.10, but plans tend to change.
That's about all we know ATM.
Regards

---

### Post by cariboo on 2016-04-23
[UOS]("http://uds.ubuntu.com/") is May 5 - 7, that should give us more of an idea of what is coming in Yakkety.

---

