---
title: "Screen goes black at random intervals and won't come back on."
date: 2008-07-24
forum: Server Platforms
---

### Post by 47_MasoN_47 on 2008-07-24
I'm running an IBM x236 server at work that we just put Ubuntu 8.04.1 on to be our new file server via Samba.

Here's the problem.  So far it has only done this 3 times, but it is annoying just the same.  While I'm using it browsing config files via webmin or looking for something on the web, right after I click a button in Firefox the screen will just turn off.  It will then turn back on for a second (nothing on display though) then the monitor will go into powersave mode and I am unable to get it back out of that.  I can CTRL+ALT+F1 and get to the terminal to shut it down and turn it back on again, but why does it do this and how can I make it stop?

Thanks.

---

### Post by 47_MasoN_47 on 2008-07-25
Please?

---

### Post by 47_MasoN_47 on 2008-07-28
Bump.  I desperately need a fix for this!

---

### Post by dca on 2008-07-28
You didn't install desktop edition on the server did you?  Are you saying you access this server remotely from another Ubuntu station using webmin or you're logged in to the server and using FF to webmin into other servers or you're using localhost webmin to config same server?  So you have a GUI/DE installed on this server and if so, is 'Visual Effects' turned off in 'System -> Preferences -> Visual Effects [TAB]'??? 
 
Also ,if this is not the case, try accessing server from remote system using webmin utility and see if you get same results...
 
I'm not going to be much help because it sounds too difficult to determine if it's some kind of add-on in FF or something relative to graphics or even ACPI...
 
What's listed in the syslog when this happens?

---

### Post by dca on 2008-07-28
By the by, try using openSSH if you're going to change text files on remote server.

---

### Post by 47_MasoN_47 on 2008-07-28
It's running server edition but I installed the ubuntu-desktop package.  That's what I do on all my servers, I just prefer a GUI.  I'll check that visual effects tab, I won't get to restart it until 5 when everyone leaves so it'll be another hour or so before I can post results.

I just use webmin on the local machine.

Sorry for being a noob, but where do I access the syslog?  I'll have to wait until I have GUI back for that too, for me trying to use vi is about as fun as [insert any number of off-color metaphors here].

Thanks for the replies, and I generally do use OpenSSH but I don't have it on this one yet, it's only been setup for about a week now and I have 3 other servers to deal with.

---

### Post by 47_MasoN_47 on 2008-07-28
Confirmed visual effects are set to none.

---

### Post by cariboo on 2008-07-29
You don't need the gui to check the logs. You are using webmin already to administer the server. To check the logs click on System then at the bottom click System Logs, this will show you a list of logs that you can peruse at your leisure. If a log isn't in the list you can add it.

With all the functions available in Webmin, I would suggest shutting down gdm, just to see if this is what is causing the problem. TO do this, from a remote computer ssh into your server and type:

```
sudo /etc/init.d/gdm stop
```

Just let it run with no gui for a couple of days  to see if the problem persists.

Addendum: you don't need vi to look at logs, I use mc, it is a dual paned file manager and it also will do ftp and has a builtin editor.

---

### Post by 47_MasoN_47 on 2008-07-29
Shutting down gnome sortof defeats the purpose though.  Gnome appears to be the part that is crashing out or whatever is happening because I can CTRL+ALT+F1 and get to the terminal.  I can still use the system and access files over the network after the Gnome problem.  I've been trying to get our accounting server running again today, but after lunch I'll post up what shows up in the logs.

---

### Post by gammypoofle on 2008-09-06
This'll be my first post..woo :).

Hi, I'm actually having the same problem.

I'm using Ubuntu Desktop (8.04) on an Intel Mac Mini(Intel Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)) running GNOME and Firefox 3.0.1.

Just a few minutes ago it happened(screen went blank) exactly at the same time as I clicked the "Save" button in Firewfox (to start downloading songbird!).

I went in to a console (CTRL+ALT+F2 in my case) and had a look at the logs (Xorg, dmesg, syslog) but could not see anything of interest. I restarted GDM twice, first by a kind-spirited /etc/init.d/gdm restart, and after confirming (the 'welcome' chime) I also tried CTRL+ALT+BS - Still just a blank screen. I had to reboot for it to come back.

I wonder, what hardware are you using?

Cheers

---

### Post by windependence on 2008-09-06
Shutting down gnome is probably the best thing you could do. If you're gonna run a real server, you should get familiar with the command line because as you discovered, you are useless without that GUI crutch. I know you hate me right now but you don't in any way shape or form need a GUI OR Webmin to run your production boxes.

As cariboo mentioned, there are very good tools available for the command line, some of them are ncurses quasi-GUI apps like mc and you don't have to use vi either, you can use nano, or another easy editor. I'm not ashamed to admit I don't use vi. Some day, when you have to use a recovery CD to recover a system without the GUI, you'll thank me for being hard on you. ;)

You might want to take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=851061](http://ubuntuforums.org/showthread.php?t=851061)

-Tim

---

### Post by 47_MasoN_47 on 2008-09-06
I'm actually having the problem on 2 different servers, 2 desktops, and a laptop.  It seems to occur most frequently when pushing buttons in Firefox or closing a tab in Epiphany.  I'm not sure what it is about web browsers, but I mainly use Opera now because of the problems with FF and Epiphany.  So far I haven't been able to reproduce the problem with Opera.  I don't know what is causing it but it's annoying.  It happens on both desktop and server edition (8.04.1) on 32 bit and 64 bit.

---

### Post by 47_MasoN_47 on 2008-09-06
> **windependence said:**
> Shutting down gnome is probably the best thing you could do. If you're gonna run a real server, you should get familiar with the command line because as you discovered, you are useless without that GUI crutch. I know you hate me right now but you don't in any way shape or form need a GUI OR Webmin to run your production boxes.

As cariboo mentioned, there are very good tools available for the command line, some of them are ncurses quasi-GUI apps like mc and you don't have to use vi either, you can use nano, or another easy editor. I'm not ashamed to admit I don't use vi. Some day, when you have to use a recovery CD to recover a system without the GUI, you'll thank me for being hard on you. ;)

You might want to take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=851061](http://ubuntuforums.org/showthread.php?t=851061)

-Tim

I've gotten pretty good with the terminal personally, but the problem is that there are a lot of other n00b upper management people that have to be able to do maintenance on the thing and they won't even attempt anything on a terminal.  If I don't have screenshots of exactly what to click on and other such things it won't work, so I have to use the GUI.  I prefer a GUI personally (this is 2008...computers have been around long enough where nothing should be terminal only IMO) but I can use the terminal to do most anything that I need to.  Others aren't so willing to learn though unfortunately.

Thanks for the input though, and I'll check out that thread I'm sure there's always more that I can learn.

---

### Post by tribez on 2008-09-07
I have had the same problem with a standard desktop install of ubuntu 8.04.
The monitor does not report 'no signal' and it's as though the monitor is still receiving data.
Unlike Mason I am a desktop user and therefore would prefer to keep the GUI.
If anyone has a reason/solution it would be much appreciated.

---

### Post by 47_MasoN_47 on 2008-09-08
This is obviously something that the devs should look in to.  If there are multiple people having the same problem then there must be a bug in GDM that causes it to crash out when certain events happen in web browsers.

---

### Post by 47_MasoN_47 on 2008-09-09
I just had this problem occur again on the server and I lost all the work I had done on writing some scripts for it.  This really ticks me off.

Any ideas on how to fix it?  Please!

---

### Post by 47_MasoN_47 on 2008-10-08
Well I guess noone knows what to do about this.  I haven't had it happen for a while at home.  Maybe the newer versions of Firefox have fixed the problem.  I switched to using Opera on our server and it hasn't ever caused any problems, so anyone else still experiencing this may just want to do that.

---

### Post by iradieh on 2008-11-12
I got the same issue with a mac mini.
I restart X  - gdm restart and ctrl-alt-back space
Nothing happends.
I can still hear sounds in the background.

This usually happends when playing movies using mplayer, vlc or xbox media center.

I am using a Mac Mini with inteprid.
I have tried _ALL_ versions
That is, alt an desktop, 64, 32, hardy and inteprid.
Same issue with all.

The only way to clear the frozen screen is with a reboot.
it's like the screen freezes and picks a colour, usually it's black but I have gotten white and beige too.

I really need a hand with this.

---

### Post by 47_MasoN_47 on 2008-11-13
Hmm I haven't ever had it happen when playing video or something.  I think all those media players use X11 as the default video output (XBMC doesn't like my ATI video card so I can't use it on my desktop).  Since there is still sound in the background I don't think it's quite the same issue I'm having.

Something you can try though, would be to switch the video output from X11 to OpenGL, or if it's set to OpenGL at the time, switch it to X11 and see if you have the same problem.  X11 generally performs better for me, but I have had some problems on my ATI machines with it.

---

### Post by afz902k on 2008-11-30
> **iradieh said:**
> 
I restart X  - gdm restart and ctrl-alt-back space
Nothing happends.
I can still hear sounds in the background.

> **iradieh said:**
> 
The only way to clear the frozen screen is with a reboot.
it's like the screen freezes and picks a colour, usually it's black

I'm having the exact same problem on my Laptop. My video card is an Intel 945, and I'm using Intrepid. It usually happens when using Firefox, or Songbird, but it has even happened randomly while using the Gimp, pidgin or gedit.

---

### Post by mitchroberts on 2008-11-30
i have had that to do the samething on the desktop but the problem was 
nvidia i updated my drivers and it fixed it.

---

### Post by klight on 2008-12-01
> Originally Posted by iradieh View Post
The only way to clear the frozen screen is with a reboot.
it's like the screen freezes and picks a colour, usually it's black


I've found that if I suspend then immediately start the system back up the screen will return.

I've been having this problem since upgrading to Ibex on a Gateway MT6821 notebook.  The screen will blank at very odd times even when there is user input going on.  The system continues to run as I can ctrl-alt-F1 and get to a shell, but resetting gdm has no effect.  Compiz is disabled (or at least It's supposed to be) but not removed.

I've also noted that the screen "jumps" on occasion.  It kind of reminds me of the jiggle that happens when you enter the wrong password at the graphical login screen.  The blanking doesn't occur at that point, but it seems to be a sign that bad things are about to happen.

The other thing that I've noticed, and it may be completely unrelated, is that the media player will only play a few seconds of video and then stops playback.  This only happens when the jitters or blanking are imminent.

---

### Post by afz902k on 2008-12-02
Well, I do experience some audio playback glitches sometimes prior to getting the "black/gray screen of death".

---

### Post by 47_MasoN_47 on 2009-03-10
Well none of my computers or my servers have done this in several months now, so I'm going to mark it as solved.

I'm not sure about the multimedia issues, but I think it is different from what I was having.

---

### Post by hypest on 2009-03-25
It's a really annoying problem!! Happens to me almost once a day :( in firefox/terminal and elsewhere...

I'm on a Intel MacMini 1.8G, Ubuntu 8.10

So, the only "solution" I can think of now is to revert back to 7.10 (where my keyb's multimedia keys where working flawlessly too!).

Sorry to bump this thread, just looking for a fix...

hypest

---

### Post by Raugturi on 2010-08-02
Did anyone ever find a solution to this?  I recently installed Ubuntu 10.04 on my IBM ThinkPad W500 and have this issue.  At random times the screen will just go blank.  The only way I've found to get it back is to Fn-F4 to go into sleep mode and then power back on.  Even if there's no fix I'd love to find a solution for reloading the screen that doesn't kill all my apps (along with any progress they've made in their current task).

Edit: I just realized that I did not have the proprietary video card driver enabled.  Turning that on now to see if it's resolved.  We'll know in few hours when it does or doesn't crash in the middle of this 4-hour job and cause me to start over. :-)

---

### Post by nosh276 on 2011-03-12
I'm running a clean install of Ubuntu on a regular laptop and my screen will go black no matter what I'm doing.

I set my powerbutton to log me off when pressed. Logging out and back in fixes returns the screen to normal.

I have everything on the default settings--visual effects in the middle.

Help?

---

