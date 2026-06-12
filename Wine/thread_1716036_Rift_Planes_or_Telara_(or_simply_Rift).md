---
title: "Rift: Planes or Telara (or simply Rift)"
date: 2011-03-27
forum: Wine
---

### Post by Extol11 on 2011-03-27
Hi! I installed this game from the client downloaded from the game's website. The wine appdb on winehq.com's site says the game runs great and has a gold rating. The only thing is that it was tested on 10.10 and I'm running 10.04. I installed the game and patched it all the way to the last one. It patches fine, the game client loads fine, but when I click play, the client just dissappears and doesn't do anything. I need help to find out the source of the problem, but I haven't touched wine in a long time. I'd like to know how can I find a way to start the game with wine through the cli so I can find out any problems the game might be having. Also, the game keeps saying I need to update the DirectX install. On the site they recommended installing d3dx9  and I did through winetricks. I installed winetricks using the ubuntu PPA they have on the site. I'm pretty sure it can't be hard to get it working. 

So how can I find out where the game installed so I can use the command wine with this executable?

Thanks in advance.

---

### Post by Kenjitamura on 2011-03-28
I read that you have to use padsp to have stable audio so my command includes that...I'd imagine if it installed the way mine did the command would look like this > padsp wine ".wine/drive_c/Program Files/RIFT Game/riftpatchlive.exe"  I have to launch from riftpatchlive, when I try to run rift.exe nothing happens.  It's common when selecting play to receive an error about connecting with the patching process, that's a bug on wines part from what I understand.  If you receive that error message just exit it out and hit play again and as many times as it takes until it starts.

Anyway the error I used to get was something about d3dx9_43, if you get that error go into winecfg and change the *d3dx9_43 override from native to builtin.

---

### Post by Extol11 on 2011-03-28
Thanks a whole lot. I'll give it a try later tonight. And the directx9 problem (it keeps asking me to install it) should be gone with the d3dx9_43 too I suppose. I'll let you know how it goes.

---

### Post by Dragonorb13 on 2011-04-04
> **Extol11 said:**
> Hi! I installed this game from the client downloaded from the game's website. The wine appdb on winehq.com's site says the game runs great and has a gold rating. The only thing is that it was tested on 10.10 and I'm running 10.04. I installed the game and patched it all the way to the last one. It patches fine, the game client loads fine, but when I click play, the client just dissappears and doesn't do anything. I need help to find out the source of the problem, but I haven't touched wine in a long time. I'd like to know how can I find a way to start the game with wine through the cli so I can find out any problems the game might be having. Also, the game keeps saying I need to update the DirectX install. On the site they recommended installing d3dx9  and I did through winetricks. I installed winetricks using the ubuntu PPA they have on the site. I'm pretty sure it can't be hard to get it working. 

So how can I find out where the game installed so I can use the command wine with this executable?

Thanks in advance.

your problem isn't finding the .exe, it's your version of Wine... you need to get the beta version, the stable version doesn't work with Rift. Problem I ran into for a while.

---

### Post by mreyes000 on 2011-04-07
> **Dragonorb13 said:**
> your problem isn't finding the .exe, it's your version of Wine... you need to get the beta version, the stable version doesn't work with Rift. Problem I ran into for a while.


i'm running 1.3 and i'm getting the same issue.

EDIT: after a bit of research i got it to work by editing the user.reg file to list the d3dx9_43 to native,builtin.  It works, however as usual with a significant reduction in fps

---

### Post by 23494asd on 2011-04-17
Could someone be so kind to post a step by step howto upgrade from 1.2.2 wine and then proper install RIFT?

Where can i find this file "user.reg"?

edit

I can run the riftpatchlive.exe, then comes a directx message to install and then c++2008 and the program shuts

---

### Post by Kenjitamura on 2011-04-22
I'm still fairly new to ubuntu in that I don't have a tendency to explore it as much as I should so anyone feel free to correct posted commands.  To remove current wine > sudo apt-get remove --purge wine Then add the wine repository for ubuntu versions 9.10+ > sudo add-apt-repository ppa:ubuntu-wine/ppa finally > sudo apt-get update

You'll then want to remove your current wine directory > rm -rf ~/.wine  Now when you enter your synaptic package manager and do a search for wine an option for wine1.3 should come up.  Install from package manager wine1.3, wine1.3-dev, and winetricks (gecko and fonts should auto install with wine1.3).  It's probably best to install Rift to its own bottle so in your home directory create a folder and name it .wine-rift > mkdir .wine-rift People say Rift on ubuntu runs best on wine under Windows 7 with OSS audio so open winecfg for that bottle > WINEPREFIX="/home/your name/.wine-rift" winecfg and set it to Windows 7 under applications and OSS in audio.

Now for the installation, first run the commands > WINEPREFIX="/home/your name/.wine-rift" winetricks d3dx9 and > WINEPREFIX="/home/your name/.wine-rift" winetricks vcrun2008 Now open winecfg again > WINEPREFIX="/home/your name/.wine-rift" winecfg Under the Libraries tab scroll down the overrides to *d3dx9_43 edit it and change it to builtin.

Launch the Rift installer using the command > WINEPREFIX="/home/your name/.wine-rift" wine /path/to/installer.exe If it ever asks to install directx or Microsoft Visual 2008 don't (deselect them and continue).  The install should go pretty flawlessly, when it's done launch the game with > WINEPREFIX="/home/yourname/.wine-rift" padsp wine ".wine-rift/drive_c/Program Files/RIFT Game/riftpatchlive.exe"


---

### Post by KEE on 2011-04-30
i get this error ```
root@poops:~# sudo add-apt-repository ppa:ubuntu-wine/ppa
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 883E8688397576B6C509DF495A9A06AEF9CB8DB0
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: key F9CB8DB0: "Launchpad PPA for Ubuntu Wine Team" 1 new signature
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:         new signatures: 1
root@poops:~# sudo apt-get update
Get:1 http://dl.google.com stable Release.gpg [197B]
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_CA       
Get:2 http://dl.google.com stable Release [1,347B]                             
Hit http://archive.ubuntu.com lucid Release.gpg                                
Get:3 http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_CA [10.3kB]
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_CA       
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/ssakar/ppa/ubuntu/ lucid/main Translation-en_CA   
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Get:4 http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_CA [425B]
Get:5 http://dl.google.com stable/main Packages [1,064B]             
Hit http://archive.canonical.com lucid Release                                 
Ign http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/ lucid/main Translation-en_CA
Ign http://ppa.launchpad.net lucid Release.gpg                       
Ign http://ppa.launchpad.net/ubuntu-wine/pp/ubuntu/ lucid/main Translation-en_CA
Hit http://ppa.launchpad.net lucid Release.gpg                       
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main Translation-en_CA
Hit http://ppa.launchpad.net lucid Release                           
Get:6 http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_CA [663B]
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_CA       
Hit http://archive.ubuntu.com lucid-updates Release.gpg                        
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_CA
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_CA
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_CA
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_CA
Hit http://archive.ubuntu.com lucid-security Release.gpg             
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_CA
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_CA
Hit http://archive.canonical.com lucid/partner Packages
Hit http://ppa.launchpad.net lucid Release     
Ign http://ppa.launchpad.net lucid Release                           
Hit http://ppa.launchpad.net lucid Release                           
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_CA
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_CA
Hit http://archive.ubuntu.com lucid Release
Hit http://archive.ubuntu.com lucid-updates Release                  
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://ppa.launchpad.net lucid/main Sources
Hit http://archive.ubuntu.com lucid-security Release
Ign http://ppa.launchpad.net lucid/main Packages
Hit http://archive.ubuntu.com lucid/main Packages
Hit http://archive.ubuntu.com lucid/restricted Packages
Hit http://archive.ubuntu.com lucid/main Sources
Hit http://archive.ubuntu.com lucid/restricted Sources
Hit http://archive.ubuntu.com lucid/universe Packages
Hit http://archive.ubuntu.com lucid/universe Sources
Hit http://archive.ubuntu.com lucid/multiverse Packages
Hit http://archive.ubuntu.com lucid/multiverse Sources
Hit http://archive.ubuntu.com lucid-updates/main Packages
Hit http://archive.ubuntu.com lucid-updates/restricted Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://archive.ubuntu.com lucid-updates/main Sources
Hit http://archive.ubuntu.com lucid-updates/restricted Sources
Hit http://archive.ubuntu.com lucid-updates/universe Packages
Hit http://archive.ubuntu.com lucid-updates/universe Sources
Hit http://archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://archive.ubuntu.com lucid-updates/multiverse Sources
Hit http://archive.ubuntu.com lucid-security/main Packages
Hit http://archive.ubuntu.com lucid-security/restricted Packages
Hit http://archive.ubuntu.com lucid-security/main Sources
Hit http://archive.ubuntu.com lucid-security/restricted Sources
Hit http://archive.ubuntu.com lucid-security/universe Packages
Hit http://archive.ubuntu.com lucid-security/universe Sources
Hit http://archive.ubuntu.com lucid-security/multiverse Packages
Hit http://archive.ubuntu.com lucid-security/multiverse Sources
Ign http://ppa.launchpad.net lucid/main Packages
Err http://ppa.launchpad.net lucid/main Packages
  404  Not Found
Fetched 14.0kB in 1s (7,093B/s)
W: Failed to fetch http://ppa.launchpad.net/ubuntu-wine/pp/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by brian70809 on 2011-04-30
Just go to WineHQ and go to the beta link.. Download the DEB file and click it.. It will auto install it.

I would Uninstall your previous version of wine.

Make sure you have winetricks installed and follow the script on how to install the various components you will need.

or

You can use Crossover Games and have it self install Rift for you.  It's wine, but the pay version..

Make sure you have your graphics at MED and the Projected Textures off.  If you have any type of decent system,  you should be in the 20-30fps range on these settings.. Very Playable.

---

### Post by Kenjitamura on 2011-05-01
I can tell you why the error is coming up, but I can't explain how that error is happening.  

It says in your terminal ```
W: Failed to fetch http://ppa.launchpad.net/ubuntu-wine/pp/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found
```

If you type in your address bar: ```
http://ppa.launchpad.net/ubuntu-wine/pp/ubuntu/dists/lucid/main/binary-i386/Packages.gz
``` You also get the 404. Reason being ubuntu-wine/**pp**/ubuntu/ is an incorrect address.  It needs to be ```
http://ppa.launchpad.net/ubuntu-wine/**ppa**/ubuntu/dists/lucid/main/binary-i386/Packages.gz
```  Typing that in the url brings up the packages.

I don't know enough about ubuntu to tell you why the repository is sending you to the wrong address.

Try opening your Synaptic Package Manager, under Settings go to Repositories, and finally under the "Other Software" tab locate the wine repository and manually editing the link to add the missing "a" so it reads ```
http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu
```

Someone had the same issue here [http://ubuntuforums.org/showthread.php?t=1559411]("http://ubuntuforums.org/showthread.php?t=1559411")

---

### Post by KEE on 2011-05-02
it now says my nvidia driver is out of date. i do seem to be stuck with gnu dont know how to uninstall it```
bash: /usr/share/GNUstep/Makefiles/filesystem.sh: No such file or directory
bash: /usr/share/GNUstep/Makefiles/print_unique_pathlist.sh: No such file or directory
bash: /usr/share/GNUstep/Makefiles/print_unique_pathlist.sh: No such file or directory
bash: /usr/share/GNUstep/Makefiles/print_unique_pathlist.sh: No such file or directory
bash: /usr/share/GNUstep/Makefiles/print_unique_pathlist.sh: No such file or directory
bash: /usr/share/GNUstep/Makefiles/print_unique_pathlist.sh: No such file or directory
poops@poops:~$ 

```

---

### Post by KEE on 2011-05-02
fail
[IMG]http://i222.photobucket.com/albums/dd124/assripp3r/Screenshot-2-5.png[/IMG]
[IMG]http://i222.photobucket.com/albums/dd124/assripp3r/Screenshot-4-1.png[/IMG]

---

### Post by KEE on 2011-05-02
k i got it working. but there is no sound while in game play?

---

### Post by Kenjitamura on 2011-05-02
That could be a wine issue that's been cropping up in the recent version. I had this too.  I would test sound in winecfg and always got an audio failure message. My fix was to open winecfg set the audio to alsa and the  hardware acceleration to emulation, logout of ubuntu and log back in, re-open winecfg and when I tested the sound it worked.

---

### Post by Crucias on 2011-05-02
I get the following terminal print outs

```
crucias@Crucias-PC://home/crucias/.wine/drive_c/Program Files/RIFT Game/RIFT Game$ wine selfpatchlive.exe
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
crucias@Crucias-PC://home/crucias/.wine/drive_c/Program Files/RIFT Game/RIFT Game$ fixme:system:SetProcessDPIAware stub!
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:ole:CoCreateInstance no instance created for interface {ea1afb91-9e28-4b86-90e9-9e9f8a5eefaf} of class {56fdf344-fd6d-11d0-958a-006097c9a090}, hres is 0x80004002
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS
fixme:imm:ImmReleaseContext (0x30060, 0x190488): stub
fixme:win:FlashWindowEx 0x33eb2c
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:win:FlashWindowEx 0x339a2c
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS
fixme:win:FlashWindowEx 0x337398
fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
err:module:import_dll Library d3dx9_43.dll (which is needed by L"C:\\Program Files\\RIFT Game\\RIFT Game\\rift.exe") not found
err:module:import_dll Library d3dx9_43.dll (which is needed by L"C:\\Program Files\\RIFT Game\\RIFT Game\\rift.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\RIFT Game\\RIFT Game\\rift.exe" failed, status c0000135

```

I have selfpatchlive.exe set to run in Win7 mode, default win7 mode and set all the dll's i need to native (dx9-43, rich20 and rich32).

Seems from err:module:import_dll Library d3dx9_43.dll i am missing this dll file. When i run winetricks -show-installed (or something similar) it shows this not installed. How can i get it? [This thread]("http://forum.winehq.org/viewtopic.php?p=58728&sid=9c98ee18a8e7095825a2dfc1924ff21c") shows a way to patch winetricks but i have no idea how to use the diff file

---

### Post by Kenjitamura on 2011-05-04
In winecfg under Libraries the *d3dx9_43 dll needs to be set to builtin not native.

---

### Post by t.rei on 2011-05-05
I'm getting an error #2016 every time I try to log in. *sigh* Will try again tomorrow.

---

### Post by Kenjitamura on 2011-05-05
If you get an error that says something along the line of cannot connect to patching process it's a bug on wine's part.  If you keep trying to log in eventually it'll let you...here is the bug [http://bugs.winehq.org/show_bug.cgi?id=17195]("http://bugs.winehq.org/show_bug.cgi?id=17195")  There used to be a patch but it doesn't work with the latest versions of wine.

---

### Post by t.rei on 2011-05-06
Oh, that error was definately me. I hardly ever reboot my computer so I forgot the ptrace thing. ;)
as "sudo su -" ran```
echo 0 > /proc/sys/kernel/yama/ptrace_scope
``` and now the only problem is HORRIBLE performance. While wow actually runs BETTER than on winslow, rift is still giving me a headache.

---

### Post by t.rei on 2011-05-08
So I got it running, and the performance is okish when using low quality renderers (on high all skin is PURPLE!). Only problem with playing on low quality renderers is: there are no sparkles on mission-items, wich frankly... sucks... big time. So I guess it's dual-boot for rift... *Sigh* And no more rift once sub is used, probably.

---

### Post by KEE on 2011-05-10
hey something after the update 1.2 the game dont work anymore

---

### Post by Kenjitamura on 2011-05-10
Same issue for me.  Rift patched to 1.2 and when running it in Windows 7 mode a wine error output comes up saying "Rift.exe has encountered a serious problem and needs to close".  When I run it in Windows XP mode rather than a wine error box I get the Rift error handler that sends an error report.

Anyone identified what the problem is?

According to [http://forums.riftgame.com/showthread.php?185656-quot-sending-error-report-quot-whenever-I-hit-Play/page6]("http://forums.riftgame.com/showthread.php?185656-quot-sending-error-report-quot-whenever-I-hit-Play/page6") many other people got the same error.  Trion has already released a new update for the patcher which has resolved the error for most Widnows Users... mine still remains and according to the thread there are still others who have the problem as well.

---

### Post by Kenjitamura on 2011-05-10
Sorry to double post however thought the new information should garner attention.  Trion is aware that the log in problem is still happening for people playing the game outside a windows environment.

Following message is from a forum moderator

> Hi everyone,

We'd like to gather a little more info from those who are experiencing this issue. If you have the latest patcher (31-20e) and are running RIFT on a Mac, please let us know in this thread. Also, we'd like to know if you're running RIFT on your Mac using Boot Camp or not.

Thanks! 

Link to the thread:[http://forums.riftgame.com/showthread.php?185656-quot-sending-error-report-quot-whenever-I-hit-Play]("http://forums.riftgame.com/showthread.php?185656-quot-sending-error-report-quot-whenever-I-hit-Play")

My suggestion is to comment in that thread (a couple have already done so).

Also as I mentioned earlier if you change, in winecfg, the mode to Windows XP when you try to log in the Rift Error Handler comes up instead of a wine error and you can send an error report.  The more error reports the more likely this will get fixed for Wine users.

---

### Post by KEE on 2011-05-11
has this been fix yet?

---

### Post by Kenjitamura on 2011-05-12
As of right now this still has not been fixed, no indication yet as to whether the problem is on Trion's side or Wine's side.  

Important Notice:  Trion has officially renounced any obligation to supporting Rift on non-Windows OS's.  The Wine AppDB should change the platinum rating to something like a bronze because there will probably be problems after every patch here on out.

Bottom line: DO NOT subscribe to Rift until it has been resolved or you have a windows dual boot.  I do not recommend using the subscription durations of longer than 1 month for the discount as you may need to cancel frequently.  Again, this only applies to people without access to Windows.

If this is a problem to you vote up the bug at [http://bugs.winehq.org/show_bug.cgi?id=27125]("http://bugs.winehq.org/show_bug.cgi?id=27125") and maybe WINE will come through for us.

I'm not expecting to even be able to log into Rift for a week unless Trion decides to fix the problem earlier.

---

### Post by t.rei on 2011-05-13
Dual booting myself again. Long time since I last did that. Took me the better part of a day just to patch windows... with all those reboots to reveal even more important patches that need to be installed... *sigh*

Even if that patch hadn't broken it all together, I'd still dual boot for performance issues.

---

### Post by Kenjitamura on 2011-05-13
I am in shock, here is a message from a forum moderator at the Rift Forums.

> Hey guys -

Apologies for what happened with the WINE / RIFT incompatibilities... luckily, we think we've figured out a way to make it all work again, and it should go out in our next hotfix update.

Thanks for your patience!
Alex 

Found at: [http://forums.riftgame.com/showthread.php?188265-Disallowing-play-using-WINE/page4]("http://forums.riftgame.com/showthread.php?188265-Disallowing-play-using-WINE/page4")

I'm not sure if the hotfix is going to work but Trion went out of its way to fix a problem for Wine users.  Also, yeah t.rei playing a directx game on ubuntu does kind of suck.  I have to keep all settings on low and still get poor fps, for directx games they should be played on windows.

Good news if you are looking into Diablo 3 when it comes out (I heard beta testing starts in June) Blizzard releases all its newest games with both DirectX and OpenGL support so it should play as well if not better on ubuntu as it does in Windows.

---

### Post by KEE on 2011-05-16
> **KEE said:**
> fail
[IMG]http://i222.photobucket.com/albums/dd124/assripp3r/Screenshot-2-5.png[/IMG]
[IMG]http://i222.photobucket.com/albums/dd124/assripp3r/Screenshot-4-1.png[/IMG]

I m getting the same screen errors

---

### Post by harliCobweb on 2011-05-16
HI ok so i was else where when the whole rift stopped working with wine thingy happened due to installing a new graphics card, have been up and running for a bit now and have since heard about it, lol, ok so what i did was change all the d3dx9 and *msvcr90 .dll's in wine config to native, builtin in a new wineprefix - before this i had a screen allmost exactly like yours kee[U]
[/U]

---

### Post by KEE on 2011-05-17
> **harliCobweb said:**
> HI ok so i was else where when the whole rift stopped working with wine thingy happened due to installing a new graphics card, have been up and running for a bit now and have since heard about it, lol, ok so what i did was change all the d3dx9 and *msvcr90 .dll's in wine config to native, builtin in a new wineprefix - before this i had a screen allmost exactly like yours kee[U]
[/U]no idea what your changing, anyway its not working  ```
***@***:~$ WINEPREFIX="/home/***/.wine-rift" winetricks msvcr90
Unknown arg msvcr90

```[IMG]http://i222.photobucket.com/albums/dd124/assripp3r/Screenshot-3-3.png[/IMG][IMG]http://i222.photobucket.com/albums/dd124/assripp3r/Screenshot-4-3.png[/IMG][IMG]http://i222.photobucket.com/albums/dd124/assripp3r/Screenshot-5-2.png[/IMG]

---

### Post by harliCobweb on 2011-05-17
have you installed vcrun2008

---

### Post by KEE on 2011-05-17
> **harliCobweb said:**
> have you installed vcrun2008

me? i didn't. what is that?
```
*@*:~$ sudo aptitude install vcrun2008
[sudo] password for *: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "vcrun2008"
Couldn't find any package whose name or description matched "vcrun2008"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

```

---

### Post by Willard on 2011-05-18
> **KEE said:**
> me? i didn't. what is that?
Visual C++ 2008 runtime. Rift needs that to run.

You get it using winetricks, as Kenjitamura explained:
> **Kenjitamura said:**
> Now for the installation, first run the commands
```

WINEPREFIX="/home/your name/.wine-rift" winetricks d3dx9

```
**and**
```

WINEPREFIX="/home/your name/.wine-rift" winetricks vcrun2008

```
Now open winecfg again  Under the Libraries tab scroll down the overrides to *d3dx9_43 edit it and change it to builtin.[...]

Launch the Rift installer using the command  If it ever asks to install directx or Microsoft Visual 2008 don't (deselect them and continue).  The install should go pretty flawlessly, [...]
By the way, I followed the directions given in Kenjitamura's post, and my game runs. Granted, without sound (so far), but it runs, and graphics are not buggy.

I am running Ubuntu 11.04 with wine-1.3.20, on a 4-year old laptop (with dedicated graphics). The game is playable with low graphics rendering.

---

