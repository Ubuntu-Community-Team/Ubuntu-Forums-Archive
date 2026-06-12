---
title: "ubuntu-desktop release candidate now has unity8 as alternate  logon option"
date: 2016-10-06
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-10-06
The daily/current amd64-ubuntu-desktop.iso now has unity8 featured as a login option in the greeter.

Give it a spin.:)

You may still have to install Libertine manually or from  Ubuntu software..

Regards..

---

### Post by mc4man on 2016-10-06
There is a claim, (S. Webb),  that snaps are now supported, I've no clue as to what that's supposed to mean as I see no sign of them in ubuntu software if not already installed & no sign of installed ones in an unity8 session anywhere.

---

### Post by bregma2 on 2016-10-06
> **mc4man said:**
> There is a claim, (S. Webb),  that snaps are now supported, I've no clue as to what that's supposed to mean as I see no sign of them in ubuntu software if not already installed & no sign of installed ones in an unity8 session anywhere.

The change to surface and launch snaps [landed]("http://bazaar.launchpad.net/~indicator-applet-developers/ubuntu-app-launch/trunk.16.10/revision/253") 2016-09-13.  That means, if you're all up to date, snaps should appear in your Unity 8 Dash and launch and run.  That's what I mean by supported.

As I understand it, there is no graphical UI for discovering and installing snapped applications from Unity 8.  You need to use the command line from a terminal app, either under Unity 7 or under Unity 8.  We have a design discussion scheduled soon to determnine how best to handle discovery and installation of snapped applications under Unity 8, since it's not entirely clear if it's best to use a scope, an app, or a web application (because the underlying snappy technology has been iterating so rapidly).

---

### Post by ventrical on 2016-10-06
> **mc4man said:**
> There is a claim, (S. Webb),  that snaps are now supported, I've no clue as to what that's supposed to mean as I see no sign of them in ubuntu software if not already installed & no sign of installed ones in an unity8 session anywhere.

@mac4man

```

ventrical@ventrical-MS-7850:~$ snap login <snip>
Password: 
error: access denied (try with sudo)
ventrical@ventrical-MS-7850:~$ snap login <snip>
Password: 
error: access denied (try with sudo)
ventrical@ventrical-MS-7850:~$ sudo snap login <snip>
[sudo] password for ventrical: 
Password: 
Login successful
ventrical@ventrical-MS-7850:~$ 

```

I had to login using sudo first and then enter the password from my system.. then .. it asks for the next password which is our SSO password.

---

### Post by ventrical on 2016-10-06
> **bregma2 said:**
> The change to surface and launch snaps [landed]("http://bazaar.launchpad.net/~indicator-applet-developers/ubuntu-app-launch/trunk.16.10/revision/253") 2016-09-13.  That means, if you're all up to date, snaps should appear in your Unity 8 Dash and launch and run.  That's what I mean by supported.

As I understand it, there is no graphical UI for discovering and installing snapped applications from Unity 8.  You need to use the command line from a terminal app, either under Unity 7 or under Unity 8.  We have a design discussion scheduled soon to determnine how best to handle discovery and installation of snapped applications under Unity 8, since it's not entirely clear if it's best to use a scope, an app, or a web application (because the underlying snappy technology has been iterating so rapidly).

The snap find or snap list show nothing. There used to be a big list.

however..
```

snap install hello world

```

did install core and the app but when using 'list' or 'find' it keeps echoing  "Try "snap install hello world".

---

### Post by mc4man on 2016-10-06
> **bregma2 said:**
> The change to surface and launch snaps [landed]("http://bazaar.launchpad.net/~indicator-applet-developers/ubuntu-app-launch/trunk.16.10/revision/253") 2016-09-13.  That means, if you're all up to date, snaps should appear in your Unity 8 Dash and launch and run.  That's what I mean by supported.

As I understand it, there is no graphical UI for discovering and installing snapped applications from Unity 8.  You need to use the command line from a terminal app, either under Unity 7 or under Unity 8.  We have a design discussion scheduled soon to determnine how best to handle discovery and installation of snapped applications under Unity 8, since it's not entirely clear if it's best to use a scope, an app, or a web application (because the underlying snappy technology has been iterating so rapidly).
Ok, started over &  they will show. What's a little unexpected is if installed in a unity8 session they don't show until a log out/in. 
(- also see libertine is back though  menus of many apps remains problematic as does audio if the so-called default device isn't correct. Plus the apparent absence of pulseaudio support is a problem that should be addressed

---

### Post by ventrical on 2016-10-06
@Cariboo

whew..!

Thanks a million Hawkeye! :)


regards..

---

### Post by mc4man on 2016-10-06
I suspect one doesn't need to log out to see changes like app installs, appears you can refresh a scope by pulling it down, nonintuitive for desktop users

---

### Post by bregma2 on 2016-10-06
> **mc4man said:**
> I suspect one doesn't need to log out to see changes like app installs, appears you can refresh a scope by pulling it down, nonintuitive for desktop users

Yes, it's different.  Not intuitive as in "not what I learned before" but not hard to pick up and in no time you'll wonder just why other windows like your browser aren't refreshing when you pull at them.

---

