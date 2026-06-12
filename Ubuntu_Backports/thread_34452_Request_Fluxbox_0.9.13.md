---
title: "Request: Fluxbox 0.9.13"
date: 2005-05-14
forum: Ubuntu Backports
---

### Post by Chrysaor on 2005-05-14
Hi. Fluxbox 0.9.13 released a few days ago, any chance we can get a backport? Ubuntu repository got 0.9.11 i believe.

[http://fluxbox.sourceforge.net/version-0.9.php](http://fluxbox.sourceforge.net/version-0.9.php)

Here is the changelog:
> News in 0.9.13:

    * Massive speed- and memory- improvements
    * Added new Buttons for the Titlebar:
        - Shade - just like the "Stick"-button
          Style resources:
            window.shade.pixmap, window.shade.unfocus.pixmap, window.shade.pressed.pixmap
            window.unshade.pixmap, window.unshade.unfocus.pixmap, window.unshade.pressed.pixmap
            etc.
        - MenuIcon - click on it provides the windowmenu, if the app
          contains a pixmap (gvim, konqueror etc etc) the pixmap is displayed, a
          little menu otherwise. 
          Style resources:
            window.menuicon.pixmap, window.menuicon.unfocus.pixmap
            window.menuicon.pressed.pixmap
            etc.
        Example ~/.fluxbox/init - entry:
          session.titlebar.left: MenuIcon Stick
          session.titlebar.right: Shade Minimize Maximize Close
    * Added more Key Actions to TextBoxes
        - Control + LeftArrow  - Moves cursor to the left direction, up to next word.
        - Control + RightArrow - to the right direction.
        - Control + BackSpace  - Removes everything from the cursor left side, up to next left word.
        - Control + Delete     - like above but removes to the right direction.
    * Added some style resources:
        - menu.hilite.submenu.pixmap:    
        - menu.hilite.selected.pixmap:   
        - menu.hilite.unselected.pixmap: 
    * Added new Iconbar Modes:
        - NoIcons   - all but iconified windows
        - WorkspaceNoIcons - all but iconified windows on the current Workspace
    * Added -screen <"all"|int[,int]> :
       $> fluxbox -screen 0,2      will run fluxbox on 0.0 and 0.2 so
                                   one can run any other wm on 0.1.
       $> fluxbox -screen all      default, fluxbox manages all screens
    * fluxbox-generate_menu now can add pixmaps to menu entries

Bug fixes:
    * Mutiple keyboard layout (#1160244, #1099704, #1094107)
    * ArrangeWindows (#1086673, 
    * Inconsistent behavior of Java dialogs (#1157361)
    * fbrun segfault (#1188690)
    * ShowDesktop (#1020399)
    * 64bit issues (#1107213, #1105041)

---

### Post by bored2k on 2005-05-14
[QUOTE=Chrysaor]Hi. Fluxbox 0.9.13 released a few days ago, any chance we can get a backport? Ubuntu repository got 0.9.11 i believe.

[http://fluxbox.sourceforge.net/version-0.9.php](http://fluxbox.sourceforge.net/version-0.9.php)

Here is the changelog:[/QUOTE]
  * Massive speed- and memory- improvements

Even more ?! I gotta try that out .

---

### Post by Technoviking on 2005-05-15
Only 0.9.12 in Ubuntu Breezy or Sid dist pools. I will keep my eye open for it.

Mike

---

### Post by darkaudit on 2005-05-15
Fluxbox 0.9.12 from Sid depends on libfontconfig1 (>= 2.3.0), and Hoary has 2.2.3-4ubuntu7. No plans to update it. Sigh.

---

### Post by Moobert on 2005-05-16
[http://logicvortex.net/debian/fluxbox/](http://logicvortex.net/debian/fluxbox/)

any use to you ? probably needs alot of ubuntu tweaking

---

### Post by darkaudit on 2005-05-16
I posted the question about libfontconfig1 on the blog. I doubt that we'll see anything new for Ubuntu until Breezy is released.

---

### Post by Lowe on 2005-05-17
[QUOTE=darkaudit]Fluxbox 0.9.12 from Sid depends on libfontconfig1 (>= 2.3.0), and Hoary has 2.2.3-4ubuntu7. No plans to update it. Sigh.[/QUOTE]

That annoyed me quite a bit, because adesklets requires the new version aswell.

Was looking forward to using the new flux aswell. =(

---

### Post by jdong on 2005-05-18
Hmm, I'll play with it a bit, and see if I can apply 0.9.12 patches to 0.9.13.

---

### Post by jdong on 2005-05-18
Ok, I have it backported and uploaded to staging, but do test it out --

There was a svnversion() function not defined, and I had to stick it in an h-file myself. Test all aspects of Fluxbox.

---

### Post by darkaudit on 2005-05-18
[QUOTE=jdong]Ok, I have it backported and uploaded to staging, but do test it out --

There was a svnversion() function not defined, and I had to stick it in an h-file myself. Test all aspects of Fluxbox.[/QUOTE]Happy dance! Happy dance! Will do.

---

### Post by UrbanSlayer on 2005-05-26
Sorry to resurrect an oldish thread, but - has this version of Fluxbox got Xinerama support compiled in?  If not, im assuming that the libraries that I would need to use/compile it are in the backports repo?

Thanks :)

---

