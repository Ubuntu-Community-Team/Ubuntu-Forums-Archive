---
title: "Virtualbox Freezes in kernels above 5.4"
date: 2022-04-21
forum: Virtualisation
---

### Post by germanloco on 2022-04-21
Hello, I would like to ask for help about a problem I have with Virtualbox.

On my Dell 3520 notebook with wd19s dock and Ubuntu 20.04 LTS (kernel 5.4) virtualbox works correctly running a Windows 7 32bit virtual machine.

But when you update the kernel above 5.4, every time I try to run a virtual machine (Windows 7 32bits) virtualbox, it crashes and you have to force it off.

Install Ubuntu 22.04 LTS and the problem persists, what can it be? 

Greetings and thank you very much

---

### Post by &amp;KyT$0P# on 2022-04-22
What version of VirtualBox and from where did you install it?

Do you have Extension Pack installed?  Does your Windows 7 guest have VirtualBox Guest Additions installed?  If yes and yes, do the versions both match your VirtualBox version exactly?

---

### Post by germanloco on 2022-04-22
[SIZE=2]Hi! Thanks for answer!

The Virtualbox version are [COLOR=#000000] 6.1.32_Ubuntu r149290, yes the windows have de Guest Additions, the version match.-

[/COLOR][/SIZE]On a clean install of 22.04, with a fresh install of Virtualbox, when I try to install windows 7, I get the same error...virtualbox crashes.-



[COLOR=#202124]*[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABQAAAAUCAQAAAAngNWGAAAA/0lEQVR4AYXNMSiEcRyA4cfmGHQbCZIipkuxnJgMStlMNmeyD2dwmc8 sZgxYJd9ErIZFHUyYYD7fkr6l4/rnvmtl7 KitrqV/fq2Y5eLY3Z9S48eRLe7BmVZ9qhTLhQ0algzZWQOVKSsCF8OjAnwbxDTWFDUhPK/jMr1H6HE/IqRky2DyvCefuwItwZzodVoYRiLqMkVCXrwpJ9twZ sgfDYEFYl8wIWxZ9uFf7zkallxlJh4YrLGsKjZRx7VGHhLqwgFUN45DGdb8MeXGpgB4ABZdeDcpZEY51A hyLKz4S1W4MQWm3AibWtgWmk6dyISa1pSdyWTOlLXVp0 eL9D/ZPfBTNanAAAAAElFTkSuQmCC[/IMG]*[/COLOR]


[COLOR=#70757A][FONT=arial]
[/FONT][/COLOR][COLOR=#70757A][FONT=arial]
[/FONT][/COLOR]

---

### Post by &amp;KyT$0P# on 2022-04-22
Have you tried the Oracle build of VirtualBox downloaded from the [official site]("https://www.virtualbox.org/wiki/Downloads")?

Is there anything related to this crash either in [FONT=Courier New]/var/log/syslog[/FONT] around the time it happens, and/or in VirtualBox's VM logs (which can be viewed following instructions [here]("https://www.virtualbox.org/manual/ch12.html#collect-debug-info"))?

---

### Post by germanloco on 2022-04-22
I was able to solve the problem. I made a new 64-bit virtual machine and it works. Thanks

---

