---
title: "Ubuntu 13.04 HOST, Win-whatever GUEST, VMWare TOOLS install fails"
date: 2013-09-09
forum: Virtualisation
---

### Post by r_avital on 2013-09-09
This is to assist anyone who's had this problem with VMWare-Player (I suppose it should address the same problem with other VMWare tools):

HOST: Ubuntu 13.04
GUEST: Windows-7, Win-XP, or any Windows-2K and above
Installation of VMWare Tools in the guest OS fails with an error (unable/try later/contact VMWare/Your Administrator).

I found this on a Linux-Mint site that I can't find again, so I'm posting the procedure here.

Download tools-windows-9.2.3.exe.tar from this location (as of this writing, this is the latest version):
[http://softwareupdate.vmware.com/cds/vmw-desktop/player/5.0.2/1031769/windows/packages/](http://softwareupdate.vmware.com/cds/vmw-desktop/player/5.0.2/1031769/windows/packages/)

1. Extract the archive to any folder accessible by your Windows guest OS and run the executable (obviously, if you have a spare Windows box, and can extract the archive there, run it there).  Running the extracted EXE will create an ISO file and an XML file.

2. Copy BOTH the ISO and XML to any location you like on your HOST OS (in your ~ folder is fine).
3. Run vmplayer, edit the settings for your Windows Guest OS: Add a CD/DVD and point it to the ISO file.
4. Start your Windows Guest OS (or re-start it if  you had it running).
5. In Explorer, go to your new CD/DVD (It should be named the same as your ISO file), and run either setup.exe or setup64.exe, depending on the architecture of your Windows Guest OS.

When done, you will be prompted to restart.  After you do, check the version of your VMWare tools, it should be 9.2.3

After you shut down your Windows Guest OS, you can safely delete that additional CD/DVD drive from its settings.

I've tested this with Win2K-Pro, Win-XP-Pro 32Bit, and Win-7-Ultimate 64Bit.  All work fine.

However, you will continue to be prompted to upgrade your VMWare tools every time you play the Windows Guest OS.

I know there is a post here on a script that fixes the problem for VMWare-Tools 9.2.2, without having to go through the above, but it refers to Ubuntu GUEST systems.  

It isn't clear whether the underlying problem is with VMWare or Ubuntu Raring (given the latter's instabilities, I suspect Raring).

HTH

---

