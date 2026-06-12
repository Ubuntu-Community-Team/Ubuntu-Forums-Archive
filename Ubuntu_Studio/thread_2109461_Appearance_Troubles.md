---
title: "Appearance Troubles"
date: 2013-01-27
forum: Ubuntu Studio
---

### Post by AcousticDJ on 2013-01-27
[ATTACH]230717[/ATTACH]
When running a program in Ubuntu Studio, the windows always appear like this.
I cannot minimize them, nor resize them, and they cannot be moved. The windows can't be closed unless the program has a 'quit' option or I kill it using Task Manager.

Can I fix this, or should I update the OS?

---

### Post by jejeman on 2013-01-27
Not sure what I see in this picture. Are you missing the title line? Did you try to move window down? Use alt+left click if needed.

---

### Post by AcousticDJ on 2013-01-27
> **jejeman said:**
> Not sure what I see in this picture. Are you missing the title line? Did you try to move window down? Use alt+left click if needed.
The title line is missing, and the window cannot be moved, even with alt+left click.

---

### Post by snowyplover on 2013-01-29
I was having a similar problem. Windows had no title bar and would have their menu bar glued into the task bar. Your screenshot appears to show that your window manager still thinks it has four workspaces, but mine only had one.

My solution was to clear the window manager session cache:

Open Settings -> Settings manager
Click on "Session and Startup"
Click on "Session" tab
Click on "Clear saved sessions"

It's not clear all of what is affected by doing this. My file manager had some settings returned to defaults, but I'm not sure if that happened because of my solution or the original problem.

On my system, it was clear that the window manager kept loading a session that I thought I had gotten rid of -- that is how I came up with this solution. I don't know if that is the case for you. However, if it is this part of the window manager that causes this particular problem. then maybe the solution will work even if you haven't been explicitly saving your sessions.

I hope this helps.

---

### Post by AcousticDJ on 2013-02-09
> **snowyplover said:**
> I was having a similar problem. Windows had no title bar and would have their menu bar glued into the task bar. Your screenshot appears to show that your window manager still thinks it has four workspaces, but mine only had one.

My solution was to clear the window manager session cache:

Open Settings -> Settings manager
Click on "Session and Startup"
Click on "Session" tab
Click on "Clear saved sessions"

It's not clear all of what is affected by doing this. My file manager had some settings returned to defaults, but I'm not sure if that happened because of my solution or the original problem.

On my system, it was clear that the window manager kept loading a session that I thought I had gotten rid of -- that is how I came up with this solution. I don't know if that is the case for you. However, if it is this part of the window manager that causes this particular problem. then maybe the solution will work even if you haven't been explicitly saving your sessions.

I hope this helps.
I can't find anything that says to "Clear saved sessions".

---

