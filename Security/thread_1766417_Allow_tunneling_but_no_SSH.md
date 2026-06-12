---
title: "Allow tunneling but no SSH"
date: 2011-05-24
forum: Security
---

### Post by ricardus1867 on 2011-05-24
Hi!

I've created a user *tunnel* that is allowed to connect to the SSH daemon, but doesn't have the neccessary file permissions to execute */bin/dash*.

Tunneling (using plink) works as a charm and if I try to open a SSH session (omitting the -N switch), I get */bin/sh: Permission denied.* So far, so good...

My question is: Does that actually make sure that *tunnel* won't be able to execute any custom commands on the server? Or is there a way of doing so **without** executing */bin/dash*?

---

### Post by matt_symes on 2011-05-24
Hi

> **ricardus1867 said:**
> Hi!

I've created a user *tunnel* that is allowed to connect to the SSH daemon, but doesn't have the neccessary file permissions to execute */bin/dash*.

Tunneling (using plink) works as a charm and if I try to open a SSH session (omitting the -N switch), I get */bin/sh: Permission denied.* So far, so good...

My question is: Does that actually make sure that *tunnel* won't be able to execute any custom commands on the server? Or is there a way of doing so **without** executing */bin/dash*?

Interesting question and one that i am not sure of the answer. Try this and see what happens.

ssh user_name@computer "/bin/bash touch /home/user_name/test"

Replace user_name with the user name and see if the file is created. Please post back on that one.

Anyway, make sure root login is disabled. Make the user a non privileged user.

You could set the shell for the user as

```
/bin/false 
```

instead of 

```
/bin/sh
```

in

```
/etc/passwd
```

Kind regards

---

### Post by bodhi.zazen on 2011-05-24
Use keys with forced commands. You can disable tty ;)

There is a nice discussion on this page:

[http://oreilly.com/catalog/sshtdg/chapter/ch08.html](http://oreilly.com/catalog/sshtdg/chapter/ch08.html)

Scroll down to the forced commands section

---

### Post by ricardus1867 on 2011-05-24
Thanks to both!


@matt_symes:

*ssh user_name@computer "/bin/bash touch /home/user_name/test"* gives permission denied.

Didn't know about "/bin/false". Avoids having to play with too many file permissions. Big headache... Seems to work like a charm!


@bodhi.zazen:

That sounds a little cleaner than my approach. ;-)

But I can't seem to get it working...

I usually paste the public key in the authorization file (ssh-rsa ...), but that doesn't seem to get along with the *Command* line.

So I tried 

[I]Key tunnel.pub
Command "/bin/echo No shell for you!"[/I]

tunnel.pub being the file that PuTTgen saved (export OpenSSH key), but now it keeps asking for a password...


What am I doing wrong?

---

### Post by bodhi.zazen on 2011-05-24
Your key is probably malformed. Make sure everything is all on one line and the syntax is correct.

Also, personally, I just use no-ptty and do not bother with the echo or other scripts.

If all you need / want is tunneling, you might want to look at VPN.

---

### Post by ricardus1867 on 2011-05-24
I just used the file PuTTYgen created. It's several lines, and it starts with

*-----BEGIN RSA PRIVATE KEY-----*.

The *echo* part was just for testing...


I need more than tunneling. It's a multi-purpose server, but I want to direct all access through tunnels for encryption and authentication. I'd like to avoid having to pay for SSL certificates and it has a WebUI that permits deleting data, so no script kiddies should be invited to try brute-force attacks...


If I get it working with the *Key / Command* approach, great. But does it have any advantage over the [I/bin/false[/I] approach?

---

### Post by bodhi.zazen on 2011-05-24
That is not how you use forced commands, or at least that is not how I use them.

Forced commands go on the server, in the authorized_keys file

Each line in that file has a syntax

[command]  [Type]  [Key]  [user_name]

command is where you add your command(s)
type is the type of key
key is the key itself and is a long list if digits.
user_name is the user who can use the key.

See: [http://blog.bodhizazen.net/linux/svnssh/](http://blog.bodhizazen.net/linux/svnssh/)

You want at least no-pty , perhaps other options.

---

### Post by CharlesA on 2011-05-24
It might not be the best way to do it, but I've done this before:

Created a script that reads this:

```
read -p "Press any key to end session."
```

Then changed the shell that the dummy user uses:

```
sudo usermod -s /home/dummy/tunnel dummy

```

So if the dummy user tries to login, they get:

```
su dummy
Password:
Press any key to end session.

```

---

### Post by ricardus1867 on 2011-05-24
@CharlesA:

Interesting. But bodhi.zazen's approach has a few options I'll be using.


@bodhi.zazen:

> **bodhi.zazen said:**
> That is not how you use forced commands, or at least that is not how I use them.

Well, that's what the forced commands section of the link you posted was saying.

*For instance, you can make an incoming SSH connection run a program of your choice, instead of the client's choice. This is called a **forced command**[...]*

Maybe I read the wrong section... :confused:

Well, nevermind.


Your approach is awesome! I didn't quite figure out the svn part, so I'm working without it for the time being.

*no-pty* doesn't quite do what I want it to. It doesn't allow a shell to get created, but I still can run custom commands using

*plink -i key.ppk [email]tunnel@server.com[/email] command*.

Instead, I'll use the custom command "/bin/false", so I'll don't even have to create a separate user *tunnel*.

It even lets me decide which ports to forward and with not (on a per user basis), so I can use it as the only authentication. Before, user A could access the private area of user B using his own (A's) tunnel. So I had to set up additional passwords... :(

Well, not anymore! :D I found a tut for that in (of course) the ubuntu forums. In cae anybody else is interested, here it is: [http://ubuntuforums.org/showthread.php?t=618733](http://ubuntuforums.org/showthread.php?t=618733)

This is what I went with:

*command="/bin/false",no-agent-forwarding,no-port-forwarding,no-X11-forwarding,permitopen="localhost:81" ssh-rsa [KEY] [COMMENT]*

It works great! Thank you so much for helping me with this!

One last question: Do you know if there's any way to make the *permitopen* option take wildcards?

---

### Post by bodhi.zazen on 2011-05-24
forced commands are awesome , but yes you need to tweak and test them a bit to adjust them to your liking.

Not sure about the permitopen option , I usually configure such things server side, either with iptables or hosts.deny / hosts.allow or some such

---

### Post by matt_symes on 2011-05-25
Hi

> **bodhi.zazen said:**
> forced commands are awesome , but yes you need to tweak and test them a bit to adjust them to your liking.

Not sure about the permitopen option , I usually configure such things server side, either with iptables or hosts.deny / hosts.allow or some such

Thanks for that link Bodhi. That book is just what i have been looking to read for a while.

Kind regards

---

### Post by bodhi.zazen on 2011-05-25
> **matt_symes said:**
> Hi



Thanks for that link Bodhi. That book is just what i have been looking to read for a while.

Kind regards

You are most welcome.

---

### Post by habr on 2011-12-19
Placed /sbin/false to the user's string in /etc/passwd
In PuTTY client checked "Don't start shell or commant at all" - that helped.
Thanks for replies!

---

