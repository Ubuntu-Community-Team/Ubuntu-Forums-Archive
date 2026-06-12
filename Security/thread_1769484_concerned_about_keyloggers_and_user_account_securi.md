---
title: "concerned about keyloggers and user account security"
date: 2011-05-28
forum: Security
---

### Post by gpost3 on 2011-05-28
hi folks,

i am concerned about keyloggers for ubuntu/linux. Are the keystrokes encrypted in ubuntu automatically? should I be concerned?

my other concern is ubuntu does not protect the home directory of one user from another user on the same computer. For example, upon creating another user x on my ubuntu, the user x can access all files under /home :confused:

---

### Post by Lars Noodén on 2011-05-28
> **gpost3 said:**
> ...upon creating another user x on my ubuntu, the user x can access all files under /home :confused:
The default is to share folders read-only.
Change the permissions on the folders to 750 and that capability goes away.  e.g.

```

chmod u=rwx,g=rx,o= /home/user

```

---

### Post by Lars Noodén on 2011-05-28
> **gpost3 said:**
> 
i am concerned about keyloggers for ubuntu/linux. Are the keystrokes encrypted in ubuntu automatically? should I be concerned?


Not that concerned, you can read [The Linux Security Circus: On GUI isolation](http://theinvisiblethings.blogspot.com/2011/04/linux-security-circus-on-gui-isolation.html) for a little background.  X11 does very well for the environment it was designed for.  Unfortunately the collaborative mood of computing in the 1970's and 1980's has been replaced by a fairly harsh one and some changes need to be made.

---

### Post by ajgreeny on 2011-05-28
This may help with /home privacy.  I've no idea about key-loggers.

sudo find /home/username -type f -exec chmod 644 {} \;
sudo find /home/username -type d -exec chmod 755 {} \;
sudo chmod 770 /home/username/

The first command searches for files in your /home/username, and does chmod on those files to 644.
The second command searches for directories in your /home/username, and does chmod 775 on those.
And because I didn't know whether you are sharing your computer with other people, I thought that a chmod 770 *only* for the ("top") directory /home/username would be good, so that other users cannot "cd" into your directory unless they're member of the group "username".

---

### Post by Lars Noodén on 2011-05-28
Good call.  Or this works, too:

```
sudo find /home/username -type f -exec chmod 640 {} \;
sudo find /home/username -type d -exec chmod 750 {} \;
sudo chmod 770 /home/username/

```

---

### Post by gpost3 on 2011-05-28
alright thank you my good friends. That fixed the /home problem.

> Not that concerned, you can read [The Linux Security Circus: On GUI isolation]("http://theinvisiblethings.blogspot.com/2011/04/linux-security-circus-on-gui-isolation.html") for a little backgroundI did a quick wiki on this lady. Apart from the statement that she is a researcher, there is no indication about her qualification and whether she has a degree in computer science or not and there is no indication of the authenticity/date stamp on that blog/article. Are there any better resources for this type of article? preferably a university press/research or a scholarly document? It seems she is just pissed about linux and wants to promote Qubes. Not a surprise since she is the author behind it.

And I am not sure what she is getting at with Windows Vista GUI security. Windows 7 is horrible at it because just a few weeks ago I wrote an app that use global key hooks. I can private message the app and the source code to anyone interested in learning and seeing it for yourself.

---

### Post by Lars Noodén on 2011-05-28
It isn't the best article I am sorry to admit, but it does point out the obvious flaws with how X works and provides a quick step-by-step to demonstrate the flaws.  Those flaws are one of those common knowledge things that for one reason or another doesn't really get written up.  

As to how Xenocara, Wayland and OpenStep are different, that's a good question.

(Aside, having a degree in CS means a lot less than it used to.  There are still some good schools out there but they're getting to be fewer each year.)

---

### Post by secret resistor on 2011-05-28
> **gpost3 said:**
> 
I did a quick wiki on this lady. Apart from the statement that she is a researcher, there is no indication about her qualification and whether she has a degree in computer science or not and there is no indication of the authenticity/date stamp on that blog/article. Are there any better resources for this type of article? preferably a university press/research or a scholarly document? It seems she is just pissed about linux and wants to promote Qubes. Not a surprise since she is the author behind it.


Regardless of that, what she said is 100% correct. You can easily try it yourself by running "xinput test <id>" as your normal user (without sudo) and see the keystroke events. I can also post a link to proof of concept code that prints out the actual characters being typed (after capturing them the same way) but I'm not sure if this is allowed in this forum. 

This can easily be used to capture passwords, including your password when you do sudo. I had thought that gksudo was supposed to protect against that but when I tried it I could see what I type in it as well. Not sure if this is the expected behaviour (I posted another thread about it but no replies yet).

---

### Post by bodhi.zazen on 2011-05-28
There are several types of key loggers form software to hardware.

In terms of software, for the most part, they require root access to run or at a minimum access to the user account. So if someone can run a key logger, you have already been cracked.

Ubuntu is no windows and is much more secure. I have in all the years of running Linux never seen a key logger maliciously installed on any linux system (all the key loggers I have seen are installed by either the user or the system administrator).

Linux does not suffer from malware in the same way as windows, I suggest you read the security sticky.

I am not saying Linux is invulnerable, but I would not list keyloggers as something I would worry about ;)

---

### Post by secret resistor on 2011-05-28
> **bodhi.zazen said:**
> 
In terms of software, for the most part, they require root access to run


This is simply not true, as has been shown in this thread. In a default Ubuntu (and most other distributions I think) install you can run a keylogger without root access.

> **bodhi.zazen said:**
> 
or at a minimum access to the user account. So if someone can run a key logger, you have already been cracked.


I'm not sure about that. Vulnerabilities in commonly used software show up all the time. All it takes is a 0-day exploit in your browser/flash player/etc. or a user running out-of-date software.

> **bodhi.zazen said:**
> 
Ubuntu is no windows and is much more secure. I have in all the years of running Linux never seen a key logger maliciously installed on any linux system (all the key loggers I have seen are installed by either the user or the system administrator).


That has been my experience so far as well, however saying that keyloggers are nothing to worry about in Linux (with XWindows) is dishonest at best. And I think that as the platform gets more popular we may see such attacks in the wild, unless something gets done about the XWindows/XInput problem before that.

---

### Post by Lars Noodén on 2011-05-28
> **secret resistor said:**
> 
I'm not sure about that. Vulnerabilities in commonly used software show up all the time. All it takes is a 0-day exploit in your browser/flash player/etc. or a user running out-of-date software.



Less than that is needed.  Every flash video is basically a potential trojan wrapped around an otherwise harmless video codec.  Similar for the flash animation.  Videos could more safely and more portably be distributed as a bare bones MPEG, Quicktime, WebM or Theora and skip the flash menace.

---

### Post by bodhi.zazen on 2011-05-28
> **secret resistor said:**
> This is simply not true, as has been shown in this thread. In a default Ubuntu (and most other distributions I think) install you can run a keylogger without root access.



I'm not sure about that. Vulnerabilities in commonly used software show up all the time. All it takes is a 0-day exploit in your browser/flash player/etc. or a user running out-of-date software.



That has been my experience so far as well, however saying that keyloggers are nothing to worry about in Linux (with XWindows) is dishonest at best. And I think that as the platform gets more popular we may see such attacks in the wild, unless something gets done about the XWindows/XInput problem before that.

You are jumbling several issues together and as such spreading misinformation and FUD.

1. Key loggers -

First, if you have physical access you can use a hardware key logger, period, independent of OS or any other security measures.

Second, if you have access to my account, you can install a software key logger to an account you have access to. If you have my password, and can log into my account, then yes you can install a key logger, and review any private data I have in $HOME that is not separately encrypted.

**You can not use a software key logger to monitor someone else's account without root access.**

If a cracker has leveraged an exploit such that they can access root, they it is for the most part game over. In that event installing a key logger is secondary, a result of a compromise to the root account and the defense it to prevent or close the exploit that allowed root access in the first place. Here we keep our system up to date, use strong passwords, etc.

So when discussing key loggers you need to be very clear are we discussing a hardware key logger, monitoring an account you have access to, or monitoring someone else.

Each of those 3 scenarios has a very different security implication and solution.

Second you are discussing security vulnerabilities vs exploits. Vulnerabilities, both known and unknown, have not yet been leveraged.

So yes, every application, by definition, has vulnerabilities so in theory anything is possible.

Now lets turn that into practical security (with respect to key loggers).

1. **There are no known active exploits that will install a key logger onto a linux system.** Your system was patched to the known exploits long ago. Please do not give the impression that key loggers are an active issue on Linux, they are not, they are a theoretical problem (see zero day exploits below).

2. Zero day exploits are when a vulnerability, either known or unknown, it leveraged to crack into a system. By definition they could do most anything, including installing a key logger.

The defense against zero day exploits is either apparmor (in ubuntu) or selinux (in Fedora).

So if you are worried about a key loggers :

1. You must first specify what kind ? hardware, software, etc.

The defense varies:

1. Hardware - inspect your hardware.
2. Monitoring your user - use strong passwords and do not use untrusted accounts. Encrypt your user account.
3. root - physical access == root access. If you can not physically secure your computer and you can not trust your system administrator, they, assume they are using a key logger or other mechanism to monitor your activity. Again encryption would be your only potential defense.

2. **Known , active Linux exploits using key loggers - there are none.**

3. Zero day exploits - Who knows ? Use apparmor or selinux. Even apparmor or selinux can be cracked, but those are currently the best two tools you have against zero day exploits.

---

### Post by secret resistor on 2011-05-28
The reason I'm "jumbling several issues together" is because they are  all tightly related when it comes to answering the question "are  keyloggers a concern?". And I definitely did not mean to be "spreading misinformation and FUD", so I apologise if it came out that way. 

All I was trying to say is this:
- a rogue application with access to the X session can monitor the keystrokes of every other application using the same X session.
- a normal application can become rogue if it has a vulnerability that has not been discovered/patched yet. This is also how keyloggers get installed on other Operating Systems.

Now, you seem to say that the above is not a concern because there are no known cases of it happening in the wild. And of course you have a right to that opinion, but I think the users should be at least aware of these issues when they are assessing the security of Ubuntu/Linux.

You imply that software vulnerabilities/exploits are beyond the scope of a discussion about keyloggers, however in other OSes this is the primary method of getting a keylogger onto a system without user interaction and I think it is a valid concern here as well.

And I do need to address one of your bolded statements in particular:
> **bodhi.zazen said:**
> 
**You can not use a software key logger to monitor someone else's account without root access.**


This is not strictly true. If your account has access to the X session, it can monitor keystrokes from every other application using that X session, even if it is run as another user. For example if you run firefox as another user and it gets compromised in some way it can monitor keystrokes from every other application sharing the X session, even those run by other users.

EDIT: Also, an application with access to the X session can easily capture the password used for "sudo" if it is entered in a graphical terminal using that same X session or (apparently) in the graphical sudo prompt.

---

### Post by bodhi.zazen on 2011-05-28
Again, you are mixing possible with practical.

It is possible for 

1. A user to disable a variety of security features, including access to his or her account and access to X, and as a result, a key logger would then work across accounts as you suggest, but it does not work "out of the box" without either user intervention (to disable security) or root access (to over ride security).

```
bodhi@linux:~$ su user2
Password: 

user2@linux:~ eog

(eog:2993): EOG-WARNING **: Service registration failed.

** (eog:2993): WARNING **: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
**
GLib-GIO:ERROR:gdbusconnection.c:2270:initable_init: assertion failed: (connection->initialization_error == NULL)
Aborted (core dumped)
```

oeg is eye of gnome, an X application for viewing pictures, and as you can see, access to X is disabled. Now I can over ride that with xhost or by running as root, but "out of the box" X security does not allow the kind of access you suggest.

Second, you are talking in theory. In theory, a cracker can exploit a known or unknown application, and thus gain sufficient access to install a key logger.

It is important to understand that **No such exploit is currently known**

What do you want me to do about potential threats ? My house might get hit by an airplane. The sun might burst in a ball of flames.

In the event of a zero day exploit against firefox, on my box, firefox is confined by apparmor. So if you gain control of firefox, and run arbitrary code, such a try to install, let alone run a key logger, apparmor will stop you.

Unless of course your theoretical exploit can also defeat apparmor.

Your security advice is long in theory and paranoia, but not very good advice to new users. It basically boils down to :

There is no such thing a compete security 

with little or no advice on how to actually secure a linux box.

---

### Post by Larkspur on 2011-05-28
I think secret resistor's point is that running "xinput test" is, to all intents, a keylogger that can run without sudo.  If malware can somehow run the command and get its output (or send it home, etc.) it can get the user's passwords.  If that user runs as sudo, that malware gets root.  I haven't tested whether it can log key presses of other users, but xinput test does work for the current user.  If he's right, that's a potential security hole.

The main stumbling block for such an exploit is getting it to run.  With Apparmor running it can't add itself to bashrc or anything like that, but it can get itself elsewhere in ~/.  Still, unless it can somehow exploit config files of another program, it can't run unless the user opens it, which brings us back to user education.

---

### Post by bodhi.zazen on 2011-05-28
It is a straw man argument.

If my system is cracked, the intruder can run abc and do xyz.

In this case we are discussing key logging.

But that is what it means to have your system exploited.

See any of these vulnerabilities:

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

If a crack exploits one of those vulnerabilities and runs "arbitrary code" you are in deep trouble.

You can make up any number of "problems" or security holes at that point, from replacing .bashrc to adding any number of programs in $HOME.

Those secondary "problems" are not the security hole, the vulnerability that allows running "arbitrary code" is the security flaw that needs to be fixed. The fix depends on the exploit and can vary from limiting physical access to patching code.

In this case, xinput is the "arbitrary code". "arbitrary code" not a security hole and there is not "fix" to "arbitrary code".

Once an intruder can run "arbitrary code" the proverbial cat is out of the bag and again short of apparmor to selinux there is not much you can do to contain an intruder at that point. If they have access to an account that has root access, the intruder has root access via any number of methods.

---

### Post by secret resistor on 2011-05-28
> **bodhi.zazen said:**
> 
In the event of a zero day exploit against firefox, on my box, firefox is confined by apparmor. So if you gain control of firefox, and run arbitrary code, such a try to install, let alone run a key logger, apparmor will stop you.

Unless of course your theoretical exploit can also defeat apparmor.


Ok, what is the apparmor rule to prevent malicious library calls to XInput, without breaking the application? (keep in mind that the xinput binary is only used as a proof of concept, any application can make the library calls). I was trying to figure it out from the apparmor documentation but I didn't see anything that can do that. If you have such a rule can you post it so that I (and everybody else who is interested) can use it? Thanks.

For running as different user, what I meant is if a graphical application is allowed to run then it can snoop on the keystrokes. If it is not allowed to run (i.e. no xhost rule) or it is not graphical then you are right that there is no problem.

As for the rest, you seem to be operating under assumption that if any of the software you run gets exploited then it is game over. If that is the case then I don't think I can (or want to) argue with you.

> **Larkspur said:**
>   I haven't tested whether it can log key  presses of other users, but xinput test does work for the current user.

It can if (and only if) the user is allowed access to the X session by adding a xhost rule. This is not the case by default, which is what bodhi.zazen was getting at but if you want that user to be able to run any X application without starting a whole new X server then you need to add the xhost rule and if you do that they can query xinput for the keystrokes of any other application using the X session. So, in short if an application can use X it can snoop the keystrokes of every other application using the same X session.

---

### Post by bodhi.zazen on 2011-05-28
> **secret resistor said:**
> Ok, what is the apparmor rule to prevent malicious library calls to XInput, without breaking the application? (keep in mind that the xinput binary is only used as a proof of concept, any application can make the library calls). I was trying to figure it out from the apparmor documentation but I didn't see anything that can do that. If you have such a rule can you post it so that I (and everybody else who is interested) can use it? Thanks.

For running as different user, what I meant is if a graphical application is allowed to run then it can snoop on the keystrokes. If it is not allowed to run (i.e. no xhost rule) or it is not graphical then you are right that there is no problem.

As for the rest, you seem to be operating under assumption that if any of the software you run gets exploited then it is game over. If that is the case then I don't think I can (or want to) argue with you.



It can if (and only if) the user is allowed access to the X session by adding a xhost rule. This is not the case by default, which is what bodhi.zazen was getting at but if you want that user to be able to run any X application without starting a whole new X server then you need to add the xhost rule and if you do that they can query xinput for the keystrokes of any other application using the X session. So, in short if an application can use X it can snoop the keystrokes of every other application using the same X session.

If you want to understand apparmor , read the apparmor sticky. I have an apparmor profile for all applications that are networks aware.

If you use firefox as an example, and firefox is exploited, and if firefox is configed by apparmor, then firefox can not access bash, ~/.bashrc, xhost, or xinput unless I allow it in the apparmor profile.

So if firefox tries to run a code, say /bin/foo

Unless there is a rule in the apprmor firefox profle

/bin/foo rwix,

then apparmor will not allow firefox to run foo (or access ~/.bashrc, or run bash, or xinput, or, well you get the idea).

selinux would be a whole topic on it's own, and if you want to see what selinux will do, try fedora 15

---

### Post by secret resistor on 2011-05-28
As I said the xinput binary is only used as a proof of concept, so it is not that relevant. What you need to block is the underlying calls or requests to the X server, otherwise you are not preventing the keylogger from obtaining the information. All your examples seem to be about running new processes (correct me if I'm wrong) which is not required for an exploited application to be recording keystrokes. And if the application is already allowed to make arbitrary HTTP requests (as firefox would be) than there is nothing stopping it from reporting the keystrokes to the attacker.

Yes, I realise that this may seem a bit offtopic but I still think it is relevant to the question of how to protect against a keylogger.

---

### Post by bodhi.zazen on 2011-05-28
> **secret resistor said:**
> So, in short if an application can use X it can snoop the keystrokes of every other application using the same X session.

But that is like saying ecryptfs is a security risk because if someone knows your password they can decrypt your home directory.

There are protocols in place to secure X sessions in a multi-user environment and they have been in place for many years.

If you disable them (as a user) or circumvent them (as root) they yes, like ecryptfs, X is a security risk, but, IMO, your argument is somewhat twisted.

---

### Post by Larkspur on 2011-05-28
> **secret resistor said:**
> As I said the xinput binary is only used as a proof of concept, so it is not that relevant. What you need to block is the underlying calls or requests to the X server, otherwise you are not preventing the keylogger from obtaining the information. All your examples seem to be about running new processes (correct me if I'm wrong) which is not required for an exploited application to be recording keystrokes. And if the application is already allowed to make arbitrary HTTP requests (as firefox would be) than there is nothing stopping it from reporting the keystrokes to the attacker.

Yes, I realise that this may seem a bit offtopic but I still think it is relevant to the question of how to protect against a keylogger.

As I understand it, because the aa Firefox profile has this:

```
/usr/ r,
  /usr/** r,
```it can't run XInput. However, if the malware gets out of FF and onto the computer, it's free to do so, because it is unconstrained by Apparmor.  The problem for the malware, as I said before, is:

1) How it gets onto the computer in the first place
2) How it launches

Because aa stops it from getting to anywhere it can self-start, it would have to be extra crafty or trick the user into running it.  And that last option is the most likely, since it only depends on one vulnerability.

---

### Post by secret resistor on 2011-05-28
> **Larkspur said:**
> As I understand it, because the aa Firefox profile has this:

```
/usr/ r,
  /usr/** r,
```it can't run XInput. However, if the malware gets out of FF and onto the computer, it's free to do so, because it is unconstrained by Apparmor.  The problem for the malware, as I said before, is:

1) How it gets onto the computer in the first place
2) How it launches

Because aa stops it from getting to anywhere it can self-start, it would have to be extra crafty or trick the user into running it.  And that last option is the most likely, since it only depends on one vulnerability.

You don't need to run the xinput binary. As I said, any application can make the library call to the XInput extension (just like the xinput tool does) and obtain the keystrokes. And my question was can apparmor protect against that? And if so, what rule is needed?

EDIT: To be more clear, what I mean is if Firefox gets compromised it itself can start retrieving the keystrokes without running any other processes. Then it can report them to a web server somewhere. And the question was how to protect against that.

---

### Post by gpost3 on 2011-05-29
Alright first of all thank you all for this discussion.

Since I dropped this bomb shell , allow me to clean it up a bit.  The focus of my thread is strictly software security not physical. Let's assume hardware is safe and protected :smile:

Bodhi, your arguments make the most sense. Either way, I am a linux fan, and especially ubuntu fan and I have my reasons for it. First is my CS degree which introduced me to Linux filesystem and the use of B+ Tree as data structure which by the way I am very impressed by (due to Math not subjective arguments). 

But then again, let's continue this discussion a bit in a healthy way and as for secret, please provide code/shell script examples like bodhi is providing to illustrate your point on XInput vulnerability. We do need to be practical so that we can have something more concrete to move on with what you are saying. If your examples can show (Even as a proof of concept) that it can be done in a given time and space, then we can discuss that further. Let's avoid hypothetical extreme arguments as bodhi pointed out using the plane example. Those will get us no where. Give us any type of mini example where the root access is not required to gain control and capture XInput. You may provide shell script, code (C++) or anything that is workable and then we will work together and analyze your code/example. This way, we can also gauge whether your talk has some skills to back it up or not. Sorry if this sounds hard to you but since we are on the internet forum, this is sort of necessary to keep the linux/ubuntu haters down (and no I am not saying that you are one).

P.S: Completely off topic, I wish to volunteer to help code small parts of ubuntu. I can invest 4-5 hours on a weekly basis. How do I volunteer with Canonical or Ubuntu team?

---

### Post by secret resistor on 2011-05-29
Easiest method, using the xinput binary and without the key code to ascii conversion:
1. Run "xinput list" and look for something like "AT keyboard" and note it's id
2. Run "xinput test <id>" where <id> is the the id found in step 1.
3. Watch the events as you type anywhere (including sudo passwords or in apps running as root)

There is a perl script that automates this and converts the keycodes to ascii characters. I can post a link to it but I don't know if I'm allowed to do that on this forum.

I could also write a standalone C program that does the same, so no xinput binary is required but I don't see the point. If you want to know how it works just look at the xinput code.

P.S. I'm not a Linux/Ubuntu hater and I'm sorry if I've implied that in any way. I've been using Linux for over a decade and I do agree that overall it is more secure than Windows, just not when it comes the separation between processes using XWindows, which is the whole issue being discussed here. BTW, this is not really a Linux (as in Linux the kernel) problem but an XWindows one.

---

### Post by bodhi.zazen on 2011-05-29
Well, we would discourage such proof of concept discussions / posting of code here.

If you are interested in security take a look at apparmor and/or selinux ;)

---

### Post by Lars Noodén on 2011-05-29
> **bodhi.zazen said:**
> Well, we would discourage such proof of concept discussions / posting of code here.

If you are interested in security take a look at apparmor and/or selinux ;)

Ok.  Thanks. I guess it's time to learn AppArmor.  Does it use systrace?

---

### Post by JKyleOKC on 2011-05-29
I just ran the xinput POC and here's my result: ```
jk@mehitabel:~$ xinput test 8
key release 36 
key press   46 
lkey release 46 
key press   39 
skey release 39 
key press   37 
key press   54 
^C

```The "8" was the ID of my keyboard; the 36 was release of the Enter key at the end of the "xinput" command. My typed input was "ls" and there's no obvious correlation to keys 45 and 39, although I suppose if the hypothetical intruder also had my keycode translation table he could figure it out. I'm not certain what the 37 refers to; I hit ctrl-C to interrupt the program so presumably the 37 and 54 are those two keys.

Bottom line: **if** the intruder has gained access by some other vulnerability, **and** knows my keycode translation (e.g. if I were using dvorak or some non-standard keyboard), then it's possible. However the risk is, IMO, vanishingly small.

Edit: just noticed that the key correlation is shown in the first character of each "release" line, for the two typed letter keys, so xinput does use the translation table. However it's still a vanishingly small risk IMO...

---

### Post by secret resistor on 2011-05-29
> **JKyleOKC said:**
> I just ran the xinput POC and here's my result: ```
jk@mehitabel:~$ xinput test 8
key release 36 
key press   46 
lkey release 46 
key press   39 
skey release 39 
key press   37 
key press   54 
^C

```The "8" was the ID of my keyboard; the 36 was release of the Enter key at the end of the "xinput" command. My typed input was "ls" and there's no obvious correlation to keys 45 and 39, although I suppose if the hypothetical intruder also had my keycode translation table he could figure it out. I'm not certain what the 37 refers to; I hit ctrl-C to interrupt the program so presumably the 37 and 54 are those two keys.

Bottom line: **if** the intruder has gained access by some other vulnerability, **and** knows my keycode translation (e.g. if I were using dvorak or some non-standard keyboard), then it's possible. However the risk is, IMO, vanishingly small.

Edit: just noticed that the key correlation is shown in the first character of each "release" line, for the two typed letter keys, so xinput does use the translation table. However it's still a vanishingly small risk IMO...

What you see at the beginning of each release line is just the local echo of the terminal (since you are typing in the same terminal you are using to start xinput). The attacker would not see this of course but the translation is always the same so it is trivial to figure out from the keycodes. Here is the mapping for the characters you typed:

36 = Enter
46 = l
39 = s
37 = ctrl
54 = c

This is always the same on every qwerty keyboard.  For the full mapping you can google for the perl script since I'm not allowed to post it. 

Yes, it would be different for dvorak but it should still be the same in every case and it would be trivial to figure out whether it is qwerty or dvorak based on which translation produces valid words.

The **only** thing the attacker needs is access to a vulnerability, whether the chance of that is "vanishingly small" is a matter of opinion as has become clear in this thread.

---

### Post by Lars Noodén on 2011-05-29
> **secret resistor said:**
> 
The **only** thing the attacker needs is access to a vulnerability.

That's where Flash comes in ...  :(

---

### Post by secret resistor on 2011-05-29
> **Lars Noodén said:**
> That's where Flash comes in ...  :(

Yes, good point. Our example here has been Firefox but historically Flash has been a much bigger problem. Also, considering that the main thing the bad guys are after is banking information and credit cards, if they compromise your browser they can probably figure this out without a keylogger. If they compromise flash though (or any other software ridden with security holes) then turning it into a keylogger would be the primary concern.

As for protection: after some more thinking I realized that blocking the library calls does not in fact solve the problem, although it makes exploitation quite a bit more difficult. The compromised application can just use its socket to the X server (or open a new one) to ask for the keystroke events. So, I think the only real way to protect against this would require tight integration with the X server so that applications that do not have focus cannot receive such events. 

From what I have read about AppArmor it seems that it can neither block the library calls nor is it integrated with the XWindows enough to solve the problem. So, I don't see how AppArmor can do anything here besides making it more difficult to make the keylogger permanent (as already discussed). But I would love to be proven wrong on this, so if there are any AppArmor gurus here please correct me. 

SELinux does seem to be integrated with XWindows enough to do the job but that is just based on skimming over the documentation / examples so I'm not sure yet if and how exactly it can be used to address this. I will try it when I have some more time and post the results but if somebody more experienced in SELinux wants to help, please feel free to do that.

---

### Post by secret resistor on 2011-05-29
I somehow missed that:
> **bodhi.zazen said:**
> But that is like saying ecryptfs is a security risk because if someone knows your password they can decrypt your home directory.

There are protocols in place to secure X sessions in a multi-user environment and they have been in place for many years.

If you disable them (as a user) or circumvent them (as root) they yes, like ecryptfs, X is a security risk, but, IMO, your argument is somewhat twisted.

The point is that the protocols that "secure X sessions in a multi-user environment" simply say who can have access to the session and who doesn't and everybody who does can do as they please. Which is why if you can run an X application in a given session you can snoop on the keystrokes from any other application regardless of the user running it. This type of all-or-nothing access controls is precisely the main problem being discussed here. 

And I don't think the analogy to ecryptfs makes sense since with an encrypted file system you only give the key to the kernel and it will still enforce proper access controls for the non-root users. You don't **need** to give a potentially malicious application the key in order for it to access some files.

Also with regards to this:
> **bodhi.zazen said:**
> Well, we would discourage such proof of concept discussions / posting of code here.

I can't say I agree with this since first you complain about me being "theoretical" and "paranoid" but then you object to me posting practical code. But it does say "forums admin" on your uniform :), so I will respect that request with regards to posting actual code.

---

### Post by Larkspur on 2011-05-29
I was searching around to shore up my lack of knowledge on this.  There's been a bit of discussion in the wake of  "Linux GUI Security Circus," but little in the way of answers.  I suppose the fact that attacks using xinput haven't been heard of is enough to not worry at the moment;  as you and bodhi.hazen suggest, the vulnerability that allows xinput to be run maliciously has to come first.  

> **secret resistor said:**
> I can't say I agree with this since first you complain about me being "theoretical" and "paranoid" but then you object to me posting practical code. But it does say "forums admin" on your uniform :), so I will respect that request with regards to posting actual code.

Maybe you should file a bug on Launchpad explaining the potential risk, and see what the Ubuntu Security Team have to say.  If you do, could you let everyone know what happens?

---

### Post by secret resistor on 2011-05-29
Yes, that blog post should probably be credited since it sparked the discussion. However, the problem is **not** confined to the XInput extension. I found two different pieces of code for a proof of concept XWindows keylogger, one using XQueryKeymap and another using XNextEvent to achieve the exact the same thing - receiving the keystrokes of any application using the same X session.

So, I think this isn't so much about XInput but rather going back to the root problem which is that XWindows, unlike the Linux kernel, is simply not designed to protect applications from each other. This apparently has been known for many years but I guess it's one of these things nobody wants to talk about, as somebody else already said in this thread. And again, it appears that SELinux has tried to address this but I am unsure of how successful it is and how practical it is to use it.

---

### Post by gpost3 on 2011-05-30
> Well, we would discourage such proof of concept discussions / posting of code here.I agree with secret, we don't admire this comment. The proof of concept is already provided by secret. I can write the C++ code and simply run those commands in a binary executable for linux but our point here is to learn and "also" help improve Ubuntu (not destroy it) - as it is very clear non of us is ubuntu hater. Discouraging us to post the relevant code will not stop the immediate threats that a potential hacker will place upon us but infact it will create awareness for users to better understand the XWindows issue and protect themselves. Bad guy doesn't need ubuntu forum's admin permission to cause harm which is why he/she is bad to begin with. Ofcourse bodhi this does not void about what you said - to have strong password and use encryption for sensitive data, that still stands true and we thank you for it. 

> converts the keycodes to ascii characters. I can post a link to it but I don't know if I'm allowed to do that on this forum.And that is very simple to do. One of my CS textbook has full chart for hex/dec/asc conversion table. :/ Regardless you don't even need that. 38 is the selstart for A. You can do a dynamic cast from (int *) to (char *) and get the asc code. As for lower cases, well 50 is the keystroke for shift. Very obvious that any key following 50 is actually in upper case whereas otherwise it is lower case.

As far as this type of vulnerability is concerned. You shouldn't really need apparmor or SELinux but a new iteration of XWindows. The idea is simple, only currently active/focused window should have access to key strokes. It just needs a simple branch condition to fix that in the composite design pattern (which is what is normally used in HCI - so I am quite sure XWindow has similar technique employed). I could write that patch for XWindows if I were a part of that team.

Having said that, even a hardware based keyboard encryptor won't work because the encrypted information would need to be decrypted at input service handler/interrupt (at the driver level) which makes the information available to all applications. The fix has to be made in XWindows. Someone should file this as a bug to Ubuntu/Canonical bulletin. I would like to see this addressed in next iteration. As for sysadmins who need this type of vulnerability, alternative downloads should be made available to them.

This thread made for a good healthy discussion. Thank you all. Ofcourse feel free to continue commenting.

---

### Post by spynappels on 2011-05-30
> **gpost3 said:**
> I agree with secret, we don't admire this comment. The proof of concept is already provided by secret. I can write the C++ code and simply run those commands in a binary executable for linux but our point here is to learn and "also" help improve Ubuntu (not destroy it) - as it is very clear non of us is ubuntu hater. Discouraging us to post the relevant code will not stop the immediate threats that a potential hacker will place upon us but infact it will create awareness for users to better understand the XWindows issue and protect themselves. Bad guy doesn't need ubuntu forum's admin permission to cause harm which is why he/she is bad to begin with. Ofcourse bodhi this does not void about what you said - to have strong password and use encryption for sensitive data, that still stands true and we thank you for it. 


The reason it is discouraged is that this forum is visited by people with a whole range of abilities and motivations and is primarily a support forum. Anything which has the potential to cause problems when people who are not completely au-fait with what they are doing attempt to use the code is not permitted, along the same lines as why it is not permitted to post how to delete your /usr directory. 
Technical discussions like this may be more suited to Launchpad, where closer co-operation with developers can be achieved if necessary.

---

### Post by Soul-Sing on 2011-05-30
> **spynappels said:**
> The reason it is discouraged is that this forum is visited by people with a whole range of abilities and motivations and is primarily a support forum. Anything which has the potential to cause problems when people who are not completely au-fait with what they are doing attempt to use the code is not permitted, along the same lines as why it is not permitted to post how to delete your /usr directory. 
Technical discussions like this may be more suited to Launchpad, where closer co-operation with developers can be achieved if necessary.

No, then you have to narrow the security subforum title. Sorry.
: Security Discussions:
"Discuss security flaws/updates/notices in the various Ubuntu releases."
So rather academic discussions are allowed and even encouraged.
This forum is visited by people with different "agenda's".No one can actively monitor these different agenda's.
Maybe restricting the subforum title is an option.

---

### Post by spynappels on 2011-05-30
> **leoquant said:**
> No, then you have to narrow the security subforum title. Sorry.
: Security Discussions:
"Discuss security flaws/updates/notices in the various Ubuntu releases."
So rather academic discussions are allowed and even encouraged.
This forum is visited by people with different "agenda's".No one can actively monitor these different agenda's.
Maybe restricting the subforum title is an option.

Ok, I see where you are coming from, but the umbrella for this section of the forums is "Main Support Categories". Perhaps another subforum under "Other Community Discussions" would be a better place for discussions of this nature.

Note: I am not against these academic discussions, I feel they are very valuable, but they could simply cloud the issues in what is primarily a Support section of the Ubuntu Forums.

---

### Post by gpost3 on 2011-05-30
> So rather academic discussions are allowed and even encouraged.Indeed and our domain for this thread is specifically Professional Practice in Computer Science.

> Anything which has the potential to cause problems when people who are  not completely au-fait with what they are doing attempt to use the code  is not permittedThis argument is a bit twisted on the extreme end of the spectrum. Grocery stores still sell table knifes and that too can be misused by people with various abilities and motivations however that doesn't mean we despair 99% of the population who just want to cut their apples and oranges.

> Note: I am not against these academic discussions, I feel they are very  valuable, but they could simply cloud the issues in what is primarily a  Support section of the Ubuntu Forums.This makes sense. Perhaps we are too academic and this isn't the place to do it. I have created a section for this in launchpad and now I believe it is the right time to close this thread. Thank you everyone for your input and for being patient. I launched this thread, everyone commented (thank you) and now I am requesting it to be marked as closed.

Special thanks to spynapples, bodhi and secret.

---

### Post by spynappels on 2011-05-30
> **gpost3 said:**
> Indeed and not only are we discussing academia in a Computer Science context, we are also being very professional.



This argument is a bit twisted on the extreme end of the spectrum. Home hardware store still sells utility knifes and that too can be misused by people with various abilities and motivations however that doesn't mean we despair 99% of the population who just want to cut their apples and oranges.

I was not questioning anyone's professionalism, but the point still stands that this is primarily a support forum and it is hardly twisted to try and eliminate information which may alarm new users unecessarily or possibly cause problems if they execute code which they don't understand. There is absolutely a place for academic discussion, I'm simply not sure that a support forum is that place.

Edit: crossover post, good discussion all the same.

---

### Post by gpost3 on 2011-05-30
> There is absolutely a place for academic discussion, I'm simply not sure that a support forum is that place.And I agree with you - this isn't the place for deep academic discussion. This thread should now be closed.
Cheers.

---

### Post by Soul-Sing on 2011-05-30
> Note: I am not against these academic discussions, I feel they are very valuable, but they could simply cloud the issues in what is primarily a Support section of the Ubuntu Forums.

The outcome of security discussions are often open-ended.
Imho security discussions are meaningful of they start with a beginning a discussion part, and a rational outcome, or conclusion.
Thats the support part of an important subforum imho. I recently discoverd the discussion part of this subforum.
Why discuss security related things without the prospect of*a*conclusion? (endless debats) I find the content very frequently confusing. Security related matters needs support, keep each other informed.
Security related questions do need clarity, security related questions are not as ambiguous as they sometimes seems.

---

### Post by bodhi.zazen on 2011-05-30
Discussing a vulnerability is acceptable, writing proof of concept code is not.

I agree it is a fine line, but the conversation in this thread turned from discussing theoretical issues to lets write the code.

It is the process of writing potentially malicious code the we do not allow.

Much of the discussion in this thread is highly theoretical and most of the discussion is the consequence of having your machine cracked.

If an intruder has access to your box, including physical, shell, or graphical (X) access your are in trouble and honestly there is not much you can do.

With that said, Linux (Unix) has a long history of being multi-user and there are in fact security mechanisms in place, as I demonstrated earlier.

If you wish, you can harden your installation by using apparmor or selinux.

So yes on these forums we support learning apparmor, but not posting / writing malicious code.

---

### Post by Larkspur on 2011-05-30
> **gpost3 said:**
> I have created a section for this in launchpad . . .

Could you give a link to it?  I imagine it's still private, but I think the Ubuntu Security team try to look at security bugs within 24 hours.

---

### Post by secret resistor on 2011-05-30
Ok, fair enough and thank you all for the useful discussion.

To provide a short summary of the outcome of this thread:

1. XWindows does not implement isolation between applications using the same X session and therefore an application with access to the session can monitor keystrokes of any other application using the same X session (regardless of user running the application, **as long as access to the X session is given**)
2. This is only a concern if any XWindows software you run is compromised or malicious to begin with. If the software you run is not vulnerable and not malicious this **cannot** be exploited since it needs "a way in".
3. AppArmor can reduce the impact by making it more difficult to install the keylogger permanently, however it cannot prevent an application from receiving keystrokes, to the best of my knowledge (so the vulnerable/malicious application could still act as a keylogger itself and if it is allowed access to the internet it can report the keystrokes somewhere).
4. SELinux appears to address the issue, however the XSElinux extensions are not loaded by default even if you run SELinux and it unclear whether they are production quality and whether they interfere with regular applications or not. Note: simply installing the SELinux packages does **not** change anything.
5. Ideally, as was already mentioned, the problem should be fixed in XWindows rather than trying to rely on AppArmor or SELinux.

I think this is about it. If there is anything factually incorrect there please let me know and I will edit it.

---

### Post by Dry Lips on 2011-05-31
> **Lars Noodén said:**
> Less than that is needed.  Every flash video is basically a potential trojan wrapped around an otherwise harmless video codec.  Similar for the flash animation.  Videos could more safely and more portably be distributed as a bare bones MPEG, Quicktime, WebM or Theora and skip the flash menace.

I'm interested in the subject and I wonder whether you could 
elaborate a little on this. Would flash-scripts for instance install
 themselves to the HDD, or are their action only restricted to the
 moment? Do you have any resources about this that you 
would recommend?

---

### Post by secret resistor on 2011-06-01
Launchpad entry: [https://answers.launchpad.net/ubuntu/+source/xorg/+question/159596](https://answers.launchpad.net/ubuntu/+source/xorg/+question/159596)

---

### Post by gpost3 on 2011-06-06
oh and this thread should be "closed down". Bodhi is correct on all accounts. The ideas here are merely theoretical and actually have no practical implications. Go nuts at it, use ubuntu. It's safe!

---

### Post by softappstudio on 2011-07-18
> **gpost3 said:**
> oh and this thread should be "closed down". Bodhi is correct on all accounts. The ideas here are merely theoretical and actually have no practical implications. Go nuts at it, use ubuntu. It's safe!
I'm not sure it is so theoretical, my wife's Ubuntu-lucid box just got "keystroke grabbed" while using Firefox and hotmail --  the user interface was frozen keyboard-wise and we got a pop-up watrning that it was being grabbed. So, being pretty wet behind the ears (!), I do need to be told how to prevent this in future. 

[1] I have installed the clamav pkg, will this help? 
[2] Should I get the thing called apparmor?  
[3] Should I put a separate "admin" A/C on the box, and deny her some capabilities?
[4] Is "SELinux" something I can put on Ubuntu?

Explicit answers to any/all of the above will surely be gratefully appreciated.
--Grahame

---

### Post by bodhi.zazen on 2011-07-18
> **softappstudio said:**
> I'm not sure it is so theoretical, my wife's Ubuntu-lucid box just got "keystroke grabbed" while using Firefox and hotmail --  the user interface was frozen keyboard-wise and we got a pop-up watrning that it was being grabbed. So, being pretty wet behind the ears (!), I do need to be told how to prevent this in future. 

[1] I have installed the clamav pkg, will this help? 
[2] Should I get the thing called apparmor?  
[3] Should I put a separate "admin" A/C on the box, and deny her some capabilities?
[4] Is "SELinux" something I can put on Ubuntu?

Explicit answers to any/all of the above will surely be gratefully appreciated.
--Grahame

You should start your own thread with this question. Sounds more like the desktop sharing feature then a key logger, but hard to be sure without additional details.

---

### Post by 19Grumpah42 on 2011-07-18
> **bodhi.zazen said:**
> You should start your own thread with this question. Sounds more like the desktop sharing feature then a key logger, but hard to be sure without additional details.
Thanks for the reply bodi. Yes I can start a new thread, but to help others I would be grateful if you could advise me what "additional details" would be important, and where they are/ how to get them.
--Grahame

---

### Post by mmm4m5m on 2011-11-27
> **gpost3 said:**
> oh and this thread should be "closed down". Bodhi is correct on all accounts. The ideas here are merely theoretical and actually have no practical implications...

I see it other way around: as long Adobe Flash player is closed source and widely used, it is _not_ a theoretical... (How many people advice - "do not install Adobe Flash player"?)

I could have userTrust for 'private/bank/credit cards' things. I could adjust home dir permissions - not readable for others.
Then, I could have another user - userBad. As userBad I could run Firefox with Adobe Flash plugin  - adobe flash installed/enabled _only_ for userBad.
And the fun stops there - adobe flash have access to do key logging. Yes, it is me who install Adobe Flash and give permissions to X server.

Then I found, I could run Firefox+Adobe Flash in second (nested) X server (Xephyr), but in that case GLX does not work - performance is like if I remove/uninstall Adobe Flash.

For me, it is a security problem. I can understand if one X application/window can see all running X applications/windows (like to see the list of files)...
But ability to intercept the data designated for another X application/window (like to see the content of file/doc) - I do think it is not OK.

regards.

(note: I did try to read all old posts... sorry if I missed the point)

---

