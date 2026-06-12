---
title: "Start desktop environment automatically"
date: 2009-10-19
forum: Server Platforms
---

### Post by Markstar on 2009-10-19
Hi,
I'm trying to set up a server (I have used XP for this until now) and since I want my girlfriend to be able to control it with VNC (so she can comfortably control aMule and Transmission with a GUI), I decided to install IceWM (according to [this]("https://help.ubuntu.com/community/Installation/LowMemorySystems") it is supposed to be easy and fast (which it is)).

I have most of it working now, but there is one big issue:
How do I get to behave IceWM like a normal Ubuntu installation (meaning that when the computer starts, it loads IceWM automatically with a certain user and when I log off, it shuts down)?

Any help on this would be greatly appreciated!

---

### Post by cdenley on 2009-10-19
> **Markstar said:**
> Hi,
I'm trying to set up a server (I have used XP for this until now) and since I want my girlfriend to be able to control it with VNC (so she can comfortably control aMule and Transmission with a GUI), I decided to install IceWM (according to [this]("https://help.ubuntu.com/community/Installation/LowMemorySystems") it is supposed to be easy and fast (which it is)).

I have most of it working now, but there is one big issue:
How do I get to behave IceWM like a normal Ubuntu installation (meaning that when the computer starts, it loads IceWM automatically with a certain user and when I log off, it shuts down)?

Any help on this would be greatly appreciated!

Do you want a graphical login which will start a GUI once you authenticate, or do you want it to log you in automatically? If you're connecting remotely, there is no need to have a GUI running locally.

---

### Post by Markstar on 2009-10-19
> **cdenley said:**
> Do you want a graphical login which will start a GUI once you authenticate, or do you want it to log you in automatically? If you're connecting remotely, there is no need to have a GUI running locally.I also want to log in automatically. 

Why is there no need to run the GUI locally? I want to be able my girlfriend (and me) to be able to use Firefox and the other apps on the server. I know there are web interfaces for the individual apps (like aMule), but we want to be able to comfortably control all apps at once (instead of having to upload files via SFTP (or other file transfer protocols), open one page for aMule, then another for Transmission, etc.). With VNC, we can start firefox on the server, download a file (like a .torrent) and control all options conveniently. 

Sadly the VNC part doesn't work either at this point, see: [http://ubuntuforums.org/showthread.php?t=1295255](http://ubuntuforums.org/showthread.php?t=1295255)

---

### Post by cdenley on 2009-10-19
> **cdenley said:**
> **If you're connecting remotely**, there is no need to have a GUI running **locally**.

With VNC, you don't have to connect to a local session. You should configure your server to start your IceWM session when you connect. There is no need to have IceWM running when nobody is using it. Unless, of course, you need a GUI locally as well.

---

### Post by Markstar on 2009-10-19
> **cdenley said:**
> With VNC, you don't have to connect to a local session. You should configure your server to start your IceWM session when you connect. There is no need to have IceWM running when nobody is using it. Unless, of course, you need a GUI locally as well.I'm sorry, I don't understand. :redface:

Are you saying that I could configure VNC in a way so that IceWM starts when I connect? Sorry, I'm still an Ubuntu newbie. I would still want aMule and Transmission to run in the background...

---

### Post by cdenley on 2009-10-19
> **Markstar said:**
> I'm sorry, I don't understand. :redface:

Are you saying that I could configure VNC in a way so that IceWM starts when I connect? Sorry, I'm still an Ubuntu newbie. I would still want aMule and Transmission to run in the background...

Yes. You could also use X11 forwarding with SSH, and forget VNC. I'm not very familiar with amule or transmission. If they require a window manager in order to run "in the background", then you would need a GUI locally.

---

### Post by Markstar on 2009-10-19
> **cdenley said:**
> Yes. You could also use X11 forwarding with SSH, and forget VNC. I'm not very familiar with amule or transmission. If they require a window manager in order to run "in the background", then you would need a GUI locally.If I connect to SSH and, for example, start Firefox, a new instance will open. Yes, the calculations will be done on the server, but as soon as I close the SSH connection, this instance will also be terminated. Yes, there are Web-Front-ends for ed2k and torrents, but I explicitly do not want to open separate Windows for each program. Especially my girlfriend should be able to simply connect to the server and immediately have an overview of all the programs. Switching to Linux should make things easier, not more difficult. 

So, yes, I definitely want to start a window manager (if you tell me IceWM does not work and I should use XYZ instead, I will do that, even though I really like IceWM) right after boot that also logs on (preferably with a limited user account).

---

### Post by cdenley on 2009-10-19
> **Markstar said:**
> If I connect to SSH and, for example, start Firefox, a new instance will open. Yes, the calculations will be done on the server, but as soon as I close the SSH connection, this instance will also be terminated. Yes, there are Web-Front-ends for ed2k and torrents, but I explicitly do not want to open separate Windows for each program. Especially my girlfriend should be able to simply connect to the server and immediately have an overview of all the programs. Switching to Linux should make things easier, not more difficult. 

So, yes, I definitely want to start a window manager (if you tell me IceWM does not work and I should use XYZ instead, I will do that, even though I really like IceWM) right after boot that also logs on (preferably with a limited user account).

If you want to run graphical applications as services and have a local window manager constantly running, it is a very inefficient use of resources, but it certainly is possible.

```

sudo apt-get install gdm
gksu gdmsetup

```
General tab:
make sure "Default session" is checked
Select IceWM for default session

Security tab:
check "Enable Automatic Login"
select the appropriate user

---

### Post by Markstar on 2009-10-19
> **cdenley said:**
> If you want to run graphical applications as services and have a local window manager constantly running, it is a very inefficient use of resources, but it certainly is possible.I know it is not the most efficient way, but overall I can live with it since the only realy additional cost is added electricity - and that is marginal at best (actually the Linux setup uses more right now because I do not yet know how to modify the voltage of the CPU - thankfully, it is already reducing the multiplier on its own). The only thing I'm really concerned about is security, so I will try to find out how to make this as secure as possible (and what the actual security thread is in the first place) as soon as I got this (and VNC) working. 

```

sudo apt-get install gdm
gksu gdmsetup

```
Alright, I did that. when I enter "gksu gdmsetup" in a terminal within IceWM, the terminal displays a bunch of warnings, the last ones being:
```
** (gdmsetup:3849): DEBUG **: Getting list of sessions for user 1004
** (gdmsetup:3849): DEBUG **: Found 3 sessions for user markstar
** (gdmsetup:3849): DEBUG **: not adding session on other seat: /org/freedesktop/ConsoleKit/Session1 
** (gdmsetup:3849): DEBUG **: not adding session on other seat: /org/freedesktop/ConsoleKit/Session2 
** (gdmsetup:3849): DEBUG **: not adding session on other seat: /org/freedesktop/ConsoleKit/Session3 
** (gdmsetup:3849): WARNING **: Error calling GetValue('daemon/TimedLoginEnable'): The name org.gnome.DisplayManager was not provided by any .service files
** (gdmsetup:3849): WARNING **: Error calling GetValue('daemon/TimedLoginDelay'): The name org.gnome.DisplayManager was not provided by any .service files
** (gdmsetup:3849): WARNING **: Unable to find users: no seat-id found
```
> General tab:
make sure "Default session" is checked
Select IceWM for default session

Security tab:
check "Enable Automatic Login"
select the appropriate userDespite the warnings, a window titled "Login Screen Settings" opens, but it has not tabs, just this:
```

When the computer starts up:
O Show the screen for choosing who will log in
O Log in as < automatically
  Allow |30| seconds for anyone else to log in first
      |Unlock|   |Close|
```
The options/text is all greyed out, only "Unlock" and "Close" can be clicked. When I click on Unlock, the terminal displays this:
```
** (gdmsetup:3849): WARNING **: Failed to unlock: The name org.gnome.DisplayManager was not provided by any .service files
```:( Damn, and it looks just like what I needed!

Should I have installed something else? BTW, restarts, different users, using "sudo gksu gdmsetup" did not change anything. Arghh, so close!

---

### Post by Markstar on 2009-11-17
Just an update:
While I never got it to work with IceWM, installing xfce4 and using gdm worked flawlessly. Too bad, I really liked IceWM, but there were just to many things that did not work correctly (aMule crashed after a few hours when it was not focussed, the column and window sizes had to be set every time, etc.).

Cheers

---

### Post by defaria on 2009-11-20
How did you get past the gdmsetup problem?

---

### Post by Markstar on 2009-11-21
> **defaria said:**
> How did you get past the gdmsetup problem?After I logged in xfce4, I simply ran it again and while I couldn't unlock the window the first time, I ran it a second time and then it worked. 

Clearly there is a bug somewhere and it is not the only one. So far I cannot understand why people say Linux is more stable and more efficient. My XP server ran for years - it ran stable and very fast. Since I've switched to Ubuntu I had several issues with it that required a restart or a new login. But that's not the issue here, so I guess I should just let it go. ;)

---

### Post by cracker on 2010-04-14
I'm having exactly the same problem. The options are all grayed out and the 'unlock' button does nothing when using IceWM. I also can't figure out how to change these settings manually, the gdm configuration is very confusing. Any help at all would be appreciated.

---

