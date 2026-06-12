---
title: "Ubuntu, Like A Rock"
date: 2014-02-10
forum: Security
---

### Post by ventrical on 2014-02-10
I am not trying to steal add time form Ford Motor Company :) lol but Ubuntu , is , like a rock ! I have been running and testing Ubuntu for over 3 and 1/2 years now and Ubuntu security provides a peace of mind that goes beyond what commercial or other operatings systems are capable of providing.

 When I see questionalble stories about Ubuntu security fails ( and yes , they do happen) I have to look at them discreetly and recognize most of them for what they are; a hill of beans! :)

  Ubuntu , thanks.

Regards..

---

### Post by ajgreeny on 2014-02-10
I've now been using *ubuntu since 5.04 and I agree with you totally.

I do not run any anti-virus on my system and never have, though I did install, though never use, clamav whilst I had XP on the machine. However, since I got rid of windows completely about 3 years ago, I haven't bothered with it.

I do not run any servers as a matter of course, just a standard desktop system, so i don't bother about ufw firewall enablement either, and when I need to use ssh between my machines, openssh-server being installed in all of them, I start it manually on the host machine with an alias in terminal, having commented out the line **# start on filesystem** in /etc/init/ssh.conf which means it does not start at bootup.

---

### Post by ventrical on 2014-02-10
Thanks for sharing your experience.  I also have a similar set up on most of my machines although I still do anti-malware rersearch. As an experimenter and beta tester I really do not have time for the hassles of firewall setups and AV installations .. etc.. With Ubuntu.. there is ....a sort of serenity in that there is just nothing that gets through (or cares to get through).  And I don't buy into the conventional wisdom that hackers have bigger fish to fry.

  The monolithic kernel (for begginers) is a natural discourager for  malware writers and the authentication process (which I use on all of my machines) is the second phlanx of defense which basically stops anything dead in it's tracks before it can cause any damage by an 'allow'.

  Some persons who I have worked with on the Ubuntus express some frustration over the authentication  for root processes but I just explain to them that this is the trade-off.  Accept the authentication process ro go back to Windows and firewalls and more crapware. Typing in my password each time I perform a root process is  nothing compared to the downtime I spent working with security programs on other operating systems.

Regards..

---

### Post by cariboo on 2014-02-10
I'd suggest not talking about the root user at all, as in Ubuntu that user is disabled. When you use sudo, all you are doing is escalating the users privileges to almost that of the root user.

If you check /etc/shadow, you'll see that the password field for root has an !, what this means, to quote from [http://linux.die.net/man/5/shadow:](http://linux.die.net/man/5/shadow:)

> If the password field contains some string that is not a valid result of crypt(3), for instance ! or *, the user will not be able to use a unix password to log in (but the user may log in the system by other means).

This field may be empty, in which case no passwords are required to authenticate as the specified login name. However, some applications which read the /etc/shadow file may decide not to permit any access at all if the password field is empty.

A password field which starts with a exclamation mark means that the password is locked. The remaining characters on the line represent the password field before the password was locked.

The command to check the root user entry in /etc/shadow should look like this:

```
sudo cat /etc/shadow | grep root
```

and the result when running Ubuntu looks like this:

```
root:!:15995:0:99999:7:::
```

For more info have a look at:

```
man shadow
```

---

### Post by ventrical on 2014-02-10
@cariboo907,

 Then I would gather that Ubuntu is more like a piece of steel with that added line of first defence.:)

---

### Post by ventrical on 2014-02-10
> **cariboo907 said:**
> 

For more info have a look at:

```
man shadow
```

 Just awesome. Learn something new every day. Even if a hacker was telereplicating a screen session through remote access they would not be able to decrypt the password in an efficient manner.

Regards..

---

### Post by bashiergui on 2014-02-10
> **ajgreeny said:**
> I do not run any servers as a matter of course, just a standard desktop system, so i don't bother about ufw firewall enablement either, and when I need to use ssh between my machines, openssh-server being installed in all of them, I start it manually on the host machine with an alias in terminal, having commented out the line **# start on filesystem** in /etc/init/ssh.conf which means it does not start at bootup.
I hope you use keys instead of passwords for ssh authentication, especially if it's accessible from the internet. Ubuntu won't protect you from routine ssh bruteforce /dictionary attacks. Then the successful attacker has all the rights that your ssh user has, which is usually in the sudo group.

---

### Post by CharlesA on 2014-02-10
> **bashiergui said:**
> I hope you use keys instead of passwords for ssh authentication, especially if it's accessible from the internet. Ubuntu won't protect you from routine ssh bruteforce /dictionary attacks. Then the successful attacker has all the rights that your ssh user has, which is usually in the sudo group.

Huge +1. Granted passwords can be effective if they are complex, but keys are better.

---

### Post by ajgreeny on 2014-02-10
> **bashiergui said:**
> I hope you use keys instead of passwords for ssh authentication, especially if it's accessible from the internet. Ubuntu won't protect you from routine ssh bruteforce /dictionary attacks. Then the successful attacker has all the rights that your ssh user has, which is usually in the sudo group.

Yes, I do use keys, though I only ever have openssh-server running on any host for a minute or two to transfer files then I stop the server, also using an alias in terminal, so even if I was allowing password authentication, I think the chance of attack would be limited.

I have also set a maximum number of tries for authorisation, a different port from the usual #22, a twenty second time allowance for logging in, and allow only two named users, none of which, I agree, would stop a determined attacker, but in the limited time that the server is running would at least make it less likely.  All those are historical from when I was learning about ssh, but I still edit sshd_config and make those changes to the default, whether or not they are now necessary.

---

### Post by CharlesA on 2014-02-10
Sounds like a similar setup to mine, minus stopping SSHD when you aren't using it. ;)

I find the AllowUser directive quite handy.

---

### Post by ajgreeny on 2014-02-10
Those aliases ssh+ and ssh- are very quick and easy to use.
[B]alias ssh+='sudo service ssh start'
alias ssh-='sudo service ssh stop'[/B]

Worth a try?

---

### Post by CharlesA on 2014-02-10
Good idea.

I have SSH installed on my servers, so stopping it when it's not in use would make managing them a bit difficult unless I wanted to connect to the console and start ssh up again.

It would work better if you are running it on a desktop install. :)

---

