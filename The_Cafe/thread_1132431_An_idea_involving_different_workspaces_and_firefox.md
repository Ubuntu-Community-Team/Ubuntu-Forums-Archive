---
title: "An idea involving different workspaces and firefox tabs when it's closed/re-opened."
date: 2009-04-21
forum: The Cafe
---

### Post by diablo75 on 2009-04-21
A client of mine had an interesting question.  He wanted to know if there were a way for Firefox to remember the tabs that you have open when you close a window (as is the case now) except that it remembers different sets of tabs depending upon which workspace you happen to be sitting on.  He's the kind of user who literally has 12 individually labeled workspaces for different types of work he does and would like Firefox to help make things easier by remembering different workspaces.  Perhaps a script/plugin exists that could do this?

---

### Post by smartboyathome on 2009-04-21
> **diablo75 said:**
> A client of mine had an interesting question.  He wanted to know if there were a way for Firefox to remember the tabs that you have open when you close a window (as is the case now) except that it remembers different sets of tabs depending upon which workspace you happen to be sitting on.  He's the kind of user who literally has 12 individually labeled workspaces for different types of work he does and would like Firefox to help make things easier by remembering different workspaces.  Perhaps a script/plugin exists that could do this?

It is possible, but it would require Firefox being used as a different user on each workspace. Either that or a different profile for each workspace, but then you have to choose the correct profile for each one.

The user option (easier in my opinion) could be done using the gksu command. Running 'gksu --user <insert user here> firefox' would give you firefox running as the selected user.

---

### Post by kpatz on 2009-04-21
Set up a profile for each workspace, and then launch Firefox in each workspace with the command: **firefox -P <profile>** specifying the profile for the corresponding workspace.

---

### Post by lovinglinux on 2009-04-21
You could try using compiz "Place Windows" plugin. Check the "Windows with fixed viewport" under the "Fixed Window Placement" tab. There are several ways of selecting a specific window with this tool. If you don't know the code, there is a grabber that captures the window class, title, name, id, role or type. For example, for this page, the best option would be "title=Ubuntu Forums - Reply to Topic - Mozilla Firefox".

---

### Post by MaxIBoy on 2009-04-21
You could create a firefox plugin for that, if you knew XUL (Java would help here too.) Just have the plugin create a dotfile in the user's home directory, with URLs representing the tabs of each window. Then, use some kind of magic to tell which is the current workspace (I know it's possible because other applications do similar things, I just don't know how it's done.) Have the plugin kick in whenever firefox starts a new window.

---

