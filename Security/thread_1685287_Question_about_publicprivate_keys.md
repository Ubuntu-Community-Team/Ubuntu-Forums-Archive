---
title: "Question about public/private keys"
date: 2011-02-08
forum: Security
---

### Post by 1serveyou on 2011-02-08
> **rudelgurke said:**
> Hmm - if you want to be kept out of trouble, why not setup your SSH daemon first properly ? Then you'll notice Fail2ban is a waste of time and even increasing the risk for your server.

Speaking of:  [http://www.ossec.net/main/attacking-log-analysis-tools](http://www.ossec.net/main/attacking-log-analysis-tools)  as example.

Meanwhile this error has been fixed, yes, still this example shows that the more complex things are, the more errors there may be.  So, take care first of your SSH server by enabling publick key authentication, setting up the other options and then watch the bots trying to bruteforce failing. If it still gets annoying, change the port though this just keeps the logfiles more clean, it doesn't improve security.

I have a question about public keys, previous I had public keys and a password to log into my server outside of my network. Now say if I didn't have a password, and only used a public key(which I thought I heard was somewhat common), every time I was on a new computer it would ask, are you sure you want to connect, and if I said yes it would let me connect(then I had to type in my password) to the server. What stops someone else from logging into your server?

---

### Post by rudelgurke on 2011-02-10
That someone else neither has the private key that is accepted nor the required passphrase for that private key.
Additionally the $HOME/.ssh/authorized_keys is only readable (at least here) by the corresponding user, not writeable so adding new keys requires root access.

Now - if someone can make it to root access to add new keys to this file, for sure I've other problems than caring about this ;)

Generally the public / private key authentication stops the possibility of bruteforce attacks on the SSH server. So things like fail2ban, denyhosts etc. that can do more damage than they're useful aren't required any longer.

---

### Post by jbrown96 on 2011-02-10
> **1serveyou said:**
> I have a question about public keys, previous I had public keys and a password to log into my server outside of my network. Now say if I didn't have a password, and only used a public key(which I thought I heard was somewhat common), every time I was on a new computer it would ask, are you sure you want to connect, and if I said yes it would let me connect(then I had to type in my password) to the server. What stops someone else from logging into your server?

He or she doesn't have your private key...

---

### Post by cariboo on 2011-02-10
Moved to a separate thread, as this has nothing to do with the thread it was in.

---

### Post by anomie on 2011-02-10
[QUOTE=1serveyou]every time I was on a new computer it would ask, are you sure you want to connect, and if I said yes it would let me connect(then I had to type in my password) to the server. What stops someone else from logging into your server?[/QUOTE]

I think you're confusing host authentication / identification keys with user authentication keys. 

The former is what your ssh client is chattering about when you connect to an unrecognized server. 

As for the latter, as mentioned, the fact that "someone" doesn't have your private user key prevents him from authenticating as you.

---

### Post by 1serveyou on 2011-02-18
> **anomie said:**
> I think you're confusing host authentication / identification keys with user authentication keys. 

The former is what your ssh client is chattering about when you connect to an unrecognized server. 

As for the latter, as mentioned, the fact that "someone" doesn't have your private user key prevents him from authenticating as you.

Thank you everyone! I knew I had made a post about this, but couldn't find it. 

Anomie, I think you are right, I thought I had setup user authentication, but I'm looking more into it, and it seems I hadn't. I believe I did confuse host authentication with user. I don't have that server up and running now as I took it off the network because it was a test machine and I was getting a lot of attempted attacks on it.

I think I'm getting a bit confused on the process/terminology, but please bare with me. If I have private/public key authentication setup, would someone who doesn't have a key even see the host authentication? If so, and they say "yes" what happens? What do they see, and can they enter a user/password? Now, if they did have the correct private/pub, would they still have to enter a user/password? If not, can you make it so they do? Thank you again everyone, and thank you in advance!

---

### Post by FuturePilot on 2011-02-18
> **1serveyou said:**
> 
If I have private/public key authentication setup, would someone who doesn't have a key even see the host authentication? 
Yes
> If so, and they say "yes" what happens? What do they see, and can they enter a user/password?
If you have disabled password authentication they will just get disconnected with "Permission denied (publickey)". However if you haven't disabled password authentication they would be prompted to enter a password. If you don't use password authentication and only key based authentication, disable password auth.
> Now, if they did have the correct private/pub, would they still have to enter a user/password?
Yes. So make sure you use a strong password on your key. But also, make sure you keep your private key safe so that it doesn't come down to that in the first place.

---

### Post by 1serveyou on 2011-02-18
> **FuturePilot said:**
> Yes

If you have disabled password authentication they will just get disconnected with "Permission denied (publickey)". However if you haven't disabled password authentication they would be prompted to enter a password. If you don't use password authentication and only key based authentication, disable password auth.

Yes. So make sure you use a strong password on your key. But also, make sure you keep your private key safe so that it doesn't come down to that in the first place.

Thank you FuturePilot for clearing them up for me!

---

