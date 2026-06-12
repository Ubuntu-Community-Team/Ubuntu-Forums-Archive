---
title: "Create ssh disconnect message"
date: 2012-11-09
forum: Server Platforms
---

### Post by mbonlineuser on 2012-11-09
Hi all (new to the forums here), two questions if anyone can help.

I have a message for ssh logins in /etc/issue.net.  Is it possible to create a message that is shown to a logged in client when their session times out?

And although frowned upon, is a login as root over ssh also disconnected?

Thanks.

---

### Post by Lars Noodén on 2012-11-09
There's not anyway to have a timeout message that I know of, but it is possible to reduce the likelihood of session timeouts by changing settings for either the client or server.  On the server side you could set ClientAliveCountMax and ClientAliveInterval.  On the client side you can set ServerAliveCountMax and ServerAliveInterval.  Either of these will keep a heatbeat signal to try to prevent the connection from timing out.  

You can shutoff remote root login by changing PermitRootLogin to "no" in /etc/ssh/sshd_config

---

### Post by CharlesA on 2012-11-09
> **Lars Noodén said:**
> There's not anyway to have a timeout message that I know of, but it is possible to reduce the likelihood of session timeouts by changing settings for either the client or server.  On the server side you could set ClientAliveCountMax and ClientAliveInterval.  On the client side you can set ServerAliveCountMax and ServerAliveInterval.  Either of these will keep a heatbeat signal to try to prevent the connection from timing out.  

You can shutoff remote root login by changing PermitRootLogin to "no" in /etc/ssh/sshd_config
+1.

Another thing you can do is allow login to the root account with keys only, but it is usually easier to just login as something who has sudo rights and do it that way.

---

### Post by mbonlineuser on 2012-11-09
Thanks for the replies.

Ok, so I cannot define my own disconnect message.

I think you misunderstood by query about root.  If we assume (for this example) that ClientAliveInterval is 60, users will be logged out if they are idle for 60 seconds (assuming ClientAliveCountMax is 0); but my question is will root also be logged out if he/she is idle for 60 seconds?  It dosen't appear so.

---

### Post by Lars Noodén on 2012-11-09
> **mbonlineuser said:**
> Thanks for the replies.

Ok, so I cannot define my own disconnect message.

I think you misunderstood by query about root.  If we assume (for this example) that ClientAliveInterval is 60, users will be logged out if they are idle for 60 seconds (assuming ClientAliveCountMax is 0); but my question is will root also be logged out if he/she is idle for 60 seconds?  It dosen't appear so.

It's the other way around.  ClientAliveInterval helps prevent the users, including root, from being logged out if they are idle.  It sets the number of seconds between "I'm Alive" messages sent out.  ClientAliveCountMax is the number of those messages that can go missing before the server decides that the connection is dead.

[http://manpages.ubuntu.com/manpages/precise/en/man5/sshd_config.5.html](http://manpages.ubuntu.com/manpages/precise/en/man5/sshd_config.5.html)

The default is for the SSH server not to be sending such messages and thus an idle connection will eventually time out.

---

### Post by mbonlineuser on 2012-11-09
Thanks Lars but this is what I don't understand, a normal test user is logged out after the interval but root is not?

---

### Post by Lars Noodén on 2012-11-09
> **mbonlineuser said:**
> Thanks Lars but this is what I don't understand, a normal test user is logged out after the interval but root is not?

I have a few instances of ssh running but can't get them to time out.  I even have ClientAliveInterval set to 0 on the server.  Though I have seen that problem of timeout on other systems in the past.

---

### Post by CharlesA on 2012-11-09
> **Lars Noodén said:**
> I have a few instances of ssh running but can't get them to time out.  I even have ClientAliveInterval set to 0 on the server.  Though I have seen that problem of timeout on other systems in the past.
Mine will time out after somewhere between 30 and 60 minutes, if I leave them idle. I usually run htop or top if I am working on something thru a tunnel, so the original session doesn't disconnect.

---

### Post by Lars Noodén on 2012-11-09
> **CharlesA said:**
> Mine will time out after somewhere between 30 and 60 minutes, if I leave them idle. I usually run htop or top if I am working on something thru a tunnel, so the original session doesn't disconnect.

You can add ServerAliveInterval 60 to your config file in ~/.ssh/config for those particular hosts.  That should keep the session from timing out.  Though top is nice, too.

---

### Post by CharlesA on 2012-11-09
> **Lars Noodén said:**
> You can add ServerAliveInterval 60 to your config file in ~/.ssh/config for those particular hosts.  That should keep the session from timing out.  Though top is nice, too.
Thanks. I've accidentally left top or htop running and found the same session was still running the next day. O_o

---

### Post by mbonlineuser on 2012-11-10
Interesting,  does anyone know if a root login is treated any differently to a non-root login, in terms of session timeout?

---

### Post by mbonlineuser on 2012-11-13
I will mark this as solved and start a new thread about the root login to avoid thread drift.

---

