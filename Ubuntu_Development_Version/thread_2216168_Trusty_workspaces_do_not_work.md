---
title: "Trusty workspaces do not work"
date: 2014-04-10
forum: Ubuntu Development Version
---

### Post by cwmoser on 2014-04-10
Installed the 10April2014 beta, then Gnome Session Fallback.

I note when I enable 4 Workspaces and then click on another workspace
that the display goes to that workspace but there is no way to return
to Workspace #1.

Carl

---

### Post by pfeiffep on 2014-04-10
> **cwmoser said:**
> Installed the 10April2014 beta, then Gnome Session Fallback.

I note when I enable 4 Workspaces and then click on another workspace
that the display goes to that workspace but there is no way to return
to Workspace #1.

CarlNot a solution, but a comparison since my workspaces function normally.

```
pfeiffep@Pete-dell:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Trusty Tahr (development branch)
Release:    14.04
Codename:    trusty

pfeiffep@Pete-dell:~$ uname -a
Linux Pete-dell 3.13.0-22-generic #44-Ubuntu SMP Wed Apr 2 20:04:41 UTC 2014 i686 i686 i686 GNU/Linux

```

flashback version 1:3.8.0-1

---

### Post by grahammechanical on 2014-04-10
Did you really install gnome-session-fallback? I think that it is gnome-session-flashback that should be installed in Trusty Tahr. That is what I installed, anyway.

I have just tested Gnome Flashback (Compiz) and Gnome Flashback (Metacity) and I can easily switch between workspaces by clicking the workspace icons. I have 4 workspaces set up.

Regards.

---

### Post by cwmoser on 2014-04-10
Yes, I stand correction -- its flashback.

I issued this to enable Gnome:
**sudo apt-get install gnome-session-flashback**

The default is one Workspace.  
When I set the preference to 4 Workspaces, the little icons in the lower right appear 
one for each Workspace.  But, when I click on the icon for Workspace 2, 3, or 4, it
takes me to a Desktop with no Workspace icons in lower right.  No way to get back
to Workspace 1.

Carl

---

### Post by mc4man on 2014-04-10
I don't have it (gnome-panel) installed atm but if I recollect correctly - if using the compiz version you need to set the workspaces in ccsm > General options > Desktop size
(ccsm = compizconfig-settings-manager

Otherwise if setting thru the panel's Ws preferences you go to some place of no return..

---

### Post by pfeiffep on 2014-04-10
> **cwmoser said:**
> Yes, I stand correction -- its flashback.

I issued this to enable Gnome:
**sudo apt-get install gnome-session-flashback**

The default is one Workspace.  
When I set the preference to 4 Workspaces, the little icons in the lower right appear 
one for each Workspace.  But, when I click on the icon for Workspace 2, 3, or 4, it
takes me to a Desktop with no Workspace icons in lower right.  No way to get back
to Workspace 1.

Carl

When I installed flash back I used Synaptic which also installed a few dependencies.

---

### Post by grahammechanical on 2014-04-10
Just a thought. How did you change default setting of 1 workspace to more than 1 workspace?

In Flashback (Metacity) we right click the workspace icon and select Preferences and then increase or decrease the number of workspaces in the dialog box that appears.

We can use that method in Flashback (Compiz) but I would not advise it. I experimented with that when I first installed gnome-session-flashback a few months ago.

In flashback (Compiz) we use CCSM but be careful. Any changes we make to the Compiz settings will be reflected in the Unity session. I would not advise using CCSM to make adjustments in Flashback (Metacity) either. We have here two different software codes, Compiz and Metacity.

Regards.

---

### Post by grumblebum2 on 2014-04-10
These are settings needed when using the flashback compiz session. The ccsm settings are up to you.
Set the workspace switcher applet to 1 workspace and the changes made in ccsm will be picked up by the switcher in real time.
The reason is because with compiz you really only have 1 desktop regardless of the amount of virtual desktops you create in ccsm.

At the moment the compiz configs are behaving independently for the ubuntu/compiz and flashback/compiz sessions
but have seen strange things in the past.

[COLOR="#FF0000"]***NOTE:[/COLOR] If you open ccsm to the "desktop size" tab again your virtual workspaces will revert to 1 and need to be reset.

---

### Post by cwmoser on 2014-04-11
CCSM was not installed in my installation of Trusty.
I had set the preferences to 4 workspaces by right-clicking
on the Workspace icon.

BUT, I then installed CCSM and set it as described above:
CCSM > General > General Options > Desktop Size
and setting Horizontal Virtual Size = 4

---

