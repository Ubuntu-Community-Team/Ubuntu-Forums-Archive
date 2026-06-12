---
title: "Remote command failing"
date: 2009-12-12
forum: Server Platforms
---

### Post by Muttley99 on 2009-12-12
I can connect okay through SSH direct to my server (9-10). However, my aim is to run scripts from my local (kubuntu) machine which invokes a command on the server (I'm lazy). I've setup a key exchange with the server for passwordless login.
I want to pm-suspend the server by;
ssh [email]david@192.xxx.xxx.xx[/email] 'pm-suspend'

my problem is, after editing my sudoers on the server to allow david NOPASSWD for /etc/pm-suspend.
I now get the error;

[HTML]sudo: no tty present and no askpass program specified[/HTML]

I can get round the error by setting visible password in sudoers BUT this makes the whole task pointless as it will then ask for a password.
How can I set the server to allow py0?

---

### Post by koenn on 2009-12-12
I'm sure someone will correct me if I'm wrong, so here goes:

I think this is one of these rare cases where sudo gets in the way.
I'd enable the root account and do 'ssh **root**@...  /etc/...'

As you use keys for ssh, the root account on the server is only protected by your own credentials on your pc, not unlike a local sudo. 
(assuming the keys don't require a pass phrase)

On the server, you can protect the root account by not allowing password authentication for remote logins (ie require a key for ssh, as you did). I believe you could disable  *local* logins for root, but I forgot the specifics. If you need to log on locally to the server (console), you'd log in with a normal user account and become root with 'su'.

---

### Post by Muttley99 on 2009-12-13
Thanks for the reply!

I'll check this out now and let you know.

---

### Post by Lars Noodén on 2009-12-13
> **Muttley99 said:**
> 
[HTML]sudo: no tty present and no askpass program specified[/HTML]


When invoking the [ssh client](http://www.openbsd.org/cgi-bin/man.cgi?query=ssh), force tty-allocation.  That might fix the problem.  

```

# this 
ssh -t david@192.xxx.xxx.xx 'pm-suspend'

# or this
ssh -tt david@192.xxx.xxx.xx 'pm-suspend'

# or this 
ssh -t david@192.xxx.xxx.xx 'sudo pm-suspend'

```

It would be a bad idea to follow recommendations to allow remote root login or other dangerous commands.

---

### Post by koenn on 2009-12-13
> **Lars Noodén said:**
> 
It would be a bad idea to follow recommendations to allow remote root login or other dangerous commands.
If that is referring to the suggestion I posted, I'd really like an explanation of how a paswordless public key authentication for a remote root account is less secure than a paswordless public key authentication for a remote sudoer, especially in a case where one wants to avoid a sudo password prompt.

But besides that, if there are other ways of solving this problem, it would be interested to se how that is done.

---

### Post by Muttley99 on 2009-12-14
> **koenn said:**
> If that is referring to the suggestion I posted, I'd really like an explanation of how a paswordless public key authentication for a remote root account is less secure than a paswordless public key authentication for a remote sudoer, especially in a case where one wants to avoid a sudo password prompt.

But besides that, if there are other ways of solving this problem, it would be interested to se how that is done.

Actually, Although this is a widely held belief I have some trouble understanding it also! If a hacker can login as a user I assume the hacker has access to my password which will allow him/her to cripple my server. 
I don't see a determined hacker being frightened of using sudo once access has been gained.
sudo rm -f is not much of an obstacle to someone who wants to do damage.
Having said that, the greater the obstacle, the greater the security!
My encrypted /home is causing me problems right now, when I sort that out I'll try both your suggestions! thanks to both of you for replying!

---

### Post by BkkBonanza on 2009-12-14
The problem isn't so much what a skilled hacker will do but what a malicious script will do. It may not be customized to your situation so if it by chance gains root then it can do a lot more than if it gains your user account.

I think chances are pretty slim that something can gain root via ssh using a key but a basic tenet of security is to keep things as tight as you can because you don't have perfect knowledge of potential attack methods.

---

### Post by Lars Noodén on 2009-12-14
> **Muttley99 said:**
> 
I don't see a determined hacker being frightened of using sudo once access has been gained.

That comes only with misuse or abuse of sudo.  Single-use keys need to have a sudoers formula that allows only the specific action to be carried out, and only with predetermined parameters.  

```

# wrong
%admin ALL=(ALL) ALL

# better
%backup   ALL=(ALL) NOPASSWD: /usr/bin/rsync --server -vlHogDtprz \
        --delete --delete-after --ignore-errors . /org/backup

```

One reason of many not to allow remote root access directly is simply to make it easier to track who is doing what.  Crackers will pound on the front door.  Rather than wasting your time trying to figure out if that root access was you or your assistant, set it up so you have a very good idea.  If it goes via a regular account, then you know to contact the regular account's owner and ask questions.  If it only says 'root' then you have to go down the list of everyone who might have access and check with them.

---

