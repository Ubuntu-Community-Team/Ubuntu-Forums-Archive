---
title: "Manual Samba Update"
date: 2009-11-07
forum: Server Platforms
---

### Post by SiarAneas on 2009-11-07
Hi!
I hope this is the right forum to ask this question -if not please excuse this!
It's just because I think that ubuntu users are more capable of really helping me...

I'm running Ubuntu 9.04 on my little "home-server".

On one of the clients I just installed Windows 7 Professional.
When I tried to enable offline files to one of the samba shares on my server I received thousands of "access denied - file is currently in use by another process" error (Just on the Win 7 machine, Vista was fine).
After some google research I found out that I had to get the latest samba version (3.4.X) as this would fix some Win 7 issues.
smbd -V returned: Version 3.3.2

OK so **question #1** is: Why can't I update samba via the Synaptic Package Manager (I really enjoy this tool as it makes things so much easier) -it seems it doesn't offer any update, though there obviously is a new version available.

Anyway, I manged to download the new version as .tar.gz file from the samba website (3.4.3). I unpacked it to my desktop and did as it said in the installation manual:
sudo ./configure
sudo make
sudo make install

Everything seemed to have worked smoothly (at least there haven't been any obvious errors).

Now my **question #2 **is: Did it actually update?? Cause when I run
_smbd -V it still returns: Version 3.3.2_
BUT
the updating process has obviously done something, as there are new files
in /usr/local/samba/sbin
because _when I run /usr/local/samba/sbin/smbd -V it returns: Version 3.4.2!!!_

This is so frustrating! Any help would be greatly appreciated! Did it actually update or not? The samba shares are available but I don't know whether it runs the new version.

Thanks to anyone who can explain this behaviour to me!

SiarANeas

---

