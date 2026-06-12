---
title: "wierd gedit bug"
date: 2012-09-18
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mc4man on 2012-09-18
Seen here, d checked on a live session though because it's an  X Window System error maybe hardware is a factor.
Easy to see - open any .desktop or .desktop type file in gedit from a terminal (for Ex. a .override file is a .desktop type file
Then open any text file from a r.click > open with text editor (in nautilus

Ex.
```
gedit /usr/share/applications/nautilus.desktop
```
Leaving it open then  find & open any text file from r. click

edit
variation of
Alt+f2, run the gedit command on any .desktop file, r.click on any text file, same deal

---

### Post by VinDSL on 2012-09-18
Interesting!

```
(gedit:7499): Gdk-ERROR **: The program 'gedit' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 251 error_code 3 request_code 18 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Trace/breakpoint trap

```

---

### Post by dino99 on 2012-09-18
That issue has been around for ages, maybe it will be fixed some days (pray & wait)  ;)

---

### Post by mc4man on 2012-09-18
> **dino99 said:**
> That issue has been around for ages, maybe it will be fixed some days (pray & wait)  ;)

Never saw before 12.10 here

---

### Post by jerrylamos on 2012-09-18
Is this the same bug I see:

1. In Nautilus, select a file and Display.  Uses gedit.

2. In terminal, do a gedit any_file

I get:

3. The display file disappears

4. The terminal gedit never appears.

Now if I use pcmanfm, same thing plus in addition a /var/crash/ report.

If I use leafpad in the terminal session, no problem.

Looking at Ubuntu as a black box, appears the bug occurs when a second tab would be opening in the Display window.

My bug is #1051976 which Launchpad reports:

"Remember, this bug report is a duplicate of a private bug.
Comment here only if you think the duplicate status is wrong." 

Maybe that makes sense to you, but how can I tell if it is a duplicate since Launchpad tells me:

"Bug 1047985 cannot be found" 

since it is "private".

Isn't "Launchpad" so user friendly.  Essential message, "don't bother us about your problem".

O.K., I have a workaround, I just remember to use leafpad.  BTW, on 12.10 B1 I've got: gedit, leafpad, "Files", pcmanfm, Firefox, Opera, ...

---

### Post by mc4man on 2012-09-18
> **jerrylamos said:**
> Is this the same bug I see:

1. In Nautilus, select a file and Display.  Uses gedit.

2. In terminal, do a gedit any_file

I get:

3. The display file disappears

4. The terminal gedit never appears.


Yep - another variation
You probably are getting a crash when doing thru nautilus, not every crash produces a popup but will create a .crash in /var/crash
(I clean the dir. out every day or so or whenever I feel like
```
sudo rm /var/crash/*.*
```

As far as LP, apport crash reports are usually or always filed as private.

---

### Post by jbicha on 2012-09-18
Jerry, I made that bug public now. Crash reports are private by default because there's a chance they could include sensitive info in the crash log. Personally, I think that risk is over-stated and the annoyance of average people not being able to see bugs (especially duplicated bugs) is worse, but maybe I don't know what I'm talking about...

---

### Post by Stinger on 2012-09-18
> **jbicha said:**
> Jerry, I made that bug public now. Crash reports are private by default because there's a chance they could include sensitive info in the crash log. Personally, I think that risk is over-stated and the annoyance of average people not being able to see bugs (especially duplicated bugs) is worse, but maybe I don't know what I'm talking about...
I think you know exactly what you are talking about :D 
I asked launchpad about this odd behavior Question [#208520]("https://answers.launchpad.net/launchpad/+question/208520") and they linked me to this [bug #764414]("https://bugs.launchpad.net/ubuntu/+source/apport/+bug/764414"), it is not marked as solved yet, so I guess we'll just have to put up with this odd behavior until it is.

---

### Post by jerrylamos on 2012-09-18
> **jbicha said:**
> Jerry, I made that bug public now. Crash reports are private by default because there's a chance they could include sensitive info in the crash log. On these test systems I don't have sensitive info.  For release for the general public perhaps the bug should be marked private.  

If I remember, when I generate a launchpad bug and happen to look, I mark it public.

---

### Post by mc4man on 2012-09-27
fixed upstream - should be in a gtk update at some point
[https://bugzilla.gnome.org/show_bug.cgi?id=684938](https://bugzilla.gnome.org/show_bug.cgi?id=684938)

---

### Post by VinDSL on 2012-09-27
> **mc4man said:**
> fixed upstream - should be in a gtk update at some point
[https://bugzilla.gnome.org/show_bug.cgi?id=684938](https://bugzilla.gnome.org/show_bug.cgi?id=684938)


Good to hear!

I'm always looking for errors/warnings, when I'm running in CLI.

And, while gedit works fine, I'm going weary of all the false flag dialogs that I've been getting lately.

---

