---
title: "String of odds difficulties has me wondering if 17.04 is an alpha"
date: 2017-08-31
forum: Ubuntu, Linux and OS Chat
---

### Post by gbambo on 2017-08-31
I am not trolling. The reputation of Ubuntu is unsurpassed. That is why I have turned to it. And I am no noob. I was the Director of IT for a $20M company. But I am no Linux expert either.

Ordinarily, I would post these incidents separately. But it is the frequency of them that is the real crux of my concern. Ubuntu 17 feels unusable, which seems a patently absurd conclusion I admit.

Incident I. Install of 17.04 minimal server. Then manual upgrade to Ubuntu-Desktop with no-recommends switch. Cannot find a menu for launching programs to save me life. Research makes reference to several desktop interface elements I cannot find. Shortly thereafter I uninstalled Ubuntu-Desktop and installed Enlightenment. Result? I can log into via a terminal mode SSH session, but If I remote in graphically the Ubuntu-Desktop sign-in does not recognize those same credentials. Only one user (other than root.) Password was never changed. And why is there an Ubuntu-Desktop sign-in and not an Enlightenment sign-in? Changing pw does not help.

Incident II. Choose US English (or the equivalent) in response to all four locality and keyboard questions during a fresh install of Ubuntu 17 server full. The result? My US market laptop now behaves as if the Y-key is a Z and vice-versa. Keyboard behaves in Windows though.

Incident III. Fresh install of 17.04 server full. First and only package I install is Samba. It won't install. Many errors, largely centered on iSCSI not starting. I'm trying to migrate from a Window's centric world to Linux. Samba is an essential bridge between those worlds. I have not always nuked the hard disk partitions between reinstalls. (But how could that cause a keyboard layout issue concerning a language I have never selected in my life?)

Context. All installs were to the same physical server (I only have access to one) and done to bare metal. Each incident involved re-downloading the install image. In some cases a, different mirror was used. No install survived more than 24 hours.

Are these three unrelated events? Or is there a common thread? Is there a possibility these are hardware issues? They don't look like hardware issues to me.

Am I mistaken in my belief that nothing beyond disk structures (partitions, LVM, RAID, arraying) can survive a reinstall? The installer claims to be reformatting all volumes.

My credentials morph on me, I don't have control over what keyboard I am using, I can't read Windows shares, and I cannot install a working desktop. This is wholly unviable as an operating system. Several runs at Debian produced no anomalous results, but I decided I wanted access to LXD and I hear setting LXD up on another distro can be challenging. Not to mention no distro seems to have such depth of free support resources.

I would just start over a fourth time, but it strikes me maybe something is horribly wrong that I just don't see and I'm just banging my head pointlessly.

---

### Post by vasa1 on 2017-08-31
If you need support, please open separate threads per issue with descriptive thread titles in the appropriate support subforums.

---

### Post by gbambo on 2017-08-31
My concern is these are not unrelated. If I open three separate threads the odds of someone with insight seeing the common thread evaporates. I literally cannot afford to invest time in a 4th and 5th failed install. The delays I am experiencing in bringing this server online are causing me serious injury. I've lost over a week dealing with this nonsense. I have poured over forums and blogs and attempted dozens off work-arounds. 

Something atypical is afoot. I just want to know what it is.

---

### Post by ajgreeny on 2017-09-01
I would suggest that for a ubuntu-server which is being used in an work situation where stability is paramount, you should have installed the long-term-support (LTS) version, 16.04, not 17.04 which will have to be updated to 17.10 before the next LTS version, 18.04, is released.

As it is a server, you would normally not need a GUI desktop as all is done via command-line, but if that is not your way of doing things I suggest you do not use a minimum-install and then add the DE but install a low resource desktop version such as Lubuntu-16.04 or even Xubuntu-16.04 and then add the server packages needed; you will end with a faster GUI and probably a more familiar one if Windows is where you came from.

You also gave no indication of your hardware, only state that it does not look like a hardware issue to you, though as you are apparently new to Linux it is impossible for any of us to know that with certainty, so tell us more about that and we may be able to give you some more useful help.

---

### Post by gbambo on 2017-09-02
Hardware

[FONT=Calibri Light]i7-950 Bloomfiield quad hyperthreading 3.05ghz[/FONT]
[FONT=Calibri Light]2tb (1,836gb) Sata3 x 2 Enterprise-grade[/FONT]
[FONT=Calibri Light]     HGST HUS724020ALA640[/FONT]
[FONT=Calibri Light]48gb DDR3-1600 run @ 1066 in 3 ch mode[/FONT]
[FONT=Calibri Light]Mobo = MSI A7522IMT v8.14b8  110912 <- BIOS vers[/FONT]
[FONT=Calibri Light]     model = MSI X58 Pro (released 2009)[/FONT]
[FONT=Calibri Light]     no UEFI support
[/FONT]
[FONT=Calibri Light]1gbps Intel Pro/1000 GT

SERVER V DESKTOP

I used the server edition because my use will be 100% server cases. I heard Desktop and Server editions had differently compiled kernels and that running Desktop edition as a server would have poor performance. I want a desktop that I would load only as needed for those minority of cases where I become overwhelmed by CLI.

I TRIED 16.04 PER YOUR ADVICE

I am unable to load a desktop, despite following posted instructions (found elsewhere).

Here is my hand made log of my attempts:

[/FONT]**[FONT=Calibri Light][COLOR=#A600C4]Enlightmentment[/COLOR][/FONT]**
[COLOR=#A600C4][FONT=&quot] connect in terminal mode vie Teamviewer[/FONT][/COLOR]
[FONT=Calibri Light][COLOR=#A600C4]     starte19[/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#A600C4]          [COLOR=#FF0000]command not found[/COLOR][/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#A600C4]     /usr/bin/enlightenment_start &[/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#A600C4]     libcurl.so.5 missing[/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#A600C4]          [COLOR=#FF0000]install libcurl.so.5[/COLOR][/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#A600C4]          sudo [/COLOR][/FONT][FONT=Calibri Light][COLOR=#A600C4]apt-get update[/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#A600C4]         [/COLOR][/FONT] [FONT=Calibri Light][COLOR=#A600C4]sudo [/COLOR][/FONT] [FONT=Calibri Light][COLOR=#A600C4]apt-cache search ^libcurl[/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#A600C4]          [/COLOR][/FONT][FONT=Calibri Light][COLOR=#A600C4]sudo [/COLOR][/FONT] [FONT=Calibri Light][COLOR=#A600C4]apt-get install libcurl3[/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#A600C4]    [/COLOR][/FONT] [FONT=Calibri Light][COLOR=#A600C4]/usr/bin/enlightenment_start &[/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#A600C4]          [COLOR=#FF0000]Cannot initialize Encore_X[/COLOR][/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#A600C4]     startx[/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#A600C4]          [COLOR=#FF0000]X is not currently installed[/COLOR][/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#A600C4]     sudo apt install xiniit[/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#A600C4]     startx[/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#A600C4]          using sys config dir "/usr/share/X11//xorg..conf.d"[/COLOR][/FONT]
[FONT=Calibri Light]     [COLOR=#A600C4]/usr/bin/teamviewer &#8211;help[/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#A600C4]     Teamviewer[/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#A600C4]          [COLOR=#FF0000]make sure $Display is set correctly[/COLOR][/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#A600C4]          Launching GUI[/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#A600C4]                    TV not running on remote[/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#A600C4]         DISPLAY=light.uni.verse:0[/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#A600C4]          export DISPLAY[/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#A600C4]          xfig &[/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#A600C4]               [COLOR=#FF0000]not installed[/COLOR][/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#A600C4]          sudo apt install xfig[/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#A600C4]               [COLOR=#FF0000]can't open display light.uni.verse:0[/COLOR][/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#A600C4]          DISPLAY=:0[/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#A600C4]          export DISPLAY[/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#A600C4]           xfig &[/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#A600C4]     sudo startx[/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#A600C4]          [COLOR=#FF0000]could not get a file descrip to the console[/COLOR][/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#A600C4][COLOR=#FF0000]          Teamviewer not runinng, even aftr starting it man[/COLOR][/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#FF0000]     [COLOR=#A600C4]sudo reboot[/COLOR][/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#A600C4]          Timeout  locking authority file home/gregg/.Xauthority[/COLOR][/FONT]
[FONT=Calibri Light]           [COLOR=#A600C4]X server to begin accepting connections[/COLOR][/FONT]
[COLOR=#A600C4][FONT=Calibri Light]               [COLOR=#FF0000]no protocol specified[/COLOR][/FONT][/COLOR]
[FONT=Calibri Light]          [COLOR=#A600C4]startx[/COLOR][/FONT]
[COLOR=#A600C4][FONT=Calibri Light]          starte19[/FONT][/COLOR]
[COLOR=#A600C4][FONT=Calibri Light]               [COLOR=#FF0000]still connects in terminal mode only[/COLOR][/FONT][/COLOR]
[FONT=Calibri Light][COLOR=#FF0000][COLOR=#3665EE]          [COLOR=#A600C4]sudo reboot[/COLOR][/COLOR][/COLOR][/FONT]
[FONT=Calibri Light][COLOR=#FF0000][COLOR=#3665EE]          If [COLOR=#4DCE1D]you prefer to start Enlightenment manually[/COLOR][/COLOR][/COLOR][/FONT]
[COLOR=#4DCE1D][FONT=Calibri Light]        , add the following line to your ~/.xinitrc file:[/FONT][/COLOR]
[COLOR=#3665EE][FONT=Calibri Light]    [COLOR=#A600C4]nano ~/.xinitrc[/COLOR][/FONT][/COLOR]
[COLOR=#A600C4][FONT=Calibri Light]     ======[/FONT][/COLOR]
[COLOR=#A600C4][FONT=Calibri Light]     exec enlightenment_start[/FONT][/COLOR]
[COLOR=#A600C4][FONT=Calibri Light]     =====[/FONT][/COLOR]
[COLOR=#A600C4][FONT=Calibri Light]     After that Enlightenment can be launched by typing[/FONT][/COLOR]
[INDENT][COLOR=#A600C4][FONT=Calibri Light]     startx[/FONT][/COLOR][/INDENT]
[FONT=Calibri Light]


[/FONT]

---

### Post by cariboo on 2017-09-02
I'd really suggest you start with packages available in the repositories. 

I'd suggest installing openssh-server, then once at the prompt install the xfce desktop environment using this simple command:

```
sudo apt install xfce4
```

---

### Post by mastablasta on 2017-09-04
> **gbambo said:**
> Hardware
[FONT=Calibri Light]
I used the server edition because my use will be 100% server cases. I heard Desktop and Server editions had differently compiled kernels and that running Desktop edition as a server would have poor performance. I want a desktop that I would load only as needed for those minority of cases where I become overwhelmed by CLI.

[/FONT]

i wouldn't know about differently compiled kernels. i do not think there is any difference.

there is no need for a GUI for server tasks. there are plenty WebGUi available for those few times you might get overwhelmed. i suggest you look into Zentyal (Small business server) or Ajenti for Ubuntu. if you do not mind Debian then Openmediavault also offers a good WebGUI interface.

server is mostly configured via config files. this is where Ajenti shows as a good solution since you can just use their web editor to edit the files. once setup and running you mostly won't touch them.

aside from the mentioned desktops there are also simple windows managers (such as for example icewm). what they all need to load easilly is a desktop manager. usually lightDM is good choice but GDM is maybe more comprehensive. you then start the desktop manager to login to desktop.

anyway on the home server i installed Ajenti for administration via GUI and Owncloud (LAMP based). I never had a need for desktop since as mentioned config files can be changed via Ajenti. In the rare occasion i need to edit file eslewhere or need easier editing i would download the file via sFTP to windows and edit it there. it is also easier for me to move files arround (file management) via sFTP. this is very rarely needed though.

what specific tasks do you expect will be easier via GUI if all you will do is use it for server? Desktop is mostly filled with stuff user needs to  communicate with machine and web, bnot so much with services. and for exampel though there is a Samba GUI it seems easier and faster to just edit the config file.

---

### Post by bluemagoo on 2017-09-04
> **cariboo said:**
> I'd really suggest you start with packages available in the repositories. 

I'd suggest installing openssh-server, then once at the prompt install the xfce desktop environment using this simple command:

```
sudo apt install xfce4
```

interesting thread - I setup a 17.04 server edition in a VM.  After adding samba and opessh-server, I added xorg, configured it with Xorg - configure, moved the new conf file to /etc/X11/xorg.conf, then added the xfce4 packages.  From there I configured .xinitrc and added exec xfce4-session.  Really works!  Cool!

I would also suggest FreeBSD as a server instead;  really easy to follow the above steps, and setup xfce4, especially if you don't need a wireless connection

---

