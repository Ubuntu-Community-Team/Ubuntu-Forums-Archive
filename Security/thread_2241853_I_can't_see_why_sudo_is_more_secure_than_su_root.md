---
title: "I can't see why sudo is more secure than su root"
date: 2014-08-28
forum: Security
---

### Post by raspatan on 2014-08-28
Sorry for this repetitive topic but after reading many forums and ubuntu guides, I just can't convince myself. 

If I have sudo privileges, then anyone knowing my password (say, a family member) can access my computer and damage the system, just like I can do with sudo. However, if there is a root user AND I have not sudo rights, then it is not enough to know my password to destroy the system. Now, this is in the context of a computer shared with other people. You might say "well, just create users for anyone or a guest account". Yes, but still anyone knowing my password can enter into my account and damage the system. This is prevented if not even from my account sudo actions can be performed. And even more, if I give no one sudo permissions but I need to perform a superuser action in any of my family members account, then I guess it is cleaner to run "su root" whenever I need it instead of "su me". 

Now, in the case of a hacker or so, I guess it is equally easy (or difficult) to know my password or the root one so in this case it is actually irrelevant. 

Therefore, I don't see why sudo is superior. And if the answer goes around the time limit implicit in the sudo command, well, I imagine that can be solved in another form? Can you not give a timelimit to the su command?

PS: As an aside, I just realize that if my computer get stolen, then anyone can just format it and reuse it, in which case ubuntu security (and any OS I guess) is pointless. Thus I set up a boot password! :)

---

### Post by ajgreeny on 2014-08-28
Have you read the page of discussions about this at [RootSudo]("https://help.ubuntu.com/community/RootSudo") shown in my signature?

There pros and cons to anything in this life.
Make your own choice, and if you really want to, enable the root account with its own password, though I am not going to tell you how as it is severely frowned on in this forum.

And of course, you are correct; physical access means all security is useless once someone who knows what they are doing has the machine.

---

### Post by deadflowr on 2014-08-29
Someone could do a fair amount of personal damage to your computer without a password at all, if you allow them into your home folder.
Letting somebody log into your account gives them the rights to do all the damage they want to your files.

One of the benefits of linux is that it is a multi user system.
Though I mainly am the only user on my system, I anticipate that others, at times, may need to use it.
For this I always create a non-admin user, which can be used to whomevers hearts content.
Since this new account has no ties with my main account, no damage can be caused to me by them.

As far as su v sudo, sudo is run per instance su(root) is persistent.
With sudo, I run a single command and that is it, with su(root) every command is a root-level command.
It can be very easy to forget that you are running as root and put in a mis-written command without thinking it through and damage the system.
At least with sudo, just by adding the word sudo, you should have a sense that what you are doing might have dire consequences.

But that is just a couple of thoughts I had on it.

---

### Post by thnewguy on 2014-08-30
The sudo approach has a couple of benefits over using the root account.
1. You only need to remember one password. On systems where you have a root account which is separate from your user account then you need to maintain two passwords to have any sense of security. Having sudo linked to your account simplifies things.

2. Sudo automatically forgets its permissions after a while. If you are logged in as root you have those permissions until you logout.

3. You can limit sudo's permissions. The root account always has access to everything, but you can limit the power of sudo. This makes sudo potentially safer.

4. You can give multiple users sudo access with separate abilities. For example, you can give one user sudo access to manage network settings, but not packages. Or give another sudo user access to packages, but not the system clock. This is much better than giving everyone the same password to the root account. You don't want multiple users all using the same account with super user access. It's much better to hand out access permissions as needed and sudo enables that.

5. Sudo will log access for you. If people have access to the root account then you don't really have an audit trail. Sudo can track who is doing what which is especially important if you work in an environment with multiple admins.

Basically, sudo is better in every possible scenario except the one where you are the only person who uses the computer, like a laptop. Even then sudo saves you from remembering credentials to two accounts, you main user and root.

---

### Post by Lars Noodén on 2014-08-30
> **thnewguy said:**
> 3. You can limit sudo's permissions. The root account always has access to everything, but you can limit the power of sudo. This makes sudo potentially safer.

4. You can give multiple users sudo access with separate abilities. For example, you can give one user sudo access to manage network settings, but not packages. Or give another sudo user access to packages, but not the system clock. This is much better than giving everyone the same password to the root account. You don't want multiple users all using the same account with super user access. It's much better to hand out access permissions as needed and sudo enables that.

5. Sudo will log access for you. If people have access to the root account then you don't really have an audit trail. Sudo can track who is doing what which is especially important if you work in an environment with multiple admins.

3 & 4 are the real power of sudo.  You do not have to dole out full root permission.  With sudo you can choose which programs a group (or user) can run as root and even which options they can or can't have with those programs.  It's all in the configuration and more relevant in a multi-user environment.  

5 is very important when a situation arises where it is important to ask someone quickly who did what.  One lesser known capability is the ability to configure it to [replay entire sudo sessions](http://manpages.ubuntu.com/manpages/natty/man8/sudoreplay.8.html) to see or show exactly what happened.

---

### Post by whitesmith on 2014-08-31
The advantages of points 3, 4 and 5 can be coupled with persistence by:```
sudo -i
```which creates a root terminal until closed. This could be dangerous, of course, as others have noted of su.

---

### Post by ajgreeny on 2014-09-01
For extra safety on the occasional use I make of **sudo -i** for a root terminal, I have edited the **.bashrc** file in root's /home folder to get a bright red prompt instead of my normal user's bright green prompt.  It's only a small point but just a reminder not to do anything stupid with that terminal open.
Just look for the lines
```
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;[COLOR=#ff0000]32[/COLOR]m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
```
and edit it to
```
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;[COLOR=#ff0000]31[/COLOR]m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
```

You also need to uncomment the line **#force_color_prompt=yes** in both files to get colour prompts in the first place.

---

