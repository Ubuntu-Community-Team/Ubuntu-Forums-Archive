---
title: "Executable Bit"
date: 2010-03-28
forum: Security
---

### Post by stepstools on 2010-03-28
I recently downloaded and installed 10.04 Beta 1, and when I am trying to install a program from CD, a security bit thing pops up, and blocks the .exe file.  When I try to make it executable from the permissions menu, it says I can't because it is read only.  Any ideas on how to disable it?

---

### Post by krull677 on 2010-03-28
i too have this problem. can not edit permission because file is read only. it worked pretty well with  older versions. copying the files to a folder and changing them there is not an option. any way of just disabling the whole executable bit thing?

---

### Post by OpSecShellshock on 2010-03-28
You can only change permissions of files where either you're listed as the owner (it's a tab on the properties) or you're a member of the group that owns it. You can go to where the folder with the file is, right click and "open in terminal" to start in that directory, and then change the permissions that way, I think. The file browser runs with regular user permissions, so if you try to do it graphically the options will be greyed out.

Windows executable files (those that have .exe) won't run just under a Linux desktop. You'd need to be running a virtual Windows machine or a Windows emulator in order for those files to run.

Additionally, you won't be able to change permissions for files on a CD because those files can't be altered on the fly. A CD that's non-rewritable or has been finalized can't be written to. That's probably where the read-only part comes from on those. That's the RO in CD-ROM.

---

### Post by krull677 on 2010-03-28
ok. i was using wine to run the exe which worked out fine in 9.10 but won't play ball in 10.04. i realise that cd rom are read only but how are you ever supposed to run the exe from the cd if the permission can never be changed? there must be a way of running it. i doesn't make sense to me. i'm reverting back to 9.10 anyway as i'm having a few more issues with this beta.

thanks for the reply

---

### Post by stepstools on 2010-03-28
I had no problem in 9.10 either.

---

### Post by adam814 on 2010-03-28
If you have wine installed you can make it work from the CD, you just need to run it using wine (i.e. in a terminal type "wine program.exe").  It may still gripe about it being read-only, but it should still run it.  I'm sure I've done this with Windows programs from CD.

---

### Post by cdenley on 2010-03-29
It looks like this was a change in nautilus. Apparently, it no longer opens files with wine unless they are executable.
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2010-January/010487.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2010-January/010487.html)
I agree with this change. Even windows executables should honor the security restrictions of the unix filesystem. Users with the windows mindset shouldn't be able to double-click install windows malware because they installed wine. You should be able to change the default mount options of CD's, though. I used to know how, but I don't think this setting is in gconf anymore.

---

### Post by amnite on 2010-03-29
Ok i figured it out when you the file you want to open. Right click and click open with other application, and select use custom command. The current command should say cautious-launcher. replace that with wine and you should be good, thats how i got my diablo to run... Lemme know if that works for you... Hehe Im kinda proud of myself, Kinda just stumbled upon it..

---

### Post by stepstools on 2010-03-29
It worked! Thanks!

---

### Post by bugritall on 2010-04-30
However, according to Wikepedia and purely in the best interests of clarity:> ...the word tw?t is more often  used in various other ways:
As a derogatory insult, a pejorative meaning a [fool]("http://en.wikipedia.org/wiki/Fool"),  synonymous with the word twit - 'You are a real tw?t and a half' (often  used in the UK)I think it's probably already clear that I'm British but that doesn't necessarily mean that I meant to call the Ubiban a bunch of fundamentalist twits. ;)

---

### Post by ken0069 on 2010-04-30
OK so did anyone figure out how to install a Windows program in Wine on Lucid?  I've got some software that I use with the Data Logger on my Race car that I want to run in Wine and I keep getting this same Executable Bit crap too?  

BTW, I also have Wine running on 9.10 and have had NO problems getting Windows apps to load on it??

Any help here?

Ken

---

### Post by ken0069 on 2010-04-30
I finally got that Windows based program to install in Wine.  That program name is Logworks3setup.exe and each time I tried to install it I got the infamous Executable bit block.  Then I changed the program name to Logwors3.exe and it ran fine?  Dunno what the word "setup" does to Wine or ubuntu but one of the two DO NOT like it.

Program installed now so I can see if it will actually work.

Ken

---

### Post by ken0069 on 2010-04-30
SCRAP THAT LAST POST!  LOGWORKS WILL NOT RUN AFTER IT INSTALLED??  The program tries to start, ie, blinks on then right back off again, like something is shutting it down as soon as it's acitvated.  It happens so fast I can't even see what is in the box that appears on the monitor.

So, I'm still needing some help with this problem.:-x

Ken

---

### Post by cdenley on 2010-04-30
Try reading the thread!

> **adam814 said:**
> If you have wine installed you can make it work from the CD, you just need to run it using wine (i.e. in a terminal type "wine program.exe").  It may still gripe about it being read-only, but it should still run it.  I'm sure I've done this with Windows programs from CD.

```

wine /path/to/file.exe

```

You shouldn't be able to double-click execute anything unless it is marked as being executable.

---

### Post by cdenley on 2010-04-30
> **ken0069 said:**
> SCRAP THAT LAST POST!  LOGWORKS WILL NOT RUN AFTER IT INSTALLED??  The program tries to start, ie, blinks on then right back off again, like something is shutting it down as soon as it's acitvated.  It happens so fast I can't even see what is in the box that appears on the monitor.

So, I'm still needing some help with this problem.:-x

Ken

Doesn't sound relevant to this thread.

---

### Post by ken0069 on 2010-04-30
> **cdenley said:**
> Doesn't sound relevant to this thread.

IMHO it IS relevant to this thread because it's an Eecutable Bit problem that I don't have with v9.10 on my other computer running this exact same software!  

The problem with the install of that Logworks program here on 10.04 just transferred to icon on the desktop after it finally did install.  And I sure hope I'm not going to have to open a terminal window to start it each time?:confused:

---

### Post by cdenley on 2010-04-30
> **ken0069 said:**
> SCRAP THAT LAST POST!  LOGWORKS WILL NOT RUN AFTER IT INSTALLED??  The program tries to start, ie, blinks on then right back off again, like something is shutting it down as soon as it's acitvated.  It happens so fast I can't even see what is in the box that appears on the monitor.

So, I'm still needing some help with this problem.:-x

Ken

It sounds like wine is executing to me, then fails to run your windows executable. How is this related to the executable bit? Sometimes newer versions of wine causes programs to break which worked in previous versions. If this were an executable bit problem, you would get an executable bit error.

---

### Post by bugritall on 2010-04-30
Aw, c'mon, cdenley! The executable bit's recent promotion is behind our problems and you know it! Please, *please* stop casting around for someone else to blame.

What we have here is a <snip> of monumental proportions and it doesn't help anyone if the culprits try to use smoke and mirrors to conceal their culpability. Why not just own up and try to put things right? That's the only real way to win friends and influence people in circumstances like these.

Remember when Intel tried to claim that their arithmetic bug didn't matter, when the tobacco industry said that smoking cigarettes was good for you, when Toyota said that runaway acceleration was something to do with carpeting? Well this is no different.

---

### Post by cdenley on 2010-04-30
> **bugritall said:**
> Aw, c'mon, cdenley! The executable bit's recent promotion is behind our problems and you know it! Please, *please* stop casting around for someone else to blame.

What we have here is a <snip> of monumental proportions and it doesn't help anyone if the culprits try to use smoke and mirrors to conceal their culpability. Why not just own up and try to put things right? That's the only real way to win friends and influence people in circumstances like these.

Remember when Intel tried to claim that their arithmetic bug didn't matter, when the tobacco industry said that smoking cigarettes was good for you, when Toyota said that runaway acceleration was something to do with carpeting? Well this is no different.

If you can't see that his current problem has nothing to do with the executable bit which is required by the launcher nautilus uses to open windows executables, then you obviously have nothing to contribute to this thread except for your overreactions to a long overdue change in ubuntu's default behavior. I think the only bad decision made was gnome (not ubuntu) no longer allowing users to configure the default mount options used for filesystems mounted with nautilus. If users understand they could execute files by double-clicking and the security implications that has, they should be able to make files on CD's executable. That certainly shouldn't be the default, though.

---

### Post by bugritall on 2010-04-30
cdenley, <snip> We seem to have another example of two nations separated by a common language but I'm ready to give it another go:

I identify your reference to a "long overdue change in ubuntu's default behavior" as a fundamental difference between us. It's clear that you welcome the change, whereas ken0069 and I do not.

Why should that be, I find me asking myself? Could it be anything to do with my (and ken0069's) sub-50 post-count, compared to your +3k posts, do you think? We are relative novices and we have a newly-created problem installing legitimate software in Ubuntu and we need help that seems not to be forthcoming.

For example, when you say> If users understand they could execute files by double-clicking and the  security implications that has, they should be able to make files on  CD's executable.it makes my blood boil. How, dammit? I have tried this and the avenues it opens but nothing works for me. What is a simple file execution strategy for you remains a file execution mystery to me and I'm pretty sure that I'm speaking for ken0069, as well.

Deal with that. Deal with it very simply, please, because Ken and I are in deep do-dos and we need help, not know-it-all obfuscation.

---

### Post by bugritall on 2010-04-30
C'm'on, cedenley. "There comes a time in the affairs of men which, taken at the flood, leads on..."

Just start your post with: "I have tried this..." and you could go on to achieve great things.

It's my birthday (honest it is) and it's 1:42 GMT and I'm very drunk but I don't care.

---

### Post by bugritall on 2010-05-01
In case I didn't make it clear earlier, I got the same result as ken0069, i.e. nothing, when I tried:> wine /media/Game_CD/MENU.EXE

---

### Post by OpSecShellshock on 2010-05-01
> **bugritall said:**
> In case I didn't make it clear earlier, I got the same result as ken0069, i.e. nothing, when I tried:
I wouldn't discount the possibility of a permissions issue here. From what I've seen, the CD/DVD-ROM drives tend to be owned by root, whereas Wine (unless run as an administrator--which is reckless) will run as a regular user. Execute access would thus not be authorized even if everything is otherwise set up correctly. You can experiment with this by pulling your network cable or disconnecting any wireless connections (not directly related, just a precaution), starting Wine as an administrative action, seeing if it gets the results you're looking for, and then closing out of it. If it works, then you can make either some ownership or permission changes (carefully--also, I'm sorry but I don't know how best to do that). However, do not, do not, take the shortcut of just casually running Wine as an administrator every time you want to play the game (assuming it even works in the first place; can't say for sure, it just doesn't seem to have been tried yet).

---

### Post by cdenley on 2010-05-01
> **bugritall said:**
> 
Why should that be, I find me asking myself? Could it be anything to do with my (and ken0069's) sub-50 post-count, compared to your +3k posts, do you think? We are relative novices and we have a newly-created problem installing legitimate software in Ubuntu and we need help that seems not to be forthcoming.

I guess you can assume from my post count that I have a better understanding of ubuntu and security, so I guess that could explain our difference of opinion. The possible solutions to the executable bit "issue" have already been discussed.
> **bugritall said:**
> 
For example, when you sayit makes my blood boil. How, dammit?
You can't! Read more carefully before replying next time.

> **bugritall said:**
> In case I didn't make it clear earlier, I got the same result as ken0069, i.e. nothing, when I tried:
Then that has nothing to do with ubuntu's launcher which requires the executable bit!

---

### Post by camdy on 2010-05-02
hi guys i've just read this thread and i'm having the same issue but the its with eve-online.I'm using the 10.04 LTS by the way

ok i thought about what you said OpSecShellshock but that wont work as you only download the launcher which then downloads the client,besides i don't wont to go down the path as i have no idea what i'll be doing.

i have also right clicked and opened properties and selected the allow executing file as program in the permissions tab.now what i get is a new window saying eve online installer  unable to elevate,error 1

and its been awhile since i've used linux so please keep it simple


EDIT: would this problem still be a security program issue or a wine issue ? and for some weird reason i get the feeling i had a similar problem years ago

---

### Post by cdenley on 2010-05-02
> **camdy said:**
> hi guys i've just read this thread and i'm having the same issue but the its with eve-online.I'm using the 10.04 LTS by the way

ok i thought about what you said OpSecShellshock but that wont work as you only download the launcher which then downloads the client,besides i don't wont to go down the path as i have no idea what i'll be doing.

i have also right clicked and opened properties and selected the allow executing file as program in the permissions tab.now what i get is a new window saying eve online installer  unable to elevate,error 1

and its been awhile since i've used linux so please keep it simple


EDIT: would this problem still be a security program issue or a wine issue ? and for some weird reason i get the feeling i had a similar problem years ago

There are many applications that do not work with wine. Your problem is clearly unrelated to the executable bit, since you already set it, and don't receive an error about it. This thread is not for any and all wine problems. Wine hardly ever works completely out-of-the-box, even for a gold-rated one like Eve apparently. It looks like that application might be made to work with a few tweaks, though.
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2249](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2249)

---

### Post by camdy on 2010-05-02
just wanted to be sure,thanks cdenley :)

---

### Post by ken0069 on 2010-05-03
I see no one has offered anything that would fix this problem.  If I can't run Windows apps in Wine then I might as well just go back to using Windows all the time and just wipe this drive and use it for storage.  

See this is the kind of junk that is a complete turn off for us newbies.  I've been wrestling with this OS since day one and at some point it would be good for someone to write some software that didn't screw up things that worked in the past.  You fixed one problem I had with 9.10 and created this one at the same time.  Telling me I can't run a .exe file is NOT going to make me want to use this or any other OS.  If you lock the damn system down so tight I can't use it, then what good is it?  That was one of the many things that pissed me off about Vista too!

I was wanting to load Ubuntu Lucid on my laptop but If I can't run that data logger software in Wine then I can't do that.  And that's just one of three Windows based apps for my race car that need to run in Wine on that laptop.  

I'm going to give this problem a few more days to see if someone will offer a "fix" for it and if that doesn't happen then I'll just wipe the drive and go back to Windows all the time.  It's getting to a point where the few benefits of ubuntu aren't worth the hassle.

Ken

---

### Post by cariboo on 2010-05-03
It may be better to ask this question in the [Wine]("http://ubuntuforums.org/forumdisplay.php?f=313") sub-forum.

---

### Post by cdenley on 2010-05-03
> **ken0069 said:**
> I see no one has offered anything that would fix this problem.  If I can't run Windows apps in Wine then I might as well just go back to using Windows all the time and just wipe this drive and use it for storage.  

See this is the kind of junk that is a complete turn off for us newbies.  I've been wrestling with this OS since day one and at some point it would be good for someone to write some software that didn't screw up things that worked in the past.  You fixed one problem I had with 9.10 and created this one at the same time.  Telling me I can't run a .exe file is NOT going to make me want to use this or any other OS.  If you lock the damn system down so tight I can't use it, then what good is it?  That was one of the many things that pissed me off about Vista too!

I was wanting to load Ubuntu Lucid on my laptop but If I can't run that data logger software in Wine then I can't do that.  And that's just one of three Windows based apps for my race car that need to run in Wine on that laptop.  

I'm going to give this problem a few more days to see if someone will offer a "fix" for it and if that doesn't happen then I'll just wipe the drive and go back to Windows all the time.  It's getting to a point where the few benefits of ubuntu aren't worth the hassle.

Ken

The "problem" that this thread is about has been solved. You must either give it executable permissions (not possible if it is on a CD-ROM and mounted with nautilus), or execute it with wine directly instead of the launcher nautilus defaults to. READ THE THREAD! If that doesn't solve your problem, then it doesn't belong in this thread.

---

### Post by bugritall on 2010-05-08
> **cariboo907 said:**
> It may be better to ask this question in the [Wine]("http://ubuntuforums.org/forumdisplay.php?f=313") sub-forum.Why, when the problem is clearly related to Nautilus' refusal to do what it used to do?

---

### Post by bugritall on 2010-05-08
I can "wine /ext4_fs/file.exe" in Terminal but this is much less  convenient than it used to be when nautilus would cheerfully use wine as  the default app for any and all windoze.exe files.  (I can also "wine /ntfs/file.exe")

 I eventually got my game installed with "wine /media/Games_CD/install/install.exe" and, despite a host of installation errors, I can run the game from the Desktop link that the installer created. I wonder if this will help with ken0069's problems?

In short, I have been able to work around the problems caused by Lucid's new exe-bit restrictions apart from a dogged refusal to run Linux executables that reside on NTFS  partitions.

---

### Post by cdenley on 2010-05-08
> **bugritall said:**
> Why, when the problem is clearly related to Nautilus' refusal to do what it used to do?

Well, the thread was supposed to be about the launcher nautilus defaults to using a launcher which requires the executable bit. That belongs here. All problems discussed recently do not. For some reason, anyone who experiences a problem with wine (there are many) somehow think it is related to this launcher even if they're not using it! If you don't want nautilus to use the cautious launcher:
```

sudo ln -s /usr/bin/wine /usr/local/bin/cautious-launcher

```
One command and your system is as unsafe as it used to be.

---

### Post by bugritall on 2010-05-08
At last we have an answer to the question that was implicit in the thread's first post and made perfectly explicit in the thread's second post. Thank you, cdenley.

---

### Post by Jonners59 on 2010-05-09
> **amnite said:**
> Ok i figured it out when you the file you want to open. Right click and click open with other application, and select use custom command. The current command should say cautious-launcher. replace that with wine and you should be good, thats how i got my diablo to run... Lemme know if that works for you... Hehe Im kinda proud of myself, Kinda just stumbled upon it..

Thanks for this, it almost works....  Could load MS Office 07 in WINE, but not CrossOver.  It's a kinda patch/solution.  I personally think Ubuntu have gone backwards and copied, knowingly or otherwise the failed Microsoft Vista approach to OS security.  Even MS have now admitted it was a big mistake, making the system unusable to all but the geeks, and certainly very complex and clunky for everyday use, hence MS Vista has ALREADY been withdrawn.

---

### Post by Jonners59 on 2010-05-09
> **cdenley said:**
> Well, the thread was supposed to be about the launcher nautilus defaults to using a launcher which requires the executable bit. That belongs here. All problems discussed recently do not. For some reason, anyone who experiences a problem with wine (there are many) somehow think it is related to this launcher even if they're not using it! If you don't want nautilus to use the cautious launcher:
```

sudo ln -s /usr/bin/wine /usr/local/bin/cautious-launcher

```One command and your system is as unsafe as it used to be.

Thank god for that.  Was totally unusable as a working business or personal tool.  This is a poor idea from Ubuntu, and mimics MS Vista what was it's downfall.  It should be an option not forced.  Again - a geek - terminal command to fix

---

### Post by Jonners59 on 2010-05-09
> **OpSecShellshock said:**
> You can only change permissions of files where either you're listed as the owner (it's a tab on the properties) or you're a member of the group that owns it. You can go to where the folder with the file is, right click and "open in terminal" to start in that directory, and then change the permissions that way, I think. The file browser runs with regular user permissions, so if you try to do it graphically the options will be greyed out.

Windows executable files (those that have .exe) won't run just under a Linux desktop. You'd need to be running a virtual Windows machine or a Windows emulator in order for those files to run.

Additionally, you won't be able to change permissions for files on a CD because those files can't be altered on the fly. A CD that's non-rewritable or has been finalized can't be written to. That's probably where the read-only part comes from on those. That's the RO in CD-ROM.


Yes, I found this.  There are documents, folders and config files and the like that are now out of bounds to me, and I have no way of accessing or fixing them.  I really do NOT like this "THOUGHT POLICE" approach taken by the developers.  It's not healthy.  It's my machine if I want to screw it up let me.  Who else is going to be able to fix config files for me, if I have no access to them???

---

### Post by Jonners59 on 2010-05-09
> **ken0069 said:**
> I see no one has offered anything that would fix this problem.  If I can't run Windows apps in Wine then I might as well just go back to using Windows all the time and just wipe this drive and use it for storage.  

See this is the kind of junk that is a complete turn off for us newbies.  I've been wrestling with this OS since day one and at some point it would be good for someone to write some software that didn't screw up things that worked in the past.  You fixed one problem I had with 9.10 and created this one at the same time.  Telling me I can't run a .exe file is NOT going to make me want to use this or any other OS.  If you lock the damn system down so tight I can't use it, then what good is it?  That was one of the many things that pissed me off about Vista too!

I was wanting to load Ubuntu Lucid on my laptop but If I can't run that data logger software in Wine then I can't do that.  And that's just one of three Windows based apps for my race car that need to run in Wine on that laptop.  

I'm going to give this problem a few more days to see if someone will offer a "fix" for it and if that doesn't happen then I'll just wipe the drive and go back to Windows all the time.  It's getting to a point where the few benefits of ubuntu aren't worth the hassle.

Ken

Ken
I have been using Ubuntu for over a year now and I like it lots and agree with what the world of, is trying to do.  This is however an exception.  I am beginning to change my mind about Ubuntu, it is moving in to the MS mindset and I do not like it.  the point of the technology is to make everyone's lives easier, not work for the geeks.

MS makes money selling licenses.  It sells 5 year maintenance contracts to corps with a free upgrade included which is the carrot, so every 3 years you get a new one.  Vista was a filler because they didn't have a new OS the year it came out.  It failed because of all the security devices and constraints, even though they said it was great.  It has already been pulled along with an admittance of failure.  10.4 is Ubuntu's Vista.

Why does Ubuntu need to go down this path too.  It does NOT need to sell licenses, so why not just upgrade. 9.10 was great and easy to install, and allowed the user to be the controller of the system so they could make adult decisions, not withstanding that EVERYTHING to get the systems to work is now going backwards to the geeks rather than attracting us users who have better things to do with our lives than learn and run complex, 'easy to screw up your system' commands.

The proof is in the eating and the 1st time no fuss install success of c20% says it all.  I have been trying to install my 10.4 upgrade on two PCs for OVER 1 week now working from 7AM to 2 AM most days...

> **cdenley said:**
> I guess you can assume from my post count that I have a better understanding of ubuntu and security, so I guess that could explain our difference of opinion. The possible solutions to the executable bit "issue" have already been discussed.

Re quote - absolutely - this is techie talk - how about listening to your customers and to the needs of the users who are crying out in pain here.

How the hec are we to get people away form MS and now Google (and soon others) with a mindset like this????  Life is far too short for this if you have one.

Sorry guys, on my high horse!

---

### Post by cdenley on 2010-05-09
> **Jonners59 said:**
> Thank god for that.  Was totally unusable as a working business or personal tool.  This is a poor idea from Ubuntu, and mimics MS Vista what was it's downfall.  It should be an option not forced.  Again - a geek - terminal command to fix

The concept of requiring executable permissions in order for executable files to be executed has been around a long, long time. Long before Vista. Long before Ubuntu. It has always been a simple and effective security measure which has always been used in Ubuntu. Bypassing this measure with nautilus by default on a double-click for any executable files, especially windows executables, was always a bad idea.

---

### Post by cdenley on 2010-05-09
> **Jonners59 said:**
> Re quote - absolutely - this is techie talk - how about listening to your customers and to the needs of the users who are crying out in pain here.

Customers? My customers? What are you talking about? We have provided multiple solutions to restore nautilus to its previous unsafe default behavior. We have explained why this is a bad idea. I don't know what more you expect from your fellow ubuntu users on this forum.

---

### Post by bugritall on 2010-05-09
> **cdenley said:**
> I don't know what more you expect from your fellow ubuntu users on this forum.It would have been nice to have Post No 33 delivered in response to Post No 2.

---

### Post by cdenley on 2010-05-09
> **bugritall said:**
> It would have been nice to have Post No 33 delivered in response to Post No 2.

I didn't have lucid installed at the time, so I didn't know how exactly this was implemented in nautilus. Post #8 told you how to accomplish the same results, though.

---

### Post by bugritall on 2010-05-09
I remember trying amnite's solution from Post No 8 - right-click and choose wine in place of cautious-launcher for the "other application" custom command - but it didn't work for me. I attributed that to the fact that I was using Lucid, whereas amnite was using something from a month earlier.

I posted to that effect saying:
> Sorry, amnite but your fix doesn't work in Ubuntu 10.04 LTS. :(but my whole post got deleted because of some comments about Ubuntu's old guard in the final paragraph. I was only expressing sentiments similar to the ones that Jonners59 expressed later but I was a little more succinct. ;) :D

---

### Post by cdenley on 2010-05-09
> **bugritall said:**
> I remember trying amnite's solution from Post No 8 - right-click and choose wine in place of cautious-launcher for the "other application" custom command - but it didn't work for me. I attributed that to the fact that I was using Lucid, whereas amnite was using something from a month earlier.

I posted to that effect saying:
but my whole post got deleted because of some comments about Ubuntu's old guard in the final paragraph. I was only expressing sentiments similar to the ones that Jonners59 expressed later but I was a little more succinct. ;) :D

Telling nautilus to open it with wine using the custom command will in fact open it with wine, which bypasses the launcher which requires the executable bit. I just tested it and it worked fine. Of course, some people had other problems with wine, and for some reason assumed it had something to do with the executable bit, and complained it didn't solve their problem even though the executable bit error never appeared.

I also tested my solution, and it doesn't seem to work. I thought I tested it before. Anyway, this is probably a good compromise. A small change to lucid's wine launcher.
```

#!/bin/bash
# For use with .desktop files and MIME handlers so that the Ubuntu Policy
# can be followed: programs cannot be executed when they lack the execute bit.
# https://wiki.ubuntu.com/SecurityTeam/Policies#Execute-Permission%20Bit%20Required
exe="$1"
shift || true
if [ -n "$exe" ] && [ ! -x "$exe" ] && \
   [ "${exe:0:5}" != "/usr/" ] && [ "${exe:0:5}" != "/opt/" ]
then
    if [ -n "$DISPLAY" ] && [ -x /usr/bin/zenity ]; then
        /usr/bin/zenity **--question** --title "**Warning**: $*" --text "The file '$exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the <a href=\"https://wiki.ubuntu.com/Security/ExecutableBit\">executable bit</a>.** Would you like to execute it?**" **&& exec "$@" "$exe"**
    else
        echo "$*: '$exe' is not executable.  Aborting." >&2
    fi
    exit 1
fi
exec "$@" "$exe"

```

Create that script in /usr/local/bin/cautious-launcher, then make it executable. You will still get the same executable bit warning, but will be given the option to proceed. Nobody will unknowingly execute an executable with a double-click, but they can easily do so if they wish with only one additional click if they cannot or would rather not change the permissions of the file.

---

### Post by Jonners59 on 2010-05-09
I managed to take control of my PC and am now able to install apps that I want (trusted sources) by:

Following the instruction to load;
sudo ln -s /usr/bin/wine /usr/local/bin/cautious-launcher
I also went in to System - Administartion - Users and Groups.... after putting in authorization password...  Then select  Manage Groups - select root - Properties and then ensure your user account is selected....

I am sure this breaks all the rules, but until a simple user interface for us simpletons is provided so we can add the things we want without becoming rocket scientists, it'll have to make do for me.

Sorry to offend those that enjoy a different experience with their setup

---

### Post by macaus on 2010-05-25
As a recent convert from Windoze to Ubuntu I had high hopes but after 10.04LT was installed those hopes were dashed. It took a lot of guessing and checking but finally I can install .exe applications from CDROM. Using a previous post as a guide, sorry but I cannot remember your name to give you credit, I found that the easiest way is to run the application using the following method.

Right click the launch application, eg. setup.exe
Select "open with"
Select WineBrowser. I think the original post said select Wine but I was unable to get that to work.

PRESTO:P Finally I have BF1942 on my computer.

For all you others out there who provided all these scripts and system changes, etc. Not all of us are rocket scientists with Linux. While you all keep it in the land of magic and voodoo there will never be a mass exodus from Windoze. The fundamental principals of Linux are fantastic but please help us newbies with workable ideas and not have us trying to crawl under the bonnet all the time because a guru knows what is best. Remember we are spoilt by the M$ paradigm and expect similar functionality when we migrate over.

Live long and prosper dude........

---

### Post by Antonio Tavares on 2010-06-09
*An house with no doors is very safe, but no one can live inside.*

I've tested the last solution with the script and it worked very well (thank you to the author!). It is a good solution to the bug (or feature?!) Ubuntu willingly created. You can't change executable bits on CDROMS or any other read only media. Pretending that this obvious limitation is the fault of the user is completly foolish! Security has nothing to do with harrassing the user. Some users need guidance, others don't, but what nobody wants is not using a program for supposed security issues. When security features are too dificult to understand, people tend to disable them completly and turn off ALL the security instead of tuning it to a good balance between eficiency vs security. So let's keep it safe, but functional too.
For the beginners reading this thread (and we have to respect them):

To create the script you use the following command:
**gksudo gedit /usr/local/bin/cautious-launcher**
and paste the code on the above post and save.
Then you better make it executable (!) with the following:
**chmod +x cautious-launcher**

You do this on the command line using the terminal. This is no "geek" thing. It is a marvellous way of being able to use solutions the "geeks" create, because it is easier to explain "type this and that" than explaining where to point with a mouse, and it can be easier to configure a machine in cases like this.
Thank you geeks for your brilliant solutions, and thank you beginners for enfatizing the geeks brilliancy.:p
Cheers to all!

---

### Post by kneewax on 2010-06-15
> **Antonio Tavares said:**
> *An house with no doors is very safe, but no one can live inside.*

I've tested the last solution with the script and it worked very well (thank you to the author!). It is a good solution to the bug (or feature?!) Ubuntu willingly created. You can't change executable bits on CDROMS or any other read only media. Pretending that this obvious limitation is the fault of the user is completely foolish! Security has nothing to do with harassing the user. Some users need guidance, others don't, but what nobody wants is not using a program for supposed security issues. When security features are too difficult to understand, people tend to disable them completely and turn off ALL the security instead of tuning it to a good balance between efficiency vs security. So let's keep it safe, but functional too.



Well said! I've watched this thread with sadness as the rhetoric has been more divisive than I've seen in a long while on this forum.

Moreover while I understand the high-ideals behind the executable-bit policy, I see shades of the infamous UAC nag boxes Windoze users have had to put up with.  Since most Windoze Malware wouldn't run in Wine even if you wanted it to the protection 10.04 defaults too is over-kill and way too intrusive. On its own for local files it would just have been annoying, but the inability to allow users too *simply* run *.exe files from CD is a poor error of judgement on behalf of the developers.

Its all very well pointing people to the command line, but for non-techy users the CLI is intimidating and seems a very hard way of working for folk brought up on point and click.

Ultimately these issues effect the home users most detrimentally because security should be set by site policy in corporate or enterprise settings.

I really thing 10.04 is a massive step forward but this issue is going to keep coming back to haunt this version of Ubuntu.

Kneewax :confused:

---

### Post by Lolpanda on 2010-06-15
Guys, Problem solved. I know some people have posted alternate responses and fixes, such as editting the script, but this is just quick and dirty. 
 
Open up terminal and type:
 
```
 
*sudo add-apt-repository ppa:ubuntu-wine/ppa*
*sudo apt-get update && sudo apt-get dist-upgrade*

```
 
That should take care of all your 10.04 problems. The Wine Dev's got annoyed with Ubuntu new security policy, which seems to be the general idea (they dont like it) coming from the users (HINT HINT UBUNTU DEVS!) So in the latest wine releases they bypass the new "Cautious-launcher" for .exe's. 
 
By bypassing the new cautious-launcher script, this should also allow for CD's to work since its impossible to edit them. As far as I can tell this restores full Ubuntu 9.10 Karmic Koala and early behavior to .exe's and CD's under Ubuntu 10.04. You cannot however use the version of wine in the repo's, they do not have the ACTUAL Wine 1.2 Package, they only have an early-release beta of it since thats as far as it got before 10.04 got released. You need a true Wine 1.2. 
 
Downside to using the latest stuff is it may be a little buggy, that being said, I've had that PPA installed into my sources file since I installed 10.04 and havent had a single problem yet. 
 
 
A more drastic fix...delete the cautious-launcher script or alter it.
 
Its under 
 
```
/usr/bin/cautious-launcher
```
 
 
 
 
a note to Dev's: Either remove the new cautious-launcher script in Meerkat, or edit it to have a "Execute Anyway" Button in the script. Tradition is great, Unix Permissions are great. But you have a major flaw in the idea with CD's and other Non-rewritable media that cannot be editted to have the execution bit checked. When tradition gets in the way of practicality and usability..its time to start a new tradition.

---

### Post by movieman on 2010-06-16
> **Lolpanda said:**
> When tradition gets in the way of practicality and usability..its time to start a new tradition.

And when convenience gets in the way of security you get Windows.

Allowing people to execute files which don't have the execute permission set without having to jump through hoops is a very, very, very bad idea.

---

### Post by Lolpanda on 2010-06-17
We're not talking about allowing webpages to alter system files (thank you activex controls..) We're talking about allowing people to CHOOSE whether or not they want to have the same level of security that they have had, and has served them fine, for the last like 10 releases of Ubuntu. 

Besides, you will never convince me that not allowing people to install software they have spent money on from CD's, is in their best benefit to keep Ubuntu secure. 

Going even further... I thought Ubuntu claimed to want to be user friendly while still being secure?  This new security policy only allows for one of those to be true. Be secure and not allow .exe's to be run without jumping through hoops (including CD's) or to be user friendly and let the user choose whether or not to run a program. 

As a member above posted, "lands of magic and voodoo" thats fairly accurate. A year ago when I first learned about Linux, something like this would've sent me IMMEDIATELY back to windows Xp or Windows 7, reminding me of Vista but even worse, since there isn't even a 'execute anyway' button for that script. Even vista didn't block Software from CD's.



There is a middle-ground between too convient (early windows) and unusable in some cases (Vista, but again, I'd definitely call this worse) and it is a middle-ground that Ubuntu has walked since as far back as I remember. 


AND  on a side note: This is open-source software! This is LINUX! This is about the end user's choice. No one is forcing people to install the wine PPA, no one is forcing people to put up with the new script, what you or I think to be totally honest, in the end doesn't matter. Ubuntu gives us a base to work off of and edit as we see fit. If in Meerkat, they take away the script, I'll rejoice. You'll cry, and we'll agree to disagree but hopefully we'd stay out of eachother's face about it in the spirit of open source software and choice. 

You love the policy, I hate it, other members love it, other members hate it. The Ubuntu Dev's decided that the base they gave us, should have this script. Thats fine, I disagree, but they are the ones designing the OS. I'm just glad this isn't windows and there are work-arounds that don't compromise the entire security integrity of the OS (Like disabling UAC in vista)

---

### Post by OpSecShellshock on 2010-06-17
Users do, in fact, have the choice to make Windows executables run from read-only optical media. The instructions for doing so are a few pages back. It's just a non-default.

This to me is less a problem with Ubuntu the OS and more a problem with third-party software developers not providing native Linux support, releasing their software on read-only media, and making it difficult to simply store a copy locally on a user's machine that the user fully controls (especially when money has changed hands--how can a developer expect users to buy something but still not own it?).

Also, I'm still a bit baffled as to how this is a security problem.

---

### Post by youngmix on 2010-07-04
I solved the ExecutableBit for myself. In 10.04; just right click,  Properties, Permissions tab. Under the Permissions tab, there should be a  category titled, "Execute" with a check box next to it. Check the check  box to enable that particular .exe as a usable executable. It worked  for me. I didn't read pages 3 to 5 of posts, so I'm not sure if this  answer has been posted yet. But, this seems to answer the original  question posted.

---

### Post by cdenley on 2010-07-05
> **youngmix said:**
> I solved the ExecutableBit for myself. In 10.04; just right click,  Properties, Permissions tab. Under the Permissions tab, there should be a  category titled, "Execute" with a check box next to it. Check the check  box to enable that particular .exe as a usable executable. It worked  for me. I didn't read pages 3 to 5 of posts, so I'm not sure if this  answer has been posted yet. But, this seems to answer the original  question posted.

The original question was about files on a CD.

---

### Post by kneewax on 2010-07-05
> **youngmix said:**
> I solved the ExecutableBit for myself. In 10.04; just right click,  Properties, Permissions tab. Under the Permissions tab, there should be a  category titled, "Execute" with a check box next to it. Check the check  box to enable that particular .exe as a usable executable. It worked  for me. I didn't read pages 3 to 5 of posts, so I'm not sure if this  answer has been posted yet. But, this seems to answer the original  question posted.

It really didn't at all! :) The premise of the question was about files on CD which are read only and therefore the permissions are uneditable.

This is a big issue for the distro that has sold itself on being Linux for Humanbeings, i.e. Linux for non-geeks.  In my opinion this issue is a big mistake for Ubuntu.  This sort of draconian 'it's safer for you mere mortal user' attitude is a bit close to the reason many of us left the dog of Windoze in the first place.

---

### Post by movieman on 2010-07-05
> **kneewax said:**
> This is a big issue for the distro that has sold itself on being Linux for Humanbeings, i.e. Linux for non-geeks.

What fraction of Ubuntu users do you believe are trying to install Windows software from CDs by double-clicking?

Clearly it's a big issue for you, but I believe you'll find that security is far more important to the vast majority of Ubuntu users. If you want an insecure OS that lets you execute random files just by clicking on them then there's always Windows.

---

### Post by kneewax on 2010-07-05
> **movieman said:**
> 
Clearly it's a big issue for you, but I believe you'll find that security is far more important to the vast majority of Ubuntu users.

I agree we all want a secure system. However the system of trusted links that was developed for Karmic was good security - it warned users of the dangers of running a file, but did not go as far as to make the distinction on my behalf as to what is secure or not.  

The reason I question the executable bit policy is because I think it is over-kill in terms of security.

How many people are running Windows files within Wine without thought or care - the very process of setting up Wine means you are not just 'randomly clicking on files'

How much damage can a non-native file actually do to a Linux box? Most trojans or virus would be ineffective even if they ran - the vast majority of wine applications are restricted within their own bottle or the compatibility layer and have little bearing on the rest of the OS.

The job of an OS is not to *decide* on behalf of the users what they can and can't do with their systems. Sure if it is a corporate system then the Sysadmin rightly has that power, but in corporate systems these things would be decided at policy level not individual desktops.  

Yes, a good OS warns you of the dangers of something that has potentially hazardous consequences - but a home user should be able to click past warnings in-order to run things at their own risk once they have been made aware of the dangers.

Making Windoze CDs with .exe setup files un-installable is not the answer in a grown up OS.  Forcing people out to the CLI to avoid this issue gives Linux a bad name - most ordinary users don't want to be forced to command syntax for something they could do in the previous version in the GUI.

I think getting the right balance in security is tricky issue, and I can see why the developers thought this might be a good move, but it actually is counter-intuitive. 
 
I think you'll find the vast majority of users expect to be able to use CDs without finding themselves unable to run the contents.

Its not about what is good for me, I am a big boy and can with the help of these forums find my way around most issues, but about striking the right balance between security and usability. IMO this issue of executable bit is one that needs more thought to get it right.

---

### Post by LeadFingers on 2010-07-28
I'll admit I was pretty steamed when I tried several times to install Windows software from a CD and got the Executable bit error message, but got over my frustration when I realized the Wine dev's were ahead of the problem. 

You now have two ways of opening something with wine, the "wine program launcher" and the "wine browser". The wine browser bypasses the executable bit issue making it once again possible to launch an executable where the permissions can't be changed. Right click on the .exe, "Open With"/ "Winebrowser", no need to muck about with the permissions. 

Are the Ubuntu dev's plugging a possible security issue? You bet, but it's no small pain until you find the work-around. While I'm sure it's documented somewhere it's by no means intuitive.

---

### Post by jcottier on 2010-07-28
Its not just a wine or Nautilus issue, it goes deeper than that. If you put in a CD that contains an exe file, Ubuntu mounts this as /media/DISC_NAME (none executable) instead of /media/CDROM (executable). So it has a different path for each CD that has an exe file on it.

I wanted to use Ubuntu to share a CD drive for windows machines to access an install disc. But I had to spend a couple of hours googling to find out why it behaves like this. This security issue is not (obviously) configurable, but also apparently users are not made aware of what is going on. The only way I found to fix this is to manually umount the CD on the command line (also with the same unique path) IE sudo umount /media/DISC_NAME, make a new folder that does not bump into ubuntu's system one like /media/cdrom0 and then manually mount it with mount -t iso9660 /dev/scd0 /media/cdrom0/. Then you have a fixed path to share or access which allows exe files. But I found all this out quite a while after being forced to simply share (with a click click) on an XP machine :-(
Still at least the XP machine was a virtual one running inside ubuntu.

This is really pants. It should be clearly documented and easily configurable by an administrator.

---

### Post by Coburn on 2010-11-21
?

---

### Post by Coburn on 2010-11-21
Ouch!  I got a paper cut!

---

### Post by Jonners59 on 2010-11-23
I do not know if my problem is related to this, I have a seperate thread, which no one is responding too, but:
 
My wife has a pink Sony Viao laptop.  It plays media on the CD drive perfectly well, yet IF I insert my Microsoft Office 2007 install CD it will not mount at all.  It does not appear on the desktop of Places, yet the CD works on other machines and other media work on this machine...
 
Are these threads related?  And can anyone help, please?
 
[URL="http://ubuntuforums.org/showthread.php?t=1576048"][HTML] 
http://ubuntuforums.org/showthread.php?t=1576048
[/HTML][/URL]

---

### Post by blacktrance on 2010-11-24
This sort of thing is a really bad decision on the developers' part. If I want to run something, then **you'd better let me run it**. I know what I'm doing.

---

### Post by Mythdc on 2010-12-11
Um can someone just tell me how to **_disable_** this?

---

### Post by TK-Tex on 2011-01-05
I just tried to install a program and got the executable bit problem. How I got around it, is by copying all the files from the CD and then marking the program as executable. And that seemed to work. Try and see if it works for you.

---

### Post by Ron May on 2011-01-22
> **Antonio Tavares said:**
> 

To create the script you use the following command:
**gksudo gedit /usr/local/bin/cautious-launcher**
and paste the code on the above post and save.
Then you better make it executable (!) with the following:
**chmod +x cautious-launcher**



Thank you (and cdenley) VERY much for the solution to this problem.  I lost the ability to launch an app (Forte Agent) from its windows folder on Local Drive on my dual boot laptop.  It works perfectly now either from Nautilus or the Application Launcher Icon on the top panel.  I understand and agree with the underlying security issue, but there should be a way to override as the two of you have provided.  Thanks again!
:cool:

---

### Post by arito on 2011-01-23
It astonishes me that this executable bit madness is brought in by purpose. I already wasted more than an hour trying to solve the problem (as if there weren't enough of other issues with Wine for a regular user), and get a piece of software to install from a CD (and it's still not done). And in the end some people on this forum try to convince us that this stupidity is for our own good :-o Dear Ubuntu developers: If we need to be warned of something, then warn, but let us use Wine and install our software without having to search through user guides and forum posts, and messing with scripts first. If you really want to prevent us from installing Windows software, then be honest and say it, but please stop wasting the time of the users with this executable bit non-sense! To most non-technical users treating the executables this way means that they can't install the software in question at all – which means that Ubuntu is severely broken to them! If you want to allow us to install Windows software, but you want us to consider the possible dangers to it, then guide as to a web site that clearly and simply explains the dangers, and if wasting our time is important to you, make us wait for an hour, before allowing us to continue the installation. Let's just leave out the unnecessary head scratching and forum searching from the process.

I must be one of the first public users of Ubuntu (as I waited hour by hour for the download link to the beta version of 4.10 to become available), but now, with this and a many other issues (some of them also related to user permissions), I'm beginning to think of moving over to another distribution (although I don't know, if these things are managed any better on any other distro).

Thanks for those in the forum who are doing their best to help (and to those developers, who are really trying to make Ubuntu easy to use).

---

### Post by arito on 2011-01-23
Thanks cdenley for instrucions, they worked. Thanks Antonio Tavares making them easier for a non-technical user to follow.

It would be even easier, if the second command (chmod +x cautious-launcher) readily contained "sudo" and the path to the file in question (I'm not quite sure, how to write the path properly)

Perhaps the instruction could be made a sticky message too, to make it easier for people to find it right away.

---

### Post by cygnus-X1 on 2011-02-06
Post #33 did not work. Neither did Antonio's solution. 

Post #49 did. Now I just need to figure out the lockup that occurs when it asks for the second disc.

---

### Post by steelsteel! on 2011-02-12
> **cygnus-X1 said:**
> 

Post #49 did. Now I just need to figure out the lockup that occurs when it asks for the second disc.

Hello!
I tried the mentioned solution, but my *.exe files lacked the x-bit. So, the cautious-launcher tries to "exec $@ $exe" and fails on my 10.10 system. Nothing happens if i prees "yes" in the dialog box.

I fixed script, but i want my fix to be discussed. Thanks in advance!

```
#!/bin/bash
# For use with .desktop files and MIME handlers so that the Ubuntu Policy
# can be followed: programs cannot be executed when they lack the execute bit.
# https://wiki.ubuntu.com/SecurityTeam/Policies#Execute-Permission%20Bit%20Required
exe="$1"
shift || true
if [ -n "$exe" ] && [ ! -x "$exe" ] && \
   [ "${exe:0:5}" != "/usr/" ] && [ "${exe:0:5}" != "/opt/" ]
then
    if [ -n "$DISPLAY" ] && [ -x /usr/bin/zenity ]; then
        /usr/bin/zenity --question --title "Warnung: Programmstart $*" --text "Kann diesem Programm vertraut werden? (ja/nein)" **&& chmod +x $exe** && ex
ec "$@" "$exe"

    else
        echo "$*: '$exe' is not executable.  Aborting." >&2
    fi
    exit 1
fi
**chmod +x $exe**
exec "$@" "$exe"
```

---

### Post by cariboo on 2011-02-12
I find this kind of funny that everyone spends so much time trying to get around security measures put in place by the wine devs, when it takes less than1 minute to find a solution to the problem, on the winehq web site. All you have to do is prepend the command with wine eg:

```
wine /path_to_executable/foo.exe
```

or just merely:

```
wine foo.exe
```

---

### Post by PeterOakland on 2011-03-18
> **amnite said:**
> Ok i figured it out when you the file you want to open. Right click and click open with other application, and select use custom command. The current command should say cautious-launcher. replace that with wine and you should be good, thats how i got my diablo to run... Lemme know if that works for you... Hehe Im kinda proud of myself, Kinda just stumbled upon it..

Worked perfectly, thanks a million!
To reprise:
right clicked
clicked on 'open with other application'
selected 'use custom command'
entered in block 'wine [name of my cd drive]/setup.exe'
Worked like a champ.
Using fresh installation of 10.04.
Thanks another million!

---

### Post by Morbius1 on 2011-03-18
> **cariboo907 said:**
> [COLOR=Blue]I find this kind of funny that everyone spends so much time trying to get around security measures put in place by the wine devs,[/COLOR] when it takes less than1 minute to find a solution to the problem, on the winehq web site. All you have to do is prepend the command with wine eg:

```
wine /path_to_executable/foo.exe
```or just merely:

```
wine foo.exe
```
The security measure was not put in place by the wine devs but by ubuntu: [https://wiki.ubuntu.com/Security/ExecutableBit](https://wiki.ubuntu.com/Security/ExecutableBit)

As someone a year ago mentioned in this thread the problem isn't wine or java ( it also happens on a jar file ) but something called cautious-launcher. Wine didn't put that there and in the case of a jar file I seriously doubt that oracle put that there :wink:

You can either use "wine /path/to/file" or remove "cautious-launcer %f" from the launcher command in /user/share/applications.

---

### Post by Yfrwlf on 2011-06-29
If a malicious program or hacker has the ability to attempt to run a program on your computer, I'd think they would also have the ability to chmod a file?

It just seems like a silly security measure to me, and one which Windows and Mac don't have to deal with.

Is this annoyance doing any actual good in the real world whatsoever?  Is this is actually mitigating any real threats to Linux security?

At the very least, pop up a box to ask if the user wants to make it executable so that there are fewer clicks required to do so?

---

### Post by The Cog on 2011-06-29
If you read the thread carefully, you will see that chmodding the file is not required. And on a CD, it's not even possible. All you need to do is to open the file with wine instead of cautious-launcher.

Maybe cautious-launcher should ask if you want to open the file instead of plain refusing, but then again maybe not. It's not a good idea to train users to click Yes too freely. If you really do repeatedly run executables from read-only media, perhaps you should change the open-with settings to use wine instead. Then you are well on the way to reducing things to Windows's level again.

---

### Post by dakkar9999 on 2011-07-19
> **amnite said:**
> Ok i figured it out when you the file you want to open. Right click and click open with other application, and select use custom command. The current command should say cautious-launcher. replace that with wine and you should be good, thats how i got my diablo to run... Lemme know if that works for you... Hehe Im kinda proud of myself, Kinda just stumbled upon it..

Thanks!  That worked for me as well!

---

