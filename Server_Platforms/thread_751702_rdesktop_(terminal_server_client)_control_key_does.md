---
title: "rdesktop (terminal server client) control key doesn't work"
date: 2008-04-10
forum: Server Platforms
---

### Post by MountainX on 2008-04-10
When I log into a Windows 2003 Server via rdesktop (terminal server client), the control key is not sent. That means ctrl-c, ctrl-v, etc. don't work on the server. (If I right click and use the context menu to select copy, paste, undo, etc. they all work - it's just the control key that doesn't work).

I think this is more of a keyboard layout issue than an rdesktop issue, but the problem only appears in rdesktop.

I'm running Hardy beta. 

What should my next step be? Is there a better place to post this question? What would some good trouble shooting steps be?

I can't even seem to come up with good searches on Google.

I could really use some help because my work requires that I log in to a Windows server. If I want to keep running Ubuntu on my desktop, I have to solve this soon! :)

Thanks.

---

### Post by MountainX on 2008-04-10
no one else has seen this issue? very strange... does anyone have any ideas what I could try? Thanks.

---

### Post by MountainX on 2008-04-11
I am now fairly sure this is a bug introduced in Hardy that lies somewhere between terminal server client, rdesktop, the the X keyboard utilities. The same problem doesn't exist in Gutsy. 

Any admins want to move this thread to the correct place? Sorry for posting it here. At first I didn't realize it is strictly a Hardy issue.

---

### Post by Maybelline on 2008-04-18
I can tell you that this was definitely not a *consistent* issue in Gutsy.  But, since I'm on Hardy full-time now, I'm noticing it (albeit still intermittently) a lot more.

One thing you might try is killing the rdpclip.exe process from TaskManager (rt-click the taskbar in Windows).  I almost NEVER copy & paste from my Ubuntu machine to the Windows box, and killing that program seems to clear up some issues I've had.

But, even without rdpclip running, I get the "control key" issue you're seeing.  I'd love to hear a solution, if anyone has one.

/subscribed

jv

---

### Post by MountainX on 2008-04-18
> **Maybelline said:**
> I can tell you that this was definitely not a *consistent* issue in Gutsy.  But, since I'm on Hardy full-time now, I'm noticing it (albeit still intermittently) a lot more.

One thing you might try is killing the rdpclip.exe process from TaskManager (rt-click the taskbar in Windows).  I almost NEVER copy & paste from my Ubuntu machine to the Windows box, and killing that program seems to clear up some issues I've had.

But, even without rdpclip running, I get the "control key" issue you're seeing.  I'd love to hear a solution, if anyone has one.

/subscribed

jv

Thanks for your feedback. One of my worst experience with rdesktop was when I had the Clip Book (clipsrv.exe) enabled on the Windows Server. That was horrendous -- with Hardy. (I don't recall any problems with Gutsy.) Unfortunately, I do like to copy paste between the client and server. 

My situation has improved somewhat using the solution posted here:
[http://ubuntuforums.org/showpost.php?p=4644873&postcount=7](http://ubuntuforums.org/showpost.php?p=4644873&postcount=7)

Unfortunately, while I said in that post that everything was completely resolved, that isn't the case. Remote desktop is still not nearly as good as it was under Hardy, mainly because of keys not working the same as they did.

I really miss the ability to use compiz plus ctrl-alt-arrow to enable full screen rdesktop sessions to integrate smoothly with multiple desktops on Ubuntu... but that's another story.

---

### Post by ombzzz on 2008-06-30
> **MountainX said:**
> When I log into a Windows 2003 Server via rdesktop (terminal server client), the control key is not sent. That means ctrl-c, ctrl-v, etc. don't work on the server. (If I right click and use the context menu to select copy, paste, undo, etc. they all work - it's just the control key that doesn't work).



i'm having a similar problem in Linux Mint Elyssa ( based on Ubuntu 8.04 ) with terminal server session on Windows 2003 servers: the ctrl and alt keys experience randomly problems, very often( really annyoing ):

when this keys stop working i can't switch applications in the windows session ( ALT-TAB ) and can't copy and paste ( CTRL-C, CTRL-V )

the workaround i use is to press many times the CTRL key and voila! the keys are responding again ( wtf??? )

please, rdesktop guys, Ubuntu, Microsoft guys or what ever: FIX THIS !!!!

---

