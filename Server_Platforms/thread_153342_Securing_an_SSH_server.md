---
title: "Securing an SSH server"
date: 2006-03-31
forum: Server Platforms
---

### Post by cleverselfreferentialname on 2006-03-31
A few friends have logins on my system, we have a system of SSHing into my box and then running irssi and connecting to a local IRC server, in order to chat securely. A few of these fellows I don't trust, and I would like to prevent them from pulling a perl -e 'fork while 1' on me, while all the while hardening SSH and general ubuntu security. Any help would be appreciated.

---

### Post by ispmarin on 2006-03-31
Don't know about the irc thing, but to "harden" the ssh connection, you can put on /etc/sshd_config:
comment 
Protocol 2,1
and put
Protocol 2 (this will permit only login via protocol 2, more secure)
Change
PermitRootLogin yes
to 
PermitRootLogin no (this will not allow remote root login)
Change
ServerKeyBits 768
to
ServerKeyBits 1024 (harden the pass)
and finally, change
X11Forwarding yes
to
X11Forwarding no (this will not allow to foward a X connection, like an X application in another computer.)

Hope it helps...

---

### Post by cleverselfreferentialname on 2006-03-31
Thanks. I had a lot of worries regarding SSH, due mainly to the fact that I heard about some issues with earlier versions. Anyone know of a way in which I can prevent people with remote logins from accessing potentially dangerous commands? I tried using Iron Bars Shell, but that caused me some serious problems.

---

### Post by kosmic on 2006-04-01
About the Forkbomb you can use the ulimit comand, with the user that has SSH login.
 
You can also use Portknocker and RSA keys authentication

---

### Post by LordHunter317 on 2006-04-01
[QUOTE=ispmarin]Change
ServerKeyBits 768
to
ServerKeyBits 1024 (harden the pass)[/quote]This won't add any security.  It's not even applicable.

The long and the short is if you don't trust someone, don't let them on your box.  Run something like SILC or an IRC server that supports SSL.

If you must let them on, set and enforce limits on resources they can use via ulimit.

---

### Post by cleverselfreferentialname on 2006-04-01
Thanks a lot, everyone. :-D Sorry for the delayed response.

---

### Post by ispmarin on 2006-04-03
From [http://www.faqs.org/docs/securing/chap15sec122.html:](http://www.faqs.org/docs/securing/chap15sec122.html:)

ServerKeyBits 1024

The option ServerKeyBits specifies how many bits to use in the server key. These bits are used when the daemon starts to generate its RSA key. 

So it will improve security on _ssh_. Like I said, I was able to help a little with ssh, not with the irc stuff.

---

### Post by LordHunter317 on 2006-04-03
[QUOTE=ispmarin]From [http://www.faqs.org/docs/securing/chap15sec122.html:](http://www.faqs.org/docs/securing/chap15sec122.html:)

ServerKeyBits 1024

The option ServerKeyBits specifies how many bits to use in the server key.[/quote]For the *empheral key in SSHv1 only.*  Which you already turned off.

> So it will improve security on _ssh_.No, it won't.

---

### Post by ispmarin on 2006-04-04
Did my research. Agreed. :rolleyes:

---

### Post by r3v3rs3pa on 2006-04-04
lordhunter317 is correct.
u can make ssh as secure as u wanna, but u are still giving them a shel on your box...

irc is old and u can find a well tested secure ircd which will support ssl.

then they have no rights on your box, but u have an encrypted network...
another thing you could look into is a waste peer to peer network, but while i have it installed, i never used it yet, and i hear there is some kinda problem with the key-sending or something, u gotta do somethin by hand

---

### Post by ubernoob on 2006-04-10
what is perl -e 'fork while 1'
and what is the security issue with that?

---

### Post by Azrael on 2006-04-10
[quote=ubernoob]what is perl -e 'fork while 1'
and what is the security issue with that?[/quote]
[http://en.wikipedia.org/wiki/Fork_bomb]("http://en.wikipedia.org/wiki/Fork_bomb")

It can be prevented by limiting the resources a user can use.

---

### Post by ubernoob on 2006-04-10
Thanks for the info. I have never heard about that before. Neat trick :D


But it is easy to avoid...

Add "ulimit -Hu 25" to /etc/profile to set a hard limit of 25 processes/user.

There is another way you can fix your problem. When a user logs on with ssh he can automaticly be sendt to a program instead of a shell. And when exiting, he will just be disconnected, so he will never get a shell. I'll try to find more info about that.

But like LordHunter317 said: "Run something like SILC or an IRC server that supports SSL" is the easiest, and most secure.

---

### Post by cleverselfreferentialname on 2006-04-11
Thanks to everyone who has posted. I appreciate your help. Just one thing, Ubernoob, are you sure that 25 will be enough for a user with a graphical environment such as myself?

---

### Post by LordHunter317 on 2006-04-11
No, probably not.

I would only set ulimits on those users who need them.

---

### Post by cleverselfreferentialname on 2006-04-11
Is there a way in which I can set the process limit for all users other than me or someone specifically?

---

### Post by ubernoob on 2006-04-14
[QUOTE=cleverselfreferentialname]Is there a way in which I can set the process limit for all users other than me or someone specifically?[/QUOTE]

I think you can add it to ~/.bash_profiles instead of /etc/profiles and take ownership of that file and prevent them from writing to it.

Anyway, you don't need many processes to stall the system. "yes >>/dev/null &" is my favourite ;) 

But if they aren't supposed to have other things than irssi, i would change ~/.bash_profiles to start irsii, and close the connection after they are done. So they will never get a shell on your system. And you should take ownership of most files in their home dir so they can't do annything there. :)

Edit: i don't use irssi myself, so i don't know how secure that is. E.g: if it is possible to run shell commands from inside irssi, the above example won't help you much.

---

### Post by windwalker78 on 2006-09-28
Hi everybody,

BTW command "ulimit -Hu 25" in /etc/profile does not solve the problem...
The problem can be solved by editing file:
/etc/security/limits.conf

Happy limiting 8)

---

