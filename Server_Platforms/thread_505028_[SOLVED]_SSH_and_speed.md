---
title: "[SOLVED] SSH and speed"
date: 2007-07-19
forum: Server Platforms
---

### Post by p_quarles on 2007-07-19
This isn't a support question, but I'm curious to see if anyone has an explanation for this.

I dual-boot Windows and Ubuntu on my main desktop machine, and I administer my server via SSH. I use Ubuntu 95% of the time, but on one of those other 5% of times, I used Putty to access the server.

When I type "ssh [account@server_IP]", it usually takes a few seconds (~5-8) before I get the password prompt. In Putty, however, the prompt comes up instantaneously. After I noticed this, I installed the Linux version of Putty, and had the same result when logging in from Ubuntu. 

Anyone here know why this is? I mean, it's the same two machines, the same port, and the same protocol. So why would a graphical application like Putty log in faster than the bash command?

---

### Post by foxylad on 2007-07-19
Could be that Linux is waiting to aquire enough entropy for the random numbers SSH uses - try moving the mouse while you are waiting and see if that speeds it up. If so, Google to see how you can resolve this.

---

### Post by p_quarles on 2007-07-19
Interesting idea . . . I tried moving the mouse, but it made no difference at all.

In any case, Putty uses SSH. This means, as far as I know, that it should work exactly the same way as the terminal command. I don't get it.

AGAIN: this is not an important "help me get this working" question; just an idle curiosity question.

---

### Post by Mr. C. on 2007-07-20
The 5 second delay is most likely a DNS lookup problem.

MrC

---

### Post by p_quarles on 2007-07-20
> **Mr. C. said:**
> The 5 second delay is most likely a DNS lookup problem.

MrC
That very well may be. Is there a way to fix that? A config file to add or something?

---

### Post by Mr. C. on 2007-07-21
Well, let's verify what is happening first.

Increase the log level of your server by setting the log level variable in your sshd_config file:

sshd_config:
```
LogLevel VERBOSE
```

Restart the server after changing the value:

```
sudo /etc/init.d/ssh-server restart
```

Next, do a back to back test of your ssh client and putty client, and examine the differences in your auth.log lof file.  If you see no differences, increase the log level higher, using the increasingly higher debug values of DEBUG, DEBUG1, DEBUG2, and DEBUG3.

You are likely to notice different methods of authentication being employed by the two clients.  Let us know what you find.

MrC

---

### Post by p_quarles on 2007-07-21
Thanks for the help.

I had to go up to DEBUG2 before I found any difference (other than "OpenSSH4.3" vs "PuTTY_Local"). Anyway, the auth.log is giving me this difference:

In putty, it logs```
debug2: mac_init: found hmac-sha1
```
In SSH, I get ```
debug2: mac_init: found hmac-md5
```
Without knowing what this means, I'm guessing it refers to a difference in protocol of some type. That said, this is logged *after* log in is complete, so I'm not sure it would explain much. (?)

I'm going to tinker with my ssh clients and see if I can get them to produce higher level logs on the desktop itself.

---

### Post by p_quarles on 2007-07-21
I think I figured it out. It looks like putty isn't configured to compare the server's key with the "known hosts" file. 

I'm pretty sure this is the case. I did a reinstallation on the server yesterday (didn't like Ubuntu's default LAMP setup). On my first attempt to compare putty and ssh this morning, the openssh client warned me that the key didn't match, and I had to update that manually. Never got such a warning from putty. 

Correct me if I'm wrong, but I don't think this is a security issue, since I never log into the server from outside the LAN. Plus, the server and the router are both configured to assign the server with a static address.

---

### Post by henryhynd on 2007-07-21
now i'm a noob with a grand total of about 6 months experience and a whole 10 beans!

So from my lowly position, i don't wanna step on anyone's shoes or anything... (oh yeh and tell me if i'm wrong/just plain stupid) but I use putty in a similar fashion (windows - ubuntu server) and it seems to me that because all of the connections happen in the background (ie you click on a saved template "my_linux_box" in the saved sessions box) and you only get your user/pass requests once the connection has been made, putty actually has less to do when it checks your password (or before) as openssh would have to connect & pass the username then wait for the ssh server to respond.

maybe this is issue is a matter of order, not actually a problem.

but then, i'm a noob!

is in interesting issue tho, let me know what you reckon.

henry

---

### Post by p_quarles on 2007-07-21
I don't think it has anything to do with running in the background. I don't use a template, I open the terminal and ```
putty {lan-IP-address}
```
Like I said in my last post, I'm almost certain that the difference is that OpenSSH, by default, performs a "handshake" with the server, where it requests its key, compares it to the ones listed in the known hosts file, and then connects if they match. PuTTY, on the other hand, doesn't know where my known hosts file is, so it doesn't go through that authentication step.

---

### Post by Mr. C. on 2007-07-21
Putty stores keys in the registry.  See:

[http://the.earth.li/~sgtatham/putty/0.60/puttydoc.txt](http://the.earth.li/~sgtatham/putty/0.60/puttydoc.txt)

and search for **host keys**.

I'm a little surprised if you changed your host keys, and putty said nothing about this change.

The difference you see (hmac-sha1, hmac-md5) are two forms of message authentication code - they use your secret key and other data to both authenticate and verify data integrity.  These would not cause your delays.

Nice detective work.
MrC

---

### Post by p_quarles on 2007-07-21
I'm sure it does that in Windows, but this is the Linux version of putty we're talking about. I discovered this effect in Windows, yes, but the speed differential is the same in Linux.

It may have asked me to add the host the first time I used it. I don't remember, honestly. In any case, the authentication settings in putty are set to attempt to use "pageant" and attempt to use "keyboard interactive (SSH-2)". The "private key file" line is blank.

I'm sure it's doing some kind of authentication, but whatever the case, the slowdown with openssh seems to involve how it looks up the keys. So, at least now I know where to look if I want to speed it up.

Thanks again for your help.

---

### Post by Mr. C. on 2007-07-21
You'd mentioned both version of putty, so I wasn't sure which we were talking about.  There's an bug on the putty buglist:

[http://www.chiark.greenend.org.uk/~sgtatham/putty/wishlist/hostkey-rekey.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/wishlist/hostkey-rekey.html)

> What PuTTY should do if a different key for the host has turned up in
the cache in the meantime is left as an exercise for the reader.

I don't know where putty stores its data in the Linux port, but it is common for cross-platform apps to use standard Windows registry-conversion routines to store items in a prefs file (probably in a dot file somewhere).

Once my authorized keys and known_hosts files were setup correctly I have no delays with my openssh ssh client connecting to the Ubuntu ssh server.

MrC

---

### Post by p_quarles on 2007-07-21
> Once my authorized keys and known_hosts files were setup correctly I have no delays with my openssh ssh client connecting to the Ubuntu ssh server.
Good to know. I'll look into the configuration of the openssh client. If I can't figure it out, I'll be back. :)

---

### Post by p_quarles on 2007-07-21
Okay, I'm back. This time, I was looking for errors in the client app, which I was able to get by running ```
ssh -vvv user@lan-IP-address
```
The vast majority of actions go through without a problem. This, however, is what it says while it slows down: ```
debug2: fd 3 setting O_NONBLOCK
debug1: An invalid name was supplied
Cannot determine realm for numeric host address

debug1: An invalid name was supplied
A parameter was malformed
Validation error

debug1: An invalid name was supplied
Cannot determine realm for numeric host address

debug1: An invalid name was supplied
A parameter was malformed
Validation error
```
It proceeds after a few seconds, and then authenticates with the key and user password. 

I looked in the config files for both the client and the server daemon, and as far as I can tell there is no setting that looks for name or host based authentication. 

I'm going to try to  track down the putty configuration file, to see if there are any clues there. In the meantime, any insight into what is causing this error message is appreciated.

---

### Post by Mr. C. on 2007-07-21
Now try:

```
ssh -o "VerifyHostKeyDNS no" -vvv user@lan-IP-address
```

MrC

---

### Post by p_quarles on 2007-07-21
Didn't change a thing. Same delay, same error message.

---

### Post by Mr. C. on 2007-07-21
Ok, that's fine.

A "realm" is related to Kerberos, so it may be trying to resolve the Kerberos realm.  Is Kerberos authentication enabled in sshd_config ?

Additionally, disable IPv6 by changing your AddressFamily to inet ( in both ssh_config and sshd_config also ).

Restart the server of course.

MrC

---

### Post by p_quarles on 2007-07-21
Okay, changed AddressFamily to inet in ssh_config, but didn't find the line in sshd_config. And made sure that all Kerberos authentication was disabled. Still no change.

I then *added *the AddressFamily inet line to sshd_config, restarted the server, reconnected, and . . . same thing. 

Urgh. Thanks for your continuing help. Like I've said, this is more an annoyance than a problem, but I really like knowing how to fix things when they break. 

I was never able to find a text-based config file for putty, and based on their documentation, I'm guessing it doesn't have one. The file I did find wanted to open in ClamTK. So, next, I'm going to get myself yet another ssh client from the repos and see how that behaves. After I get some sleep. 

In the meantime, I'm still somewhat convinced that the problem is with the client configuration, so here's ssh_config:```
# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   BatchMode no
#   CheckHostIP yes
AddressFamily inet
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no
```
Anything jump out here?

---

### Post by p_quarles on 2007-07-22
I was never able to get the other clients I tried working at all, so I tried something different, that kind of throws a wrench in all of my theories.

I installed openssh-server on my desktop, so that I could connect "back" to it from the server. The results: the handshake/connection operation was much faster. That's partly to be expected, since the desktop is certainly the faster machine. Running the ssh client from the server in verbose mode produced messages nearly identical to those I posted above . . . but it slowed down in a completely different place. 

In other words, it still gave me the "Could not determine realm for numeric host address" bit, but sped right past that and slowed down at a later step. 

Ssh_config on the server is all defaults; same with sshd_config on the desktop, for the brief time I had it installed. The only non-default settings I have on the server's sshd_config are to disallow root login and disable X forwarding. 

Of course, I also realize that by talking about installing a server on my desktop, and then logging in from my server, I may have taken this debugging process past the point where any written communication about can be very clear. ;)

---

### Post by Mr. C. on 2007-07-23
I am still pretty certain this is a DNS timeout issue.

When there is one nameserver directive in /etc/resolv.conf, the timeout is 5 seconds, which exactly matches your description. 

Some users will add incorrect domain names in their resolv.conf files, thinking that places them in such a domain, and not realizing that the system resolver will attempt to query the root name servers to find such a name, and DNS timeouts occur, slowing down various networking activities that required DNS name services.

Anyway, hope you narrow it down,
MrC

---

### Post by walmartshopper67 on 2007-07-23
My brother and i had this problem with our Ubuntu boxes as well, to fix it, we commented out these lines:

```


# SendEnv LANG LC_*
# HashKnownHosts yes
# GSSAPIAuthentication yes
# GSSAPIDelegateCredentials no

```

Worked for us.

---

### Post by p_quarles on 2007-07-23
@walmartshopper67: That did the trick. Thanks so much. 

@Mr. C: I never did anything with resolv.conf. The speed issue is solved, but I'll take a look at that anyway to make sure it's good. 

Thanks everyone.

---

### Post by Mr. C. on 2007-07-23
Great, glad ist solved.

I should have mentioned earlier that GSSAPI in sshd implies Kerberos; when you said earlier that Kerberos authentication was disabled, I took that at face value.  The GSSAPIAuthentication default is **no**, so someone/thing enabled it.

MrC

---

### Post by p_quarles on 2007-07-23
It's disabled in in sshd_config, but it was on in the client's config file. 

I obviously should have done a little more research about kerberos before making that statement. :oops: 

As for the default, I've installed Feisty Fawn twice on my desktop and once on my laptop, and have experienced the same slowdown with the default ssh client config. So, I dunno.

---

