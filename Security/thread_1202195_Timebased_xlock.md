---
title: "Timebased xlock?"
date: 2009-07-02
forum: Security
---

### Post by ToshiBoy on 2009-07-02
Is there a way to lock a Ubuntu server (9.04) at a certain time each day, say at 5pm?

---

### Post by kerry_s on 2009-07-02
crontab?

---

### Post by ToshiBoy on 2009-07-02
> **kerry_s said:**
> crontab?

Good idea... but it doesn't seem to be doing anything, screen stays unlocked, no screensaver kicks in... xlock is executed though.

---

### Post by scorp123 on 2009-07-02
> **ToshiBoy said:**
> Good idea... but it doesn't seem to be doing anything, screen stays unlocked, no screensaver kicks in...  Are you running this as the same user? What I mean is: Is the "cron" job user the same user who's running the GUI?

You can't lock another user's screen that way, if this is what you want to achieve.

But maybe it would be better if you could provide more background info? What is it exactly that you want to achieve and why? Maybe there are other and better ways to do it ....

---

### Post by ToshiBoy on 2009-07-02
Well, this is a political thing. The server is a 9.04 box, to which I've added ubuntu-desktop without recommends. It's a host for three of our core servers, two of which are pretty much essential to the company functioning. No problem. I've had 7.10 on this thing and it didn't need a reboot for 18 months.

Then my bosses desktop PC blew up and he insisted on using the server as his workstation. So, he now has WinXP in a virtual box. We are talking about a guy who is not prepared to go out of fullscreen to mount a CD. He just "wants it working".

Initially, I had his virtual box under a separate log in to the server, but whenever something happened to one of the virtual servers it was "too difficult" to go out of fullscreen and switch users.

Anyway, to cut a long story short, we had a harddrive crash (another long story) and I needed to rebuild the host from scratch and one of the conditions was that all virtual boxes run under the same server log in.

If I could I would love to have a way to stop people from "playing" around on the server, and since the holy WinXP virtual box "must" be running at all times during business hours, I need a way to lock it after hours, or else I've got a host wide open to anyone that walks past it.

Since I installed the desktop with no-recommends, I didn't even have a screensaver.

---

### Post by ToshiBoy on 2009-07-02
> **scorp123 said:**
> Are you running this as the same user? What I mean is: Is the "cron" job user the same user who's running the GUI?

You can't lock another user's screen that way, if this is what you want to achieve.

But maybe it would be better if you could provide more background info? What is it exactly that you want to achieve and why? Maybe there are other and better ways to do it ....

LOL, and since I got carried away... to answer your question, yes, it's running as the same user.

---

### Post by scorp123 on 2009-07-02
> **ToshiBoy said:**
>  I've had 7.10 on this thing and it didn't need a reboot for 18 months.  You never installed any kernel patches? ;)

In any case:

For 9.04 Jaunty you might be interested in this:
[http://www.ksplice.com/uptrack/](http://www.ksplice.com/uptrack/)

Yes, you read correctly. With KSplice you can apply security patches to the kernel without having to reboot.

There is a thread in the forum about KSplice:
[http://ubuntuforums.org/showthread.php?t=765352](http://ubuntuforums.org/showthread.php?t=765352)

I have it on two 9.04 installations so far and despite a kernel update yesterday I did not yet have to reboot ....


> **ToshiBoy said:**
>  Then my bosses desktop PC blew up and he insisted on using the server as his workstation.  Bad idea. Why not invest a little bit of money and get one of those new "NetTops"? They have the same CPU's like those "NetBooks" everyone is talking about and they are ultra ultra ultra cheap. The PC shop next door to the place where I work is selling net-tops for as cheap as CHF 249.-- / 163.-- EUR / USD 230.-- / AUD 287.--

Such a small PC should be more than good enough to run XP and to do office work with it.

> **ToshiBoy said:**
>  So, he now has WinXP in a virtual box. If you want to have it like this, then I would have gone this route:

[http://wikis.sun.com/display/VDI3/Home](http://wikis.sun.com/display/VDI3/Home)

Yes, I know: It's Solaris. But it works perfectly.


> **ToshiBoy said:**
>  We are talking about a guy who is not prepared to go out of fullscreen to mount a CD. He just "wants it working".  Migrate him to Linux. I doubt you have the necessary licenses from Microsoft that would allow you to deploy Windows XP on a virtualisation platform where at least in theory more than one user at once might have access to one and the same Windows XP installation. This is illegal and punishable with heavy fines and jail-time ....

Not that I really care :lolflag: .... But it's most likely true anyway. Just to give you some arguments that you could use. The goal here: he either has to buy a proper Microsoft "Enterprise License" which will cost way too much; or he has to buy himself a new PC with a proper Windows license which would be waaaay cheaper. In both cases you'd get to free your server from that stupid Windows XP desktop running there ... ;-)

> **ToshiBoy said:**
>  and since the holy WinXP virtual box "must" be running at all times during business hours. You have to "su" into the user running the desktop and then trigger the screensaver from inside there using the correct "DISPLAY" variable. Example:
```
...
su - vboxuser
DISPLAY=:0.0 xlock &
...

```

The stuff above works here, e.g. I can jump to a TTY (e.g. by hitting CTRL+ALT+F2 ...), login as another user, and then issue above sequence. And guess what: it triggers "xlock" as intended.

I suppose this is what you want?

---

### Post by ToshiBoy on 2009-07-03
Yeah, KSplice sounds good, and no, I never installed any patches on that 7.10 box... I've got another one sitting here under my desk, not hooked up to the internet and it's been running non-stop for close to 2 years...

And running licensed software would be nice, too... as it would be to stop banging my head against brickwalls... office politics drive me nuts. 

As for running DISPLAY... that works from the other terminal, as you said, but it doesn't do it via crontab for me. It also won't do it if I log in via ssh - which would enable me to do it remotely...

... and I like Solaris. Never had a day of trouble with it until I bought a new laptop and the wireless card wasn't on the list.

---

### Post by scorp123 on 2009-07-03
> **ToshiBoy said:**
>  It also won't do it if I log in via ssh - which would enable me to do it remotely... Did you use "ssh -X" or "ssh -Y" or something like that?

---

### Post by ToshiBoy on 2009-07-03
> **scorp123 said:**
> Did you use "ssh -X" or "ssh -Y" or something like that?

No, how do I use them? I don't use any parameters for ssh, apart form the IP

---

### Post by scorp123 on 2009-07-04
> **ToshiBoy said:**
> No, how do I use them? I don't use any parameters for ssh, apart form the IP Try with "ssh -X" or "ssh -Y" ... Pure "ssh x.x.x.x" to an IP doesn't set any DISPLAY variables whatsoever, hence the impossibility to do anything X11 related. -X or -Y will add the necessary environment bits. Read "man ssh" for all the details.

---

