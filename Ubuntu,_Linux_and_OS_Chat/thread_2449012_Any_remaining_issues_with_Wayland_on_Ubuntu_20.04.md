---
title: "Any remaining issues with Wayland on Ubuntu 20.04?"
date: 2020-08-18
forum: Ubuntu, Linux and OS Chat
---

### Post by maglin2 on 2020-08-18
I have been using ubuntu 20.04 wayland for a couple of months now and haven't come across any issues in normal daily desktop use.

Anyone else come across any?

---

### Post by exploder on 2020-08-18
I have to agree. Wayland is working well here too on two machines. The only quirk I have noticed at all is the LibreOffice splash displays higher on the display, very minor!

---

### Post by maglin2 on 2020-08-18
Seems to use a bit less RAM on my box too.

---

### Post by TheFu on 2020-08-18
Don't know.  Most of my system access is using remote X11. Doesn't Wayland just have wrappers around X11 for that mode?
None of my physical systems use 20.04, just in 1 VM. Perhaps in 2021 I'll move a desktop system or 2 up.  Some "servers" might move this fall. We'll have to see if the server programs are all stable on 20.04 by then.

I remember that screen recording didn't work under Wayland. Did they get that fixed yet?  I record live video conferences to make them available later for other members of the group who couldn't attend.  Use SimpleScreenRecorder for that.  [https://askubuntu.com/questions/980115/simplescreenrecorder-does-not-work-with-wayland](https://askubuntu.com/questions/980115/simplescreenrecorder-does-not-work-with-wayland)

Also need some screen capture software to work. I use **import**.
[https://imagemagick.org/discourse-server/viewtopic.php?t=30759](https://imagemagick.org/discourse-server/viewtopic.php?t=30759)

Those are older posts, so perhaps they will work. I just don't want to risk breaking a working solution.  Already had a problem with my backup software failing between 16.04 server and 20.04 client. Would rather not have a similar issue that requires lots of manual effort to build a workaround solution.  The 16.04 --> 20.04 migration will probably happen over a weekend for many systems.

These tools are part of larger automation setup using xdotool and cnee.  Much easier to just keep using X11 for my needs.  

If you don't use remote-X11 much, I can see where Wayland would be significantly better, especially for a desktop-centric user.

---

### Post by maglin2 on 2020-08-18
Screen capture works. 
I don't do any screen recording.

---

### Post by zebra2 on 2020-08-18
I have been using Ubuntu/Gnome/Wayland with the current Dev version since Ubuntu dropped Unity Desktop and introduced Wayland. I have not had a single issue with Wayland but back in the beginning there was a couple of x11 apps that wouldn't work without workarounds, LuckyBackup was one that I needed the most.  I used rsync for a while until xwayland got LuckyBackup on board.  All of the  proprietary software that I was using at the time already worked with wayland.  So other than that I haven't used x11 since Unity was dropped.  To this day my wife doesn't even know we made the switch and she is happy with what she has. This migration from one thing to another has always been a drama creator. First is was the demise of Gnome2 to Unity, then Grub to Grub2, then the demand that the install disk not exceed 700meg, then init to systemd, then x11 to Wayland. I'm sitting here running 20.10 with Gnome and Wayland and have never been more pleased with an operating system in my life and I started with MSDOS 2.3 or something like that back in the 1980's.  Darned! now my ear buds aren't working with pulse audio!

---

### Post by TheFu on 2020-08-18
> **zebra2 said:**
> Darned! now my ear buds aren't working with pulse audio!

Perhaps I'm a glass-half-full, risk adverse, person.  Been burned a few times when people claimed "there's no difference", since for me there always is.

There are many problems with 20.04 that concern me.  X11 is working great, so why change? To me, seems like a solution to a problem that I don't have.  

Just like systemd (and all the added crap that systemd is trying to take over), upstart, PulseAudio, snaps, flatpaks, netplan, network-manager, resolvconf, avahi, Unity, KDE, Gnome DEs (any version) ... all seem to be ways to break what is already working great.

Before we roll out a new desktop to 25K users, we need some things to absolutely, positively, work.

---

### Post by zebra2 on 2020-08-18
@TheFu
I've gotten some great insights reading your posts, so thank you for that. But regarding the "absolutely positively working" dream on!  I love linux but not for its perfection. Just take all of the UEFI borked login posts as an example of that. Look at it like this, Ubuntu works great for me, but that has a lot to do with me! Like everything else in this reality, we make our own decisions.

---

### Post by TheFu on 2020-08-18
We don't use UEFI booting about 95% of the time. 

As long as Wayland is a choice, not mandated, that's excellent.  Certainly,` some group of users see it as a benefit.  Choice is good while technology matures.  The handling of Wayland by Canonical has been really excellent.  
[LIST=1]
[*]Introduced in a non-LTS release
[*]Delayed as the default in the next LTS, but still easily available
[*]Key issues being solved as development progressed.
[*]Even the second LTS didn't force it as a default.
[/LIST]

Choice is key while it matures.

---

### Post by poorguy on 2020-08-21
So when Ubuntu decides to implement Wayland will it come through normal updates as an option.

From what I've read it will only work with Open source drivers as it will be up to hardware manufacturers to create proprietary drivers for Wayland.

[https://www.maketecheasier.com/what-is-wayland/](https://www.maketecheasier.com/what-is-wayland/)

---

### Post by deadflowr on 2020-08-21
> So when Ubuntu decides to implement Wayland will it come through normal updates as an option.
It's already implemented.
It's just not the default login option.

You can run it on either Ubuntu's desktop or on the Plasma desktop for Kubuntu
Should have a login option for wayland sessions.
(On Ubuntu it shows as Ubuntu on Wayland
On Kubuntu it shows as Plasma on Wayland, or Plasma Desktop On Wayland)

(On 17.04 they set it as the default option.
That gave the developers some idea of where it stands.
and so they subsequently reverted to X11 as the default after that.)

I don't no anything about recent status of nvidia drivers and wayland.
They used to just block wayland as an option when running the nvidia drivers.
I do know they've been working on it like this:
[https://wiki.gnome.org/Initiatives/Wayland/NVIDIA]("https://wiki.gnome.org/Initiatives/Wayland/NVIDIA")


As for issues here are some:
[https://github.com/mpv-player/mpv/wiki/FAQ#I_use_GNOME_Wayland_and_I_have_xyz_problem]("https://github.com/mpv-player/mpv/wiki/FAQ#I_use_GNOME_Wayland_and_I_have_xyz_problem")
[https://community.kde.org/Plasma/Wayland_Showstoppers]("https://community.kde.org/Plasma/Wayland_Showstoppers")

---

### Post by poorguy on 2020-08-21
Hello deadflowr,

I don't have any option at boot because I have auto login.

Where might I be able to find that option.

Thanks.

---

### Post by deadflowr on 2020-08-21
On Ubuntu?
For 20.04 in the login screen select your user and then look down in the lower right corner of the screen and an icon should show,
click on it to open the session select box. Make a selection and then enter your password.

You might not need to even select a user first, but I always do.

This only applies to default Ubuntu.

---

### Post by poorguy on 2020-08-21
Hello deadflowr,

OK I guess I'm going to have to switch from automatic login to login with password because I get no login screen because I don't use a password to login.

I'll see what I can do.

I'm using Ubuntu 20.04

Thanks again.

---

### Post by poorguy on 2020-08-21
Hello deadflowr,

OK changed from automatic login and now have a login screen and have to use to a password and found the Wayland option and selected Wayland logged in with my password and I have Wayland.

env | grep -i wayland

```


nelson@Dell-OptiPlex-XE:~$ env | grep -i wayland
XDG_CONFIG_DIRS=/etc/xdg/xdg-ubuntu-wayland:/etc/xdg
DESKTOP_SESSION=ubuntu-wayland
XDG_SESSION_DESKTOP=ubuntu-wayland
XDG_SESSION_TYPE=wayland
XAUTHORITY=/run/user/1000/.mutter-Xwaylandauth.D6Y3P0
WAYLAND_DISPLAY=wayland-0
XDG_DATA_DIRS=/usr/share/ubuntu-wayland:/usr/local/share/:/usr/share/:/var/lib/snapd/desktop
GDMSESSION=ubuntu-wayland
nelson@Dell-OptiPlex-XE:~$ 



```

Thanks deadflowr for your help.


[SIZE=3][B]To OP my apologies for butting in to your discussion but this thread sparked up my interest to try Wayland.
[/B][/SIZE]

---

### Post by mikewhatever on 2020-08-21
There is no option to use Wayland on Ubutu Mate 20.04. Perhaps in another 5-10 years, let us hope.

---

### Post by maglin2 on 2020-08-22
> **poorguy said:**
> 


[SIZE=3][B]To OP my apologies for butting in to your discussion but this thread sparked up my interest to try Wayland.
[/B][/SIZE]

Not a problem. This is a chat board, as opposed to a support board, after all.

---

### Post by poorguy on 2020-08-22
Thank you [COLOR=#000000]maglin2.[/COLOR]


[COLOR=#000000]So far everything is working without any problems or issues or glitches and what a [/COLOR][COLOR=#000000]performance[/COLOR][COLOR=#000000] improvement this old Core 2 Duo E7400 (2.8 GHz) dual processor in this 2013 Dell Optiplex XE with 8.0 GB DDR3 memory and [/COLOR]Intel 4 Series Integrated Graphics runs great.

):P

---

