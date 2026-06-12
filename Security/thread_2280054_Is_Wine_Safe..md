---
title: "Is Wine Safe."
date: 2015-05-27
forum: Security
---

### Post by QDR06VV9 on 2015-05-27
So Ok I have used linux for about 11 or 12 years now without a piece of malware or virus.
That being said I also like testing android based Roms. **I do not use Windows at all**.
I had a problem with pushing a rom to my tablet using Ubuntu so I asked a friend if I could use his windows machine.
All good there. But had to install odin to flash a recovery, When installing Odin Eset had blocked a url exploit, Again all is good uninstalled Odin found another link for Odin.
So I loaded the bad file for odin so I could report to the hosting site and they wanted a malwarebytes log to see.
As we all know there is no malwarebytes install for Ubuntu, Here is where the fun begins.
> How to Install Malwarebytes on Ubuntu
by G.S. Jackson, Demand Media

Your office workstations use Ubuntu because of their cost and reliability. Ubuntu computers are known for their security, but this does not rule out the possibility of viruses. If you want to use a Windows virus program, such as the Malwarebytes free antivirus tool, you must first install the Windows environment application Wine, then install Malwarebytes through that. Once installed, you can use the application just like a native Windows program.
Step 1

Download the Malwarebytes installer to your Ubuntu Desktop (see Resources).
Step 2

Click on the Ubuntu dash symbol, type "terminal" into the search bar and click the terminal option that appears in the search results.

Step 3

Enter the following commands to enter the Wine repository into your Ubuntu installation list, each followed by pressing the "Enter" key:
sudo add-apt-repository ppa:ubuntu-wine/ppa && sudo apt-get update
Enter your password when prompted.
Step 4

Enter the following command in the terminal to install Wine, the Windows program loader for Linux:
sudo apt-get install wine
Step 5

Right-click the Malwarebytes installation icon on your desktop. Select "Open With Wine Windows Program Loader" from the drop-down menu. The Wine installation wizard will begin and walk you through the installation process.
References (1)
Resources (2)
About the Author

G.S. Jackson specializes in topics related to literature, computers and technology. He holds a Bachelor of Arts in English and computer science from Southern Illinois University Edwardsville.
And It did find the Odin PUP
But the rest was a bit of a delema, So is Wine safe? Here is the log I had sent.
> Malwarebytes Anti-Malware 
[www.malwarebytes.org]("http://www.malwarebytes.org") 
 
Scan Date: 5/27/2015 
Scan Time: 12:59:24 PM 
Logfile: mb log.txt 
Administrator: Yes 
 
Version: 2.01.6.1022 
Malware Database: v2015.05.27.04 
Rootkit Database: v2015.05.24.01 
License: Free 
Malware Protection: Disabled 
Malicious Website Protection: Disabled 
Self-protection: Disabled 
 
OS: Windows XP Service Pack 3 
CPU: x64 
File System: NTFS 
User: mate 
 
Scan Type: Custom Scan 
Result: Completed 
Objects Scanned: 284840 
Time Elapsed: 1 hr, 13 min, 7 sec 
 
Memory: Enabled 
Startup: Enabled 
Filesystem: Enabled 
Archives: Enabled 
Rootkits: Disabled 
Heuristics: Enabled 
PUP: Enabled 
PUM: Enabled 
 
Processes: 0 
(No malicious items detected) 
 
Modules: 0 
(No malicious items detected) 
 
Registry Keys: 0 
(No malicious items detected) 
 
Registry Values: 0 
(No malicious items detected) 
 
Registry Data: 5 
Broken.OpenCommand, HKCR\batfile\shell\open\command, Good: ("Bad: ()" %*), Delete-on-Reboot,[ffffffffffffffffffffffffffffffff], %5 
Broken.OpenCommand, HKCR\comfile\shell\open\command, Good: ("Bad: ()" %*), Delete-on-Reboot,[ffffffffffffffffffffffffffffffff], %5 
Broken.OpenCommand, HKCR\piffile\shell\open\command, Good: ("Bad: ()" %*), Delete-on-Reboot,[ffffffffffffffffffffffffffffffff], %5 
Broken.OpenCommand, HKCR\scrfile\shell\open\command, Good: ("Bad: ()" /S), Delete-on-Reboot,[ffffffffffffffffffffffffffffffff], %5 
Broken.OpenCommand, HKCR\regfile\shell\open\command, Good: (regedit.exe "Bad: ()"), Delete-on-Reboot,[ffffffffffffffffffffffffffffffff], %5 
 
Folders: 0 
(No malicious items detected) 
 
Files: 9 
[COLOR=#ff0000]PUP.Optional.Unizeto, C:\users\mate\My Documents\Documents\Tablet Root\Odin3-v1.85_3.zip.exe, Quarantined[/COLOR], [6f31a7f197f358de4cd29286a85e46ba],  
Trojan.Agent, C:\windows\system32\dmusic32.dll, Quarantined, [bce47b1d15756dc9a0ea0b6e0bf96997],  
Trojan.Agent, C:\windows\syswow64\dmusic32.dll, Quarantined, [841c752301892a0cfa90db9e56ae6898],  
Backdoor.Bot, C:\windows\system32\iexplore.exe, Quarantined, [e7b9fe9aa3e7c47281689ede36ce8080],  
Backdoor.Bot, C:\windows\syswow64\iexplore.exe, Quarantined, [e2be2c6cdeacb0863faaa8d446bed12f],  
Trojan.Agent, C:\windows\rundll.exe, Quarantined, [b0f090081674d2648451e9aaa06442be],  
Trojan.Tracur, C:\windows\system32\winnls32.dll, Quarantined, [9c04a7f1e1a9a69090258f39699b41bf],  
Trojan.Tracur, C:\windows\syswow64\winnls32.dll, Quarantined, [2c7400984d3d092d3580d5f3cd3724dc],  
Trojan.Agent, C:\windows\system32\start.exe, Quarantined, [128e3f5924662214dbadf4f2cd377f81],  
 
Physical Sectors: 0 
(No malicious items detected)   
(end) 
Kind Regards
Never Mind I found what i was looking for
> **Risks**

  
**11.1. Wine is malware-compatible**

 Just because Wine runs on a non-Windows OS doesn't mean you're protected from viruses, trojans, and other forms of malware. 
There are several things you can do to protect yourself: 

[LIST]
[*]Never run executables from sites you don't trust. [Infections have already happened.]("http://www.winehq.org/pipermail/wine-devel/2007-January/053719.html") 
[*]In web browsers and mail clients, be suspicious of links to URLs you don't understand and trust. 
[*]Never run any application (including Wine applications) as root (see [above]("http://wiki.winehq.org/FAQ#run_as_root")). 
[*]Use a virus scanner, e.g. [ClamAV]("http://www.clamav.org") is a free virus scanner you might consider using if you are worried about an infection; see also [Ubuntu's notes on how to use ClamAV]("https://help.ubuntu.com/community/ClamAV"). No virus scanner is 100% effective, though. 
[*]Removing  the default Wine Z: drive, which maps to the unix root directory, is a  weak defense. It will not prevent Windows applications from reading your  entire filesystem, and **will prevent you from running Windows applications that aren't reachable from a Wine drive (like C: or D:).** A workaround is to copy/move/symlink downloaded installers to ~/.wine/drive_c before you can run them. 
[*]If you're running applications that you suspect to be infected, run them as their own Linux user or in a virtual machine (the [ZeroWine]("http://wiki.winehq.org/ZeroWine") malware analyzer works this way). 
[/LIST]
 
**11.2. How good is Wine at sandboxing Windows apps?**

 **Wine does not sandbox in any way at all.**  When run under Wine, a Windows app can do anything your user can. Wine  does not (and cannot) stop a Windows app directly making native  syscalls, messing with your files, altering your startup scripts, or  doing other nasty things. 
You need to use AppArmor, SELinux or some type of virtual machine if you want to properly sandbox Windows apps. 
Note that the [winetricks]("http://wiki.winehq.org/winetricks") sandbox  verb merely removes the desktop integration and Z: drive symlinks and  is not a true sandbox. It protects against errors rather than malice.  It's useful for, e.g., keeping games from saving their settings in  random subdirectories of your home directory. 


Form Here [http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ)
Maybe Helpful to others.
Regards

---

