---
title: "So I suggested Ubuntu-linux for &quot;some&quot; computers at work..."
date: 2009-10-14
forum: The Cafe
---

### Post by ZarathustraDK on 2009-10-14
...and they said YES! (or, at least, a gave a "go" to starting up a project to test it out, with me as the lead-guy) :guitar:

If I'm being rather vague, it's because I can't reveal the details.

Outline:
We have a lot of audience-pc's (trust me when I say "a lot" ;) ). Their function is basically running an office-suite, surfing the internet, and running an assortment of not-too-sophisticated windows apps (apps I have little doubt will run in WINE if no alternative exist). These pc's have run WinXP so far, but they have been marred with vira and malware because of their "exposed" position ("porn-star caught in a maximum security-prison-riot" is a fitting analogy). People are coming in each day with their own usb-keys (supplementing the on-site borrow-usb's), they surf nefarious sites, you know, a security admins nightmare where you can't count on people following security guidelines because...well...they don't care. On one location (note ONE location) I was called out to there was a huge conficker-outbreak (about 200 machines), it took 3 people more than a week to clean up.

And so I suggested Linux as a solution, the rest is, as you say, history.
The basic idea is to create a couple of standard-images that'll be rolled out on all the pc's in question. The pc's will be using the [linux altiris agent]("http://www.altiris.com/Support/Documentation.aspx") to communicate with our servers for software-rollouts (don't even get me started on that, it's sort of like apt/synaptic done badly). The machines will have to access what I, at this early stage, gathers is a Windows 2003 server-share (you know, as when you in winxp go "Start"-->"Run..." and punch in something like "\\someserver\someshare$". 

So, guys, I might be relying on this forum quite a bit in the near future, hope you're up for it. Believe me when I say this could potentially be a big win for us if it gets executed right. Tonnes of people will get to use it and it could serve as inspiration for other, more widespread, projects in the future if it withstands the barrage of abuse it will be subjected to (Mike Rowe would run away screaming).

An initial question: What would your take be on locking down the pc most efficiently? I'm talking users not being able to touch anything (not even altering/deleting configuration-files in the home-directory (yes, only ONE account for all the users))? The only thing they should be allowed to do is running the installed programs available to them and saving stuff to a usb-key and, perhaps, a particular folder (I, for instance, managed to mess up my x-session by doing stuff I shouldn't have done with some of the hidden files in my home-dir, without using root-privileges). Is there an easy/standard/rock-solid way to accomplish this?

Again, this is just the preliminary phase, but trust me when I say I'm psyched about making it happen ;D .

---

### Post by uberg on 2009-10-14
Congratulations.  And Good luck.  I will be following this forum to see your progress.

---

### Post by TheStroj on 2009-10-14
Congratulations and good luck! =)

Answer to your question: If you don't tell anyone a 'sudo' password, they can't really do anything. They can't delete important files and install programs with Synaptic (they all require a password).
But you can also encrypt the folders: Right-click on folder, Encrypt - so people can't access them.

---

### Post by gdonwallace on 2009-10-14
I would suggest creating a single user group and making sure that everyone is a member of that group.  You can use that group to then control what they are able to do on the machine.  You can also assign them to the same /home directory.  Although that would make for a huge directory based on what you are saying.  I would suggest multiple home directories.  Not one for each, but at least a few to spread the usage of the directory around.  

Also, when you setup the users / groups, the app in Ubuntu will allow you to tell it what they can / cannot do.  Take a look at it.  If you have Ubuntu running on anything, check your own login and see what you have access to.  

Good luck and I hope everything works out for you.

---

### Post by praveesh on 2009-10-14
> **ZarathustraDK said:**
> ...and they said YES! (or, at least, a gave a "go" to starting up a project to test it out, with me as the lead-guy) :guitar:

If I'm being rather vague, it's because I can't reveal the details.

Outline:
We have a lot of audience-pc's (trust me when I say "a lot" ;) ). Their function is basically running an office-suite, surfing the internet, and running an assortment of not-too-sophisticated windows apps (apps I have little doubt will run in WINE if no alternative exist). These pc's have run WinXP so far, but they have been marred with vira and malware because of their "exposed" position ("porn-star caught in a maximum security-prison-riot" is a fitting analogy). People are coming in each day with their own usb-keys (supplementing the on-site borrow-usb's), they surf nefarious sites, you know, a security admins nightmare where you can't count on people following security guidelines because...well...they don't care. On one location (note ONE location) I was called out to there was a huge conficker-outbreak (about 200 machines), it took 3 people more than a week to clean up.

And so I suggested Linux as a solution, the rest is, as you say, history.
The basic idea is to create a couple of standard-images that'll be rolled out on all the pc's in question. The pc's will be using the [linux altiris agent]("http://www.altiris.com/Support/Documentation.aspx") to communicate with our servers for software-rollouts (don't even get me started on that, it's sort of like apt/synaptic done badly). The machines will have to access what I, at this early stage, gathers is a Windows 2003 server-share (you know, as when you in winxp go "Start"-->"Run..." and punch in something like "\\someserver\someshare$". 

So, guys, I might be relying on this forum quite a bit in the near future, hope you're up for it. Believe me when I say this could potentially be a big win for us if it gets executed right. Tonnes of people will get to use it and it could serve as inspiration for other, more widespread, projects in the future if it withstands the barrage of abuse it will be subjected to (Mike Rowe would run away screaming).

An initial question: What would your take be on locking down the pc most efficiently? I'm talking users not being able to touch anything (not even altering/deleting configuration-files in the home-directory (yes, only ONE account for all the users))? The only thing they should be allowed to do is running the installed programs available to them and saving stuff to a usb-key and, perhaps, a particular folder (I, for instance, managed to mess up my x-session by doing stuff I shouldn't have done with some of the hidden files in my home-dir, without using root-privileges). Is there an easy/standard/rock-solid way to accomplish this?

Again, this is just the preliminary phase, but trust me when I say I'm psyched about making it happen ;D .

congratulations .  But it is possible to make windows almost as secure as linux by the use of limited user accounts etc .  . . . . .

---

### Post by imbjr on 2009-10-14
I'm trying to think how you stop the home config files from being messed with.

You can stop the use of the terminal and nautilus/other file manager, but if you want to allow downloading onto USB you are going to have to corral them into one directory somehow.

---

### Post by earthpigg on 2009-10-14
have it autologin to a 'guest session' where no changes are saved?

create a script that runs at boot time that copies the contents of a backup /home that you have kept in /opt/home to the normal /home?

---

### Post by mintochris on 2009-10-14
> **earthpigg said:**
> have it autologin to a 'guest session' where no changes are saved?

create a script that runs at boot time that copies the contents of a backup /home that you have kept in /opt/home to the normal /home?

my suggestion is to use guest sessions with a face-browser style gdm. Have the machine auto-logout after 10 mins of inactivity (with a 30 sec warning) and the face browser gives you one click access to a fresh guest session.

---

### Post by NTolerance on 2009-10-14
I wonder if simple UNIX permissions on the /home directory can make this work.  Deny write access to the home directory and deny execute access to any GNOME programs that customize the desktop or user settings. 

There might be a better way to do this, but UNIX permissions are straightforward and simple.  I'm curious to hear other opinions about this.  

Also, if it were me, I'd make the GNOME desktop somewhat resemble an XP desktop.  Just simple changes, like single menu bar at the bottom with launchers to the common apps on the panel and/or desktop.  I think the last thing you want is users taking one look at the desktop and not wanting to even try using it because the icons they look for aren't in the familiar place.

---

### Post by slakkie on 2009-10-14
You might want to look at puppet for configuring all those boxes. It is in the repo's.

---

### Post by starcannon on 2009-10-14
> **ZarathustraDK said:**
> ...and they said YES! (or, at least, a gave a "go" to starting up a project to test it out, with me as the lead-guy) :guitar:

If I'm being rather vague, it's because I can't reveal the details.

Outline:
We have a lot of audience-pc's (trust me when I say "a lot" ;) ). Their function is basically running an office-suite, surfing the internet, and running an assortment of not-too-sophisticated windows apps (apps I have little doubt will run in WINE if no alternative exist). These pc's have run WinXP so far, but they have been marred with vira and malware because of their "exposed" position ("porn-star caught in a maximum security-prison-riot" is a fitting analogy). People are coming in each day with their own usb-keys (supplementing the on-site borrow-usb's), they surf nefarious sites, you know, a security admins nightmare where you can't count on people following security guidelines because...well...they don't care. On one location (note ONE location) I was called out to there was a huge conficker-outbreak (about 200 machines), it took 3 people more than a week to clean up.

And so I suggested Linux as a solution, the rest is, as you say, history.
The basic idea is to create a couple of standard-images that'll be rolled out on all the pc's in question. The pc's will be using the [linux altiris agent]("http://www.altiris.com/Support/Documentation.aspx") to communicate with our servers for software-rollouts (don't even get me started on that, it's sort of like apt/synaptic done badly). The machines will have to access what I, at this early stage, gathers is a Windows 2003 server-share (you know, as when you in winxp go "Start"-->"Run..." and punch in something like "\\someserver\someshare$". 

So, guys, I might be relying on this forum quite a bit in the near future, hope you're up for it. Believe me when I say this could potentially be a big win for us if it gets executed right. Tonnes of people will get to use it and it could serve as inspiration for other, more widespread, projects in the future if it withstands the barrage of abuse it will be subjected to (Mike Rowe would run away screaming).

An initial question: What would your take be on locking down the pc most efficiently? I'm talking users not being able to touch anything (not even altering/deleting configuration-files in the home-directory (yes, only ONE account for all the users))? The only thing they should be allowed to do is running the installed programs available to them and saving stuff to a usb-key and, perhaps, a particular folder (I, for instance, managed to mess up my x-session by doing stuff I shouldn't have done with some of the hidden files in my home-dir, without using root-privileges). Is there an easy/standard/rock-solid way to accomplish this?

Again, this is just the preliminary phase, but trust me when I say I'm psyched about making it happen ;D .
Well done; if you pull this off, it looks as though you may have carved yourself a nice niche in your company.

I think from the sounds of it, that Ubuntu could be a solid choice for your project. I can't wait to hear more about it. Your going to have way more control over everything the Users can and can not do with the Operating System, all while letting the User never feel like they are being denied privs.

GL and HF

---

### Post by ibuclaw on 2009-10-14
> **earthpigg said:**
> have it autologin to a 'guest session' where no changes are saved?

create a script that runs at boot time that copies the contents of a backup /home that you have kept in /opt/home to the normal /home?

Look-up what a Union Filesystem is. Removes the need to do this, with the downside of adding overhead with the more MBs of changes you make ontop of it. But in an office environment, this won't be the issue between reboots if you have the user accounts sync with a profile server.

Regards
Iain

---

### Post by NCLI on 2009-10-14
Tillykke!! I do hope you'll share the details of how it went when the trial period is over and the decision is made.

Anyway, I'd probably setup one account for all of them, with a shared, unwritable /home directory. However, on the desktop, there should be a link to a fileserver on the network where the could all save what they want to. It would essentially be a home directory without access to any configuration files. Of course, you should also remove the alt+F2 keybinding, and remove all configuration utilities from the Ubuntu menu.

---

### Post by keiichidono on 2009-10-14
Why so secretive? Do you work for Uncle Sam or do you have a Non-Disclosure Policy at your place?

---

### Post by t0p on 2009-10-14
> **ZarathustraDK said:**
>  vira and malware

*Vira*, huh?  That's a new one...  Hint: it isn't vira, viri, virii... the word is **viruses**.

> **ZarathustraDK said:**
> 
So, guys, I might be relying on this forum quite a bit in the near future, hope you're up for it.

Oh, I'm sure folk here will be only too happy to help.  But if this is as big a deal as you're suggesting, don't you think your employer should shell out for some proper support?  You don't really want to rely on amateur and voluntary support for an operation of this magnitude, surely?  I know I wouldn't.

> **ZarathustraDK said:**
> 
An initial question: What would your take be on locking down the pc most efficiently? I'm talking users not being able to touch anything (not even altering/deleting configuration-files in the home-directory (yes, only ONE account for all the users))? The only thing they should be allowed to do is running the installed programs available to them and saving stuff to a usb-key and, perhaps, a particular folder 


[This HOWTO]("http://users.telenet.be/mydotcom/howto/linuxkiosk/ubuntu01.htm") is a few years old, so the details may be off.  But it does cover locking down machines in a "kiosk mode" quite nicely.  There's also stuff in [this thread]("http://ubuntuforums.org/showthread.php?t=1068317") about locking down Firefox.

Good luck!

---

### Post by dragos240 on 2009-10-14
> **uberg said:**
> Congratulations.  And Good luck.  I will be following this forum to see your progress.

So will I.

---

### Post by Niko Johnson on 2009-10-14
Congratz man thats great... i mentioned using linux in my workplace but it was a no go... some people are just to scared to make the change.... taking you linux virginity only hurts the first time ;)

---

### Post by NTolerance on 2009-10-14
> **t0p said:**
> 
[This HOWTO]("http://users.telenet.be/mydotcom/howto/linuxkiosk/ubuntu01.htm") is a few years old, so the details may be off.  But it does cover locking down machines in a "kiosk mode" quite nicely.  There's also stuff in [this thread]("http://ubuntuforums.org/showthread.php?t=1068317") about locking down Firefox.


I checked out that howto and it was quite comprehensive.  But I wonder about virtual terminals.  Sure, if that guide is followed the user's shell is set to /usr/bin/screen so a shell wouldn't start within a virtual terminal, but a nefarious user could "black out" all the kiosk PC screens by switching to a virtual terminal.  

Is there a way to disable virtual terminals on a per-user basis or do you just have to wipe out all the TTYs altogether to prevent CTRL-ALT-F1?

---

### Post by ceramicm on 2009-10-14
I don't know if this is exactly what you are looking for (I've never used them), but if you open "gconf-editor" and navigate to /desktop/gnome/lockdown, there are keys that disable application handlers, command line, lock screen, printing, print setup, save to disk, and user switching.

Good luck!

---

### Post by Bölvaður on 2009-10-14
this sounds superb like you described it in the following posts.
and the thing with guest account, it's just brilliant.

now all you need to do is make the stuff that the people want the only thing they will see or be able to get to, and then you are set to go.

---

### Post by Pasdar on 2009-10-15
1. Make an account.
2. Make that account auto login.
3. Install what they need and uninstall what they don't need.
4. Place only shortcuts to the programs they need.
5. Remove all other shortcuts.
6. Change read/write permissions on folders.
7. Disable all keyboard shortcuts.

Done.
1. Make an image of that system.
2. Place it on a few PCs and ask random people to do their utmost best to destroy it/corrupt the system if they can.
3. If they manage to do so, ask how they did it and make counter measures.
4. Make final image and roll out on more PCs as test for your audience.

PS: Place a good theme, not the standard lame gnome theme that looks like win3.1

---

### Post by RichardLinx on 2009-10-15
You might want to make it so users can't run malicious commands like rm ~rf.

---

### Post by earthpigg on 2009-10-15
> **RichardLinx said:**
> You might want to make it so users can't run malicious commands like rm ~rf.

my vote would be:

a) deny users root permissions, of course.
b) let them do whatever they want in their ~.
c) ensure the changes to ~ are non-persistent between reboots.



oh, and don't forget to remove the 'recovery mode' or whatever it is in GRUB that gives you a root tty.

local access is root access, as we all know, but i'd assume that co-workers would notice someone opening the case to reset the password-protected BIOS that will not boot from CD or USB... start your security concerns at GRUB.

---

### Post by ZarathustraDK on 2009-10-15
Great, lots of good advice here, I'll discuss them with my teammembers. Think we'll take a friday night (with plenty of beer) messing around with the user/group-permissions and other stumblingblocks that pop up (Altiris-agent being another one, I'm not too proficient with how that one works practically, but it should, it's native after all).

As for the confidentiality question, well, I'm not sure if I should be confidential or not, so I play it safe. As far as I can see it's pretty benign, but strange people possibly have strange reasons to want to keep stuff like this on the low (y'know, be careful of who's toes you're stepping on today, as they may be connected to the butt you have to kiss tomorrow (ok, that was sick, I'm not like that :D )).

Stuff I have to do right now/tomorrow: Get a hold of a test-pc, set up an appointment with the guy who (hopefully) will be willing to become guinea-pig later on if we get pilotproject-approval. He seems reasonable, he knows how malware can ruin your day, and I get the impression he's aching to get new computers.

So the plan is basically:

1. Make a test-pc that works.
2. Pilotproject, test a bunch of the pc's in the environment they're supposed to be in.
3. Boom goes the dynamite :)

But I'm getting ahead of myself. Lots of stuff can go wrong, or simply get hamstrung by higher-ups.

---

### Post by The Real Dave on 2009-10-15
> **mintochris said:**
> my suggestion is to use guest sessions with a face-browser style gdm. Have the machine auto-logout after 10 mins of inactivity (with a 30 sec warning) and the face browser gives you one click access to a fresh guest session.

I've seen alot of public pcs with that set up, UCC, the closest college to me, uses such as set up on XP Pro with the computers in lecture halls and that. Once a user logs out, the account is cleared, bar for one folder on the desktop. Keeps things clean and snappy

---

### Post by markbuntu on 2009-10-15
Just make sure that he understands that he needs to learn some new tricks. Tell him there are just a few simple tricks to learn that will make his life easier and more fun.

Fun is important, so is being tricky.

You can set up the machines so a reboot will return them to a default state no matter what people do with them. You can even set the machines up to do this when the usb key is removed or someone logs out.

---

### Post by ZarathustraDK on 2009-10-17
So we've talked it over the last couple of days.

The idea came up to use Ubuntu Netbook Remix in a kiosk-kind of way. I haven't had any experience with that just yet, so I couldn't really give any meaningful feedback on it.

What do you guys think? I can see it makes sense from the perspective that the users aren't going to have access to most of the things that the "regular" Ubuntu interface is build with in mind (System-menu, Places-menu, a desktop to save things to), so a regular desktop would end up kind of empty with lot of unused screen-real-estate. But how mature is netbook remix? Guess my concern is that it introduces some unexpected side-effects that one takes for granted with the regular interface. Got to test it out methinks.

On another note, before I couldn't wait for the project to go ahead, now I really wanna wait for Karmic (got a lot of sweet things like better intel-video-support that would be dandy, plus it's an LTS).

---

### Post by xuCGC002 on 2009-10-17
> **ZarathustraDK said:**
> 
On another note, before I couldn't wait for the project to go ahead, now I really wanna wait for Karmic (got a lot of sweet things like better intel-video-support that would be dandy, plus it's an LTS).

Karmic is **NOT** an LTS release. Just clarifying that.

---

### Post by NCLI on 2009-10-17
> **t0p said:**
> *Vira*, huh?  That's a new one...  Hint: it isn't vira, viri, virii... the word is **viruses**.
Just wanted to add that we say can use the word vira in Danish, so he probably got it messed up.

> **ZarathustraDK said:**
> So we've talked it over the last couple of days.

The idea came up to use Ubuntu Netbook Remix in a kiosk-kind of way. I haven't had any experience with that just yet, so I couldn't really give any meaningful feedback on it.

What do you guys think? I can see it makes sense from the perspective that the users aren't going to have access to most of the things that the "regular" Ubuntu interface is build with in mind (System-menu, Places-menu, a desktop to save things to), so a regular desktop would end up kind of empty with lot of unused screen-real-estate. But how mature is netbook remix? Guess my concern is that it introduces some unexpected side-effects that one takes for granted with the regular interface. Got to test it out methinks.

On another note, before I couldn't wait for the project to go ahead, now I really wanna wait for Karmic (got a lot of sweet things like better intel-video-support that would be dandy, plus it's an LTS).
As said above, _**Karmic is NOT an LTS**_ ;)

Netbook-Remix is VERY mature, but if you just want the interface, I'd recommend doing an ordinary lighweight Ubuntu install, then installing the ubuntu-netbook-remix package, and making sure it starts at boot. 

UNR comes with a lot of drivers you don't need if you're not using a netbook, so using that for a desktop PC would be quite stupid, which is why I recommend just adding the interface to a regular installing.

---

### Post by ZarathustraDK on 2009-10-17
> Karmic is NOT an LTS release. Just clarifying that.

Oh, silly me, still stuck in the "every third Ubuntu is an LTS"-mode. :)

> Netbook-Remix is VERY mature, but if you just want the interface, I'd recommend doing an ordinary lighweight Ubuntu install, then installing the ubuntu-netbook-remix package, and making sure it starts at boot.

UNR comes with a lot of drivers you don't need if you're not using a netbook, so using that for a desktop PC would be quite stupid, which is why I recommend just adding the interface to a regular installing.

Good stuff, good stuff. I'll look into that.

---

### Post by Rainstride on 2009-10-17
> **ZarathustraDK said:**
> So we've talked it over the last couple of days.

The idea came up to use Ubuntu Netbook Remix in a kiosk-kind of way. I haven't had any experience with that just yet, so I couldn't really give any meaningful feedback on it.

there is a program in the repo's that is meant to lock down a pc in kiosk mode. its called lockdown editor, i don't have a clue if it has what you would need though. 

you would probably be better off setting up a custom user group for normal users with custom permissions. Im not completely sure how, im a little behind on my linux reading:(.

---

### Post by ZarathustraDK on 2009-10-18
Here's a little more info on specs, goals, thoughts and otherwise:

> 
**Goal: Make an unbreakable pc that let's users surf and write documents in.**
	
**Hardware-specs:**
	Model: HP DC5800 Small form-factor
	Mainboard : Intel Q33 Express
	FSB : 1066MHz
	Processor : Intel Core 2 Duo ??GHz (can't remember if it's 2.5GHz o 3GHz)
	RAM : 2/4 GB DDR2 SDRAM 800MHz
	Graphics: Intel GMA 3100 onboard
	HD-Interface : Serial ATA-300
	HD-capacity : 160GB
	HD-speed : 7200rpm
	CD/DVD : Yes
	Monitor(s) : 1280x1024 resolution (probably set to 1024x768 by default for visually impaired people), 17'' and 19'' displays

**Software:**
	Operating System : Minimal Ubuntu (hopefully Karmic Koala) with Netbook Remix interface
	Browser : Firefox (hopefully we'll cram 3.5 in there), with flash and java installed (other plugin-suggestions would be nice)
	Word-processing : OpenOffice 3 (hmm... 3.2 is in december, that's an awful long time to wait)
	Graphics-editor : GIMP, and perhaps some other lightweight paint-clone for people who are not used to layers
	Video : VLC media-player (they don't "need" it, but regardless it's nice to have around)
	Some timewaster games (Nexuiz, ah j/k :) )
	Brasero (hey it's got a Lightscribe DVD-burner, let's use it)
	Antivirus : ClamAV (yeah yeah, what could possibly go wrong, it's policy, so no evading that one)
	Altiris-agent

**Notes on the PC-setup:**
[LIST]
[*]BIOS should be password-protected
[*]Boot from cd/dvd should be disabled (possible to hose the system if not)
[*]Access to GRUB should be prohibited or password-restricted
[*]Automatic security-updates, otherwise no software-updates (new versions of programs may introduce breakage, but security-updates are important)
[*]Hog-tying of user-permissions. Yet to be decided, lot's of possibilities, needs playing around with
[*]If users get write-access to a folder (still to be decided), the system must roll back any changes on reboot
[*]Users get automatic write-permissions to mounted usb-drives
[*]Must be done in a way that does not make the users feel limited (ie. automatically guide the user to the USB-share if he/she wants to save something, avoid situations that will lead to the user continuously being reminded that he/she does not have permission to do this and that.)
[*]Make the interface look significantly more snazzy than WinXP
[/LIST]

**Thoughts:**
[LIST]
[*]Should there be more (basically unneeded) applications on the pc for showcasing possibilities in other areas? Or should we just make it OpenOffice & Firefox? The latter is easier to maintain and probably more secure, the former may entice further projects/make the audience want to try it out at home.
[*]32 bit or 64 bit?
[*]Will the Netbook Remix interface look bad in 1280x1024? (It was made for netbook-resolutions after all...)
[/LIST]


I know, the hardware is totally overpowered compared to the task it has to perform. But it's what we use :D

---

### Post by billdotson on 2009-10-18
Good job man, time to potentially save a lot of money for your company.

---

### Post by Slug71 on 2009-10-18
I would probably encrypt the /home partition.

---

### Post by ZarathustraDK on 2009-10-30
UPDATE:

We received our test-pc's (these [http://search.hp.com/query.html?charset=iso-8859-1&lk=1&la=en&nh=10&st=1&rf=0&qs=&hpvc=sitewide&uf=1&qt=HP+Compaq+dc5800+Small+Form+Factor+PC&ocoldqt=dc5800&oc=3658094]("http://search.hp.com/query.html?charset=iso-8859-1&lk=1&la=en&nh=10&st=1&rf=0&qs=&hpvc=sitewide&uf=1&qt=HP+Compaq+dc5800+Small+Form+Factor+PC&ocoldqt=dc5800&oc=3658094")).

I installed Karmic on one with an alternate install cd (stupid me thought "alternate"="minimal install", so it took a while :)

The computer booted, everything was peachy, with a few exceptions:

1. Graphics were strange. Compositing with compiz worked, but it was waaaaay choppy. The amount of choppyness seemed to grow with the size of the thing being moved around (windows, for instance).
I did an lspci and got the following:
```
XXXXX@Sephiroth:~$ lspci
00:00.0 Host bridge: Intel Corporation 82Q33 Express DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82Q33 Express Integrated Graphics Controller (rev 02)
00:03.0 Communication controller: Intel Corporation 82Q33 Express MEI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
```
I'm not sure what video-driver I'm supposed to use for this chipset (Q33). The xorg-video-intel package on the machine is for i740, which seems outdated to me but I could be wrong. Any ideas?

2. Sound isn't working. The pc has an onboard (well inside the chassis at least) speaker. I suspect it's tied into the chipset-drivers again.

3. When blank computers get the future image, the hostname of a given computer should be changed to the serial-number of the motherboard. As in the output of:
```
henrik@Dabendan:~$ sudo dmidecode | more
............lots of other stuff............
Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: ASUSTeK Computer INC.
	Product Name: M3N78 PRO
	Version: 1.XX
	Serial Number: **MS1C89B26502405**
```

So I'll need to do some kind of script for that at some point that'll be run after/during imaging.

Only got to play around a couple of hours today, but that's my preliminary findings. Netbook-remix interface looks sweet on a 1280x1024 screen, feared the opposite (alas, the video-problems does burst that bubble a bit).

So, any ideas on the video-problem? It's a showstopper if it doesn't work.

---

### Post by ZarathustraDK on 2010-01-25
Just letting you know we're not dead ;)

The project is coming along nicely, although we've been marred with accidents along the way. First (well, not really an accident) the requirements escalated (suddenly we needed to provide multi-support-capability were before we didn't), then, through misunderstanding, one of our test-pc's were taken and returned to the oblivion of our storage (had to remake it). Then we thought "hey, let's just bring the server and the client home with us, then we can work undisturbed there", but as luck would have it my isp disconnected my internet for a week (again miscommunication was to blame). So yeah, rough ride so far, but it's not all doom and gloom.

On the bright side we finally figured out the support-part and it works like a wonder. It's pretty simple, works like Teamviewer and Gotomeeting, and I'll be sure to publish the details once it's finalized, scripts and all, as it seems we're missing something like that. But basically it breaks down to this:

1. Supporter starts his VNC-program and makes it listen for incoming feeds.

2. Customer clicks a launcher->script that asks which port on the server they want to connect to, customer punches in a number (which he is told by the supporter), script establishes a reverse vnc-tunnel between the server and the customers pc.

3. The server has an incoming port dedicated to each supporter-computers MAC/IP. When it receives a connection (from a customer) on one of these, it will ssh-tunnel the connection to the supporter-computer associated with the given port. Voila, a  vnc-support solution that supports multiple supporters and not-on-network multiple clients.

---

