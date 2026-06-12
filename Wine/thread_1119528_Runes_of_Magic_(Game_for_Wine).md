---
title: "Runes of Magic (Game for Wine)"
date: 2009-04-08
forum: Wine
---

### Post by Gen2ly on 2009-04-08
[Another post]("http://ubuntuforums.org/showthread.php?t=1118099") brought up a free RPG like Regnum Online or World of Warcraft called Runes of Magic.  Woojoo claims to have luck with it but it didnt' work for me, but I'll pass on my experiences in hope that it does for someone else.

First, the Rom_Downloader doesn't work.  It just crashes when trying to run with wine.  Rather i had to download the full version.  The full version does install but didn't allow input into the entry boxes till after i pressed the go button.  Then I was able to register.  When I tried start game, I got "Direct3D version does not match requirements."  So it looks like Runes of Magic would be able to be used with wine.  Doh!

lol, I think woojoo may've got me on this one.

---

### Post by ifyc576 on 2009-04-08
Just wanted to throw my 2 cents in fwiw.

I downloaded the client.

I installed the client to the latest wine.

I started the launcher which proceeded to download and execute update patches.

Once the patching was done I started the game.  I was presented with a scenic view of a forest with a waterfall in the background and a running river cutting through the middle of the scene. There were also some birds flying around.  There was also music.  Also the mouse pointer had changed to what I assume is the game pointer.  There were no dialog boxes present.  Such a tease!

I could always boot to Windows and install but damn that sucks!

Any ideas?

---

### Post by Gen2ly on 2009-04-08
Definitely got farther than i did.  Would be bono to have this game run on linux.

---

### Post by ifyc576 on 2009-04-09
Yeah, but it is still incredibly frustrating.  Just so that you can see what I get I've included some screen shots attachments.

The first one shows the Launcher. Notice the two bottom left progress bars show 100% complete so I can assume the game is patched up to date.

The second one shows what I get when I click on the "start game" button on the launcher above.  Also, I am not sure why the game cursor was not captured in the second screen shot.  Also, notice the version number in the top right corner of the first screen shot.

Oh well!  It still shows how powerful a program WINE is and I do appreciate all the hard work that goes into it!  In the meantime, my resistance to booting to Windows is crumbling fast.;)

---

### Post by Junkieman on 2009-05-02
You will probably have more success using the [latest development version]("http://www.winehq.org/download/deb") of WINE, 1.1.20 as of now.

Still no luck? press Alt+F2 and run 'winecfg' to configure WINE, on the *Graphics* tab switch the Direct3D shader support option.

On my pc it runs without hardware acceleration, but way too slow to be playable. Guess I'll need some real drivers before I can play, and that might take a while :(

Hope this helps!

---

### Post by ifyc576 on 2009-05-03
Thanks for the reply Junkieman.

I tried WINE, 1.1.20, but still no go.

I ran winecfg and switched the Direct3D shader support option, but still no go.

Thanks again for the suggestions.

---

### Post by gpapadak on 2009-05-03
Installed wine 1.1.20 and the game is working for me , no problems at all .

Game is running slower than windows , but i guess that should be expected.

Installed , patched , played with wine 1.1.20 np.

---

### Post by Junkieman on 2009-05-04
> **ifyc576 said:**
> Thanks for the reply Junkieman.

I tried WINE, 1.1.20, but still no go.

I ran winecfg and switched the Direct3D shader support option, but still no go.

Thanks again for the suggestions.
That second (forest) screen you're at is normally where you enter your login username and password. Can you tell if the game has crashed at that point, or perhaps the login input fields aren't showing for some reason.

---

### Post by ifyc576 on 2009-05-04
Hi Junkieman:

Yeah the login fields do not appear.  But, the EULA statement does not appear either.  I can't tell if the game has crashed.

Thanks.

---

### Post by jmervyn on 2009-05-09
I'll add myself to the growing list that gets to the pretty animated forest & stream picture with music, but never see an EULA or logon window.  Wine 1.1.21, Ubuntu 8.04, Linux Kernel 2.6.24.24.26, nVidia 6600 card.  Doesn't appear to crash; I have to escape or close the window out.

An earlier WineHQ post indicated "start with -game -opengl" but I wasn't too sure what the context was...
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14853&iTestingId=38315](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14853&iTestingId=38315)

Just in case, there's apparently been some success by Germans adding winsock.dll to /home/username/.wine/drive_c/windows/system32 and then enabling it in wine under the libraries tab.

---

### Post by kukuku on 2009-05-10
I can only get to the forest screen as well. Geforce 7600 GS.

I'm thinking of upgrading to a newer Geforce from the 8000 or 9000 series to sidestep this horrible problem... But I'd appreciate any ideas anyone has on what to try. I've got winetricks dotnet20, ie6, and d3dx9 installed. 

Disabling GLSL didn't help, it only resulted in a black screen instead of the forest scene (the game mouse cursor worked, though).

Clicking around on the forest screen doesn't give any game sound effects. I tried systematically clicking everywhere on the screen numerous times but didn't get anything.

---

### Post by ifyc576 on 2009-05-11
> **jmervyn said:**
> I'll add myself to the growing list that gets to the pretty animated forest & stream picture with music, but never see an EULA or logon window.  Wine 1.1.21, Ubuntu 8.04, Linux Kernel 2.6.24.24.26, nVidia 6600 card.  Doesn't appear to crash; I have to escape or close the window out.

An earlier WineHQ post indicated "start with -game -opengl" but I wasn't too sure what the context was...
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14853&iTestingId=38315](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14853&iTestingId=38315)

Just in case, there's apparently been some success by Germans adding winsock.dll to /home/username/.wine/drive_c/windows/system32 and then enabling it in wine under the libraries tab.

Yeah, I saw those suggestions as well.  Like you, I do not understand what starting the game with "-game -opengl" would do.  Maybe someone can enlighten us on what these options do...:confused:

As for adding the winsock.dll, I am hesitant to adding any windows dlls to my wine directory.  Yeah I scare easily.:eek:

---

### Post by jmervyn on 2009-05-12
> **ifyc576 said:**
> As for adding the winsock.dll, I am hesitant to adding any windows dlls to my wine directory.  Yeah I scare easily.:eek:Don't sweat the small stuff... :smile:  You can always change the load order or even remove the entry if you find it bothers you:

Wine configuration - Libraries tab
Existing overrides: winsock (native, builtin)

 - edit it, and just change it to "builtin then native" or even disable it.

> **kukuku said:**
> Clicking around on the forest screen doesn't give any game sound effects. I tried systematically clicking everywhere on the screen numerous times but didn't get anything.At one point I click-dragged and I 'moved' to standing on top of the stone platform, but there was still no interface.  I'm guessing that I managed to trigger the first of the screens by accident.

---

### Post by ifyc576 on 2009-05-13
> **jmervyn said:**
> Don't sweat the small stuff... :smile:  You can always change the load order or even remove the entry if you find it bothers you:

Wine configuration - Libraries tab
Existing overrides: winsock (native, builtin)

 - edit it, and just change it to "builtin then native" or even disable it.

Thanks for the assist.  I added the winsock dll, but no changes.  I tried the -game -opengl flags too, but to no success.

Oh well, at least some folks have been successful in getting the game to run albeit slower than in Windows.:)

---

### Post by jmervyn on 2009-05-14
> **ifyc576 said:**
> Oh well, at least some folks have been successful in getting the game to run albeit slower than in Windows.:)I'm betting it has to do with nVidia graphics cards.  Mine's a Ge-6600LE

---

### Post by ifyc576 on 2009-05-14
> **jmervyn said:**
> I'm betting it has to do with nVidia graphics cards.  Mine's a Ge-6600LE

Mine is a GeForce 6200.

---

### Post by stryderjzw on 2009-07-13
I have an ATI card and am only getting a black screen. :(

And where do I get a winsock.dll anyways?

Cheers!

---

### Post by Tantalus90 on 2009-07-20
Works good for me under wine 1.1.25 

1.1.26 makes it crash very soon after logging in.

For those of you stuck at the river with no clicky  eul agreement, try using winetricks and installing ie6 and or firefox.

Hope that helps

---

### Post by jnewl on 2009-07-24
Just wanted to add that I've been playing Runes for several months now with no problems, so it is possible. Unfortunately, I couldn't tell you now what I had to do to get it set up right. I don't remember. It wasn't that tough, though, as I recall.

One thing I'd suggest is searching the ENG forum (English language European forum) for Runes for directions on getting it to run under Linux. There's a thread there about it, I believe.

---

### Post by stryderjzw on 2009-07-24
> **jnewl said:**
> Just wanted to add that I've been playing Runes for several months now with no problems, so it is possible. Unfortunately, I couldn't tell you now what I had to do to get it set up right. I don't remember. It wasn't that tough, though, as I recall.

One thing I'd suggest is searching the ENG forum (English language European forum) for Runes for directions on getting it to run under Linux. There's a thread there about it, I believe.

Hey jnewl... What video card do you have?

---

### Post by TrelNadal on 2009-07-28
Hey all

i'm running 9.01, wine from CVS (cron job updates it weekly) winetricks with all the fonts and DX, this game works flawlessly for me. downloader worked, installer worked, game play is smooth, sound works updates work fine. no hacks in the registry, no adding windows files. works on multiple machines multiple video cards. nvidia 7300GS, ati X300, nvidia 9500GT, nvidia 9400.

my advice if you're having issues, is dump the canned version of wine. install wine from CVS. run winecfg and save the default settings. download winetricks, using winetricks install DX and allfonts.

:popcorn:

---

### Post by B00R4dL3y on 2009-08-03
I get to the logon screen, but when I enter my account name and password they are not accepted.  I tried the same account name and password on the website and it works.  It just doesn't work when trying to logon in the game.

At first I couldn't get the game going, but then I installed the d3dx9, directx9, and the fonts, IE6, dotnet20.  Not sure which ones where important to get it running.  After that I could get to the logon screen.

Now I am just stuck trying to logon.  Set 

--- Okay, I think I know what's wrong.  I set my server to the USA one, but I don't have an account.  I change to one of the other servers and it's working.  I'm just creating a character now.  So far so good.

---

### Post by nixIT on 2009-08-06
I installed WINE from the repos, installed Runes of Magic, and I am getting this error:

```

fixme:shdocvw:OleObject_Close (0x16ecc0)->(1)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x12e2fe0)->((nil))
fixme:shdocvw:OleObject_Close (0x16f928)->(1)
fixme:mshtml:HlinkTarget_SetBrowseContext (0xc3bcf8)->((nil))
fixme:actctx:parse_assembly_elem wrong version for assembly manifest
fixme:actctx:parse_manifest_buffer failed to parse manifest L"Z:\\mnt\\doitdata\\rom\\Microsoft.VC80.CRT\\Microsoft.VC80.CRT.manifest"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_assembly_elem wrong version for assembly manifest
fixme:actctx:parse_manifest_buffer failed to parse manifest L"Z:\\mnt\\doitdata\\rom\\Microsoft.VC80.CRT\\Microsoft.VC80.CRT.manifest"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\mnt\\doitdata\\rom\\xerces-c_2_8.dll") not found
err:module:import_dll Library xerces-c_2_8.dll (which is needed by L"Z:\\mnt\\doitdata\\rom\\Client.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\mnt\\doitdata\\rom\\Client.exe" failed, status c0000135

```

any ideas on how I can get this to work?

--nixIT

---

### Post by nixIT on 2009-08-07
> **TrelNadal said:**
> Hey all

i'm running 9.01, wine from CVS (cron job updates it weekly) winetricks with all the fonts and DX, this game works flawlessly for me. downloader worked, installer worked, game play is smooth, sound works updates work fine. no hacks in the registry, no adding windows files. works on multiple machines multiple video cards. nvidia 7300GS, ati X300, nvidia 9500GT, nvidia 9400.

my advice if you're having issues, is dump the canned version of wine. install wine from CVS. run winecfg and save the default settings. download winetricks, using winetricks install DX and allfonts.

:popcorn:

I tried winetricks to install dx and allfonts, but still getting the message that I posted about in my previous email. 

Any help getting ROM to run in Ubuntu would be GREAT, as I really don't like dual booting just to play 1 game.  :(

--nixIT

---

### Post by Noremacam on 2009-08-16
> **nixIT said:**
> I installed WINE from the repos, installed Runes of Magic, and I am getting this error:

```

fixme:shdocvw:OleObject_Close (0x16ecc0)->(1)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x12e2fe0)->((nil))
fixme:shdocvw:OleObject_Close (0x16f928)->(1)
fixme:mshtml:HlinkTarget_SetBrowseContext (0xc3bcf8)->((nil))
fixme:actctx:parse_assembly_elem wrong version for assembly manifest
fixme:actctx:parse_manifest_buffer failed to parse manifest L"Z:\\mnt\\doitdata\\rom\\Microsoft.VC80.CRT\\Microsoft.VC80.CRT.manifest"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_assembly_elem wrong version for assembly manifest
fixme:actctx:parse_manifest_buffer failed to parse manifest L"Z:\\mnt\\doitdata\\rom\\Microsoft.VC80.CRT\\Microsoft.VC80.CRT.manifest"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\mnt\\doitdata\\rom\\xerces-c_2_8.dll") not found
err:module:import_dll Library xerces-c_2_8.dll (which is needed by L"Z:\\mnt\\doitdata\\rom\\Client.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\mnt\\doitdata\\rom\\Client.exe" failed, status c0000135

```any ideas on how I can get this to work?

--nixIT

Install winetricks from here:

[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

Follow the instructions to install the 
vcrun2005sp1

package. That'll fix that particular error.

---

### Post by nixIT on 2009-08-17
Thanx, did that, and now I can get to what appears to be the login screen, as I can hear the music, but the screen is black.

--nixIT

---

### Post by stryderjzw on 2009-08-19
Where do I get winsock32.dll?  :(

---

### Post by nixIT on 2009-08-19
> **stryderjzw said:**
> Where do I get winsock32.dll?  :(

I got mine from [here]("http://www.dll-files.com/")

---

### Post by stryderjzw on 2009-08-19
Thanks, but it didn't seem to work. :(

At least with ATI's new drivers, the screen isn't black anymore. Too bad I don't get the EULA screen.

---

### Post by nixIT on 2009-08-22
hmm, my screen is still black.  did you make any other changes?

---

### Post by stryderjzw on 2009-08-22
FYI, I have an ATI card.

I upgraded Wine to 1.1.27 and there was a recent ATI drivers upgrade. I can see the forest, but the controls don't appear. :(

At least I dual boot, so it's okay.

---

### Post by nixIT on 2009-08-25
What ATI card do you have?  I have the HD3870, and with the latest ATI drivers, installed on Friday, my screen is still black.  :(

---

### Post by stryderjzw on 2009-08-25
> **nixIT said:**
> What ATI card do you have?  I have the HD3870, and with the latest ATI drivers, installed on Friday, my screen is still black.  :(

I have the ATI radeon hd 4650.

---

### Post by nixIT on 2009-08-25
I wonder if it's my 3870.  hmmm

---

### Post by stryderjzw on 2009-08-25
All I see is the forest screen anyways. There's still the bug with wine that on some video cards, the login box doesn't appear. So I can't play it anyways. Ugh.

At least I dual boot. :)

---

### Post by nixIT on 2009-08-26
but you can also see the forest, all I see is black, but hear the music and can see the RoM cursor, which is odd, and makes me think that there is a simple setting.  GRRR, I would love to have this game play in linux.

--nixIT

---

### Post by omgitsmit on 2009-09-01
I posted a full HOWTO on installing/running Wine + RoM + Curse Client under Ubuntu Linux on my blog.

[http://timashley.me/node/185](http://timashley.me/node/185)

Problem solved!

---

### Post by Xpander69 on 2009-09-19
little correction to 

```
Problems:

64bit Linux users will not be able to run the Curse Client. It's a 32bit based windows app and crashes when launched. You can manually install addon's by extracting them to ~/.wine/drive_c/Program\ Files/Runes\ of\ Magic/Interface/AddOns/
```

using 9.10 64bit, and curse client works like charm. with wine 1.1.29

---

### Post by omgitsmit on 2009-09-19
> **Xpander69 said:**
> little correction to 

```
Problems:

64bit Linux users will not be able to run the Curse Client. It's a 32bit based windows app and crashes when launched. You can manually install addon's by extracting them to ~/.wine/drive_c/Program\ Files/Runes\ of\ Magic/Interface/AddOns/
```

using 9.10 64bit, and curse client works like charm. with wine 1.1.29

I was having a lot of issues with the curse client. Maybe the latest release of curse works better, since RoM released their Chapter 2 version which forced everyone to upgrade their scripts/clients.

Glad to hear that its working for you, i will definitely give it a try here in a bit!

---

### Post by varkas on 2009-10-08
[LEFT]I am having trouble getting this game to launch.  There were no problems with the installation or updates.  However after I select game start there is an error saying "GPU does not meet minimum requirements".  I have a GeForce 6200 256mb card with and there are no problems when booting this game on my windows HD.  The only thing I can think of is my xorg.conf file is not configured for pixel shader support, opengl or something along those lines.  

      
Being new to this I am unaware of which options I should land into the configuration file without causing display problems.  Any help would be greatly appreciated.
[/LEFT]
 
V

---

### Post by omgitsmit on 2009-11-18
**UPDATE:** 

For those who are having the "No EULA / Login" display issue, a quick registry hack will get you up and running in no time! :)

[http://timashley.me/node/265](http://timashley.me/node/265)

---

### Post by blakjak02 on 2009-11-24
I did the registry hack but i still only see the waterfall and stuff..

---

### Post by CanadianBac0n77 on 2009-11-27
Where exactly do i put the .dll file?
i put it in the windows/system folder, but still nothing happens when i try to start the game. I can get the launcher but nothing happens when i press start game.

I also Tried this: [http://timashley.me/node/265](http://timashley.me/node/265)  and still no luck...(I installed the game and then did these steps, could that be the issue?)

I don't see how some people can just install it, do they have some software i don't maybe?

---

### Post by cabagekiller on 2009-11-30
I can't get the game to run either. I did all the mods for it to run on PlayOnLinux. It starts up the client, but crashes when it tries to load the game.

---

### Post by omgitsmit on 2009-11-30
> **blakjak02 said:**
> I did the registry hack but i still only see the waterfall and stuff..

Make sure you've installed your restricted graphics driver.

Make sure you're running the latest wine.

Make sure you've installed Visual C++ *AND* SP1 for VC++, DirectX and IE6 via Winetricks.

Check your registry for typos, ensure that it matches the screen shot in the article on my website.

I have made the registry hack on two computers that were having the "No EULA/Login" issue and it's worked for me 100% of the time.

> **CanadianBac0n77 said:**
> I also Tried this: [http://timashley.me/node/265](http://timashley.me/node/265)  and still no luck...(I installed the game and then did these steps, could that be the issue?)

I've only had one major problem when trying to run RoM on linux. Some video cards spaz out and wont display the EULA or Login. Per my tutorial on the website.

1) Install your accelerated video graphics driver 
2) Run the latest and greatest Wine 
3) Install Wine Dependencies via Winetricks 
4) Only make the reg hack if you're having EULA/Login issues.

Side note: I did download the individual packages instead of using their downloader app. Don't know if that makes much of a difference, it's all the same bits in the end...

> **cabagekiller said:**
> I can't get the game to run either. I did all the mods for it to run on PlayOnLinux. It starts up the client, but crashes when it tries to load the game.

I don't know much about "PlayOnLinux" but the tutorial on my site is for Ubuntu (Debian).

---

### Post by Bwathke on 2009-12-21
If I try to run the game it loads then says that its encountered a critical error and crashes. Any help?

---

### Post by omgitsmit on 2009-12-21
> **Bwathke said:**
> If I try to run the game it loads then says that its encountered a critical error and crashes. Any help?

I get the same error when the game is loading. I simply click "cancel" on the send report and it continues.

Couple things.

Only do the regedit hack if you're getting a infinite black screen with no login prompt (it does take awhile for the login to come up so be patient).

Make sure you're running the latest Wine

Make sure you have the latest accelerated video driver installed for your card.

Make sure you've installed all the required packages via Winetricks.

I say start from scratch. Download everything on a windows computer and transfer it over to your Linux box for installation. Then start with my first article: [http://www.timashley.me/node/185](http://www.timashley.me/node/185)

If you're having issues seeing the EULA/Login prompt, follow the rest of my article here: [http://www.timashley.me/node/265](http://www.timashley.me/node/265)

Good luck! :)

---

### Post by JoZ3 on 2010-01-01
Thanks for the article omgitsmit, I follow step by step each of the instructions but still do not see the EULA / Login prompt. my system is as follows:

- AMD X3 phenon II 710
- ATI RAEDON 4850
- 4GB RAM
- Ubuntu 9.10 64 bits
- Wine 1.1.35

I installed the latest ATI proprietary drivers and I run WOW smoothly and Torchlight among other games,

If you could help I would appreciate it, I played the beta of RoM and I was delighted, but at that time was using winxp, but now only use Linux, delete the winxp on my PC

(OMG my first post in the 2010 in the forum and all internet - Happy New Year 2010)

---

### Post by omgitsmit on 2010-01-02
> **JoZ3 said:**
> Thanks for the article omgitsmit, I follow step by step each of the instructions but still do not see the EULA / Login prompt. my system is as follows:

- AMD X3 phenon II 710
- ATI RAEDON 4850
- 4GB RAM
- Ubuntu 9.10 64 bits
- Wine 1.1.35

I installed the latest ATI proprietary drivers and I run WOW smoothly and Torchlight among other games,

If you could help I would appreciate it, I played the beta of RoM and I was delighted, but at that time was using winxp, but now only use Linux, delete the winxp on my PC

(OMG my first post in the 2010 in the forum and all internet - Happy New Year 2010)

Did you do the registry DirectX hack? Ensure that you spelled everything correctly, verbatim. Did you run tall the winetricks installations? Specifically vcrun2005, vcrun2005sp1 and directx9.

Recheck your work, i had two machines that wouldn't produce the EULA/Login screen and my updated regedit hack worked perfectly on both of them.

---

### Post by stroon on 2010-01-06
Hello!
I get a "Download /:0 version.txt fail!" when I try to open the game. Any help please?

---

### Post by omgitsmit on 2010-01-07
> **stroon said:**
> Hello!
I get a "Download /:0 version.txt fail!" when I try to open the game. Any help please?

Are you downloading the game or have you already completed the install?

---

### Post by 5nak3 on 2010-01-13
Hi all,

Just wanted to say that with a mixture of 

[http://gameshogun.ws/libregame/install-runes-of-magic-on-ubuntu-linux](http://gameshogun.ws/libregame/install-runes-of-magic-on-ubuntu-linux)

and

[http://timashley.me/node/185](http://timashley.me/node/185)

I managed to install the game, overcome the EULA issue and actually log in.

But this is where my problem begins, performance. I know performance through wine wont be great, but I'm getting 10fps with everything low except view distance which is at 1600.

And with everything (including view distance) as low as possible I'm getting 15-20fps.

I was wondering if anyone has any tips on how to boost performance at all?
I have a BFG 7600GS OC, and while it isn't latest and greatest that is the best my AGP board could find.



@omgitsmit

You mentioned installing "Visual C++ *AND* SP1 for VC++, DirectX and IE6 via Winetricks".

And i notice that in your two tutorials namely

[http://timashley.me/node/185](http://timashley.me/node/185) and [http://www.timashley.me/node/265](http://www.timashley.me/node/265)

You give a different set of winetricks downloads, would this impact performance in any way? 

I have no interest in installing IE6 or ROM addons, but I am curious about these two commands:

# sh winetricks vcrun2005sp1
# sh winetricks directx9

Because I only install vcrun2005 and everything seems to be working well except the fps issue.

Cheers!

---

### Post by limestone on 2010-08-04
For those who are interested, I made a request list for Runes to Linux here [http://ubuntuforums.org/showthread.php?t=1545713](http://ubuntuforums.org/showthread.php?t=1545713)

---

### Post by jpalko on 2010-08-12
There's one interesting thing I noticed regarding the Runes of Magic.

Personally I've preordered Overgrowth and Natural Selection 2 due to the fact that they are going to be available to Linux as well. At least that has been the advertisement all the time. If it won't happen, I'll want my money back. :)

However, the bit that Runes of Magic has in common with Overgrowth is that it uses also [Awesomium](http://www.khrona.com/products/awesomium/) as will Overgrowth. They are all the time promising that Linux support is in the horizon.

Seems like if RoM would take a few steps after/if Awesomium is ported to Linux that it might not be so far fetched to get a native version... All though there might be movement towards Berkelium in Overgrowth... :)

---

