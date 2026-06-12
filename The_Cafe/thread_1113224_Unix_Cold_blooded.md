---
title: "Unix Cold blooded?"
date: 2009-04-01
forum: The Cafe
---

### Post by peter_q on 2009-04-01
So I'm in this unix class, which is helping me learn about linux and stuff too... And we went around mkdiring and touching... Making all these cute little files. I got to spend time with em--going around cding and stuff. catting all the outputs...

But then came time to stop using the terminal... Then the horrible command rm -rf came about...

Oh the horror. No "Are you sure" or "Won't you miss them?" prompts... I should have aliased to rm -i...

It just felt so inhumane... A whole directory massacared. And all I see is the cold, hollow user$_

---

### Post by smartboyathome on 2009-04-01
Just DON'T RUN rm -rf /* as it will kill your system. :(

---

### Post by Kareeser on 2009-04-01
The unix program "rm" does one thing, removing files, and it does it well. That's a core linux philosophy :)

So rm assumes you know what the heck you're doing when you add the "f" switch. :)

---

### Post by t0p on 2009-04-01
I agree with the OP.  All commands that have the potential to be harmful should be removed from Linux forthwith.

Also, only fluffy bunnies should be allowed as screensaver images.  Why would anyone want something more vicious than a fluffy bunny on their display?

---

### Post by jespdj on 2009-04-01
Maybe they should replace the "-f" switch with something more elaborate. Like this:

rm -r -yes-I-really-want-to-destroy-my-system-please-let-me-do-it *

:P

---

### Post by Yownanymous on 2009-04-01
> **t0p said:**
> Why would anyone want something more vicious than a fluffy bunny on their display?

Might I direct you [here]("http://ubuntusatanic.org/")?

---

### Post by tjwoosta on 2009-04-01
the #1 rule with unix commands

RTFM!!

if you would have read the man entry for rm you would have noticed what each of the flags does

-r, -R, --recursive
 remove directories and their contents recursively

-f, --force
 ignore nonexistent files, never prompt

---

### Post by mcduck on 2009-04-01
> **jespdj said:**
> Maybe they should replace the "-f" switch with something more elaborate. Like this:

rm -r -yes-I-really-want-to-destroy-my-system-please-let-me-do-it *

:P

That would be quite funny :D

I kind of miss the good old "glxgears --iacknowledgethatthistoolisnotabenchmark"

---

### Post by insane_alien on 2009-04-01
> **smartboyathome said:**
> Just DON'T RUN rm -rf /* as it will kill your system. :(

i tried it ages ago. it DOESN'T kill your system...

...until you reboot.

although you won't be able to run any program that isn't cached in RAM after this command has done its dirty work.

---

### Post by Mehall on 2009-04-01
> **insane_alien said:**
> i tried it ages ago. it DOESN'T kill your system...

...until you reboot.

although you won't be able to run any program that isn't cached in RAM after this command has done its dirty work.

Did that to a EEE in John Lewis. That's what they get for not putting a passwd on sudo.

---

### Post by lisati on 2009-04-01
> **t0p said:**
> I agree with the OP.  All commands that have the potential to be harmful should be removed from Linux forthwith.


And while we're at it, we should ban ALL motor vehicles and other things which can kill people. (Just kidding!)

Accidents happen: sometimes we just have to swallow our pain and get on with putting the pieces back together again and moving on. And people do dumnb things and try risky commands out of curiosity (which is why the mention of certain commands in these forums is sometimes discouraged)

Speaking of motor vehicles, one idea I came across a year or two back was to replace airbags with some kind of device which hurts people, such as enormous metal spikes. This has the potential for motivating people to drive safely. The down side is that I haven't yet come across a way of preventing innocent people getting hurt.

---

### Post by billgoldberg on 2009-04-01
> **Mehall said:**
> Did that to a EEE in John Lewis. That's what they get for not putting a passwd on sudo.

That's not very nice.

:p

---

### Post by smbm on 2009-04-01
> **Mehall said:**
> Did that to a EEE in John Lewis. That's what they get for not putting a passwd on sudo.

That's pretty uncool.

---

### Post by apmcd47 on 2009-04-01
> **peter_q said:**
> So I'm in this unix class, which is helping me learn about linux and stuff too... And we went around mkdiring and touching... Making all these cute little files. I got to spend time with em--going around cding and stuff. catting all the outputs...

But then came time to stop using the terminal... Then the horrible command rm -rf came about...

Oh the horror. No "Are you sure" or "Won't you miss them?" prompts... *I should have aliased to rm -i...*

It just felt so inhumane... A whole directory massacared. And all I see is the cold, hollow user$_

NO! DON'T DO IT!
```
$ rm *.tmp
no0001.tmp? y
no0002.tmp? y
.
.
.
no2003.tmp? y
$
```
One of the philosophies of the original coders of UNIX was "We are grown-ups. We don't need hand-holding". If you really need that don't do```
alias rm='rm -i'
```do something like ```
alias rmi='rm -i'
```instead. If you are used to typing "rmi" and it doesn't exist, fine. If you are used to typing rm and expect it to be an alias, and it isn't, you have a problem.

Actually, I agree that Unix is a harsh mistress. I'm surprised that people in charge of creating distros haven't thought "let's create a few hand-holding commands for the less computer-savvy". Stick 'em into another directory (eg /usr/bin/hh) and the Unix purists can ignore it while the others put it ahead of the other commands.

Andrew

---

### Post by LookTJ on 2009-04-01
> **t0p said:**
> I agree with the OP.  All commands that have the potential to be harmful should be removed from Linux forthwith.Then I wouldn't have the joy of self-discipline.

---

### Post by jenkinbr on 2009-04-01
> **t0p said:**
> I agree with the OP.  All commands that have the potential to be harmful should be removed from Linux forthwith.


I disagree.

Do you realize that many apps use rm, dd, and other potentially dangerous commands as a backend for removing files?

Caution is the key here.  Read the man page, and know exactly what it is you type before pushing enter.

---

### Post by schauerlich on 2009-04-01
> **apmcd47 said:**
> NO! DON'T DO IT!
```
$ rm *.tmp
no0001.tmp? y
no0002.tmp? y
.
.
.
no2003.tmp? y
$
```

The solution to that is to pipe yes through it.

```
$ yes | rm *.tmp
remove no0001.tmp? remove no0002.tmp? ... remove no2003.tmp?
$

```

yes basically just says "y" over and over until the next command stops.

---

### Post by jenkinbr on 2009-04-01
> **EDavidBurg said:**
> The solution to that is to pipe yes through it.

```
$ yes | rm *.tmp
remove no0001.tmp? remove no0002.tmp? ... remove no2003.tmp?
$

```

yes basically just says "y" over and over until the next command stops.
That doesn't eliminate the potential for accidents when using an alias, though.

---

### Post by schauerlich on 2009-04-01
> **jenkinbr said:**
> That doesn't eliminate the potential for accidents when using an alias, though.

Well, leave the alias on for normal usage, and then you're sure about something, use the "yes" trick.

---

### Post by apmcd47 on 2009-04-02
> **EDavidBurg said:**
> The solution to that is to pipe yes through it.

```
$ yes | rm *.tmp
remove no0001.tmp? remove no0002.tmp? ... remove no2003.tmp?
$

```

yes basically just says "y" over and over until the next command stops.
An easier workaround is```
$ \rm *.tmp
```WHEN I remember it (prefixing a command in bash forces it to disregard aliases and functions). But why should I work around somebody else's brain-dead attempt to stop themselves from accidentally deleting something?

*rm -i* was a lazy attempt to filter out the wheat from the chaff when attempting to delete with a wild-card. What is really needed is the prompt```
Are you sure you want to delete this many files?
``` when a certain number is exceeded. Anyone could write a shell-script which could do the job. I'm just surprised that no-one has.

I think I'd better stop now ;)

Andrew

[Edit] Just found this in the rm man page:```

       -I     prompt once before removing  more  than  three  files,  or  when
              removing  recursively.  Less intrusive than -i, while still giv&#8208;
              ing protection against most mistakes



```

---

### Post by Eisenwinter on 2009-04-02
> **t0p said:**
> I agree with the OP.  All commands that have the potential to be harmful should be removed from Linux forthwith.

Also, only fluffy bunnies should be allowed as screensaver images.  Why would anyone want something more vicious than a fluffy bunny on their display?
rm is not harmful. you just need to know what you're deleting.

---

### Post by jenkinbr on 2009-04-02
> **Eisenwinter said:**
> rm is not harmful. you just need to know what you're deleting.
On the flip side of this, rm is dangerous when you don't know what it does

[FONT="Arial Black"][COLOR="Red"]**[SIZE="6"]!!!WARNING!!!: DO NOT RUN COMMANDS BELOW THIS POINT!!![/SIZE]**[/COLOR][/FONT]
On a complete other note, however, my Ubuntu install is *almost* completely replaceable, as there are only a few customizations I've made to things in the /usr, /var, and /etc directories.  I would much rather run 
```
 sudo rm -rf /usr /etc /var
```
and have to enter my password, then run
```
rm -rf ~/*
```
and not receive any prompts.

The main system can be recovered in a few hours by doing a fresh install, update, upgrade, and install of additional packages.  Personal files are a different story entirely, for those who don't make backups regularly (or at all).

---

### Post by overdrank on 2009-04-02
Hi and I believe this has been covered in the [Announcement: ATTENTION ALL USERS: Malicious Commands]("http://ubuntuforums.org/announcement.php?f=326")

---

