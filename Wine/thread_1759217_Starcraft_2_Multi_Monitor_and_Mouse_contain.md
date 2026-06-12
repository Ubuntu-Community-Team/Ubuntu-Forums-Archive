---
title: "Starcraft 2 Multi Monitor and Mouse contain"
date: 2011-05-15
forum: Wine
---

### Post by completely on 2011-05-15
Hi there,

i've got now finaly my Starcraft 2 running and its quite as fast it was under windows :P
but i got one problem which i can't solve.

I've got a MultiMonitor setup with 3 Screens (Screen 0 1680x1050 / Screen 1 2560x1024 (thats a Maxtor DualHead2Go with 2 19" Monitors in it)). Normaly i use a TwinView setup but i've tried already a "seperate x server" setup and still won't work.

The behavior is the following:

Playing the game at Fullscreen or Windows Fullscreen i can move the mouse out of the game into the screen 1 setup. Thats quite annoying while playing and i often mess up a fight.

Can anyone help me with my problem? I've already made a Support Ticket at crossover games but they haven't answered till now :(

Cheers and thanks in advice.

---

### Post by bobwyajnr on 2011-05-21
> **completely said:**
> 
Playing the game at Fullscreen or Windows Fullscreen i can move the mouse out of the game into the screen 1 setup. Thats quite annoying while playing and i often mess up a fight.

Can anyone help me with my problem? I've already made a Support Ticket at crossover games but they haven't answered till now :(

Cheers and thanks in advice.

Hi.

I don't much about multi-monitor setups (can't afford that sort of thing myself :) ) or CrossOver for that matter! In fact I don't even own a copy of SC2!! :popcorn:

I would suggest posting a query on the [WineHQ AppDB: Starcraft II page]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=11123") (choose the retail version I would presume) - you might get lucky there.

You can't raise a support ticket on the [WineHQ website]("http://bugs.winehq.org/") because you aren't using a mainline version of Wine.

There are a lot X-input mouse fixes in the unreleased Git tree for the Wine source code (which will be in the next version - 1.3.21). Your problem maybe upstream of Wine e.g. an Nvidia driver (??I presume) or X-Server bug - if it's the latter you might get a fix when it is eventually replaced by Wayland :D.

Like I said I don't know how **CrossOver** works exactly - but I presume they cherry pick a specific Wine version for each game (perhaps with patches applied) and install each into it's own WINEPREFIX. These additional levels of complexity make it hard to get support from other Wine users and impossible to get help from the Wine developers...

Sorry I'm just trolling for unanswered forum posts TBH...
Ha, ha - bet you wish you'd never asked the question now! :popcorn:

Bob

---

### Post by completely on 2011-05-23
Thanks for your answere bobwyajnr,

well i've postet a support ticket at Codeweavers (maker of crossover games)

Jack answered me with a solution which doesn't work but heres the quote, maybe it helps someone else :)

> 
Inside Crossover's Manage Bottles>Control Panel>Wine Configuration>Graphics settings, there is a checkbox called "Allow DirectX apps to stop the mouse from leaving their window".  At present toggling this setting, perhaps in conjunction with "Emulate a Virtual Desktop" (which sets a window as defined by Crossover, so a game can be run in full screen mode but will still exist within a window of the specified size), is your main option for trying to overcome this problem, but I don't expect that it will work very well (though of course it is worth a shot).  Our developers are currently working on window management issues for a future release that will solve this, among other problems, but in my personal experience I haven't seen this setting work reliably.  Best regards, Jack


---

