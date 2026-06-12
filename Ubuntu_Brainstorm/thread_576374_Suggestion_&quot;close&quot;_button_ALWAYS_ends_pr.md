---
title: "Suggestion: &quot;close&quot; button ALWAYS ends program, add &quot;close to tray&quot; button"
date: 2007-10-15
forum: Ubuntu Brainstorm
---

### Post by DeadZedz on 2007-10-15
In linux desktop environments all windows should behave consistently: 
1. "close" button always closes program (no popups, no questions "do you want to close or minimize to  task bar or tray" or whatever) 
2. Add "minimize to tray" button next to minimize button.

---

### Post by Sisophon2001 on 2007-10-15
Agreed 100%

---

### Post by Zdravko on 2007-10-20
Okay. Would be nice to have it, but it is not that essential IMHO.

---

### Post by m0eman on 2007-10-20
Every program I use closes when i click X and minimizes to tray when I click its tray icon. I don't think its nessesary. And Zdravko are you trying to get the front page all your name lol?

---

### Post by Zdravko on 2007-10-20
[m0eman]("http://ubuntuforums.org/member.php?u=159095"), yes. I want to be the last one to post at every thread.
Reason: [http://ubuntuforums.org/showthread.php?t=578606](http://ubuntuforums.org/showthread.php?t=578606)

---

### Post by smartboyathome on 2007-10-20
> **Zdravko said:**
> [m0eman]("http://ubuntuforums.org/member.php?u=159095"), yes. I want to be the last one to post at every thread.
Reason: [http://ubuntuforums.org/showthread.php?t=578606](http://ubuntuforums.org/showthread.php?t=578606)

Please don't spam. Spamming is NEVER appropriate, and is gross too. ;)

---

### Post by Next.Step on 2007-10-20
+1
Also defining a commmon keyboard shortcut
in some cases  Alt+F4 minimizes apps to tray(ex. Pidgin)

---

### Post by smartboyathome on 2007-10-20
I would rather have a "minimize to tray" icon, and not a "close to tray" icon (less confusion!)

---

### Post by Zdravko on 2007-10-21
> **smartboyathome said:**
> Please don't spam. Spamming is NEVER appropriate, and is gross too. ;)

I am not spamming. 90% of my posts here are appropriate and thread-oriented. Just get used to me. I am not trying to spoil anything. Just trying to feel better.

---

### Post by Arathorn on 2007-10-21
> **DeadZedz said:**
> In linux desktop environments all windows should behave consistently: 
1. "close" button always closes program (no popups, no questions "do you want to close or minimize to  task bar or tray" or whatever) 
2. Add "minimize to tray" button next to minimize button.
I agree, but isn't this a DE problem? I like the way eMule does on Windows. By default, it offers four choices: minimize to tray, normal minimize, increase / decrease windows size and close (I've set it up to always minimize to tray).

---

### Post by smartboyathome on 2007-10-21
AllTray does this, but it doesn't work with Compiz Fusion. :(

---

### Post by ButteBlues on 2007-10-21
1. The notification area is NOT to be used as some ubiquitous dump for every application. It has specific uses, and applications that don't actively notify the user of events don't belong there.

2. There is a distinct difference between Closing the window and Quitting the application. In any application that does have a tray icon, closing the window simply closes the window and lets you create it again by clicking on the tray icon, whereas quitting the application actually quits the application. These are defined in the GNOME HIG.

3. In reality, you're trying to use the notification area like a glorified Window List. Just minimize ****. Or if you just _have_ to have icons for doing so, use AWN or similar.

---

### Post by bethaviv on 2007-10-22
I always thought those different buttons (minimize to tray, always close on 'X') were dependant on the program. Some programs had 'em and some didn't... Or maybe I'm too used to Windows?

---

### Post by Xbehave on 2007-10-22
isnt this a DE problem (possible higher than DE if you want it done only for programs that minimize to tray)?
if you were to add it to all KDE pograms id be happy!
yes it does end up turning the tray into a store of programs but that could be usefull

and perhaps latter optimisation could be added such as suspending the tasks of trayed programs to save cpu sort of an extreme minimize?

---

### Post by exile on 2007-10-23
I have to agree with ButteBlues - the notification area is not another place to park your apps. If people want to differentiate between "close" and "make dormant" (my word for sending a notification dialog back to it's box) maybe a different icon can be used rather than both being "X"?

---

### Post by Arathorn on 2007-10-23
Yes, I hate x not entirely closing a program. So I suggested to do it like eMule, with an extra button, just for minimizing to tray. But it's still a DE issue, so the *Ubuntu devs can't do much about it.

---

### Post by Martje_001 on 2007-10-25
> **DeadZedz said:**
> 1. "close" button always closes program (no popups, no questions "do you want to close or minimize to  task bar or tray" or whatever) 
It can't. Some programs save configuration files when you close them. If it gets forced to shutdown, it will never remember you settings.

---

### Post by Martje_001 on 2007-10-25
> **smartboyathome said:**
> AllTray does this, but it doesn't work with Compiz Fusion. :(
In 7.10 it works ;)

---

### Post by smartboyathome on 2007-10-25
> **Martje_001 said:**
> In 7.10 it works ;)

Not for me... when I click any window, nothing happens. :(

---

### Post by peter_ryan on 2007-11-27
i am in the same boat. if anyone has found a way for alltray to work with compiz / 7.10 please help. right now when i click a window alltray does not respond.

> **smartboyathome said:**
> Not for me... when I click any window, nothing happens. :(

---

### Post by tjagoda on 2007-11-27
I believe that a minimize to tray button would clout up the GUI.  Maybe something in a right-click menu or a specific keyboard shortcut.

---

### Post by Endolith on 2008-01-05
We need a fourth "shrink to tray" button on the title bar.  I've filed a bug, though it's probably in the wrong place.  "Close" should always close things, and a separate button should exist for "shrink to tray" or "make dormant" as suggested in this thread.

[https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/124326](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/124326)

---

### Post by Endolith on 2008-01-05
> **ButteBlues said:**
> 2. There is a distinct difference between Closing the window and Quitting the application.

Then there should be a distinct button for each.  See attached pic of eMule, which has distinct buttons for each function.

> In any application that does have a tray icon, closing the window simply closes the window and lets you create it again by clicking on the tray icon, whereas quitting the application actually quits the application. These are defined in the GNOME HIG.

Are you sure it works that way?  Some apps with notification area icons:

[LIST]
[*]Gaim/Pidgin is not a GNOME app, but iconifies when I press the Close button.
[*]Skype is not a GNOME app, but iconifies when I press the Close button.
[*]Amule is not a GNOME app, and quits when I press Close.  It can be configured to iconify when I press Minimize.
[*]Rhythmbox is a GNOME app, and quits when I press Close.
[*]Gnome-RDP iconifies when I press Close.
[/LIST]
Certainly not consistent or predictable.

> 3. In reality, you're trying to use the notification area like a glorified Window List.

Isn't it a difference between apps you use to accomplish some specific task, and apps that run all the time in the background, and... notify you of things?

---

### Post by Endolith on 2008-07-07
[[IMG]http://brainstorm.ubuntu.com/idea/10865/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/10865/)

---

### Post by CarpKing on 2008-07-08
This behavior is application-specific; bugs should be filed against programs that do not behave as expected (and probably already have, though most developers probably have justifications for why their way is best).

---

### Post by animaniac on 2008-07-08
no. i like the current behavior, an adding more buttons is bad. -1

---

### Post by Endolith on 2008-07-08
> **CarpKing said:**
> This behavior is application-specific;

The presence of the 4th button would be application-specific.  The possibility of adding that button for applications that support it is part of the window manager, though.

> **animaniac said:**
> no. i like the current behavior, an adding more buttons is bad. -1

...because?  Just blind resistance to change?  :)

---

### Post by qamelian on 2008-07-08
> **Endolith said:**
> 
...because?  Just blind resistance to change?  :)
No. Because some people genuinely do not see any value in this suggestion. Why is it that any time someone disagrees with a suggestion on this forum, someone else feels the need to accuse them of being resistant to change? This is is disrespectful of the opinions of fellow forum members and is, frankly, very insulting. 

Not everyone agrees that this is a good suggestion. I'm one of them. It just does not seem necessary and I cannot see any real benefit. The current behaviour is exactly how I would expect it to be in almost all cases. Personally, I would find yet another button on the titlebar to be annoying as the current buttons do exactly what they are supposed to do and I don't want every single app to to be able to drop to the notification area. That is contrary to the purpose of this area.

---

### Post by Endolith on 2008-07-08
> **qamelian said:**
> Why is it that any time someone disagrees with a suggestion on this forum, someone else feels the need to accuse them of being resistant to change?

Because it's a very common attitude in the Linux community that prevents us from making any real progress?  Linux merely plays catch-up with other OSes and mimics them *after *they implement things, because Linux users are too afraid of  anything that might represent real innovation.  Then after Apple does it, it's suddenly a good idea...

If enough people are complaining about resistance to change for you to notice a pattern, don't you think their complaints might have some validity?

> The current behaviour is exactly how I would expect it to be in almost all cases.

The current behavior is to abuse the "Close" button or the "Minimize" button to achieve a purpose they were not designed for, in a way that is completely inconsistent from one app to another.  You really think this is the best way to do it?

> I don't want every single app to to be able to drop to the notification area.

As I said, it would only be present on apps that supported this functionality, so that they didn't abuse one of the other standard buttons.  Rhythmbox would have four buttons, Firefox would have three.

---

### Post by bruce89 on 2008-07-08
Having the "Close Window" button replaced with "Force quit" would mean that huge numbers of config files would be screwed up. Even worse, there could be memory freeing issues.

---

### Post by mc4100 on 2008-07-09
> **Endolith said:**
> 
[An extra button] would only be present on apps that supported this functionality, so that they didn't abuse one of the other standard buttons.  Rhythmbox would have four buttons, Firefox would have three.
 I get the point of a button only ever doing one action, but a selectively-appearing one is totally counterproductive; the point of having three buttons, IMO, is ubiquity and not having to learn on an app-by-app basis. If a button appeared only when an app supported a certain function, then we would have to, at some level, look for it. If I'm working with many windows and want to free space, I close the *windows* I don't think are important; I don't think about it much, I know if I'm using writer and a web browser is open, an email client, an instant messenger and a music player, then I just close them quickly. But I only want to close the windows, i.e., I still want to keep the music playing, and similarly I want to keep receiving IM notifications, so I set them to minimize to tray on closing.
I know that could get messy and possibly confusing, but that's why good defaults, and preferences menus, are there.

---

### Post by qamelian on 2008-07-10
> **Endolith said:**
> Because it's a very common attitude in the Linux community that prevents us from making any real progress?  Linux merely plays catch-up with other OSes and mimics them *after *they implement things, because Linux users are too afraid of  anything that might represent real innovation.  Then after Apple does it, it's suddenly a good idea...

If enough people are complaining about resistance to change for you to notice a pattern, don't you think their complaints might have some validity?

Nope. Some of the suggestions I see in this forum are quite good but the vast majority are, in my opinion, a waste of time that provide no genuine benefit. Not all change is good  or even necessary.


> The current behavior is to abuse the "Close" button or the "Minimize" button to achieve a purpose they were not designed for, in a way that is completely inconsistent from one app to another.  You really think this is the best way to do it?
How so? The Close buttons purpose is to close a window, not necessarily to close an application. In most cases, this amounts to the same thing but not always. The current behaviour is consistent across every OS GUI that I have used since the days of the Atari ST / Commodore Amiga. It should not come as a surprise, unpleasant or otherwise, to anyone who has used any OS with a GUI in the past 20 years. That isn't to say that improvement to various GUIs could not be made. I just don't see the change suggested here as truly being beneficial. In my mind, all it does is add clutter to the UI.


> As I said, it would only be present on apps that supported this functionality, so that they didn't abuse one of the other standard buttons.  Rhythmbox would have four buttons, Firefox would have three.
Again, based on the actual purpose of the Close button, I fail to see how this is an "abuse".

---

### Post by Endolith on 2008-07-10
> **mc4100 said:**
> the point of having three buttons, IMO, is ubiquity and not having to learn on an app-by-app basis.

Huh?  That's exactly why we're advocating for a fourth button.  Currently the behavior *is *different from app to app, with buttons having different functions in different apps.  It's nonsensical to say that the three buttons that are always in the same place on the same title bar of every app with the same images on them should do *different *things from one app to the next.

In most apps, you press *Close* and it closes the app.  But in some, the app does not actually close, but switches to icon/system tray mode instead.  In these, you can only close the app by choosing *Quit* from the menu bar.  In others, *Close* does close the app, but *Minimize* does not minimize.  Instead, *Minimize *is the button that converts to system tray mode.  It's confusing to users and there's no good reason why it should be inconsistent.

> If a button appeared only when an app supported a certain function, then we would have to, at some level, look for it.

Where are you getting the idea that it's going to appear and disappear?  It's going to be shown on the menu bar at all times for apps that support that functionality, and not for apps that don't, just like the Minimize and Maximize buttons are only shown for apps that support them.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=77153&d=1215701439[/IMG]

This is not at all difficult to understand, unlike the current abuse of standard buttons and removal of standard functionality in inconsistent ways from one app to the next.

---

### Post by mc4100 on 2008-07-13
> **Endolith said:**
> Huh?  That's exactly why we're advocating for a fourth button.  Currently the behavior *is *different from app to app, with buttons having different functions in different apps.
OK, you're  right: currently, we need to learn (app-by-app) whether 'closing' will *actually* close. However, you sort-of missed my point: 
Having the close button do selective things means I only need to press *one* button to get rid of the window -- I think this is useful for quick window management, and means I never need to think much about it. Useful apps that don't need a window because they run silently in the background, (e.g., Pidgin) should just do so, and not require their users constantly clicking a button to let them continue to function as was designed.
 
> **Endolith said:**
> It's nonsensical to say that the three buttons that are always in the same place on the same title bar of every app with the same images on them should do *different *things from one app to the next.

Now, this, I simply disagree with. I don't think is nonsensical at all, in fact, I think it's the right way to do things: it's smart and it's efficient. 

> **Endolith said:**
> In most apps, you press *Close* and it closes the app.  But in some, the app does not actually close, but switches to icon/system tray mode instead.  In these, you can only close the app by choosing *Quit* from the menu bar.  In others, *Close* does close the app, but *Minimize* does not minimize.  Instead, *Minimize *is the button that converts to system tray mode.  It's confusing to users and there's no good reason why it should be inconsistent.

I can see the issues with inconsistency, but the buttons are for window management; often, we still need an app to function even when we don't want to see it's window. For example, Transmission closes to tray when downloading. That's confusing for like a day; it's also really useful.

> **Endolith said:**
> Where are you getting the idea that it's going to appear and disappear?
In terms of windows, it's going to appear on some, and not on others. Which makes managing a huge amount of windows less convenient.

You make a good argument and, in summary, I suggest the following options, possibly in "System -> Preferences -> Window" which I think would be a good idea:


Show minimize to tray button [checkbox]

When I close the window:   
[option 1]  Let the application decide to quit
		           [option 2] Explicitly quit the application


OR possibly a specification in the GNOME HIG for an option in Edit -> Preferences.

---

### Post by Endolith on 2008-07-13
> **mc4100 said:**
> OR possibly a specification in the GNOME HIG for an option in Edit -> Preferences.

Nah.  Options upon options are for KDE.  :)

---

### Post by mc4100 on 2008-07-13
> **Endolith said:**
> Nah.  Options upon options are for KDE.  :)
I laughed at that; but is buttons upon buttons for GNOME any different? ;)

---

### Post by k99goran on 2008-07-14
> **qamelian said:**
> The Close buttons purpose is to close a window, not necessarily to close an application. In most cases, this amounts to the same thing but not always.
The problem is that the behavior is inconsistent. Which application will actually close down when I click the X and which will continue running?
> The current behaviour is consistent across every OS GUI that I have used since the days of the Atari ST / Commodore Amiga. It should not come as a surprise, unpleasant or otherwise, to anyone who has used any OS with a GUI in the past 20 years.
But I haven't used Banshee for the last 20 years, so the fact that it doesn't close down when I click the X can still come as a surprise. And I have seen a lot of applications on the Windows side that solves this inconsistency by adding a "minimize to tray" button.

I would argue that you can never get used to inconsistency.

---

