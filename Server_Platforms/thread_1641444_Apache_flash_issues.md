---
title: "Apache flash issues"
date: 2010-12-09
forum: Server Platforms
---

### Post by tubaguy50035 on 2010-12-09
I've looked online and on here and haven't seen anyone else come across this issue.  I have a website that I recently switched from being hosted to my own private server.  I have two flash elements that are Google Voice call widgets.  Neither of them show up on the site.  The code is the exact same as it was when it was hosted, and it worked there.  Is there a configuration setting for Apache I need to set to enable flash?  When I right click the element it tells me that the movie is not loaded. 

Thoughts?

---

### Post by tubaguy50035 on 2010-12-09
If anyone would like to take a look at the actual site, pm me.

---

### Post by tubaguy50035 on 2010-12-09
please help.  I'm sorry to bump, but I need this to work

---

### Post by James78 on 2010-12-09
Flash not showing up in the browser has to do with the browser, client side, not the server. So if it's not working, it can be a few things:

[LIST=1]
[*]Your operating system and/or browser*
[*]Your website (html, php, files, etc) are incorrect
[/LIST]
So, it's most likely the website content that's the cause. If you copied the HTML verbatim, you probably need to edit the HTML and fix it, as you can seldom copy HTML verbatim and expect it to work without some small tweaks.

* In this case, it could be many problems. You don't have flash installed, you have driver issues, browser issues, software issues, it really could be anything.
> **tubaguy50035 said:**
> I've looked online and on here and haven't seen anyone else come across this issue.  I have a website that I recently switched from being hosted to my own private server.  I have two flash elements that are Google Voice call widgets.  Neither of them show up on the site.  **The code is the exact same as it was when it was hosted, and it worked there.**  **Is there a configuration setting for Apache I need to set to enable flash?**  When I right click the element it tells me that the movie is not loaded. 

Thoughts?
[LIST=1]
[*]Like I said earlier, you can seldom copy HTML code verbatim
[*]No, Apache will serve anything correctly as long as it's not server side generated files (in which case you configure it a certain way to serve them.. related files include shtml, php, asp ..)
[/LIST]

---

### Post by tubaguy50035 on 2010-12-09
I know flash works on my computer and the same browser.  I can see all flash sites with no problem.  I have tried it on two other computers with the same problem.  Can I pm you the code for the page?  I copied the files, not the code into new files.

---

### Post by James78 on 2010-12-09
> **tubaguy50035 said:**
> I know flash works on my computer and the same browser.  I can see all flash sites with no problem.  I have tried it on two other computers with the same problem.  **Can I pm you the code for the page?**  I copied the files, not the code into new files.
Sure.

---

### Post by tubaguy50035 on 2010-12-09
Sent

---

### Post by tubaguy50035 on 2010-12-09
Browser cache fixed it.  Thanks!

---

### Post by tubaguy50035 on 2010-12-10
It no longer functions yet again.  I haven't touched the code at all.  It's like it functions for a while, then goes away until I erase my cache.  Any thoughts on why this would be?  Check out the page [http://jamboxllc.com/jambox_005.htm](http://jamboxllc.com/jambox_005.htm)

---

### Post by James78 on 2010-12-10
Well, as I said in the PM, it still works fine for me. ;) Browser cache again?

---

### Post by tubaguy50035 on 2010-12-10
It works right after I clear it.  After about five minutes it is gone again.

---

### Post by James78 on 2010-12-10
What browser, browser version, OS, and OS version are you using?

---

### Post by tubaguy50035 on 2010-12-10
Firefox, I believe it's the latest stable version, Windows 7 64 bit with all current updates

---

### Post by James78 on 2010-12-10
Could you manually browse to the folder:
```
C:\Users\Username\AppData\Local\Mozilla\Firefox\Profiles\randomcharacters.default\Cache\
```

Once you get there, just delete everything inside the folder, then restart/start Firefox. See if your problem occurs again after that.

---

### Post by tubaguy50035 on 2010-12-10
Will do.  I'll post back in a couple hours with my results

---

### Post by tubaguy50035 on 2010-12-10
Seems to have worked for now.  I'll post back if I encounter problems again.

---

### Post by tubaguy50035 on 2010-12-10
Still happening.  I left the page open while I browsed around.   Came back, reloaded and it went away.  I reinstalled flash player, that did nothing.  I have ad block plus but it's not blocking anything on that page.

---

### Post by James78 on 2010-12-10
This is the closest I could find that might be related to the issue. It might also have nothing to do with it...
[http://www.google.com/support/forum/p/voice/thread?tid=1fdf66bb44e06635&hl=en](http://www.google.com/support/forum/p/voice/thread?tid=1fdf66bb44e06635&hl=en)

---

### Post by tubaguy50035 on 2010-12-10
Interesting.  I bet it does.  Now that you say that, every time I'm clearing my cache, I go to the site, check to see if the widget is there (always is at first), then I log into my google account.  Wow.  That's really dumb.  Thanks for your help.

I literally sign in to my account, refresh the page and it goes away.  Sign out, refresh, comes back.  Silly me for thinking it was an Ubuntu issue.

---

