---
title: "MapleStory Private Server v0.62 ~ SUCCESS!"
date: 2010-01-21
forum: Wine
---

### Post by SmittyJensen on 2010-01-21
first, here are the results (arethusa said it was ok if his/her name was present:

[IMG]http://img687.imageshack.us/img687/4938/screenshotge.jpg[/IMG]



so, how do you do it? its really simple, first get the v0.62 game client and eternalms.exe (you can try other private servers, not sure if they work). you need these two dlls:

[http://www.dll-files.com/dllindex/dll-files.shtml?ws2help](http://www.dll-files.com/dllindex/dll-files.shtml?ws2help)
and
[http://www.dll-files.com/dllindex/dll-files.shtml?ws2_32](http://www.dll-files.com/dllindex/dll-files.shtml?ws2_32)

extract them both to your system32 in your wine prefix. should work now, just launch EternalMS.exe with wine. at least it works pretty good for me.

surprisingly simple, but took a long, long time to figure out but arethusa helped me a LOT. not sure if wine version matters but im using 1.1.36 from the ubuntu-wine ppa.

oh, and if this is against the rules go ahead and do whatever you need to do mods. really don't mind

---

### Post by AllRadioisDead on 2010-01-21
Are you kidding me? People have been trying to get this game running for year, and you download a couple of dll files and fix it?

---

### Post by SmittyJensen on 2010-01-21
> **ihermit said:**
> Are you kidding me? People have been trying to get this game running for year, and you download a couple of dll files and fix it?
i **** you not.


remember when i told you i couldnt get that patch working (i.e. no output)? well it was because maplestory was crashing, not sure why it didn't give any output but that guy on #wine told me how to debug, i did and he helped me out with the debug messages (3mb worth of debug messages :B). turns out some dll files were missing or incomplete or something, so i just replaced those dlls (1) and added another (1 more) and now it works.

yeah i know i've been trying to get it to work for years, too. all the wasted hours *kry*

i'd like to add that this is not for official maplestory (v.80), but private servers.

---

### Post by AllRadioisDead on 2010-01-21
> **SmittyJensen said:**
> i **** you not.


remember when i told you i couldnt get that patch working (i.e. no output)? well it was because maplestory was crashing, not sure why it didn't give any output but that guy on #wine told me how to debug, i did and he helped me out with the debug messages (3mb worth of debug messages :B). turns out some dll files were missing or incomplete or something, so i just replaced those dlls (1) and added another (1 more) and now it works.

yeah i know i've been trying to get it to work for years, too. all the wasted hours *kry*

i'd like to add that this is not for official maplestory (v.80), but private servers.
That's amazing, I'm happy to see you didn't give up.
A lot of people are going to be really happy, even if it's only private servers. Good work!

---

### Post by SmittyJensen on 2010-01-21
so has anyone else tried it? id like feedback, maybe its just me.

---

### Post by AllRadioisDead on 2010-01-21
I'd love to try it, but I upgraded to lucid, and I have a stupid ati card. I might downgrade over the weekend because I'm itching to try it out. I doubt the open source drivers will cut it, I can't get them working right now anyways. I'll have more time on the weekend, I will post feedback.

---

### Post by SmittyJensen on 2010-01-21
> **ihermit said:**
> I'd love to try it, but I upgraded to lucid, and I have a stupid ati card. I might downgrade over the weekend because I'm itching to try it out. I doubt the open source drivers will cut it, I can't get them working right now anyways. I'll have more time on the weekend, I will post feedback.
great.

just need one other person saying it works and ill be happy/satisfied.

---

### Post by SmittyJensen on 2010-01-21
also for the unexperienced user, you should make a wine prefix before testing so you dont mess up your current prefix. google it. afaik this replaces wine parts which should not be replaced, and could b0rk something.

played for 30mins yesterday with no crashes, just that weird text thing in the screenshot. but hey, it works nicely. very good fps as well.

im very excited over this, once again. i've been waiting for maple to work (better than vmware) for years now, it was the only thing holding me back from linux full time -- once again, for years. it makes me incredibly happy to see this happen.

also someone should make a winedb entry on this.

---

### Post by AllRadioisDead on 2010-01-21
This makes me want to get a nvidia card, so I don't have to deal with this ati garbage every upgrade.

---

### Post by SmittyJensen on 2010-01-22
> **ihermit said:**
> This makes me want to get a nvidia card, so I don't have to deal with this ati garbage every upgrade.
seems you and i are the only ones interested anyway. :popcorn:

---

### Post by AllRadioisDead on 2010-01-22
> **SmittyJensen said:**
> seems you and i are the only ones interested anyway. :popcorn:
I doubt that. I'm sure you'd gain interest if you posted on some pserver development sites, ie ragezone.

---

### Post by SmittyJensen on 2010-01-22
w00t

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2341](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2341)

im now a maintainer of the maplestory appdb

---

### Post by AllRadioisDead on 2010-01-22
Grats on getting the first gold rating in the wine database for maplestory!

---

### Post by AllRadioisDead on 2010-01-24
Hmm, I just tried. I installed wine 1.36, installed maple, set windows version to 2000, placed the two dll's in my system32 folder, and tried launching. It fails to execute with no errors. Am I missing anything?
I also tried setting those two libraries to native, didn't work either.

---

### Post by SmittyJensen on 2010-01-25
> **ihermit said:**
> Hmm, I just tried. I installed wine 1.36, installed maple, set windows version to 2000, placed the two dll's in my system32 folder, and tried launching. It fails to execute with no errors. Am I missing anything?
I also tried setting those two libraries to native, didn't work either.
 er, are you sure you're using a private server?
 
i didnt have to install maplestory, i just ran EternalMS.exe in wine. maybe thats the problem?

---

### Post by AllRadioisDead on 2010-01-25
> **SmittyJensen said:**
> er, are you sure you're using a private server?
 
i didnt have to install maplestory, i just ran EternalMS.exe in wine. maybe thats the problem?
The client needs to be placed in a Maplestory directory because it depends on the .wz files among other things. I'm trying with EcstasyMS v75.

---

### Post by SmittyJensen on 2010-01-26
> **ihermit said:**
> The client needs to be placed in a Maplestory directory because it depends on the .wz files among other things. I'm trying with EcstasyMS v75.
thats v75, ive only tested it with v62.

---

### Post by AllRadioisDead on 2010-01-26
> **SmittyJensen said:**
> thats v75, ive only tested it with v62.
I don't think it'll make a difference to be honest, but I'll install .62 and see if my luck changes.

---

### Post by SmittyJensen on 2010-01-27
> **ihermit said:**
> I don't think it'll make a difference to be honest, but I'll install .62 and see if my luck changes.
you HAVE to replace the dll. if it didn't ask you to replace a file when copying over the dll you did something wrong.

im assuming thats where you went wrong. you cant just copy + paste over the ws2_32.dll dll from dll-files.coms ws2_32.zip archive. you have to rename it so its lowercase then replace the one in ~/.wine (linux is case sensitive)

---

### Post by SmittyJensen on 2010-01-27
oh and also it has to be set to the win98 version.

i thought i remembered that it was win2000, but its actually win98.

---

### Post by SmittyJensen on 2010-01-27
fix it?

---

### Post by AllRadioisDead on 2010-01-28
The win98 thing might do the trick, unfortunately I'm too tired to bother right now so I'll post results in the morning. Thanks! 
Edit: No dice, it doesn't work. Trying to run BlizzardMS v62 with wine set to win98. Is there anything else you installed, because it's not spitting out anything, just crashing.

---

### Post by SmittyJensen on 2010-01-29
> **ihermit said:**
> The win98 thing might do the trick, unfortunately I'm too tired to bother right now so I'll post results in the morning. Thanks! 
Edit: No dice, it doesn't work. Trying to run BlizzardMS v62 with wine set to win98. Is there anything else you installed, because it's not spitting out anything, just crashing.
 Can you try specifically running EternalMS v62?
 
im not sure what the problem could be. i've even tested it on multiple reinstalls with the exact same steps and its worked fine for me (albeit with eternalms v62 only). tried it on linux mint & ubuntu.

---

### Post by AllRadioisDead on 2010-01-29
> **SmittyJensen said:**
> Can you try specifically running EternalMS v62?
 
im not sure what the problem could be. i've even tested it on multiple reinstalls with the exact same steps and its worked fine for me (albeit with eternalms v62 only). tried it on linux mint & ubuntu.
That wouldn't make a difference. The only difference in the clients is a hex string modified to connect to the private server instead of Nexon's server.

---

### Post by SmittyJensen on 2010-01-29
> **ihermit said:**
> That wouldn't make a difference. The only difference in the clients is a hex string modified to connect to the private server instead of Nexon's server.
thats the only thing i can think of. im not sure how this would vary from computer to computer (as its the running it portion, not any graphical glitches or what not).
 
anyway, i'm not going to be playing maplestory much anymore. i just bought lord of the rings online and its a lot funner than maplestory. i no longer get bored after 10 minutes, because i just got done playing lotro for 4 hours straight. :D
 
i wish i could've bought guild wars nightfall and played with handy (if possible, but the no monthly fees really encourages me to buy it), but too expensive for now. really looking at buying it though

---

### Post by sodra on 2010-01-30
XX33!
Finally! Someone found how to get on Maplestory on Ubuntu
even if it is a private server.

2 questions

1- Does this work with the Full download (MS and The Private Server client) on the EternalMS Website?

2-Do you have a link to The MS .62 client?

thanks

---

### Post by SmittyJensen on 2010-01-30
> **sodra said:**
> XX33!
Finally! Someone found how to get on Maplestory on Ubuntu
even if it is a private server.

2 questions

1- Does this work with the Full download (MS and The Private Server client) on the EternalMS Website?

2-Do you have a link to The MS .62 client?

thanks
yes. at least it did for me, 1 other has had different results (with a different client, of course).

i just downloaded the full client from the eternalms site and it worked.

---

### Post by AllRadioisDead on 2010-01-31
Oh well, at least you got it working. Have fun with LOTR.
I'm planning on getting a new Nvidia card soon and I'll be reinstalling Lucid, so I'll give it a go on my fresh install.

---

### Post by Alderas24 on 2010-02-01
I've tried everything and still can't get this to work =/

I downloaded the client straight from eternalms website and put it in my wine Program Files. At first it gave me a few errors in terminal saying that it needed some dll files, so i downloaded them and placed them in my sys32 folder. Now, nothing happens. No terminal error, no game launch. Nothing. Halp!

Edit: GOT IT TO WORK. Had to uninstall my wine completely. I had the beta release too if that helps. I uninstalled it totally (removed .wine folder in home) and installed the stable release NOT the beta. Put the .dll files in the sys.32 folder BEFORE anything. Then right clicked the EternalMS.exe and said run in wine. GG.

Thank you Smitty for your hard work :)

---

### Post by SmittyJensen on 2010-02-01
> **Alderas24 said:**
> I've tried everything and still can't get this to work =/

I downloaded the client straight from eternalms website and put it in my wine Program Files. At first it gave me a few errors in terminal saying that it needed some dll files, so i downloaded them and placed them in my sys32 folder. Now, nothing happens. No terminal error, no game launch. Nothing. Halp!

Edit: GOT IT TO WORK. Had to uninstall my wine completely. I had the beta release too if that helps. I uninstalled it totally (removed .wine folder in home) and installed the stable release NOT the beta. Put the .dll files in the sys.32 folder BEFORE anything. Then right clicked the EternalMS.exe and said run in wine. GG.

Thank you Smitty for your hard work :)
huh. could've sworn i used wine 1.1.36.

who knows, i do have bad memory. :D

---

### Post by AllRadioisDead on 2010-02-01
> **SmittyJensen said:**
> huh. could've sworn i used wine 1.1.36.

who knows, i do have bad memory. :D
Interesting, I'll give that a shot then. I just came home with my new Nvidia GTS 250 ^^.

---

### Post by Alderas24 on 2010-02-01
> **ihermit said:**
> Interesting, I'll give that a shot then. I just came home with my new Nvidia GTS 250 ^^.

Best of luck! :D

---

### Post by HKPlastik on 2010-02-08
If this works I will be so happy.
Unfortunately I am running Windows 7 atm, but im getting my linux on here again (dual boot at first) to see if this can work.

It's so sad how just ONE game can make you not wanna use another OS XD;

I just played Dragonica yesterday, loved it, if that would work I'd be happy as well, but if this thing with MS works, I'd give you so many hugs I think you'd die from lack of oxygen. XD

---

### Post by AllRadioisDead on 2010-02-09
> **HKPlastik said:**
> If this works I will be so happy.
Unfortunately I am running Windows 7 atm, but im getting my linux on here again (dual boot at first) to see if this can work.

It's so sad how just ONE game can make you not wanna use another OS XD;

I just played Dragonica yesterday, loved it, if that would work I'd be happy as well, but if this thing with MS works, I'd give you so many hugs I think you'd die from lack of oxygen. XD
Dragonica uses hackshield, it won't work.

---

### Post by reexe on 2010-02-26
i know it is a little old but for everyone else out there that want it to work, i got it working too :D
i am using wine 1.1.38
and you need to download 2 dlls, then dont forget to rename to lower chase!!
that was what i was doing wrong for 2 hours... -.-
put the dlls in /home/<your user name>/.wine/drive_c/windows/system32
(.wine is a hidden directory).
then i added the eternalms.exe in winecfg (wine config) and set it up so it uses win98 and window mode 800x600

i have tested v62 and v75, only v62 works i dont know if any other version might work but stick whit v62  till they update, then you cant try to find another version that works :)

if you want higher frame rate disable the audio driver in winecfg

i forgot, i installed 2 other things to, dont know if the game needs them, mscorefonts and gecko (wine asked to install gecko when i first started)

---

### Post by AllRadioisDead on 2010-02-26
> **reexe said:**
> i know it is a little old but for everyone else out there that want it to work, i got it working too :D
i am using wine 1.1.38
and you need to download 2 dlls, then dont forget to rename to lower chase!!
that was what i was doing wrong for 2 hours... -.-
put the dlls in /home/<your user name>/.wine/drive_c/windows/system32
(.wine is a hidden directory).
then i added the eternalms.exe in winecfg (wine config) and set it up so it uses win98 and window mode 800x600

i have tested v62 and v75, only v62 works i dont know if any other version might work but stick whit v62  till they update, then you cant try to find another version that works :)

if you want higher frame rate disable the audio driver in winecfg

i forgot, i installed 2 other things to, dont know if the game needs them, mscorefonts and gecko (wine asked to install gecko when i first started)
Meh, still can't get it.

---

### Post by MangoPie on 2010-09-19
Not working D:

---

### Post by marat569 on 2010-09-25
I run a maplestory private server, with no gameguard and all that, and i followed all your steps and i still get this error:
[img]http://img840.imageshack.us/img840/9890/screenshotkb.png[/img]

Help me out please =]
I think its because i need to put in a nvidia driver or library or something.

---

### Post by GoldenKevin on 2011-05-06
Hi guys. I know this thread is very old, but I got some helpful information that may assist any future visiters of this thread.

Note that for those who aren't familiar with the notation yet, a # (hash) in front of the command signifies that you need to execute the command under root, while $ (dollar sign) signifies you should run the command as a regular user. If you're logged in as a regular user, just prefix your commands with sudo to execute as root.

First off, make sure you installed Wine by entering in terminal:

# apt-get install wine

First some tips in order to get the actual program working. Make sure that for the two DLL files you download that they both are in all lowercase. My ws2_32.dll file name was in all caps, so I had to rename that to all lower case in order for the program to start (Linux is case sensitive unlike Windows). You will know if you did it right if both files overwrite previously existing ones.

Also, you have to run under Windows 98 compatibility as running under Windows XP just creates one of those "This program has encountered a serious error" messages. I think it's because ws2help.dll says it's for Windows 98, so maybe one that says for Windows NT will run fine under Windows XP compatibility.

I also have a tip about good practice. Since you're overwriting DLLs that come with Wine and since you have to switch the application compatibility to Windows 98, I suggest that you create a separate Wine prefix for your installation of MapleStory. This is really easy. In terminal we'll make a new folder in your home directory named .wine-maplestory (or whatever you wish to call it).

$ mkdir ~/.wine-maplestory

Then type

$ env WINEPREFIX=~/.wine-maplestory wine MSSetupv62.exe

Substituting MSSetupv62.exe with the path to your MapleStory installer.

This will first add the Wine files to a the .wine-maplestory directory in your home folder and then will start the MapleStory installer. The installation took a very long time for me, so be patient.

When that is done, change the compatibility of the Wine prefix to Win98. Type:

$ env WINEPREFIX=~/.wine-maplestory winecfg

And the Wine configuration for that specific Wine prefix will open. Under the Applications tab, and next to the Windows Version: label, select Windows 98 in the drop down menu and click OK. Extract those two DLLs you downloaded. Then copy them:

$ cp WS2_32.DLL ~/.wine-maplestory/drive_c/windows/system32/ws2_32.dll
$ cp ws2help.dll ~/.wine-maplestory/drive_c/windows/system32/ws2help.dll

Substituting WS2_32.DLL and ws2help.dll with the paths to the two files that you extracted from the downloaded ZIP files.

You can then launch the game using the command

$ env WINEPREFIX=~/.wine-maplestory wine C:\\Nexon\\MapleStory\\MapleStory.exe 

And substitute MapleStory.exe with the modified client exe that works with the server you wish to connect to.

I found several bugs so far, so it isn't perfect. First off, the sound is not synced (there is a few seconds delay) and the sound itself is very low-fidelity. It sounds tinny and a bit staticky. Also, it looks like that white text isn't rendered properly, and you'll find your name and password randomly changing between white and gray when you select or type anything in the login screen. The same thing applies to the chat box in game. I also found that sometimes, the keys will "stick" once I release a key, so I'll keep on moving in the direction of the key that I last held. It can be fixed just by tapping that key once you find that it is sticking.

For the record, I'm running under Natty Narwhal, with Wine 1.2.2.

EDIT: I fixed the audio quality issue by going to the winecfg of the Wine prefix, then to the Audio tab, and changing default sample rate from 44100 to 48000 under DirectSound. Doesn't fix the sync issues though. You probably also want to go to the Graphics tab and check "Emulate a virtual desktop" with 800x600 resolution to enable windowed mode. Wine isn't very pretty under fullscreen.

EDIT2: I tried my ws2_32.dll and ws2help.dll files from both my Windows XP and my Windows Vista installations. Looks like my hypothesis was wrong. My Windows XP dll works, but I still have to set compatibility to Windows 98 mode or otherwise the game still crashes. My Windows Vista dll just breaks Wine completely ('err:module:import_dll Library NSI.dll (which is needed by L"C:\\users\\root\\Temp\\...") not found') so it looks like your best bet will be those Windows 98 copies ([WS2_32.DLL]("http://www.dll-files.com/dllindex/dll-files.shtml?ws2_32") and [ws2help.dll]("http://www.dll-files.com/dllindex/dll-files.shtml?ws2help")).

---

### Post by Shaided on 2011-06-18
Anyone have any pointers for getting a v83 private server to work, trying to join one my friend is making.
~

---

### Post by GoldenKevin on 2012-03-26
Sorry for bumping this thread, but I was just so excited to find out that as of wine 1.3.28 on Ubuntu 11.10 (actually Linux Mint 12, but it's essentially the same thing), the wine developers have fixed the semi transparent chat text that is demonstrated by the screenshot posted by the OP! Now the chat box looks just as it should.

[[IMG]http://img31.imageshack.us/img31/6522/screenshotat20120326161.png[/IMG]](http://imageshack.us/photo/my-images/31/screenshotat20120326161.png/)

I changed my hardware a bit since I last posted (including my video card), but it looks like they also fixed the audio quality bug as well. My current audio sample rate is 44100 Hz, while in my last post, I said you had to set it to 48KHz to fix the low fidelity audio. Unfortunately, the audio delay is still present. The audio delay is the only remaining bug that I could find so far. The frame rate is still a bit choppier than what I would get in Windows, but I expected that. All in all, I think I would be happy to switch over to Linux as my server emulator development environment, considering I love developing on Eclipse in Linux Mint on any Java project that did not involve running Windows applications.

If you guys want to try out a v0.62 client on a private server, I listed what I did in a previous post I made, but I'll quote it right here:
> **GoldenKevin said:**
> Hi guys. I know this thread is very old, but I got some helpful information that may assist any future visiters of this thread.

Note that for those who aren't familiar with the notation yet, a # (hash) in front of the command signifies that you need to execute the command under root, while $ (dollar sign) signifies you should run the command as a regular user. If you're logged in as a regular user, just prefix your commands with sudo to execute as root.

First off, make sure you installed Wine by entering in terminal:

# apt-get install wine

First some tips in order to get the actual program working. Make sure that for the two DLL files you download that they both are in all lowercase. My ws2_32.dll file name was in all caps, so I had to rename that to all lower case in order for the program to start (Linux is case sensitive unlike Windows). You will know if you did it right if both files overwrite previously existing ones.

Also, you have to run under Windows 98 compatibility as running under Windows XP just creates one of those "This program has encountered a serious error" messages. I think it's because ws2help.dll says it's for Windows 98, so maybe one that says for Windows NT will run fine under Windows XP compatibility.

I also have a tip about good practice. Since you're overwriting DLLs that come with Wine and since you have to switch the application compatibility to Windows 98, I suggest that you create a separate Wine prefix for your installation of MapleStory. This is really easy. In terminal we'll make a new folder in your home directory named .wine-maplestory (or whatever you wish to call it).

$ mkdir ~/.wine-maplestory

Then type

$ env WINEPREFIX=~/.wine-maplestory wine MSSetupv62.exe

Substituting MSSetupv62.exe with the path to your MapleStory installer.

This will first add the Wine files to a the .wine-maplestory directory in your home folder and then will start the MapleStory installer. The installation took a very long time for me, so be patient.

When that is done, change the compatibility of the Wine prefix to Win98. Type:

$ env WINEPREFIX=~/.wine-maplestory winecfg

And the Wine configuration for that specific Wine prefix will open. Under the Applications tab, and next to the Windows Version: label, select Windows 98 in the drop down menu and click OK. Extract those two DLLs you downloaded. Then copy them:

$ cp WS2_32.DLL ~/.wine-maplestory/drive_c/windows/system32/ws2_32.dll
$ cp ws2help.dll ~/.wine-maplestory/drive_c/windows/system32/ws2help.dll

Substituting WS2_32.DLL and ws2help.dll with the paths to the two files that you extracted from the downloaded ZIP files.

You can then launch the game using the command

$ env WINEPREFIX=~/.wine-maplestory wine C:\\Nexon\\MapleStory\\MapleStory.exe 

And substitute MapleStory.exe with the modified client exe that works with the server you wish to connect to.

I found several bugs so far, so it isn't perfect. First off, the sound is not synced (there is a few seconds delay) and the sound itself is very low-fidelity. It sounds tinny and a bit staticky. Also, it looks like that white text isn't rendered properly, and you'll find your name and password randomly changing between white and gray when you select or type anything in the login screen. The same thing applies to the chat box in game. I also found that sometimes, the keys will "stick" once I release a key, so I'll keep on moving in the direction of the key that I last held. It can be fixed just by tapping that key once you find that it is sticking.

For the record, I'm running under Natty Narwhal, with Wine 1.2.2.

EDIT: I fixed the audio quality issue by going to the winecfg of the Wine prefix, then to the Audio tab, and changing default sample rate from 44100 to 48000 under DirectSound. Doesn't fix the sync issues though. You probably also want to go to the Graphics tab and check "Emulate a virtual desktop" with 800x600 resolution to enable windowed mode. Wine isn't very pretty under fullscreen.

EDIT2: I tried my ws2_32.dll and ws2help.dll files from both my Windows XP and my Windows Vista installations. Looks like my hypothesis was wrong. My Windows XP dll works, but I still have to set compatibility to Windows 98 mode or otherwise the game still crashes. My Windows Vista dll just breaks Wine completely ('err:module:import_dll Library NSI.dll (which is needed by L"C:\\users\\root\\Temp\\...") not found') so it looks like your best bet will be those Windows 98 copies ([WS2_32.DLL]("http://www.dll-files.com/dllindex/dll-files.shtml?ws2_32") and [ws2help.dll]("http://www.dll-files.com/dllindex/dll-files.shtml?ws2help")).

EDIT: Apparently you also cannot hold ALT to jump and CTRL to attack. Just minor annoyances.

EDIT2: Amazingly enough, [this post]("http://ubuntuforums.org/showpost.php?p=3322003&postcount=6") from 2007 fixed the issue for me:
> **ph0nph0n said:**
> After some testing, it turned out that setting the driver emulation to on on the audio tab of the wine config (run winecfg in a terminal, or click on the link in your applications menu) greatly decreased the sound delay.
In other words, simply running
$ env WINEPREFIX=~/.wine-maplestory winecfg
then going to the Audio tab, and setting Hardware Acceleration to Emulation completely fixes my audio delay.

---

### Post by donhas on 2012-04-14
Im downloading it now as we speak

---

