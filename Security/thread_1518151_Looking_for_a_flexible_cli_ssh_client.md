---
title: "Looking for a flexible cli ssh client"
date: 2010-06-26
forum: Security
---

### Post by bobdobbs on 2010-06-26
Hi all.

I'd like to know if there are cli ssh clients available other then the default openssh client.

In particular, I'm looking for a client with that will let me bookmark locations.

I've been using gftp for ages, and I've just started to play with fireftp. But I do a lot of work from the terminal.

Some years ago I was using ncftp. It's a great program, but it doesn't support ssh.

---

### Post by Bachstelze on 2010-06-26
Define "bookmark"?

---

### Post by bobdobbs on 2010-06-26
> **Bachstelze said:**
> Define "bookmark"?

Well, I'm guessing that you have used GUI ftp or ssh clients before. Most of them have the means to "bookmark" a connection, so the next time you log in you don't have to enter all the details in again. The details get remembered, are stored and can be used in the future.

ncftp does something similair from the commandline. 
It can bookmark your connections.

As far as I can tell, the openssh cli client doesn't do this.

---

### Post by Bachstelze on 2010-06-26
> **bobdobbs said:**
> 
As far as I can tell, the openssh cli client doesn't do this.

Yes it does. ;)

```
man ssh_config
```

---

### Post by bobdobbs on 2010-06-26
> **Bachstelze said:**
> Yes it does. ;)

```
man ssh_config
```

I still can't see how the openssh client provides me with what I want. 
I would like to log in to my remote host on a shared server without personally having to remember the details. Including the ssh passphrase. I want my client to take care of that for me.

This would be particularly helpful because I administer more then one host. And I already have a bajillion passwords to remember.


I have ssh passwordless logins (using ssh keypairs) set up for the computers in my home/office network. Setting this up was a complete headache, and it occasonally breaks unpredictably and I have repeat the process of setting it up.

Its difficult to understand and very hard to implement.

I don't know if my remote shared host supports ssh passwordless logins, and even if it does, I'm reluctant to learn the way implementation on each host does this.

All I want is a client that can be set up so that I don't have to remember all the details - even the password.

Can the openssh client be configured for this, without having to mess around with messing around with keys on remote hosts?

If not, are you aware of other ssh clients that can be configured for this?

---

### Post by cariboo on 2010-06-26
If you are just transferring file back and forth, you can use Filezilla, it is in the repositories. You have to set up keys for it within the program.

Setting up key pairs is fairly simple, have a look [here]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")

---

### Post by bobdobbs on 2010-06-26
> **cariboo907 said:**
> If you are just transferring file back and forth, you can use Filezilla, it is in the repositories. You have to set up keys for it within the program.

Setting up key pairs is fairly simple, have a look [here]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")

Neither of these items address my problem.

I'm looking for a commandline solution. Filezilla is GUI client.

A key exchange will still require me to remember a passphrase.

---

### Post by teejaybee on 2010-06-26
You're posting in the security forum, not general use or the like, so the main solution we're going to suggest is: Use key based logins. You only set it up once. Leave the passphrase blank if you must - it's only used locally anyway (and only gives you a little more time if an attacker steals your keys). If you consider making keys and propagating them to the servers you require access to be a headache, then maybe linux isn't for you.

I'd much prefer key-based ssh logins without a (local) passphrase than leaving them all in plain text in a config file somewhere.

Just make sure your home and .ssh directory have the proper permissions (I use 700) so that the keys cannot be accessed by other users.

The little bit of effort it requires to generate and propagate keys is, IMHO, well worth it.

---

### Post by CharlesA on 2010-06-26
> **bobdobbs said:**
> Neither of these items address my problem.

I'm looking for a commandline solution. Filezilla is GUI client.

A key exchange will still require me to remember a passphrase.

Then create a key without a passphrase. It'll be less secure, but it seems you want convenience instead of security.

---

### Post by CharlesA on 2010-06-26
> **5replica said:**
> the next time you log in you don't have to enter all the details in again.

?

You always have to enter your password/passphrase. If you are using a passphrase-less key, then you are taken directly to a prompt.

I guess the OP wants to be able to run a command and login to "X" server.

---

### Post by bobdobbs on 2010-06-27
> **CharlesA said:**
> ?

You always have to enter your password/passphrase. If you are using a passphrase-less key, then you are taken directly to a prompt.

I guess the OP wants to be able to run a command and login to "X" server.

No, I don't want to run a command to login to an X server. 
As I stated, I'm looking for a flexible cli ssh client that will not require me to remember yet another password.
cli mean "command line interface". This means that X is not neccessary.

You do not always have to enter a password/passphrase.
I somehow managed to set up a system on my home/office network that does not require me to remember or enter a pass before I ssh around.

The problem is, that my existing ssh public key is actually locked to a passphrase. At the moment, this credential is remembered by X on any local computer that I log into to.
 
But I don't want to have to set this system up again for yet another computer. Let alone one that is not local.
Setting it up initially was a nightmare. Barely worth the effort. And the system has occaisonaly and unpredictably broken, requiring it to be set up all over again.

Having to use two or three passwords to log into a system, and one to power down is just too much already.

I want to relieve myself of having to remember another password for every remote web server I log in to, while actually being able to use a command line application.

---

### Post by CharlesA on 2010-06-27
Perhaps I should have said that the OP wants to type in a command and log into "y" server, where "y" is whatever server they want to login to?

I must have something set up wrong, since I only need to remember one password for logging in via ssh, and for using sudo - e.g., sudo reboot

---

### Post by bobdobbs on 2010-06-28
> **CharlesA said:**
> Perhaps I should have said that the OP wants to type in a command and log into "y" server, where "y" is whatever server they want to login to?

I must have something set up wrong, since I only need to remember one password for logging in via ssh, and for using sudo - e.g., sudo reboot

Ah. Sorry. I see what you mean.

I'm sure you've got things set up right.
But at the moment, when I log in, depending on which machine I'm one, I need my password to login.
Then I need a password to unlock an application so that I can turn on wireless networking. Sometimes X also requires the passphrase for my ssh key as X is starting up.

The last stage enables passwordless ssh for me throughout the session. I deal with the inconvenience upfront, rather then having to type in my passphrase for every ssh session.

So, that's three passwords just on login.
I'd really like to minimise all of this.
Having a cli ssh client being able to help me out would be great.

---

### Post by teejaybee on 2010-06-28
Have you looked at "seahorse" that comes with ubuntu/gnome? It can link in to a lot of stuff, even ssh, but I think that you need X running and ssh from terminals inside X (I have no real experience with seahorse, though, so i'm not sure if it's X specific).

---

### Post by spynappels on 2010-06-28
> **bobdobbs said:**
> Having to use two or three passwords to log into a system, and one to power down is just too much already.

I want to relieve myself of having to remember another password for every remote web server I log in to, while actually being able to use a command line application.

I have all my servers accessed from Putty on my Windows Laptop (work provided) and it is set to remember the passwords, but I still need to know them to accomplish any sudo tasks, so unless you use the same password on all remote servers, you are going to have to remember different passwords to be able to do anything on remote servers anyway.

---

### Post by CharlesA on 2010-06-28
> **bobdobbs said:**
> Ah. Sorry. I see what you mean.

I'm sure you've got things set up right.
But at the moment, when I log in, depending on which machine I'm one, I need my password to login.
Then I need a password to unlock an application so that I can turn on wireless networking. Sometimes X also requires the passphrase for my ssh key as X is starting up.

The last stage enables passwordless ssh for me throughout the session. I deal with the inconvenience upfront, rather then having to type in my passphrase for every ssh session.

So, that's three passwords just on login.
I'd really like to minimise all of this.
Having a cli ssh client being able to help me out would be great.

Wow that sounds like a lot of work. I don't run X on any of my servers, but I do sometimes forward applications that use X over SSH so that it's easier to work with then using command line stuff.

---

