---
title: "SFTP with GUI?"
date: 2007-05-14
forum: Server Platforms
---

### Post by dreamie on 2007-05-14
Hi!

Just installed my first Linux system at home, and it is an Ubuntu 6.06 :-)

I might be swearing in church here but I am after a sftp (secure ftp over ssh) with a nice admin-GUI (or web based admin). I am not that fond of config-file adminitration, atleast not if I can avoid it...

I have looked at proftpd, vsftpd, pure-ftpd, MySecureShell SFTP, and jscape

jscape seem to have all I need, but it is commercial and I am a simple home user.

The other projects seem to lack SSH capability except for MySecureShell SFTP, but it's presentation doesn't give much confidence (although it may just be the poor spelling). OR am I mistaking? Is it possible to run proftpd with SSH?

This is what I have in mind:
- Noone should be able to sniff users login/password
- Noone should be able to sniff contents of data beeing transferred
- Users are mainly friends, but I want to make sure they can't access the system files etc.So they should be restricted to ftp-dirs
- Group privileges (powerusers and users etc.)
- Download area is readonly
- Upload area is readonly except for your own files.
- Downloading could require a certain amount of uploading
- Graphical interface for setting up users, directories and privileges...

Given the server should be easily accessed, not requiring very special operation on the client side
- Is SSH (SFTP) the best choice when it comes to security? I don't think Public-Private key sharing is an option.
- Am I wrong to say SSL is used to protect the transferred data, or does SSH fix that as well? (Now you know I am a total newbie to this ;-) )

Any ideas, comments are most welcome!

Best regards,

 Peter

---

### Post by craigp84 on 2007-05-14
Hi Dreamie,

Sftp is great, but it's pretty lightweight, it's basically just a (not too powerful) FTP interface bolted onto SSH.

From what you suggest below, you'd probably be better off with full-fat FTP over SSL. This can optionally be setup to encrypt the control connection, the data connection, or both. It's normally setup to encrypt everything (both connections).

To my mind, it doesn't make all that great a difference which FTP server you choose, most of the big names (vsftpd, proftpd, pure-ftpd) offer SSL support. Just pick one and go for it, if it turns out to be a dead end for you, for whatever reason, just pick another - they're all just a "sudo apt-get install" away, or a "sudo dpkg --purge <pkgname>" to completely remove all trace of them again.

Some of the open source stuff that's available in this area is nothing short of outstanding, i can't really see much point in parting with cash for a paid for version.

If your users are windozers, you may find it's easier for them to find a good FTP client capable of FTP over SSL, than to find a good SFTP client (not to say that there aren't any, just that i don't know of them).

Hope this helps,

Craig

---

### Post by elst on 2007-05-14
SSH is pretty much the gold standard WRT security, and automatically encrypts connections, but key-based authentication is part of what makes it so strong. If you make an SSH or FTP service publicly available with username+password security then you need to enforce good passwords, as SSL only protects against interception, rather than username/password guessing programs. If you can implement a maximum number of login attempts per connection then it's probably well worth doing.

---

### Post by Seq on 2007-05-14
> **craigp84 said:**
> If your users are windozers, you may find it's easier for them to find a good FTP client capable of FTP over SSL, than to find a good SFTP client (not to say that there aren't any, just that i don't know of them).

This is out of the scope of the question (Server-side handling of this stuff on Linux), but thought I would mention WinSCP can handle scp and sftp connections with a decent GUI.

---

### Post by dreamie on 2007-05-14
> **elst said:**
> SSH is pretty much the gold standard WRT security, 
So you would say that SSH is more secure than SSL?

> **elst said:**
> If you can implement a maximum number of login attempts per connection then it's probably well worth doing.
This should be easily achieved using fail2ban right?

I think I will try proftpd, it seems to have a graphical admin module. I'll get back to you as soon as I have it up and running.

Thanks for the input!

---

### Post by craigp84 on 2007-05-14
> So you would say that SSH is more secure than SSL?


It's a tough one to put a metric on. Probably easier to say both are excellent, and at this point in time, there is no good evidence that one is better than the other.

> This should be easily achieved using fail2ban right?

Normally you don't need to go as far as that, the server will normally have options to deal with this. Although chucking in fail2ban may be an ok idea too.

-c

---

### Post by elst on 2007-05-14
> **craigp84 said:**
> It's a tough one to put a metric on. Probably easier to say both are excellent, and at this point in time, there is no good evidence that one is better than the other.


Without key-based authentication, I would agree. The advantage of SSH over pretty much everything else is that it offers you a much stronger authentication method than passwords, if the users are willing/able to use keys.

---

### Post by craigp84 on 2007-05-14
> The advantage of SSH over pretty much everything else is that it offers you a much stronger authentication method than passwords, if the users are willing/able to use keys.

And what would that be - that's not also present in SSL? ;-)

-c

---

### Post by elst on 2007-05-14
> **craigp84 said:**
> And what would that be - that's not also present in SSL? ;-)

-c

It's present, it just ain't working in practice ;).

---

### Post by craigp84 on 2007-05-14
It's not working? i think you've been playing with the wacky baccy!

Works a treat.

-c

---

### Post by elst on 2007-05-14
I've fiddled with SSL certificates for emails and servers, and it's a bit more hassle than it should be. I haven't used smartcards and that kind of thing, which are probably more equivalent to SSH key-based auth, but I can use the latter fairly easily  on any computer, which is why I feel that SSH is better in practice, although I probably wouldn't recommend it to the non-technical.

---

### Post by dreamie on 2007-05-15
Many of the mentioned ftp-servers supports SSL/TLS encryption, but do you know of a stable, respected linux ftp that supports sftp (ssh)?

Regards,
 
 Peter

---

### Post by elst on 2007-05-16
SSL is a general-purpose thing that can be attached to many protocols, but SFTP is actually a specific facility of SSH, rather than a variation or add-on to FTP. They are separate network protocols - the name is misleading.

If you install the OpenSSH service (the openssh-server package) then it provides SFTP access automatically, with no additional configuration required on the server end. OpenSSH doesn't really have any Open Source competition, probably because it's proven sufficiently secure and robust that there isn't a significant need. FTP had some unsatisfactory implementations, so a bunch of people have been motivated to do better.

There is no technical issue with running both FTP and SSH services on the same system if you want, and obviously you are the best judge of what setup is right for your situation. At one time I ran a server which had SSH to give the admins secure remote access, and vsftpd to provide FTP for the Web development tools that the regular users had, with the chroot option switched on to confine them to their home directories, and both sides seemed happy.

---

### Post by fyl2u on 2007-05-18
[quote=elst]
SSL is a general-purpose thing that can be attached to many protocols, but SFTP is actually a specific facility of SSH, rather than a variation or add-on to FTP. They are separate network protocols - the name is misleading.[/quote]

Oh, really? I didn't realise that.  So... vsftpd is FTP as oppose to SFTP?

What should I "switch on" in vsftpd to keep it as secure as possible?

I need to transfer huge amounts of highly sensitive information (gigs and gigs of it) per week and have just set up an Ubuntu server running vsftpd, but I'm a complete noob at this.

I've got the chroot jail switched on so that users are restricted to their respective home folder (which I had to do because if I logged onto the FTP site with IE7 I saw a directory listing of the ROOT folder instead of the home folder!)

Do I need to "enable" SSL in vsftpd or is it on by default?

Am I going about this the right way? I don't want my information or passwords to be sniffed.

---

### Post by craigp84 on 2007-05-18
fyl2u,

> I need to transfer huge amounts of highly sensitive information (gigs and gigs of it) per week

> but I'm a complete noob at this.

That's seriously concerning. I hope you're not involved in processing any data related to me.

I genuinely hope that data's not as sensitive as you make out. Otherwise, how do you sleep at night?

Shame on you.

-c

---

### Post by fyl2u on 2007-05-18
> **craigp84 said:**
> fyl2u,


That's seriously concerning. I hope you're not involved in processing any data related to me.

I genuinely hope that data's not as sensitive as you make out. Otherwise, how do you sleep at night?

Shame on you.

-c

:-) Up until now, all our transfers have been via our remote DMZ Win2000 server that was set up by people far more experienced that I, but I've convinced the company to let me replace it with an Ubuntu server (still in the DMZ)  that I'll be administrating myself :guitar:

---

### Post by elst on 2007-05-18
> **fyl2u said:**
> Oh, really? I didn't realise that.  So... vsftpd is FTP as oppose to SFTP?

What should I "switch on" in vsftpd to keep it as secure as possible?

I need to transfer huge amounts of highly sensitive information (gigs and gigs of it) per week and have just set up an Ubuntu server running vsftpd, but I'm a complete noob at this.

I've got the chroot jail switched on so that users are restricted to their respective home folder (which I had to do because if I logged onto the FTP site with IE7 I saw a directory listing of the ROOT folder instead of the home folder!)

Do I need to "enable" SSL in vsftpd or is it on by default?

Am I going about this the right way? I don't want my information or passwords to be sniffed.

It sounds like you guys need to talk to an security expert who can advise you on how to do this in a safe and regulation-compliant way. 

I'm not a security expert, but to answer your questions as best I can:

- vsftpd is one of a number of products that implement the FTP protocol. Most allow you to add SSL to protect the FTP traffic, but it's not switched on by default.

- SFTP is a facility provided by the SSH protocol, a general-purpose remote access protocol implemented by OpenSSH. It automatically encrypts, and it's fairly easy to implement key-based authentication. Unlike FTP servers, OpenSSH doesn't support virtual users, chrooting users to home directories and other features that are useful for dedicated file servers.

- Service security involve several wholly distinct issues, and you have to cover all of them:

i) Service compromise through buffer overflows etc. You avoid this by using actively maintained products with a good track record. SSH and vsftpd qualify, and I'm sure that other FTP products would too.

ii) Traffic interception. Any protocol with strong encryption will deal with this. If you use unsafe protocols you can protect them by tunnelling them through a VPN or SSH port forwarding.

iii) Account compromise. If your server is accessible from the public Internet then automated sweeps by cracking software *will* find services on standard ports and try to sign in with common usernames and passwords. Most nontechnical people can't/won't make passwords strong enough. Ideally, you use SSH keys or SSL certificates to authenticate clients as far as you can, rather than relying on passwords. You can actually avoid most probes just by using non-standard ports, and defeat casual attacks by denying logins to built-in accounts like "root".

---

