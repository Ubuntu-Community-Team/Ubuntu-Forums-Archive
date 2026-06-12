---
title: "Wine won't save a game - always have to reinstall it"
date: 2011-02-02
forum: Wine
---

### Post by suzy223 on 2011-02-02
***Changed the title because I found out that it does save***

Hi, all. I've managed to open a PSP Japanese visual novel with Wine and sound/all the controls work properly. The only thing is that the Japanese text is all jumbled up into weird blank squares and stuff. Whenever I start it up, I get ????? errors and the .dat opening sequence for the game doesn't load--it skips right to the menu. On Mac OS X 10.6, I managed to convert the game into an application but after 1-5 minutes of play I encounter a "Serious problem encountered" message and I'm forced to shut it down. Therefore, I can only play it on Ubuntu. xD

Am I doing something wrong? Is there a way to fix the font for this game or insert a Japanese font for it in Wine? Why aren't the .dat files opening in the game (they are movie files, the opening and ending sequences for the game... they open with video players fine).

How do I install a Japanese font for Wine? Does it have to be done  through winetricks? Also, why won't the .dat files (the opening and  ending) for the game open when I start playing it? It gives me a ????  error. D: Also, why can't I minimize the game? I only get an 'x' to the  top right and nothing else. Is there any way to stop the game from  freezing up and crashing after I take a screenshot? Sorry for all the  questions.

I'm a Ubuntu and Wine n00b and not very computer-savvy (idiot here), so please explain things in simple terms. D: I can provide screenshots, but the error messages from the game only show ????? marks and nothing else.

-The game was originally a .iso file but when I mounted it I got 'setup.exe' and '[the game's name].exe'. I used the latter and it opened fine. All the other IMG/BIN/DAT files or the files needed for the game to work are mounted on floppy0.

---

### Post by cogadh on 2011-02-02
Use winetricks and try the "fakejapanese" setting. I believe it requires you to already have Japanese fonts installed in Ubuntu.

As for the .dat files, run the app from the terminal to get Wine's error output, it might explain what is going on.
```
cd /path/to/app/directory
wine app.exe
```
Obviously replace the path and "app.exe" with the correct info for this application.

---

### Post by suzy223 on 2011-02-02
^Umm... I'm not sure about the first part, but this is what I get after I type in 'wine [app].exe':

Error in file "/home/user/.local/share/applications/wine-extension-?r?????????????r?????`?????@?r???????????`Save-asgard.desktop": "application/x-wine-extension-?r?????????????r?????`?????@?r???????????`Save-asgard" is an invalid MIME type ("application/x-wine-extension-?r?????????????r?????`?????@?r???????????`Save-asgard" contains an invalid character in the subtype)

Hopefully winetricks will install the fonts without giving me any errors on Ubuntu, unlike my Mac. I'm downloading a bunch of Japanese fonts from Synaptic Package Manager right now. ^^ Thanks for replying!

---

### Post by cogadh on 2011-02-02
Looks like you ran the wrong thing, or at least did not run the executable for the game. You need to change directories to where the game is installed, then "wine" the executable. If you installed it normally, the game would usually be found somewhere in /home/<your username>/.wine/drive_c/Program Files.

The info we want will be the error output that appears in the terminal after you "wine" the executable. It should contain a lot of messages that start with "fixme", which can be mostly ignored. We really care about anything that starts with "err".

---

### Post by suzy223 on 2011-02-03
^I'm getting really confused now. DD: I have the game in my '.wine' folder in my username but I don't open it from there. In my applications menu, I have a little subsection called 'Other' and the game is over there too. Though I don't get the proper green square icon of the game like I'm supposed to.

Anyway, could you please show me how to use winetricks and the "fakejapanese" setting on Ubuntu? I know next to nothing about the terminal and whenever I use it I end up failing...

---

### Post by cogadh on 2011-02-03
The link in the Applications menu is just a shortcut, not the game executable itself. You need to run the game executable directly, not the shortcut:

[LIST=1]
[*]Open a terminal. Applications >  Accessories > Terminal
[*]Change directories to the game's install directory: ```
cd ~/.wine/drive_c/Program\ Files/asgard/Starry\ Sky\ in\ Summer
```Note the "\" before all the spaces in the file names, like between "Program" and "Files", they are required (the terminal can't "see" the space in the file names otherwise). The odd characters in the "Starry Sky" part might be a problem to type. If you simply type "Starry" and then hit the TAB key, it should autocomplete the directory name for you
[*]Run the game's executable: ```
wine <appname>.exe
``` You will have to figure out what the actual name for the .exe file is. Since I don't have the game and your screenshot did not include the actual files within the "Starry" directory, I can't give you the specifics.
[*]A ton of output should appear in the terminal. Copy that output and post it here. Click on the Edit button in the terminal, Select All, then Copy. Use the [forum CODE tags]("http://ubuntuforums.org/misc.php?do=bbcode") when you post it, it will keep the output readable
[/LIST]

Okay, now for winetricks. I've never actually done the whole additional language font thing, so I don't know if this will actually fix your problem, but this is how you should do it:
[LIST=1]
[*]First make sure you have a Japanese font installed. The winetricks info on WineHQ specifically mentions the "Takao fonts". There are four of them listed in the Ubuntu Software Center (Application > Ubuntu Software Center, search "Takao"), you should probably install all four.
[*]Open a terminal. Applications >  Accessories > Terminal
[*]You should already have winetricks installed (it is automatically installed with Wine), so all you need to do now is run it from the terminal to "install" the fakejapanese fonts setting:
 ```
sh winetricks fakejapanese
```
[/LIST]
That's it. Post back with any results you get (good or bad) and we'll go from there.

---

### Post by suzy223 on 2011-02-03
The first part of your post:
```
user@user:~/.wine/drive_c/Program Files/asgard/Starry&#8482;Sky`in Summer`$ wine starrysky_summer.exe
fixme:imm:ImmGetOpenStatus (0x139078): semi-stub
fixme:imm:ImmReleaseContext (0x10058, 0x139078): stub
err:winediag:X11DRV_WineGL_InitOpenglInfo The Mesa OpenGL driver is using software rendering, most likely your OpenGL drivers haven't been installed correctly
fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 4 and card vendor 0000.
fixme:win:EnumDisplayDevicesW ((null),0,0x32f380,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1bebc0,0x1beae0): stub
fixme:amstream:IAMMultiMediaStreamImpl_AddMediaStream (0x3a03380/0x3a03380)->(0x13b960,{a35ff56a-9fda-11d0-8fdf-00c04fd9189d},0,(nil)) partial stub!
fixme:amstream:IAMMultiMediaStreamImpl_AddMediaStream (0x3a03380/0x3a03380)->((nil),{a35ff56b-9fda-11d0-8fdf-00c04fd9189d},1,(nil)) partial stub!
```ETA: NVM, I got winetricks. :D Now I'm trying that code... and I have fakejapanese installed! Yay.

---

### Post by cogadh on 2011-02-03
What Nvidia packages did you install? It sounds like you broke your graphics driver in some way.

---

### Post by suzy223 on 2011-02-03
^Oh no, I fixed it. It opens up the same again, with the annoying .DAT error message. I just had to switch to the recommended Nvidia driver...

---

### Post by cogadh on 2011-02-03
There is a reference to "amstream" in the original errors you got, which is probably related (amstream.dll is connected to DirectShow filters used to display video). Try using winetricks to install a native DirectShow filter runtime, quartz.dll (terminal command: sh winetricks quartz).

---

### Post by suzy223 on 2011-02-03
^Okay, I installed it... but I get the same pop-up error when I open the game. D: Is it because direct rendering isn't enabled? I don't even know how to enable it, lol.
```
fixme:imm:ImmGetOpenStatus (0x13af78): semi-stub
fixme:imm:ImmReleaseContext (0x10058, 0x13af78): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32f380,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:amstream:IAMMultiMediaStreamImpl_AddMediaStream (0x210ffc8/0x210ffc8)->(0x137f60,{a35ff56a-9fda-11d0-8fdf-00c04fd9189d},0,(nil)) partial stub!
fixme:amstream:IAMMultiMediaStreamImpl_AddMediaStream (0x210ffc8/0x210ffc8)->((nil),{a35ff56b-9fda-11d0-8fdf-00c04fd9189d},1,(nil)) partial stub!
```P.S. How do I apply the Japanese fonts to the game? I don't know the command. :(

---

### Post by cogadh on 2011-02-03
Wait, open a terminal and run this:
```
glxinfo | grep direct
```
If it comes back saying "Direct Rendering: Yes", then direct rendering is enabled, if it comes back saying "no", then you video card drivers are not properly installed and you need to reinstall them.

As for the fonts thing, I honestly have no idea. I figured the "fakejapanese" thing would have already taken care of that.

---

### Post by suzy223 on 2011-02-03
^Thanks. And it is enabled. Now, how to go about the fonts problem...

I guess I'll play the game with the errors then. I'm just happy that it has sound and everything. Thank you for your help!

ETA: alright, so I got the Japanese fonts to show by using LANG=ja_JP.UTF-8, but the game won't open. I get an error message. The game only opens when I don't use that command (then it becomes blocks and random letters again).

---

### Post by suzy223 on 2011-02-03
Woot! I got the Japanese fonts to work! =DDD Strangely enough, the game is even faster now. o.0

Had to re-install the game, but it's so worth it. Everything's working great. Thank you, cogadh! I would have given up if not for your prompt replies. xD

As for the .dat files, from what I've heard from Hongfire it's normal for some games to have errors opening them in Linux. I don't mind it now. Hmm... just how do I get that green icon for it on my desktop..?

---

