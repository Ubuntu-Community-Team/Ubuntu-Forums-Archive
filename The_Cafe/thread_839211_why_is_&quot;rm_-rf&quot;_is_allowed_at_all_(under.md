---
title: "why is &quot;rm -rf&quot; is allowed at all (under root partition)?"
date: 2008-06-24
forum: The Cafe
---

### Post by gtdaqua on 2008-06-24
Isn't linux supposed to protect the kernel-level files? I mean, you can't delete the files needed to run linux but "rm -rf" could kill those..how and why???

---

### Post by mister_pink on 2008-06-24
It will only delete system files if you run it as root, ie add "sudo" to the beginning. Thats because when you run as root you can do absolutely anything you want to the system. It doesn't restrict this because you should probably tend to know what you're doing before you run anything with sudo, and people don't like be told what they can and can't do with their own computer anyway.

---

### Post by lswest on 2008-06-24
Also, what if you do want to delete system files, in order to replace them with backed up/uncorrupted ones?  rm -rf is there for those who know what they're doing, and can be used to remove, forcibly, files which can impact the stability of your OS.  Just like windows had "deltree" (or still does?).

---

### Post by gtdaqua on 2008-06-24
> **lswest said:**
> Also, what if you do want to delete system files, in order to replace them with backed up/uncorrupted ones?  rm -rf is there for those who know what they're doing, and can be used to remove, forcibly, files which can impact the stability of your OS.  Just like windows had "deltree" (or still does?).

You shouldnt be able to delete system files whoever you are. Windows does not allow to delete system files - it throws a warning error message and quits.

At least this musnt happen on running OS. May be you could delete system files on other mounted partitions which is not connected to the running OS. 

Thoughts??

---

### Post by fatality_uk on 2008-06-24
> **gtdaqua said:**
> You shouldnt be able to delete system files whoever you are.

I am sure many system administrators would disagree. Having the flexibility to delete said files could mean the difference between a file refresh and a clean install.

---

### Post by Trail on 2008-06-24
I like how Linux permits unlinking (deleting) open files via reference-counting. This is a direct consequence of this, so technologically, the geek in me approves :)

As for security, in terms of virii and co, I don't think that's a problem. First of, the virus would need root permitions, which is hard to obtain. Second of, if a virus did that then it would suicide along with its host, so it wouldn't be able to spread easily; if I'd make a virus I'd like it to expand to other hosts, so I wouldn't kill my host.

As far as security in terms of preventing a user's mistake, well, maybe a warning message asking for confirmation at most. A root user should be aware and responsible, after all. And, I wouldn't like it to not be at all able to delete /, it probably has its uses. chroot comes to mind. If you see a root laughing or crying, better have a backup.

---

### Post by odiseo77 on 2008-06-24
> **gtdaqua said:**
> You shouldnt be able to delete system files whoever you are. Windows does not allow to delete system files - it throws a warning error message and quits.

At least this musnt happen on running OS. May be you could delete system files on other mounted partitions which is not connected to the running OS. 

Thoughts??

Maybe someone *might* eventually need to (or be forced to due to a specific problem/situation) delete ***some*** system files for some reason (I can't think of a concrete example right now, but I almost sure this might happen). So, why limiting the usability of this command to certain levels ***only*** under the root directory? Of course, it's not a good idea to use it in the root directory because all there is behind are system files, entire set of files need for the system to run, or data files (as in /home), so, if you make a minimal mistake, like mistyping something, you could damage your system. But as I said, why limiting the usability of this command? Maybe a simple warning that it's destructive and you're running it in the top level directory would be enough, IMO (something like: "Are you sure?" and then "Do you want to continue?", something like that).

---

### Post by mister_pink on 2008-06-24
The problem is that warning for this one command is entirely arbitrary. There's a million and one ways you can completely hose your system, not least hitting it with a lump hammer, but you don't get warned about that. It's fairly simple to just not do it.

---

### Post by pmlxuser on 2008-06-24
> **gtdaqua said:**
> Isn't linux supposed to protect the kernel-level files? .how and why???

How. By running the command $sudo rm -rf
why? Oh openness its your system if you want to delete the system WHY Not you are the Boss not the operating system (like window$ -you pay alot to have a computer tell you what you canand cannot do)

Linux-You pay almost nothing to get the freedom to tell your computer or OS to do what you want it to do even to "self destruct" very cool:)

---

### Post by odiseo77 on 2008-06-24
> **mister_pink said:**
> The problem is that warning for this one command is entirely arbitrary. There's a million and one ways you can completely hose your system, not least hitting it with a lump hammer, but you don't get warned about that. It's fairly simple to just not do it.

Yeah, I know what you mean. I'm not very comfortable with the idea of a warning either. And you're right: if, for example, you use it inside /etc, /dev or /usr without knowing what you're doing, you could mess with important things and completely damage your system (but it might be needed in some cases).

---

### Post by odiseo77 on 2008-06-24
I forgot to say this: IMO, deleting, loosing data files (as those some people saves inside /home/username) is far worse than damaging your own system. If, for example, you damage your system by removing some important files for it to run, there's no big deal, you simply have to reinstall. But, if you delete some directory inside your home directory where you had all your photographs from an unforgettable travel you made in the vacations, there's no way back and you will have to conform with the memories you have of the travel :) (a similar situation would be someone who accidentally deletes a file of an important project the person has been working in for months and has to get done for the next week). So, using this command (or messing with the GUI) inside your /home/username directory could be as dangerous as using it in the root directory (but this can happen to anyone who doesn't pay too much attention to what he/she does).

---

### Post by Barrucadu on 2008-06-24
Put simply, 'rm -rf /' is allowed because the 'rm' stands for 'remove' and 'f' for 'force', and it wouldn't make sense if it *didn't* forcible remove things now, would it? If you want it to ask you about everything use 'rm -ri', or even 'rm -rvi'.

---

### Post by jrusso2 on 2008-06-24
Basically in the twelve years I have been using Linux it has always been made for people that knew what they were doing.  It was not until Ubuntu came along and disabled the root account that I even thought about that being a bad idea.  I mean it never was a problem for me, I never ran as root as that was evul but I certainly would do administration as root and it was never a problem in 12 years.

But since Ubuntu came out there is this move to make it easy and safe for the average user, Yet its still too difficult and arcane for them so its a bit pointless to do somethings and not finish it.

The way I always looked at it Windows would ask you are you sure you want to do that?  But Linux was like well its your system if you want to do that and destroy your system, your the boss, I am not going to stop you.

---

### Post by Alasdair on 2008-06-24
Why is rm -rf allowed at all? Well so you can delete stuff... It's really that simple. You should never run as root unless you absolutely need to, so I fail to see how this is a problem.

Not to mention that there are likely hundreds of commands that could trash your system, blocking one for no good reason would hardly solve any problems related to the posting of malicious commands.

---

### Post by dizee on 2008-06-24
Sometimes there is a need for it, like for example when I wanted to uninstall Google earth and the proper command didn't work, I just ended up using "sudo rm -rf /opt/googleearth". It's just a command-line equivalent of Shift+Delete in a GUI file browser anyway. The whole point of linux is that it gives you full control, of course you can end up breaking things but that's your responsibility.

---

### Post by Ozor Mox on 2008-06-24
> **jrusso2 said:**
> Basically in the twelve years I have been using Linux it has always been made for people that knew what they were doing.  It was not until Ubuntu came along and disabled the root account that I even thought about that being a bad idea.  I mean it never was a problem for me, I never ran as root as that was evul but I certainly would do administration as root and it was never a problem in 12 years.

But since Ubuntu came out there is this move to make it easy and safe for the average user, Yet its still too difficult and arcane for them so its a bit pointless to do somethings and not finish it.

The way I always looked at it Windows would ask you are you sure you want to do that?  But Linux was like well its your system if you want to do that and destroy your system, your the boss, I am not going to stop you.

I think Ubuntu provides a good central point between letting the user do what they want with their system and not treating them like an idiot, but at the same time making the computer easier to use. I wouldn't be happy if Ubuntu stopped me running the rm -rf command, not because I think I'll necessarily ever need it, but because it is a step away from me being in total control of my system.

The good thing about Linux is of course that there are so many variations of it, that anyone can pick the distribution that gives them whatever control they like, such as compiling every single application for maximum efficiency. With all the different types of users, some will always look at commands like rm -rf as giving them control, others as giving them a dangerous and unnecessary command.

---

### Post by original_jamingrit on 2008-06-24
I agree, that this would be good for Ubuntu, to implement it by default.

The difficulty would be in implementing it.  Maybe by default sudo could promote you to a sort of "sub-root" user instead of root user, where sub-root was able to preform normal admin tasks such as install from the repos and use gnome/kde's system tools.  Root would still be necessary to read and write to files directly, using mv, rm, chmod, vim or gedit, but everything that had a full front-end could be accessed by sub-root.  And of course, root would still have the ability to do everything else.  Which still solves the problem, if we teach normal users to use sub-root instead, and not touch root except for special occasions.  Does any of that make sense?

---

### Post by Majorix on 2008-06-24
Come on... "rm -rf /" (which will ONLY delete your home folder) is one of the very few exploitable things on Linux/Ubuntu and lately it is far too exaggareted on the new comers.

There has been months since the first few hackers using this way (I haven't seen any with my own eyes, but whatever), and I thought we all learned our lesson from that.

To delete system files with that command you have to run it as root, and you shouldn't run commands you can't trust with sudo/su.

---

### Post by Alasdair on 2008-06-24
Could someone explain to me, why this is even a problem? How is deleting things wrong and dangerous? Last time I checked people don't randomly go around deleting files with superuser privileges. Using rm is really not that different to deleting files using a file manager, but like all cli commands, it gives you more flexibility. Both the recursive and force options are absolutely necessary, I shudder to think how many shell scripts would break if you changed or removed rm.

---

### Post by nrs on 2008-06-24
> **gtdaqua said:**
> You shouldnt be able to delete system files whoever you are. 
No. If this were the case virtually every system update/alternation would require a reboot. It's not like just anybody has the power to do this anyways.

---

### Post by Greyed on 2008-06-24
> **odiseo77 said:**
> Maybe a simple warning that it's destructive and you're running it in the top level directory would be enough, IMO (something like: "Are you sure?" and then "Do you want to continue?", something like that).

Warnings don't help.  Because all it does is train the user to do an extra step without thinking about it.  The 2000 times to hit "yes" as a matter of habit will not stop you from doing it that 2001st time when you meant to say "no".  All it is is 2000 wasted keystroks/mouse clicks.

Besides, I could've sworn that, at least on base Debian, the system bashrc file does redefine rm -rf to prompt before executing.

---

### Post by Alasdair on 2008-06-24
But what is the point in a 'force' option if you alias it to prompt? :)

If ubuntu forced a prompt option, you could get around it with 'yes | rm -r' (or similar), that would just become the new rm -rf.

---

### Post by Mr. Picklesworth on 2008-06-24
Mhm...
I feel I should point out that the -f explicitly tells rm not to warn the user. If you want rm to warn you about potentially foolish acts, do not use the Force option.

Edit:
OOops, Alasdair beat me to it! Although the one prompt before running the command is a different behaviour than a prompt for each read-only file.

I should also point out that it's just as destructive to move / to another location, which again can be forced.

---

### Post by Greyed on 2008-06-24
> **Mr. Picklesworth said:**
> I should also point out that it's just as destructive to move / to another location, which again can be forced.

Let's not even get into the evil that is chmod or chown in the wrong directory with recursion turned on.  ;)

---

### Post by koenn on 2008-06-24
>  why is "rm -rf" is allowed at all (under root partition)?
One of the principles in the design of unix (and therefore linux as well) was that the OS should provide powerful tools so the user/administrator would be able to do what needs done. With such powerful tools, yes, you can shoot yourself in the foot, but they also allow you to fix problems that might be unsolvable with tools that are made less powerful to protect the user. 
rm -rf is just one example of this concept

In the end, it's the guy behind the keyboard that makes the decisions. You dont* have to * use wildcards in every rm statement, but the option is there should you *need* it. . you don't have to put the  -f flag in every rm statement, but it's there for those cases that you can't do without it. 

As for rm -rf / being used by crackers or malware to destroy your system : if you've come to the point where an outsider or a rogue program can run stuff with root privileges, you have more serious issues to deal with that the existence of a -r or -f option in the rm command.

---

### Post by madjr on 2008-06-24
> **gtdaqua said:**
> You shouldnt be able to delete system files whoever you are. Windows does not allow to delete system files - it throws a warning error message and quits.

At least this musnt happen on running OS. May be you could delete system files on other mounted partitions which is not connected to the running OS. 

Thoughts??

**many people here don't want to lose the freedom of shooting themselves in the foot.**

But my **Aging Grandmother** will not want this.

so the best we could do is **provide 2 options** during installation.


- Am a **POWER USER** i want all commands enabled.

- Am **NOT** a power user, i don't need **rm -rf**


**Now every 1 is happy**.


either that or add some restore thing


if linux is about choice, we also want the choice of disabling these.

else this topic will just come up over and over

---

### Post by Mateo on 2008-06-24
Why shouldn't it be allowed?  It's my files, I should be able to delete them if I want.

---

### Post by Mateo on 2008-06-24
> **madjr said:**
> **many people here don't want to lose the freedom of shooting themselves in the foot.**

But my **Aging Grandmother** will not want this.

so the best we could do is **provide 2 options** during installation.


- Am a **POWER USER** i want all commands enabled.

- Am **NOT** a power user, i don't need **rm -rf**


**Now every 1 is happy**.


if linux is about choice, we also want the choice of disabling these.

Unnecessary.  Anyone who uses sudo rm -rf is already a power user and has decided to run the command.

---

### Post by hanzomon4 on 2008-06-24
I don't get why this ever became an issue. sudo rm -rf is not some evil command. I've had to use it to get rid of files in my home dir that just wouldn't die. I even used it to delete system files. Point is telling some one never to run rm -rf "whatever" is dumb, now telling people never to run sudo rm -rf / is fine. I just don't get the hysteria around this

---

### Post by jrusso2 on 2008-06-24
> **original_jamingrit said:**
> I agree, that this would be good for Ubuntu, to implement it by default.

The difficulty would be in implementing it.  Maybe by default sudo could promote you to a sort of "sub-root" user instead of root user, where sub-root was able to preform normal admin tasks such as install from the repos and use gnome/kde's system tools.  Root would still be necessary to read and write to files directly, using mv, rm, chmod, vim or gedit, but everything that had a full front-end could be accessed by sub-root.  And of course, root would still have the ability to do everything else.  Which still solves the problem, if we teach normal users to use sub-root instead, and not touch root except for special occasions.  Does any of that make sense?

If they remove that command I would quit Ubuntu forever.  I don't need baby sitting.
People shouldn't use commands that they don't know what they do.  You can delete with the gui if your worried about it. Don't limit the people that took the time to learn how to use the system.

---

### Post by original_jamingrit on 2008-06-24
> **jrusso2 said:**
> If they remove that command I would quit Ubuntu forever.  I don't need baby sitting.
People shouldn't use commands that they don't know what they do.  You can delete with the gui if your worried about it. Don't limit the people that took the time to learn how to use the system.

I wasn't talking about removing sudo, just changing it.  Make is so that there's two sudo commands, one that behaves like sudo currently does (elevates you to root) and one that we tell new users to stick to (elevates you to a sort of a sub-root, or a crippled root).  The crippled root sudo would be used for synaptic, gnome's log-in manager, other gui stuff.  And then the true root sudo would be used for dpkg, and editing xorg.conf or fstab, and so on.

So, there's not any functionality lost, it's just that the line between 'normal' admin and 'deep-magic' admin is a bit clearer to new users.  The only real problem is that it could make things more complicated.

---

### Post by shad0w_walker on 2008-06-24
rm -rf is the best learning experience about. It's devastating and you don't forget it.

Also, The system keeps running when you run rm -rf assuming you have the programs you want still loaded into RAM. If you happen to want to do something nice and advanced there are some awesome uses for rm -rf. If you know what you are doing it's entirely possible to change distro whilst you are still running the system, perform a reboot and have the new distro boot.

To the OP: You seem to miss the point of Linux. You can do whatever you want to do. If someone runs rm -rf that is their problem. You don't take cars away because some people don't know what they are doing and crash. This is the same thing only not dangerous to lives.

I actually love rm -rf. It's a damn good learning experience. If someone runs it, they remember it's effects on the system. It reinforces that you shouldn't just run everything as root user.

---

### Post by FyreBrand on 2008-06-24
If the OS is going to be used in a server or work station setting then all the power needs to be available with no speed bumps.

But Ubuntu is promoted as an OS for all people and there are a lot of people that don't want to learn the intricacies or details that a power user/admin would but will still occasionally need to perform some administrative tasks.  If there is going to be widespread adoption for the OS into a less technically focused demographic then there should be some thought into putting a cushion between the end user and potentially hazardous operations.

People can easily wander into areas they shouldn't and not necessarily know it.  It's not that that people need babysitting or should be treated with a condescending attitude but they should be given a little space to try and get some administrative tasks accomplished without having to walk on eggshells.

---

### Post by hanzomon4 on 2008-06-24
The OP has been taken by all the stupid warnings floating around here saying that rm -rf is an evil command.

---

### Post by reyfer on 2008-06-24
Why do people talk about new users as if ALL new users will behave as they think? To be REALLY dangerous, "rm -rf" and other commands need the "sudo" or "su" and the root password....my grandmother is using Ubuntu since Feisty, and she's NEVER used the "sudo" unless a package she's installing asks for root permissions, and still she looks around (here and on other places) to see if it is safe. 

The "little space to try and get some administrative tasks accomplished without having to walk on eggshells" is given by the fact that the system itself tells you WHEN it needs root permissions to do some task, and the rest of the time you cannot do REAL harm. 

I just hate it when people here talk about new users as if they are all ignorant monkeys. People are intelligent, just let them learn.

---

### Post by Barrucadu on 2008-06-24
I have to ask, how many completely new people open the terminal and run a completely unknown command, without asking what it does first?
New users should be helped, but not treated as complete idiots.

---

### Post by cardinals_fan on 2008-06-24
> **gtdaqua said:**
> You shouldnt be able to delete system files whoever you are. Windows does not allow to delete system files - it throws a warning error message and quits.

At least this musnt happen on running OS. May be you could delete system files on other mounted partitions which is not connected to the running OS. 

Thoughts??
This is why I don't run Windows.  It also won't let you kill system processes.  I don't really like having my OS tell me what to do.

---

### Post by Greyed on 2008-06-24
> **FyreBrand said:**
> But Ubuntu is promoted as an OS for all people and there are a lot of people that don't want to learn the intricacies or details that a power user/admin would but will still occasionally need to perform some administrative tasks.

This sentence is self-contradictory.  If they still need to perform some administrative tasks then it behooves them to learn the details of performing said task, period.

To trot out the tired old car analogy what you're proposing is that someone should be able to change the brakes on their car without learning on how to properly use a jack-stand.  Do they need to know how to do it to drive their car?  No.  But when their body is under a 1/2-1 ton car do you think they should have invested a tad of brainpower in knowing where to place the jack stand so the car doesn't come down on top of them?  Yup.

Same thing.  They don't need to know it to operate the computer.  But if they get in there it is expected they expend some brain power to learn what's going on lest they do something dangerous.  If they don't want to they can do what I do when I want my brakes changed...  Hire a mechanic... er... computer tech.

---

### Post by cardinals_fan on 2008-06-24
> **greyed said:**
> this Sentence Is Self-contradictory.  If They Still Need To Perform Some Administrative Tasks Then It Behooves Them To Learn The Details Of Performing Said Task, Period.

To Trot Out The Tired Old Car Analogy What You're Proposing Is That Someone Should Be Able To Change The Brakes On Their Car Without Learning On How To Properly Use A Jack-stand.  Do They Need To Know How To Do It To Drive Their Car?  No.  But When Their Body Is Under A 1/2-1 Ton Car Do You Think They Should Have Invested A Tad Of Brainpower In Knowing Where To Place The Jack Stand So The Car Doesn't Come Down On Top Of Them?  Yup.

Same Thing.  They Don't Need To Know It To Operate The Computer.  But If They Get In There It Is Expected They Expend Some Brain Power To Learn What's Going On Lest They Do Something Dangerous.  If They Don't Want To They Can Do What I Do When I Want My Brakes Changed...  Hire A Mechanic... Er... Computer Tech.
+1

---

### Post by kevdog on 2008-06-24
I love the rm -rf command.  Its really useful to delete an entire directory tree.  Unfortunately it seems to have gotten a bad rap for obvious reasons.  A car can be deadly too, however when used properly its really helpful also.

---

### Post by toupeiro on 2008-06-24
> **fatality_uk said:**
> i Am Sure Many System Administrators Would Disagree. Having The Flexibility To Delete Said Files Could Mean The Difference Between A File Refresh And A Clean Install.

+1

---

