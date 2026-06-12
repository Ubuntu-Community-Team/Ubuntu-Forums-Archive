---
title: "Blank screen after switch user/logout/inactivity"
date: 2007-11-14
forum: System76 Support
---

### Post by EmilyRose on 2007-11-14
Occasionally after logging out, switching users, or simply closing the computer for a time, we get a blank screen, with the same background as the log-in screen, with a pointer. The pointer moves, but theres nothing to click on, and ctrl+alt+delete has no affect, nor do any of the other keys... the only thing that we can do is hold down the power button untill the computer shuts down and then push it again to restart. 

This has happend several times now, seemingly randomly... mostly it seems to occur when we switch users or leave the computer running, but closed...

---

### Post by ackey on 2007-11-14
I've also seen this on my daru2 a few times, but I have had a variety of problems with ubuntu (even before upgrading from feisty to gutsy) that I assumed were just due to my fiddling (and incompetence...).  When my laptop gets into some unresponsive state I usually try switching to one of the terminals and restarting from there.

---

### Post by thomasaaron on 2007-11-15
Does it ALWAYS happen when you switch users?

I'd check your power management settings (System > Prefs > Power Management) and make sure it isn't trying to drop into sleep or something after a certain period of time (and failing to do so correctly).

---

### Post by happyisland on 2007-11-15
I'm getting the same error on a non-System 76 desktop I have at home.

---

### Post by EdwardOwens on 2007-11-17
I'm having the same problem. Im running Gutsy with 6 user accounts. So far everything is running great except this. I have desktop effects enabled. If you need any other info just ask. Im a noob with linux although I have installed many distros trying the find the greatest. Ubuntu and PCLinuxOS so far seems to be the best with PCLOS at the top.

P4   3.2Ghz
RAM 1.5GB
HIS X1950Pro Turbo 512MB AGP 8x

Im tripple booting XP, Ubuntu, PCLinuxOS

---

### Post by ofir_k on 2007-11-18
I have this issue too

My computer has 3 user accounts and when I try to switch to an user which is already logged-in, the screen turns white or black (blank screen...)

Is there any fix for this?

---

### Post by DomIncollingo on 2007-11-18
Does this problem occur when desktop effects are disabled?  I had a very similar problem running Gutsy on an old HP laptop, but the problem went away when I disabled desktop effects.

---

### Post by EdwardOwens on 2007-11-19
> **ofir_k said:**
> I have this issue too

My computer has 3 user accounts and when I try to switch to an user which is already logged-in, the screen turns white or black (blank screen...)

Is there any fix for this?

My problem is slightly different then yours. I could switch users just fine. My problem was if I had more than one person logged in and tried to logoff someone I would get that black screen. Although I just checked this and it seems that all is well and working. I don't know what was done but it is working. One thing i did do was this though maybe it will help.

sudo gedit /etc/usplash.conf

and make sure the resolution is set at whatever your monitor can handle. Then update the theme with this..

sudo update-usplash-theme usplash-theme-ubuntu

Hope that helps.. 

GL..

Ed:)

---

### Post by EmilyRose on 2007-11-19
It defiently doesnt happen everytime we switch users, just sometimes... and now that I read other posts, it may very well be happening when we've switched and then the other person (usually me) logs out while others are still 'switched'...

ETA: and for what its worth effects are enabled (normal)

---

### Post by thomasaaron on 2007-11-19
EmilyRose (nice name, by the way),

Try disabling the desktop effects (System > Prefs > Appearance > Visual Effects > None.

If that nips it in the bud, we'll need to take this to compiz. If it doesn't, we'll probably need to take it to Ubuntu.

---

### Post by EmilyRose on 2007-11-19
Since disabling visual affects I've run into a ton more random and bizzare problems:

Loading the computer takes FOREVER - 2+ minutes to login screen, hanging for a minute or so on starting CUPS

then after logging in it seriously takes at LEAST 2-4minutes to load my desktop before I can begin working

when i try checking for updates I get:

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

and it just flat out wont let me re-enable visual effects

All this has transpired since I disabled visual effects and re-added the network-manage applet to my panel... Oh, and when I booted up I got errors along the lines of OAF1D_Gweatehr Applet and OAF1D FastUserSwitch Applet

I am totally at a lost as to what has happend... or how to fix it...

And this is happening (or at least the super-long log-in is) on multiple user accounts...

---

### Post by EmilyRose on 2007-11-20
And now this morning it all works just peachy fine... bizzarre.... (with visual effects turned off...)

---

### Post by octathlon on 2007-11-20
> **EmilyRose said:**
> 
All this has transpired since I disabled visual effects and re-added the network-manage applet to my panel... 

I bet it was network manager and not disabling effects that caused the problem.  I had a similar slowdown happen because of n-m, when I turned off the wifi switch at the wrong moment.

---

### Post by wwilkinson on 2007-11-20
When I switch users, I get a blank white screen.  However, I can type the password and it will switch to the user.  I just do not get the password screen.  I disable all effects (for both accounts) and then I get a password pop up box with a blank, black background.  I do not remember if this was the default behavior (without effects), because I have always had effects turned on at some level.  It looks like it has something to do with the effects.

I have to say, that other than this small problem, I am enjoying my freedom from the other choice.

Now if I could just get rid of Quicken in a virtual console.

Dell XPS M1710, Core 2 Duo, 2G memory
GeForce Go 7900 GS - Using NVIDIA restricted driver

Wayne

---

### Post by betes on 2007-11-21
FWIW- This isn't a system76 problem (it happens on my HP desktop) and isn't a Compiz problem (i have desktop effects disabled).

---

### Post by DaBigEd on 2007-11-21
Yea i have this problem on my lappy as well. I am running Xubuntu 6.06 (did the same thing with 7.04 and 7.10). I have no desktop effects turned on. It happens to me every time i try to enter the log in screen after booting. (ie ctrl+Alt+bkspace, logout or sleep).

any ideas?

---

### Post by desertboy on 2007-11-21
Happens here as well, switch user seems to work but when I log out of another user I get the white screen can still type the password but my Family struggle with it.

Only happens if there's one user left logged in, when I logout everyone on the system I get the proper screen, compiz is on.

---

### Post by markoloka on 2007-11-21
I have blac/nk screen problem when i either switch user or logout. 
Usually  when i start my pc i get to blac/nk screen but that's worked w/ CTRL+ALT+BACKSPACE. I wouldn't rather use it w/ switching user as it throws me out and all programs are shutdown.

Specs:
Ati 2400HD
MSI Neo-F2
2gb ram
No compiz or so 
and FGLRX 8.42.
Edit:Gutsy.

---

### Post by jhetrick62 on 2007-11-24
All, I have experienced the same problem.  Upon reading these threads, I tested it and indeed, the problem with the white screen is that it isn't putting up a password screen?

If you type the password from the first user and hit "enter" it logs right back in.  So the bug must be that after the second user logs out, it fails to supply a password request GUI, although it is looking for it and will accept it to get back to the original user.

Jeff

---

### Post by thomasaaron on 2007-11-26
It sounds like when you are switching users, the computer is prompting for the password of the new user. However, the login window is not appearing.

This could be because your backlight is off. (?)
Try using your brightness function keys to turn on the backlight.
Or touching your mousepad.

---

### Post by johnsonjii on 2007-12-18
I have this exact problem as well. When I switch from one user to another and then log out the second user I get a white screen instead of the screen that requests the previous user's password. The white screen accepts the password, though, and then switches back to the first user.

This seems to be completely unrelated to the Visual Effects setting. It happens with Visual Effects set to None and with Visual Effects set to Extra or Custom.

Also, this is *not* an issue with a backlight. This is happening to me on a desktop machine and the screen is turning completely white except that I can see the mouse cursor just fine.

I also found that when I had three users logged in, logging out the third user gave me the correct screen, but logging out the second user still had the bug.

---

### Post by Dr. Strange on 2007-12-21
Confirming a fix. I have a Dell D400 (specs and other relevant data at [http://ubuntuforums.org/showthread.php?t=591229&page=7](http://ubuntuforums.org/showthread.php?t=591229&page=7) ).

I hadn't tried a logout yet on this system and tried one after completing the fix in the above post. The result was the same as a reboot before the reboot=b fix - system appeared to hang, black screen, etc.

I changed Preferences -> Appearance -> Visual Effects from Extra to Normal. The logout problem vanished.

---

### Post by Dr. Strange on 2007-12-21
OK... the previous success-post seems to have been a little hasty - it didn't hold. However, I think I've found out why this is happening, as well as numerous other problems - there may well be a common cause. Please see:

[http://ubuntuforums.org/showthread.php?p=3995260#post3995260](http://ubuntuforums.org/showthread.php?p=3995260#post3995260)

for a more detailed look and a possible work-around.

---

### Post by jhetrick62 on 2007-12-26
Well all, after some research, I have at least found a useable workaround.  It still does not post the log-in screen for the gdm when switching users to an "active", already logged-in user that was previously switched out of.  However the following workaround does work for me.

When you are presented with the "white screen", press Alt-s and it will re-display the login/password screen.  For me, I'm using a gnome user browser log-in screen.  This works so far every time.

I was getting the white screen when using the switch user and then logging out of the second user to go back to the original user.  I was also seeing it when leaving the second user open and switching back to the original user using the "fast user" selection.

Give the Alt-s a try and it may solve the issues for now.

Goodluck,
Jeff

---

### Post by dpdamato on 2007-12-31
Had  the same problem.  Disabled desktop effects, which solved the problem, but I like the eye-candy.   Alt-S also works, but my wife (the other user)  is a computer novice. I'm trying to get her to use Ubuntu & didn't want it to be complicated.

Thanks for the help.

---

### Post by cm690 on 2008-01-02
i got the same problem. I think the computer didn't freeze. It just showing the blank screen for asking user to type his/her password. here is the workaround i have been using:

1) User A switched to User B
2) Blank screen showed up (seems like freeze on User B)
3) Type User B's login password
4) User B's desktop show up

This worked for me

Ubuntu Gusty; AMD 64 5200+; 2GB; GeForce 7050PV; AN-M2HD MB

---

### Post by johnsonjii on 2008-01-03
cm690 said:
> ... here is the workaround i have been using:

1) User A switched to User B
2) Blank screen showed up (seems like freeze on User B)
3) Type User B's login password
4) User B's desktop show up

You are having the exact same problem as the rest of us. Your workaround is not a workaround; it is the bug. I for one do not want to enter my password to a blank screen. I want to see the screen that requests the password.

----------------------------------------------------------------

dpdamato said:
> Disabled desktop effects, which solved the problem...

This does not work for everyone. I can completely disable desktop effects and the bug still shows up.

---

### Post by frediE on 2008-01-05
Having the same issue.  Blank/white screen after switching users.  I think it has something to do with the fast-user-switch-applet current version is 2.20.0.

A workaround for for me is...
  System > click Quit > and choose Switch User

I get a new log in screen, enter username and password and I am up and running.
This is nice because I can leave the desktop effects enabled.

---

### Post by frediE on 2008-01-05
Also noticed in the About of fast-user-switch-applet 2.20.0 is a dead URL.  good job.

[http://ignore-your.tv/fusa/](http://ignore-your.tv/fusa/)

---

### Post by zekesmz on 2008-01-19
I have been seeing this issue consistently since I performed a fresh install of Gutsy on my home PC (Pentium 3.0 Ghz Single Core / 2GB RAM )

The problem happens with and without desktop settings enabled.

I have seen both the white screen and a black one. 

With the white screen, no cursor is visible. With the black screen, I can see the cursor.

One factor that seems to increase the frequency of the occurance is heavy use of Flash based web sites. The problem almost always occurs when I log out of my daughter's account - she is a frequent visitor of nickelodeon.com, disney.com and other kids sites which have a lot of Flash in them. 

The problem rarely occurs from other accounts where Flash sites are not visited.

Not sure if this will help...hope it does.

-z

---

### Post by johnsonjii on 2008-01-22
> zekesmz said:
The problem rarely occurs from other accounts where Flash sites are not visited.

I can confirm that Flash does not have to be present for this issue to show up. I have a 64bit system and this shows up every time there are two users logged in. I don't have Flash installed because the 64bit version of Flash is broken and cannot be installed.

---

### Post by gsmart on 2008-02-04
I have also had this problem.  I have a user logged in (myself) and I switch user to allow someone to access their account without disturbing what I was doing.  So I select to switch user.  Then the other person logs in and does their thing.  When they are finished, they logout as normal...but it goes to a white screen.  Alt+s will bring me to the log in screen as described in this thread.

I looked at the logs at the time that this happens and I found the following entry... Hopefuly this helps someone who is able to fix this bug.  We use this as a family computer and the bug is a little irritating.

You will see the cannot determine username when trying to get back to my account and perhaps accounts for the blank screen?

Greg

auth.log

Feb  4 18:41:56 smart-desktop gdm[5692]: pam_unix(gdm:session): session opened for user gsmart by (uid=0)
Feb  4 18:41:56 smart-desktop gdm[5692]: gkr-pam: unlocked 'login' keyring
Feb  4 18:53:57 smart-desktop gdm[6341]: pam_nologin(gdm:auth): cannot determine username
Feb  4 18:53:59 smart-desktop gdm[6341]: pam_unix(gdm:session): session opened for user julie by (uid=0)
Feb  4 18:53:59 smart-desktop gdm[6341]: gkr-pam: unlocked 'login' keyring
Feb  4 18:54:10 smart-desktop gdm[6341]: pam_unix(gdm:session): session closed for user julie
Feb  4 18:54:19 smart-desktop gdm[6598]: pam_nologin(gdm:auth): cannot determine username

---

### Post by Superkoop on 2008-02-04
I was having the same problem today when I was setting up Ubuntu for the rest of my family, and Ubuntu would always give me a white screen when I either logged off of a user, or when I would switch. 
So I did some searching around the web, and I stumbled on a bug report from a couple years ago, someone posted a fix. It has worked for me, so far. I have logged off and switched users a couple times, without the "white screen of death". [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/48974](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/48974)
That's the bug report, and here is the fix they posted:



In /etc/gdm/gdm.conf-custom :

[daemon]
AlwaysRestartServer=true
RemoteGreeter=/usr/lib/gdm/gdmgreeter
[security]
AllowRoot=true

---

### Post by johnsonjii on 2008-02-26
I can confirm that adding the line:
> AlwaysRestartServer=true
does not fix the issue on my system (amd64/nvidia/4096M RAM).

There is a current [bug (#112518)]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/112518") in Launchpad that explains the issue quite well.

Currently it seems that the issue is with the nVidia driver or the way it interacts with Xorg. There are some workarounds suggested in the bug comments, but I have not had a chance to test any of them on my system. You mileage may vary.

---

### Post by zaffod on 2008-03-10
Ok, here's my 2 cents. 

Issue occurs only when compiz is enabled! Switching users works but switching back to the first session brings up the white screen. Alt-s seems a suitable workaround for this issue.

Nothing of interest in auth.log
Disable all Visual Effects = no problems. 

Playing with various x settings / changing drivers etc has caused a few freezes. Usually able to ssh to the machine and reboot it gracefully. 

System: AMD64 4800+, 3GB RAM, nVidia 7900GT

I am tempted to try Envy. Many users seem to report it "fixes" all their issues. 
I know it's not supported, but hey, if it works, it works. Any opinons here?

---

### Post by zaffod on 2008-03-11
err. it didn't work.
Still have the same issues after trying Envy, so i got rid of it.

---

### Post by mattjtwomey on 2008-03-12
I still get this issue.
I had it in Gutsy and now I've upgraded to Hardy (Alpha 6) I still get it.
So basically I'm switching users using the "User Switcher" and each time I get a blank screen.
I'm going to reinstall all Compiz-Fusion to see if this helps.

---

### Post by zaffod on 2008-03-13
Something just occurred to me. 
I was on Feisty till a week ago. I did an dist-upgrade to Gutsy but synaptic was broken afterwards ([here for details]("http://ubuntuforums.org/showthread.php?t=717566")). I used the system for several days and switched users many times. However! This issue white screen issue did not occur!!! No problems! Only when I could not resolve the synaptic issue did I clean install Gutsy...

Maybe this might help someone figure out where to troubleshoot this issue.

---

### Post by bibby on 2008-03-15
I'm certainly affected by this bug, though in my opinion it's not related to Flash sites, network manager or compiz as has been suggested (at least not for me), because it's easy for me to reproduce.

I can consistently lock up the computer by:
Starting the computer and logging in as User A.
Switch User..
Login screen appears, log in as User B.
Switch User..
Login screen appears, log in as User A.
As soon as I submit my passwd, I see nothing but black.

I'll keep reading these posts, and fiddling around, but I wanted to at least make these steps public.

---

### Post by zaffod on 2008-03-15
bibby, can you enter your password for user A in the black screen and hit enter?

---

### Post by ace007 on 2008-03-22
Yeah, I t does it only when I am switching from a non-admin account to my admin account.  Not the other way around.  

And when the blank screen comes up, I can type my password and press enter and all works as its suppose to. 

Any ideas?

---

### Post by zaffod on 2008-03-22
Do both account have desktop effects enabled? I'd guess it'd be more related to that than account privileges. 

I removed my 7900gt card and started using the onboard graphics. All these issue went away. Not sure what that means.

---

### Post by dbius on 2008-03-29
I have the same problem with Kubuntu 7.04. I'm using Compiz.

If I switch from user "A" from user "B", then when I switch back to user "A" I have only a black screen with the mouse pointer.

The mouse I can move, but nothing else...

I can't type blink my password, because it doesn't work.

Only CTRL+ALT+BACKSPACE works.

I have nvidia 7900gto vga, with driver installed with envy.

---

### Post by AlanB66 on 2008-04-18
> **jhetrick62 said:**
> 
Give the Alt-s a try and it may solve the issues for now.

Goodluck,
Jeff

Thank You!

---

### Post by AlanB66 on 2008-04-18
I have attempted a number of suggestions in this forum to no avail. However, I would not call this the "white screen of death" since Jeff wrote, in [_[COLOR="Blue"]http://ubuntuforums.org/showpost.php?p=4018345&postcount=3[/COLOR]_]("http://ubuntuforums.org/showpost.php?p=4018345&postcount=3"), a viable alternative for now:


press  **Alt-S**  and your login screen should get refreshed. :guitar:

This, of course, is more viable than guessing if you're typing the username/password for the unknown-selected user at the whited-out screen.

---

### Post by robaldred on 2008-04-22
I do not have an issue when logging in or switching user, but I get a blank screen with just the mouse cursor when I return to the PC after it has been on screen saver!

It never shows the unlock screen box, if i just type my password it unlocks but this is pretty rubbish, the only way our is ctrl+alt+Fx , login to new session and killall gnome-screensaver

Any suggestions?
Rob

---

### Post by dbius on 2008-04-25
I found a solution in Compiz-Fusion forums and it works for me!

**from adamk:** *"This is with an nvidia card, correct? This seems to be a known issue with their drivers. **You can try seeing if setting or unsetting 'Sync to VBlank" in ccsm --> general options --> display settings** has any impact."*

**[SIZE="5"][[COLOR="Red"]ORIGINAL TOPIC ABOUT SOLUTION IS HERE![/COLOR]]("http://forum.compiz-fusion.org/showthread.php?t=6745")[/SIZE]** :guitar:

---

### Post by valadil on 2008-04-28
I have this problem too.  When using the switcher applet to switch between users I get a white screen instead of a password screen.

A couple things to note: 

If I switch to a user who does not lock the screen when switched out, there is no white screen.  It's definitely the password prompt that doesn't show up.

This only happens when switching to a user with compiz running.  Switching from compiz to no compiz gives me a password prompt as expected.  Switching from no compiz to compiz gives me a blank screen.

Incidentally this happens on an nvidia card running two displays in twinview.  I had assumed it was twinview related.

---

### Post by dbius on 2008-04-28
> **valadil said:**
> I have this problem too.  When using the switcher applet to switch between users I get a white screen instead of a password screen.

A couple things to note: 

If I switch to a user who does not lock the screen when switched out, there is no white screen.  It's definitely the password prompt that doesn't show up.

This only happens when switching to a user with compiz running.  Switching from compiz to no compiz gives me a password prompt as expected.  Switching from no compiz to compiz gives me a blank screen.

Incidentally this happens on an nvidia card running two displays in twinview.  I had assumed it was twinview related.

Did you try that I wrote in #47?

---

### Post by valadil on 2008-04-29
> **dbius said:**
> Did you try that I wrote in #47?

Yes, I tried sync to vblank in both accounts, then rebooted.  No luck.

---

