---
title: "ubuntu-update.sh - open source script to update Ubuntu"
date: 2018-03-26
forum: Ubuntu, Linux and OS Chat
---

### Post by tleroy1 on 2018-03-26
Hi folks,

I, no doubt like many of you, found myself typing ```
sudo apt update && sudo apt upgrade -y && sudo apt full-upgrade -y
``` every time I logged into several individual Ubuntu 16.04 LTS servers I maintain. I decided to create a script and put it on [GitHub]("https://github.com/TedLeRoy/ubuntu-update.sh") for your enjoyment. 

It's open source, licensed under GPL v 3. 

Please have a look, provide input, or join the project!

Kind regards,

Ted LeRoy

---

### Post by tleroy1 on 2018-03-26
Some features:


[LIST]
[*]It runs the following commands:
[/LIST]

```
apt-get update
apt-get update -y
apt-get dist-upgrade -y
apt-get autoremove

```


[LIST]
[*]It presents a readable banner at the beginning of each command run.
[/LIST]


[LIST]
[*]It creates a temp file of the output and parses it, presenting items you may want to investigate at the end of the run.
[/LIST]

Ted

---

### Post by oldos2er on 2018-03-26
Not a support request,  moved to Ubuntu Linux & OS chat.

---

### Post by tleroy1 on 2018-03-26
Thanks oldos2er! Sorry for posting in the wrong area.

---

### Post by tleroy1 on 2018-03-27
Here's another GitHub project with similar goals but a little different approach.

[https://github.com/clickwir/dist-upgrade/blob/master/dist-upgrade](https://github.com/clickwir/dist-upgrade/blob/master/dist-upgrade)

Nice work clickwir!

---

### Post by monkeybrain20122 on 2018-03-27
> **tleroy1 said:**
> Some features:


[LIST]
[*]It runs the following commands: 
[/LIST]

```
apt-get update
apt-get update -y
apt-get dist-upgrade -y
apt-get autoremove

```


[LIST]
[*]It presents a readable banner at the beginning of each command run. 
[/LIST]


[LIST]
[*]It creates a temp file of the output and parses it, presenting items you may want to investigate at the end of the run. 
[/LIST]

Ted

Why would you want the "-y" option? Once in a while there are updates which would remove other stuffs, either because of user's set up or bad updates, the result can be disastrous if one goes ahead. what if one wants yo hold back some problematic packages (partial upgrades e.g) I don't think updates should be done via an automatic script without prompting user feedback, it is dangerous and the "-y" option is also dangerous, but then you can just use apt or synaptic (or other gui package manager such as muon depending on DE)

---

### Post by tleroy1 on 2018-03-27
Hi monkeybrain20122,

I run the commands frequently with the -y option, but I run it on stable systems.

If your system will be blown up by running the commands with the -y option, I wouldn't use a script like this, but would update manually every time.

If a user doesn't like the -y option, skip the script and run apt update && apt upgrade && apt full-upgrade. 

Even put that in a script:

```
#!/bin/bash
apt update && apt upgrade && apt full-upgrade

```

Then answer yes or no to apt upgrade and apt full-upgrade.

I appreciate you sharing your thoughts though.

Kind regards,

Ted

---

### Post by monkeybrain20122 on 2018-03-27
> **tleroy1 said:**
> 
I run the commands frequently with the -y option, but I run it on stable systems.




[This]("https://askubuntu.com/questions/1006621/2-15-18-compiz-update-broke-unity") just happened in Feb on stable systems (16.04).

---

### Post by tleroy1 on 2018-03-27
Wow, thanks monkeybrain20122,

That lessens my faith in Ubuntu! I hope they don't deploy any more updates without thorough testing!

---

### Post by tleroy1 on 2018-03-27
I do think, though, if I had not known it would break things, I would have answered yes when requested to by apt upgrade.

---

### Post by monkeybrain20122 on 2018-03-28
> **tleroy1 said:**
> I do think, though, if I had not known it would break things, I would have answered yes when requested to by apt upgrade.

Well I always check what it installs or removes (esp remove!) before going ahead. Total breakage resulting from removing key components to system like that is rare, but I have seen enough "partial upgrades" which if goes ahead will break something.

---

### Post by tleroy1 on 2018-04-01
If I don't have an up to date backup and quick way to restore, I'll check too monkeybrain20122.

Thanks for the head's up!

If I ran a larger environment, I'd have a test infrastructure to try it out on first.

---

### Post by tleroy1 on 2018-04-01
Version 1.2 released.

There's now a pre-flight check to see if you're running as root or with sudo permission. If not, it will exit after displaying a warning.

---

### Post by monkeybrain20122 on 2018-04-01
> **tleroy1 said:**
> If I don't have an up to date backup and quick way to restore, I'll check too monkeybrain20122.

Thanks for the head's up!

If I ran a larger environment, I'd have a test infrastructure to try it out on first.

I have the feeling that most people who would use such a script to automatically update are inexperienced users who want the convenience,  chances are they don't have an up to date backup and a quick way to restore, and don't have the infrastructure to do a test run first.

---

