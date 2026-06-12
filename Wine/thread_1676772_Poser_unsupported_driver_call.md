---
title: "Poser unsupported driver call"
date: 2011-01-27
forum: Wine
---

### Post by mystmaiden on 2011-01-27
I've run Poser 5 under wine with few issues in every version of Ubuntu I've used until now. I'm running Ubuntu 10.04 LTS. Poser seemed to install just fine but when I try to open it I get an 'unsupported driver call' error but no details of any kind. I'm at a loss on how to even begin sorting it out. As far as configuring wine, I left it on all default, could my problem be there?

thanks,

mystmaiden

edited to add - I can't seem to cd to the right spot to start it via the command line. The path is Programs/Curious Labs/ Poser 5/poser.exe

---

### Post by mystmaiden on 2011-01-27
Sorry I should add a bit more information

Ubuntu 10.04 LTS
Wine 1.2

I just have onboard video going, no card installed currently, I'm not sure what drivers are currently working but I was battling with getting my Nvidia card to work - gave up but maybe there's something residual mucking up the works?

As far as the apps list goes, Poser 5 is older but it was listed as gold and from my personal experience it worked well for me before (with Ubuntu 8.04- 9.10 and an earlier version of wine.)

I'm not getting the command right when I try to cd to the file and start it via the terminal but when I browse the c drive and navigate to it, this is the error I get - 
```
Archive:  /home/mystmaiden/.wine/dosdevices/c:/Program Files/Curious Labs/Poser 5/poser.exe
[/home/mystmaiden/.wine/dosdevices/c:/Program Files/Curious Labs/Poser 5/poser.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /home/mystmaiden/.wine/dosdevices/c:/Program Files/Curious Labs/Poser 5/poser.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /home/mystmaiden/.wine/dosdevices/c:/Program Files/Curious Labs/Poser 5/poser.exe or
          /home/mystmaiden/.wine/dosdevices/c:/Program Files/Curious Labs/Poser 5/poser.exe.zip, and cannot find /home/mystmaiden/.wine/dosdevices/c:/Program Files/Curious Labs/Poser 5/poser.exe.ZIP, period.

```I'm not sure what all that actually means.

I think I may have been making the command lines too complicated as far as cd-ing to the file and starting it. I was using commands I found on the winehq site. But when I just did ```
cd .wine
wine start poser

```(Not sure those commands are correct) but it came up with a long list of dll files it needed. When I looked at the Poser 5  file more closely  they were there but hidden so I moved them to windows/system 32 and stopped getting the dll file errors. I also found a shellextension.exe file on the content cd and put it in system 32. The program still starts to load then closes immediately but there is a shorter list of errors (the screen also sort of flashes when it happens.) Now it returns just these..

```
mystmaiden@hal:~$ cd .wine
mystmaiden@hal:~/.wine$ wine start poser
fixme:ntoskrnl:KeInitializeMutex stub: 0x110dc0, 0
fixme:ntoskrnl:KeInitializeMutex stub: 0x110f00, 0
fixme:ntoskrnl:KeInitializeMutex stub: 0x110f28, 0
fixme:ntoskrnl:IoGetDeviceObjectPointer stub: L"\\Device\\DebugMessageDevice" 1f01ff 0x53e62c 0x53e628
fixme:ntoskrnl:KeInitializeEvent stub: 0x111008 1 0
fixme:ntoskrnl:KeInitializeEvent stub: 0x111020 1 0
fixme:ntoskrnl:IoRegisterDriverReinitialization stub: 0x6832c4a0 0x5443ee 0x111e80
fixme:exec:SHELL_execute flags ignored: 0x00000100
mystmaiden@hal:~/.wine$ 

```

---

### Post by mystmaiden on 2011-01-29
Giving this a little bump in case anyone is following along. In another thread Nightwish suggested rolling back to wine 1.0 and downloading winetricks from WineHQ. 

This is the result - 

```
mystmaiden@hal:~$ cd .wine
mystmaiden@hal:~/.wine$ wine poser.exe
err:winedevice:ServiceMain driver L"TPkd" failed to load
err:menubuilder:WinMain unknown option -a
err:menubuilder:WinMain unknown option -r
mystmaiden@hal:~/.wine$ env WINEPREFIX="/home/mystmaiden/.wine" wine "C:\Program Files\Curious Labs\Poser 5\Poser.exe"
err:winedevice:ServiceMain driver L"TPkd" failed to load
err:menubuilder:WinMain unknown option -a
err:menubuilder:WinMain unknown option -r
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:font:load_VDMX No suitable ratio found
wine: Call from 0x7b845390 to unimplemented function msvcirt.dll.??0streambuf@@IAE@XZ, aborting
Segmentation fault
mystmaiden@hal:~/.wine$ 


```The program still loads then closes immediately.

UPDATE - Thanks to NightwishFan who put me on the right track! I searched the first err on the list above and found a post I had made a few years back and in that thread was the answer. I just needed to use winetricks to load the vm6 file. So after several headaches and several days frustration here's what got Poser going for me - just in case someone else wants to give it a whirl.

Install and configure wine 1.0, then do Not use the winetricks deb from synaptic, instead go to [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks) and install it with the wget command line you see there.

Make sure to have the core ms fonts and vm6 loaded via winetricks

Install Poser and move the dlls to windows/system 32 (I also had to copy the ShellExtension.exe file from the content cd  and copy the poser.exe file to system 32)

Then cross your fingers and click through  Applications/Wine/Programs/Curious Labs/Poser/Poser

---

