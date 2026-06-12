---
title: "sudo has a lot of potential to be a great security model"
date: 2006-07-19
forum: The Cafe
---

### Post by aysiu on 2006-07-19
Most people who have seen me talk about root/*sudo* on these forums know that I'm a big advocate of *sudo*.

When people ask how to enable root, I always ask why they would want to enable root. I then link them to pages explaining more about *sudo* and how to use it.

I believe that the *sudo* model is more convenient than a separate root login, it allows for better security management (as users can be added to and removed from the *admin* group without having to "forget" or change an administrative password), and it also seems more "natural" to people who have passwords and keys in real life (after all, I don't turn into a different user to pull money from my bank--I'm still me, but I'm prompted for my PIN at the ATM machine).

Nevertheless, I'm beginning to rethink (at least with Ubuntu's current implementation of *sudo*) my position on root/*sudo*.

There are certain things that could make *sudo*'s implementation in Ubuntu a lot better, and until they come to fruition in Edgy+1, I'm going to be a lot more understanding of people who want to enable root:

***sudo*, as it stands now is too fragile.** Oh, it can't get lookup via hostname? Oh, there's *nobody* in the *admin* group, so you have to boot into recovery mode to manually add someone? Granted, I don't have these problems myself, but I've seen them many, many times on these forums, and they confuse the hell out of new users.

There need to be easy ways (that don't involve rebooting your computer) to rescue or restore *sudo* to its original state. There should also be a lot of warnings before you're allowed to take the last user out of the *admin* group.

You know how when you do *sudo dpkg-reconfigure xserver-xorg*, Ubuntu automatically makes a timestamped backup of the /etc/X11/xorg.conf file? Why can't it do that for the /etc/sudoers and /etc/group files any time you make a change to the groups?

***sudo* isn't fully implemented graphically**
Why do I have to tell people to create launchers for *gksudo nautilus* or *kdesu konqueror*? This is silly. I know the developers will never go for including these buttons, but I think they're crucial when the vast majority of new Ubuntu users install and configure Ubuntu themselves. The command-line is a wonderful thing, especially when you can copy and paste instructions others give you. But when you're trying to make changes yourself, sometimes you (as, most likely, an ex-Windows user) just want a quick fix of the point-and-click variety.

What should happen (and I mentioned this before on the Edgy wishlists) when a *sudo*er clicks to open a root-owned file--instead of simply being told she doesn't have the right to open it, a dialogue should pop up, "This file is a system file that affects all users. Are you sure want to modify it? If yes, enter your password here." Otherwise, for those without *sudo* privileges, the traditional "access denied" message should suffice.

**The current warnings encourage people to *sudo* graphical applications**
I've explained [here](http://www.psychocats.net/ubuntu/graphicalsudo) why you should use *gksudo* or *kdesu* for graphical apps and *sudo* for terminal apps, but people continue to use *sudo* for graphical apps, mainly because they get "errors" from using *sudo* the proper way.

A bug report has already been filed about these false errors and warnings, but the developers have deemed this bug a low priority. In the meantime, people will continue to accidentally *chown* home preference files and their .ICEauthority file (disallowing a login).

I'll continue to use *sudo* myself, but until Ubuntu fixes its implementation of *sudo*, I'm not going to be so die-hard against people logging in as root.

I've spoken my piece. Attack me, reaffirm me--do as you please.

---

### Post by G Morgan on 2006-07-19
I think sudo is a great thing but is more about encouraging good behaviour than a superior security model. The same results can be achieved using su and the root account, in both cases its the disipline of the user that determines the success or failure of either model.

Simply put I prefer to switch to root via su to do any significant work but sudo is useful for one shot switching. The very fact that sudo is the only way as default however makes it easier to teach people a security model and forces knowledge of why pure root all the time is a bad idea. For this reason I think Ubuntu should stick as sudo only for the future, its not as if a knowledgable user will need more than 5 seconds to enable root.

---

### Post by aysiu on 2006-07-19
Yeah, *sudo* is pretty cool. I just wish it were implemented better.

---

### Post by T700 on 2006-07-19
Good points all, Aysui.  Why don't you think the dev's would be open to incorporating these changes (or did I misread you)?

Paul

---

### Post by aysiu on 2006-07-19
> **T700 said:**
> Good points all, Aysui.  Why don't think the dev's would be open to incorporating these changes (or did I misread you)?

Paul
Because Ubuntu is designed to "just work" and not have to be configured a lot.

Unfortunately, the hard reality is that if you have to install the OS yourself, odds are you will have to do a lot of configuring. I guess it's generally being jaded about seeing [my last suggestion get shot down](https://launchpad.net/distros/ubuntu/+source/gnome-terminal/+bug/52914) (and seeing [the *gksudo* error getting a low priority on Launchpad](https://launchpad.net/distros/ubuntu/+source/gksu/+bug/23917)--it was filed last December, by the way).

---

### Post by xtacocorex on 2006-07-19
Good points aysiu. 

Although I've only experienced the hostname lookup problem you mentioned in the OP, I do follow what you mean with the others.

As for switching to a "root" in a sudo model, one could do 
```
sudo -s
```
which simulates a root terminal.

[quote="aysiu"]What should happen (and I mentioned this before on the Edgy wishlists) when a *sudo*er clicks to open a root-owned file--instead of simply being told she doesn't have the right to open it, a dialogue should pop up, "This file is a system file that affects all users. Are you sure want to modify it? If yes, enter your password here." Otherwise, for those without *sudo* privileges, the traditional "access denied" message should suffice.[/quote]

I do like this idea. I've briefly thought about something like this before, but never came up with anything useful. I don't know if you have to hack the code of nautilus or konqueror to fix this.

---

### Post by aysiu on 2006-07-19
> **xtacocorex said:**
> Good points aysiu. 

Although I've only experienced the hostname lookup problem you mentioned in the OP, I do follow what you mean with the others.

As for switching to a "root" in a sudo model, one could do 
```
sudo -s
```
which simulates a root terminal. In fact, that's what I usually recommend to people who say they don't want to type *sudo* a hundred times.

> I do like this idea. I've briefly thought about something like this before, but never came up with anything useful. I don't know if you have to hack the code of nautilus or konqueror to fix this. The closest to that right now is an "Edit file as root" right-click context in Konqueror. I believe you can also create a similar functionality in Gnome with a Nautilus script. But the authentication through double-click (or single-click in Konqueror) isn't available right now.

Not being a programmer myself, I have no idea what it would take to get that functionality in there.

---

### Post by xtacocorex on 2006-07-19
Thanks for reminding me about the konqueror right click menu option. I used to have that back in the days of KDE 3.1. 

I do know that there is a program in the repos that puts an option in the Gnome menu that allows one to open programs as a different user. I have it installed, forgot the name, and haven't tried it yet. 

Do you know if anyone can post a bounty on launchpad? Maybe if a monetary amount gets put behind a request for the gksudo and kdesu lanuchers you mentioned, they might get included into the appropriate packages. It's such a simple task to do, but I'm sure some dev would be interested if even a small amount was put up for it.

I'm sure if one sent the files ready to be input into the packages and then promised a six-pack of beer, someone would go for that too.

---

### Post by aysiu on 2006-07-19
Is that how bounties work?

---

### Post by GarethMB on 2006-07-19
> **aysiu said:**
> Is that how bounties work?

That's what he was asking.

Basically can bounties be posted upstream. Ie. we set incentives for Dev's.

As usual good thread Aysiu, canonical should hire you.

---

### Post by scxtt on 2006-07-19
enabling the root user makes an attack twice as easy ... instead of "guessing" the admin username, you're easily giving them "root" and just leave it to them to "guess" the password ...

IMO, sudo is a great idea (no particular feelings on its implementation) ... i'll never use a root login again ...

---

### Post by xtacocorex on 2006-07-19
> **GarethMB said:**
> That's what he was asking.

Basically can bounties be posted upstream. Ie. we set incentives for Dev's.

As usual good thread Aysiu, canonical should hire you.

I wasn't sure if anyone could post one, thanks for the clarification GarethMB.

---

### Post by BuffaloX on 2006-07-19
I think if sudo wasn't an option, I would log in as root all the time.
I hate being blocked from my own system, but using sudo is a very nice "workaround".
I think my system is more secure this way, but I'm not an expert.

---

### Post by GarethMB on 2006-07-19
> **xtacocorex said:**
> I wasn't sure if anyone could post one, thanks for the clarification GarethMB.

I haven't answered the question. Just tried to clarify as what i interpret the meaning to be.

---

### Post by pulver on 2006-07-19
yeah don't you just love it when the user may use passwordless sudo for a short period of time. also, off topic but sudo and tab completion rox too doesn't it.

---

### Post by xtacocorex on 2006-07-19
[quote=GarethMB] I haven't answered the question. Just tried to clarify as what i interpret the meaning to be.[/quote]

I thought you accidentally left a word out of your post.

[quote=GarethMB] Basically can bounties be posted upstream. Ie. we set incentives for Dev's.[/quote]

After further review, I must have modified your sentence in my head to make it what I wanted to read. Sorry for the misunderstanding.

---

### Post by givré on 2006-07-19
> **BuffaloX said:**
> I think if sudo wasn't an option, I would log in as root all the time.

That's one of the reason why sudo was implemented. If you forget to exit after a root session, and if you do a mistake, you will not have error message.

---

### Post by BuffaloX on 2006-07-19
> **givré said:**
> That's one of the reason why sudo was implemented. If you forget to exit after a root session, and if you do a mistake, you will not have error message.

Me make mistake? Thats just rumours..:-\" 

Now that I think about it, the sudo option may be one of the reasons I stayed with Linux at all. :-k

My previous Linux experience, I never figured out how to log in as root, so it felt like I couldn't do anything at all. ( The entire 1½ hour It lasted )
I think sudo is a very important part of the userfriendliness of ubuntu.

---

### Post by pulver on 2006-07-20
If it wasn't for sudo, sun would still revolve around the earth.

---

### Post by kabus on 2006-07-20
[QUOTE=aysiu]Oh, it can't get lookup via hostname? Oh, there's nobody in the admin group, so you have to boot into recovery mode to manually add someone? [/QUOTE]

Wouldn't sudo be pretty pointless if it allowed an unauthorized user to make those changes?

[QUOTE=pulver]yeah don't you just love it when the user may use passwordless sudo for a short period of time.[/QUOTE]

I love it so much that I use passwordless sudo permanently.

---

### Post by aysiu on 2006-07-20
> **kabus said:**
> Wouldn't sudo be pretty pointless if it allowed an unauthorized user to make those changes? It's also kind of useless if people can't use it because they're supposed to be authorized but they're not--which was my whole point... it's too fragile the way it's implemented now.

---

### Post by kabus on 2006-07-20
> **aysiu said:**
> It's also kind of useless if people can't use it because they're supposed to be authorized but they're not

But there is already a way to fix that and I think (someone correct me if I am wrong) it is a good bit more secure than what you want because it requires physical access to the computer.

---

### Post by aysiu on 2006-07-20
> **kabus said:**
> But there is already a way to fix that and I think (someone correct me if I am wrong) it is a good bit more secure than what you want because it requires physical access to the computer.
Yes, and there is a way to fix accidentally getting your last admin user out of the admin group, too, but why not make it difficult for it to be broken in the first place? Or make it so that a recovery or restoration to the original state is easy? That's all I'm saying.

What's wrong with including the computer Ubuntu is installed on in the /etc/hosts file? What's wrong with automatically backing up the /etc/hosts file when it's been modified?

---

### Post by xtacocorex on 2006-07-20
I think this may be the time to ask. 

Should we put some money together and set up a bounty to get sudo better implemented? I know it's supposed to be in the works, but the faster it gets done, the better secure systems will be and hopefully fix the problems associated with it currently.

We can use aysiu's OP as a basis for expanding on what the bounty should accomplish.

---

### Post by aysiu on 2006-07-20
*sudo* is pretty secure as is--it just breaks easily. 

How, practically, would we gather up the money? It appears that payment for bounties go through PayPal:
[https://launchpad.net/bounties](https://launchpad.net/bounties)

---

### Post by xtacocorex on 2006-07-20
Well, I guess we'd have to determine an amount of money to set the bounty to. We'd also have to determine someone to keep hold of the money until the bounty is complete. I have a PayPal account, and I'm sure that others here also have them. I wouldn't be able to put in a lot of money since I'm still looking for a job that goes with my degree, but I think I can spare $10 or so. 

I also just threw out the idea. I don't knows if it's even feasible for us (community) to set up it. 

Otherwise, I guess we can try to find the breakages with sudo and fill out bug reports.

---

### Post by aysiu on 2006-07-20
I think we should start with bug reports. If they don't get answered for a while, then we should figure out how to go into together on a bounty... unless there are people who have more than $10 to spare (my wife is in school, so $10 is about how much I could spare, too).

---

### Post by xtacocorex on 2006-07-20
I'll start seeing if I can break stuff. I might have to set up another computer, assuming I can find one, so I don't destroy my laptop with the projects I'm working on, but I'm going to back them up by the weekend.

[https://launchpad.net/products/sudo/+bugs](https://launchpad.net/products/sudo/+bugs)
I just checked launchpad and it seems that there are no bug reports for sudo.

---

### Post by aysiu on 2006-07-21
Well, here are some bug reports:
[https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/53592](https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/53592)
[https://launchpad.net/distros/ubuntu/+bug/53593](https://launchpad.net/distros/ubuntu/+bug/53593)
[https://launchpad.net/distros/ubuntu/+source/sudo/+bug/53594](https://launchpad.net/distros/ubuntu/+source/sudo/+bug/53594)

---

### Post by aysiu on 2006-07-21
Well, the auto-backup of the /etc/sudoers file (importance--wish list; status--rejected) got rejected:
[quote=Martin Pitt]

The same could be said about any other file in the system. That's why there are backup programs, so that you do not need to duplicate this functionality to a multitude of editors, and do not clutter the disk with lots of copies.

Please use a proper backup solution for things like this. An interesting way I use myself is to put /etc/ under revision control, that makes it very handy to retain history.[/quote] The problem is that inexperienced users don't necessarily back up stuff like that, and unlike /etc/X11/xorg.conf (which *does* get auto-backed up), the /etc/sudoers file cannot be reproduced without help from online.

If I screw up my /etc/X11/xorg.conf file, I can just do ```
sudo dpkg-reconfigure xserver-xorg
``` and get a standard file regenerated. If I screw up the /etc/sudoers file... well, I'd better have an online connection to ask someone on these forums to post their file so I can copy it... and I may not be able to do it "easily" since I'll be in recovery mode.

---

### Post by bruce89 on 2006-07-21
> **aysiu said:**
> Well, the auto-backup of the /etc/sudoers file (importance--wish list; status--rejected) got rejected:

I commented on it, didn't realise it was rejected. :
Gedit creates a backup copy of any file it edits by default, not sure about other text editors.

---

### Post by aysiu on 2006-07-21
Well, maybe we should encourage new users to edit the /etc/sudoers file with [i[gedit[/i] instead of *vi*.

As it is now, most documentation says to use ```
sudo visudo
```

---

### Post by scxtt on 2006-07-21
looking @ the manpage for nano (which is used by default when you do a visudo) adding the -B flag (as in nano -B) will automatically create a /etc/sudoers~ file upon saving the new one ... i'm not sure how visudo works (is it just an alias?) - but if it could be implemented as **sudo nano -B /etc/sudoers** - then there's your automatic backup ...

---

### Post by aysiu on 2006-07-21
Oh, it's *nano* that's used by default? For some reason, I thought it was *vi*.

Thanks for the tip, scxtt. Theoretically, though, shouldn't people use *sudo visudo*, since it checks for syntax errors?

---

### Post by scxtt on 2006-07-21
i'm not sure - using **sudo visudo** or **sudo nano -B /etc/sudoers** produces the same output on the screen (and i don't want to 'test it' on the off chance editing the file does goof it up, tho i doubt it) - tho i was able to confirm that the -B flag in nano does work as intended w/ a normal txt file ... but even if using nano on it's own doesn't check for errors, you still have a backup until you can figure out the correct syntax ...

---

### Post by aysiu on 2006-07-21
Yeah, I think I would prefer people having a backup to using the correct syntax.

After all, the correct syntax could leave you with everyone having administrative privileges... or no one having them!

A backup file, however, will allow you to easily restore functionality. I'm going to advise ```
sudo nano -B /etc/sudoers
``` from now on.

---

### Post by aysiu on 2006-07-22
Apparently [one of my bug reports](https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/53592) is a duplicate of [ an existing bug report](https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/12154).

For the existing one, it doesn't sound as if the developers are going to implement it any time soon.

So far--1 rejected, 1 soon to be rejected, and 1 unconfirmed.

It's not looking good for the home team.

As I suspected earlier, the developers are living in an imaginary world where only knowledgeable users who are comfortable with the terminal would be accessing system files and "ordinary users" wouldn't have to concern themselves with configuring the system.

Ideally, if Ubuntu came preinstalled on more computers, that would be the case.

But let's face the facts--most people who install Ubuntu are ex-Windows users who are used to point-and-click. And most people who use Ubuntu are also people who *install* Ubuntu.

It's not like Dell installs and configures Ubuntu for some schmuck on the street who can't burn an ISO or edit the /etc/X11/xorg.conf file...

---

### Post by DoktorSeven on 2006-07-22
> **aysiu said:**
> Yeah, I think I would prefer people having a backup to using the correct syntax.

After all, the correct syntax could leave you with everyone having administrative privileges... or no one having them!

A backup file, however, will allow you to easily restore functionality. I'm going to advise ```
sudo nano -B /etc/sudoers
``` from now on.

Nice to have a backup of sudoers, but visudo does sanity checks and locking of the file to prevent simultaneous editing (not as big of a problem on a desktop system, I grant you).  Besides, it is the absolutely most correct way to edit sudoers.  As I've stated before, the EDITOR environment variable can be set to whatever editor you want to, including gedit, nano, etc., and backing up files you edit in /etc should be done anyway (**sudo cp /etc/sudoers /etc/sudoers.backup** works fine).

Sorry, I'm a huge advocate of doing things the proper way so that bad habits won't be learned, and the proper way to edit /etc/sudoers is with **visudo**.

---

### Post by scxtt on 2006-07-22
yes, what you say is true (and just the current 'policy', right or wrong) but aysiu is basically saying it's not enough - thinking 'oh, i should backup /etc/sudoers' isn't a solution [ not everyone needs a solution to this, granted - but i think aysiu is looking to better how it's handled for the less savvy and hoping the devs can make use of it ] ... besides remembering to set the $EDITOR variable is asking just as much of a 'newbie' as someone who could handle this anyway ...

and i don't really see the point of these 'sanity checks' when using **sudo visudo** presents you w/ the same file to edit as **sudo nano -B /etc/sudoers**, yes it may lock the file, but how many people that have root access are going to be editing /etc/sudoers @ the same time anyway - i'd rather have a backup if i 'goof up' then have these sanity checks looking over my shoulder ...

i suppose i look at this more as providing options to users, because i certainly see benefits to visudo, but i also see how it can be overwhelming to properly use it ...

---

### Post by DoktorSeven on 2006-07-22
Generally, common users won't have any reason to modify it in the first place, but if they do, it's always better to learn the right way to do things rather than the wrong way.  I've always thought that telling people to do things the right way -- even if doing so might require them to do something they're not used to -- is the best way to do it.  And in the process, they might learn something (*gasp!*).

Education is always good, even if you have to drag someone through it kicking and screaming. ;)

---

### Post by scxtt on 2006-07-22
i don't disagree w/ that - trust me ... i can think of a lot of things worse than actually learning how to do something (new), but i do see the validity in making sudoers a little less cryptic ...

---

