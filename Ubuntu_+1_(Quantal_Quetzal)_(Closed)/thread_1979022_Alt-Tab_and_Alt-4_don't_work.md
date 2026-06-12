---
title: "Alt-Tab and Alt-4 don't work"
date: 2012-05-12
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by jerrylamos on 2012-05-12
Alt-Tab and Alt-F4 in Unity-2D not working after today's update anyone remember where these are defined as switch window and close window?

Thanks, 

Jerry

---

### Post by jerrylamos on 2012-05-12
Found the fix.  Somehow Disabled now so re-activated them in System Settings Keboard Shortcuts.

Jerry

---

### Post by jerrylamos on 2012-05-12
Hmmm.  Systems Settings Keyboard Shortcuts show Ctrl-Alt-Del as logout but nothing happens.

Jerry

---

### Post by zika on 2012-05-13
Alt-SysReq-K ;)

---

### Post by jerrylamos on 2012-05-13
> **zika said:**
> Alt-SysReq-K ;)

Boom!  Sure did work, logged right out.  Systems settings keyboard is wrong but the function is there.

Thanks, Jerry

---

### Post by codingman on 2012-05-13
Set this as solved ;)

---

### Post by mc4man on 2012-05-13
> **jerrylamos said:**
> Boom!  Sure did work, logged right out.  Systems settings keyboard is wrong but the function is there.

Thanks, Jerry
Not the same "function"
Alt-SysReq-K kills X, Ctrl+Alt+Delete runs this which works fine here
/usr/lib/indicator-session/gtk-logout-helper --logout

---

### Post by zika on 2012-05-13
> **mc4man said:**
> Not the same "function"
Alt-SysReq-K kills X, Ctrl+Alt+Delete runs this which works fine here
/usr/lib/indicator-session/gtk-logout-helper --logout;) I never said that these two were the same... ;)
But, how come if X is killed I end up, again, on login screen... :)

---

### Post by mc4man on 2012-05-13
> **zika said:**
> ;) I never said that these two were the same... ;)
But, how come if X is killed I end up, again, on login screen... :)

Didn't quote you...
Probably  there is some tech difference between Alt-SysReq-K &  Ctrl+Alt+Backspace, I don't bother so much in that regard, the result is the same here - kills the session & goes to login without any prompt, ect. (if open unsaved work then changes lost

So certainly will apologize for self inflicted ignorance in such matters

---

### Post by zika on 2012-05-13
> **mc4man said:**
> Didn't quote you...
I did not feel it like that anyhow. I just wanted to clarify...

> **mc4man said:**
> Probably  there is some tech difference between Alt-SysReq-K &  Ctrl+Alt+Backspace, I don't bother so much in that regard, the result is the same here - kills the session & goes to login without any prompt, ect. (if open unsaved work then changes lost
I see the only use of either in situations when X stops being responsive... In that case I use SK (S part of REISUB, and K)

[LIST]
[*]S: Sync all mounted filesystems (to save what saved can be...)
[/LIST]
 > **mc4man said:**
> So certainly will apologize for self inflicted ignorance in such mattersNo need for any apologizing... ;)

---

### Post by zika on 2012-05-16
At my place Alt-Tab does work in Unity, FluxBox and OpenBox but not in Gnome-slassic(a.k.a. fallback)...

---

### Post by jerrylamos on 2012-05-21
> **zika said:**
> At my place Alt-Tab does work in Unity, FluxBox and OpenBox but not in Gnome-slassic(a.k.a. fallback)...

Update keeps killing Alt-Tab and Alt-F4.  I don't know why the developers keep removing function....

Jerry

---

### Post by mc4man on 2012-05-21
Alt-Tab and Alt-F4 work in all sessions here by default with the exception of Alt-Tab in Classic (compiz). In that case one of the switchers needs to be enabled in ccsm
So don't see the "developers" causing anything in this regard

---

### Post by jerrylamos on 2012-05-21
> **mc4man said:**
> Alt-Tab and Alt-F4 work in all sessions here by default with the exception of Alt-Tab in Classic (compiz). In that case one of the switchers needs to be enabled in ccsm
So don't see the "developers" causing anything in this regard

Well, this is quantal quetzal Unity-2D.  I guess I'm not as lucky as you are.  No big deal, just adds to the manual things to do on a new install.  I do a lot of installs on "unstable" development ubuntu's on four pc's looking for bugs.

Jerry

---

### Post by rpaskudniak on 2012-05-22
> **jerrylamos said:**
> Found the fix.  Somehow Disabled now so re-activated them in System Settings Keboard Shortcuts.

Jerry

Jerry,

I'm gratified you found it in the settings.  Now please share that with us: What did you do to get at those settings?  Like, how did you find the dialog box where you you can set those settings?

Please start from the top menu.  BTW, I'm using the Gnome classic desktop but if you can direct us to the correct starting point it should make no difference.

Thanks.

---

### Post by jerrylamos on 2012-05-22
> **rpaskudniak said:**
> Jerry,

I'm gratified you found it in the settings.  Now please share that with us: What did you do to get at those settings?  Like, how did you find the dialog box where you you can set those settings?

Please start from the top menu.  BTW, I'm using the Gnome classic desktop but if you can direct us to the correct starting point it should make no difference.

Thanks.

Let me try.  I think Unity keeps changing underneath me.  
Top right applet 
System Settings
Keyboard
Keyboard
Shortcuts
Windows
Close Window 
Go to right end of line, press "Alt-F4"
back up to Shortcuts
Navigation
Switch Applications
Go to right end of line, press "Alt-Tab"
press close

Isn't this fun.  Ctrl-Alt-Del doesn't do anything even though it is in the Shortcuts.

Only thing I know about Gnome Classic is 10.04 LTS which I'm running on two notebooks - one because Quantal Quetzal doesn't supprt wireless, the other because Unity Overhead is sluggish on 1 GHz 512 MB.

On 10.04, there is a vaguely similar set of menu choices

System
Preferences
Keyboard Shortcuts
whole bunch of similar shortcuts organized in a long list instead of categories.
Ctrl-Alt-Del does work, gets Shutdown, Restart, Suspend, Hibernate.  I use this all the time on 10.04.

Do note in general for what I do, Unity requires a lot more keystrokes/mouse actions than 10.04 does.  Could well depend on what applications you use.  

Have fun.  I wonder what long standing defaults will change next.

Jerry

---

### Post by Mathor on 2012-05-24
> **jerrylamos said:**
> 
Isn't this fun.  Ctrl-Alt-Del doesn't do anything

Works for me. :confused:

---

### Post by jerrylamos on 2012-05-31
Updates are still disabling Alt-F4 and Alt-Tab.  At least system settings still works.

Jerry

---

### Post by rpaskudniak on 2012-06-10
I win!  Though at the cost of publicly confessing to jerkhood.

I've been looking for the executable because I did not see it in the [Applications]->[System Tools]->[Preferences] menu.  In fact, I couldn't see the Preferences menu at all.  Why?

Because my inner Mr. Spock was logically searching the [System Tools] menu alphabetically.  Well, an inspired madness had me do a sequential scan down the menu and there it was - near the top of the {system Tools] menu.  And there I found the CompizConfig-settings-manager, the very thing that many have stated is the solution to this problem.

Scroll to the bottom category, Windows Management, check the box on Application Switcher, close the application and ***voila***! Alt-Tab now works.  And I've banging my head on the wall for this solution for over 2 weeks!

BTW, the executable name is simply ccsm. (Path: /usr/bin/ccsm)

I need to post this in a few threads.

Yes, I claim it is a bug in the upgrade that application switching becomes disabled.  But with an easy workaround, if you know where to look. (no always my strongest point._

---

