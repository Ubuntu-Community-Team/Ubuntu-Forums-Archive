---
title: "continued discussion. ps3mediaserver as a daemon service"
date: 2012-02-28
forum: The Cafe
---

### Post by xclusive585 on 2012-02-28
I am starting this thread to continue a discussion from [this thread]("http://ubuntuforums.org/showthread.php?t=1931660") in regards to running ps3mediaserver as a daemon service. 

EDIT: Ubuntu 12.04/ps3mediaserver still suffers from the "ps3mediaserver daemon needs to be restarted after boot" bug]
EDIT again: 12.04 does not have this bug when the service is installed from the PPA repos using APT. See My last post, P.3]

I have ubuntu 10.04 server running headless, on which I've installed ps3mediaserver from the script found [here (by happy neko)]("http://www.ps3mediaserver.org/forum/viewtopic.php?f=3&t=13046&p=63060#p63060"). It is not recommended to run ps3mediaserver as a daemon, but in my case I have to, as it's running on a server that will not always be logged into, it's a headless box that's there to do it's jobs without human intervention when need be. 

The install script worked fine, even ps3mediaserver as a service works fine, with one catch. It only works right (in my case) if it's restarted AFTER the boot process. Even when it did work at boot, the daemon would crash once accessed by other machines. The only way for it to work right, and work **every** boot, was to make sure the service is restarted **after** everything else booted. What specifically it's depending on to start right is still unknown by me. (If you want more details see the first thread [here.) ]("http://ubuntuforums.org/showthread.php?t=1931660")

So currently I am using a small "restart service" script that's run by cron at boot. The script sleeps for eight seconds then restarts ps3mediaserver. eight seconds was the shortest tested time that was far enough into/after boot to restart ps3mediaserver with the desired results (i.e. it works right).

---

### Post by kevdog on 2012-02-28
The references I used for upstart was here: [http://upstart.ubuntu.com/cookbook/](http://upstart.ubuntu.com/cookbook/)

My bet is that it works with rc.local or after you manually restart the service because it depends on another running service.  Usually files in rc.local are the last to run, so all services should theoretically be started by this time.  

If your daemon is dependent on a listening or active process, I'm not sure the best way to figure what the process should be.  If you look at the various upstart scripts in /etc/init/ this will give you a pretty good idea of what other processes do.

Possibly the best thing would be to start your daemon process at the command line but don't fork it to the background -- run it in the foreground with the -v or -verbose option (if available), to see if the running process gives any hints whats going on.

---

### Post by Jumbs on 2012-04-06
Thank you for the root cron idea!

I have been dealing with this exact issue for months.

I have scripts for auto downloading and auto converting to PS3 formats... the only thing missing was having to do the manual restart of the server part.

i added:

```

@reboot sleep 8; service ps3MediaServer restart

```

to the root cron, and it seems fine now.

It is not a perfect, but it is 100% usable until the next reformat.

Without the cron change, the PS3 would not see the server, however other devices (wdtv) would. But they would not play anything.
Nothing in the logs was ever helpful.

It is worth noting that it wasnt always like this. It used to work fine on boot without logging in or restarting. Something changed.

---

### Post by Jumbs on 2012-04-06
the debug.log that it outputs looks identical to a successful startup, even when it fails

---

### Post by xclusive585 on 2012-04-06
Yea It never worked for me so I wasn't sure if it was PS3mediaserver itself or if it was something else. Even on my buntu12.04 test box the same rigged fix is needed.

Glad to know that it used to work. But I wish we knew if it was something with upstart or if it was ps3mediaserver that broke it. I haven't had the time, or desire to look into this too deeply.

If anyone figures out the cause let me know, I'll then pass it along to the proper people. 

-Dave

---

### Post by xclusive585 on 2012-04-06
> **Jumbs said:**
> 

i added:

```

@reboot sleep 8; service ps3MediaServer restart

```to the root cron, and it seems fine now.

It is not a perfect, but it is 100% usable until the next reformat.

Without the cron change, the PS3 would not see the server, however other devices (wdtv) would. But they would not play anything.
Nothing in the logs was ever helpful.


This is the problem I had. Even if it did start on boot, it just won't run right, without the restart being issued.


(side note, I never tried using the command directly in cron, I'm glad to see that works, I can alter my cron and ditch my script.)

---

### Post by Jumbs on 2012-04-07
What init script are you using?

---

### Post by xclusive585 on 2012-04-07
> **Jumbs said:**
> What init script are you using?
I'm using the stock init.d script.

For the cron, I had the cron job point to a script that restarted the service. your way is one less step. I didn't try putting the command directly in cron just in case crons environment didn't like doing a root command.

---

### Post by Jumbs on 2012-04-07
> **xclusive585 said:**
> I'm using the stock init.d script.

For the cron, I had the cron job point to a script that restarted the service. your way is one less step. I didn't try putting the command directly in cron just in case crons environment didn't like doing a root command.

Where did you find a stock one? I made one, but then found a better one on the ps3mediaserver forums?

As long as you are running the ROOT cron and not your accounts, it will have no issue with su commands.

---

### Post by xclusive585 on 2012-04-07
I installed ps3mediaserver using [this script found here by happy necko. ]("http://www.ps3mediaserver.org/forum/viewtopic.php?f=3&t=13046&p=63060#p63060")

I like install scripts people make, they simplify my program installing life.

I'll bet the init.d script you found on their forums is identical

---

### Post by xclusive585 on 2012-04-07
out of curiosity what did you use to install it? And you wrote your own upstart script for it!?
wow. That's dedication. :-)

---

### Post by Jumbs on 2012-04-07
> **xclusive585 said:**
> out of curiosity what did you use to install it? And you wrote your own upstart script for it!?
wow. That's dedication. :-)

Didn't use anything. Use the latest linux build on [http://www.ps3mediaserver.org/](http://www.ps3mediaserver.org/)
Have their RSS feed wired in so i get the new build announcements.

simple init.d scripts are simple. mine was like 4 lines. But then i found a more complex one on a forum, much more features.

Once you have the script, you just drop it in the init.d folder and run
sudo update-rc.d script defaults

And ta-da, sessionless startup script.

Before that i just had it run when you logged in, but that is SO 20011.

---

### Post by xclusive585 on 2012-04-07
> **Jumbs said:**
> Didn't use anything. Use the latest linux build on [http://www.ps3mediaserver.org/](http://www.ps3mediaserver.org/)
Have their RSS feed wired in so i get the new build announcements.

simple init.d scripts are simple. mine was like 4 lines. But then i found a more complex one on a forum, much more features.

Once you have the script, you just drop it in the init.d folder and run
sudo update-rc.d script defaults

And ta-da, sessionless startup script.

Before that i just had it run when you logged in, but that is SO 20011.
Lol classic.

The init.d script I'm using is semi-complex (from my point of view)... let's see here it is.

the script's name was "ps3mediaserver" it got renamed in my moving things around. check it out see if it's the one you're using.

---

### Post by Jumbs on 2012-04-07
> **xclusive585 said:**
> Lol classic.

The init.d script I'm using is semi-complex (from my point of view)... let's see here it is.

the script's name was "ps3mediaserver" it got renamed in my moving things around. check it out see if it's the one you're using.

I use this one:
[http://www.ps3mediaserver.org/forum/viewtopic.php?f=3&t=902](http://www.ps3mediaserver.org/forum/viewtopic.php?f=3&t=902)

It gives you more control, but essentially the same thing.

However you should give your JVM more memory, it will stop some MKV subbed things from skipping around.

Ill have to post all my scripts someday.

---

### Post by xclusive585 on 2012-04-07
Thanks for the info, I've got lot's of memory to spare so anything to make it run smoother. is there a way to allow a bigger video transcode buffer?

---

### Post by Lucradia on 2012-04-08
PlayStation 3 doesn't need ps3media server anymore. Any media server software works now more or less. (it may not be able to access the media server straight away, but it will be able to see it on the network, much like how when a Windows machine is connected, it will detect it.)

---

### Post by xclusive585 on 2012-04-08
Um. You never *needed *ps3mediaserver. Any UPNP media server would always have worked.

The issue comes in the supported file types. File types that the ps3 can actually play are very limited. 

So, if you want to use most/all types of media, you need a program that's good at [I]transcoding.

[/I]You let me know when you find something that transcodes as many file types and codec formats as ps3mediaserver can.

Or you can use whatever else you want, and only be able to play/transcode 3 file types.

Use whatever works for you. Those of us that know what does the most will choose what we chose.

[On a side note: ps3mediaserver has NOTHING to do with Sony, it is made by independent developers. It IS a stand alone media server software. Not only is it an independently developed stand alone upnp media server software, but it is among the BEST available. Don't think that it's only for ps3 or made by sony, 'cause it's neither of these things.]

---

### Post by Lucradia on 2012-04-08
> **xclusive585 said:**
> Um. You never *needed *ps3mediaserver. Any UPNP media server would always have worked.

The issue comes in the supported file types. File types that the ps3 can actually play are very limited. 

So, if you want to use most/all types of media, you need a program that's good at [I]transcoding.

[/I]You let me know when you find something that transcodes as many file types as ps3mediaserver can.

Or you can use whatever else you want, and only be able to play/transcode 3 file types.

Use whatever works for you. Those of us that know what does the most will choose what we chose.

You can always transcode beforehand :P If you have a network drive or two, you can have one of one type on one, and one of one type on another.

---

### Post by xclusive585 on 2012-04-08
Lol you sound like any other Linux geek. No offense intended.

The issue is who wants to do all that. When you can just play the freaking file.

Lol. To each his own. That's the great thing about options and choice.


But In defense of your argument. It takes a pretty powerful beast of a processor to transcode some things, so I can see the need to pre-transcode files if your machine cannot handle doing it on the fly.

---

### Post by Lucradia on 2012-04-08
> **xclusive585 said:**
> But In defense of your argument. It takes a pretty powerful beast of a processor to transcode some things, so I can see the need to pre-transcode files if your machine cannot handle doing it on the fly.

If the media server can't transcode, then what will?

---

### Post by xclusive585 on 2012-04-08
I dont know. I can transcode anything on the fly. It's called a Xeon. with lots of ram. And it does it with little effort.

I'll let you know when I find something that can't be transcoded by ps3mediaserver

---

### Post by Jumbs on 2012-04-08
> **xclusive585 said:**
> I dont know. I can transcode anything on the fly. It's called a Xeon. with lots of ram. And it does it with little effort.

I'll let you know when I find something that can't be transcoded by ps3mediaserver


You're both right.
With ps3mediaserver over ethernet and a decent machine (core 2 can do it fine), it can transcode 1080 on the fly. The hole there is really wifi vs ethernet link.

However i still have my scripts that remux most videos to mp4/mpg.
Its a remux, not a reencode, so it only takes a few seconds, so it falls into the "why not" zone.

If it is of the right type, you can fast forward and or jump (circle) on the ps3, however all not needed.

if you watch MKVs with soft subs, you need a transcoding server, and ps3mediaserver seems to be the best. Although it still chokes on a few file types.

I've spent like 3 years slowly getting my "perfect" setup going, so I have tried it all!

---

### Post by xclusive585 on 2012-04-22
Good news.

I stumbled on a working solution, verified for 12.04 LTS:
Just install ps3mediaserver with the below commands instead of using any scripts...(if you have an existing install from another method, I'd manually get rid of everything first...)

1. Add the ppa repo for ps3mediaserver;
```
sudo add-apt-repository ppa:happy-neko/ps3mediaserver 
```2. Simply update apt and install ps3mediaserver;
```
sudo apt-get update 
sudo apt-get install ps3mediaserver 
```The end. It works on reboot every time, simply by editing the "PS3MS-START" line to "1" in /etc/default/ps3mediaserver. 

I'm marking this solved.

I should have installed ps3mediaserver in this fashion in the first place. :-)

---

### Post by CharlesA on 2012-04-22
Thanks for the info. I might give it a shot to see if it'll steam to my Panasonic bluray player.

---

### Post by cariboo on 2012-04-23
> **CharlesA said:**
> Thanks for the info. I might give it a shot to see if it'll steam to my Panasonic bluray player.

MiniDLNA works well too, I use it to stream to two Samsung Blu-ray players and a system running XBMC. MiniDLNA is in the Precise repositories, or for earlier versions from [Sourceforge]("http://sourceforge.net/projects/minidlna/")

---

### Post by CharlesA on 2012-04-23
> **cariboo907 said:**
> MiniDLNA works well too, I use it to stream to two Samsung Blu-ray players and a system running XBMC. MiniDLNA is in the Precise repositories, or for earlier versions from [Sourceforge]("http://sourceforge.net/projects/minidlna/")
Nice. I just found out the bluray player I have doesn't have an option for dnla. D'oh!

---

### Post by xclusive585 on 2012-04-23
This is why I swear by ps3mediaserver. For devices that are limited in what they can do, ps3mediaserver seals the deal. As I mentioned before, it will just "play the freaking file".

Those of us that fall into Linux, tend to already be equipped to find our way around and make things happen, in one way or another.

But, if we all want to truly see Linux grow into the everyday world, we should support stuff that works well. (This is why I support Ubuntu, (it tends to "work, and work right"))

One thing we can all be sure of, is stuff that works, and works great, attracts attention. I'd put money on it that ps3mediaserver is one of (if not THE) most used media servers on windoze. This is because it works well and transcodes almost anything, I also know for a fact that Xbox users love it too. :-)

I'm surprised ps3mediaserver is not natively in the ubuntu repos. (The gui end of it needs to default to some sort of simplified settings layout for the everyday users while leaving the existing settings intact IMHO, but besides that it's great)

---

### Post by Jumbs on 2012-04-24
Saw that ppa once, but didnt use it. good to know it works now.

Ill probably transition to it eventually. Right now everything works as is, no need to poke it.



> **xclusive585 said:**
> This is why I swear by ps3mediaserver. For devices that are limited in what they can do, ps3mediaserver seals the deal. As I mentioned before, it will just "play the freaking file".

Those of us that fall into Linux, tend to already be equipped to find our way around and make things happen, in one way or another.

But, if we all want to truly see Linux grow into the everyday world, we should support stuff that works well. (This is why I support Ubuntu, (it tends to "work, and work right"))

One thing we can all be sure of, is stuff that works, and works great, attracts attention. I'd put money on it that ps3mediaserver is one of (if not THE) most used media servers on windoze. This is because it works well and transcodes almost anything, I also know for a fact that Xbox users love it too. :-)

I'm surprised ps3mediaserver is not natively in the ubuntu repos. (The gui end of it needs to default to some sort of simplified settings layout for the everyday users while leaving the existing settings intact IMHO, but besides that it's great)

---

