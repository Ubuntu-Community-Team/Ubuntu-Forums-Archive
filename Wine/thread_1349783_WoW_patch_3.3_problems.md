---
title: "WoW patch 3.3 problems"
date: 2009-12-08
forum: Wine
---

### Post by dardack on 2009-12-08
So I started with a fresh .wine and installed vcrun2005sp1, and when I load a toon it just sits at 100% load and never actually logs in so I can play.  Top says wow is at 2% cpu and sits at same memory after it hits 100%.  Ther eis no errors in the terminal.  I need help badly.

---

### Post by polpak on 2009-12-08
What sits at 100% exactly? Where in the process is it getting hung up? The servers are having some issues right now, so it may not be related to your client or wine install in any way.

---

### Post by zenben1126 on 2009-12-08
I am also having issues with the new 3.3.0 patch. For some reason i cannot log in to the game. The game starts up and everything is running fine, this being after i have the patch installed. I get a message as soon as i have put my information in and hit enter, saying:

<Heading> Microsoft Visual C++ Runtime Library

Runtime Error!

Program: C:\Program Files\World of Warcraft\Wow.exe

R6034

An application has made an attempt to load the C runtime library incorrectly.

<End of Message>


Anyone understand what this means, because I'm lost. I've tried re-installing the patch, and yet nothing changes. Is this a wine issue? Do I need to re-install wine? I'm going to pursue re-installing the game.

---

### Post by traemccombs on 2009-12-08
> **zenben1126 said:**
> I am also having issues with the new 3.3.0 patch. For some reason i cannot log in to the game. The game starts up and everything is running fine, this being after i have the patch installed. I get a message as soon as i have put my information in and hit enter, saying:

<Heading> Microsoft Visual C++ Runtime Library

Runtime Error!

Program: C:\Program Files\World of Warcraft\Wow.exe

R6034

An application has made an attempt to load the C runtime library incorrectly.

<End of Message>


Anyone understand what this means, because I'm lost. I've tried re-installing the patch, and yet nothing changes. Is this a wine issue? Do I need to re-install wine? I'm going to pursue re-installing the game.

THIS!  

I have the same exact thing.  I've checked on #Ubuntu but no love.  There really needs to be a #ubuntu-wow  lol

Please, any help will be greatly appreciated.

---

### Post by traemccombs on 2009-12-08
Ok, I tried (as someone on the wow.com forums suggested) and moved ~$USER/.wine/.../$WOWDIR/WTF dir to ~   then fired up wow again and I got the same error as before.  This doesn't fix things. 

:(

---

### Post by Presto123 on 2009-12-08
Here you go fellas. Did a quick Google search and found one specifically posted for this issue on Wine's forums:

[http://forum.winehq.org/viewtopic.php?p=36350&sid=77b1b532c5414e9db961c5143dab4196](http://forum.winehq.org/viewtopic.php?p=36350&sid=77b1b532c5414e9db961c5143dab4196)

Please try the quick download from Microsoft's site for the new C+ library as listed in the replies. Worked for me.

---

### Post by Presto123 on 2009-12-08
Actually, it would save us time if I just link the actual download here, lol.

[http://www.microsoft.com/downloads/en/confirmation.aspx?familyId=200b2fd9-ae1a-4a14-984d-389c36f85647&displayLang=en](http://www.microsoft.com/downloads/en/confirmation.aspx?familyId=200b2fd9-ae1a-4a14-984d-389c36f85647&displayLang=en)

---

### Post by traemccombs on 2009-12-08
> **Presto123 said:**
> Here you go fellas. Did a quick Google search and found one specifically posted for this issue on Wine's forums:

[http://forum.winehq.org/viewtopic.php?p=36350&sid=77b1b532c5414e9db961c5143dab4196](http://forum.winehq.org/viewtopic.php?p=36350&sid=77b1b532c5414e9db961c5143dab4196)

Please try the quick download from Microsoft's site for the new C+ library as listed in the replies. Worked for me.

YES!!!

Thanks tons mate.

3.3 here I come!

---

### Post by kidcharles on 2009-12-08
That microsoft download worked for me too. I just downloaded it and ran it with "$ wine vcredist_x86.exe" and I was able to log into WoW without problem. Thanks community for this very quick fix!

---

### Post by faeyin on 2009-12-08
For some reason I cannot install the run time libraries 

it gives me these errors

err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly

I'm running kubuntu 910 . any ideas of what i might try?

Edit:  im running a 64 bit operating system, if that helps

---

### Post by elliez on 2009-12-08
@ faeyin

i was having the same problem. creating a new prefix worked for me. there are instructions for how to do that over here:

[http://forum.winehq.org/viewtopic.php?p=36395#36395](http://forum.winehq.org/viewtopic.php?p=36395#36395)

the ITERATE_PublishAssembly error still came up during the install of vcredist_x86 but something worked as wow loads from there just fine.

good luck!

---

### Post by Gaddorm on 2009-12-08
When I try to install the 2005 runtime I get this error:

[IMG]http://img338.imageshack.us/img338/3228/screenshot2dn.png[/IMG]

Wine 1.1.34

Any ideas?

---

### Post by toupeiro on 2009-12-09
Attention x64-bit users.  Download this instead:

[http://www.microsoft.com/downloads/en/confirmation.aspx?familyId=eb4ebe2d-33c0-4a47-9dd4-b9a6d7bd44da&displayLang=en](http://www.microsoft.com/downloads/en/confirmation.aspx?familyId=eb4ebe2d-33c0-4a47-9dd4-b9a6d7bd44da&displayLang=en)

---

### Post by GJLenon on 2009-12-09
I've been trying to use winetricks to get the files, and it's plain not working.  I get "QueryServiceConfig2W Level 6 not implemented" errors.

Any ideas?

---

### Post by faeyin on 2009-12-09
What can I say?  That worked for me. Thanks so much  It took me a bit to figure out how to work with my custom paths,but once i did I was in.   I still have sound issues  but i think i can suss those. 

Your a genius !

> **elliez said:**
> @ faeyin

i was having the same problem. creating a new prefix worked for me. there are instructions for how to do that over here:

[http://forum.winehq.org/viewtopic.php?p=36395#36395](http://forum.winehq.org/viewtopic.php?p=36395#36395)

the ITERATE_PublishAssembly error still came up during the install of vcredist_x86 but something worked as wow loads from there just fine.

good luck!

---

### Post by zenben1126 on 2009-12-09
AWESOME! I'm going to try it later today after school >.< But thank you all for the help. I'll post up here again if I encounter any issues.

And just as a BTW, does anyone have issues playing WoW in fullscreen? Or how about this one: when using the launcher to start the game, it doesn't start the game, but instead locks the entire wow folder, and requires me to go in and manually reset the permissions. This happens every time i use the launcher, anyone have this issue?

---

### Post by Pikestaff on 2009-12-09
> **zenben1126 said:**
> Or how about this one: when using the launcher to start the game, it doesn't start the game, but instead locks the entire wow folder, and requires me to go in and manually reset the permissions. This happens every time i use the launcher, anyone have this issue?

The launcher is glitched.  Just change the desktop icon you're clicking on to say "WoW.exe" instead of "launcher.exe".

---

### Post by rob2nd9th on 2009-12-09
Ok thanks. Downloaded to desktop then right click with :-
"Open with "wine windows program loader"
And all worked fine :)

Thanks all....:D

---

### Post by rob2nd9th on 2009-12-09
Sorry? Got slow Internet and it took 5/6 hours to get this patch Could any one tell we what "File/s Folders to copy to my laptop to save doing it again?

Thanks.

---

### Post by ysaric on 2009-12-10
> **toupeiro said:**
> Attention x64-bit users.  Download this instead:

[http://www.microsoft.com/downloads/en/confirmation.aspx?familyId=eb4ebe2d-33c0-4a47-9dd4-b9a6d7bd44da&displayLang=en](http://www.microsoft.com/downloads/en/confirmation.aspx?familyId=eb4ebe2d-33c0-4a47-9dd4-b9a6d7bd44da&displayLang=en)

I used the instructions from here:

[http://ubuntuforums.org/showpost.php?p=8464546&postcount=2093](http://ubuntuforums.org/showpost.php?p=8464546&postcount=2093)

and they worked, it got rid of the error, but should I have used the above instead?  I'm confused!

I am using the 64-bit 9.10.  Thanks much for any info provided.

---

### Post by MrJason1234 on 2009-12-11
> **Presto123 said:**
> Here you go fellas. Did a quick Google search and found one specifically posted for this issue on Wine's forums:

[http://forum.winehq.org/viewtopic.php?p=36350&sid=77b1b532c5414e9db961c5143dab4196](http://forum.winehq.org/viewtopic.php?p=36350&sid=77b1b532c5414e9db961c5143dab4196)

Please try the quick download from Microsoft's site for the new C+ library as listed in the replies. Worked for me.
Worked for me. Thanks!

---

### Post by Z0014ND3l2 on 2009-12-11
What I did was uninstalling everything WINE related ./cry and basically re-installing it.

Also used it as a good reason to update WINE:

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

Then after WINE was installed I installed 

[http://www.microsoft.com/downloads/en/confirmation.aspx?familyId=eb4ebe2d-33c0-4a47-9dd4-b9a6d7bd44da&displayLang=en](http://www.microsoft.com/downloads/en/confirmation.aspx?familyId=eb4ebe2d-33c0-4a47-9dd4-b9a6d7bd44da&displayLang=en)

This time it installed without an error.

After all of that I re-installed WoW and Ventrilo. All Patches work and as stated before; just remember to change your shortcut to open with "Wow.exe" and not "Launcher.exe" as this will bring up the launcher and change your WoW Folder Permissions.

---

### Post by hikaricore on 2009-12-12
Sometimes it's easier to use wine prefixes instead of completely removing wine.

---

### Post by roh8880 on 2009-12-13
Okay, up untill recently my WoW has worked near flawlessly. That is, however, until this latest patch.
I got everything loaded and up to date and I can't even get to the login screen.

I saw on the wine website where someone used the following to fix it:
       > Code:
                   wine .wine/drive_c/Program\ Files/World\ of\ Warcraft/Wow.exe

 . . . . . . but that just further exasperated things for me. Now, WoW crashes everytime upon me even thinking of wanting to play!
My compy "zooms in" on the desktop and I have to restart it everytime just to get back where I was!

What in the sam hell happened?

I swear, for their own sick amusement, Blizzard comes out with these complicated patches just to watch us scatter around and panic trying to come up with a solution!

**FIXED**
Okay after a few hours of playing with it, I fixed my problem by deleting the patches and re-running the downloader, re-installing the patch and re-starting my system.

---

### Post by LastDanza on 2009-12-15
I've been able to run warcraft perfectly until patch 3.3. I've tried all of the fixes i could find in this thread and on other forums. winetricks hasnt worked, c++ library hasn't worked, and opening from wow.exe has not worked. Any ideas?

---

### Post by amenfex on 2010-04-11
> **LastDanza said:**
> I've been able to run warcraft perfectly until patch 3.3. I've tried all of the fixes i could find in this thread and on other forums. winetricks hasnt worked, c++ library hasn't worked, and opening from wow.exe has not worked. Any ideas?
Same issue as LastDanza

---

### Post by amenfex on 2010-04-11
Got this from the WoW forum. 

The sound is choppy, but thats another issue I guess i can tackle later on. 

I'm still downloading the patches, but if anyone has the same sound issue and resolves, please post here.

***FIXED*** 
<<Thank Fallhalen from the winehq forums for this fix, also, so you may help me, hehe, winehq has a forum with a great support community, so does ubuntu's forum community, assuming you don't listen to the first jerk to tell you to partion (yes, they said partion, I'm not making that up) and give the community time to work it out.>> don't partition and install holy exploder, I did this fix, it works. 

***FIXED*** 

Here is what I did: 

Step one, DO NOT DELETE ANYTHING!!!' 

Step two: Navigate to your World of Warcraft Directory (this will be different depending on your version of Windoze) Mine was found in: 

C:\Users\Public\Games\World of Warcraft 

Step Three: Edit the Microsoft.VC80.CRT.manifest file 

Step Four: Find the line that looks like this: 

<assemblyIdentity type="win32" name="Microsoft.VC80.CRT" version="8.0.50727.4053" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3b"></assemblyIdentity> 

Replace the version number to 8.0.50727.762 (it should look like this) 

<assemblyIdentity type="win32" name="Microsoft.VC80.CRT" version="8.0.50727.762" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3b"></assemblyIdentity> 

Step Five: Save the file (it is a good idea to first make a backup file before overwriting) 

All done. Your WoW should work perfectly. (You may also need to apply the aforementioned updates). But this worked for me.

---

