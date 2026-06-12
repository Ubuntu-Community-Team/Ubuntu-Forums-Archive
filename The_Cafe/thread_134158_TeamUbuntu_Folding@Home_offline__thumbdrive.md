---
title: "TeamUbuntu Folding@Home offline / thumbdrive"
date: 2006-02-21
forum: The Cafe
---

### Post by KermitJr on 2006-02-21
Hi all,

I was wondering how to run FAH while on a different computer that may or may not have internet access, and I saw these directions over on the maximumpc forums (via google).

This is for the windows client, but I was hoping someone could help me get it working on linux as a removable type program.

Initial Setup
1. Make a FAH folder on the thumbdrive.
2. Put the FAH502-Console.exe file into the folder.
3. Launch the console on a computer connected to the internet. Do the normal config but don't launch as a service.
4. Wait until it downloads a work unit and starts working, then press Ctrl+C to close the console.
5. Depending on if you want to leave the thumbdrive in the P4
A. just launch the console from the thumbdrive, or
B. make a directory on the harddrive and copy the FAH folder to it and launch the console from the harddrive.

Maintenance

6. When the workunit finishes, if you chose:
A. Close the console, take the thumbdrive to your connected computer, launch the console, let it upload and download a new workunit, close the console, take the thumbdrive and launch the console on the P4
B. Close the console, delete the whole work folder and queue from the thumbdrive, copy the whole work folder and queue file to the FAH directory on the thumbdrive, take the thumbdrive to your connected computer, launch the console, let it upload and download a new workunit, close the console, take the thumbdrive to the P4, delete the work folder and queue from the hard drive, copy the work folder and queue from the thumbdrive to the hard drive, launch the console

---

### Post by jpkotta on 2006-10-15
I have done this.  My particular situation was a Windows client that was firewalled, so that I could download WUs but not upload.  So I copied the entire FAH directory after a WU had completed on to a key drive and moved it over to my Linux machine.  Then I copied the FAH dir to a directory visible to Wine and did 
```
cd /path/to/fah/dir
wine FAH502-Console.exe -send all
```

Now for two non-obvious points: 

When you start a new client, it has no history of completed WUs.  As you complete WUs, the WUs you get are better, so keep reusing the same client.  I had a bunch of clients that I rotated through (about 3-5), and a little batch file that started the next one after the current was finished.

On Windows, for whatever reason, the client uses the registry.  You *must* update the registry to have the same user id or whatever they call it one each computer.  In wine, you can edit the reg just like in Windows with ```
regedit
```.  I will be adding a link to the howto I used in the wiki.

---

