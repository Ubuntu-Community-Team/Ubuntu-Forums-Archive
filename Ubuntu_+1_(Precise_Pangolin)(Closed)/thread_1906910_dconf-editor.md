---
title: "dconf-editor"
date: 2012-01-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by 3vi1 on 2012-01-10
Regulars will recall that I'm no fan of the MS-Windows-registry-inspired dconf system.  Some others here think it's great, and I'm okay with them being wrong.  However I just had to share last nights experience... because as frustrating as it was, it's kind of funny in an ironic way.

So, I'm configuring a new laptop install:  I set up a bunch of keyboard shortcuts, tweeked a bunch of app settings in dconf, etc...  and I decide I need one more thing to be added to the allowed indicators settings.  So, I open dconf-editor and go hunting for the setting (hint: ctrl-F almost works sometimes, but other times appears to do nothing).

Now when I think I see it, and I click on the field to edit it.... dconf-editor disappears.

Odd.

I check the other virtual desktops...  it's not there.  I go back to my command window, and the prompt has never returned.  So, I ctrl-c that @#^#* and run it again....

The window doesn't appear.  The command line's still waiting for it to end... but the window won't appear.

Log out/in.  No change.  Reboot.  No change.  The command line acts like it's running, but alt-tab doesn't show any entry for it when switching desktop windows.

Here's where it gets funny:  So, apparently... the dconf-editor thought I made some change to the editor window and now the window isn't valid and can't be displayed... and dconf-editor saved that change... into... dconf.

How to fix?  That's easy:  delete/rename dconf... and lose every setting from every app that I had previously tweaked.  *sigh*

I renamed it, and now dconf-editor runs fine.

Now, even if you disagreed with my dconf rant last year, you gotta admit:  That's pretty screwed up.

--------------------

HOW TO RECREATE THE PROBLEM:  I actually figured out how to recreate this issue so that I can file a bug against it today (if someone hasn't already).  The bad thing is IT'S INCREDIBLY EASY TO SCREW UP DCONF IN THIS MANNER.  I'm posting this here so you guys can avoid it.  If you try this, be sure to copy your .config/dconf directory first so that you can copy it back to fix the problem.  In fact, go backup that directory now, regardless of if you try this.  You'll thank me later.

#1) Either have a screen that is 1280 pixels or less of width, or set your resolution down.  Apparently the authors of dconf-editor work exclusively in 1920 and therefore haven't run into this.

#2)  Open dconf-editor, go to desktop/unity/launcher (I missed "panel" by one click when I stumbled upon this) and then click on "favorites" in the right pane.  This will "automagically" resize your dconf-editor window to try to fit all of the favorites.  BOOM.  On my CR-48, this width is invalid and kills the window (but not the app).  In the background, dconf-editor saves this new size (even if you Ctrl-C out) somewhere into its own database (which you'll find impossible to easily edit with a broken dconf-editor).

Some days you eat the bear...

EDIT:  Note - I'm not sure why the forum admins felt it necessary to change the title of my post from "dconf-editaaauuurrrghhhh" to "dconf-editor", but it really spoils the joke and the original is not offensive/inappropriate.  It's a very apt title, given the time I spent debugging the problem.

---

### Post by ventrical on 2012-01-10
Eating bear and eating crow comes all in a days work I guess :)

 thanks for sharing that . :)

---

### Post by lucazade on 2012-01-10
really weird issue..
dconf-editor also suffers of a broken gtk3 treeview widget.. when you click in the right pane of dconf-editor the list is resized to show all the options. These options instead should be normally visible without any user interaction.

---

### Post by drs305 on 2012-01-10
Thanks for sharing your experiences with dconf. 

You mentioned tweaking dconf. If you find yourself installing more than once a release, or install on multiple systems, it may save you time to just set up a script.

I won't include the entire script, but here are some of the dconf settings I set with a single command:

> 
	echo "Modifying dconf settings."
		# nautilus settings
			gsettings set org.gnome.nautilus.preferences show-hidden-files "true"
			gsettings set org.gnome.nautilus.preferences default-folder-viewer "list-view"
			gsettings set org.gnome.nautilus.preferences enable-delete "true"
			gsettings set org.gnome.nautilus.preferences always-use-location-entry "true"
		# gedit settings
			gsettings set org.gnome.gedit.preferences.editor auto-save "false"
			gsettings set org.gnome.gedit.preferences.editor create-backup-copy "false"
			gsettings set org.gnome.gedit.preferences.editor display-line-numbers "true"
			gsettings set org.gnome.gedit.preferences.ui max-recents "25"
			gsettings set org.gnome.gedit.state.window size  "(1050,500)"
			gsettings set org.gnome.gedit.preferences.ui statusbar-visible "true"
			gsettings set org.gnome.gedit.preferences.print print-header 'false'
		# Date/time panel format
			gsettings set com.canonical.indicator.datetime custom-time-format '   %a    %d %b   %l:%M   ' # format - "man date"
			gsettings set com.canonical.indicator.datetime show-clock
			gsettings set com.canonical.indicator.datetime show-date
			gsettings set com.canonical.indicator.datetime show-day

		# Misc			
			gsettings set org.gnome.desktop.screensaver lock-enabled 'false'  
			gsettings set org.gnome.desktop.sound event-sounds 'false'
		# HERE IT IS::: Disable resume password [http://ubuntuforums.org/showthread.php?p=11355285#post11355285](http://ubuntuforums.org/showthread.php?p=11355285#post11355285)
			# gsettings set org.gnome.desktop.lockdown disable-lock-screen 'true'  

		# dconf-editor window
			gsettings set ca.desrt.dconf-editor.Settings width 800
		# Eliminate shutdown confirmation.
			# X	gsettings set com.canonical.indicator.session suppress-logout-restart-shutdown "true"


# Launchers:  dconf-editor desktop.unity.launcher
# Export from old setup
			gsettings get com.canonical.Unity.Launcher favorites > /path/filename
# Import launchers from file if previously saved or backed up from an installation.
			launchersettings=`cat /path/filename`
			gsettings set com.canonical.Unity.Launcher favorites "$launchersettings"



---

### Post by MacUntu on 2012-01-10
Or just backup your dconf file (like you would backup your .gconf dir). ;)

---

### Post by jbicha on 2012-01-10
I'm also experiencing dconf-editor crashes. 3vi1, could you go ahead and report your bug?

---

### Post by MacUntu on 2012-01-10
> **3vi1 said:**
> MS-Windows-registry-inspired dconf system.
It's a database storing settings. I don't know what this got to do with the Windows registry. Also, it doesn't store /etc in that file, does it? ;)

> **3vi1 said:**
> which you'll find impossible to easily edit with a broken dconf-editor
```
gsettings set ca.desrt.dconf-editor.Settings height 500
gsettings set ca.desrt.dconf-editor.Settings width 500
gsettings set ca.desrt.dconf-editor.Settings maximized false
```

BOOM - much ado about nothing. Report a bug, wait for a fix, continue with testing the **ALPHA** of Ubuntu+1.

Btw, that's also how you can easily reproduce the bug - just set the width to something high (9000 worked for me).

---

### Post by Mr. Picklesworth on 2012-01-10
Sounds like you want to use dconf's key files feature. Try the [System Administrator Guide]("http://live.gnome.org/dconf/SystemAdministrators").

You'll also find man gsettings quite enlightening. It's quite a useful little command.

And, yes, dconf-editor is ugly at the moment. I doubt many people would think otherwise.

---

### Post by kansasnoob on 2012-01-10
> **drs305 said:**
> Thanks for sharing your experiences with dconf. 

You mentioned tweaking dconf. If you find yourself installing more than once a release, or install on multiple systems, it may save you time to just set up a script.

I won't include the entire script, but here are some of the dconf settings I set with a single command:

+1!

Instead of using an actual script I still like just "stringing" things with && ............. old habits are hard to break, but I find things quite tolerable - both with Unity and classic/no-effects.

I'm curious how much more of gconf will be killed in Precise. Will gconf go away all together soon?

---

### Post by 3vi1 on 2012-01-10
Thanks for the feedback guys.  I did file a bug this morning, so hopefully it will get resolved in the next revision.

And thanks to MacUntu for posting the exact offending keys (I didn't have a chance to go looking through every part of the tree for them yet).  Now that we know the keys, we can poke them back down to smaller values from a CLI in the event anyone runs into this.

Thanks for the link to the systems admin guide too, Mr. Picklesworth.  That may come in handy.  Though, to be honest, I feel it does reinforce one of the benefits of plain text configuration:  You don't have to go find and read new documentation to learn new tools to fix simple values when something goes wrong.

Later all!

---

