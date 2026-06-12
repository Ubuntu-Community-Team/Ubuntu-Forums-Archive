---
title: "Well, I was fooled (Win10/Ubuntu)"
date: 2016-08-02
forum: The Cafe
---

### Post by kurt18947 on 2016-08-02
I learned something today. I was looking for a Windows 10 Anniversary .iso to install in a VM and see which rumors were true. Searching for 'Windows 10 Anniversary downloads' I came upon this page:

[ATTACH=CONFIG]270535[/ATTACH]


And all this time I thought I was using this:

[ATTACH=CONFIG]270536[/ATTACH]

This is taken while using Firefox but with no user switcher agent in addons that I can spot. Does this rank me among the 350 million users of Windows 10? I thought I was among the 2% (or less) of Linux Desktop users? :confused:


:-P

---

### Post by yoshii on 2016-08-02
That is odd.  
i do know, however, that nowadays there are tons of other ways site get user info besides user-agent strings.  I have to use a lot of firefox addon's to try and block a lot of them for privacy reasons.  But I wouldn't trust the accuracy of microsoft snooping code anyhow :D

---

### Post by grahammechanical on 2016-08-03
I knew no good would come of Canonical working with Microsoft to get a Bash shell running on Windows 10. :)

The thought occurs to me, that if a person clicks "Update now" would Windows 10 be installed over Ubuntu? Or, would the upgrader have a nervous break down?

There is a kind of Microsoft logic to this. It is a computer. It has an OS. It is not Windows 10. And Windows is the only OS in the universe therefore it must be an older version of Windows. Upgrade it to Windows 10! Resistance is futile!

Regards.

---

### Post by kurt18947 on 2016-08-03
I will say that Windows 10 seems to run okay as a guest using QEMU/gnome-boxes. I'm not sure how to maintain Windows activation moving from one VM to another. Boxes doesn't have the options or configurability of Vbox but it is SUPER quick & simple. Clipboard is enabled by default which I disabled.

EDIT: Well, Win10 runs well in QEMU/gnome-boxes until I try to mount a USB drive. NTFS or FAT32 flash drives will mount on another linux distro running as a guest, it will not mount on Win10 anniversary edition guest. The same flash drives will mount on an older Windows 10 install on 'bare metal' no problem. I'm not distraught about the Win10 guest not mounting a flash drive, it's just intended as temporary.

---

