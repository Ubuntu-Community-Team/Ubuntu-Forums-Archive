---
title: "Question about &quot;rm&quot; command"
date: 2011-11-10
forum: Security
---

### Post by asturbal on 2011-11-10
If the Ubuntu runs dangerous commands like that, doesn't mean that ubuntu is easily corrupted, more easily that Windows or other operational system?

---

### Post by haqking on 2011-11-10
see [http://ubuntuforums.org/announcement.php?f=48](http://ubuntuforums.org/announcement.php?f=48)

3rd post down from Jdong

---

### Post by nothingspecial on 2011-11-10
You don't need to post a whole collection of them.

To answer your question, linux doesn't stop you breaking your system because you might want to. And that's up to you :P

---

### Post by asturbal on 2011-11-10
Sorry, I didn't know that to post this command is forbidden, but why they dont block this commands? or just pick a bunch of commands that breaks the system and put a advice that they will ruin the system if executed? like:

user@pc:~$<dangerous command>
Run this command will ruin your system, do you really want to execute it any way?(Y/N)

---

### Post by nothingspecial on 2011-11-10
> **asturbal said:**
> Sorry, I didn't know that to post this command is forbidden, but why they dont block this commands? or just pick a bunch of commands that breaks the system and put a advice that they will ruin the system if executed?

Because I might want to ruin my system or do anything I want to with my system. Stopping people doing what they like is not the way linux works.

---

### Post by haqking on 2011-11-10
> **asturbal said:**
> Sorry, I didn't know that to post this command is forbidden, but why they dont block this commands? or just pick a bunch of commands that breaks the system and put a advice that they will ruin the system if executed?

to use SUDO assumes responsibility for your system, if commands were disabled you couldnt administer your system.

If you use SUDO then linux assumes you know what you are doing, if you dont know what a command does then dont run it.

If you are in the habit of running commands without knowing what they will do then somewhere along the line you will trash your system anyway

---

### Post by tubbygweilo on 2011-11-10
Commands are not bad per se it is often down to users malicious or not that can give a command a bad name.

---

### Post by asturbal on 2011-11-10
I didn't meant to block the command, i think that just to put a message that this command will ruin your system and give the choice cancel the action will solve the problem. In some way, anyone that is new on linux can be fooled by anyone with the minimum knowledge of pyton script.

Most of times, they don't put this command with "sudo" in a terminal, they just execute a .deb file or a .py script, then insert the password in the message dialog and BAM!

---

### Post by nothingspecial on 2011-11-10
You can do that yourself with aliases eg

```
alias rm='rm -i'
```

---

### Post by satanselbow on 2011-11-10
Linux working as a community as it does - bomb scripts usually get flagged as such and pulled pretty sharpish. Most recently for example - damaging code uploaded to gnome-look.

You are correct, however, that there is always the potential for an unskilled/unexperienced user to fall prey to a malicious helping hand before a mod/admin could intervene.

The admins here work tirelessly to ensure all posts that involve the use of code and scripts are not malicious or likely to cause more harm than good.

Do I check every line of code that I download? No I don't - because I have a reasonable serving of commonsense and trust in the community, it's repos and humanity of others.

In answer to your original question - and for the very same reasons - no this does not make linux any less secure than windows... and I never thought I might have reason to type that :P

---

### Post by CharlesA on 2011-11-10
> **nothingspecial said:**
> You can do that yourself with aliases eg

```
alias rm='rm -i'
```
+1.

I saw this in someone's sig:

"Linux assumes you know what you are doing."

Oh, that was actually, nothingspecial's sig. :lol:

---

### Post by OpSecShellshock on 2011-11-10
Well , I know everyone is keeping good, recent backups, right? So really running the wrong command early on, while not good, isn't *so* costly. All downloading and re-installing the OS costs you is the time it takes, and you may have a net gain in lessons learned. Not that I would suggest running any old command with abandon, obviously.

---

### Post by CharlesA on 2011-11-10
> **OpSecShellshock said:**
> Well , I know everyone is keeping good, recent backups, right? So really running the wrong command early on, while not good, isn't *so* costly. All downloading and re-installing the OS costs you is the time it takes, and you may have a net gain in lessons learned. Not that I would suggest running any old command with abandon, obviously.

Huge +1 to backups.

I do daily backups cuz I am paranoid (and I don't like losing data!)

---

### Post by asturbal on 2011-11-10
Ok, but you all dodge the main reason....
Why the linux don't advise when some program, script, .deb, .ram, command line, etc. tries to execute a malicious command?

It will be so simple and will make the linux bullet proof (in this case, noob pro of).

I think that it is not so dificult to make something like that. A easy way to make linux more safe!
And finaly makes all the discursions about safety in operational systems less agressive (at least the comand "blablabla -rf /" will not be the greatest argument!).

---

### Post by CharlesA on 2011-11-10
> **asturbal said:**
> Ok, but you all dodge the main reason....
Why the linux don't advise when some program, script, .deb, .ram, command line, etc. tries to execute a malicious command?

It will be so simple and will make the linux bullet proof (in this case, noob pro of).

I think that it is not so dificult to make something like that. A easy way to make linux more safe!
And finaly makes all the discursions about safety in operational systems less agressive (at least the comand "blablabla -rf /" will not be the greatest argument!).

Only install stuff from trusted sources. If something is questionable, examine the source and decide if it's worth the risk to run it or not.

If you run something on a *nix box, it is assuming you know what you are doing. You won't run into any sort of malicious files if you stick to the repos.

---

### Post by haqking on 2011-11-11
> **asturbal said:**
> Ok, but you all dodge the main reason....
Why the linux don't advise when some program, script, .deb, .ram, command line, etc. tries to execute a malicious command?

It will be so simple and will make the linux bullet proof (in this case, noob pro of).

I think that it is not so dificult to make something like that. A easy way to make linux more safe!
And finaly makes all the discursions about safety in operational systems less agressive (at least the comand "blablabla -rf /" will not be the greatest argument!).

Because then people would complain about the annoying messages every 2 seconds.

Plugging in a USB device is potentially unsafe, allowing a script in a Browser is potentially unsafe, installing software is potentially unsafe, doing any action as sudo is potentially unsafe (**hence the warning the first time you ever run sudo, which by the way covers the warning for sudo actions including your commands**).  Everytime you connect to the internet it is potentially unsafe.

Warning messages would never end, and i am sure devs would prefer people took the time to figure out how to use Linux than they develop warning messages for every potentially malicious action.

Cheers

---

### Post by FuturePilot on 2011-11-11
> **nothingspecial said:**
> You can do that yourself with aliases eg

```
alias rm='rm -i'
```

The only problem is that when you use sudo to rm something you won't get that prompt because that is your personal alias, not root's.

---

### Post by Thewhistlingwind on 2011-11-11
> **asturbal said:**
> Ok, but you all dodge the main reason....
Why the linux don't advise when some program, script, .deb, .ram, command line, etc. tries to execute a malicious command?

It will be so simple and will make the linux bullet proof (in this case, noob pro of).

I think that it is not so dificult to make something like that. A easy way to make linux more safe!
And finaly makes all the discursions about safety in operational systems less agressive (at least the comand "blablabla -rf /" will not be the greatest argument!).

By the point that you (As an attacker) can execute sudo rm -rf ANYTHING, there are much worse problems in the install, AND the box has been owned.

---

