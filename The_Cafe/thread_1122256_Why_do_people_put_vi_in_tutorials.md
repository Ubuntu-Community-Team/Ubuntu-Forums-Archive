---
title: "Why do people put vi in tutorials?"
date: 2009-04-10
forum: The Cafe
---

### Post by PacSci on 2009-04-10
Many times, when people are writing Linux tutorials (often including ones aimed at beginners), they use commands of the form:

```
sudo vi /important/system/file
```

I'm not here to argue about whether vi is superior to emacs, ed, nano, or gedit. That's already being done. What I'm questioning is: why do people writing tutorials assume that the user of the tutorial know how to use vi? I've been using Linux regularly for months, often using the Mac terminal before that, and had Linux exposure intermittently within the past few years, but I still am hopeless within vi - in fact, I almost think that I'm better at ed than vi.

I think that when tutorials are being written, the writers should use "nano" when talking about editors (or, if it's Debian-derivative-specific, "sensible-editor"). But I'm trying to figure out how the "type 'vi' whenever the user needs to edit a file" thing got started. Yes, many people use "nano" or "gedit" in their tutorials, but many write "vi", and I don't think telling anyone to use vi is the best way to get them to keep using Linux.

"But it's the standard!" No it's not. ed is the standard. Besides, just because something is the standard doesn't mean that it's a good reason to throw users into it with no instruction if it's marginally harder than something else.

"They're going to have to learn to use it anyway!" Not really. I can't remember a single instance during my time with any OS ending in X that I have **had** to use vi. Instead, I gradually picked it up on my own time. In the meantime, a more intuitive editor can be used.

If someone told me, with no explanation, to type "sudo vi /important/system/file" into a terminal and make a change, the computer would beep repeatedly and I might end up breaking everything. Can anyone explain why "vi" is used as the editor in tutorials?

*P.S. In the interest of full disclosure, my favorite editors are nano on the console and gedit in the GUI.*

---

### Post by Mehall on 2009-04-10
vi has been around for a smidgen longer I believe?

---

### Post by SuperSonic4 on 2009-04-10
Probably because a lot of the authors use vi

---

### Post by Sporkman on 2009-04-10
I find vi to be impossible to use. The first thing I do on a new commandline-only system is build & install nano.

---

### Post by Mehall on 2009-04-10
to get to nano-style editing mode: press "i"

to return to "normal" (non-edit) mode press escape.

to save and quit, in "normal" mode, ":wq" (without quotes)

If ever in doubt, thats all you need to know to be able to use vi(m) if you ever absolutely have to.

---

### Post by swoll1980 on 2009-04-10
Perhaps the geek gods will rain fire upon them if they suggest nano instead.

---

### Post by Sporkman on 2009-04-10
> **Mehall said:**
> to get to nano-style editing mode: press "i"

to return to "normal" (non-edit) mode press escape.

to save and quit, in "normal" mode, ":wq" (without quotes)

If ever in doubt, thats all you need to know to be able to use vi(m) if you ever absolutely have to.

No - I tried that on a solaris box today - backspace & arrow keys screwed everything up - lines & funny characters got inserted, and I couldn't delete them.

---

### Post by cariboo on 2009-04-10
I have been using Linux for about 10 years, and I still don't like vi. My preferred editors are mc and nano. If I ever get around to writing a tutorail for newbies, I'll be sure to specify nano.

Jim

---

### Post by FuturePilot on 2009-04-10
I'm guessing because just about every distro ships with vi so it's pretty much guaranteed to be there. I have yet to come across a distro that did not have vi installed. However I have come across distros that don't have nano installed by default.

---

### Post by Kareeser on 2009-04-10
Somewhere out there, a hardcore linux geek is crying because you picked nano over vi :)

I can certainly understand that from a coding standpoint, learning vi can be a lot more efficient, since there are tools there to copy and paste multiple lines, and manipulate character strings, all through the keyboard!

However, for simple tutorials and short scripting, nano wins since it's quick and painless :)

---

### Post by kevdog on 2009-04-10
Man up -- vi is for winners.  nano is for whiners!  Glad I could clear some things up! :)

---

### Post by SomeGuyDude on 2009-04-10
Vi just baffles me. For the life of me I can't figure out what it can do that I can't do much more easily in nano, especially things like what your average user needs.

---

### Post by kdorf on 2009-04-10
Firstly... vim > vi (and no, they are not the same). 

> **SomeGuyDude said:**
> Vi just baffles me. For the life of me I can't figure out what it can do that I can't do much more easily in nano, especially things like what your average user needs.

The reason is because you haven't used vi/vim long enough to see what it can do to save you time. It's a thinking man's editor, that much you can be sure of, but it works well.

---

### Post by SomeGuyDude on 2009-04-10
Give me a task that vi/vim makes easier for me, and no I'm not joking around. Like, gimme an example of what it can do that makes it great. I'm being genuine because if I'm really shortchanging myself I'd like to know.

---

### Post by sekinto on 2009-04-10
Because Vi is garrentied to be on almost every Linux install, I think having Vi is actually one of the things required to be Posix-complient. xD

Users would be really confused if they typed nano <something> and got:
bash: nano: command not found

---

### Post by Kareeser on 2009-04-10
> **SomeGuyDude said:**
> Give me a task that vi/vim makes easier for me, and no I'm not joking around. Like, gimme an example of what it can do that makes it great. I'm being genuine because if I'm really shortchanging myself I'd like to know.

You have local access to a server that doesn't have a mouse. You have a keyboard. The nearest computer store is an hour and a half away. You have a screaming wife who wants her latest episode of scrubs available on the network ASAP.

To do this, you have to edit a config file and move several large chunks of code from one section to another (think Apache's <Directory> sections).

Go.

---

### Post by samjh on 2009-04-11
As others have said, it's because vi is installed in almost every Unix and Linux system.

Nano or pico, are not.  (Although IMHO they should be, as they are more conventional and easier to use for beginners than vi.)

<- Vim user.

---

### Post by SomeGuyDude on 2009-04-11
> **Kareeser said:**
> You have local access to a server that doesn't have a mouse. You have a keyboard. The nearest computer store is an hour and a half away. You have a screaming wife who wants her latest episode of scrubs available on the network ASAP.

To do this, you have to edit a config file and move several large chunks of code from one section to another (think Apache's <Directory> sections).

Go.

Nano.

Ctrl+K every single line I need.

Go to where I need the text.

Ctrl+U.

Funny thing was, I figured that out just opening nano and noticing what the little list of commands was at the bottom.

---

### Post by sekinto on 2009-04-11
> **kareeser said:**
> you have local access to a server that doesn't have a mouse. You have a keyboard. The nearest computer store is an hour and a half away. You have a screaming wife who wants her latest episode of scrubs available on the network asap.

To do this, you have to edit a config file and move several large chunks of code from one section to another (think apache's <directory> sections).

Go.

IMA CHARGIN MAH REGULAR EXPRESSIONS

Edit: Stupid forums won't let me post in all caps. ]:
Edit2: I guess it works if you have some non-caps text.

---

### Post by chucky chuckaluck on 2009-04-11
while vi may be universal, knowing how to do something as simple as saving the text file you are creating/editing/asterisking the asterisks out of, is not. nano will do in nearly all cases.


> **kevdog said:**
> Man up -- vi is for winners.  nano is for whiners!  Glad I could clear some things up! :)

aren't you a vim user?

---

### Post by Icehuck on 2009-04-11
I find I'm really not liking VI/VIM now that I'm starting to switch to the Dvorak keyboard layout. 

That said, if you are new there is no way you are figuring out how to do anything in VI/VIM. The first time I used it I mashed buttons to get it to insert text. I could not for the life of me figure out how to save and exit.

---

### Post by SomeGuyDude on 2009-04-11
> **chucky chuckaluck said:**
> while vi may be universal, knowing how to do something as simple as saving the text file you are creating/editing/asterisking the asterisks out of, is not. nano will do in nearly all cases.

This. Nano makes a lot of sense and is great for most any tasks. Even if you're brand spanking new to it, you can open 'er up and get things done.

---

### Post by -grubby on 2009-04-11
> **FuturePilot said:**
> However I have come across distros that don't have nano installed by default.

Such as? I'm completely baffled as to why a distro wouldn't include nano...

---

### Post by p_quarles on 2009-04-11
> **SomeGuyDude said:**
> Nano.

Ctrl+K every single line I need.

Go to where I need the text.

Ctrl+U.

Funny thing was, I figured that out just opening nano and noticing what the little list of commands was at the bottom.
If Nano works for you, then you probably don't need VI/Vim. What it does, though, is provide a much more full-featured interface. Yes, it's easy to delete a single word using Nano, but Nano's approach is to make you press "delete" while each individual character os that word is highlighted. In Vim, it's two keystrokes:
```
d$
```
That deletes the string that's currently underneath the cursor. That's just one example, of course: it basically allows fine-grained editing of words, blocks, and entire documents with simple one line commands. In the example you gave, no, learning Vim isn't likely to pay off. However, it does allow you perform to larger-scale tasks much more quickly and easily. 

As for the question raised by the thread: most tutorials I've seen that suggest using Vim are on advanced enough topics that a user who doesn't know how to choose a different editor would probably be advised to get some help before proceeding. At least that's my experience.

---

### Post by SomeGuyDude on 2009-04-11
And tell me how one should know d$, or for that matter why in the world that's the command anyway.

The point is vi si a REALLY unintuitive and unnatural little piece of software that may very well be super useful when you're dealing with incredibly advanced tasks but for some reason lack a GUI, but there is NO reason to make someone using a simple tutorial learn the goofy haphazard keyboard commands vi throws at them.

I'm not a big believer in dumbing things down, but I -am- big on necessary tools for the job, and vi is using a computer guided heat-seeking missile to knock down a fence. It shouldn't be the default text editor, it's the kind of thing introduced to someone when they start having tasks nano isn't up for.

Thank the lawd Archs tutorial is all about nano or I'd probably NEVER have finished installing.

---

### Post by FuturePilot on 2009-04-11
> **nathangrubb said:**
> Such as? I'm completely baffled as to why a distro wouldn't include nano...

I know OpenSuse doesn't.

---

### Post by kevdog on 2009-04-11
Taking time to switch to Linux/Ubuntu = Priceless

Not learning vi/vim = Ridiculous

nano is for my mother!

---

### Post by SomeGuyDude on 2009-04-11
Then your mother has the good sense to realize what tool is the most useful for the task at hand. ;)

---

### Post by kevdog on 2009-04-11
but my mother wouldn't be using ubuntu either!  Heck she wouldn't even be using notepad either!  Its M$Word or bust!

---

### Post by p_quarles on 2009-04-11
> **SomeGuyDude said:**
> And tell me how one should know d$, or for that matter why in the world that's the command anyway.

The point is vi si a REALLY unintuitive and unnatural little piece of software that may very well be super useful when you're dealing with incredibly advanced tasks but for some reason lack a GUI, but there is NO reason to make someone using a simple tutorial learn the goofy haphazard keyboard commands vi throws at them.

I'm not a big believer in dumbing things down, but I -am- big on necessary tools for the job, and vi is using a computer guided heat-seeking missile to knock down a fence. It shouldn't be the default text editor, it's the kind of thing introduced to someone when they start having tasks nano isn't up for.

Thank the lawd Archs tutorial is all about nano or I'd probably NEVER have finished installing.
Right, you're missing my point. Vim is not for occasions on which one lacks a GUI "for some reason." It's a radically more efficient way of doing things than a point-and-click interface could possibly be. Again, for simple tasks, the learning curve is probably too steep to be worth the effort for most users. But it's still an easier way of doing even moderately less-simple tasks. 

"d" is "delete" and "$" stands for string. The latter is true of various programming languages, so while it may not be intuitive for everyone, it's not arbitrary either. As for "how you're supposed to know," it is just like anything you learn. No one is born knowing how to drive, cook, read, or knit. If you are faced with one of those tasks, you need to learn how first.

---

### Post by speedwell68 on 2009-04-11
I didn't realise that VI was still around.  I used to use VI for coding Pascal at college in the early '90s.  It was bloody awful then.

---

### Post by schauerlich on 2009-04-11
> **speedwell68 said:**
> I didn't realise that VI was still around.  I used to use VI for coding Pascal at college in the early '90s.  It was bloody awful then.

vi largely lives on in the form of vim. It still exists and is useful for situations when you have to use it but most everyone I know uses vim.

---

### Post by Eisenwinter on 2009-04-11
> **SomeGuyDude said:**
> And tell me how one should know d$, or for that matter why in the world that's the command anyway.
**d** is for **d**elete, and **$** is a meta-character in regex that signifies an end-of-line match.

```
my $blah = "vi"; $blah =~ /i$/;
```
This matches, because the string "vi" ends with "i".

---

### Post by Paqman on 2009-04-11
What kind of an idiot would use vim in a tutorial? I'd probably stop reading the tutorial as soon as I saw that, since the author is probably doing everything the needlessly hard way.

---

### Post by sekinto on 2009-04-11
> **Paqman said:**
> What kind of an idiot would use vim in a tutorial? I'd probably stop reading the tutorial as soon as I saw that, since the author is probably doing everything the needlessly hard way.

At least they're not using cat! :D

---

### Post by ice60 on 2009-04-11
a few years a go i was doing a BSD install and had a nightmare adding myself to the wheel group, or whatever you need to edit during the install/setup, i couldn't remember how to delete charactors. i think i ended up going on irc and asking how to install nano lol, they thought i was somekind of lunatic. since then i made sure i know the vi basics. 

thinking now i'm not sure why i didn't man/info/help the stuff i needed. maybe i am a lunatic after all.

---

### Post by ssam on 2009-04-11
most tutorials should be showing GUI ways to do things.

the few times you do actually need to edit a text file, then nano is a better choice to put into the example. vim/emacs uses can easily sub in their own editor. also it might be wise/kind to have a 'if you are not familiar with editing files in linux click here' link, maybe point it to [http://ubuntuforums.org/showthread.php?t=3771](http://ubuntuforums.org/showthread.php?t=3771) unless you know a better one.

i am a vim user. its great for programming. as you gradually learn new commands you can get faster and faster. it has handy things like spell checking, syntax highlighting, code folding, auto indenting, but still quick over a network, and available almost everywhere.

---

### Post by jelle_ on 2009-04-11
> **SomeGuyDude said:**
> Nano.

Ctrl+K every single line I need.

Go to where I need the text.

Ctrl+U.

Funny thing was, I figured that out just opening nano and noticing what the little list of commands was at the bottom.

that sounds really unintuitive to me. i prefer d$ and p.

---

### Post by chucky chuckaluck on 2009-04-11
> **jelle_ said:**
> that sounds really unintuitive to me. i prefer d$ and p.

it doesn't need to be intuitive. it's right there at the bottom of the screen.

---

### Post by smbm on 2009-04-11
> **chucky chuckaluck said:**
> it doesn't need to be intuitive. it's right there at the bottom of the screen.

Ditto

---

### Post by Sporkman on 2009-04-11
> **chucky chuckaluck said:**
> it doesn't need to be intuitive. It's right there at the bottom of the screen.

**Swish!** :)

---

### Post by cardinals_fan on 2009-04-11
I don't see why they should include an editor at all.  If it is deliberately geared toward new users, a suggestion could be made (I would probably recommend nano), but in general "Edit this file" is probably sufficient.

---

### Post by Peasantoid on 2009-04-11
I occasionally use pico/nano, but I prefer vi(m) for some reason.

If you really want to be user-friendly, suggest gedit instead of anything command-line.

---

### Post by yeats on 2009-04-11
I can see everyone's point here, as I was completely baffled by vi when I first came across it, but now I think of it as just a necessary skill for the job at hand, as it is almost certainly going to be included on any *nix install.  You don't have to love it, and only people who love it (or need it) are going to learn all the commands, but if you have some basic vi/vim skills, it will definitely serve you well in certain situations... Anybody been pushed to the BusyBox prompt during an install? (for instance) :-)

---

### Post by Simian Man on 2009-04-11
[LIST]
[*]vi is the standard editor for Unix systems
[*]vi is installed on very nearly every Linux system
[*]vi is what most sysadmins I know use
[/LIST]

If you don't like vi, then you can at least be bothered to learn that it is a text editor and that you can always replace it with your preferred editor.

---

### Post by defaultusername on 2009-04-11
^ What he said ...

I never had trouble learning vi back when. Basic editing commands are not rocket science.

---

### Post by Icehuck on 2009-04-11
> **defaultusername said:**
> ^ What he said ...

I never had trouble learning vi back when. Basic editing commands are not rocket science.

So when you first used VI and if you didn't have anyone showing you or the listed commands you would have been able to use it no problem?

---

### Post by Mehall on 2009-04-11
> **Icehuck said:**
> So when you first used VI and if you didn't have anyone showing you or the listed commands you would have been able to use it no problem?

+1

I was getting frustrated having to use vi from a busybox a while back, ended up mashing the keys and "insert" came up.

I noticed this was text entry mode, what I wanted, entered my text, guessed hitting escape, then wondered... pressed "i", insert again, right, got the basics. Remembered someone telling me ":" was the control character, guessed ":wq" for "write & quit" like in nano (I always do ^W then ^Q ) and was sorted for the basics.

I still prefer nano though.

---

### Post by Polygon on 2009-04-11
nano is easier for noobs. When i was setting up arch linux, the hardest part was just figuring out how to freaking save with vi. I searched the internet for a super long time trying to find the answer, until i found it was esc + :wq. geez.

---

### Post by RiceMonster on 2009-04-11
To learn vim, don't look far. Open up a terminal and type vimtutor, or start vim and type :help

The first time I learned to use vi, I only learned how to go into insert mode, move around with the arrow keys and type : x to save and exit(except with no space, it makes a smiley without one). So it was sort of like using nano. Now that I took the time to learn it properly, other editors don't feel right. Sometimes I'll be writting in visual studio and I'll accidentally type c3w or something. No, it's not intuitive, but that's not the point in it.

Still, if I were writing a newbie tutorial and had to choose an editor to tell them to use, it sure as hell would not be vi/m. If you've never seen it before, you'll have no idea what's going on.

---

### Post by Paqman on 2009-04-12
> **Simian Man said:**
> [LIST]
[*]vi is the standard editor for Unix systems
[*]vi is installed on very nearly every Linux system
[*]vi is what most sysadmins I know use
[/LIST]

If you don't like vi, then you can at least be bothered to learn that it is a text editor and that you can always replace it with your preferred editor.

And all tutorials are written for sysadmins, are they?

---

### Post by 3rdalbum on 2009-04-12
Oh my god, I agree with the OP. The first time I installed Ubuntu, I made a little mistake that caused my user account to not have permission to use sudo (actually, a bug in the Debian installer - long story). I did some research and found that I could boot up in recovery mode and use the "visudo" command to edit the sudoers file.

Visudo started up Vim. Not only did I have to edit this complicated file, but I also couldn't figure out how to use Vim. The easier solution was to reinstall Ubuntu, which I did. I'm sure anyone less adventurous than me would have run away from Ubuntu screaming about this text editor.

I'm sure Vim is great, but you don't want to let newbies use it. Wherever possible I tell people to use Gedit, Mousepad or Kate rather than even Nano, as I can imagine the discussion between the helpee and the helper. ("Why doesn't Control-S save the file? *Saving is done by pressing Control-O.* Why Control-O? *It stands for 'Write Out'.* Why don't they just use Control-S for 'save'?")

---

### Post by Barrucadu on 2009-04-12
Completely off topic, but you can make visudo use any editor you like by setting the EDITOR variable. For example, I use "sudo EDITOR=emacs visudo" when I want to run it.

---

### Post by Polygon on 2009-04-12
> **Simian Man said:**
> [LIST]
[*]vi is the standard editor for Unix systems
[*]vi is installed on very nearly every Linux system
[*]vi is what most sysadmins I know use
[/LIST]

If you don't like vi, then you can at least be bothered to learn that it is a text editor and that you can always replace it with your preferred editor.

nano is also included in almost every single distro i have tried. its not hard to replace the word 'vi' with 'nano' in tutorials =)

---

### Post by Kareeser on 2009-04-12
Odd, Ubuntu uses Nano in visudo :)

Also, I use ctrl-x to save and quit. heh.

---

### Post by Simian Man on 2009-04-12
> **Barrucadu said:**
> Completely off topic, but you can make visudo use any editor you like by setting the EDITOR variable. For example, I use "sudo EDITOR=emacs visudo" when I want to run it.

If you put:
```

EDITOR=emacs

```
Inside your .bashrc, then visudo (and other programs like svn) will automatically use your editor of choice.

---

### Post by toupeiro on 2009-04-12
> **Paqman said:**
> And all tutorials are written for sysadmins, are they?

No, but a lot of sysadmins write tutorials.  You can do the math from there.

there is also "man vi" 

and once you are in vi, there is also :help

There was a time I didn't know vi, and now that I do, it is my preferred editor, so naturally, I am going to prefer to use it in documentation.

---

### Post by castrojo on 2009-04-12
I use vim but I always use:

sudoedit /etc/blah

and when I show people how to do stuff. That way everyone gets the editor they use but the docs are consistent since it just spawns $EDITOR.

---

### Post by Paqman on 2009-04-12
> **toupeiro said:**
> No, but a lot of sysadmins write tutorials.  You can do the math from there.

there is also "man vi" 

and once you are in vi, there is also :help

There was a time I didn't know vi, and now that I do, it is my preferred editor, so naturally, I am going to prefer to use it in documentation.

If you're writing a tutorial that's only going to be of interest to sysadmins, then it would make sense to use tools they were familiar with. But if it's for anybody else, then writing it for vi is just dumb, because most people don't know vi. The point of the exercise is to communicate, if you're not adapting your teaching style to the geek level of your audience, then you're doing it wrong.

What's the point of even writing a tutorial if you're not doing it in a way that helps the most people? You're just wasting everybody's time.

---

### Post by SKLP on 2009-04-12
One could use "editor" in howtos, which will open your editor of choice, which can be set by: sudo update-alternatives --config editor
I believe nano is the default

---

### Post by toupeiro on 2009-04-12
> **Paqman said:**
> If you're writing a tutorial that's only going to be of interest to sysadmins, then it would make sense to use tools they were familiar with. But if it's for anybody else, then writing it for vi is just dumb, because most people don't know vi. The point of the exercise is to communicate, if you're not adapting your teaching style to the geek level of your audience, then you're doing it wrong.

What's the point of even writing a tutorial if you're not doing it in a way that helps the most people? You're just wasting everybody's time.

What complete conjecture. :lolflag:

I guess you are the spokesperson for *everybody else*?  If you're not adapting your learning habits, and applying what you already know to what you are being taught, it sounds like more of a reader error than a writer error.  The only time wasted I see here is a ridiculous banter over something you could just as easily substitute, or if you didn't know you could substitute, you could ask.  Giving a new Linux person a text editor to use is better than saying "your text editor du jour" which, if they are truly new, they probably don't know anything else.  Vi is guaranteed to be in any linux or unix distro they may be using, no matter how old, or how new it is.  to vi or not to vi is a petty semantic, and telling someone who spends their time documenting a procedure is wasting everybody's time because they used vi is shallow, one-sided, and rude.  Your attitude sounds more like you think if YOU have a problem with it, EVERYBODY has a problem with it.  The best way to magnify your issues is to make them known, keep them in context, and have people contribute constructively, not blow them out of proportion by trying to be the self-proclaimed spokesperson for a community of individuals.

---

### Post by Paqman on 2009-04-12
> **toupeiro said:**
> 
I guess you are the spokesperson for *everybody else*?

No, but it's pretty self-evident that a lot of folks won't have ever used vi, and that it has a very steep learning curve. Do you actually disagree with that? 

Expecting someone who already has a broken system to climb an obscure learning curve just because of your personal preferences is ridiculous. Focus on the user. If they can't achieve the task you're trying to teach _it's your fault_. That's how teaching works.

---

### Post by chris200x9 on 2009-04-12
emacs!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by toupeiro on 2009-04-12
> **Paqman said:**
> No, but it's pretty self-evident that a lot of folks won't have ever used vi, and that it has a very steep learning curve. Do you actually disagree with that? 

Expecting someone who already has a broken system to climb an obscure learning curve just because of your personal preferences is ridiculous. Focus on the user. If they can't achieve the task you're trying to teach _it's your fault_. That's how teaching works.

So I should write documentation that caters to a smaller group by using editors less seen across all distributions because they require less brain and social activity to use?  I should lower the bar to a level rather than try to help people get that bar on the next?  And its my fault if I don't lower the bar?  And we (people in the US) wonder why our scholastic scores are getting lower and lower..

What kind of brain activity does it take to say "wow, this is text, I dont like vi, I will try <insert text editor here>" or to make a post asking, hey if I use <insert text editor here>, will it work the same as vi?   Learning is an interactive sport...  You can't teach those who aren't willing to learn.  You describe people who want to be told what to do, with no regard as to whether they learn something or not.  These are the same people who will severely break their system one day by blindly cutting and pasting commands from a forum with no understanding of what they do.  There is value to learning a new tool, and there is value to learning when a tool can be substituted.  There is no value, however, in putting down documentation because *you* don't want to learn how to follow it directly, or apply it to your situation.

---

### Post by Paqman on 2009-04-12
> **toupeiro said:**
> You describe people who want to be told what to do

Yep. That's exactly what a lot of folks want when they're googling for tutorials. 

Remember that the people who use tutorials the most are new users, or those who're still a bit unsteady. This depends of course on what your tutorial is about. If it's uber-techy, then using vi might make sense. But then, even amongst ubernerds, a lot of them hate vi/vim, so that line of thinking doesn't really lead to my happy place either.

---

### Post by toupeiro on 2009-04-12
> **Paqman said:**
> Yep. That's exactly what a lot of folks want when they're googling for tutorials. 

Remember that the people who use tutorials the most are new users, or those who're still a bit unsteady. This depends of course on what your tutorial is about. If it's uber-techy, then using vi might make sense. But then, even amongst ubernerds, a lot of them hate vi/vim, so that line of thinking doesn't really lead to my happy place either.

And there will be documents out there for them, but it doesn't make me, or anyone else, a failure or time waster if we don't choose to predict which text editor they are going to want us to use to find "their happy place.", but rather choose one which we know will be there for them no matter which distro they are using.

---

### Post by Paqman on 2009-04-12
Who cares if it's there? They have to know how to use it.

---

### Post by cardinals_fan on 2009-04-12
> **Paqman said:**
> Who cares if it's there? They have to know how to use it.
Not every user of a given distro will know how to use it, but I can pretty much guarantee that it won't work for anyone if it isn't there.

---

### Post by toupeiro on 2009-04-12
> **Paqman said:**
> Who cares if it's there? They have to know how to use it.

they will care when it says: **command not found**

Again, what brain power does it take to substitute vi, or .. to ASK if it can be substituted?

---

### Post by Paqman on 2009-04-12
> **toupeiro said:**
> 
Again, what brain power does it take to substitute vi, or .. to ASK if it can be substituted?

It's not about brain power. It's about experience. If you want to write tutorials that are usable only be people with a certian level of knowledge, then that's fine. But don't write for newbies and use vi.

Just to put some perspective on this argument:

[Debian popularity contest stats for vim]("http://qa.debian.org/popcon.php?package=vim")

Sure, loads of folks have some form of this editor installed, but most never use it. So you wouldn't expect any of those people to have any proficiency with it. These people aren't thick, they just don't use it.

---

### Post by super breadfish on 2009-04-12
Most tutorials only require the user to add a few lines to a file then save. Why not just stick a note at the top telling them how to do that in whatever editor is being used?

That way the writer doesn't have to change their habits, and the reader isn't left stuck and confused in some archaic text editor.

---

### Post by toupeiro on 2009-04-12
> **Paqman said:**
> It's not about brain power. It's about experience. If you want to write tutorials that are usable only be people with a certian level of knowledge, then that's fine. But don't write for newbies and use vi.

Just to put some perspective on this argument:

[Debian popularity contest stats for vim]("http://qa.debian.org/popcon.php?package=vim")

Sure, loads of folks have some form of this editor installed, but most never use it. So you wouldn't expect any of those people to have any proficiency with it. These people aren't thick, they just don't use it.

In a round-about way, you have proven my point.  It really doesn't matter whether I document using VI, or whether they know how to use VI, they obviously completed their tasks regardless of these two components by recognising there are other text editors they can use.  Look, nobody here is a mindreader, and I can't know what text editor people are going to like or dislike, nor do I care, what I care about is giving them **a** way to accomplish their task. but I write documentation that I know will work everywhere regardless, and if you like a different text editor than I chose, than use it.  If you find a better document than mine, use it as well,  Text is text, in vi or anything else, and if you don't like vi, and can't ask whether or not you can use something else, thats not the documentation authors fault.

---

### Post by Paqman on 2009-04-12
My point is, if the majority of people enter your commands verbatim, they'll get something they can't use.

They may get something usable if they adapt the command to use a different editor. But a lot won't know how unless you tell them. So why not just tell them in the first place?

---

### Post by Simian Man on 2009-04-12
> **Paqman said:**
> My point is, if the majority of people enter your commands verbatim, they'll get something they can't use.


But people shouldn't paste commands from the internet into a terminal without knowing what they do.  People that can't be bothered to learn what vi does - and that it can be substituted for something else - shouldn't be using the command line any way.  If someone pastes commands into a terminal they find on line without thinking, a confusing text editor is the least of their troubles - they're likely to fubar their system anyway.

---

### Post by donovan1983 on 2009-04-12
I really like vim and it is definitely my preferred editor. But when doing simple modifications to system files I generally just use nano. And most Linux systems nowadays have it installed anyway, so I do believe most tutorials should be using nano instead. It is a lot less intimidating for a new user than vi(m) or Emacs. I even prefer nano for the simplest of tasks since it is usually quicker to use, and I've been messing around with Linux for nearly 10 years.

---

### Post by cardinals_fan on 2009-04-12
> **Paqman said:**
> My point is, if the majority of people enter your commands verbatim, they'll get something they can't use.

They may get something usable if they adapt the command to use a different editor. But a lot won't know how unless you tell them. So why not just tell them in the first place?
1. Copy/pasting commands without understanding them is a bad idea.

2. I believe that telling them is the right idea, which is why I think instructions should just say "Edit this file and add xyz".

There is no way to know what editor will work best for a given individual.

---

### Post by toupeiro on 2009-04-12
> **Paqman said:**
> My point is, if the majority of people enter your commands verbatim, they'll get something they can't use.

They may get something usable if they adapt the command to use a different editor. But a lot won't know how unless you tell them. So why not just tell them in the first place?

Because its a bad behavior.  Its the same reason I tell people not to click on emails from people they don't know that say "Click this link to win a new house!"

---

### Post by red_Marvin on 2009-04-12
We are on page eight of an editor war and ed is yet to be mentioned!? What kind of forum is this!?
Oh well, my main gripe with vi is that it is not ideal for use with the Swedish keyboard, adding the dvorak sub-layout makes the standard movement keys move to much less useful positions. But I find ed usable for some reason.

On the subject of which editor should be used in tutorials, I have to repeat what others have said, that it shouldn't matter and that if the user cannot identify (common ones) and eventually substitute one editor for another they haven't done their homework and should do some more basic cli tutorials first.

---

### Post by Paqman on 2009-04-13
> **cardinals_fan said:**
> 1. Copy/pasting commands without understanding them is a bad idea.


I agree, but people do it. It's worth taking that into consideration when writing a tutorial.

> 
2. I believe that telling them is the right idea, which is why I think instructions should just say "Edit this file and add xyz".

There is no way to know what editor will work best for a given individual.

Again, I agree. As mentioned above, nano is probably the best bet, because it's also ubiquitous, but put a huge speedbump between the user and the result like vi/vim does.

All it would take would be a note somewhere in the tutorial explaining the situation. The fact is, if you're trying to write a tutorial that's usable on any type of Linux then you can't avoid creating a lot of extra hassle for yourself. Which text editor they have installed is only one of many variables. You're going to have to go the extra mile and consider all options if that's the kind of tutorial you're trying to write.

---

### Post by red_Marvin on 2009-04-13
Obviously it is not that kind of tutorial they are writing then.

A tutorial on compiling wireless drivers, since the ones in the repos are not up to date or whatever, should not have to include a basic cli tutorial or a basic editing tutorial.
A user that is doing a certain thing is supposed to have some *basic prerequisite knowledge*. The instructions on how to connect your brand new monitor should not have to teach you where the power button is placed on your computer, and have a list of all kinds of power button placement possibilities just because you may not have the same case as the author of the instructions.

However, on all ubuntu centric tutorials I've seen that do not specifically need editing in cli I've only seen /gksudo/ gedit.

---

### Post by bp1509 on 2009-04-13
d

---

### Post by billgoldberg on 2009-04-13
If you write a tutorial aimed at noobs, you don't use cli text editors period.

That's like telling first grader to proof why pi is 3.1415 in order to make a drawing.

I don't care about cli text editors.

If I need one I'll use nano, because it's easy and straightforward.

---

### Post by bp1509 on 2009-04-14
d

---

### Post by chucky chuckaluck on 2009-04-14
> **billgoldberg said:**
> If you write a tutorial aimed at noobs, you don't use cli text editors period.

That's like telling first grader to proof why pi is 3.1415 in order to make a drawing.

I don't care about cli text editors.

If I need one I'll use nano, because it's easy and straightforward.

the point of using a cli editor is that they are more likely to be universally available than gedit, kate, mousepad, or any other gui editor. while vi may be on every distro, instructions for its use are not readily available. while nano may not be universally available, it nearly is and a drunken child of four, or five could use it with relative ease.

---

### Post by ntowakbh on 2009-04-14
The question makes sense. I can see for myself how it can be more efficient to use vi at times, but if a tutorial is aimed at a really basic beginer, at the very least, they should choose nano, if not gedit, for those afraid of the command line.

As for those not being universaly available, know your audience is the response here.  If they're using a distro where gedit(or some other gui text editor) isn't available, then they probably know a thing or two already.  If they are using a system where nano, or the like, isn't available, then they probably know how to use vi, and aren't beginners either.

Note to vi fans: Don't take this the wrong way, I use vi myself, but tutorials aren't the place for it.

---

### Post by bp1509 on 2009-04-14
d

---

### Post by doorknob60 on 2009-04-14
> **FuturePilot said:**
> I'm guessing because just about every distro ships with vi so it's pretty much guaranteed to be there. I have yet to come across a distro that did not have vi installed. However I have come across distros that don't have nano installed by default.

Anyone using a nano-less distro probably knows their way around Linux well enough to either figure out vi or to install a different editor. Ubuntu, Debian, and Arch all have nano by default, as well as most others.

---

### Post by billgoldberg on 2009-04-15
> **chucky chuckaluck said:**
> the point of using a cli editor is that they are more likely to be universally available than gedit, kate, mousepad, or any other gui editor. while vi may be on every distro, instructions for its use are not readily available. while nano may not be universally available, it nearly is and a drunken child of four, or five could use it with relative ease.

I'm talking noob reviews here (like the OP said).

Anyone who knows Linux commands a bit know you can easily change text editors.

So I think it's better to use gedit (and mention kate and mousepad in the beginning of any how-to) then using vi.

You and I know that when we see lets say the command

vi /etc/X11/xorg.conf

we can change vi to gedit or something else. Noobs might not.

---

### Post by billgoldberg on 2009-04-15
> **bp1509 said:**
> do you have any idea how many people have learned unix in one fashion or another in the last 30 years by starting with the command line and command line editors?

No, I am unaware of that fact.

</facepalm>

---

### Post by toupeiro on 2009-04-15
> **chucky chuckaluck said:**
> the point of using a cli editor is that they are more likely to be universally available than gedit, kate, mousepad, or any other gui editor. while vi may be on every distro, instructions for its use are not readily available. while nano may not be universally available, it nearly is and a drunken child of four, or five could use it with relative ease.

To that effect, do I want to make it any easier for a drunken child of four or five to modify files on my system from a guide which they have no real idea what it will do? ;)


Seriously now though, people can hate on VI all they want, the arguements I've heard in support of never using it almost completely surround bad practices, likely learned from years and years of running Windows.  I will not contribute to bringing linux or its communities down any notches to support these behaviors.  VI stays in my docs.  It was good enough for me to learn on before I new twiddle about linux CLI, and admittedly, I would use Pico (nano) if I wanted to do something I didn't know how to in VI.  I certainly didn't complain about it being in the doc someone was kind enough to take the time to write. Today I prefer it over any of the alternatives out there. If you don't like it, substitute it.  My docs are Open Source...

---

### Post by mister_doctor on 2009-04-15
Using vi(m) takes some getting used to, that said it has a great deal of power for a CLI editor.

Being forced to use it at my workplace (AIX has nothing else but vi) has helped me appreciate it more.

That said, unless I'm remotely connecting to my Ubuntu machine via ssh, I use GUI editors.

---

### Post by calrogman on 2009-04-15
Attention vi supremacists!

The kind of people who are looking at these tutorials are new Linux users who have migrated from Windows or Mac OS,  they do not know vi, vim or nano.  But which looks easier to a [SIZE="4"]NEW[/SIZE] user?  I'll leave that up to you lot.  *cough nano cough*

---

### Post by bp1509 on 2009-04-15
d

---

### Post by RiceMonster on 2009-04-15
To sum up all 10 pages of this thread:

"Vi is too hard for beginners. Nano is way easier"
"Yeah, well Vi is a standard editor, it's on all Linux distributions and everyone should learn it."

*repeat*

---

