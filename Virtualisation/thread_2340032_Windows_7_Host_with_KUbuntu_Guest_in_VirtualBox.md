---
title: "Windows 7 Host with KUbuntu Guest in VirtualBox"
date: 2016-10-15
forum: Virtualisation
---

### Post by Mark_McDonald on 2016-10-15
I am new to this, and I am on the steep learning curve, but I have been trying my best to share a file.
But maybe I am missing something.

First - I tried to copy and paste something from LibreOffice Writer, thinking I could somehow paste it into MS Word, or Notepad. No Go.

I could screen shot, from Windows 7 and VM window open, that worked like a charm.

But I think I need to share a folder, then install LibreOffice on my MS W7.

On my Windows 7 desktop I created a file called sharedfile.
With KUbuntu VM turned off, I went into its settings, by right clicking the VM in VB and selecting Settings.
Clicked on Shared Folder, Add new shared folder, then selected the desktop folder in W7.
But I can not find it on the KUbuntu VM.
I've been searching the web, and found a few links in the forums here.
But I get to a certain point and I am clueless.

I cant find my file anywhere.

I have tried 
gksudo nautilusand find sharedfile
it states no such file or directory

---

### Post by howefield on 2016-10-15
Thread moved to the "*Virtualisation*" forum.

Have you added your user to the vboxsf group ?

---

### Post by ajgreeny on 2016-10-15
Do you have the "Guest extension pack" appropriate for your VBox version installed in your guest OS?
If not go to [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads) and see the info and downloads there, double click on the download and it will be installed in the VBox-manager.  Then in your guest go to Devices menu ->"Insert Guest Additions CD Image".

That will add a VBOXADDITIONS folder to your guest system, in media/username in I remember correctly, and in that folder will be a VboxLinuxAdditions.run file which you need to run as root to install the guest additions into your guest.

Have you also made the appropriate changes in the settings for the guest to allow bidirectional clipboard, and to setup whatever shared folders you want to make available?

Both those settings require that you are a member of the vboxsf group in the Ubuntu guest OS, as mentioned by howefield above.

---

### Post by Mark_McDonald on 2016-10-15
I did not realize there was a virtualization topic. Thanks for moving my post.

I added Guest Extension pack.
"Have you added your user to the vboxsf group ?"

Yes I did that, the last thing I did before it worked, but it works now.
It took me a few hours, to search the web and follow the process. Its a different game this Linux, a learning curve no doubt, I kind of dig it in a way, when I am in the moment I dont get too pissed off, but I do get a little ticked.
I will start up a new VM and do the process over again, because before I added a few command lines to the Konsole, having no idea what they were intended to do. But I kinda of knew the last step in a vague way. Which was to add permissions to the file.
I wont even bother trying to move the file out of the media file.

Thanks!

---

