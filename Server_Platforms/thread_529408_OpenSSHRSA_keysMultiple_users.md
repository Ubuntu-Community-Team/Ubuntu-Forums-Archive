---
title: "OpenSSH/RSA keys/Multiple users"
date: 2007-08-19
forum: Server Platforms
---

### Post by h4ckett on 2007-08-19
Hey Gang,

I'm running a 6.06LTS server (no gui) on some old hardware for about 2 years (used to have 5.10 until upgrading a while back), and she runs magnificently. It sits under my desk with only power and ethernet cords; I control it primarily with OpenSSH and I use an RSA key to gain access, via Putty on my Windows box. While I've found tons of walkthroughs, I haven't found one that shows how to create one for an additional user(s), or at least, one that would work in my situation. 

I have to be logged in as, lets say, User2 to generate a key pair for that user, right? But, if I'm already connected to this box as User1, if I logout I get kicked out of ssh so I can't switch to User2 once I'm in. I can't ssh in as User2, because that user doesn't have a key yet.

Should I disable RSA and go back to password, ssh in as User2, make the keypairs and do what I need to do, then reenable RSA? While that sounds like it makes sense, it just sounds all unnecessary. But, maybe thats a drawback of not directly interfacing with the machine?

Is there are way to set this all up as User1 (an admin) or root? Thinking about that though, I guess it wouldn't be in security's best interest to have other users making/managing keys for other users... or is it?

Any suggestions?

Thanks!
Chris

---

### Post by a9k on 2007-08-21
Can you launch another copy of Putty? Because you could have one ssh session open as user1 and then play with user2. 

SSHD is very good about maintaining existing connections through sshd restarts. It is scary to update a remote sshd and the run /etc/init.d/sshd restart -- but it works.

ssh-keygen doesn't care about who is making the key pair - it is just that the default location for storing the pair is ~/.ssh/ . I've moved private and public keys around a lot onto new systems etc.

You could try this on your Ubuntu server
1) run ssh-key -t dsa  -b 1024  # I like dsa 1024
2) it will prompt with "Enter file in which to save the key (/home/xyz/.ssh/id_dsa):" but change that to "user2_dsa"
3) put in a pass phrase for the user or skip it (twice). This is the fishy part if you only want the user knowing the pass phrase. Maybe you could have them at your terminal when you generate the pair?

Now you should have a pair of files: user2_dsa and user2_dsa.pub
4) install the user2_dsa.pub into the /home/user2/.ssh/authorized_keys2 by using cp. Like cp /home/user1/user2_dsa.pub /home/user2/.ssh/authorized_keys2

Another way to do this (faster) would be to 
```
useradd user2
sudo -H -u user2 -s
cd
ssh-keygen -t dsa -b 1024
exit

```

Now you still need to get the private key "user2_dsa" off the server and into the user2's PC or usb-keyfob or something.

---

### Post by h4ckett on 2007-08-25
Brilliant! Thank you!

I wasn't sure if anyone could just generate the key or the user that was going to use them. Thanks for clearing that up for me.

As for the whole passphrase deal, I don't care if I know the user's passphrase (as it's just friends accessing my box remotely), just was wondering what the general accepted practice is, if there is any.

Thanks again!

---

