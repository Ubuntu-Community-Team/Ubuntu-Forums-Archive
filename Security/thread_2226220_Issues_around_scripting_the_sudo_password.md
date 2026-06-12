---
title: "Issues around scripting the sudo password"
date: 2014-05-26
forum: Security
---

### Post by jacob20 on 2014-05-26
A quick google search just tells me "NO" but not "NO BECAUSE".Basically, I'm working on a script that's going to be the grand master of productivity for a recurring task I have to do. Without getting into the intricates, it will essentially run remote SSH commands with sudo in it.I'm seriously considering doing something like:ssh user@server "echo sudopasswd | sudo -S command" The reason for this is because the constant requirements for entering in the same password about 15 times during the same script is negating the productive aspect of the script - sometimes you wont get prompted for the sudo password, othertimes it will break up the format of the output.. so on and so fourth.Basically everyone tells me it's a terrible idea because "someone can get your script" but in this particular instance.. they can't - not to mention that the password would be no less secure than storing it in a text file somewhere.So my question for the ubuntu forum security experts here is what is the concern about using the sudo password in this manner? Is the issue around storing a password in plain text? Or is it related to having it showing up in bash history?When parsing the password through ssh, does it actually get stored in the bash history? Are there any other concerns you can think of surrounding this usage?Thanks in advance.

---

### Post by jacob20 on 2014-05-26
I'm trying to edit the original post because the formatting messed up but it won't let me. Will try again once i'm home from work.

---

### Post by Lars Noodén on 2014-05-26
You can grant specific options to sudo use .  It does not have to be all or nothing.  Do you have a specific command with specific options that will be run the same way each time?  If so, then that is easy to set up in /etc/sudoers

```

%somegroup  ALL=(ALL) NOPASSWD: /usr/bin/somecommand -optionone -optiontwo

```

That way you can run that command with sudo, but not need a password.  And since you specific which options it is to run with, it can only run with those options and no others.

Also, you can tighten down the script further by forcing the command in the key itself.  In the public key, the one stored on the server, specify the command with its options at the beginning of the line.

```

command="/usr/bin/sudo /usr/bin/somecommand optionone optiontwo" ssh-rsa AAAAB3NzaC1yc2EAAAADAQA...S2Mqf

```

That way the key can't be used for anything other than that command.

---

### Post by papibe on 2014-05-26
Hi jacob20. Welcome to the forum ):P

There are a few ways to accomplish this. For instance:
[LIST]
[*]Use [keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") instead of password to login through ssh.
[*][Disable the sudo password]("http://askubuntu.com/questions/147241/execute-sudo-without-password") for 'some' commands.
[/LIST]
There's also some common security practices:
[LIST]
[*]Only allow remote connections using keys, and additionally disable passwords all together (for login).
[*]Disable root connections via ssh.
[*]Set up a firewall using iptables to:
[LIST]
[*]prevent brute force attacks.
[*]restrict access from certain IPs.
[*]blacklist common attacker.
[*]
[/LIST]
[*]etc
[/LIST]
Having said that, I think if you give us more details of what you are trying to do, we can come up with suggestions more in tune with your particular situation.

As far as I understand:
[LIST]
[*]You run a script on a remote machine from a normal user.
[*]It connects via ssh to a admin/sudoer user on a remote server.
[*]Finally, it tries to run root commands via sudo.
[/LIST]
Is that it?

Regards.

---

