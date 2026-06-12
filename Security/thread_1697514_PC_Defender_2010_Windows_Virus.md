---
title: "PC Defender 2010 Windows Virus"
date: 2011-02-28
forum: Security
---

### Post by pi3.1415926535... on 2011-02-28
Someone I know, luckily not me, has a virus on windows. I believe the name of the virus is "PC Defender 2010". This has self-installed, causing popups attempting to convince the user that there is a security flaw, and that they should upgrade to the advanced version. I have looked this up, and it is definitely a virus. The virus creates a shortcut with a target in the AppData folder named defender.exe. When I went to search for this file, after having set it to show hidden files and folder, I looked in the folder, and found nothing by the name of defender.exe. Does anyone have any ideas as to how to find this file, if it even exists, and then remove the virus all together from the computer. Ideally these solutions will be executable from Windows, as the user is rather afraid of linux.

Thank you

---

### Post by cariboo on 2011-02-28
This is really a question for a windows malware forum, so it really doesn't belong here.

To repair the problem, do a search for combofix.exe, and download it. Start the computer in safe mode and copy combofix to somewhere on the hard drive, then run it as an administrator. It may take a while for anything to happen, so just let it run and go do something else. Once combofix has popped up the log of what it did on screen, reboot and the system should be clean.

With that, this thread is closed.

---

