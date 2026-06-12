---
title: "Empty Trash"
date: 2009-12-31
forum: Security
---

### Post by Dad1985 on 2009-12-31
Where can I find the code or module which runs the "Empty Trash" routine.  Ive been looking and cant seem to find it.  Thank you.

---

### Post by fibercode on 2009-12-31
The trash that you see on the desktop is actually a gnome applet. You can find it here:

/usr/lib/gnome-applets/trashapplet

It is a compiled code and it does the "Empty Trash" routine.

I am not sure if it takes any parameters so that you can execute it from command line though.

---

### Post by Dad1985 on 2010-01-01
> **fibercode said:**
> The trash that you see on the desktop is actually a gnome applet. You can find it here:

/usr/lib/gnome-applets/trashapplet

It is a compiled code and it does the "Empty Trash" routine.

I am not sure if it takes any parameters so that you can execute it from command line though.

well I figure it likely only uses rm() to delete the files.  I wanted to modify it to use srm() instead.

---

### Post by BkkBonanza on 2010-01-01
From the command line,

srm -lrz ~/.local/share/Trash/*/*

I haven't seen a method yet to replace the Nautilus empty trash button.

I have a secure delete right menu item which I created with the Nautilus Actions Configuration in menu Systems, Prefs. This works for regular files and I can get it to show up for the trash, but so far I have had no luck getting it to actually work for the trash. Right now, probably making a desktop icon or panel launcher applet for this command may work best.

**[COLOR="Red"]Update:[/COLOR]** Ok. I did find a way to make this work. Use the menu Systems, Prefs, Nautilus Actions Config to add a new action that runs a script. I found that using the srm command directly did not work for the trash.

Create a script with these two lines, 
#!/bin/bash
srm -lrz ~/.local/share/Trash/*/*

Then call that script in your Action. Give the action a Title like "Secure Empty Trash". For conditions set to show for Both and Multiple. And then the trick now is the select "Advanced Conditions" and add a scheme called "trash" and checkmark it but not other schemes. This makes it only show up for Trash files. Save this.

Now go open your trash and right click any item to see your Secure Empty option. I have yet to find a way to add/replace the toolbar button. Maybe possible though.

I also experimented with creating a custom app launcher panel applet for the script. This worked as well for a one-click solution.

---

### Post by BkkBonanza on 2010-01-01
Here is an improved version of my script.
This one will empty all the trash if no file supplied but will only secure delete certain files if they are passed in. 
Use this with the Nautilus Action by setting the parm field to "%m" (no quotes).

```
#!/bin/bash
if [ $# -eq 0 ]; then
  srm -lrz ~/.local/share/Trash/*/*
else
  for f in "$@"; 
  do
    srm -lrz ~/.local/share/Trash/files/"$f"
    srm -lrz ~/.local/share/Trash/info/"$f".trashinfo
  done
fi

```

So if you select files in the trash you can right click to secure delete them, but if you select "Secure Empty" from the files menu then it does them all.

---

### Post by Dad1985 on 2010-01-01
Thank you for posting the script and other info.  I will certainly use it.  Though my intention was to build a security patch for ubuntu user who wanted a more secure system.

---

### Post by BkkBonanza on 2010-01-02
That would be a good idea. An option in Nautilus for selecting secure delete would be nice. You would have to go to the Nautilus source code for that presumably. A good way would be to enable customizing the Empty Trash function through gconf editor settings. That way people could customize it with any method they prefer and it may be easier to get accepted into the standard builds. I was looking for settings in there for that but didn't see any.

---

