---
title: "ubuntu one music store doesn't connect"
date: 2010-05-17
forum: Ubuntu One (CLOSED)
---

### Post by toffifeemann on 2010-05-17
hey,
so since ive installed 10.4 im quite taken by rythmbox which i didnt really discover before somehow
but i have a problem with the store-plugin
whenever i restart rythmbox it seems to be working fine, then i try to buy a song and then it says "connecting..." but then nothing happens, meaning it doesnt connect
i made an account but i dont find a problem-log so i can't really help myself
is this a common issue? how can i help you guys help me?

---

### Post by joshuahoover on 2010-05-17
> **toffifeemann said:**
> hey,
so since ive installed 10.4 im quite taken by rythmbox which i didnt really discover before somehow
but i have a problem with the store-plugin
whenever i restart rythmbox it seems to be working fine, then i try to buy a song and then it says "connecting..." but then nothing happens, meaning it doesnt connect
i made an account but i dont find a problem-log so i can't really help myself
is this a common issue? how can i help you guys help me?

Can you try the following and let me know if it helps or not?

[LIST=1]
[*]Quit Rhythmbox (Music->Quit)
[*]Open Applications->Accessories->Terminal and run:
u1sdtool -q; killall ubuntuone-login; u1sdtool -c
[*]If you haven't added your computer to your Ubuntu One account, then the command above should start a browser and take you through the process outlined here: [https://one.ubuntu.com/support/installation/](https://one.ubuntu.com/support/installation/) Otherwise, the command above should connect you to Ubuntu One
[*]Open Rhythmbox and try to access the Ubuntu One Music Store
[/LIST]
If you still have problems, can you run *u1sdtool -s *in a terminal session and post the output here?

Thanks!

Joshua

---

### Post by toffifeemann on 2010-05-18
that worked fine!
so but now im wondering, do i have to use that command everytime i start rythmbox? no right?

---

### Post by joshuahoover on 2010-05-18
> **toffifeemann said:**
> that worked fine!
so but now im wondering, do i have to use that command everytime i start rythmbox? no right?

No, you shouldn't have to do that. My suggestion is to make sure you have all the latest Ubuntu updates via System Update. There was a bug from long ago that would cause this type of behavior but was fixed prior to 10.04 LTS being released. I'd be surprised if you were being affected by that. If you restart your computer and experience the same problem, please let me know.

Thank you,

Joshua

---

### Post by toffifeemann on 2010-05-24
nope, thanks! works fine!

---

### Post by joshuahoover on 2010-05-24
> **toffifeemann said:**
> nope, thanks! works fine!

Great to hear! Thank you for following up!

---

### Post by allquixotic on 2010-05-25
This worked for me, too.

The first time I got this popup page that asked me to add my computer, I quickly closed the Firefox browser because I thought it was some advertisement. But then later on I realized I wanted to buy a song in the music store. So after following these instructions I'm all set.

Would be nice if you could get that page to pop up every time in Firefox if a service is trying to use Ubuntu One.

---

### Post by craig100 on 2010-06-23
This worked for me to: u1sdtool -q; killall ubuntuone-login; u1sdtool -c

But I was disappointed I had to use it on a brand new and totally up to date installation.

I then proceeded to buy an album using Rhythmbox.  The screen has been on "Transferring to your Ubuntu One storage" for over 9 hours now. Checking my Ubuntu One storage shows the files there but they are definitely not on my local machine which was added as a synch machine when I set up the account.  I'm finding the whole rigmarole totally non-intuitive and therefore it really isn't ready to out class iTunes. You should be able to follow your nose and it just work. That's the mark of a good UI!

Can someone please tell me how I get my music to a place I can listen to it, or I'm going to have to demand a refund of the money I just paid out.

Thanks

KIND OF HUMBLE PIE
Instead of the files turning up in my music folder and being added to my music library, they were downloaded to /home/myName/.local/share/ubuntuone/Purchased from Ubuntu One/ArtistName/Album & track. I couldn't find them in the Rhythmbox music library until I expanded the "Music" label and found the "Puchased from Ubuntu One" link.

It's taken a while, not sure it was necessary (from a UI design point of view!).

Cheers

---

### Post by mike4ubuntu on 2010-07-05
doesn't work for me.  The command line commands seem to work and give status that I'm connected, but Rythmbox just sits saying "connecting...," but never does.

```

mike@lic7:/share/webdav$ u1sdtool -q; killall ubuntuone-login; u1sdtool -c
ubuntuone-syncdaemon stopped.
ubuntuone-login: no process found
mike@lic7:/share/webdav$ u1sdtool -s
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE

```

---

### Post by superfrogman94 on 2010-08-09
> **mike4ubuntu said:**
> doesn't work for me.  The command line commands seem to work and give status that I'm connected, but Rythmbox just sits saying "connecting...," but never does.

```

mike@lic7:/share/webdav$ u1sdtool -q; killall ubuntuone-login; u1sdtool -c
ubuntuone-syncdaemon stopped.
ubuntuone-login: no process found
mike@lic7:/share/webdav$ u1sdtool -s
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE

```

ugh.... same here, i used the commands like 3 times, restarted the computer
and nothing.... it dosnt connect, been like this for over a week! and i have updated my system....

---

### Post by superfrogman94 on 2010-08-18
BUMP

a still have the same issue... only happens on my 64 bit desktop and not my netbook (which is 32 bit)

i have uninstalled reinstalled the plugin still didnt work and also rythmbox as well...
this also happens in banshee

please help!

---

### Post by soulShredder on 2010-08-21
Hi I've got the same problem - tried the fix but it doesn't work for me. Same terminal output as Mike and FrogMan.

---

