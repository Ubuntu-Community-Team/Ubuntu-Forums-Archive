---
title: "Artful can corrupt some UEFI BIOSes"
date: 2017-12-22
forum: Ubuntu, Linux and OS Chat
---

### Post by DuckHook on 2017-12-22
This has happened to some users on this very forum: [https://www.theregister.co.uk/2017/12/21/ubuntu_lenovo_bios/](https://www.theregister.co.uk/2017/12/21/ubuntu_lenovo_bios/)

And Ubuntu's [download page]("https://www.ubuntu.com/download/desktop") currently has this:> The download of Ubuntu 17.10 is currently discouraged due to an issue on certain Lenovo laptops. Once fixed this download will be enabled again.

While I can't claim that LTS versions will never suffer from such issues, I think this just reinforces my conviction that general users should stick to LTS versions and not be on standard release versions. It is natural for Ubuntu to push the envelope on standard releases. That's what they're for. But this also necessarily means the inclusion of stuff that's not as well tested. Standard releases, simply by their nature, have more bugs and are less robust.

---

### Post by #&amp;thj^% on 2017-12-22
Good Information to bear in mind.
> may also fall foul: selected Acer, HP, Toshiba and Dell hardware are said to be hit, too.
[B]EDIT: Updated list of Affected Machines:
[/B]
```
Lenovo B40-70
Lenovo B50-70
Lenovo B50-80
Lenovo Flex-3
Lenovo Flex-10
Lenovo G40-30
Lenovo G50-30
Lenovo G50-70
Lenovo G50-80
Lenovo S20-30
Lenovo U31-70
Lenovo Y50-70
Lenovo Y70-70
Lenovo Yoga Thinkpad (20C0)
Lenovo Yoga 2 11" - 20332
Lenovo Z50-70
Lenovo Z51-70
Lenovo ideapad 100-15IBY

Acer Aspire E5-771G
Acer Aspire ES1-111M-C1LE (not fixed by 4.14.9 and 4.14.10)
Acer TravelMate B113
Acer Swift SF314-52 (Fixed by 4.14.9)
Toshiba Satellite S55T-B5233
Toshiba Satellite L50-B-1R7
Toshiba Satellite S50-B-13G
Dell Inspiron 15-3531 (not fixed by 4.14.9)
Mediacom Smartbook 14 Ultra M-SB14UC
Acer Aspire E3-111-C0UM
HP 14-r012la
```
Thanks DuckHook....;)

---

### Post by DuckHook on 2017-12-22
Here's the Launchpad bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147)

---

### Post by sudodus on 2017-12-23
Thanks for this warning, Duckhook.

---

### Post by Geoffrey_Arndt on 2017-12-26
Wonder if this is also a reported issue with the "mother ship" (Debian) . . . and distros based on Ubuntu . . . ??

---

### Post by jeremy31 on 2017-12-27
[https://bugzilla.kernel.org/show_bug.cgi?id=195951](https://bugzilla.kernel.org/show_bug.cgi?id=195951)
It affects more than Ubuntu.  It appears the bug started in 4.11 rc1 and was fixed in 4.14 rc1

After seeing the Lenovo forums thread, [https://forums.lenovo.com/t5/forums/v3_1/forumtopicpage/board-id/ll04_en/page/1/thread-id/154203](https://forums.lenovo.com/t5/forums/v3_1/forumtopicpage/board-id/ll04_en/page/1/thread-id/154203) it might just be a buggy BIOS update as a few posters there are having issues that don't even mention using Linux

---

### Post by sonicwind on 2017-12-27
Ubuntu 17.10's Laptop Issue Appears To Be Under Control, Fixable (Phoronix)

If it broke your system, this article says it can be fixed.

[https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-17.10-Laptop-Fix](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-17.10-Laptop-Fix)

---

### Post by #&amp;thj^% on 2017-12-27
I can confirm that the kernel upgrade to 4.14.9 worked on a "ThinkPad T470". (One (1) case test though)
Bios back and functional!
Wish i had seen that link earlier, It would have saved me some time last night. :)
See this for more: [https://ubuntuforums.org/showthread.php?t=2381317](https://ubuntuforums.org/showthread.php?t=2381317)

---

### Post by cupoflinuxun on 2017-12-29
[https://www.youtube.com/watch?v=UILuGiIud98](https://www.youtube.com/watch?v=UILuGiIud98)

[SIZE=1]Ubuntu 17.10 And Other Linux Distros Damaging Lenovo BIOS?[/SIZE]

---

