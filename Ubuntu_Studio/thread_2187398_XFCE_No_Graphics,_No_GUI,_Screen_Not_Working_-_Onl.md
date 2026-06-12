---
title: "XFCE No Graphics, No GUI, Screen Not Working - Only Patterns"
date: 2013-11-11
forum: Ubuntu Studio
---

### Post by ARTwolf on 2013-11-11
XFCE No Graphics, No GUI, Screen Not Working - Only Patterns
 

 So I ran into a very peculiar graphics problem with XFCE today.
 I am running Ubuntu Studio 13.10 on a Sony Vaio VGN-FW laptop.
 I was trying to hookup an external monitor via VGA and had selected the &#8220;Use this output&#8221; option in the Settings Manager under &#8220;Display&#8221; menu option.
 The display worked and was mirroring across the laptop screen and external monitor well with the 1024x768 resolution. However I thought that it was too measly of a resolution and tried switching it to 1920x1080 (both displays support this). The screen then randomized into a very trippy and infinite pattern of bubbles with RGB dots (pic attached).
[ATTACH=CONFIG]247781[/ATTACH]


 I then rebooted the computer and got to the login screen with my user name and password prompt as usual, then selected the &#8220;Default&#8221; xfce session as I usually do and to my horror and amazement found that that pattern was all I could see.
 I tried a few things and crawled around on forums and came up with a solution and a conclusion to this GUI FUBAR.
 The answer lies in booting up to the login screen.
 Getting to the command line with CTRL-ALT-F2
 Logging in with your user name and password
 Then moving or deleting a file called displays.xml, it is located in ~/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml

 I chose to move the file in order to check out what was in it later

 Create a backup folder ```
mkdir ~/.config/xfce4/displays-backup
```

 Issue the command ```
mv ~/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml ~/.config/xfce4/displays-backup


``` Then reboot the computer with the command ```
sudo reboot


``` You should have your display and sanity back...

 

 NOTE: if this does not work, perhaps some other file got totally messed up in the xfce4 folder. In order to isolate it and get at least your GUI back instead of moving just the displays.xml file. Move the entire folder with this command ```
mv ~/.config/xfce4 ~/.config/xfce4-backup


``` 

 P.S. During this troubleshoot I learned that while CTRL-ALT-F2 gets you to a terminal screen, in order to get back to the GUI session CTRL-ALT-F7 is the answer :)
 

 May all your pixels stay responsive!

---

