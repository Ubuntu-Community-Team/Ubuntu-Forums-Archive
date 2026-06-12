---
title: "LTSP Thin Client - Limited Desktop"
date: 2011-10-28
forum: Server Platforms
---

### Post by witkedm on 2011-10-28
Hi All,

I have an Ubuntu 11.10 LTSP set up and I am able to login with my thin client. The problem is the thin client desktop is almost completely bare. It has the 11.10 purple wallpaper and the gray menu bar across the top, but only 'File Edit View Go Bookmarks Help' are listed on the menu bar. 

There isn't a launcher on the left side and there are no icons on the top right (i.e. network status, sound, time, account, settings). I tried adjusting the resolution of the thin clients and switching between an older laptop thin client and a newer laptop thin client with the same result. 

I assume I am missing something simple? Maybe it has to do with the Unity desktop or user account settings?

Any help would be greatly appreciated. Thank you.

---

### Post by bob53124 on 2011-10-30
Read This > **bob53124 said:**
> I have found a workaround its not ideal but it works. If you install kde from the host pc (opening terminal and typing 'sudo apt-get install kubuntu-desktop' without quotes ) and then when loading up the client select session from preferences > session > then either KDE Plasma Workspace or Kubuntu depending on your version and it will permanently stay like that for than user

---

### Post by bob53124 on 2011-11-03
bump - can you get unity

---

### Post by ricmat on 2011-11-03
> **witkedm said:**
> Hi All,

I have an Ubuntu 11.10 LTSP set up and I am able to login with my thin client. The problem is the thin client desktop is almost completely bare. It has the 11.10 purple wallpaper and the gray menu bar across the top, but only 'File Edit View Go Bookmarks Help' are listed on the menu bar. 

There isn't a launcher on the left side and there are no icons on the top right (i.e. network status, sound, time, account, settings). I tried adjusting the resolution of the thin clients and switching between an older laptop thin client and a newer laptop thin client with the same result. 

I assume I am missing something simple? Maybe it has to do with the Unity desktop or user account settings?

Any help would be greatly appreciated. Thank you.

I have been trying to get LTSP working on Edubuntu, and Ubuntu for about a month now, and have yet to see a successful login.  So you're doing great.

I have a stack of paper 3 inches high with forum posts, "quick setup guides" and the like.  All of them different.  None of them work.  Even though it's all supposed to work "out of the box."  I'm convinced that people write the code and never test it.

My bright spot was with Skolelinux - I can make that work.  Unfortunately, it uses KDE and I want Gnome.  The interface looks like something from DOS 3.0.   Their instruction manual lists a desktop=gnome option that can be changed, but guess what - when you do that, no more logins.  A bug according them.  So how the heck did they test it with gnome, if you can't log in under gnome?  Answer, they didn't test it.  Just like the rest of LTSP.

I'm convinced that all of the LTSP stuff is total cr*p.  I had high hopes for it (for use at a K-8 school where I volunteer.)  But I can't waste any more time on it.  Especially since my client HW varies considerably.

So, if you've got it up and logging in successfully, consider yourself lucky. ](*,)

---

### Post by interfejs.eu on 2011-11-14
Hi, the easiest way to make it work install gnome-shell, and change session to gnome before yo log in to thin client.

Regards,

Mike

---

### Post by shaneo1 on 2012-01-24
That is hardly a fix to the problem.  I have tested both KDE and Gnome desktops and they work perfectly.  Why is Unity not working?  Each time I have to select Unity 2D session.  Its not default.

I would like to know why as well

---

