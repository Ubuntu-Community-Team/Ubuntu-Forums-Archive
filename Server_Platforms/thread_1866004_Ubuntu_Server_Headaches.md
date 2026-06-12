---
title: "Ubuntu Server Headaches"
date: 2011-10-20
forum: Server Platforms
---

### Post by hattriq27 on 2011-10-20
I have been running Ubuntu for what seems like an eternity.  I have set up 100s of servers in headless configs for various projects.

But now I am just getting frustrated.  One of our boxes get all messed up so we thought we'd try 11.04 (we were running 9.x like a champ).

My issue is the box keeps dropping it's network connection but I can live with that because I know I know I can fix it.  When I reset the machine it sits on some screen waiting for human interaction, the initramfs.  I need that crap to go, how do I wipe it from this machine and how do I never have that crap show up again on any new installs?

As you can tell I am a tad frustrated from having to reconnect this box to a keyboard and monitor.  Ubuntu used to be so clean and simple....why muck it up and make me wanna go back to BSD?

/rant

any suggestions will be appreciated, thanks

---

### Post by vasile002 on 2011-10-21
can you please attach a screenshot with that? what do you do to get over that?

---

### Post by chrisjsmith on 2011-10-21
> **hattriq27 said:**
> I have been running Ubuntu for what seems like an eternity.  I have set up 100s of servers in headless configs for various projects.

But now I am just getting frustrated.  One of our boxes get all messed up so we thought we'd try 11.04 (we were running 9.x like a champ).

My issue is the box keeps dropping it's network connection but I can live with that because I know I know I can fix it.  When I reset the machine it sits on some screen waiting for human interaction, the initramfs.  I need that crap to go, how do I wipe it from this machine and how do I never have that crap show up again on any new installs?

As you can tell I am a tad frustrated from having to reconnect this box to a keyboard and monitor.  Ubuntu used to be so clean and simple....why muck it up and make me wanna go back to BSD?

/rant

any suggestions will be appreciated, thanks

I've had the same problem.  Bar one machine, I'm on Debian stable now.

---

### Post by Jonathan L on 2011-10-21
> **hattriq27 said:**
> I have been running Ubuntu for what seems like an eternity.  I have set up 100s of servers in headless configs for various projects.

But now I am just getting frustrated.  One of our boxes get all messed up so we thought we'd try 11.04 (we were running 9.x like a champ).

My issue is the box keeps dropping it's network connection but I can live with that because I know I know I can fix it.  When I reset the machine it sits on some screen waiting for human interaction, the initramfs.  I need that crap to go, how do I wipe it from this machine and how do I never have that crap show up again on any new installs?

As you can tell I am a tad frustrated from having to reconnect this box to a keyboard and monitor.  Ubuntu used to be so clean and simple....why muck it up and make me wanna go back to BSD?

/rant

any suggestions will be appreciated, thanks

Hi Hattriq

May I suggest you use the long-term support releases?   I've used lots of the 10.04 LTS server installation in various headless configurations with great success, normally in fully-scripted blind installations.

Almost all of my work relies on having very low maintenance servers, so there are no screens, keyboards or fingers nearby, and many of the systems are inaccessible or far away -- so I probably share many of your goals; and also had a lot of good experience with other operating systems, especially FreeBSD.  But my recent projects needed more hosting choices and I've found Ubuntu LTS images to be the best of the things I've looked at.  I can't comment on 11.04 or .10 but one hears there's a fair amount of change, especially in the Desktop version.

Hope that's of some use.

Kind regards,
Jonathan.

---

### Post by reddevil2064 on 2011-10-21
> **hattriq27 said:**
> I have been running Ubuntu for what seems like an eternity.  I have set up 100s of servers in headless configs for various projects.

But now I am just getting frustrated.  One of our boxes get all messed up so we thought we'd try 11.04 (we were running 9.x like a champ).

My issue is the box keeps dropping it's network connection but I can live with that because I know I know I can fix it.  When I reset the machine it sits on some screen waiting for human interaction, the initramfs.  I need that crap to go, how do I wipe it from this machine and how do I never have that crap show up again on any new installs?

As you can tell I am a tad frustrated from having to reconnect this box to a keyboard and monitor.  Ubuntu used to be so clean and simple....why muck it up and make me wanna go back to BSD?

/rant

any suggestions will be appreciated, thanks

Whenever a stable box suddenly starts acting weird, and you haven't made any huge changes, I point to hardware. I've had a few boxes hang/or just plain quit working and it usually tended to be bad memory, or a bad motherboard.

---

### Post by Demented ZA on 2011-10-21
> **reddevil2064 said:**
> Whenever a stable box suddenly starts acting weird, and you haven't made any huge changes, I point to hardware. I've had a few boxes hang/or just plain quit working and it usually tended to be bad memory, or a bad motherboard.

Faulty HDD is also not excluded from this behavior. But I couldn't agree more. I'd start thinking hardware too.

---

### Post by Jonathan L on 2011-10-25
> **hattriq27 said:**
>  it sits on some screen waiting for human interaction, the initramfs.  I need that crap to go, how do I wipe it from this machine and how do I never have that crap show up again on any new installs?

Hi Hatriq

... I also wondered if you had a hardware fault of some kind.

Nonetheless, if what you're describing is something running the ash shell, you might take a look at the init script, and specifically the failure hooks and the panic function, which is called when the system can't boot.  The default behaviour is to put you in a minimal 'ash' shell.  Which is potentially extremely helpful.

At the very least, if you really don't want it ever to go to a shell, you can set panic=10 or whatever, to give a pause and then reboot.  I needed this behaviour for a recent network boot installation, where I want the clients to reboot if they find anything wrong.  (Forum [post]("http://ubuntuforums.org/showthread.php?t=1866444").)

Perhaps that's of some use.

Kind regards,
Jonathan.

---

### Post by Jarozas on 2011-10-25
Hi,

Is your problem similar at what I've described in the thread,

[http://ubuntuforums.org/showthread.php?t=1869080](http://ubuntuforums.org/showthread.php?t=1869080)

?

---

