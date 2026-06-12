---
title: "DVD Mounting as Read-only ... Non-executable"
date: 2010-12-27
forum: Wine
---

### Post by jacrider on 2010-12-27
Hello All:  I have done a bunch of searching to no avail.

I received a magazine archive as a gift.  It is a series of pdf's and a Windows application to search them.  

I have seen in the Wine AppDB that it works perfectly under wine.  Great.  

I insert the disk and can't get the installer to run as it is flagged as not executable.  So typically, I either use the terminal to chmod the file or I use 'sudo nautilus' to make these files executable.  No go this time as the DVD has been mounted as read-only.  

What do I need to do?

I am on Ubuntu 10.10 (x86) with a standard install.

I feel silly, as I thought I knew enough to fix this.

Many thanks.

---

### Post by JBAlaska on 2010-12-27
Well, your DVD is going to be read only, unless you put blank media in it. Try copying the content to your HD and setting the executable bit there.

Also if it's just PDF files you need to view, you can do that with native Linux apps.

---

### Post by jacrider on 2010-12-27
Thanks.  I was going to do that, but I thought I could change permissions somehow.  

Anyway, thanks for the response.  

I know there are many applications available for handling pdf's, but this application seemed to have a decent search utility.  I guess I could just use Google Desktop to do this as well in Ubuntu.

Thanks.

---

### Post by JBAlaska on 2010-12-27
If the utility gets a good rating on WineHQ, copy the installer to your HD, set it as executable, and give it a try!

---

### Post by disabledaccount on 2010-12-27
I had similar problem, and solution is simple: (for me it works) mount DVD manually from terminal, and run installer using: wine /path_to/install.exe. In some cases it can be neccessary to assign DVD-drive letter in winecfg, so it will point to location where you have mounted your DVD.
I suppose this can be due to problems between gvfs and wine. Besides, nautilus seems to look at file permissions for .exe while it should only launch wine with installer file as argument.

---

