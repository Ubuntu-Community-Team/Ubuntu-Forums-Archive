---
title: "[SOLVED] Why does sudo fail where su succeeds?"
date: 2007-07-07
forum: Server Platforms
---

### Post by B-Con on 2007-07-07
Why is it sometimes I attempt to perform an action as root with "sudo", but can't even if logging in as root with "su" works? Take the following example:
> b-con@beacon:~/Desktop$ sudo echo 1 > /proc/sys/net/ipv4/ip_forward 
bash: /proc/sys/net/ipv4/ip_forward: Permission denied
b-con@beacon:~/Desktop$ sudo su
root@beacon:/home/b-con/Desktop# sudo echo 1 > /proc/sys/net/ipv4/ip_forward 
root@beacon:/home/b-con/Desktop#
Doing the command with sudo returns a permission error, but logging in as root and doing it doesn't. My best guess is that sudo attempting to give me permissions other than root when I use it, is that possibly the culprit?

---

### Post by aysiu on 2007-07-07
Because you need sudo after the > part of the command.

---

### Post by B-Con on 2007-07-07
What exactly do you mean? Like this?
> sudo echo 1 > sudo /proc/sys/net/ipv4/ip_forward 
That's definitely not it...?

---

### Post by aysiu on 2007-07-08
What if you try something like this? ```
sudo echo 1 | sudo tee /proc/sys/net/ipv4/ip_forward
```

---

### Post by B-Con on 2007-07-08
Cool, that works. Thanks.

Why doesn't the very first thing I tried work, though? Shouldn't sudo grant permission to the entire operation about to be performed? I'm assuming the problem is because of the output redirection somehow.

---

### Post by aysiu on 2007-07-08
No, the **>** puts a break in *sudo*'s powers.

---

### Post by B-Con on 2007-07-08
Right, that's what I actually meant.

Ahh, I think I get it, it's a syntax evaluation problem. First "sudo echo 1" is being evaluated, *then* "> /file/path" is being processed. Ie,
(sudo echo 1) > /file/path

...rather than what I thought it did:
sudo (echo 1 > file/path)

Is that correct?

---

### Post by MJN on 2007-07-08
Another method is to use a sub-shell for all the commands:

[B]sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

[/B]This can be useful if you're not sure how to modify the command list (e.g. if you didn't know about **tee** in the above example).

Mathew

---

### Post by Mr. C. on 2007-07-08
The shell sets up redirection and pipelines *before* any commands are executed, therefore, these redirections and pipelines are connected with your current shell's privileges.

MrC

---

### Post by B-Con on 2007-07-08
> **MJN said:**
> Another method is to use a sub-shell for all the commands:

[B]sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

[/B]This can be useful if you're not sure how to modify the command list (e.g. if you didn't know about **tee** in the above example).

Mathew
Cool, thanks.

> **Mr. C. said:**
> The shell sets up redirection and pipelines *before* any commands are executed, therefore, these redirections and pipelines are connected with your current shell's privileges.

MrC
Ah, that makes sense. Thanks.

Since that's the responsibility of the shell, is this unique to bash or fairly universal?

---

### Post by Mr. C. on 2007-07-08
Because of how Unix/Linux works internally, any general redirection or pipelining "plumbing" must be setup prior to command execution.  Redirection and pipelining syntax (eg. >, <, |, 2>&1, etc.) are a shell concepts, but the general mechanisms that support this are part of the kernel.

This is standard on all sh / csh derived shells; although there are slight syntactical differences between sh-derived shells and csh-derived shells (and between early sh vs. bash), the order in which the plumbing occurs is the same.

See Redirection and Pipes, week 4 Coursework: [http://cis68a.mikecappella.com/](http://cis68a.mikecappella.com/)

MrC

---

### Post by B-Con on 2007-07-08
Good stuff. Thanks for the info.

---

