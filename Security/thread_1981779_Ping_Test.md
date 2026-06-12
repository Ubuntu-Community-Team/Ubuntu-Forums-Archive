---
title: "Ping Test"
date: 2012-05-17
forum: Security
---

### Post by WyndSayl on 2012-05-17
This has been asked probably countless times. And for all the searching on this forum and other sites that have popped up I seem to be unable to find something that works.

Call me paranoid or whatever but how does one shut off the ping test. Going to GRC gives me a fail because of the ping being answered.

Using 10.04LTS. Just everyday desktop use. 

Using the ufw as firewall and all is fine until the ping test.

---

### Post by codemaniac on 2012-05-17
> **WyndSayl said:**
> This has been asked probably countless times. And for all the searching on this forum and other sites that have popped up I seem to be unable to find something that works.

Call me paranoid or whatever but how does one shut off the ping test. Going to GRC gives me a fail because of the ping being answered.

Using 10.04LTS. Just everyday desktop use. 

Using the ufw as firewall and all is fine until the ping test.

```
echo 1 >/proc/sys/net/ipv4/icmp_echo_ignore_all
```
disables ping responses in your system .

```
echo 0 >/proc/sys/net/ipv4/icmp_echo_ignore_all
```

to ebable it .

---

### Post by CharlesA on 2012-05-17
Disabling ping doesn't do jack for security. There are ways to tell if a host is up even when it does not respond to pings.

The GRC site is a decent port scanner, but it is made to sell security software.

---

### Post by codemaniac on 2012-05-17
> **charlesa said:**
> disabling ping doesn't do jack for security. There are ways to tell if a host is up even when it does not respond to pings.

The grc site is a decent port scanner, but it is made to sell security software.
+1 .

WyndSayl
Is there any specific reason , you want to turn off ping requests ?

---

### Post by WyndSayl on 2012-05-17
echo 1 >/proc/sys/net/ipv4/icmp_echo_ignore_all
Gives me Bash then echo 1 >/proc/sys/net/ipv4/icmp_echo_ignore_all:Permission Denied.

I've tried other scripts and can't do it.

I may be a bit of a noob but I get the sudo command.

As to the question of why do I want to shut it off?

Well, like I said in my op call me paranoid. And maybe it's a windows leftover but I want to be as stealthy as possible and a ping reply gives whoever is sniffing a response so to be as secure as possible.

Plus now I have gotten very curious as can it even be done.

BTW-Thanks for the responses so far.

---

### Post by matt_symes on 2012-05-17
Hi

```
echo 1 | sudo tee /proc/sys/net/ipv4/icmp_echo_ignore_all
```

...but listen to CharlesA here.

Kind regards

---

### Post by CharlesA on 2012-05-17
> **matt_symes said:**
> [SIZE=2]...but listen to CharlesA here.[/SIZE]

Thanks. ;-)

The GRC site can be misleading cuz if you have a router, it will respond to pings unless you tell it otherwise.

As a sidenote: It is usually better to block pings via a firewall but that is another can of worms.

---

### Post by Cheesemill on 2012-05-17
The site isn't pinging your computer, it's pinging your router.

You would have to go to the admin page of your router and switch of ping reply (also called echo request) there instead.

---

### Post by codemaniac on 2012-05-18
> **WyndSayl said:**
> echo 1 >/proc/sys/net/ipv4/icmp_echo_ignore_all
Gives me Bash then echo 1 >/proc/sys/net/ipv4/icmp_echo_ignore_all:Permission Denied.

I've tried other scripts and can't do it.

I may be a bit of a noob but I get the sudo command.

As to the question of why do I want to shut it off?

Well, like I said in my op call me paranoid. And maybe it's a windows leftover but I want to be as stealthy as possible and a ping reply gives whoever is sniffing a response so to be as secure as possible.

Plus now I have gotten very curious as can it even be done.

BTW-Thanks for the responses so far.

Yes you need administrative privileges to run the above command .
add sudo as prefix to the command .

---

### Post by CharlesA on 2012-05-18
sudo doesn't work with redirects by the way.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

The command Matt posted would work fine.

---

### Post by codemaniac on 2012-05-18
> **CharlesA said:**
> sudo doesn't work with redirects by the way.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

The command Matt posted would work fine.

Thanks CharlseA for the enlightenment.

---

### Post by WyndSayl on 2012-05-18
To the response of why bother because there are ways to sniff other than the pinging? Anything wrong with being secure as possible? That's what I'm trying to accomplish.

And so far no luck with trying several more scripts plus what has been suggested here.

---

### Post by Cheesemill on 2012-05-18
Have you turned of Echo Request in your router yet?

---

### Post by CharlesA on 2012-05-18
> **WyndSayl said:**
> To the response of why bother because there are ways to sniff other than the pinging? Anything wrong with being secure as possible? That's what I'm trying to accomplish.

And so far no luck with trying several more scripts plus what has been suggested here.
The point is turning ping off does not increase your security.

It may be security thru obscurity, but if someone really wanted in, they can find a way in even with ping disabled.

---

### Post by WyndSayl on 2012-05-20
So, take this how you want.

Turning it off is no big deal huh? If someone wants to get in then they will, right?

So, what's the point of a firewall anyway then eh?

Well, go try something else somewhere else then.

---

### Post by CharlesA on 2012-05-20
Firewalls are there to filter traffic based on rules. They can help limit access via IP, port or user.

Check out this thread:
[http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177)

---

### Post by CharlesA on 2012-05-20
Firewalls are there to filter traffic based on rules. They can help limit access via IP, port or user.

Check out this thread:
[http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177)

---

### Post by matt_symes on 2012-05-20
Hi

> **WyndSayl said:**
> So, take this how you want.

Turning it off is no big deal huh? If someone wants to get in then they will, right?

So, what's the point of a firewall anyway then eh?

Well, go try something else somewhere else then.

How do you think disabling ping will increase your security ?

Most people use ping to see if a host is up and to determine if there is a route to that host, although ICMP itself may have some exploits.

This is different than securing a box. 

Nobody in this thread has ever stated that having a firewall is irrelevant and, on a server, should be mandatory along with other security measures.

The "security thru obscurity" method of disabling ICMP raised by CharlesA removes a way to see if a box is up and reachable; a way to map a network. There are other methods to determine that though.

This has no real impact on securing that box.

It's just like changing the port SSH uses.

I think, maybe, your mixing two issues here.

Kind regards

---

