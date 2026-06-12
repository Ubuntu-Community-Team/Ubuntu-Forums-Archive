---
title: "What's the most secure way of doing huge file transfers?"
date: 2007-05-18
forum: Server Platforms
---

### Post by fyl2u on 2007-05-18
Having just discovered on another thread that SFTP is misleadingly named and is a bolt-on to SSH as oppose to a more secure version of FTP...

Basically, I need to transfer huge amounts of highly sensitive information (gigs and gigs of it) per week and have just set up an Ubuntu server running vsftpd, but I'm a complete noob at this.

Am I going about this the right way? I don't want my information or passwords to be sniffed.

What should I "switch on" in vsftpd to keep it as secure as possible?

I've got the chroot jail switched on so that users are restricted to their respective home folder (which I had to do because if I logged onto the FTP site with IE7 I saw a directory listing of the ROOT folder instead of the home folder!)

Do I need to "enable" SSL in vsftpd or is it on by default?

What's this certificates / key thing all about?

I would truly appreciate any help that anyone could give me in understanding this.

Thanks in advance,

Phil
Ubuntu noob (1 week's experience) but totally addicted.

---

### Post by rich.bradshaw on 2007-05-18
What exactly are you doing? Is it just you doing this, or lots of different people?

I just use the service myself, so I don't worry about security on the box too much - i.e. no point chrooting it, as I am the only person who is going to connect, and I can trust myself!

I use SSH + SFTP to transfer, using key based authentication. SSH is very secure, as all data is encrypted. The key means that there is no password for the computer, I have a key which requires a password to use. This is basically like having a key to my house, kept in a locked box. I have the key (the passphrase) for the box, which in turn has a key for the computer. Becuase the key for the computer is such a complex key, it is essentially unbreakable.

Read up on passwordless entry, key based SSH and things like that, there are plenty of sites about it.

If you want to do even better, you could encrypt all the data as well - this way even if you did get the data stolen, noone could read it. Ubuntu comes with gpg, in Kubuntu there is a GUI for it, not sure about Ubuntu. THis lets you encrypt data in a very secure key based way.

---

### Post by fyl2u on 2007-05-18
> **rich.bradshaw said:**
> What exactly are you doing? Is it just you doing this, or lots of different people?

I just use the service myself, so I don't worry about security on the box too much - i.e. no point chrooting it, as I am the only person who is going to connect, and I can trust myself!

I use SSH + SFTP to transfer, using key based authentication. SSH is very secure, as all data is encrypted. The key means that there is no password for the computer, I have a key which requires a password to use. This is basically like having a key to my house, kept in a locked box. I have the key (the passphrase) for the box, which in turn has a key for the computer. Becuase the key for the computer is such a complex key, it is essentially unbreakable.

Read up on passwordless entry, key based SSH and things like that, there are plenty of sites about it.

If you want to do even better, you could encrypt all the data as well - this way even if you did get the data stolen, noone could read it. Ubuntu comes with gpg, in Kubuntu there is a GUI for it, not sure about Ubuntu. THis lets you encrypt data in a very secure key based way.

Hi, and thanks for the reply.

It's not just me that'll be using it, there'll be 7 or 8 people that will be using it from the host end, and a constantly changing group of many users at the client end.

We're a recording studio, owned and run by a major label, and the information we're sending will be the session data and mixes of brand new unmastered pre-release music, albums and music for films/tv that we send to mastering houses, A&R, and clients at other studios.

It is imperative that the public don't get hold of these versions because firstly it will affect sales and secondly they will sound quite different from the finished mastered versions that will be on the official CD / DVD / TV releases, so security is of utmost importance.

To begin with I've set up vsftpd with 10 users, each with their own passworded home folder and chroot set up so that each logon only has access to their associated directory, not to the other folders, (because we don't want any of our clients getting hold of our other clients' material either).

I would like to know that it will be as secure as possible, and that there is as little chance as possible of anyone intercepting the data or gaining unauthorised access.

---

### Post by rich.bradshaw on 2007-05-18
I don't really know much than what I have already said I'm afraid, I don't have much experience with multiuser environments.

sftp is the way to go though, so assuming passwords aren't leaked etc, the connection is pretty secure from the client to the server.

By chrooting the system, the files are secure from each other.

As I said, you could encrypt the files on the server - are they to be worked on there, or just stored? gpg will let you give the clients your encyrption key, then they can encrypt it, but only you can decrypt it for instance. If you are worried about the server being physically comprimised, this might be a good way to go. You can alternativly encrypt each users home directory, though I have no experience of doing this.

Maybe someone more qualified will come along, though I would say what you have done so far sounds sensible.

---

### Post by fyl2u on 2007-05-18
> **rich.bradshaw said:**
> I don't really know much than what I have already said I'm afraid, I don't have much experience with multiuser environments.

sftp is the way to go though, so assuming passwords aren't leaked etc, the connection is pretty secure from the client to the server.

By chrooting the system, the files are secure from each other.

As I said, you could encrypt the files on the server - are they to be worked on there, or just stored? gpg will let you give the clients your encyrption key, then they can encrypt it, but only you can decrypt it for instance. If you are worried about the server being physically comprimised, this might be a good way to go. You can alternativly encrypt each users home directory, though I have no experience of doing this.

Maybe someone more qualified will come along, though I would say what you have done so far sounds sensible.

They won't be worked on while they're on the server - it'd be a case of upload from here, email the client, they download, they email us to say they've got it, we delete.

Thanks, I'll check out gpg - sounds promising.

---

### Post by rich.bradshaw on 2007-05-18
Sure, then it probably makes sense for them to be encrypted on the server - gpg is good, as they can encrypt, and then send to you, so even if the server was comprimised, the files are useless.

You might want to install something like fail2ban or denyhosts on the server as well, in order to prevent the SSH passwords being bruteforced. Of course, if you did get them all using key based entry, then you can turn passwords off in sshd_config. I use fail2ban as it doens't need an configuration, you can apt-get it, it bans anyone who gets the password wrong 5 times in a row for 5 mins - basically makes bruteforcing the password take forever.

---

### Post by fyl2u on 2007-05-18
> **rich.bradshaw said:**
> Sure, then it probably makes sense for them to be encrypted on the server - gpg is good, as they can encrypt, and then send to you, so even if the server was comprimised, the files are useless.

You might want to install something like fail2ban or denyhosts on the server as well, in order to prevent the SSH passwords being bruteforced. Of course, if you did get them all using key based entry, then you can turn passwords off in sshd_config. I use fail2ban as it doens't need an configuration, you can apt-get it, it bans anyone who gets the password wrong 5 times in a row for 5 mins - basically makes bruteforcing the password take forever.

Ah, that sounds great!

OK - got that installed now... does it just run on its own or do I need to start it?

---

### Post by rich.bradshaw on 2007-05-18
fail2ban? Think it's automatic.

cat /var/log/fail2ban.log   

will show you what it's doing - if that file has anything in it, then it's working. If you ever have anyone try and bruteforce you, then you will see it in /var/log/auth.log, and the fail2ban.log will show their IP being blocked.

---

### Post by fyl2u on 2007-05-18
> **rich.bradshaw said:**
> fail2ban? Think it's automatic.

cat /var/log/fail2ban.log   

will show you what it's doing - if that file has anything in it, then it's working. If you ever have anyone try and bruteforce you, then you will see it in /var/log/auth.log, and the fail2ban.log will show their IP being blocked.

Thanks for that mate, I've got it going - I didn't know about the "cat" command so I found the log file and "pico"'d it.

I just managed to ban my XP machine for 5 minutes for failing to log in 5 times, so it works :-)

Apparently the existing Win2000 DMZ FTP server we've been using up til now gets bruteforce attacked on a weekly basis.

The IT manager's going to love this daemon! :-D

Thanks again, this is great!

---

### Post by rich.bradshaw on 2007-05-18
That's alright! if you do 

tail -f ANYLOG

e.g.

tail -f /var/log/auth.log

that will show you the newest part of the log, and it updates as things happen. If you sudo in another terminal for instance, you will see it on the auth.log. It's a useful one to keep an eye on. If you have a webserver then /var/log/apache2/access.log is useful as well.

Think that's the extent of my knowledge for now!

---

