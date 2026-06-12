---
title: "Guest Windows 7 error message, &quot;Windows created a temporary paging file on your ...&quot;"
date: 2015-11-30
forum: Virtualisation
---

### Post by moonguide on 2015-11-30
I'm running VirtualBox 4.3.34_Ubuntu r104062 on Ubuntu 14.04. I have a Windows 7 guest that started giving me this message a week or so ago:

"Windows created a temporary paging file on your computer because of a problem that occurred with your paging file configuration when you started your computer. The total paging file size for all disk crives may be somewhat larger than the size you specified."

I run a program called GearPlayer 4, which is used by transcriptionists to play back an audio file and control play/pause/backspace with a foot pedal.

During those times when I was able to start the virtual Windows 7, I had no problem loading and playing audio files. Today, while GearPlayer acts as if it loaded a file, there's no sound when I try to play it. The file resides on a shared folder. I don't use Windows 7 for other purposes, and don't keep copies of either the audio file or the transcription on the virtual machine. I have confirmed that there is audio content in the .mp3 file by opening it with Totem Movie Player and with Audacity. 

I followed defaults when installing Windows 7 on the virtual machine, so I have a Win7.vmdk that is 25 GB. 

Where do I start looking for what to do to restore the machine to it's previous functionality?

---

### Post by T.J. on 2015-12-01
That's a Windows issue. Check how much space you have left on C drive.  If you have less than 2-4 GB you probably need to expand the allocated disk space.  I would go into your computer properties and disable the swap file, reboot, re-enable it and reboot again.  That should delete and recreate the swap file. I would also defrag the disk.

---

### Post by SeijiSensei on 2015-12-01
Remember that all those fixes apply to the virtual hard drive on which Windows is installed.  

25 GB might be a bit small.  I'd start by cleaning out the Recycle Bin and running the Control Panel utility to identify possible junk.  Defragmenting might help, but I'm guessing you're just at or near the maximum size of the virtual drive.

Take a look, too, at the amount of free space on the Linux host, and at the size of the virtual image in $HOME/VirtualBox VMs/.  Maybe the Linux drive is full or nearly full.

---

### Post by moonguide on 2015-12-01
The C drive is pretty full. It claims to have zero bytes free. It's actually a few hundred megabytes, but it might as well be zero. I tried your ideas about disabling the swap file, but that didn't amount to much. I ran windirstat which showed that C:\Windows is using 94 percent of the space. I might have to create a new virtual machine with more space and reinstall Windows 7 and GearPlayer 4 again. (Not that big of a deal.)

Thanks for your thoughts.

---

### Post by moonguide on 2015-12-01
The drive on which the vmdk resides has a total capacity of 483.8  GB, and has 287.4 GB free.

I ran the tools to clean things out, but there wasn't much to clean. I've just been pointed to:

[http://www.cnet.com/how-to/delete-windows-update-files-to-regain-hard-drive-space/](http://www.cnet.com/how-to/delete-windows-update-files-to-regain-hard-drive-space/)

I'll give that a try.

Thanks for your thoughts.

---

### Post by moonguide on 2015-12-01
It turns out that my virtual machine was in a .vmdk file, not a vdi, and the tool to increase the size of a .vmdk is not yet released.

So, I simply created a new virtual Windows 7 machine, installed Windows 7 on it, installed GearPlayer 4 on that, fixed an audio driver issue, and I'm ready to go.

Thanks to all for your comments.

---

### Post by T.J. on 2015-12-02
If the problem is solved, please mark the thread as closed.

---

### Post by moonguide on 2015-12-02
I looked for where to do that, but I didn't discover until this morning that the tool to use to do that has been buried. I had to search the web for an answer on how to mark the thread as closed. For others with the same problem, there's an item in the bar just above the messages called, "Thread Tools." It has the thing to click to mark a thread as closed.

---

