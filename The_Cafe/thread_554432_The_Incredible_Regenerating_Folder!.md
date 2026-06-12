---
title: "The Incredible Regenerating Folder!"
date: 2007-09-19
forum: The Cafe
---

### Post by Nano Geek on 2007-09-19
Woa, this is weird. 
I'm taking an HTML class online, and I wanted to see the code for some websites, so I downloaded linux.com with wget, and now it won't leave my hard-drive!

Every time I try to delete it, it makes a copy of its self again.
I included a video for those who want to see it.
I would appreciate any help that I could get or any similar experiences that you might have had.

---

### Post by FuturePilot on 2007-09-19
wget isn't stuck in a loop is it?

---

### Post by blithen on 2007-09-19
VERY cool. 'Cept if you can't get it off that kinda sucks lol.

---

### Post by Shazaam on 2007-09-19
ctrl+c

Might work.

---

### Post by bluenova on 2007-09-19
sudo pkill wget

---

### Post by blithen on 2007-09-19
> **Shazaam said:**
> ctrl+c

Might work.
:/ Why would he do that? Seems quite silly.

---

### Post by Nano Geek on 2007-09-19
> **bluenova said:**
> sudo pkill wgetwget's not running anymore, the folder is coming back on its own.

---

### Post by Paul820 on 2007-09-19
Instead of moving it to the trash, just delete it fully. There is an option to add a delete command in the preferences when you open your home folder. Weird though. :)

---

### Post by Ebuntor on 2007-09-19
> **Paul820 said:**
> Instead of moving it to the trash, just delete it fully. There is an option to add a delete command in the preferences when you open your home folder. Weird though. :)

I think you can do that by pressing Shift+Delete. :)

---

### Post by Zaneyard on 2007-09-19
idk if you have to become sudo or not for this but do that if it doesn't work this way

first try changing directory to whatever folder it is in
Ex. cd /home
then use the command rm to remove
rm [www.linux.com](www.linux.com)
thats the only thing i can think of

---

### Post by Nano Geek on 2007-09-19
I did a rm -rf, and it still came back.

---

### Post by asmoore82 on 2007-09-19
> **asjdfwejqrfjcvm msz34rq33 said:**
> wget's not running anymore, the folder is coming back on its own.

```
~$ ps -A | grep get
```

---

### Post by Nano Geek on 2007-09-19
Hmm.
I just rebooted, and that fixed it.
Thanks for the help guys.
I wonder what could have happened.
:-k

---

### Post by Zaneyard on 2007-09-19
is it possible that a program is recreating it as you delete it?
what does the -rf do that you used?
can you move it to another folder w/o it regenerating? 
maybe it is having malicious software problems. the only way a folder would have problems deleting even though you can move it w/o a problem would be that another program is storing it and looking for the delete command
as you saw it is regenerating and not just denying deletion altogether
unless linux itself is doing this you have some kind of application storing and restoring the folder
have you tried restarting, or is that not an option?

---

### Post by Zaneyard on 2007-09-19
haha i was right
restarting works
i just take a long time to post
that was the second time that happened today

---

### Post by Nano Geek on 2007-09-19
> **Zaneyard said:**
> is it possible that a program is recreating it as you delete it?
what does the -rf do that you used?
can you move it to another folder w/o it regenerating? 
maybe it is having malicious software problems. the only way a folder would have problems deleting even though you can move it w/o a problem would be that another program is storing it and looking for the delete command
as you saw it is regenerating and not just denying deletion altogether
unless linux itself is doing this you have some kind of application storing and restoring the folder
have you tried restarting, or is that not an option?Thanks for the help.
**rm -rf** will remove a folder, and everything in it.

---

### Post by argie on 2007-09-19
> **asjdfwejqrfjcvm msz34rq33 said:**
> Hmm.
I just rebooted, and that fixed it.
Thanks for the help guys.
I wonder what could have happened.
:-k

Okay, I don't know much about these things but when linux deletes files it just removes the link to the inode (or something like that). Maybe that's the problem.

On second thought, after seeing how it happened, I think you accidentally made wget a background process. If you use Ctrl-C to close wget, you may have accidentally hit Ctrl-Z, they're close on the keyboard. Or something like that.

---

### Post by merlyn on 2007-09-19
> **Zaneyard said:**
> what does the -rf do that you used?

I know that you already have a response to this but the command```
rm -rf
```translates to,

rm = **r**e**m**ove

-r  = recursive i.e. the specified directory, sub directories and all contents.

-f = force, meaning that the person issuing the command will not be prompted for confirmation during the removal process.

For further information, open a terminal and type the following```
man rm
```where

man = **man**ual & rm = (see above).

As you can see from these two examples commands are typically truncated forms of actual words, which in time will help in understanding their purpose and aid in remembering them.

[Here]("http://www.linuxdevcenter.com/linux/cmd/") is an excellent online guide to *nix commands.

Cheers.

---

### Post by cmat on 2007-09-19
> **blithen said:**
> :/ Why would he do that? Seems quite silly.

That kills it.

---

### Post by asmoore82 on 2007-09-19
> **asjdfwejqrfjcvm msz34rq33 said:**
> Hmm.
I just rebooted, and that fixed it.
Thanks for the help guys.
**I wonder what could have happened.**
:-k

wget was still running/orphaned/zombied...

---

