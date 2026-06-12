---
title: "Unappreciated embellishments in Jaunty"
date: 2009-05-07
forum: The Cafe
---

### Post by jimbob on 2009-05-07
Jaunty is becoming a PITA.  Why can't I close a terminal by clicking the X in the upper right corner without being informed that someone is using it?  Of course someone is using it - it's ME! and I've decided I'm through with it.

Thanks for adding additional clicks fellas.  It really speeds up my work ...

---

### Post by LightB on 2009-05-07
Say wuuttttt????

---

### Post by CraigPaleo on 2009-05-07
> **jimbob said:**
> Jaunty is becoming a PITA.  Why can't I close a terminal by clicking the X in the upper right corner without being informed that someone is using it?  Of course someone is using it - it's ME! and I've decided I'm through with it.

Thanks for adding additional clicks fellas.  It really speeds up my work ...

That only happens if you're running something in the terminal and have not quit it, not every time you close it.

---

### Post by jimbob on 2009-05-07
True, but that's the way I usually run.

When you start adding little warnings and pop-ups you start moving toward "Operating Systems for Dummies" and away from the old Unix traditions and looking like another widely used OS I know.

Come on, we're all grown-up here and if I want to cd to root and do an rm -rf * then that's what I want to do.  It's my system and I can accept the consequences of my actions without being treated like a moron.

---

### Post by phaed on 2009-05-07
> **CraigPaleo said:**
> That only happens if you're running something in the terminal and have not quit it, not every time you close it.

Yes, and in that vain, it's a smart feature to have so people don't lose data.

---

### Post by Therion on 2009-05-07
[COLOR="White"].[/COLOR]

---

### Post by calrogman on 2009-05-07
Enjoy your zombie processes.

Actually, I think this is a brilliant feature, but that's because A) I'm clumsy and B) I use Folding @ Home.

---

### Post by Bodsda on 2009-05-07
> **phaed said:**
> Yes, and in that vain, it's a smart feature to have so people don't lose data.

I dont understand this... Since when and why is it the operating systems problem if the user is not smart?

If i clicked the x its because I want to close the program, If it was an accident, my fault, live with it. It's hardly likely that I would lose any data, most programs create backups upon opening the file anyway.

I really think this is one of the major downfalls, maybe its just me but I really hate being asked for confirmation for trivial things like closing programs.

---

### Post by Bodsda on 2009-05-07
> **jimbob said:**
> True, but that's the way I usually run.

When you start adding little warnings and pop-ups you start moving toward "Operating Systems for Dummies" and away from the old Unix traditions and looking like another widely used OS I know.

Come on, we're all grown-up here and if I want to cd to root and do an rm -rf * then that's what I want to do.  It's my system and I can accept the consequences of my actions without being treated like a moron.

Totally agree! +1

---

### Post by CraigPaleo on 2009-05-07
I didn't like the way the fast user switch did that either so, I turned the confirmations off. 

There must be a way to turn confirmations off in the terminal, I would think.

---

### Post by Bodsda on 2009-05-07
> **CraigPaleo said:**
> I didn't like the way the fast user switch did that either so, I turned the confirmations off. 

There must be a way to turn confirmations off in the terminal, I would think.

Yes you can,

```
gconf-editor
```

/ >> apps >> gnome-terminal >> glabal >> untick 'confirm_window_close'

---

### Post by Bölvaður on 2009-05-07
why use the mouse to click the x if you can```
exit
```

---

### Post by CraigPaleo on 2009-05-07
> **Bodsda said:**
> Yes you can,

```
gconf-editor
```

/ >> apps >> gnome-terminal >> glabal >> untick 'confirm_window_close'

That was fast!

---

### Post by jimbob on 2009-05-07
> Enjoy your zombie processes.
That's OK, there's 53 tty's in the /dev directory, they don't soak up any CPU cycles and they will be gone in the morning when I boot up.

---

### Post by jimbob on 2009-05-07
> 
Code:

gconf-editor

/ >> apps >> gnome-terminal >> glabal >> untick 'confirm_window_close'
Thanks for that!

---

### Post by Bodsda on 2009-05-07
> **jimbob said:**
> Thanks for that!

No problem :)

take a look at 
```
gconftool-2
```
to automate it, you can change key values with it, so you could alias the command and then be able todo

```
foo@bar:~$ prompt_on
foo@bar:~$ prompt_off

```

if you really wanted to

---

### Post by Sublime Porte on 2009-05-07
sudo apt-get install mrxvt

If you don't like the 'features' of a program, chances are there's 10 or so alternative programs you can use.

---

### Post by Rainstride on 2009-05-07
> **Bodsda said:**
> I dont understand this... Since when and why is it the operating systems problem if the user is not smart?

If i clicked the x its because I want to close the program, If it was an accident, my fault, live with it. It's hardly likely that I would lose any data, most programs create backups upon opening the file anyway.

I really think this is one of the major downfalls, maybe its just me but I really hate being asked for confirmation for trivial things like closing programs.

because human beings are stupid and make mistakes, and this is linux for human beings.:)

---

### Post by pastalavista on 2009-05-07
I always use alt-f4 to close a window and enter to confirm if there's a pop-up. That's only 3 keystrokes... easier than reaching for the mouse

---

### Post by phaed on 2009-05-07
That's my feeling.  Ubuntu is not Unix.  Ubuntu is Linux for Human Beings.  If you want an OS that doesn't coddle you, there are other options.

---

### Post by baseface on 2009-05-07
if you want something that isnt "linux for dummies" or whatever you, op, said, then dont use ubuntu. ubuntu is made for people who dong know anything about linux. SO of course its going to throw extra warnings at you.
"omg i have to click one more time because i dont know how to properly kill a process".
thats your fault.

---

### Post by Bodsda on 2009-05-07
Since when has being a human meant that you have to be asked for confirmation when doing something.

Does your toilet ask you for confirmation before it flushes? No, so why should your computer ask you for confirmation before it kills a process.

Human Beings may be uneducated, but they are by no means stupid.

---

### Post by jimbob on 2009-05-07
> f you want something that isnt "linux for dummies" or whatever you, op, said, then dont use ubuntu. ubuntu is made for people who dong know anything about linux
If they don't know anything about Linux, what are they doing opening up terminal windows??

PS:  What is "dong"?

---

### Post by CraigPaleo on 2009-05-07
> **phaed said:**
> That's my feeling.  Ubuntu is not Unix.  Ubuntu is Linux for Human Beings.  If you want an OS that doesn't coddle you, there are other options.

I agree but there should also be an obvious option such as "don't show this warning again." That would be ideal for all users.

---

### Post by baseface on 2009-05-07
whoops.

---

### Post by baseface on 2009-05-07
> **jimbob said:**
> If they don't know anything about Linux, what are they doing opening up terminal windows??
 
PS: What is "dong"?
 
obviously theyre starting processes that they dont know how to terminate properly.
it doesnt take a genius to open up a shell and type some bs.

---

### Post by Bodsda on 2009-05-07
> **CraigPaleo said:**
> I agree but there should also be an obvious option such as "don't show this warning again." That would be ideal for all users.

At least there are some people who can see both sides, thank you

---

### Post by baseface on 2009-05-07
> **jimbob said:**
> If they don't know anything about Linux, what are they doing opening up terminal windows??
 
PS: What is "dong"?
 
dont you think your sig is a bit hypocritical?
you use ubuntu, but your sig says crap about doing stuff from the command line like it was intended. why are you running ubuntu... a distro that configures EVERYTHING for you in a nice, pretty graphical environment?

---

### Post by Bodsda on 2009-05-07
> **crackdealer said:**
> dont you think your sig is a bit hypocritical?
you use ubuntu, but your sig says crap about doing stuff from the command line like it was intended. why are you running ubuntu... a distro that configures EVERYTHING for you in a nice, pretty graphical environment?

So people are not allowed to use the terminal on ubutnu? 

The terminal is the most powerful tool you have on a computer, and most people who are not recent converts will know this, and those that feel comfortable with it will utilize it.

---

### Post by jimbob on 2009-05-07
> at least there are some people who can see both sides, thank you
++1

---

### Post by swoll1980 on 2009-05-07
I'm glad it reminds me. I close a terminal, out of habit, not remembering that it has an app attached to it, then the app closes. That's a lot more trouble than an extra click. If you want to be all super leet, just throw your mouse in the garbage, those things are for noobs anyways.

---

### Post by Bodsda on 2009-05-07
Thank goodness for the ampersand

```
firefox www.google.com &
```

---

### Post by Keyper7 on 2009-05-07
Guys, could you please stop arguing about something that's essentially a personal opinion that varies from user to user? There's no right or wrong here.

---

### Post by Bodsda on 2009-05-07
> **Keyper7 said:**
> Guys, could you please stop arguing about something that's essentially a personal opinion that varies from user to user? There's no right or wrong here.

Who is arguing?

I was having a debate

---

### Post by Vitamin-Carrot on 2009-05-07
And I am eating toast

---

### Post by Bodsda on 2009-05-07
> **Vitamin-Carrot said:**
> And I am eating toast

Does your toast ask you to confirm that you wish to bite it?

---

### Post by Keyper7 on 2009-05-07
> **Bodsda said:**
> Who is arguing?

I was having a debate

Let's debate if you were having a debate.

I think the issue is too personal. It's like "debating" if apples taste better than oranges.

---

### Post by Bodsda on 2009-05-07
> **Keyper7 said:**
> Let's debate if you were having a debate.

I think the issue is too personal. It's like "debating" if apples taste better than oranges.

You think the issue of dumbing down the user interface is personal?

I'm not sure whether its actually ubuntu or gnome to blame... any ideas?

---

### Post by phaed on 2009-05-07
> **Bodsda said:**
> I dont understand this... Since when and why is it the operating systems problem if the user is not smart?

Since users on all platforms have demanded that kind of functionality.  That's what Canonical set out to do: make Linux easy for non-experts.

The point isn't whether an operating should do this or that, since people will have different software philosophies than you.  The point is that the OS should be customizable, and as we've seen, you can turn that prompt off in gconf-editor.

You still have far more control over GNOME than Windows.

---

### Post by mister_pink on 2009-05-07
I like the idea of having an option not to show it again, or at least putting a tick box in the options that toggles the gconf value. Should be easy to do.

I actually quite like it. The shutdown one annoyed me because I had already done two clicks to get there anyway, so I turned that off. 

I've left the terminal one on, because if I have loads of terminals open and decide to close them all I might not notice one is running an app, especially if its a gui one. I've closed gedit with unsaved work in it plenty of times before now. Even if it is saved it still takes me ages to open it all back up again vs occasionally having to click again.

---

### Post by Keyper7 on 2009-05-07
> **Bodsda said:**
> You think the issue of dumbing down the user interface is personal?

More than that. The definition of "dumbing down" is personal.

On this one-hour thread alone there is already more than one person who does not agree with yours.

---

### Post by Bodsda on 2009-05-07
But then we get to the issue of, which should be default, 

should it prompt first and if you dont like it you can trawl through a settings manager until you stumble accross the right key 

or

Should it not prompt and let you 'learn' the hard way so that you actually understand things a little bit better, then with an informed decision you can trawl the settings manager to turn it on,

personally i think it should be the latter, if you want to be treated like a four year old, buy a mac

---

### Post by Bodsda on 2009-05-07
> **Keyper7 said:**
> More than that. The definition of "dumbing down" is personal.

On this one-hour thread alone there is already more than one person who does not agree with yours.

Your still failing to get across any actual point though. what was that post supposed to show, that not everyone agrees with me? Of course they dont.

---

### Post by Keyper7 on 2009-05-07
> **Bodsda said:**
> Your still failing to get across any actual point though. what was that post supposed to show, that not everyone agrees with me? Of course they dont.

The point is simple: there is no right or wrong in this issue.

---

### Post by Dharmachakra on 2009-05-07
Sounds like a gross overreaction to me.

---

### Post by Sealbhach on 2009-05-07
> **jimbob said:**
> 

When you start adding little warnings and pop-ups you start moving toward "Operating Systems for Dummies" and away from the old Unix traditions and looking like another widely used OS I know.
.

I think that's the point of Ubuntu. Its' "Linux for the rest of us". 


.

---

### Post by Bodsda on 2009-05-07
hmm, maybe i should head over to LFS and do some downloads tonight, lol :)

---

### Post by Bodsda on 2009-05-07
> **Sealbhach said:**
> I think that's the point of Ubuntu. Its' "Linux for the rest of us". 


.

Yeah, but its not Linux that is prompting you. The kernel doesnt care if you loose work. Its the distribution and the DE that is the problem (not saying ubuntu is a problem) so that fact that its 'Linux for the rest of us' makes no difference really, its still the same engine, just a different body kit

---

### Post by swoll1980 on 2009-05-07
> **Bodsda said:**
> But then we get to the issue of, which should be default, 

should it prompt first and if you dont like it you can trawl through a settings manager until you stumble accross the right key 

or

Should it not prompt and let you 'learn' the hard way so that you actually understand things a little bit better, then with an informed decision you can trawl the settings manager to turn it on,

personally i think it should be the latter, if you want to be treated like a four year old, buy a mac

Think of it this way. Anyone that doesn't know what they are doing will appreciate the warning. Anyone that does know what they're doing can find away around it. I made this same argument for the update manager, it's for people that aren't "computer people" the people that update their systems voluntarily  are the ones that know what they are doing and will find a way around it.

---

### Post by Sealbhach on 2009-05-07
As I understand it, Ubuntu is unashamedly an end user distro. It's not envisaged that most users will aspire to learning the command line, though they can if they want to. 

It's for people who want to look at Facebook all day long and nothing else.  

I see people complaining that Ubuntu is turning out like Windows and I wonder why they're not using Gentoo or something else.

.

---

### Post by CarpKing on 2009-05-07
> **Keyper7 said:**
> The point is simple: there is no right or wrong in this issue.

Perhaps the same could be said of all threads in the Cafe.  But if we don't discuss anything that doesn't have a right or wrong, it won't be a very interesting forum.

---

### Post by Sealbhach on 2009-05-07
> **Bodsda said:**
> Yeah, but its not Linux that is prompting you. The kernel doesnt care if you loose work. Its the distribution and the DE that is the problem (not saying ubuntu is a problem) so that fact that its 'Linux for the rest of us' makes no difference really, its still the same engine, just a different body kit

Sorry, I wasn't really intending to mean the kernel, how about "a GNU/Linux based distro for the rest of us"?:)

.

---

### Post by Sealbhach on 2009-05-07
> **CarpKing said:**
> Perhaps the same could be said of all threads in the Cafe.  But if we don't discuss anything that doesn't have a right or wrong, it won't be a very interesting forum.

That's a moot point.:)

*dang* i can't stop spamming this thread!


.

---

### Post by happysmileman on 2009-05-07
KDE's Konsole doesn't do this.

There, argument over, you may now unite against KDE. :P

---

### Post by swoll1980 on 2009-05-07
> **Sealbhach said:**
> As I understand it, Ubuntu is unashamedly an end user distro. It's not envisaged that most users will aspire to learning the command line, though they can if they want to. 

It's for people who want to look at Facebook all day long and nothing else.  

I see people complaining that Ubuntu is turning out like Windows and I wonder why they're not using Gentoo or something else.

.

That's the funny part about Linux, everyone's all like it needs this, and that, then when a distro starts to do those things, they're "selling out"

---

### Post by CraigPaleo on 2009-05-07
> **swoll1980 said:**
> I made this same argument for the update manager

Is [this]("http://ubuntuforums.org/showthread.php?p=7233659#post7233659") what you were talking about regarding the update manager?

---

### Post by swoll1980 on 2009-05-07
> **CraigPaleo said:**
> Is [this]("http://ubuntuforums.org/showthread.php?p=7233659#post7233659") what you were talking about regarding the update manager?

The fact that it now has an in your face, update me now approach, rather than the quite icon that sits unattended by all, but the computer enthusiast. I installed Linux on my buddies, and my aunts computer, and both went the whole release cycle w/o updating once.

---

### Post by DougieFresh4U on 2009-05-07
Some one 'higher up' is having an awful time with Ubuntu, first their fingers are flying around the keyboard, hitting wrong keys (Contrl-alt-Delete) and x restarts, and they lost work and now they close terminal and (lost work), omg, :o  what next??
Sorry couldn't resist the chance to bring the 'control-alt-delete' crap again.
(I'm having a little fun :P:P)

---

### Post by Bodsda on 2009-05-07
> **DougieFresh4U said:**
> Some one 'higher up' is having an awful time with Ubuntu, first their fingers are flying around the keyboard, hitting wrong keys (Contrl-alt-Delete) and x restarts, and they lost work and now they close terminal and (lost work), omg, :o  what next??
Sorry couldn't resist the chance to bring the 'control-alt-delete' crap again.
(I'm having a little fun :P:P)

Apart from the fact that ctrl+alt+delete doesnt restart x and to my knowledge never did, maybe your thinking of ctrl+alt+backspace, but how anyone could hit that combo by accident is beyond me

---

### Post by Hells_Dark on 2009-05-07
… new gnome version, new xorg version…

All of this are not ubuntu choices…

Am i wrong ?

---

### Post by swoll1980 on 2009-05-07
> **Hells_Dark said:**
> … new gnome version, new xorg version…

All of this are not ubuntu choices…

Am i wrong ?

All these things can be changed, so the default settings are up to Ubuntu

---

### Post by CraigPaleo on 2009-05-07
> **swoll1980 said:**
> The fact that it now has an in your face, update me now approach, rather than the quite icon that sits unattended by all, but the computer enthusiast. I installed Linux on my buddies, and my aunts computer, and both went the whole release cycle w/o updating once.

It's probably a bug then. The problem for me and some others is that it's not in your face at all!

---

### Post by 23meg on 2009-05-07
> **swoll1980 said:**
> The fact that it now has an in your face, update me now approach, rather than the quite icon that sits unattended by all, but the computer enthusiast. I installed Linux on my buddies, and my aunts computer, and both went the whole release cycle w/o updating once.

Stable release updates are not meant for "all but the computer enthusiast"; they are meant for all users. Not installing them is not any more advisable practice for your aunt than for your geek friend. It's just that the tool used for installing them (the update manager) *can* also be used by the enthusiast for other purposes than installing them as well. If its interface cannot communicate the importance of its primary function (which it couldn't; an arrow pointing down does not communicate "I do something important regarding the health of your computer" to a significant portion of users, perhaps including your friends and aunt) reasonably well, it's not a good interface.

Case in point: bad interfaces encourage bad practices, and since people will tend to take the interface norms they are given for granted and adjust their actions accordingly, they become tradition.

---

### Post by swoll1980 on 2009-05-07
> **23meg said:**
> Stable release updates are not meant for "all but the computer enthusiast"; they are meant for all users. 

I know. That's why I like the in your face approach, it lets the "myspacers" know that this needs to be done. The icon was just ignored.

---

### Post by gymophett on 2009-05-07
You had to click twice?! Oh god! Someone please help Ubuntu get this straight! :|

Are you serious, some people just don't want things messed up during the middle of installing packages so it makes you click twice only during the middle of a process. Which is good. If you don't like it, simply turn it off.

---

### Post by Keyper7 on 2009-05-07
> **CarpKing said:**
> Perhaps the same could be said of all threads in the Cafe.  But if we don't discuss anything that doesn't have a right or wrong, it won't be a very interesting forum.

I have nothing against discussing subjects that do not have a right or wrong.

What I am against is *stating a right or wrong* in subjects that do not have a right or wrong.

Claiming that a certain behavior should be the default "because I don't like it" is essentially that.

It's like the endless "the music player I use should be the default" discussions.

---

### Post by Bodsda on 2009-05-08
> **Keyper7 said:**
> 
It's like the endless "the music player I use should be the default" discussions.

That is a pointless thread I agree, but "the music player I use should be the default **[SIZE="3"]because[/SIZE]**" is a much better thread

---

