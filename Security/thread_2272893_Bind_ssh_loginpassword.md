---
title: "Bind ssh login/password"
date: 2015-04-09
forum: Security
---

### Post by nabz0r on 2015-04-09
Hi guys,

I am new to Linux so please bare with my questions. :P 
I was wondering if it is possible to bind ssh login and password to a key and use that key to login to the ssh server. This is possible when using SecureCRT. I can't use public/private key because it is out partners server and this is not possible. 

It is not like I can't type my username/pass it is that I want to do it faster instead of typing password every time I login and I do login to that server like 100+ every day. 

Thank you!

---

### Post by TheFu on 2015-04-09
ssh-keygen
then use ssh-copy-id

Passwords are so, so, so .... 1993.
[http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)

I've never heard of anyone disabling key-based authentication anywhere. Don't think its possible with UNIX.  How do you know this isn't possible?

Of course, you can use expect or keepass to "type" things for you, but this isn't very secure.  ssh-keys are 1000x better.

---

### Post by Lars Noodén on 2015-04-09
In addition to that, there is [ssh-add](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh-add.1.html) which can load a key into the agent so you do not need to retype the passphrase for each login.  Ubuntu has the agent up and running automatically so you only need to load the key once per desktop login session and then you can log in repeatedly to the remote computer.

---

### Post by matt_symes on 2015-04-09
Hi

> I can't use public/private key because it is out partners server and this is not possible.

You cannot use ssh key authentication with the server because of business policy ?

If not, I would suggest talking to your partners and trying to get them to enable it for you and use the tips from the last two posts.

Would you be keeping your password on the USB stick unencrypted ? That may be a security risk.

I know you can use the pam_usb module to log into Linux but i'm not sure you can use it with passwords with ssh.

Kind regards

---

### Post by nabz0r on 2015-04-09
Thank you guys for the replies! 

Ok maybe I should explain more.. We have L2L VPN and we use the linux server to login into their Cisco devices for various of things using tacacs+ with personal logins. Anyway, for login to this linux server we all have one pass and username and this user and pass I want to bind to a keyboard key or if it possible do a little script to login without typiong ssh -l yaya 1.1.1.1 and the type my phrase.

In my SecureCRT I have an autologin to this server and when I am logged in I use ctrl+§ to login with my personal username/password into their Cisco devices. I want to achieve this in Linux, since I am using Linux and want to learn more and more. 

I hope it is more clear now. :)

---

### Post by TheFu on 2015-04-10
Anything that can be typed can be put into a keyboard macro. If a password is involved, this is not very secure at all. I use openbox as my WM, so keyboard macros are stored in that config file. There is probably some GUI way to maintain it, but I've never bothered. I have about 10 macros setup and tied to different keyboard chords.  Anyway - please don't be "that guy" who causes a backdoor by putting your password into a file.

Also, if you need an interactive script that pauses and fills in stuff, the old school way is with a program called "expect" - before ssh happened, we used **expect** to maintain passwords across lots of systems.

Of course, the new kids have created typing tools like auto-hot-key for Linux, so those exist as well.

Or perhaps a good password manager with auto-type will work?  KeePassX is what I use.  It will fill in userid{tab}password{enter} - or you can customize the keys per entry - perhaps adding a delay, for example.

And you can always put stuff into a script or alias.  Don't forget that ssh has a config file stored in ~/.ssh/config - that file can provide fill in userid, aliases for hosts, change the port used, etc.  I like it because it provides documentation for all my remote logins.

So you have many options.

---

