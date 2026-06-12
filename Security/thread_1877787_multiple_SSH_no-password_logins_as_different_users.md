---
title: "multiple SSH no-password logins as different users from 1 client"
date: 2011-11-08
forum: Security
---

### Post by bpb_21 on 2011-11-08
I hope this is in the correct section for this post - please move if not.

I have a moderate level of general experience with Ubuntu server and all machines in this question are running updated Ubuntu 11.10.

I have my main production laptop (Ubuntu desktop 11.10 with Unity) which I have set up to connect to a server at home (running Ubuntu server 11.10, no GUI, mainly for backup/printer sharing purposes) and I use SSH to connect, no passwords allowed.  I log in to both laptop and server machines as the same user.

There is also another Ubuntu server (11.10, no GUI) at work which I log in to, using SSH, as a different user (not present on my laptop).  But, this server still allows password logins over SSH.

What I would like to do is to be able to log in to both servers, as a different user on each, using SSH with passwords disabled on both.  (Not disabled, just for login purposes.)

I'm pretty comfortable with the command line, but I'm having some conceptual difficulty how I set up the public/private key pairs so that none of my home server access information gets on the work server and vice versa.  Basically, I don't want to use my client laptop user name to sign in to the work server or to have the same public/private key pair associated with my home server and work server.

This obviously works fine if password logins over SSH are enabled, as that's what I'm doing now.  But I'm wondering how it works if you want to not allow password logins over SSH and still be able to log in without that user on your client machine.  Does that make any sense?

I set up both servers and have full access to them.  The work server will host only one non-mission-critical application and will be a stand-alone from the rest of the hardware, but I want to make sure I conceptually understand this before allowing others access even to it.

I hope that makes sense!  Any help is appreciated.

---

### Post by markbl on 2011-11-08
You keep your private key only on your laptop but copy your public key to the ~/.ssh/authorized_keys file on each server. Use ssh-copy-id to do this easily. That only allows logins from your laptop to each server, not vice-versa. Add a stanza to ~/.ssh/config on your laptop to make logging in easier. E.g:

```

Host mywork
    Hostname mywork.somewhere.com
    User my_work_user_name

```

then just a "ssh mywork" logs you in with correct host + user. Can also set port, proxy through firewalls (via ProxyCommand - need to know about this), etc.

---

### Post by bpb_21 on 2011-11-09
Ok, I get it!  Not sure why I was having a mental block with that, but thanks.  And, that's a neat script as well.  Appreciate the help!

---

