---
title: "Setting up a secure chroot"
date: 2011-06-28
forum: Security
---

### Post by rasmusson.stefan on 2011-06-28
I'm setting up this very over scaled security system on my home server. The main way in is a OpenVPN tunnel with three factor authentication(password, certificate and one-time password) =)

This I'll probably get working. But I would also like an emergency solution for the quite improbable possibility that all of theses are compromised.

My plan is to set up an SSH server with password authentication. There is only one user that can log in and that user is only allowed to shut down the server.

I was thinking that I could make a chroot jail and then somehow give the user access to the shutdown program. 

What I'm looking for is a good best practice solution how to make the jail air tight. Any ideas?

Feel free too come with different solution on the emergency shutdown and show your admiration to the rest of the security design =)

---

### Post by HermanAB on 2011-06-28
Howdy,

The short answer is that you cannot.

Chroot isn't secure, so trying to make it secure is mostly a waste of time.  The US and Canadian government don't use chroot anymore for the last 5 years or so.

---

### Post by Dry Lips on 2011-06-28
> **HermanAB said:**
> Howdy,

The short answer is that you cannot.

Chroot isn't secure, so trying to make it secure is mostly a waste of time.  The US and Canadian government don't use chroot anymore for the last 5 years or so.

Really? Have you got any references for this? 
And if chroot isn't secure, what alternatives do you have?

---

### Post by rasmusson.stefan on 2011-06-28
Ok, do you have any suggestion for other solutions to this problem? I absolutely don't need to use chroot. What do the governments use?

---

### Post by Dangertux on 2011-06-28
There are a few factors to think about here. Is it really necessary? 

If you really want best practices ; you're going to limit the amount of entry points as much as possible. Ideally choosing between the VPN or the SSH server.  Obviously the more holes you punch in something , the less secure it will be , regardless of how many stumbling blocks you put in the way. A door will always be a door.

As far as securing the chroot environment as much as possible, you can try the following. 

+ Ensure that NO processes are running in the chrooted environment as root (this is going to be tricky since you want to be able to shutdown from the chrooted environment)

+ Ensure that there is NO access to a C compiler from within the environment , as well no access to perl , ruby, python, you get the idea. 

+ Make sure that there is not a process running with the same uid inside the environment as outside of it.

+ Make sure your user cannot create directories, or files within the chrooted environment


That should at least give you a basic idea of how tough what you are trying to do is. Honestly, it's a little paranoid imo , but good luck none the less.

---

### Post by bodhi.zazen on 2011-06-28
> **Dry Lips said:**
> Really? Have you got any references for this? 
And if chroot isn't secure, what alternatives do you have?

chroot are sort of old school and do not increase security as much as more modern tools such as are available with **[COLOR=darkred][SIZE=4]selinux, apparmor[/SIZE][/COLOR]** , and / or virtualization. chroot also are relativly high maintenance as one typically needs to manually maintain the libs. 

Another alternate to a chroot is LXC, although I would not give out root access in a LXC container, and IMO, LXD is in rapid development. Personally I would consider openvz or Xen (the 3.0 kernel apparently has Xen support built in) >> LXC >> chroot.

Another alternate would be Virtualbox, KVM, or the BSD jails.

---

### Post by rasmusson.stefan on 2011-06-29
> **Dangertux said:**
> There are a few factors to think about here. Is it really necessary?


I really can't see that anything else than two-factor authentication would be necessary. Think of it more as training =)

> **Dangertux said:**
>  If you really want best practices ; you're going to limit the amount of entry points as much as possible. Ideally choosing between the VPN or the SSH server.  Obviously the more holes you punch in something , the less secure it will be , regardless of how many stumbling blocks you put in the way. A door will always be a door.


Yes only VPN would probably be the best then. But it doesn't seem to be possible to use different authentication methods per user. 

Ok, I'll play around a bit with chroot, but maybe there is a better solution than chroot if there is a need for all this customizing.

> **Dangertux said:**
> That should at least give you a basic idea of how tough what you are trying to do is. Honestly, it's a little paranoid imo , but good luck none the less.

Yes, it is very paranoid, but as I say, it is more for practice.

---

### Post by rasmusson.stefan on 2011-06-29
I'll check out selinux and apparmor.

> **bodhi.zazen said:**
> Another alternate would be Virtualbox, KVM, or the BSD jails.

I guess virtualization would would be quite secure but how could you shutdown the host machine from the guest vm?

---

### Post by bodhi.zazen on 2011-06-29
> **rasmusson.stefan said:**
> I guess virtualization would would be quite secure but how could you shutdown the host machine from the guest vm?

lolwut ?

This is a thread about "setting up a secure chroot" - it would be an insecure chroot that allowed access to the host, shutdown or otherwise. By definition a "secure chroot" denies access to the host (in theory at least).

To shutdown the host from a remote location you need remote access, I personally would use ssh + keys and disable password authentication.

The weak link in your setup is password authentication. 

ssh + keys + selinux/apparmor would be much more secure without any need for VPN or a chroot.

ssh + keys with a forced command (shutdown) is probably what you want.

---

### Post by rasmusson.stefan on 2011-06-30
After reading about forced commands. I would say this is the absolute best solution to my problem... If, it could be applied to a user authenticating with password. Password authentication is something I need on the function.

---

### Post by Dry Lips on 2011-06-30
I don't mean to hijack Stefans thread or anything, (tjänare!) but would the general advice
 of using apparmor instead of chroot also apply to creating chrooted sftp-only accounts?
 

 See for instance this link:
 [http://www.howtoforge.net/chrooted-ssh-sftp-tutorial-debian-lenny](http://www.howtoforge.net/chrooted-ssh-sftp-tutorial-debian-lenny)

---

### Post by bodhi.zazen on 2011-06-30
> **Dry Lips said:**
> I don't mean to hijack Stefans thread or anything, (tjänare!) but would the general advice
 of using apparmor instead of chroot also apply to creating chrooted sftp-only accounts?
 

 See for instance this link:
 [http://www.howtoforge.net/chrooted-ssh-sftp-tutorial-debian-lenny](http://www.howtoforge.net/chrooted-ssh-sftp-tutorial-debian-lenny)

Well, the problem with ftp is that it is insecure. It is popular with web developers, and the result is cracked websites.

IMO you should use ssh.

I think a better question is what do you hope to achieve by using a chroot ? You can then determine the best tool, ssh (scp), LXC , apparmor, etc.

---

### Post by bodhi.zazen on 2011-06-30
> **rasmusson.stefan said:**
> After reading about forced commands. I would say this is the absolute best solution to my problem... If, it could be applied to a user authenticating with password. Password authentication is something I need on the function.

You would have to script a login, but, I do not understand why you insist on password authentication.

I highly advise you use a key, it is not that hard, and if needed, make the key available over https with password authentication to download, lol.

---

### Post by Dry Lips on 2011-06-30
> **bodhi.zazen said:**
> Well, the problem with ftp is that it is insecure. It is popular with web developers, and the result is cracked websites.

IMO you should use ssh.


SFTP=**SSH File Transfer Protocol, **right? I think I wrote sftp, not ftp. :wink:

---

### Post by rasmusson.stefan on 2011-06-30
> **bodhi.zazen said:**
> You would have to script a login, but, I do not understand why you insist on password authentication.

I highly advise you use a key, it is not that hard, and if needed, make the key available over https with password authentication to download, lol.

My thought is that if my other means of authentication gets compromised. I can do a shutdown of the server without any specific hardware. I could of course memorize the key... but I don't think that would stick for very long.

Maybe the key over https solution could be a solution. A bit hacky though.

---

### Post by bodhi.zazen on 2011-06-30
> **rasmusson.stefan said:**
> My thought is that if my other means of authentication gets compromised. I can do a shutdown of the server without any specific hardware. I could of course memorize the key... but I don't think that would stick for very long.

Maybe the key over https solution could be a solution. A bit hacky though.

memorize the key ???

Just checking, do you know what a ssh key is ?

---

### Post by rasmusson.stefan on 2011-06-30
> **bodhi.zazen said:**
> memorize the key ???

Just checking, do you know what a ssh key is ?

Yepp, I do, that's why I think it is hard to memorize =)

---

