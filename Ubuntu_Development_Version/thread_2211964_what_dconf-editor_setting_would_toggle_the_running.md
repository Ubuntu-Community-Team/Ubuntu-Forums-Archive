---
title: "what dconf-editor setting would toggle the running icons from the left pane"
date: 2014-03-18
forum: Ubuntu Development Version
---

### Post by gmoore777 on 2014-03-18
In Ubuntu 14.04 TrustyTahr, the available apps are on the left side pane.
The running apps are there as well.

Let's say I click on my Firefox icon, Firefox appears, but
I really did not mean to work on Firefox.

I would like to click that very same icon, so that Firefox
iconifies/minimizes again.
I do NOT want to move my mouse over to Firefox, and click
the minimize button.
(this functionality is in the Lubuntu desktop by default.)

What is that functionality called in the dconf-editor?
or,
What other application/configuration tool, would I run to get
this accomplished?

---

### Post by ajgreeny on 2014-03-18
Which particular icons on the Lubuntu system are you clicking on to do this? It is not the behaviour I have on my Lubuntu 14.04.

If I open a program in Lubuntu either with the icons I have added to the desktop, or more usually using the application launch bar I use at the left side of thenscreen, a second click just opens another instance of that program, it does not minimise it to the panel.

I believe the behaviour I am seeing is the default as I have not made any changes to that in any way.

---

### Post by gmoore777 on 2014-03-18
In Lubuntu (TrustyTahr 14.04), if Firefox is already running, it's icon is showing up in the "Task" bar, which
would, by default, be at the bottom, middle of that "panel" that runs all along the bottom.

If you then click that "running" application by clicking the icon in the Task bar, 
it will either toggle the maximize or minimize.

That's the behaviour I have on two machines that I just built out
in the last week.
I want to mimic this behaviour in the Ubuntu desktop(TrustyTahr 14.04).

I'm not talking about the application launch bar, which is to the left and
bottom. That will "start" an application, and that application will now
show up in the "Task" bar.

---

### Post by grahammechanical on 2014-03-18
This should interest you

[http://www.omgubuntu.co.uk/2014/03/minimize-click-launcher-option-ubuntu-14-04](http://www.omgubuntu.co.uk/2014/03/minimize-click-launcher-option-ubuntu-14-04)

Regards.

---

### Post by mc4man on 2014-03-18
If the official patch, (not yet been added to 14.04),  is just on 1 window & users want to extend a bit then there would be this ppa, how it acts is described on page - 
[https://launchpad.net/~zxcq14/+archive/minimize-unity-7](https://launchpad.net/~zxcq14/+archive/minimize-unity-7)

Edit: released in new unity package, set in cssm > unity >  launcher

---

### Post by ajgreeny on 2014-03-19
> **gmoore777 said:**
> In Lubuntu (TrustyTahr 14.04), if Firefox is already running, it's icon is showing up in the "Task" bar, which
would, by default, be at the bottom, middle of that "panel" that runs all along the bottom.

If you then click that "running" application by clicking the icon in the Task bar, 
it will either toggle the maximize or minimize.

That's the behaviour I have on two machines that I just built out
in the last week.
I want to mimic this behaviour in the Ubuntu desktop(TrustyTahr 14.04).

I'm not talking about the application launch bar, which is to the left and
bottom. That will "start" an application, and that application will now
show up in the "Task" bar.
Ok, I understand now what you mean.  What confused me was your suggestion that the icon was the one you used to start the application in the first place, or that is what I thought you meant.

You are, however, talking about the "Window buttons" which show in the taskbar/panel of most DEs, but not unity, when an application is open.

Good to know that the option is back, even though I don't personally think it is needed in unity, which I have steered away from in the past, but am now looking at more seriously as I now have hardware that can use it properly.

---

### Post by bapoumba on 2014-03-21
Moved to Ubuntu +1.

---

### Post by gmoore777 on 2014-03-31
Several solutions here, especially one provided by fossfreedom at:
[http://askubuntu.com/questions/36433/why-cant-i-use-the-unity-launcher-icon-to-minimize-applications-windows/436542#436542](http://askubuntu.com/questions/36433/why-cant-i-use-the-unity-launcher-icon-to-minimize-applications-windows/436542#436542)

The one solution I just tried:
gsettings set org.compiz.unityshell:/org/compiz/profiles/unity/plugins/unityshell/ launcher-minimize-window true
gsettings set org.compiz.unityshell:/org/compiz/profiles/unity/plugins/unityshell/ launcher-minimize-window false

Very nice!

---

