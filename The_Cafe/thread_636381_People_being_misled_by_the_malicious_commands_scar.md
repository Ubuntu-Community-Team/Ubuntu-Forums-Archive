---
title: "People being misled by the malicious commands scare?"
date: 2007-12-09
forum: The Cafe
---

### Post by Nekiruhs on 2007-12-09
No, I'm not trying to say that the commands are good. I'm just pointing out an observation that some people's sigs read like this:
> **WARNING**: Never run a command with sudo rm -rf in it!!!
Which is completely false and makes it unnecessarily difficult when helping some users. People seem to be missing out on the difference between rm, sudo rm, sudo rm -rf, and sudo rm -rf /. Let me break it down

rm - Normal delete command
sudo rm - Delete command with root permissions
sudo rm -rf - Recursive delete command with root permissions and no checks
sudo rm -rf / - Deletes all files that root can write to. 

There are crucial differences. sudo rm -rf has many uses. Please stop smearing this command and update your sigs to say > sudo rm -rf / or other important directories (/home /usr /bin /etc)

---

### Post by user1397 on 2007-12-09
> **Nekiruhs said:**
> No, I'm not trying to say that the commands are good. I'm just pointing out an observation that some people's sigs read like this:

Which is completely false and makes it unnecessarily difficult when helping some users. People seem to be missing out on the difference between rm, sudo rm, sudo rm -rf, and sudo rm -rf /. Let me break it down

rm - Normal delete command
sudo rm - Delete command with root permissions
sudo rm -rf - Recursive delete command with root permissions and no checks
sudo rm -rf / - Deletes all files that root can write to. 

There are crucial differences. sudo rm -rf has many uses. Please stop smearing this command and update your sigs to sayyup, I agree, I use 'sudo rm -rf insert-directory-here/' all the time, I just don't use it on default and system directories.

---

### Post by -grubby on 2007-12-09
I fixed it

---

### Post by ~LoKe on 2007-12-09
I'm too paranoid to run sudo rm -rf on any directory, because I often hit return much too soon.

---

### Post by ntowakbh on 2007-12-09
I prefer to let people know what the command does.  I mean, if someone just tells you NOT to do something, with no explanation as to why, doesn't that make you just want to do it more?

---

### Post by -grubby on 2007-12-09
> **ntowakbh said:**
> I prefer to let people know what the command does.  I mean, if someone just tells you NOT to do something, with no explanation as to why, doesn't that make you just want to do it more?

good point

---

### Post by aysiu on 2007-12-09
I disagree that it has many legitimate uses, and I cannot think of any situation in which I would advise a new user to type or paste in a command that starts with *sudo rm -rf*

Well-intentioned though the helper may be, there is too much room for error if someone hits *Enter* too early or hits the wrong key.

---

### Post by finer recliner on 2007-12-09
see next

---

### Post by finer recliner on 2007-12-09
> **~LoKe said:**
> I'm too paranoid to run sudo rm -rf on any directory, because I often hit return much too soon.

if you edit you bash config file (~/.bashrc), you can alias common commands that delete/overwrite existing files to prompt you before doing so. 

try this to see what i mean:
```

touch test   #create an empty file named 'test'
rm -i test      #will prompt you for confirmation before actually deleting

```

if you like this, do what i did and add the following lines to your .bashrc:
```

#safety commands
alias cp='cp -i'
alias rm='rm -i'
alias mv='mv -i'

```

---

### Post by mcduck on 2007-12-09
> **ntowakbh said:**
> I prefer to let people know what the command does.  I mean, if someone just tells you NOT to do something, with no explanation as to why, doesn't that make you just want to do it more?

Agreed. Changed my sig,and finally got rid of Chuck Norris as well :D

Anyway, running "rm -rf" without sudo in users home dir would be just as annoying for most people than running it with sudo in a system directory..

And when giving commands to help people it would always be a good idea to also explain what the commands do.

---

### Post by wana10 on 2007-12-09
if you, like i have before, accidentally 'sudo wget' a file it appears in your home directory and you cannot delete it without root abilities. in that case you would have to 'sudo rm', so while it may not be advisable for a new user, i can see situations where it is needed.

---

### Post by -grubby on 2007-12-09
> **aysiu said:**
> I disagree that it has many legitimate uses, and I cannot think of any situation in which I would advise a new user to type or paste in a command that starts with *sudo rm -rf*

Well-intentioned though the helper may be, there is too much room for error if someone hits *Enter* too early or hits the wrong key.

signature fixed to reflect Aysiu's point

---

### Post by ~LoKe on 2007-12-09
> **wana10 said:**
> if you, like i have before, accidentally 'sudo wget' a file it appears in your home directory and you cannot delete it without root abilities. in that case you would have to 'sudo rm', so while it may not be advisable for a new user, i can see situations where it is needed.

sudo rm and sudo rm -rf are two completely different things. ;)

---

### Post by erfahren on 2007-12-09
> **ntowakbh said:**
> I prefer to let people know what the command does.

I think that's a good idea anyway, otherwise a person just might be blindly entering in "strange" commands without learning anything. 
> **ntowakbh said:**
> 
  I mean, if someone just tells you NOT to do something, with no explanation as to why, doesn't that make you just want to do it more?
we're not talking about cardinal pleasures here - lol !


I think what **finer recliner** was talking about doesn't work with sudo, does it?

@aysiu - a [post by Amaranth](http://ubuntuforums.org/showpost.php?p=3171088&postcount=618) includes it. 

I think the OP does have a point. I changed my sig a little as well.

---

### Post by red_Marvin on 2007-12-09
I think that once you are "old" enough to question those "NEVER!!..." signatures you also tend to be experienced enough to look them up.

However I might disagree with the signatures that only focus on rm -rf, there are a sea of potentially dangerous commands out there...

---

### Post by p_quarles on 2007-12-09
> **red_Marvin said:**
> I think that once you are "old" enough to question those "NEVER!!..." signatures you also tend to be experienced enough to look them up.

However I might disagree with the signatures that only focus on rm -rf, there are a sea of potentially dangerous commands out there...
Agreed, there are many dangerous commands out there, which is why my sig both focuses on "rm" and links to jdong's excellent explanation of the myriad dangers that go along with running unknown programs. As long as "rm -rf" is the current tactic being used by the unfriendly types, I'm going to highlight it specifically.

I remember being completely new to Linux. If I'd seen a warning that said "never run any command if you aren't sure what it does," I'd probably have ignored it on the grounds that I didn't know what *any* command would do, including "man." I work in higher education, and I know from experience that people retain information much more efficiently when they are given at least one concrete example. Eyes tend to glaze over if you only speak in generalities (I know this from painful first experiences in the classroom, too).

---

### Post by wana10 on 2007-12-09
> **~LoKe said:**
> sudo rm and sudo rm -rf are two completely different things. ;)

when i was but a wee linux lad i would have instructions tell me to wget a tar.gz, then extract it then do something else, so on and so on. however, if i 'sudo wget' the first tar.gz, then i would have to use sudo to extract it, leaving me with a folder in my home directory that i couldn't erase without a 'sudo rm -rf'. if this sounds oddly specific its because this exact thing happened to me...twice. after that i started slapping myself everytime i prefaced a wget with sudo:)

---

### Post by FuturePilot on 2007-12-09
> **~LoKe said:**
> I'm too paranoid to run sudo rm -rf on any directory, because I often hit return much too soon.

Me too.:shock:

---

### Post by forrestcupp on 2007-12-09
I very rarely use the command line, so I don't really have to worry about it.

---

### Post by boast on 2007-12-09
> **forrestcupp said:**
> I very rarely use the command line, so I don't really have to worry about it.

blasphemy!!!!

---

### Post by erfahren on 2007-12-10
> **boast said:**
> blasphemy!!!!
rofl !

I think [jdong's main post about this](http://ubuntuforums.org/announcement.php?f=73) (that appears above every category) covers some of the other commands that could be malicious. 

I was messing around one day trying to learn using the find command with -exec and forgot to put in the "-name" option. I ended up completely destroying my home directory (I think the line I entered was like: "find ~/ test1 -exec mv {} ~/temp  \;"  - I had the file "test1" somewhere and was trying to find and move it to my ~/temp)

... and this was just after I read a post somewhere where someone was saying to be careful using it.

*everything* in my home directory was moved to that temp directory, and not "neatly" either. What a mess! I had *mv* set as interactive in my .bash_aliases but apparently it didn't come into play.

Anyway, sudo wouldn't even need to be used with rm to mess someone up. Just a "rm -rf ~/" would as well, wouldn't it? (Edit: more like  *rm -rf ~/**  I guess)

---

### Post by toupeiro on 2007-12-10
I've thrown my .02 cents in on this several times.  To recap, I agree with the O.P.  

Yes, I've heard the arguements that I could never think of a circumstance where you would want a *new* user to do this command; but I'm opposed to that logic.  I could never think of a circumstance where I would deter someone from using a command simply because they are new.  I would teach them what it can do, and what could happen if they use it incorrectly, but I would never tell some to never use a command.  If a new user is not mislead of what the command does, they may very well have a need to run that command with those switches someplace.  Apt-get can be malicious if you mislead someone on how to use it.  Imagine a post where someone said a prerequisite to install the latest linux based game was to do a remove of linux-image*, or a removal of xserver-*  Malicious much?  rm is not the problem, blanket command cutting and pasting without understanding it is the problem.  

In my opinion, a much better approach is to teach people the correct way to use rm, and end the public flogging sessions of this command.  If I put myself in new user shoes, and I saw hundreds of signatures saying BEWARE, DANGER, RM -RF etc etc..  all that does is deter me from ever feeling confident enough to trust the CLI, which is a very negative feeling to have going into a linux operating system.  If you really want to curb malicious posts, always put "verify these commands for your own understanding" before a helpful post, give a link to a page or something illustrating what the commands do.  There are productive ways of helping new users understand a valid post from a malicious one besides scaring them away from commands.  I've seen legit posts here where rm -rf is used to install awn-curves.  Now, how is a new user sopposed to interpret that?

Not to mention, I support hundreds of people local to me who use linux and UNIX on a daily basis, and I get internships every year from colleges around the U.S. that I have to support.  If I give instruction to use rm -rf, I don't want people unfamiliar with linux to be so freaked out because they read somewhere that rm -rf was the root of all that is evil to type. That creates more work for me and other  people  who deal with linux and UNIX support for a living that want to teach people how to properly use it and feel confident about it.  I don't want to have to reverse engineer  misplaced socially engineered fear.  I know your intentions are good, but you are not instilling the right message.

---

### Post by macogw on 2007-12-10
Doesn't rm -rf / ask first, and only rm -rf /* actually do the bad thing?  I thought someone said that had been changed in rm.  Anyway,  the warning is only really valid with "sudo" at the beginning.  I use "rm -rf ~/src/mozilla/" or whatever to remove build directories.  I like it better than using the stupid "trash can" because things still take up space on the hard drive using the trash can.  Once in a while I do "rm -rf ~/.Trash/*" to empty it out since the delete key on the desktop sends things there instead of actually deleting them.

---

### Post by samwyse on 2007-12-10
Teach people to use 'man' and --help so they can check themselves what the command and switches do.

---

### Post by aysiu on 2007-12-10
> **samwyse said:**
> Teach people to use 'man' and --help so they can check themselves what the command and switches do.
Newcomers often cannot make any sense of the *man* or *help* pages.

I've been using Linux for two and a half years, and most of the *man* pages still make no sense to me. Imagine how confusing those pages might be for someone who's used Linux for ten minutes or only a few days.

---

### Post by ExpatPaul on 2007-12-10
> **red_Marvin said:**
> However I might disagree with the signatures that only focus on rm -rf, there are a sea of potentially dangerous commands out there...

This is a good point. I think there is a lot to be said for trying to make sure hust how much authority **sudo** gives you.

---

### Post by gn2 on 2007-12-10
> **aysiu said:**
> I cannot think of any situation in which I would advise a new user to type or paste in a command that starts with *sudo rm -rf*


Let me remind you: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

(illustration second from bottom of the page)

---

### Post by Flyingjester on 2007-12-10
I'm keeping mine the way it is for a simple reason, if you know enough about linux to disregard my signature warning, then you don't need the warning.

---

### Post by aysiu on 2007-12-10
> **gn2 said:**
> Let me remind you: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

(illustration second from bottom of the page)
I would not advise a new user to follow that tutorial. Here is a disclaimer from the top of that page: > I and others have been successful in creating a separate /home partition using this tutorial, but there are many who have had difficulty being successful with the process. If you are not confident in what you're doing or in repairing or recovering from this process should anything go wrong, then do not attempt the instructions outlined here. I cannot help you troubleshoot problems that result from following this tutorial. In any case, I explain what that command does.

---

### Post by user1397 on 2007-12-10
> **aysiu said:**
> I disagree that it has many legitimate uses, and I cannot think of any situation in which I would advise a new user to type or paste in a command that starts with *sudo rm -rf*

Well-intentioned though the helper may be, there is too much room for error if someone hits *Enter* too early or hits the wrong key.
I use it a lot in my /var/www/ directory, as I have a web server and I'm constantly trying out new designs for my website, and when I want to completely scratch out a design I don't like, I have to delete that folder; the easiest way to do that is with sudo rm -rf [insert-dir-here]

I know there aren't that many cases, and usually you could just use rm -rf if you're in your home directory, but I can't believe you can't think of *any* uses...

---

### Post by toupeiro on 2007-12-10
> **aysiu said:**
> Newcomers often cannot make any sense of the *man* or *help* pages.

I've been using Linux for two and a half years, and most of the *man* pages still make no sense to me. Imagine how confusing those pages might be for someone who's used Linux for ten minutes or only a few days.

ok.  In Aysiu's defense, I can admit that man pages of complex commands like sed, awk, strings, etc can be complicated but these commands are truly 'advanced' commands in their nature, and I don't believe that is a true statement for the majority of common system commands like "cp, mv, pwd, dir, touch or rm"  Through any teaching experience I've ever conducted, or been through, their are some very fundamental principles taught.  One is: creating a file, files, or directories and another is deleting a file, files or directories.  All of a sudden it seems that deleting recursively became taboo because of some social engineering scheme?  Im sorry, but thats kind of like saying its the cars fault (not the person driving) for hitting someone  because they were told by a random person that it was safe to cross a street at a certain place when it really wasn't.  Weren't you also taught "look both ways before you cross?"

Just because some man pages can be wordy, doesn't mean they all are.  In the first few lines, you know exactly what rm is for:

**MAN of RM from Solaris 8:**

NAME
       rm - remove files or directories

SYNOPSIS
       rm [OPTION]... FILE...

**MAN of RM from RHEL3/4:**

NAME
       rm - remove files or directories

SYNOPSIS
       rm [OPTION]... FILE...

**MAN of RM from SGI IRIX:**

NAME
     rm, rmdir - remove files or directories

SYNOPSIS
     rm [-f] [-i] file ...
     rm -r [-f] [-i] dirname . . . [file . . .]

     rmdir [-p] [-s] dirname . . .

You can also, in your own words, describe what the commands you are posting are doing, or hyperlink them to other resources online that have better descriptions than the man pages.  I just think all this flogging of rm is misguided overkill for a problem that is a socially learned behavior to execute anything, not just rm, without really knowing what you are doing.

---

### Post by gn2 on 2007-12-10
> **aysiu said:**
> In any case, I explain what that command does.

Indeed you do, it's an excellent well crafted tutorial and I can assure you that new Linux users can easily follow it with a successful outcome.

---

### Post by aysiu on 2007-12-10
> **ubuntuman001 said:**
> I use it a lot in my /var/www/ directory, as I have a web server and I'm constantly trying out new designs for my website, and when I want to completely scratch out a design I don't like, I have to delete that folder; the easiest way to do that is with sudo rm -rf [insert-dir-here]

I know there aren't that many cases, and usually you could just use rm -rf if you're in your home directory, but I can't believe you can't think of *any* uses... I didn't say I can't think of any uses for it.

I said [quote=aysiu]I disagree that it has many legitimate uses, and I cannot think of any situation in which I would advise a new user to type or paste in a command that starts with sudo rm -rf[/quote] There are some legitimate uses, but not many.

And I can't think of any situation in which I would advise a new user (as opposed to a veteran) to use a command that starts with *sudo rm -rf*. Even if that command is appropriate for a certain situation, I think it'd be safer to have them *gksudo nautilus* and delete through the GUI. Too much room for error otherwise (hit *Enter* too soon or mistype).

---

### Post by Calash on 2007-12-10
Any Recursive action is dangerous, even more so with Sudo attached.  A chmod or chown with -r can really mess up a system.

Just my opinion on it :)

---

### Post by toupeiro on 2007-12-10
> **aysiu said:**
> I didn't say I can't think of any uses for it.

I said  There are some legitimate uses, but not many.

And I can't think of any situation in which I would advise a new user (as opposed to a veteran) to use a command that starts with *sudo rm -rf*. Even if that command is appropriate for a certain situation, I think it'd be safer to have them *gksudo nautilus* and delete through the GUI. Too much room for error otherwise (hit *Enter* too soon or mistype).

interestingly enough, the most devastating mistake I ever made to a production environment was using an Active Directory GUI as an administrative account on Windows (no different than Nautilus as root).  I think that highlighting and hitting the delete  key is a quicker way to kill yourself than typing a command string.

I don't think I know how to make my point and concern any clearer, so I won't harp on it anymore, I'm just trying to curb any unnecessary FUD around rm.

---

### Post by aysiu on 2007-12-10
> **toupeiro said:**
> interestingly enough, the most devastating mistake I ever made to a production environment was using an Active Directory GUI as an administrative account on Windows (no different than Nautilus as root).  I think that highlighting and hitting the delete  key is a quicker way to kill yourself than typing a command string.

I don't think I know how to make my point and concern any clearer, so I won't harp on it anymore, I'm just trying to curb any unnecessary FUD around rm.
I'm not saying mistakes can *never* be made in the GUI.

But newcomers are already familiar with the types of accidental deletions that can happen in the GUI. The danger of *sudo rm -rf*ing the wrong thing is greater for those unfamiliar with the power of the terminal.

And Ubuntu defaults to the Delete key moving items to the trash, not immediately deleting them.

---

### Post by p_quarles on 2007-12-10
> **toupeiro said:**
> interestingly enough, the most devastating mistake I ever made to a production environment was using an Active Directory GUI as an administrative account on Windows (no different than Nautilus as root).  I think that highlighting and hitting the delete  key is a quicker way to kill yourself than typing a command string.

I don't think I know how to make my point and concern any clearer, so I won't harp on it anymore, I'm just trying to curb any unnecessary FUD around rm.
Nautilus will send it to the trash folder instead of deleting it altogether. It also warns you about removing directories, even in root. 

Yes, you have made your point perfectly clear. No one is disputing that "rm" can be a useful command, and no one is claiming that it's the only dangerous command. 

However: "rm" was specifically given to users in the ABT section as a prank. That's why people are warning new users about that specific command. That's not FUD about rm, it's pointing out that it can easily break your installation completely. And, yes, there are other ways of breaking a system: the link in my signature provides a detailed discussion of this topic.

---

### Post by Dimitriid on 2007-12-10
I see the points of both the "scare" and the "educate" stands here. However I am a proponent of using the GUI to teach users CLI: more apps should at least have the option of being transparent and put a little  cli window so you can see what its going on your system like synaptic.

But truth to be told, if you are gonna help new users, as annoying and time/resource comsuming as it is, screenshots and directions to do things on GUI should be preferable than giving "oh yea just type this on terminal: " solutions which contribute to the problem as much as malicious people.

---

### Post by toupeiro on 2007-12-10
fair enough..

ok.  So since I am not in front of, or near an ubuntu system right now.  If I were to use gksu nautilus and delete something.  which trash directory does it go in, mine or roots?  

gksu nautilus is not necessarily cross platform.  not that its ubuntu specific, but doesn't do me any good on RHEL or any other linux distro where I don't have gnome or gksudo installed.

---

### Post by conehead77 on 2007-12-10
> **aysiu said:**
> Newcomers often cannot make any sense of the *man* or *help* pages.

I've been using Linux for two and a half years, and most of the *man* pages still make no sense to me. Imagine how confusing those pages might be for someone who's used Linux for ten minutes or only a few days.

I completely agree. There are few people like aysiu who can think like a inexperienced Linux user.
If you are used to Linux you tend forget how it was in the beginning.

---

### Post by toupeiro on 2007-12-10
> **conehead77 said:**
> If you are used to Linux you tend forget how it was in the beginning.

mmm..  well you are talking about two different world exposure levels of linux, at least in my case, so that is not really a fair statement.  I never had something as diverse as ubuntuforums.org in my beginnings.  However, having had several beginnings on several different OSes over the last 10 years (one of them I picked up this year which I am now supporting), I take two things into each one of them:  the fact that I am new, and the fact that I want to learn.  man and ? or -? or /? or --? or --help, or F1 and all the other universal switches for help systems get used very frequently by me, regardless of my knowledge level.  

I guess it comes down to how you look at yourself being new to something.  Do you want to learn how to do something, or do you want to be told what to do?

I suppose solutions have to exist for both.

---

### Post by aysiu on 2007-12-10
> **toupeiro said:**
> 
ok.  So since I am not in front of, or near an ubuntu system right now.  If I were to use gksu nautilus and delete something.  which trash directory does it go in, mine or roots?   It goes into /root/.Trash

---

### Post by toupeiro on 2007-12-10
> **aysiu said:**
> It goes into /root/.Trash

*nods*  

maybe conehead is right then :)  Because recovering from this location -- to me--, would be more confusing as a new user than just having someone explain to me what rm -rf does and why I should understand when and where to use it.

---

### Post by aysiu on 2007-12-10
> **toupeiro said:**
> 
maybe conehead is right then :)  Because recovering from this location -- to me--, would be more confusing as a new user than just having someone explain to me what rm -rf does and why I should understand when and where to use it. I guess the point is that it *can* be recovered relatively easily. Whereas deleting with *sudo rm -rf* erases the file(s) completely unless you quickly reboot your computer with a live CD and use some kind of recovery software to salvage what files are still salvageable.

> **toupeiro said:**
> 
I guess it comes down to how you look at yourself being new to something.  Do you want to learn how to do something, or do you want to be told what to do? The two aren't mutually exclusive. When I was new, I did, in fact, just want to be told what to do, as my main concern was getting my system up and running. Once I got comfortable with Ubuntu, I then took the time to understand a few more things. Many new users want solutions first and understanding second. There's nothing wrong with this approach... except that you have to trust the people giving you commands. Since I used [http://www.ubuntuguide.org](http://www.ubuntuguide.org) mostly (instead of commands given from one user in one thread), I didn't worry too much about malicious intent (I figured if the Ubuntu Guide had malicious commands in it, someone would have mentioned that somewhere).

---

### Post by toupeiro on 2007-12-10
> **aysiu said:**
> 
 The two aren't mutually exclusive. When I was new, I did, in fact, just want to be told what to do, as my main concern was getting my system up and running. Once I got comfortable with Ubuntu, I then took the time to understand a few more things. Many new users want solutions first and understanding second. There's nothing wrong with this approach... except that you have to trust the people giving you commands. Since I used [http://www.ubuntuguide.org](http://www.ubuntuguide.org) mostly (instead of commands given from one user in one thread), I didn't worry too much about malicious intent (I figured if the Ubuntu Guide had malicious commands in it, someone would have mentioned that somewhere).

You make a good point here.  I didn't really look at it in quite that light.  I have no soap box for that.  ;-) 

 That really does kind of come down to what conehead talked about, because such guides did not really exist the first time I installed RedHat 5.2.  I just learned a different way I guess.  It doesn't make the approach you outlined wrong, its just harder for me to identify with that approach so , in the case of the rm signatures, It seemed like people were focusing attention on the wrong points.  While I will still take the approach of understanding > social engineering, I see a bit better where you are coming from.  I do appreciate your patience in your responses!

---

### Post by aysiu on 2007-12-10
The point about *rm -rf* not being the only dangerous command and having practical uses (not always dangerous ones) and that education is important are points well taken, and I'm glad we've been able to see that side of the issue.

But there are many sides to it, and the truth is that *sudo rm -rf* appears to be the most prevalent among the dangerous commands given in the past month or so, and it's also possible that new users could become paranoid about all commands.

Ultimately, when it comes down to pragmatism, users are either going to trust other users or they are generally going to find things themselves. If a user is going to Google or *man* every single command given, that user is probably more inclined to find answers on her own anyway (and not post a thread for a question that's been asked thousands of times before).

The best practical advice would actually be to wait an hour or two before executing commands someone posts. On these forums, that's ample time for someone to jump in and say, "No, don't run that command. It's dangerous!"

---

### Post by t0p on 2007-12-11
I periodically tidy up my home directory, getting rid of files I no longer need.  I tend to do this in CLI as I find such tasks much faster there.

If I want to delete a directory that contains files, I'll use rm -r.  The alternative is to delete each file in the directory and then the directory itself.  Potentially hundreds of words to type, when rm -r is so much easier.

Yeah, if you do it in the wrong place you're gonna cause yourself some problems.  But rm -r, rm -rf and sudo rm -rf *have* got uses!

---

### Post by aysiu on 2007-12-11
> **t0p said:**
> 
Yeah, if you do it in the wrong place you're gonna cause yourself some problems.  But rm -r, rm -rf and sudo rm -rf *have* got uses! No one is denying the commands have uses.

The commands, however, are usually not necessary (the same task can be accomplished another way), and they are especially dangerous for new users to type into the terminal.

---

### Post by Presto123 on 2007-12-11
> **boast said:**
> blasphemy!!!!

Hrmm...Cupp must be an Ubuntu purist. ;P

---

### Post by Nekiruhs on 2007-12-11
I found a very good example of a signature warning:

Running "rm -rf" permanently deletes files. Make sure you know what you are doing before running it!

It explains and warns, thereby accomplishing both tasks.

---

### Post by mcduck on 2007-12-11
> **Nekiruhs said:**
> I found a very good example of a signature warning:

Running "rm -rf" permanently deletes files. Make sure you know what you are doing before running it!

It explains and warns, thereby accomplishing both tasks.Thanks :D

I changed my sig to that when you created this thread. Before it I had pretty much the kind of warning this thread was about..

---

### Post by erfahren on 2007-12-14
LOL ! I think the best signature I've seen regarding this is [Incense's](http://ubuntuforums.org/member.php?u=94820)
> 
[COLOR="Red"]*Practice safe text.*[/COLOR] Never run a command unless you know exactly what it is going to do.


---

