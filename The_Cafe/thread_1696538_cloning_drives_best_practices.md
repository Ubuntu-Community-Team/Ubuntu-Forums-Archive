---
title: "cloning drives best practices?"
date: 2011-02-27
forum: The Cafe
---

### Post by greenwom on 2011-02-27
I just got my hand on 20 desktops (all the same model)from a trade-in on a job.
I want to reinstall an OS on them (XP in this case, just to sell them).

I've installed, updated and configured a test computer and want to image that disk and then write that image to all the rest of the machines.

I've been looking at clonezilla but not to sure if it's the right tool for me.

Is there a utility on my Ubuntu install where I can just clone that drive or make an iso without going into a live environment?
And then just write that image to a new drive?

I'm reading a ton of how to's but can't find a Linux based solution that makes sense.  Doing this over the network doesn't appeal to me but I'm willing to try

---

### Post by CharlesA on 2011-02-27
Clonezilla will do what you want. They have a server you can run that boots via PXB and can image many machines at once.

Is there a reason you don't want to clone the machines over the network?

You could always take an external hard drive to each machine and boot off a clonezilla cd and image it from that.

EDIT: Depending on how big the image is, you can create an ISO using clonezilla and restore the image by booting off a dvd.

See [here]("http://www.ehow.com/how_5779033_create-clonezilla-recovery-dvd.html") for how to create the bootable ISO after imaging a machine.

---

### Post by handy on 2011-02-27
When I was in the business I regularly used Symantec Norton Ghost. 

If Clonezilla had of been around then I would have used it. It is very intelligent in the way that it uses the various tools that are incorporated into it. 

Meaning that it automatically uses the right tools for the right file-system or combination thereof when you have a multi-partitioned drive using a variety of file-systems.

I wouldn't think about using anything else other than Clonezilla.

---

### Post by The Real Dave on 2011-02-27
Clonezilla is fantastic, I swear by it. It should do all you want and more :)

---

### Post by juancarlospaco on 2011-02-27
Clonezilla for H@x0r
Redo-Live for no0bz

---

### Post by sudoer541 on 2011-02-28
[FONT=Arial Narrow]> **greenwom said:**
> I just got my hand on 20 desktops (all the same model)from a trade-in on a job.
I want to reinstall an OS on them *[FONT=Arial][COLOR=Red]**(XP in this case, just to sell them).**[/COLOR][/FONT]*

I've installed, updated and configured a test computer and want to image that disk and then write that image to all the rest of the machines.[/FONT] [FONT=Arial Narrow]

I've been looking at clonezilla but not to sure if it's the right tool for me.[/FONT] [FONT=Arial Narrow]

Is there a utility on my Ubuntu install where I can just clone that drive or make an iso without going into a live environment?[/FONT] [FONT=Arial Narrow]
And then just write that image to a new drive?

I'm reading a ton of how to's but can't find a Linux based solution that makes sense.  Doing this over the network doesn't appeal to me but I'm willing to try[/FONT] [FONT=Arial Narrow]
[/FONT] 

making multiple copies of Windows xp and selling them is illegal.

---

### Post by Ctrl-Alt-F1 on 2011-02-28
> **sudoer541 said:**
> [FONT=Arial Narrow][/FONT] [FONT=Arial Narrow]
[/FONT] 

making multiple copies of Windows xp and selling them is illegal.
Depends where you live.  The Copyrights/Patents/DMCA isn't enforceable everywhere.

edit: nvm user is from Chicago. D'oh!

---

### Post by koenn on 2011-02-28
> **sudoer541 said:**
> [FONT=Arial Narrow][/FONT] [FONT=Arial Narrow]
[/FONT] 

making multiple copies of Windows xp and selling them is illegal.

depending on the license,
- multiple copies of Windows xp is illegal, whether you sell them or not -- eg OEM en FPP licenses
-  multiple copies of Windows xp is perfectly legal -- I'm sure MS has (or had) a licensing program for hardware vendors that allows them to sell computers with  Windows XP installed :)

---

### Post by Bungo Pony on 2011-02-28
> **CharlesA said:**
> Clonezilla will do what you want.

...unless there's bad sectors on the drive. Then it does what every other Linux-based cloning tool does... it hangs :(

---

### Post by handy on 2011-02-28
> **Bungo Pony said:**
> ...unless there's bad sectors on the drive. Then it does what every other Linux-based cloning tool does... it hangs :(

With Clonezilla you go into expert mode & use the rescue option.

---

