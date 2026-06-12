---
title: "Why do you need root to shut down via CLI but not via GUI?"
date: 2009-07-16
forum: The Cafe
---

### Post by l-x-l on 2009-07-16
OK... I'm a relative linux noob but one thing I don't get about linux & Ubuntu. Why do you need sudo privileges to shutdown/reboot a **DESKTOP** OS in CLI but in GUI those privileges aren't requested to perform the requested function?

I could understand in a server environment where you'd want to restrict that but on a **desktop** OS, why do u need sudo to do the following in CLI:

1. poweroff
2. reboot
3. sudo shutdown -h now
4. sudo shutdown -r now

I'm tempted to send in a paper-cut on it. Someone help me with the logic.

---

### Post by t4thfavor on 2009-07-16
because if your sitting at your desktop, you usually know if others are using it. When I ssh into my desktop from work, and my wife is on the PC, I tend to want to have to think twice about rebooting my PC hence the password.

It gives you a second change to think about what you are doing, and you cannot accidentally select the command by pressing up arrow, and then enter.


With the GUI you get a prompt that tells you there are others logged onto the system, and you could possibly lose unsaved data.

Make sense?

---

### Post by l-x-l on 2009-07-16
> **t4thfavor said:**
> because if your sitting at your desktop, you usually know if others are using it. When I ssh into my desktop from work, and my wife is on the PC, I tend to want to have to think twice about rebooting my PC hence the password.

It gives you a second change to think about what you are doing, and you cannot accidentally select the command by pressing up arrow, and then enter.


With the GUI you get a prompt that tells you there are others logged onto the system, and you could possibly lose unsaved data.

Make sense?

Actually no it doesn't make sense. Instead of asking for a password why doesn't it just ask for confirmation with a "[Y/N/?]" prompt like other apps I've seen do. Why the requirement for a password to do such a mundane task?

Edit: Actually instead of just asking for confirmation, shouldn't you be informed that there are other users still logged on? Then if you want to proceed, ask for sudo privileges?

---

### Post by doas777 on 2009-07-16
linux is unix's younger. unix is a multi-user system that allows many people use it at once over terminal sessions. it would be really bad if some stupid user shutdown my session while rebooting the server I was connected to.

---

### Post by khelben1979 on 2009-07-16
On Debian Lenny I'm able to reboot the system without root priviliges if I reboot from graphical mode.

I wouldn't say that this is a Linux thing, it's about user priviliges.

---

### Post by l-x-l on 2009-07-16
> **doas777 said:**
> linux is unix's younger. unix is a multi-user system that allows many people use it at once over terminal sessions. it would be really bad if some stupid user shutdown my session while rebooting the server I was connected to.

I understand your point but if you re-read my initial post I made a concerted effort to highlight the word **desktop**. In a **desktop** environment like ubuntu (non-server edition) where 95% of the time the user knows if additional people are logged into their pc, why is their a requirement to provide sudo privileges via cli?

I did an experiment & logged into multiple GUI accounts on my laptop. When I tried to shutdown with multiple users logged in, it asks for sudo privileges. When only 1 user is logged in there's no requirement for sudo privilege to shutdown/reboot. This behavior makes sense.

Why can't this same behavior be replicated in the cli environment? Why can't the system check to see if others are logged in first before requesting sudo privileges in a **desktop** CLI environment?

Please don't flame me for asking. My question is one of consistency hence my suggestion of making a papercut request.

---

### Post by l-x-l on 2009-07-16
> **khelben1979 said:**
> On Debian Lenny I'm able to reboot the system without root priviliges if I reboot from graphical mode.

I wouldn't say that this is a Linux thing, it's about user priviliges.

Good to know. Thx.

---

### Post by t4thfavor on 2009-07-16
We can reboot without root using graphical as well, just not from the CLI. Which I would imagine is the same on your Lenny install.

He's asking why we cannot do it from the CLI without root, and I am saying that its better to ask for root, then to let the user reboot on a whim. It's the same underlying system on both the server, and desktop OS's, so it just makes more sense to require root like you would on a server then to maintain two seperate base installs for the same OS.

If you argue about being noob friendly I will just say "Stay off the CLI".


plus, I am sure you could change permissions on poweroff, and shutdown to allow any old user to do it. Or you could just add yourself to the root group or whatever, and I bet it would never ask you again.



EDIT:

Open up a terminal, and type uptime

what do you see?
```

15:28:22 up 2 days,  5:07,  4 users,  load average: 0.09, 0.21, 0.26

```
each terminal is considered a user, I'm not sure what significance that has, I just wanted to add it.

---

### Post by ddrichardson on 2009-07-16
> **l-x-l said:**
> OK... I'm a relative linux noob but one thing I don't get about linux & Ubuntu. Why do you need sudo privileges to shutdown/reboot a **DESKTOP** OS in CLI but in GUI those privileges aren't requested to perform the requested function?

I could understand in a server environment where you'd want to restrict that but on a **desktop** OS, why do u need sudo to do the following in CLI:

1. poweroff
2. reboot
3. sudo shutdown -h now
4. sudo shutdown -r now

I'm tempted to send in a paper-cut on it. Someone help me with the logic.
You know, you can change that.  Adding yourself to the power group is all it takes.

You needn't issue a password to do it from the GUI though, so not sure if its in papercut territory.

Edit: Should've actually checked on an Ubuntu box first as there appears not to be a power group.  You can still sort it but would need to add a group.

---

### Post by l-x-l on 2009-07-16
> **t4thfavor said:**
> 

If you argue about being noob friendly I will just say "Stay off the CLI".


I'm not afraid of the CLI at all, in fact I love it. I've been spending a lot of time using the CLI to improve my overall Linux skills & to try to automate some tasks. Hence why I noticed the inconsistency between the GUI & CLI.

---

### Post by l-x-l on 2009-07-16
> **ddrichardson said:**
> You know, you can change that.  Adding yourself to the power group is all it takes.

You needn't issue a password to do it from the GUI though, so not sure if its in papercut territory.

Edit: Should've actually checked on an Ubuntu box first as there appears not to be a power group.  You can still sort it but would need to add a group.

Well maybe this isn't paper-cut territory but I noticed an inconsistency so that's why I asked here first. I also noticed that there isn't a "power" group.

---

### Post by ddrichardson on 2009-07-16
> **l-x-l said:**
> Hence why I noticed the inconsistency between the GUI & CLI.
Thats because there isn't a GUI and a CLI (by the way they're called terms in the Linux world).  There are umpteen of them so there are always going to be inconsistencies as different people see different methods as better or worse, I hope this stays the same as its Linux's greatest strength that anyone can tailor it to their own needs.

---

### Post by ddrichardson on 2009-07-16
> **l-x-l said:**
> Well maybe this isn't paper-cut territory but I noticed an inconsistency so that's why I asked here first. I also noticed that there isn't a "power" group.
I didn't say it wasn't a paper cut - just that I wasn't sure because the majority of people will use the GUI.

---

### Post by khelben1979 on 2009-07-16
> **t4thfavor said:**
> We can reboot without root using graphical as well, just not from the CLI. Which I would imagine is the same on your Lenny install.

That's right. And if I would add more users to my system I should be able to disable their permissions to do a reboot from graphical mode if I want to, but I would not be able to stop them from pulling out the power cable.. [-X :-D

---

### Post by doas777 on 2009-07-16
> **l-x-l said:**
> I understand your point but if you re-read my initial post I made a concerted effort to highlight the word **desktop**. In a **desktop** environment like ubuntu (non-server edition) where 95% of the time the user knows if additional people are logged into their pc, why is their a requirement to provide sudo privileges via cli?

I did an experiment & logged into multiple GUI accounts on my laptop. When I tried to shutdown with multiple users logged in, it asks for sudo privileges. When only 1 user is logged in there's no requirement for sudo privilege to shutdown/reboot. This behavior makes sense.

Why can't this same behavior be replicated in the cli environment? Why can't the system check to see if others are logged in first before requesting sudo privileges in a **desktop** CLI environment?

Please don't flame me for asking. My question is one of consistency hence my suggestion of making a papercut request.

good questions. the reason as I understand it, is that *nix is developed to use a "monolithic" kernel. everything that the kernel needs for all it's possible tasks is in there. as a result, there is no special kernel for Servers/cli-clients that is differant from the GUI. also X-Windows and gnome and whatnot, are used in remote terminal sessions everyday, so just because you are in gnome does not mean that you are on a single user system. 

a shutdown involves changing hardware states; a task almost always reserved for root. some newer "user-space" technologies like the network-manager and fuse allow normal users to approximate some hardware features (like cd autoplay or dynamic selection of wifi connections) but something like a shutdown could not be localized to a single user. 

in most cases, being able to shutdown a box against the admins will is considered a Denial of Service attack vector.

---

### Post by l-x-l on 2009-07-16
doas777,

That's the most instructive answer I've heard thus far. Thanks.

---

### Post by bodhi.zazen on 2009-07-16
It is "silly" on a single user system, but it is not so silly on a multiuser system.

Unlike windows, *unix is built from the ground up to be multi-user and is thus more secure.

This is one example as outlined by doas777.

I would add, if you are connected to the internet, you do not really have a single user system. The recent (and as of yet unpatched) FireFox 3.5 vulnerability is a classic example (this vulnerability allows shell access via malignant JavaScript).

---

### Post by CatKiller on 2009-07-16
> **l-x-l said:**
> Why do you need sudo privileges to shutdown/reboot a **DESKTOP** OS in CLI but in GUI those privileges aren't requested to perform the requested function?

...

Someone help me with the logic.

I think you'll find that there isn't any. They both use different methods to achieve the same result, and so it would take a concerted effort to make them behave consistently. I shouldn't imagine that that will happen, not least of all because CLI-only users are going to want to keep the default as-is, and being able to turn on the computer but not shut it down again for a graphical-only user is just stupid. Historical factors and different use cases are what created this inconsistency and will probably mean that it will hang around for quite some time.

---

### Post by mcduck on 2009-07-16
> **l-x-l said:**
> I understand your point but if you re-read my initial post I made a concerted effort to highlight the word **desktop**. In a **desktop** environment like ubuntu (non-server edition) where 95% of the time the user knows if additional people are logged into their pc, why is their a requirement to provide sudo privileges via cli?

I did an experiment & logged into multiple GUI accounts on my laptop. When I tried to shutdown with multiple users logged in, it asks for sudo privileges. When only 1 user is logged in there's no requirement for sudo privilege to shutdown/reboot. This behavior makes sense.

Why can't this same behavior be replicated in the cli environment? Why can't the system check to see if others are logged in first before requesting sudo privileges in a **desktop** CLI environment?

Please don't flame me for asking. My question is one of consistency hence my suggestion of making a papercut request.

There is no real difference between desktop version of Ubuntu and server version. They are one and the same OS, only giving you a slightly different setup from the installation.

It only makes sense that Ubuntu behaves the same way regardless of which installation CD you use as your starting point.

You simply can't divide Ubuntu systems to desktop or server machines, quite many people run server apps on desktop version, or desktops on server version, and both can be multiuser setups. In other words Ubuntu isn't a "desktop OS", not even if you install it from the desktop installer. It's OS for both desktop and server use and every Ubuntu install CD can be used to setup CLI-only server systemor desktop system with any of the available desktop environments and window managers. Or something taht combines all these things.

Anyway, the basic rule is that everything that affects the whole system is admin level task. And shutdown definitely affects the whole system and all it's users. Being able to shutdown/reboot from Gnome & KDE without a password is an exception created to help desktop users, but if you'll try any other window manager you'll notice that you need password to shutdown the machine.

---

### Post by battleTop on 2009-07-16
> **l-x-l said:**
> OK... I'm a relative linux noob but one thing I don't get about linux & Ubuntu. Why do you need sudo privileges to shutdown/reboot a **DESKTOP** OS in CLI but in GUI those privileges aren't requested to perform the requested function?

I could understand in a server environment where you'd want to restrict that but on a **desktop** OS, why do u need sudo to do the following in CLI:

1. poweroff
2. reboot
3. sudo shutdown -h now
4. sudo shutdown -r now

I'm tempted to send in a paper-cut on it. Someone help me with the logic.

Well, if a hacker has gained access to your system via CLI, you don't want them shuting you down. The password is just another security layer that keeps you safer than you would be in Windows.

---

### Post by battleTop on 2009-07-16
> **khelben1979 said:**
> That's right. And if I would add more users to my system I should be able to disable their permissions to do a reboot from graphical mode if I want to, but I would not be able to stop them from pulling out the power cable.. [-X :-D

LMAO. Or just hold the power button down.

---

### Post by mcduck on 2009-07-16
> **battleTop said:**
> LMAO. Or just hold the power button down.

Only if they are local users. ;)

Remote user would have quite hard time pulling the power cord or pushing the power button.

---

### Post by doorknob60 on 2009-07-16
That's just how Linux (and UNIX) works. The only reason you don't need root privilages to shutdown from the GUI is GDM is running with root privilages in the background, and when you click shutdown it tells GDM to shutdown. I don't use a Login Manager, and I can't do that (although there's workarounds with /etc/sudoers and using other pgorams). Gnome, KDE, XFCE, and LXDE all do that I'm pretty sure.

---

### Post by Friqenstein on 2009-07-16
As many have already stated before, it's about security.
And as you keep pointing out **Desktop** OS is just that... a Desktop.
When you are in CLI you are NOT in your desktop. So why should you have the same access rights as a user in GUI mode?

Aside from that, most people who use the CLI use it because they prefer it to the GUI counter part. And as stated before, sudo helps even the most geeky of gurus from making the slightest mistakes.
And, aside from that, if someone logs in remotely (whether you know it or not) do you really want them to be able to shutdown your Desktop OS from their CLI environment? That seems kinda silly.

Sudo is there for a reason. If it is a complete over-the-head understanding, then perhaps the CLI is not for you. Not trying to be brash or harsh, just stating the facts. 'Keyboard Cowboys' will tell you they despise the GUI and can do faster with a keyboard and terminal that you can with multiple mouse clicks... while some think this is non-sense, others whole heartedly agree.

Aside from all of that, if you are only wanting to use a Single User Desktop OS, then why would you ever bother shutting down from the terminal anyway?

---

### Post by aysiu on 2009-07-16
I think you need it in the GUI, too, but the popular GUIs (Gnome and KDE) have some kind of running service that starts up with root privileges allowing the user to have root privileges just for shut down and rebooting tasks.

A few years ago, Xfce did not have this built in, so you would have to manually edit the /etc/sudoers file to allow particular users to issue the *shutdown* command without a password.

In IceWM (and I think other window managers as well), you still have to do that /etc/sudoers fix; otherwise you can't shut down or reboot.

---

### Post by ieBrazil on 2009-07-16
Man, I'll tell you as clearly as language may be possible: I DID NOT EVEN UNDERSTAND YOUR QUESTION. WHAT ARE YOU TALKING ABOUT??

Anyway, good luck!

I'm outta here.


ie


> **l-x-l said:**
> OK... I'm a relative linux noob but one thing I don't get about linux & Ubuntu. Why do you need sudo privileges to shutdown/reboot a **DESKTOP** OS in CLI but in GUI those privileges aren't requested to perform the requested function?

I could understand in a server environment where you'd want to restrict that but on a **desktop** OS, why do u need sudo to do the following in CLI:

1. poweroff
2. reboot
3. sudo shutdown -h now
4. sudo shutdown -r now

I'm tempted to send in a paper-cut on it. Someone help me with the logic.

---

### Post by ZankerH on 2009-07-16
Real men run gdm as root. 

:popcorn:

---

### Post by aysiu on 2009-07-16
> **ZankerH said:**
> Real men run gdm as root. 

:popcorn:
I thought GDM automatically runs as root. Isn't that why it's in /etc/init.d?

---

### Post by doas777 on 2009-07-16
looks like it:
```
~$ sudo ps -ef | grep gdm
root      4826     1  0 17:42 ?        00:00:00 /usr/sbin/gdm
root      4827  4826  0 17:42 ?        00:00:00 /usr/sbin/gdm
root      4832  4827  2 17:42 tty7     00:00:41 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7

```

---

### Post by bash on 2009-07-16
Actually you can shut down/reboot the computer **without** sudo from the CLI, if you issue the right dbus command. As this is what happens when you click on Shutdown/Reboot in the GUI.

---

### Post by mcduck on 2009-07-16
> **aysiu said:**
> I thought GDM automatically runs as root. Isn't that why it's in /etc/init.d?

I've understood that GDM itself runs as root, while the interface (gdmgreeter and gdmlogin) run as user "gdm".


edit: That's also what GDM documentation says:
> 
The GDM daemon normally runs as root, as does the slave. However GDM should also have a dedicated user id and a group id which it uses for its graphical interfaces such as gdmgreeter and gdmlogin.
.
.
By default GDM assumes the user and the group are called "gdm".

[http://projects.gnome.org/gdm/docs/2.14/security.html]("http://projects.gnome.org/gdm/docs/2.14/security.html")

---

### Post by Wiebelhaus on 2009-07-16
> **l-x-l said:**
> OK... I'm a relative linux noob but one thing I don't get about linux & Ubuntu. Why do you need sudo privileges to shutdown/reboot a **DESKTOP** OS in CLI but in GUI those privileges aren't requested to perform the requested function?

I could understand in a server environment where you'd want to restrict that but on a **desktop** OS, why do u need sudo to do the following in CLI:

1. poweroff
2. reboot
3. sudo shutdown -h now
4. sudo shutdown -r now

I'm tempted to send in a paper-cut on it. Someone help me with the logic.

This is a very good question! One that improves the community discussion and I appreciate that , I think others have already done a fantastic job of answering your question.

---

### Post by sdlynx on 2009-07-16
> **t4thfavor said:**
> 
It gives you a second change to think about what you are doing, and you cannot accidentally select the command by pressing up arrow, and then enter.


you could technically because after sudo'ing once you don't need to type the password anymore

also I'm thinking maybe this is because that way a program that is running cannot shutdown your computer.

---

### Post by l-x-l on 2009-07-16
> **battleTop said:**
> Well, if a hacker has gained access to your system via CLI, you don't want them shuting you down. The password is just another security layer that keeps you safer than you would be in Windows.

Makes no sense. If a hacker has already gained access to your system what's to stop them from shutting it down. Getting access is the hard part.

---

### Post by MaxIBoy on 2009-07-16
From what I understand, you do need root access to shut down in every case. It's just that there's a daemon which is already running as root, and when you send it the right signal, it has the permissions needed to shut down. It's like a voluntarily-installed rootkit.

It might be that one wants to stop a computer from being shut down (if it's a "shell account" server or a time-sharing machine, for example.) In that case, you edit the policies in policykit.

It's still kinda dumb to require different levels of authorization that way. That's why, on my computer, you need root access to shut down, doesn't matter how you do it.

---

### Post by l-x-l on 2009-07-16
> **Friqenstein said:**
> 
Sudo is there for a reason. If it is a complete over-the-head understanding, then perhaps the CLI is not for you. Not trying to be brash or harsh, just stating the facts.  

What "facts" were stated from your sentence above? Did u read the post where I said I like using CLI? Do u even read before u post? Or are all your posts knee-jerk reactions?

> **Friqenstein said:**
> 
'Keyboard Cowboys' will tell you they despise the GUI and can do faster with a keyboard and terminal that you can with multiple mouse clicks... while some think this is non-sense, others whole heartedly agree.
 

Why are you trying to derail the thread? My post wasn't about GUI vs CLI. You're free to start your own thread on that topic.

> **Friqenstein said:**
> 
Aside from all of that, if you are only wanting to use a Single User Desktop OS, then why would you ever bother shutting down from the terminal anyway?

Again, did u even bother reading any of my posts before the knee jerk reactions? Who said I wanted to use a Single user Desktop OS? R.I.F. (Reading is Fundamental).

---

### Post by bodhi.zazen on 2009-07-16
> **l-x-l said:**
> R.I.F. (Reading is Fundamental).

LOL to death :)

---

### Post by l-x-l on 2009-07-16
> **doorknob60 said:**
> That's just how Linux (and UNIX) works. The only reason you don't need root privilages to shutdown from the GUI is GDM is running with root privilages in the background, and when you click shutdown it tells GDM to shutdown.

> **aysiu said:**
> I think you need it in the GUI, too, but the popular GUIs (Gnome and KDE) have some kind of running service that starts up with root privileges allowing the user to have root privileges just for shut down and rebooting tasks.

> **MaxIBoy said:**
> From what I understand, you do need root access to shut down in every case. It's just that there's a daemon which is already running as root, and when you send it the right signal, it has the permissions needed to shut down. It's like a voluntarily-installed rootkit.

Thanks for all these responses. Very informative & you can't learn this from a book.

---

### Post by aysiu on 2009-07-16
P.S. When you shut down from Gnome, you aren't technically using ```
/sbin/shutdown -h now
```

You're invoking the command ```
/usr/bin/gnome-session-save --shutdown-dialog
```

---

### Post by doas777 on 2009-07-16
> **l-x-l said:**
> Makes no sense. If a hacker has already gained access to your system what's to stop them from shutting it down. Getting access is the hard part.

it is kinda server-centric isn't it. I think you'll find many more linux servers with ssh enabled, than you would ubuntu desktops with vino or xdmp enabled and directly connected to the Internet. if you were hacking linux, you would probably do it via a terminal over ssh or telnet or whatever.

if your managing a server with thousands of accounts, it's only a matter of time before some stupid user hands a hacker a password (cause they jsut had to click that "win a laptop for 5$" banner blinking in the corner). at that point it's a game of privledge escalation; the quest for root. everythign you can do to make getting root harder is a good thing.

---

### Post by l-x-l on 2009-07-16
> **doas777 said:**
> it is kinda server-centric isn't it. I think you'll find many more linux servers with ssh enabled, than you would ubuntu desktops with vino or xdmp enabled and directly connected to the Internet. if you were hacking linux, you would probably do it via a terminal over ssh or telnet or whatever.


It makes sense now . I don't run or admin a server so my experience is strictly as a end-user. But your explanation & others made me realize how flexible linux is & how many of it's features are for it's use in server environments.

---

### Post by MaxIBoy on 2009-07-16
UNIX originally ran on time-sharing machines. Back then, a single computer cost so much that a university might only be able to buy two or three. A lot of college kids needed to be given access to one machine in order to complete their studies. Even into the era of personal computers, PCs weren't powerful enough (or they didn't have enough storage) for students to complete certain assignments. At the same time, the chances were pretty good that one of them would try to subvert the security of the system. As a result, people who had login accounts still needed to be treated with suspicion.

(This was all before my time. I know about this stuff the way I know about the battle of Gettysburg.)

---

### Post by earthpigg on 2009-07-16
outstanding thread!

*goes off to load his Arch virtual machine and see what user slim (gdm equivelent, i think it stands for Simple LogIn Manager) runs as...*

```
ep@ep-9:~$ uptime
 19:32:42 up 1 day, 19:33,  2 users,  load average: 2.67, 2.46, 2.49
ep@ep-9:~$ 
```

one users is ep.
what would the other user be?

gdm (since that runs as its own group/user)? or root (since i have run things with sudo)?

---

### Post by cariboo on 2009-07-16
Run w or who to see who the other user is.

---

### Post by Mehall on 2009-07-16
> **earthpigg said:**
> outstanding thread!

*goes off to load his Arch virtual machine and see what user slim (gdm equivelent, i think it stands for Simple LogIn Manager) runs as...*

```
ep@ep-9:~$ uptime
 19:32:42 up 1 day, 19:33,  2 users,  load average: 2.67, 2.46, 2.49
ep@ep-9:~$ 
```

one users is ep.
what would the other user be?

gdm (since that runs as its own group/user)? or root (since i have run things with sudo)?

I don't know what the second user is, but SLiM works a bit differently, and doesn't allow you to simply have a non-root shutdown, as it doesn't have hal integration, whereas GDM and KDM DO have hal integration, and it is that (or the subsystem of the root-level user running the gdm daemon) that allows gdm and kdm users to shutdown without supplying a password.

---

### Post by earthpigg on 2009-07-16
```
ep@ep-9:~$ who
ep       tty7         2009-07-15 00:01 (:0)
ep       pts/0        2009-07-16 19:55 (:0.0)

ep@ep-9:~$ w
 19:55:41 up 1 day, 19:56,  2 users,  load average: 2.73, 2.86, 2.76
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
ep       tty7     :0               Wed00   43:55m  2:41m  1.34s x-session-manag
ep       pts/0    :0.0             19:55    0.00s  0.12s  0.00s w

ep@ep-9:~$ uptime
 19:55:42 up 1 day, 19:56,  2 users,  load average: 2.73, 2.86, 2.76
ep@ep-9:~$ 
```

apparently, the first user is me... and the 2nd user is '*me running something to see who is logged in*'.

any way to see who has logged in since the system booted?

---

### Post by bodhi.zazen on 2009-07-16
```
last
```

---

### Post by lisati on 2009-07-16
> **MaxIBoy said:**
> UNIX originally ran on time-sharing machines. Back then, a single computer cost so much that a university might only be able to buy two or three. A lot of college kids needed to be given access to one machine in order to complete their studies. Even into the era of personal computers, PCs weren't powerful enough (or they didn't have enough storage) for students to complete certain assignments. At the same time, the chances were pretty good that one of them would try to subvert the security of the system. As a result, people who had login accounts still needed to be treated with suspicion.

(This was all before my time. I know about this stuff the way I know about the battle of Gettysburg.)

Back in the 1980s, I worked for a company which hired out computer services on their network of mainframes to a number of local businesses. Security was paramount because they didn't want the "wrong" people accessing the "wrong" information. The way it was organized was that I couldn't take a walk of a few minutes from the building I worked in, visit someone I knew at another business who worked in another building, and log in as myself - the security system was smart enough to know that the login attempt was coming from a place that wasn't normally associated with the userid.
I only ever discovered one security vulnerability on that system - and that was by piecing together a snippet of technical information I overheard in the cafeteria with some other stuff I had read somewhere.

---

### Post by Skripka on 2009-07-16
> **doorknob60 said:**
> That's just how Linux (and UNIX) works. The only reason you don't need root privilages to shutdown from the GUI is GDM is running with root privilages in the background, and when you click shutdown it tells GDM to shutdown. I don't use a Login Manager, and I can't do that (although there's workarounds with /etc/sudoers and using other pgorams). Gnome, KDE, XFCE, and LXDE all do that I'm pretty sure.

And the Archers are the first to hit the nail on the head.

---

### Post by pelle.k on 2009-07-16
> why do u need sudo to do the following in CLI:
You can use gnome-power-cmd.
```
gnome-power-cmd shutdown/suspend/hibernate/reboot
```
If you run a CLI only enviroment, i'm pretty sure you would know how to modify policykit or /etc/sudoers to allow "normal" user accounts to shut down ;)

---

### Post by Mr. Picklesworth on 2009-07-16
Eeeergh... The question is simply "why," folks.

At present, shutting down via GUI actually does require the same kind of superuser privileges you see with the raw shutdown command (which is implemented at a lower level). However, graphical desktop environments provide means to escalate privileges for the sake of user friendliness. This is often done via PolicyKit, or with existing, cautious daemons which have the needed permission taking orders by proxy.

This is all done via dbus, talking to a daemon at org.freedesktop.PowerManagement. There is a command line app called gnome-power-cmd which does the same magic you are used to on the gui.

Of course, that only happens if you are have the appropriate freedesktop power management interface on your dbus session bus, so if you are freshly logged in to a terminal (without gnome running at any level) it won't work. That one is a feature.

Edit:
'My bad, I missed the second page. Looks like people on this page read more closely ;)

---

### Post by toupeiro on 2009-07-17
> **doas777 said:**
> linux is unix's younger. unix is a multi-user system that allows many people use it at once over terminal sessions. it would be really bad if some stupid user shutdown my session while rebooting the server I was connected to.

TRUE STORY!

I run several shared servers, sometimes hosting more than 50 login sessions simultaneously.  The last thing I want is people rebooting my boxes.

---

### Post by Eclipse. on 2009-07-17
> **Mr. Picklesworth said:**
> Eeeergh... The question is simply "why," folks.

At present, shutting down via GUI actually does require the same kind of superuser privileges you see with the raw shutdown command (which is implemented at a lower level). However, graphical desktop environments provide means to escalate privileges for the sake of user friendliness. This is often done via PolicyKit, or with existing, cautious daemons which have the needed permission taking orders by proxy.

This is all done via dbus, talking to a daemon at org.freedesktop.PowerManagement. There is a command line app called gnome-power-cmd which does the same magic you are used to on the gui.

Of course, that only happens if you are have the appropriate freedesktop power management interface on your dbus session bus, so if you are freshly logged in to a terminal (without gnome running at any level) it won't work. That one is a feature.



What he said. :)

---

### Post by l-x-l on 2009-07-17
> **pelle.k said:**
> You can use gnome-power-cmd.
```
gnome-power-cmd shutdown/suspend/hibernate/reboot
```


> **Mr. Picklesworth said:**
> 
This is all done via dbus, talking to a daemon at org.freedesktop.PowerManagement. There is a command line app called gnome-power-cmd which does the same magic you are used to on the gui.

Of course, that only happens if you are have the appropriate freedesktop power management interface on your dbus session bus, so if you are freshly logged in to a terminal (without gnome running at any level) it won't work. That one is a feature.



Thx.

---

