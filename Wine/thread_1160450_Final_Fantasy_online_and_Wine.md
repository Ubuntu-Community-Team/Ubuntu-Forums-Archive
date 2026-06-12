---
title: "Final Fantasy online and Wine"
date: 2009-05-15
forum: Wine
---

### Post by Terrain on 2009-05-15
I am posting here as a last resort, hoping that someone else has had the same issue and can help me. I have found no help over on the Winehq website.

This supposedly runs at a Gold level, but I can't even get it to install, update and then launch properly. Here is a listing of the versions I have used:

8.10 32 bit + WINE 1.18-1.21
9.04 32 bit + WINE 1.18-1.21
9.04 64 bit + WINE 1.21

As you can see, I eventually lost heart and stopped testing all the allegedly working versions. Also please note that the 8.10 was a fresh installation and the 9.04 32 bit was an upgrade, and the 64 bit was a fresh installation. 

In between all the wine versions I removed via the package manager, issued the commands as documented in the WineWiki to remove the menu items, and deleted the virtual Windows installation directory. 

Now, here is what the problem is. I can install the program according to the instructions in the AppDB for this game. It installs without an issue using the Vana'Diel collection 2008 DVD. I am able to launch the program and run the PlayOnline viewer update. Upon completion of the update, the PlayOnline viewer needs to replace a couple files and it attempts to do so, which is when it throws an error that it was unable to replace the files (being the Pol.exe and I believe the unicows.dll). However, it does seem to have replaced them, as the timestamps are updated and the .tmp files are gone. 

So, the viewer does not restart itself, and I manually launch it again. This is when it crashes with a standard "this program has performed an illegal operation etc" type error, forgive me for not having the exact WINE verbiage. 

I have copied a dxdiagn.dll from my Windows XP pc to the system32 directory and added the override, as documented in the AppDB instructions, and I have tried it in both Vista and XP mode, but I am convinced that there must be something that isn't documented there that I am missing. 

My system is fairly basic, AMD64 processor, Nvidia 7200 with proprietary drivers (1.80), 2 GB RAM, it's nothing special. The graphics card seems to work well with WoW, so I don't think that is the problem. According to the folks over at WineHQ the Nvidia tends to work better than ATI so I think my problem has to be some sort of dependency that I am missing. 

Does anyone here have any advice, anything at all, on how I can get this working? 

Again I apologize for posting a question here that isn't quite Ubuntu-related, but the truth is that Ubuntu works great and I don't have any questions about it :p

Wine however, does not. At least not for this one application.

---

### Post by NightMKoder on 2009-05-15
> **neonide said:**
> I've never seen wine actually do any good at anything.  best to just scratch the idea completely and dual-boot into xp.  ANYONE who has a similar level of experience as me with wine would tell you the same thing.

I have plenty of good experience with wine. Especially the latest versions of wine are getting more and more stable. It really depends what you're blaming - if you have video issues they may be related to video drivers and not wine. Also - don't rant if you're not even going to try to help.

Back to the topic - 
The howto on appdb states to register dxdiagn and set it native BEFORE launching the update. It doesn't seem like you did that.

The "undocumented" thing you're missing is the fact that appdb howto's are expected to be used on a fresh wine prefix, so if you have WoW installed, try running the installation for FF in a separate prefix or just before WoW.

---

### Post by hikaricore on 2009-05-16
Best just to ignore trolls like this who can't say anything useful.
Sorry I can't offer more help aside from suggesting you ignore neonide.

---

### Post by Terrain on 2009-05-17
I actually did, I registered it using the following command as directed in the installation instructions (Did I forget to mention that I used the instructions on the appdb?) wine regsvr32 c:\\windows\\dxdiagn.dll

My copy of dxdiagn.dll came straight from my XP laptop, so I know it's a good file. That's not the problem, as I have tried registering it before, after, during, everything. It's something that isn't documented on the appdb because I have followed those instructions PRECISELY. 

As far as WoW working - WoW isn't an actual installation. I have the WoW folder on an external drive which I just copied over to the virtual C:\ on Wine. I am going to assume you may not be completely familiar with the way that WoW is coded - but once it's been "installed" once, you can take the entire World of Warcraft folder anywhere and play the game. They did that to retain compatibility, and I am glad that they did because it makes life easier.

Thanks for the input though. What I am looking for is a specific tweak that I may be missing, that isn't listed in the appdb.

---

### Post by Terrain on 2009-05-17
As a final note, whoever sent me the private message "dude you can get it to work it just needs some hacking" - that's the kind of response I am NOT looking for. 

I know that it needs some hacking, what I am looking for are instructions, documentation, illustrations, ANYTHING, that tells me HOW. 

This is exactly the kind of response that I got over on the WineHQ site - "It needs some hacking" "RTFM".... I read the manual and followed it precisely with multiple clean installations and multiple configurations, as I said. The hacks that it needs are not documented anywhere in any meaningful way.

So let me try to rephrase my initial question:

Does anyone have the program working, who had to use tweaks above and beyond what is in the "FM", and could you please tell me those tweaks? 

I would really appreciate it. I have been trying to get this to work for the better part of three weeks now.

---

### Post by nolliecrooked on 2009-05-17
> **Terrain said:**
> As a final note, whoever sent me the private message "dude you can get it to work it just needs some hacking" - that's the kind of response I am NOT looking for. 

I know that it needs some hacking, what I am looking for are instructions, documentation, illustrations, ANYTHING, that tells me HOW. 

This is exactly the kind of response that I got over on the WineHQ site - "It needs some hacking" "RTFM".... I read the manual and followed it precisely with multiple clean installations and multiple configurations, as I said. The hacks that it needs are not documented anywhere in any meaningful way.

So let me try to rephrase my initial question:

Does anyone have the program working, who had to use tweaks above and beyond what is in the "FM", and could you please tell me those tweaks? 

I would really appreciate it. I have been trying to get this to work for the better part of three weeks now.

lmao, I was gonna try and help ya, but not after that :p

---

### Post by NightMKoder on 2009-05-17
Hmm... This is an interesting problem.

So let me get this straight - you go through all the 5 installations, copy dxdiagn.dll from windows xp to wine's system32, regsvr32 it, add it as native, and then run the viewer, but it fails nonetheless, on copying a couple of files. And this is all on latest wine (1.1.21)

Can you post the terminal output from running the updater?

---

### Post by Terrain on 2009-05-18
> 
lmao, I was gonna try and help ya, but not after that

Actually, you seemed to just be trolling my inbox. I wasn't going to call attention to who it was but since you went through the additional trouble of posting here I might as wel give you some advice. 

Perhaps if you want to help someone, you shouldn't just send them a "dude urdoinitwrong". It just looks like trolling and nobody would take that as a serious offer of help.



[QUOTE=NightMKoder] 	
Re: Final Fantasy online and Wine
Hmm... This is an interesting problem.

So let me get this straight - you go through all the 5 installations, copy dxdiagn.dll from windows xp to wine's system32, regsvr32 it, add it as native, and then run the viewer, but it fails nonetheless, on copying a couple of files. And this is all on latest wine (1.1.21)

Can you post the terminal output from running the updater? [/QUOTE]

Close. I stopped going through all 5 installations after the first couple of failures because it was just wasting my time. I have only been installing the viewer and attempting to get that up and running, because if that runs, the expansions *should* run as well. Does that make sense? 

So here is what I a doing in a nutshell:

I install Wine using one of the Deb packages downloaded from the WINE repositories (Could this be my problem? I am not compiling anything from source, just assuming that the .deb will have everything I need for WINE to work). 

I then install the Playonline viewer using the terminal command wine install /path/to/my/cdrom/exe

It installs without throwing any errors.

So now, I copy my dxdiagn.dll from my xp laptop to a thumb drive (my laptop runs XP home, is there a notable difference between Pro and Home versions for this file?) and put a copy in the virtual installation /windows/system32

After this, I register the dll with Wine's regsvr32 command

Now, I open WINE's configuration utility and add Pol.exe and set it to run in Vista mode (note, I have also tried it in xp mode but that doesn't open at all). 

I have pol.exe highlighted and hop over to the libraries tab where I select the dxdiagn.dll file and set the override to native windows. 

I would also like to note that I have tried it with and without setting up a virtual desktop. It doesn't seem to make a difference other than with the virtual desktop, the program doesn't close until I close it. 

So after all of this, I then launch the pol.exe, and it looks good, and updates itself. It gets to the point where it wants to restart to apply the new files, and it chokes on replacing the files. After this, no matter what configuration I do, and believe me I have tried everything from registering the dll's in the POL directory to copying a new dxdiagn.dll to system32, it just will not launch. 

I actually ended up putting XP back on my desktop since I couldn't get this working. I'm going to set up a dual-boot environment and will try again, if I get same error I'll post that output. 

Thanks for looking at my issue, and thanks to those who tried to be helpful.

---

### Post by nolliecrooked on 2009-05-18
lmfao@trolling. Actually dude, I have set up FFXI successfully on a number of friends machines, and have come to learn a few tips and tricks that Wine wont tell you, but w/e, carry on with you trolling fantasies =)

---

