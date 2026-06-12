---
title: "Maya Reinstall help needed"
date: 2008-11-23
forum: Ubuntu Studio
---

### Post by Neon612 on 2008-11-23
I was working away in my 3D program - Maya 2008 - when a 100% disk usage message popped up. I figured 'great. need to go make some space.' so I deleted some old, out of date files (of my creation, noting Ubuntu or Maya needed to function), shut down my computer for the night and when I try to get into Maya today to work on a project, the splash screen pops up telling me what is being processed. When it hits shelves I get an error message saying that some items cannot be found, do I want to Quit or Continue. No matter which button I click, the script editor pops up loading stuff like normal, but when it gets done nothing else happens. No Maya window. No nothing.

I look to see what processes are running and, sure enough, there is a maya, and a maya-bin in the process tree, but I still cannot do anything with the program.

So I figured I could try to reinstall the DEBs, didn't work. Just going through Nautilus to find the files and double-clicking on them will give me an error saying the files are corrupted or I don't have enough privilages. Going through the command line says there is an error in the update tag or something along those lines.

I even tried re-converting the RPM's to DEB's again. But all I get is a folder with what I assume is the contents of the DEB package inside of it. No DEB package.

What can I do to get Maya working again? Any and all help will be greatly appreciated. Thank you.

Edit:
I've tried Completely Removing, root deleting, and just plain dumb luck but with no avail.

And for clarification here is the error message I was talking about:
```
The shelf "PaintEffects" has an item that cannot be read.
The shelf will only display the items before the first unreadable item it finds.
If you start Maya and save this shelf then you will lose the unreadable items.
This will happen automatically if you have your preferences set to save the shelves on exit.
```

Will I need to try a different version? How can I get this to work?

---

### Post by Neon612 on 2008-11-25
BUMP
A little help will be greatly appreciated

---

### Post by Wisp2006 on 2008-11-26
First, make sure that when you convert them you do it with the -cv option. It will show you the complete log. Usually at the end there is a command which moves all unpacked folders into the .deb package. The command itself takes some time to complete. See if there is a problem before that command.
Second, what kind of Maya is it? 8, 8.5? I just installed yesterday Maya 8.5 with absolutely no issues. I'm no expert in Maya, I worked primarily with 3ds Max; there was a possibility that a certain texture library, for example, to be loaded by default. If it was removed, things were not too nice. Is it possible that you created something that Maya used, and now, being deleted, it can't continue without it? If so, try remove with purge option, maybe some config files were left, even if Maya was removed.

---

### Post by Neon612 on 2008-11-26
It is Maya 2008. I had installed this about 6 months ago, working with it on and off since then. When, all of a sudden, sometime earlier this week or last week I got this error. So I was wondering if I needed to reinstall Maya, which I have tried multiple ways with no success.

I also was getting an error when I first tried to reinstall the deb files that one or more of them were corrupted, hence the questions about converting RPMs to DEBs. But during my multiple reinstallation tries I've found out that the ones I have will work, meaning no corruption error given anymore.

The purge idea I hadn't thought about, I may try that and let you know how things work out. Thank you.

EDIT:
I tried the purge idea. It worked so far as removing the packages cleanly (I think). But after I reinstall the packages and enter the "maya" start command, it returns "bash: maya: command not found." How can this be? I've installed Maya just like I have been, so why now all of a sudden, will my computer not recognize Maya?

---

### Post by binbash on 2008-11-27
If you are using ATI card with latest drivers, at ati's changelog, they are talking about  that some models may not work with latest drivers with maya 2008.I dont know if it is related with this issue but you should check it

---

### Post by Wisp2006 on 2008-11-28
Well, this is good news! If purge worked fine, but when you install them it does not find the maya exec, it is good. I got this error when i converted incorrectly the .rpm's the first time. So...
Make sure again that you have the latest version of alien and csh.
Go in the folder where all Maya .rpm's are install and convert them with the command
```
sudo alien -cv all-tree-maya.rpm
```
The -c option is mandatory since it also includes the scripts, and i believe that your deb packages were build without this option and this would be the reason not to find the binary.
After the packages are done, install them in this order:
awcommon-server
awcommon
maya
maya-doc(optional)
At this stage Maya should try to start, but it will ask for a licence file. A quick sign of successful install is the presence of the Maya2008 icon in the Applications->Graphics menu. It should be there by default.
I hope to hear good news. :KS

L.E. Before doing this remove everything related to maya with purge option! "By everything" means awcommon also. Also, I have the atest drivers but i didn't find any issues with Maya. Anyway, upgrade you drivers if you have Ati. Older drivers had a tendency to f**k-up the font paths.

---

