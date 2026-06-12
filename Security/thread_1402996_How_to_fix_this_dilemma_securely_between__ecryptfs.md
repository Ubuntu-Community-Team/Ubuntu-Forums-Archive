---
title: "How to fix this dilemma securely between  ecryptfs and ssh server"
date: 2010-02-09
forum: Security
---

### Post by LighthouseJ on 2010-02-09
I just installed Ubuntu 9.10 on this server of mine.
I want to open it to a few people so I changed to a nonstandard port (>1024), turned off password authentication and turned on key authentication.

I also installed this with eCryptFS, which mounts and unmounts an encrypted home directory for each user on their first login and last logout.

The problem is if I'm not logged in and try to ssh in, openssh server can't find my authorized_keys file (it's inside of my encrypted home that's not mounted yet) and I cannot login.  I had to plug a keyboard into the headless machine and login blind to get access via ssh.

What's the best way to fix this?  Tell the sshd_config file to use an authorized_keys file not in my home dir?

thanks

---

### Post by FuturePilot on 2010-02-09
[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/362427/comments/12]("https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/362427/comments/12")
That's what I did

---

### Post by LighthouseJ on 2010-02-09
ah, thanks friend, but what if the machine is headless and would be a massive PITA to do this from the console?

---

### Post by Agent ME on 2010-02-09
If the machine is headless, isn't using a few console commands your only choice? You can run those commands over SSH.

---

### Post by FuturePilot on 2010-02-09
> **LighthouseJ said:**
> ah, thanks friend, but what if the machine is headless and would be a massive PITA to do this from the console?

You can do it just fine over SSH.

---

### Post by LighthouseJ on 2010-02-10
But how do I get to the unmounted home directory while my encrypted home is mounted?

---

### Post by cariboo on 2010-02-10
You shouldn't have to mount your unecrypted home, it is already mounted. Just follow the instructions in the link FuturePilot provided.

---

### Post by LighthouseJ on 2010-02-10
Okay, I think that worked.
I had to do a few more steps but I know my way around linux and got it to work.

The steps linked above should include a proper chmod on the new autheorized_keys file that was created.

Thanks everyone.
I'll mark as solved.

---

