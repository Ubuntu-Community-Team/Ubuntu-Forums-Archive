---
title: "How to enable 'su' command on Pangolin"
date: 2013-04-03
forum: Security
---

### Post by frankvw on 2013-04-03
Hi everyone,

A looooong time ago when I was still running Jaunty, I enabled the 'su' command. Yes, I know all about 'sudo' but I'm old fashioned so I like to 'su' every once in a a while. So now I want to do the same on my Precise Pangolin install. But no matter what I try I can't get it to work.

In /etc/sudoers I have:```
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```and I have created a group 'admin' and added my user account to it. Which, if memory serves, did the trick on Jaunty. But not, apparently, on Pangolin, which may have tighter security settings that need tweaking elsewhere. Or not.

So. How do I enable 'su' for my everyday user account on Pangolin? 

// FvW

---

### Post by wojox on 2013-04-03
Create an alias in root's .bashrc?```
alias su='sudo'
```

---

### Post by Cheesemill on 2013-04-03
The su command should already be installed and working.

Which user are you trying to su to? If it's the root account then this can't be done in a default Ubuntu installation as the root account is disabled.
The preferred method of getting a root shell in Ubuntu is by using...
```
sudo -i
```

---

### Post by haqking on 2013-04-03
> **wojox said:**
> Create an alias in root's .bashrc?```
alias su='sudo'
```

Why would you want to alias one command with another ?

An alias is not for that purpose IMO.

su and sudo are different commands

As cheesemill mentioned above, it is likely the OP cannot su due to them by default "su" without a username therefore defaulting to root which has no password set by default in Ubuntu and so locked.

---

### Post by Dave_L on 2013-04-04
> **frankvw said:**
> So. How do I enable 'su' for my everyday user account on Pangolin?

See this article: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by wojox on 2013-04-07
> **haqking said:**
> Why would you want to alias one command with another ?

:lolflag: I thought he was looking to shorten the word.

---

