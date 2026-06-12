---
title: "Deetecting what is already installed"
date: 2009-06-12
forum: Wine
---

### Post by gwm on 2009-06-12
Hi,
I have some of my own applications that I have written using VB6 and Visual Studio. They seem to install but they don't want to run.

I figured that I need to install Jet and things.

I tried using winetricks to install Jet40 but it failed. Perhaps it's because I'm running a 64 bit Ubuntu? Perhaps it is already installed as part of another windows application install.

How do I find out?

From my reading it looks like one needs to look in system32 to see if the dll is there.

I am expecting this trouble with other .net programs.

Is there a cross reference list somewhere, of the products and their dlls?

Is there a better way of working out what infrastructure is already installed?

---

### Post by asdfoo on 2009-06-12
> **gwm said:**
> Hi,
I have some of my own applications that I have written using VB6 and Visual Studio. They seem to install but they don't want to run.

I figured that I need to install Jet and things.

I tried using winetricks to install Jet40 but it failed. Perhaps it's because I'm running a 64 bit Ubuntu? Perhaps it is already installed as part of another windows application install.

How do I find out?

From my reading it looks like one needs to look in system32 to see if the dll is there.

I am expecting this trouble with other .net programs.

Is there a cross reference list somewhere, of the products and their dlls?

Is there a better way of working out what infrastructure is already installed?

When you install Wine, nothing but the basics are there.  Wine does not interact nor is it designed to interact with existing Windows installs.

So you've installed jet, post the terminal output of the program you're running here and tell us your Wine version.

---

### Post by gwm on 2009-07-08
Sorry about delay in responding, I have been somewhat distracted recently.
To remove the 64 bit possibility, I used a 32 bit PC.
Wine is configured with the default settings as Windows XP.
Running winver.exe tells me that my version of wine is 1.1.25
I downloaded the latest winetricks (2009-07-05). It came as a page full of text, which I saved as a file in my home directory. From there I went into terminal and typed
sh winetricks jet40
This is what happened:
> billy@puer:~$ sh winetricks jet40
Executing wine /home/billy/.winetrickscache/jet40sp8_9xnt.exe
ALSA lib pcm_dmix.c:841:(snd_pcm_dmix_open) unable to create IPC semaphore
fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels
fixme:mixer:ALSA_MixerInit No master control found on PC Camera, disabling mixer
ALSA lib pcm_dmix.c:841:(snd_pcm_dmix_open) unable to create IPC semaphore
fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels
fixme:mixer:ALSA_MixerInit No master control found on PC Camera, disabling mixer
fixme:setupapi:extract_cabinet_file awful hack: extracting cabinet "C:\\windows\\temp\\IXP001.TMP\\Jetsetup.CAB"
fixme:setupapi:SetupDefaultQueueCallbackW notification 262144 params 33f92c,0
fixme:setupapi:extract_cabinet_file awful hack: extracting cabinet "C:\\windows\\temp\\IXP001.TMP\\Jetsetup.CAB"
fixme:setupapi:SetupDefaultQueueCallbackW notification 262144 params 33f92c,0
fixme:setupapi:extract_cabinet_file awful hack: extracting cabinet "C:\\windows\\temp\\IXP001.TMP\\Jetsetup.CAB"
fixme:setupapi:SetupDefaultQueueCallbackW notification 262144 params 33f92c,0
fixme:setupapi:extract_cabinet_file awful hack: extracting cabinet "C:\\windows\\temp\\IXP001.TMP\\Jetsetup.CAB"
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program files\\Common files\\Microsoft shared\\dao\\dao2535.tlb" failed with error 2
Install of jet40 done
winetricks done.

I then went to windows/system32 and found jet40.dll together with several other files with related names.
For my program (called tt), I used vb6 to generate an install executable which I run. when installing on a windows box. Running it in Ubuntu also seems to work okay. The correct files are placed in /Program Files/tt/ and the program can be started. As soon as I ask it to do something that accesses the database, which is an mdb file in the same directory, it fails with a message box saying:
> Program Error
The program tt.exe has encountered a serious problem and needs to close etc. etc. 
During the install, I was told that newer versions of some files already existed. Keeping the existing files or overwriting them yields the same result.

---

### Post by gwm on 2009-07-21
Hi,
As one can see from the above, Jet40 didn't actually install. If that is so, I suppose the Jet dll in system32 must have come from my program install.
Are there perhaps some libraries that I have to make native or something?
If so, which ones?
That brings one back to the initial question in this thread. Is there somewhere, where someone, perhaps at winehq, who is knowledgeable about such things, has been kind enough to create lists of which ms product uses what libraries?
I suppose I could do a directory listing of system32 and simply make all the dlls I find be native libraries. I hate doing that sort of thing because I don't really know what I'm doing and it feels to me that I am likely breaking all sorts of other code.

---

