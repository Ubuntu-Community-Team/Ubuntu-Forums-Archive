---
title: "Weird situation with SSH and SCP service"
date: 2011-06-23
forum: Security
---

### Post by luvshines on 2011-06-23
I am stuck in a weird situation and could definitely use some help from gurus in security area.

I have categorized my users into 3:
1. root user
2. other local users
3. LDAP users

I want to setup following 2 usecases:
a)
1. Allow keybased ssh and scp to root users
2. Allow ssh but disallow scp service to other local users
3. Disallow ssh and scp to LDAP users

b)
1. Allow keybased ssh and scp to root users
2. Disallow both ssh and scp to other local users
3. Disallow ssh but allow scp to LDAP users

For the 1. in both cases, I think PermitRootLogin in sshd_config could help

For the 3. I am thinking of deploying rssh to control scp service access, since ssh will be restricted anyways.

Problem area is 2. primarily. 
i) How to allow ssh but disallow scp to 'other local users'
ii) How to disallow both ssh and scp to 'other local users'

Any help or pointers would be appreciated

---

### Post by Dangertux on 2011-06-23
As far as I understand , and I could be wrong you can not allow a shell  and simultaneously deny scp (short of rm'ing scp command)

Definitely an interesting question you pose, however I'm not sure it's possible to micromanage it this far.

The only real suggestion I can offer would be to set up the user's permissions so that if they do scp they can only cp files to a very controlled area :-/

---

### Post by luvshines on 2011-06-24
Came across this[http://serverfault.com/questions/28858/is-it-possible-to-prevent-scp-while-still-allowing-ssh-access]("http://serverfault.com/questions/28858/is-it-possible-to-prevent-scp-while-still-allowing-ssh-access")

What and how will ForceCommand restrict SCP, any ideaz ?

---

### Post by luvshines on 2011-06-30
**[color="red"]**bump**[/color]**

---

### Post by arius13721 on 2011-07-01
As was mentioned in the serverfault thread you posted, by blocking scp you're only making it harder to transfer files, because there will be 101 ways to get around the removal of scp.

In my experience, the harder you make something for someone to do, the more likely it will make that person look for a way to circumvent that security control which will in-turn make it more difficult to secure the box.

Additionally, removal of scp on the target box will not actually remove the scp functionality of copying files to the target.

With as tightly as scp is integrated into ssh, I don't think you can achieve a differentiation between allowing ssh and disallowing ssh.

It looks like you could accomplish a3 and b2 using the DenyGroups sshd_config item if assigning those users to a specific group is an option. 

[http://manpages.ubuntu.com/manpages/intrepid/man5/sshd_config.5.html](http://manpages.ubuntu.com/manpages/intrepid/man5/sshd_config.5.html)

---

### Post by luvshines on 2011-08-19
One possible way I found was as explained in the link I posted.
It used 'sh' shell.

Same way I could define my customized login shell for all users, which doesn't have 'scp' service enabled.
Going with /bin/bash, etc standard shells, I was not able to block scp but allow ssh

Guess, I have to live with this since I can't change my login shell for those users.

Marking this as SOLVED for now.

---

