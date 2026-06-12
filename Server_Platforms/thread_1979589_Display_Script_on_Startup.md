---
title: "Display Script on Startup"
date: 2012-05-13
forum: Server Platforms
---

### Post by JasonMarquez on 2012-05-13
I have a script that runs on startup, but it doesn't display the terminal of it. Is there a way to get it to display instead of it running in the background?

---

### Post by ajgreeny on 2012-05-13
Instead of pointing to the script in the startup application list you will need to point to another launcher (or script maybe if using gnome 3) that starts gnome-terminal and then runs your first script in it.

In gnome 2 you could easily do it by right clicking on desktop and choosing "Create launcher" then "Application in terminal" and that allowed you to point to a script by clicking the browse button.  I have no idea if you can do the same in gnome 3, hence my comment above about another launcher script.

---

