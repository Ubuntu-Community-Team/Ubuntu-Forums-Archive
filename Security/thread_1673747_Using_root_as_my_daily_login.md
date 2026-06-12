---
title: "Using root as my daily login"
date: 2011-01-22
forum: Security
---

### Post by UncleBoarder on 2011-01-22
I know... I KNOW... don't do it.  What I don't know is why.  Before you rant, let me explain my question.

It's my personal computer, no other users, no one else in the house.  I'm behind a separate stand alone firewall (Checkpoint device).  I'm the admin on my machine and I'm going to enter sudo, or login as root, every time I need it anyway.

There's no way that having to switch to root is going to make me stop and think about what I'm getting ready to do.  In fact it's quite the opposite.  If I'm in the midst of troubleshooting, I'm preparing to enter a command that I think is going to work, and I get "Permission denied"...  The aggravation is more likely to reduce my logical thinking, and I'll immediately switch to root and type it anyway.

I DO understand the rational of setting users (even admin users) to a lower permission level.  However I don't understand the lack of a command to make a user PERMANENTLY root equivilent.

Switching back and forth is a waste of time.  AND it means that I now have to deal with two home directories... /root and /home/user.

Having to type sudo, or su to switch to root, does not protect my system.  It only aggravates.  Ok, I'm ready.  Hit me.  :-)

---

### Post by Bitrate on 2011-01-22
So you want to run your Ubuntu desktop like an insecure Windows XP machine ?

Go ahead then, nobody will stop you but be prepared for disaster if you inadvertently delete a critical system file or your system is compromised by specific malware. Keep good backups and you should be ok.

---

### Post by yetiman64 on 2011-01-22
> **UncleBoarder said:**
> I know... I KNOW... don't do it.  What I don't know is why.  Before you rant, let me explain my question.

It's my personal computer, no other users, no one else in the house.  I'm behind a separate stand alone firewall (Checkpoint device).  I'm the admin on my machine and I'm going to enter sudo, or login as root, every time I need it anyway.

There's no way that having to switch to root is going to make me stop and think about what I'm getting ready to do.  In fact it's quite the opposite.  If I'm in the midst of troubleshooting, I'm preparing to enter a command that I think is going to work, and I get "Permission denied"...  The aggravation is more likely to reduce my logical thinking, and I'll immediately switch to root and type it anyway.

I DO understand the rational of setting users (even admin users) to a lower permission level.  However I don't understand the lack of a command to make a user PERMANENTLY root equivilent.

Switching back and forth is a waste of time.  AND it means that I now have to deal with two home directories... /root and /home/user.

**Having to type sudo, or su to switch to root, does not protect my system**.  It only aggravates.  Ok, I'm ready.  Hit me.  :-)

The bolded is clearly wrong, enforcing ownership and permissions is what protects your system from viruses and malware. 

Read the link #4 "RootSudo" in my sig,. It will explain the use of sudo.

Please note this site supports the Canonical security model, which you are undoing on your machine if you enable a root account, and it is against the forum rules to post instructions for what you want.

Please see here: [http://ubuntuforums.org/showthread.php?t=885580](http://ubuntuforums.org/showthread.php?t=885580)  Don't # 12.

---

### Post by Quackers on 2011-01-22
As the sole user of my laptop I quite agree with the OP here. I'm a big boy, and I'll live and die by my mistakes. I should be allowed to do that imo.
I find it quite ludicrous that to open synaptic, with the intention of checking for updates, I have to enter my password. I could understand needing to enter my password to install something, or to remove something, but just to check for updates? No. 
There are commands that can be used on a per-session basis to circumnavigate this problem and there is visudo which can be edited. Not sure how much more I can say, without breaking forum etiquette :wink:

---

### Post by tigerstripedcat on 2011-01-22
It's really not that much of a hassle. Learn these commands to make things easier.

If you forgot to put sudo do this:

1) up arrow
2) ctrl+a (to go to the beginning of the command line)
3) type "sudo"
4) <enter>

I think you might be right to a point, there is not really any malware for linux, but the problem is that you want to allow certain programs to have access privledges, not just users.  So going around as root and modifying things just means that ever single user on your computer will need elevated access privledges to do anything. 

There is a reason that ubuntu hasn't developed an always-on adminstration, and why windows developed a UAC.  I just trust in those who know a lot more about access control than I do and keep to my six keystrokes.

---

### Post by Vaphell on 2011-01-22
> As the sole user of my laptop I quite agree with the OP here. I'm a big boy, and I'll live and die by my mistakes. I should be allowed to do that imo.

no problem, you are allowed to do that - it's linux after all - but in such case you should be able to find the instructions and follow them on your own. Spreading such information freely on this forum would cause an untold amount of grief. Ubuntu is a newcomer's distro of choice.
Newly converted xp users would simply love the idea that they can run everything without those pesky permissions and passwords just like in a good ol' windows.
Everyday there are dozens of threads of inexperienced users who totally hosed their system trying to shave like 20 secs/day, imagine how many of such threads would be there if the instructions were trivial to obtain for an avarage newbie.
Besides how often after the initial setup do you need to sudo anything? i type password maybe twice a day tops. I will gladly sacrifice those 5 seconds to avoid the hassle of system reinstallation in case my fingers slip and i use the shift-del combo in the wrong place.

> 
1) up arrow
2) ctrl+a (to go to the beginning of the command line)
3) type "sudo"
4) <enter>


even better
1. run a command that fails
2. sudo !! (!! stands for last command)
3. ???
4. profit

---

### Post by Quackers on 2011-01-22
Lol, I did, and I have :-) 
I enter my password more than twice a day just checking for updates! Updates which may not even exist! But I am using Natty (in which my visudo changes don't work - very irksome :-) )

---

### Post by tigerstripedcat on 2011-01-22
> **Vaphell said:**
> 
even better
1. run a command that fails
2. sudo !! (!! stands for last command)
3. ???
4. profit


Nice! I didn't know that.  Better yet, just create an alias for 'sudo !!'

1. sa <enter>
2. ???
3. ???
4. profit

---

### Post by djeikyb on 2011-01-22
Searching the internets for "how to enable root on ubuntu" would have taken you less time than posting here.

Personally, I find there are times when logging on as root for a long series of administrative tasks to be incredibly useful. But using it as a normal user account is stupid.

**Scenario:** You're browsing the web when suddenly a website exploits an unpatched bug in firefox and executes malicious code on your computer. Suuucks to be you, because you're running as root, and now some evil stranger has hooks into your computer. You've probably been conscripted into a botnet, and you'll have trouble explaining to your wife why hardcore porn inexplicably pops up. **The rest of us** get attacked, but the damage is limited to our home folders. Our system isn't pwned because the malicious code didn't have the permissions it needed to do system damage.

---

### Post by Ocxic on 2011-01-22
Using root as your daily login, is like saying "I'm the only one who lives in my house, why bother putting locks on the doors."

---

### Post by Quackers on 2011-01-22
> **Ocxic said:**
> Using root as your daily login, is like saying "I'm the only one who lives in my house, why bother putting locks on the doors."

Lol, do you have to enter a password to get through your internal doors?

---

### Post by hawkmage on 2011-01-22
Personally I don't login as root.  Since I do server administration so using sudo comes naturally.  

On a personal system I agree that it is up to you how you log into your machine but there are many reasons not to that have been mentioned over and over.  To me the biggest reason not to log in as root is not the possible loss of data or time to rebuild but that by running with elevated privileges makes the system less secure and the systems that are out there that are insecure the more likely Linux as a platform will become a target for malware.

---

### Post by amsterdamharu on 2011-01-22
If it's wrong to log in a root or not is not as importaint as the forum policy stating that such information is not allowed to be given here.

Even if I agree with the op the forum policy prevents me from posting the answer so to the op; this is the wrong place to ask.

I have had nautilus scripts that require sudo and because it's executed by nautilus it'll never ask me for a password and would fail. The solution to that is the command visudo that edits the sudoers and allows you to set certain commands (or all commands) to be executed for certain users (or all users) without asking for a password.

---

### Post by slooksterpsv on 2011-01-22
> **Quackers said:**
> Lol, do you have to enter a password to get through your internal doors?

No but you do have to use the door knob to twist open the door (like typing a password for sudo). Why not just take all the doors off of your house, then you won't need a key to get in, or doors for privacy for your bedroom, bathroom, etc.

The reason it's bad to run as root is, what if you're in the terminal and you write a command that you accidentially typed in something wrong, but it would still execute and do major damage?

What if a site tried to hook into your system, and ran a script to do xyz?

What if you clicked on a folder by accident, and it dragged what you clicked to wherever, and you couldn't move it back cause it was a system folder that had commands to do so in it?

What if someone cracked your home network, cracked your root user cause they tried that, and started doing a key-log of everything you type and you log into your bank and check your bank stuff or use your credit card or this or that?

There's probably others, but I can't think right now...

---

### Post by hawkmage on 2011-01-22
> **Quackers said:**
> Lol, I did, and I have :-) 
I enter my password more than twice a day just checking for updates! Updates which may not even exist! But I am using Natty (in which my visudo changes don't work - very irksome :-) )
That is odd, every personal Linux box I have I add a group called "sudoallnp", add my account to the group. and add the line "%sudoallnp ALL=NOPASSWD: ALL" and I have never had an issue.

---

### Post by Quackers on 2011-01-22
hawkmage, it doesn't work in either of my Natty installs. It uses a newer sudo.


slooksterpsv,
You could take the internal doors off, but leave the external doors on, couldn't you?
"The reason it's bad to run as root is, what if you're in the terminal and you write a command that you accidentially typed in something wrong, but it would still execute and do major damage?"
What kind of argument is that? So, if I type sudo in front of it and enter my password I won't make the same mistake? A completely invalid argument, imho.

"What if you clicked on a folder by accident, and it dragged what you clicked to wherever, and you couldn't move it back cause it was a system folder that had commands to do so in it?"
Then the item shouldn't have moved in the first place, without warning!

---

### Post by bodhi.zazen on 2011-01-22
Thread closed.

As you already know, this kind of activity is not advised and it is not supported here. 

See: [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

If you are connected to the internet you are not the only potential user.

If you really want this kind of activity, use a live CD (such as Slax) with a persistent home, and not Ubuntu.

---

