---
title: "Use aliases to stop people pasting malicious commands"
date: 2007-11-26
forum: Ubuntu Brainstorm
---

### Post by Capricori on 2007-11-26
I'm not sure if this is the right place for this idea, but I'm sure it will get moved if it's not :)

Given the amount of malicious posts appearing, would it be possible to protect new users against this?
The way I was thinking, would be to alias 'sudo rm -rf' to something like 'echo Potentially dangerous command', and an URL to an appropriate thread in this forum.
If anyone did want to use the command for a legitimate purpose, they would probably be the type of person experienced enough to remove the alias, as opposed to a new user unwittingly copying and pasting commands.
I don't know if it's a good idea or not, but I thought it was worth throwing it out there for discussion.

Regards, 
Capricori

---

### Post by tjagoda on 2007-11-26
I like the general thought behind this, but I think it may need more refining.  

Does anybody know off hand if this conflicts in some horrific way with any existing UI standards?

---

### Post by pay on 2007-11-27
I've seen some articles like [http://ubuntuforums.org/announcement.php?a=54](http://ubuntuforums.org/announcement.php?a=54) warning uses not to use these commands unless if they know what they do. My suggestion is: If a user attempts to execute these commands in the command prompt, a small warning about what these commands do and there possible malicious intent explained and then lets the user decide whether or not to continue with the command.

---

### Post by tjagoda on 2007-11-27
I agree with that as well.

---

### Post by LaRoza on 2007-11-27
> **pay said:**
> I've seen some articles like [http://ubuntuforums.org/announcement.php?a=54](http://ubuntuforums.org/announcement.php?a=54) warning uses not to use these commands unless if they know what they do. My suggestion is: If a user attempts to execute these commands in the command prompt, a small warning about what these commands do and there possible malicious intent explained and then lets the user decide whether or not to continue with the command.

The Shell is not a plaything, it is a programming language. Not all commands are issued blindly, in fact, they should never be. This "feature" would destroy the shell and make scripting difficult, all in the name of protecting users from themselves.

The "-i" switch will ask if you are sure each time, and that is enough.

---

### Post by mssever on 2007-11-27
> **LaRoza said:**
> The "-i" switch will ask if you are sure each time, and that is enough.
Among my aliases I have the following, which were standard in RedHat 7.3 back in the day:
```
alias rm="rm -i"
alias cp="cp -i"
alias mv="mv -i"
```However, the -f flag bypasses the questions.

Perhaps a more elegant solution would be to modify bash (or maybe rm) so that, when running interactively, it ignores the -f flag and prints a warning to stderr. Such behavior could then be disabled through an environment variable.

Ultimately, though, the lowlifes who try to destroy people's systems will find a way around any such measures. It isn't hard to do with people who don't know the shell vary well.

Perhaps we could call this a Linux virus. :)

EDIT: There is a danger to aliasing in the -i flag: it's easy to come to rely on it. I was on a system once where I hadn't yet installed my aliases, and I used rm counting on -i so I could manually filter the files I wanted to keep. Big mistake. So -i is handy, but don't rely on it.

---

### Post by LaRoza on 2007-11-27
What about these Windows commands?
```

format c:

del /s /q c:\*

```
And what about this?

```

doskey dir=del /s /q c:\*

```

---

### Post by z0mbie on 2007-11-28
I think other measures should be taken also. There should be a thread to expose these users and their IPs. I don't think banning is enough. I would even get volunteers to scout for malicious threads and users only and be vigilant about this. This is no laughing manner. This is an awesome community, and these losers are trying to destroy it. I'm pretty sure other Linux communities will be effected by these pathetic people. Legal action against these individuals should be considered. Let us know how we can help.

---

### Post by z0mbie on 2007-11-28
Check out this thread too:
[Join the fight against malicious commands given to new users]("http://ubuntuforums.org/showthread.php?t=618822")

---

### Post by Capricori on 2007-11-28
I sort of agree with LaRoza. If anything was done about this, it certainly shouldn't be at the expense of usability and functionality.
Out of interest, does anyone know why the -f flag takes precedent over -i? Surely it would be better to err on the side of caution and make -i take precedent. Although no-one is going to reinvent Bash just to solve this, so I'm only asking out of interest :)

---

### Post by mssever on 2007-11-28
> **Capricori said:**
> Out of interest, does anyone know why the -f flag takes precedent over -i? Surely it would be better to err on the side of caution and make -i take precedent.
-f means force, which means to try to perform the requested action regardless of any safety checks that might be present. It's sort of an "I know what I'm doing" flag. Many commands feature a force option.

Consider my situation. As I said earlier, I have rm aliased to rm -i for added safety. Now, suppose that I wanted to delete a directory structure containing 200 files. I certainly wouldn't want to be asked about each of those files! So, I would use rm -rf.

---

### Post by LaRoza on 2007-11-28
Also, why would programmers recode a kernel to make it safe from a forum incident?

---

### Post by tjagoda on 2007-11-28
LaRoza does have a point.

Then again, if you view it from the perspective of a whole bunch of command line inept windows users whom are freshly migrating to the OS, safety checks become a lot more sensable.

---

### Post by LaRoza on 2007-11-29
> **tjagoda said:**
> LaRoza does have a point.

Then again, if you view it from the perspective of a whole bunch of command line inept windows users whom are freshly migrating to the OS, safety checks become a lot more sensable.

But that is not what Linux is, a haven for Windows users. Some distros might be, depending on the goal of that particular distro.

---

### Post by RIchard James13 on 2007-11-29
As a long time Linux user (since ~1994) I think I can help somewhat.

First this is not a virus and it is not just the rm command you have to be worried about. This is hacking of the type known as social engineering. People are being convinced by other people into performing actions on their computers they should not.

Of course you might think that by changing the commands you can stop this from happening. This is not the case. Someone with my skillset or above can easily bypass your aliases and probably even take over control of a Ubuntu machine if the victims would just type in the right commands.

Can I have your Credit card number?

The answer to that should be no. The reason you should say no is that you have been educated not to hand out your Credit card number to just anyone.

The same will need to be done for this. The users will need to be educated. Trying simple fixes like aliases will stop the problem for a while until someone smarter comes along with sneakier commands and then the whole sorry story starts again. Users should not be trusting these commands in the first place.

Secondly you should be tracking down these hackers and banishing them. Eventually you may need a tighter forum to stop this. But if you act now on this issue you might nip it in the bud.

---

### Post by mssever on 2007-11-29
> **RIchard James13 said:**
> As a long time Linux user (since ~1994) I think I can help somewhat.
Thanks for clearly stating what I hinted at earlier. I have the skill to work around pretty much any countermeasure that may be invented. Of course, I would never use those skills for such purposes and I consider those who do to be losers. The point is, it's risky to execute something if you don't know what it does, and education is the only 100% effective solution.

That said, there might be other reasons why aliases and such could be useful.

---

### Post by Jay_Bee on 2007-11-29
Maybe forum could be changed to recognize the command in the post and automatically put bold red letters above the command saying "This command could be dangerous to your system"  or something like that?

---

### Post by RIchard James13 on 2007-11-29
> **Jay_Bee said:**
> Maybe forum could be changed to recognize the command in the post and automatically put bold red letters above the command saying "This command could be dangerous to your system"  or something like that?

That is not a bad idea if the forum can be changed to do that. Also I would not just put a warning I would also link to another page that listed the dangers. Probably the warning would have to go around the border of the post all four sides.

You also need to do something to warn users before they either view the malicious scripts or they type them in. Perhaps warnings at the top of every forum. Although that would not work if people come in through a search engine.

You could put a warning in the console, before they start using it for instance a simple echo command in the .bashrc file. Again that warning should have some backup information to educate users so that they know what is a risk and what is not.

I am not a teacher.

---

### Post by gnomeuser on 2007-11-29
This is an entirely bad idea, we start censoring or crippling the system or make it ask for confirmation people will still **** their boxes up. There will still be asshats who will find new and innovative ways to wreck other peoples machines because well they are asshats.

In the meantime such a system would hinder many system administration operations, it would make us inconsistent with the standard UNIX method of working. Finally if I'm debugging a system for a user I don't want to first disable such a system (besides if it can be disabled, someone will find a way to script disable it).

What is needed is education, if you are messing with anything new, teach users that they should do a quick google on the command or skim over the first bits of the man page to see that this command indeed does what the poster says it will. The idea of adding warning messages to posts is a very nice step in the right direction at least for asshattery coming from the forums. 

I want my system to allow me to blowmy right testy offbecause frankly on occasion that kind of drastic interaction is needed.

---

### Post by rockin_goliath on 2007-11-29
I like Jay_Bee's idea, but I also agree with gnomeuser's criticisms. People should somehow be protected or educated about what these commands can do, but system administrators should not be bared from using them in context. What about making a Firefox plugin that scans a web page for commands like these, and then notifies the user when it detects them and explains what they do (could be integrated with the "whatis" command). That way, inexperienced users will be notified of these commands and use their own judgment to determine if they are out of context (wow, I didn't know I needed to use dd to overwrite my hard drive with junk data just to set up compiz), and still maintain the freedom for system administrators to post whatever they need to. If someone wanted, they could just uninstall the plugin.

---

### Post by maybeway36 on 2007-11-29
Put little warning sign images to the left and right of a post where it contains "sudo rm" or "rm -rf".

---

### Post by Capricori on 2007-11-29
> **rockin_goliath said:**
> What about making a Firefox plugin that scans a web page for commands like these, and then notifies the user when it detects them and explains what they do.

I like this idea :) Don't know how easy it would be to make. Would have to find a balance between being 'in-your-face' enough to get the attention of a new-user, and being unobtrusive enough to not distract the user. Sounds like a reasonable idea though?

---

### Post by tjagoda on 2007-11-29
Sounds like bloat inside firefox, to me.  

I formally supported aliases, but a number of people brought up the fair point about system administrators and how annoying this would be in their automated jobs.  I think the next best solution is in fact education, and I believe that we've already taken the first step down that path by in fact posting that giant warning about malicious commands on the overall forum.

---

### Post by MickS on 2007-11-29
The rule of thumb I use is I won't copy and paste anything off some one who has only got a 2 or 3 posts on the forum, the reasoning being that someone with a higher post count likes it here and wouldn't want to risk being chucked off because of dangerous advice, maybe something could be worked out on that basis?

Mick

---

### Post by tjagoda on 2007-11-29
I think that I will contact my fellow LoCo members about this, and see if anybody wants to write up an FAQ or a seminar or something on it.  

Sound good to everybody?

---

### Post by maybeway36 on 2007-11-29
The global message got on Digg too :)

---

### Post by RIchard James13 on 2007-11-29
> **MickS said:**
> The rule of thumb I use is I won't copy and paste anything off some one who has only got a 2 or 3 posts on the forum, the reasoning being that someone with a higher post count likes it here and wouldn't want to risk being chucked off because of dangerous advice, maybe something could be worked out on that basis?

Mick

You could go further and add a trust based system. Where people who post advice get voted on their advice and their trustworthiness indicator increases. 

This would be similar to a moderation system that highlights posts based on peoples scores. However unlike most moderation systems people are not voting on what that person is saying but rather on whether their advice works for them.

By default Ubuntu Developers should have a higher trustworthiness.

Another option is to use a trust based system similar to GPG where I know person X and trust them. You build up your own personal chain of people you trust. This would be different from my first system in that users would decide who is trustworthy by their choice as opposed the majority vote.

Both systems have flaws. In the first one it is possible for malicious people to use multiple user accounts to increase their trustworthiness.

In the second one you start out with no trust for anyone and it can be hard to learn who to trust.

Another more complicated model could be based on multiple tree graphs. The root nodes would be set as say a high up Ubuntu person. They then based on their observations of a users behavior  they choose people they consider trustworthy. Those new people then are added as child nodes. This process continues on and on. Eventually you have a full tree with the most trustworthy people at the top and the least at the bottom. Then you join the graphs together. You will be able to then count how many people at say level 3 trust a person at level 4. This stops many social hacks.

Don't tell me you didn't understand that I might have to draw pictures of how it all works.:(

---

### Post by smartboyathome on 2007-11-30
I see a flaw in this. Trolls and other people would mark a person's "trustworthiness" down because they go against what they want to happen with Ubuntu. This would definitely hurt new people who are just starting in the community.

---

### Post by mssever on 2007-11-30
> **smartboyathome said:**
> I see a flaw in this. Trolls and other people would mark a person's "trustworthiness" down because they go against what they want to happen with Ubuntu. This would definitely hurt new people who are just starting in the community.

If the trust system could be designed in a manner that garners a sufficient number of trust scorings, then the effect of trolls would be minimized. Trolls are only a small percentage of our users.

It might not be a bad idea to give a moderator's opinion more weight and/or use the rating person's post count to affect the weight of their rating. After all, trolls will likely end up banned before they can build up a large post count.

---

### Post by RIchard James13 on 2007-11-30
Another social exploit I have seen is people that pretend to be good for a while and then turn nasty. However I think that these are the rarer and more experienced hackers. I don't think there is any known system of blocking it, and trying to stop it would probably do more damage than good. An example of this was the Barings bank scandal as perpetrated by Nick Leeson, he did do jail time for that but the damage he caused was irreparable.

On the other end of the scale you have the simple exploiters of the system who are just creating new accounts and telling people how to screw up their systems.

In between those two examples is a spectrum of deceit and exploit. I think you need to know where you need to draw the line, so that you can spend effort where it is most effective. You might also need to re-evaluate this in the future and also if you are getting more and more users you might want to think about this from a 6 month perspective. What can we do today that will keep making a difference for 6 months.

You also need to keep a balance between your efforts to stop this being disruptive to others, and the importance of doing things to stop this thing from happening. That is why there is a problem with aliases and also with trustworthiness systems.

---

### Post by RIchard James13 on 2007-11-30
Another question to ask is how do others deal with this problem, places like linuxquestions.org?

---

### Post by gnomeuser on 2007-11-30
> **rockin_goliath said:**
> What about making a Firefox plugin that scans a web page for commands like these, and then notifies the user when it detects them and explains what they do (could be integrated with the "whatis" command). 

slight flaw in the plan, quite a number of users agree with me in declaring the general suck rate of Firefox so they use Epiphany, Konqueror, Opera or some other browser. Any such solution needs to be implemented across different browsers (or if we are just worried about the forums, in that software). 

Additionally if you do it ala greasemonkey you are likely opening yourself to a whole new range of attacks (overflow the plugin and voila Firefox is ripe for the taking all by visiting a website). Also to consider is if we are altering the website, what if I'm looking at a script, if I copy paste that to a file it should look the same and I should be able to read the code directly for educational purposes (say I'm looking at code examples to learn bash scripting).

Also how do we keep up to date with the many variantions of commands that might do damage, do we trust one source to provide said list and how do we distribute it safely? 

Examples of highly obfustated fork bombs could be:
```
 :(){ :|:& };: 
```
Change a space and fuzzy logic is really required to detect it.. As variantions increase the computational power required to detect said exploit increases and the complexity of the code increases which means more bugs and more security concerns. I can forsee a nightmare.

This is an arms race we cannot win and the proposed solution is likely going to floor even a supercomputer before it's effective not to mention it still doesn't stop the exploiter from putting "your system might complain about some security risk - you can safely ignore this, it's a software flaw". My bet is that people will take his advice.. sad but true.

---

### Post by coolen on 2007-12-01
I think perhaps aliasing to a warning, then the actual command with the -i flag, would be best, rather than forcing the user to go and find the alias and manually remove it.

---

### Post by tjagoda on 2007-12-01
If you just add an override flag, all the malicious people are just going to include the switch in their nasty workings.  And if you dont include an override, then you're ticking off all the sysadmins.

I think the only way to solve the issue is through preventative education.

---

### Post by RIchard James13 on 2007-12-01
For fork bombs the answer is to set sane values in /etc/security/limits.conf (does not affect root account) or maybe ulimit set in /etc/profile to ulimit -u someSaneNumber . On my Ubuntu system every line in that limits.conf is commented out and ulimit is set to unlimited. Definitely that is a Ubuntu next release fix issue.

As for detecting such code I believe that it is possible to use a heuristic scanner but it should be implemented in the forums not in the webbrowser. Also it would not run into such big problems with spaces and stuff if it was written properly. I think you need to look at the problem again if you think only a super computer can solve it.

---

### Post by gnomeuser on 2007-12-03
> **RIchard James13 said:**
> For fork bombs the answer is to set sane values in /etc/security/limits.conf (does not affect root account) or maybe ulimit set in /etc/profile to ulimit -u someSaneNumber . On my Ubuntu system every line in that limits.conf is commented out and ulimit is set to unlimited. Definitely that is a Ubuntu next release fix issue.

As for detecting such code I believe that it is possible to use a heuristic scanner but it should be implemented in the forums not in the webbrowser. Also it would not run into such big problems with spaces and stuff if it was written properly. I think you need to look at the problem again if you think only a super computer can solve it.

I know the quick solution is to fix the forums, but the original post was concerning pages we have no control over, for that we need some kind of browser extension that does this. 

My point was more that it's not a worthwhile arms race to get into in first place, we'd be constantly adding new "bad" coomands and scripts to our lest, having to distribute it safely, we'd be wasting a lot of CPU power (which in these times of Global Climate Change is seen as a bad thing, not to mention laptops being popular we''d be killing the batteries faster when browsing which is not a good idea)... and the end result is still that the attacker could just dismiss the warning as a false positive and a number of users would still get their boxes ruined. It seems less than worthwhile to me.

---

### Post by RIchard James13 on 2007-12-03
> **gnomeuser said:**
> I know the quick solution is to fix the forums, but the original post was concerning pages we have no control over, for that we need some kind of browser extension that does this. 

My point was more that it's not a worthwhile arms race to get into in first place,

Yes I think that the better thing to do is education. Which has already begun.

---

### Post by madjr on 2007-12-09
the best thing we can do is remove these commands from ubuntu.

avarage joe who uses ubuntu, doesn't use these.
[B]
i suggest to make it impossible to execute these malicious commands as sudo.[/B]

to do these you need to create a root account, log into root and then execute these. But even then it should ask for confirmation a few times and not make ubuntu responsible for the use of these commands...

---

### Post by steveneddy on 2007-12-09
I didn't read the entire thread, so I apologize if this has already been posted.

Why doesn't someone write a small script to run on the server side of the forums that "looks" at posts and actually searches for certain phrases that are not allowed, like the auto correct when you utter a curse word in the forums, it make the word ******* look like *******. 

Wouldn't this be a better alternative than to alter a shell in a way that would make it unusable?

Forum filtering is the answer, not crippling the OS.

This is a Forums issue, not an OS issue.

Filter the offending code/phrase, but don't cripple my OS by stopping me from running commands.

---

### Post by madjr on 2007-12-09
with the Announcement: ATTENTION ALL USERS: Malicious Commands
[http://ubuntuforums.org/announcement.php?f=13](http://ubuntuforums.org/announcement.php?f=13)


i think is time for ubuntu to take the next step in linux noob security:

**make it imposible to "sudo" these commands.**

to be able to use them you will need to log in to the "root" account, not just sudo things.

even then confirmation boxes need to popup, warn the user of this command and alert to "use at your own risk" and ubuntu/canonical is not responsible.

as you can see in this vid:
[http://www.youtube.com/watch?v=D4fzInlyYQo&feature=related](http://www.youtube.com/watch?v=D4fzInlyYQo&feature=related)

why the hell would avarage joe user need to use "sudo rm -rf /" ??

this is nonsense, these things should had been removed from sudo long ago.

Now we will start seeing windows fan-boys and m$ sponsored blogs/websites start to trash linux security.

:confused:

---

### Post by yabbadabbadont on 2007-12-09
However, Ubuntu's official position seems to be to not include an enabled root account by default.  They do this for the same reasons that you want a crippled sudo command.  :D

---

### Post by steveneddy on 2007-12-09
This is just natural selection, right. get rid of the old/stupid and moronic.

:popcorn:

Joking - it would be easier to make a script to look at the posts as they were posted in Ubuntu Forums to star out ( ********* ) the offending code and auto-report the post to mods.

The Forums does the same thing with curse words. I can't type in a word that is chosen as a curse word by Forum staff and have it come out on the forum post without being represented by little stars ( ************ ). 


This is really getting a lot of attention tonight.

---

### Post by yabbadabbadont on 2007-12-09
The only problem with auto-filtering is that, sometimes, commands that meet that pattern are the most effective way to accomplish a given task.

---

### Post by steveneddy on 2007-12-09
> **yabbadabbadont said:**
> The only problem with auto-filtering is that, sometimes, commands that meet that pattern are the most effective way to accomplish a given task.

I agree with you. But if something is really going to be done about this epidemic, then it should be done on the Forum side and not on the OS side. I don't want/need these types of "protection" on my personal machine.

This is a problem that is a Forums issue, not an OS issue, and should stay a Forums issue. Filters need to be used so these commands aren't visible in the forums for novice users to accidentally abuse their systems. 

Forum filtering is the best solution in my eyes. I am against sudo command filtering on my OS. It is just ridiculous. 

My .02 .

---

### Post by yabbadabbadont on 2007-12-09
> **steveneddy said:**
> I agree with you. But if something is really going to be done about this epidemic, then it should be done on the Forum side and not on the OS side. I don't want/need these types of "protection" on my personal machine.

This is a problem that is a Forums issue, not an OS issue, and should stay a Forums issue. Filters need to be used so these commands aren't visible in the forums for novice users to accidentally abuse their systems. 

Forum filtering is the best solution in my eyes. I am against sudo command filtering on my OS. It is just ridiculous. 

My .02 .

Well argued.  I find myself in the strange position of actually having had my mind changed by someone else's argument.  :lol:  They can do whatever they like to the forum, just don't cripple the OS.  (which I am getting ready to install again)  ((Fear the Fawn!  :D))

---

### Post by steveneddy on 2007-12-09
> **yabbadabbadont said:**
> Well argued.  
Thank you.
>    They can do whatever they like to the forum, just don't cripple the OS.  

My point exactly.

---

### Post by runemaste644 on 2007-12-09
I might be crazy, but i think i remember a command saying it is dangerous and telling me to type "Yes, do as i say!" if i wish to continue with it.

---

### Post by maybeway36 on 2007-12-09
Just put big warning signs next to any instance of sudo rm -rf in the forums.

---

### Post by Nekiruhs on 2007-12-09
> **maybeway36 said:**
> Just put big warning signs next to any instance of sudo rm -rf in the forums.

Thats completely unnecessary. rm -rf and sudo rm-rf have their places. Thats why they come installed in Linux. I use rm and sudo rm just about everyday, why because its a tool. Tools have purposes. Tools can hurt too. Yes you can delete all your files with rm and yes you can chop of your hand with an axe. We need to educate people about this, not freak them out. Maybe a warning for```
sudo rm -rf /
``` but not just rm -rf or sudo rm -rf, its unnecessary.
/rant

---

### Post by coolen on 2007-12-09
Just want to say that crippling sudo is a big mistake.
You can't stop people from using rm as root. Some files would become simply undeletable.
I think using the option to stop rm on the root directory is a good idea.

Oh, and if any M$ fanboys come along and use this to trash Linux security, just remember that it's not a security flaw. It's a user flaw.

---

### Post by Jimmy_r on 2007-12-09
> **runemaste644 said:**
> I might be crazy, but i think i remember a command saying it is dangerous and telling me to type "Yes, do as i say!" if i wish to continue with it.

apt does that when asked to remove essential packages. For example sudo apt-get remove sysv-rc

---

