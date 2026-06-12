---
title: "Installing as non-root"
date: 2008-09-11
forum: Security
---

### Post by Tanker Bob on 2008-09-11
I was setting up a Kubuntu Hardy system at the church last night. I installed all the major software as the initial user (super user) with no problems. I then created and logged into a normal user account. While setting up Firefox, I needed to install Flash support for that user. I had already done so in the initial account but of course it didn't carry over to the next user's profile.

Bottom line is that I could not find a way to install anything that required sudo in the regular user account. Yet, there was certainly a need to do so. I eventually gave up, made the user an administrator with root privileges, logged back in as the user, then did the install followed by changing the user's privileges back to normal. This seems like an extraordinary measure that surely isn't routine.

Is there a way to install software in a normal user (non-sudo) account without upgrading their privileges? I'm looking for a way for an administrator to execute commands using sudo while logged in under a regular user's account so that the setup goes into that user's profile. This would seem to me to be a common situation, yet I cannot find an answer.

---

### Post by jerome1232 on 2008-09-11
Well you could create a group called lets say 'install' add users you want to be able to install programs to the group 'install'

Then you could edit the sudoers file to allow members of the group 'install' to run /usr/bin/apt-get as root.

This way they can only run that one program as root.

On a second note I find it odd other users didn't have flash, on my system flash works across acounts... I'm pretty sure I didn't have to install it on the other ones.

You might want to skim through this for details on syntax of the sudoers file
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)
I tested it on my system and puting the following line allowed users of the group install to run apt-get as root.

%install ALL=(root) /usr/bin/apt-get

%install - that means this rule is for the group install
ALL - all users of the group install
(root) - this is the user they can run this command as
/usr/bin/apt-get - they can only run this command with escalated privilages

to edit the sudoers file
```
sudo visudo
```

I'm pretty sure I only installed flash once it works across accounts i'm going to setup a test user with limited privileges to check here real quick

edit: I just created a new user with the command
```
sudo adduser test
```
And the new user had all the firefox plugins that I have installed on my admin account so I'm not sure why it doesn't do that for you.

---

### Post by Tanker Bob on 2008-09-11
Thank you, Jerome, for your detailed and helpful answer. I was surprised when the Flash plugin didn't go universal. Not sure what I did wrong.

I'll check out that sudoers file setup. That looks like a good compromise approach. I really wanted the ability to do admin work from inside of a standard user's session without changing that user's permissions. Is that possible?

---

### Post by jerome1232 on 2008-09-11
Sorry that was the best I could figure out.

re-reading your post I didn't notice the 'without upgrading their privileges' part, sorry about that :)

I think the main mystery is why isn't flash universal, how did you install flash?

I've always installed the flashplugin-nonfree package via apt-get, I'm assuming that's how you installed it.

I'm afraid I can't be of much help beyond that.

---

### Post by Tanker Bob on 2008-09-11
You've been a great help and I appreciate it. I especially want to limit admin privileges, and you've shown me how.

I installed the system from scratch with a particular goal in mind. That goal didn't include Flash, but it came up when configuring Firefox in the normal user account. I honestly don't remember how I installed Flash in my account last night, but I normally do it as you said except that I use aptitude instead of apt-get. In fact, I don't remember installing Flash in my account, but it obviously was because it worked fine and appeared in the about->plugins list.

---

### Post by qstraza on 2008-09-11
> **Tanker Bob said:**
> I was setting up a Kubuntu Hardy system at the church last night.

god knows which OS is leet ;>

---

### Post by Biochem on 2008-09-11
> **Tanker Bob said:**
> 
I'll check out that sudoers file setup. That looks like a good compromise approach. I really wanted the ability to do admin work from inside of a standard user's session without changing that user's permissions. Is that possible?

You can do admin work from inside a standard user's session without changing their permission. You can actually work as any other user from a regular user account BUT you have to know the other user password. 
```
userA@computer:~$ su userB
Password:
``` 
will let you in userB account, is he has admin priviledge you can use them. Usefule if your girlfriend is working on the computer and need a app now. Faster than logout/login.

---

### Post by jerome1232 on 2008-09-11
You can use sudo things as any user, it will prompt for your password this way
```
sudo -u <user> <command>
```

which will run <command> as <user>

I thought you wanted something totally different

---

### Post by Tanker Bob on 2008-09-11
> **Biochem said:**
> You can do admin work from inside a standard user's session without changing their permission. You can actually work as any other user from a regular user account BUT you have to know the other user password. 
```
userA@computer:~$ su userB
Password:
``` 
will let you in userB account, is he has admin priviledge you can use them. Usefule if your girlfriend is working on the computer and need a app now. Faster than logout/login.

Thank you! That's exactly what I need. Will that keep the original user's home directory current or will the newly logged in user's home directory become current?

---

### Post by Biochem on 2008-09-12
> **Tanker Bob said:**
> Will that keep the original user's home directory current or will the newly logged in user's home directory become current?
Youn will stay in the current directory. to go directly in the new home just us cd.

```
userA@computer:~$ su root
Password: 
userA:/home/userB# cd
computer:~# 
```

---

