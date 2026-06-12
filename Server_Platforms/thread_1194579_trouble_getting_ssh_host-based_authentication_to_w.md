---
title: "trouble getting ssh host-based authentication to work"
date: 2009-06-22
forum: Server Platforms
---

### Post by anonmars on 2009-06-22
Hello,

I am trying to get host-based authentication to work between two Ubuntu 9.04 Server systems so any user can ssh without password between server1 and server2.

I was able to get the public key authentication working (on per user basis) with no trouble at all.

For getting the host-based authentication I basically followed these short instructions:
[https://wiki.systemsx.ch/display/ITDOC/OpenSSH+hostbased+authentication+HOWTO](https://wiki.systemsx.ch/display/ITDOC/OpenSSH+hostbased+authentication+HOWTO)

The user exists on both servers (and ssh-ing with user-specific keys works fine).

However, when I try to connect as some random user, e.g. ssh randomuser@server2 it fails. Turning on verbose basically says (under the host-based authentication section) that it ran out of keys to try. I took /etc/ssh/ssh_host_rsa_key.pub (and the dsa pub) keys on server1 and put it in /etc/ssh/ssh_known_hosts on server2 (along with the other instructions outlined in that link above).

Can anyone see anything obvious that I've missed?

Thanks.

---

### Post by windependence on 2009-06-23
You cannot connect to a key based ssh server unless you have the private key so therefore you won't be able to connect as just any old user. Any user who connects must have the key, otherwise what's the point? If that were the case, just anyone could log in to your server.

-Tim

---

### Post by anonmars on 2009-06-23
> **windependence said:**
> You cannot connect to a key based ssh server unless you have the private key so therefore you won't be able to connect as just any old user. Any user who connects must have the key, otherwise what's the point? If that were the case, just anyone could log in to your server.

-Tim
But my understanding was that with host-based authentication the two hosts could be setup to trust each other (on a host level rather than user). So with the steps I've done server2 trusts server1, as well as the users on server1 just as though they were users on its own system (and indeed, would treat them as such if the same user exists on both systems). I haven't setup server2 to trust just "any old person" on the Internet.

server1 does have the private key for the public key that I put in server2's /etc/ssh/ssh_known_hosts file, etc. 

Thanks.

---

### Post by Bachstelze on 2009-06-23
Watch your [font="monospace"]shosts.equiv[/font] on the server. If you only have the hostname of the client in it, user [font="monospace"]john[/font] on the client will be allowed to connect *only* as user [font="monospace"]john[/font] on the server. There is no way to allow any user on the client to connect to any account on the server using only the global [font="monospace"]shosts.equiv[/font] file. A user who wishes to let everyone from a given client access his account on the server would put this into his [font="monospace"]~/.shosts[/font]:

```
wild (,,)

client.domain.org @wild
```

Of course, for this to work, the server must read users' [font="monospace"]~/.shosts[/font] files, i.e. [font="monospace"]IgnoreRhosts[/font] must be set to [font="monospace"]no[/font] in the server config.

---

### Post by anonmars on 2009-06-23
> **HymnToLife said:**
> Watch your [font="monospace"]shosts.equiv[/font] on the server. If you only have the hostname of the client in it, user [font="monospace"]john[/font] on the client will be allowed to connect *only* as user [font="monospace"]john[/font] on the server. 

Excellent. This is what I want. I'm managing the passwd, group, and shadow files between server1 and server2, so john is the same john on both systems.

I actually have it working now except only if I disable strict host key checking on the client (something I don't want to do). I put the public key of server2 in /etc/ssh/ssh_known_hosts file... but is that the right one? What file is the global file that is checked for host key verification?

Thanks.

---

### Post by Bachstelze on 2009-06-23
> **anonmars said:**
> I actually have it working now except only if I disable strict host key checking on the client (something I don't want to do). I put the public key of server2 in /etc/ssh/ssh_known_hosts file... but is that the right one? What file is the global file that is checked for host key verification?

This is the right file. Are you saying hostbased authentication doesn't work anymore when you disable strict host cheking on the client?

---

### Post by anonmars on 2009-06-23
> **HymnToLife said:**
> This is the right file. Are you saying hostbased authentication doesn't work anymore when you disable strict host cheking on the client?
When I disable strict checking it does work. When strict host key checking IS enabled, it does not work. I'd like to have it enabled.

---

### Post by anonmars on 2009-06-23
> **anonmars said:**
> When I disable strict checking it does work. When strict host key checking IS enabled, it does not work. I'd like to have it enabled.
Hmm.. so I was seeing this:

No RSA host key is known for machine.mydomain.com and you have requested strict checking.
Host key verification failed.

But when I add *.mydomain.com to the beginning of the ssh-rsa line in /etc/ssh/ssh_known_hosts on server1 then it works. Sweet!

FYI- I found these two docs the most helpful (from my Googling around):

[http://www.clusterresources.com/pipermail/torqueusers/2005-November/002424.html](http://www.clusterresources.com/pipermail/torqueusers/2005-November/002424.html)

[http://www.securityfocus.com/infocus/1806](http://www.securityfocus.com/infocus/1806)

---

### Post by Bachstelze on 2009-06-23
```
me@wakaba ssh % ssh aoba
No DSA host key is known for aoba and you have requested strict checking.
Host key verification failed.
```

If that's the error message you get, it's a different issue. Here's how to get rid of it:

First, I get the host DSA key of aoba:

```
me@aoba ssh % cat /etc/ssh/ssh_host_dsa_key.pub
ssh-dss AAAAB3NzaC1kc3MAAACBAPjBzDB3TmtlJGhbodpMnKJYKaX4kdwMG2ZXtVGLbI4Xu/8tytam/YFKrEWvyxpqIbnt0hAJOQiTleytko/mV6FJoTMHFsAgbYIjVu4Th75LgDVLuf1YRiAyQHJkPDLybw/9Bw8MFZLRlvsR6aYRPAB7Ev3RXE4by2jMeGuE2IfpAAAAFQCUSM7btSrTmZ2EI8W27+leKZJcCQAAAIATXgXbdfIhLmAGmL3bOB6HGC2rl1lwfhtnT3DJJOcP5f6Mcy76cU7t9sVbdEtVSgvdy9Tz7AEqNTR+H349GazfC5+pBRKg3RfBRwb7jPq5OIso3gN1YKp4R0mxfXVDdNtMTI5eeilD9NHmAjaoSQiakCoFn4z1HtCe0aDvJSAR+wAAAIAVJv648Ttg/BtJCzEpLN43gSABmH9qJjF0eRbOW9q93ofa6OJj/varGxEjFYE07upbnYeq2QS5D7FS+QIxaEX9i7ZT1VVJTwu2kGx2oLSxrBnMlZlajavz9uyncTzaU3o3YOAUJms35q5oNyjxfVkykHfGrl5pMRAUCEpuUx2ZtA== root@aoba.mydomain.org
```

And I add it to my [font="monospace"]~/.known_hosts[/font] on wakaba:

```
me@wakaba ssh % cat >> ~/.ssh/known_hosts
aoba ssh-dss AAAAB3NzaC1kc3MAAACBAPjBzDB3TmtlJGhbodpMnKJYKaX4kdwMG2ZXtVGLbI4Xu/8tytam/YFKrEWvyxpqIbnt0hAJOQiTleytko/mV6FJoTMHFsAgbYIjVu4Th75LgDVLuf1YRiAyQHJkPDLybw/9Bw8MFZLRlvsR6aYRPAB7Ev3RXE4by2jMeGuE2IfpAAAAFQCUSM7btSrTmZ2EI8W27+leKZJcCQAAAIATXgXbdfIhLmAGmL3bOB6HGC2rl1lwfhtnT3DJJOcP5f6Mcy76cU7t9sVbdEtVSgvdy9Tz7AEqNTR+H349GazfC5+pBRKg3RfBRwb7jPq5OIso3gN1YKp4R0mxfXVDdNtMTI5eeilD9NHmAjaoSQiakCoFn4z1HtCe0aDvJSAR+wAAAIAVJv648Ttg/BtJCzEpLN43gSABmH9qJjF0eRbOW9q93ofa6OJj/varGxEjFYE07upbnYeq2QS5D7FS+QIxaEX9i7ZT1VVJTwu2kGx2oLSxrBnMlZlajavz9uyncTzaU3o3YOAUJms35q5oNyjxfVkykHfGrl5pMRAUCEpuUx2ZtA== root@aoba.mydomain.org
```

And voilà!

```
me@wakaba ssh % ssh aoba
[...]
me@aoba ~ %
```

---

