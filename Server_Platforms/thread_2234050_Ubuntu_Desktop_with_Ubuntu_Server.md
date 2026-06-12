---
title: "Ubuntu Desktop with Ubuntu Server"
date: 2014-07-12
forum: Server Platforms
---

### Post by Tyler_Meier on 2014-07-12
I installed Ubuntu Server first, because Desktop doesn't have all the features I need, and now am trying to run ubuntu desktop. I used sudo apt-get install ubuntu-desktop, and after some google research, used the startx command to launch desktop (not sure if this is right). This failed and told me I needed to install xinit (sudo apt-get install xinit). I did this, along with [COLOR=#333333][FONT=Helvetica]sudo apt-get install unity8-desktop-session-mir, which also turned up in my research. After that, I typed in startx again, and now the screen shows mostly black with a white square in the top left corner, with what appears to be a command line prompt (username@computername) but it is unusable. Appears to be frozen. Please help, point out where I went wrong, and what I need to do differently/as well.[/FONT][/COLOR]

I am very very new to Linux in general, and so please be as plain as possible with responses :)

---

### Post by Bucky Ball on 2014-07-12
Welcome. First, install lightdm:

```
sudo apt-get install lightdm
```

Reboot.

Unless you wanted mir, you only needed:

```

sudo apt-get install unity
```

... for that command, not 'unity9-etc'. ;) 

Puzziling, as ubuntu-desktop should have installed enough to get going, including lightdm.

---

### Post by Tyler_Meier on 2014-07-12
okay that got me a desktop, for sure! Thanks! When I try to login, I get "failed to start session" though :(

Just saw your second part there, trying that now

---

### Post by Bucky Ball on 2014-07-12
Good news. Progress. ;)

When at the login screen, hit ctl+alt+F1, login, then:

```
sudo apt-get install ubuntu-session
```

 Then:
```

sudo reboot now
```

You got the login screen, not the desktop, but you'll get there.

Minimal installs are my hobby and they're not far off a server install, but I've never needed to do one of those so know what's there with a minimal, but not default with a server. We'll keep punting. :-k

---

### Post by Tyler_Meier on 2014-07-12
you sir are a hero. We punted it over the goal line! I have a desktop now :D thanks so much!

query: crtl+alt+F1 - does this always quit to command line?

---

### Post by Bucky Ball on 2014-07-12
Happy as you are! Great news.

> **Tyler_Meier said:**
> 

query: crtl+alt+F1 - does this always quit to command line?

Yep. So does replacing F1 with F2, F3 etc. They are actually called a 'tty'. ctl+alt+F7 should take you back to the desktop. Try it.

At this point, I'd advise you open a terminal and:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Report any errors. If none, you can mark the thread as solved and are welcome to start a new one with a descriptive title for any furthers support issues.

---

### Post by Tyler_Meier on 2014-07-12
I did those things, and I didnt notice any change. The gui has some sever graphical errors though, stuff duplicated onto random parts of the screen, windows fuzzing out and not closing. overall I'd say I need graphics drivers, but I'm not sure. New to this and stuff. it also looks way different overall, I used a livecd to try out ubuntu 14.04 and this looks immensely different. Not sure excatly why lol. 

Thanks for your help so far, I have to go, I'll be back on tomorrow to continue the quest!

---

### Post by Tyler_Meier on 2014-07-13
So, I ended up formatting the raid array, started over, reinstalled server, did sudo apt-get install ubuntu-dekstop, which worked this time, at least at first glance. It took a reboot to get into desktop, and then the resolution was funny, so I went into the graphics settings, changed the driver to a tested version, rebooted again, and desktop froze after prompting and accepting my password. I'm not sure where to go from here. I have SSH from my main computer so I can work with Desktop frozen, if I need to.

---

### Post by Bucky Ball on 2014-07-13
So, back to square one. Perhaps follow the steps we did yesterday and see if that helps again.

---

