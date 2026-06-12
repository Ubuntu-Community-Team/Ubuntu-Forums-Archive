---
title: "tunnelled clear text passwords"
date: 2010-11-13
forum: Security
---

### Post by duduntu on 2010-11-13
Hi

The ubuntu installation came with my ubuntu (it does not matter which version etc.) 
contains sshd_config file with this interesting lines:

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes


The same lines are seen in many Ubuntu-related internet pages.
This is quite surprising to see. 
This seem to contradict to the fact that ssh was created specially 
to provide authentication (with passwords, of couse) but without 
sending them by internet as clear text like previous programs did.

But I could not find any clear confirmations of that neither 
in Kubuntu-related documents no anywhere else.  
I put below fragment of a document from RedHat.
This seem to imply that if one will use two "yes", the passwords
will be passed in encripted form (and this is what is recommended by RedHat).
Is that true? 
Is this true for Ubuntu too? 
Is the quoted line from  sshd_config wrong? 
Or incomplete?


[http://www.faqs.org/docs/securing/chap15sec122.html](http://www.faqs.org/docs/securing/chap15sec122.html)
**           RSAAuthentication yes**           The option RSAAuthentication specifies whether to try RSA authentication. This option must be set to **yes** for better security in your sessions. RSA use            public and private key pairs created with the ssh-keygen1utility for authentication purposes.           
**           PasswordAuthentication yes**           The option PasswordAuthentication specifies whether we should use password-based authentication. For strong security, this option must always be set to **yes**.

---

### Post by SeijiSensei on 2010-11-13
SSH never sends passwords in plain-text; they're encrypted first then sent over the wire.  I suspect the materials you've been reading mean that you enter the password in plain text when prompted.  They're not in plain text when they leave the client, though.

There are a variety of methods by which you can authenticate using SSH.  I've used passwords but nowadays I generally use RSA.  It's especially helpful if you need to log into that server you haven't checked on in ages and don't remember what the root password is!

---

### Post by duduntu on 2010-11-14
Thank you for reply.

The phrase is:
tunnelled CLEAR text passwords

So this statement is wrong?

As I understand, it is distributed in all recent versions in /etc/ssh/sshd_config files.
And repeated in many internet pages,
You can simply to google it in commas.

Can somebody related to this comment correct it in distribution and to give correct stemenets here ?
To formulate it correctly. Whether the passwords are really never sent in plain text or
they are not sent if RSA is invoked?
It does not need to explain the importance of these issues.
All other "security issues" are unimportant if this is not handled properly.

---

### Post by matt_symes on 2010-11-14
Hi

> tunnelled CLEAR text passwords

I believe the emphasis should be on the word _tunnelled_. That is the encrypted tunnel.

Kind regards

---

### Post by cariboo on 2010-11-14
> **duduntu said:**
> Thank you for reply.

The phrase is:
tunnelled CLEAR text passwords

So this statement is wrong?

As I understand, it is distributed in all recent versions in /etc/ssh/sshd_config files.
And repeated in many internet pages,
You can simply to google it in commas.

Can somebody related to this comment correct it in distribution and to give correct stemenets here ?
To formulate it correctly. Whether the passwords are really never sent in plain text or
they are not sent if RSA is invoked?
It does not need to explain the importance of these issues.
All other "security issues" are unimportant if this is not handled properly.

Could you please file a bug about the above problem. You'll have to create an account on [https://launchpad.net]("https://launchpad.net"), then once you have an account submit the bug by pressing Alt-F2 and typing:

```
ubuntu-bug openssh-server
```

Things will be pretty self-evident from there.

---

### Post by duduntu on 2010-11-14
> **matt_symes said:**
> Hi



I believe the emphasis should be on the word _tunnelled_. That is the encrypted tunnel.

Kind regards

Of course I imagine that the tunnel can be encrypted. But this is only a guess. Moreover,
it can be encrypted and in can be not encrypted. Where it is written that the tunnel is encrypted?
While it is not written clearly that it is encrypted, we don't know.
May be it encrypted only in RedHat? and only if to invoke RSAAuthentication as they recommend,
but it is not encrypted in Ubuntu? Who knows...

---

### Post by cariboo on 2010-11-14
It is encrypted in Ubuntu too. I was playing with wireshark last week and made an ssh connection to my server, there was nothing sent in plain text whether I used key based authentication or a password.

---

### Post by DZ* on 2010-11-14
```
man ssh
```
"if other authentication methods fail, ssh prompts the user for a password. The password is sent to the remote host for checking; however, since all communications are encrypted, the password cannot be seen by someone listening on the network."

---

### Post by CharlesA on 2010-11-14
SSH is encrypted end-to-end.

For the record, that entry has been in every linux distro I've used, the one in CentOS 5.5 is this:

```
# To disable tunneled clear text passwords, change to no here!
#PasswordAuthentication yes
#PermitEmptyPasswords no
PasswordAuthentication yes

```

---

### Post by matt_symes on 2010-11-15
Hi

As has been highlighted SSH uses encrypted tunnels. Really, read the man pages before googling.

SSH is pretty secure especially if you use version 2 only. Version one has some vulnerabilities.

This is one reason why SFTP, which uses SSH, is so much more secure than FTP. No plain text user names or passwords.

However, there are a number of things one can do to make the SSH server even more secure.

Here is a great little tutorial

[http://ubuntuforums.org/showthread.php?t=831372](http://ubuntuforums.org/showthread.php?t=831372)

EDIT: BTW use keys rather than passwords.

Kind regards

---

### Post by duduntu on 2010-11-18
> **cariboo907 said:**
> Could you please file a bug about the above problem. You'll have to create an account on [https://launchpad.net](https://launchpad.net), then once you have an account submit the bug by pressing Alt-F2 and typing:

```
ubuntu-bug openssh-server
```Things will be pretty self-evident from there.

OK, thank you. Somehow without Alt-F2, but I submitted this (as possibly wrong comment).

---

### Post by CharlesA on 2010-11-18
> **duduntu said:**
> OK, thank you. Somehow without Alt-F2, but I submitted this (as possibly wrong comment).
You could submit a bug report from a terminal as well. :)

Got a link to the bug report?

---

### Post by duduntu on 2010-11-18
> **CharlesA said:**
> You could submit a bug report from a terminal as well. :)

Got a link to the bug report?

I am now not at Ubuntu. May be because of this I did not find a desent application for Alt-F2 :)

Here the link, if you are interesting:
[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/677161](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/677161)

---

### Post by cariboo on 2010-11-18
Alt-F2 just brings up a run dialogue box, you enter a command and press enter.

I'm running Natty, and it doesn't work here at the moment, so I use a terminal.

---

### Post by hggdh on 2010-11-18
I have just commented on the bug. Summary: the session is already going in an encrypted tunnel. There is no risk -- except the fact that one should use public-key authentication, and *not* password-based authentication.

---

### Post by cariboo on 2010-11-18
Nobody is disputing the fact that the data is being sent encrypted, the wording in the config file is just ambiguous.

---

### Post by CharlesA on 2010-11-18
> **cariboo907 said:**
> Nobody is disputing the fact that the data is being sent encrypted, the wording in the config file is just ambiguous.

Yep. I've seen it worded that way in many distros, so I don't think that it's something specific to Ubuntu.

---

### Post by hggdh on 2010-11-18
Well, it is pretty much how upstream coded it. The confusion, I guess, comes from 'tunnelling' and 'clear-text password' one after the other.

But this is exactly what it is doing: tunnelling a clear-text password.

What is implicit -- well, sort of, we are talking about an *encrypted channel*, that's the whole idea of SSH -- is that the tunnel is encrypted.

I see no reason to add more text (and delta to us) to explain the (for SSH) obvious.

---

### Post by duduntu on 2010-11-19
> **hggdh said:**
> Well, it is pretty much how upstream coded it. The confusion, I guess, comes from 'tunnelling' and 'clear-text password' one after the other.

But this is exactly what it is doing: tunnelling a clear-text password.

What is implicit -- well, sort of, we are talking about an *encrypted channel*, that's the whole idea of SSH -- is that the tunnel is encrypted.

I see no reason to add more text (and delta to us) to explain the (for SSH) obvious.

This discussion is becoming strange.
For me as occasional nonprofessional (although experienced) 
system adminitrator it is obvious that if the the key configuration file states that
passwords are tunelled in clear text, then it is impossible to say more clearly,
that they are sent as clear text. THIS is obvious.

If you or somebody wanted to say that they are encrypted, they would simply
say this: "tunelled encrypted text pawsswords" or "text passwords sent via encrypted tunnel".
You did not say this. OK, then you meant that the passwords are sent unencrypted. This is obvious.

If it is stated as it is now, anybody who don't have ten years of system administration
and masters or doctor degree in computer science, so any not too "involved" person 
will understand this as sending of non-protected passwords. Which is wrong if to believe to
to your suggestins. 

At this bug tracking site they wait for my answer, but
I cannot figure out how to make a new post, and I do not have time to study this.
The issue is clear enough.

Even if a person will spend probably a hour for reading "man ssh",
he will have two different statements and he will need a third source, to decide between them.
What can be the third source?


And do not say this nonsence about login through keys.
Keys may be stolen or lost. 
In addition, in some other circumstances they are not convenient enough.
In many circumstances they are not convenient.
For example, they probably want me to use keys for answering to that bug tracing
post, but I do not have time to figure out in how to make the key.
The whole story with keys might appear due to this wrong phrase.
Meanwhile password logins to ordinary computers (not for bank transfers) 
are safe enough provided you adjusted properly your /etc/host... files.

By the way in these things with it is not all good /etc/host... with Ubuntu.
But I do nto have more time to discuss this.

---

### Post by cariboo on 2010-11-19
To add something to the bug, scroll done to **Add Comment** to add extra info to the bug. See the screen shot.

---

### Post by hggdh on 2010-11-19
> **duduntu said:**
> If it is stated as it is now, anybody who don't have ten years of system administration
and masters or doctor degree in computer science, so any not too "involved" person 
will understand this as sending of non-protected passwords. Which is wrong if to believe to
to your suggestins. 

Password are send in clear-text. The message is, as you point out, crystal-clear. The **channel** is encrypted. This is the whole idea of SSH -- to provide you with an encrypted channel under which you can rest assured nobody can sniff the traffic and get your password (or other secrets/private data).

> **duduntu said:**
> At this bug tracking site they wait for my answer, but
I cannot figure out how to make a new post, and I do not have time to study this.

You have to login to the site, in the same way you logged in when you opened the bug. You should have an userId and password to do that. And yes, I was waiting for your answer there.

> **duduntu said:**
> The issue is clear enough.

Even if a person will spend probably a hour for reading "man ssh",
he will have two different statements and he will need a third source, to decide between them.
What can be the third source?

From the openssh-server package description (italics mine): "Ssh (Secure Shell) is a program for logging into a remote machine and for executing commands on a remote machine. *It provides secure encrypted communications between two untrusted hosts over an insecure network*. X11 connections and arbitrary TCP/IP ports can also be forwarded over the secure channel. It can be used to provide applications with a secure communication channel."

As I said in the bug, there is no other way to send a password over but in clear-text. If you look deep enough, a clear-text password is always processed somewhere.

> **duduntu said:**
> And do not say this nonsence about login through keys.
Keys may be stolen or lost. 
In addition, in some other circumstances they are not convenient enough.
In many circumstances they are not convenient.

Although I dispute the "nonsense" part of the above, you are correct on the other points. 

> **duduntu said:**
> For example, they probably want me to use keys for answering to that bug tracing
post, but I do not have time to figure out in how to make the key.

No, it is not required, needed, or used, for one to post to the [Ubuntu bug tracker]("https://bugs.launchpad.net"). Please see above.

> **duduntu said:**
> The whole story with keys might appear due to this wrong phrase.

I am sorry, I lost you here. The whole story with public-keys is due to the fact that password-based authentication to an SSH server is widely considered insecure. It has nothing to do with tunnelled clear-text passwords, but more with brute-force attacks.

> **duduntu said:**
> Meanwhile password logins to ordinary computers (not for bank transfers) 
are safe enough provided you adjusted properly your /etc/host... files.

By the way in these things with it is not all good /etc/host... with Ubuntu.
But I do nto have more time to discuss this.

I am sorry, again I lost you here.

---

### Post by CharlesA on 2010-11-19
I can understand the confusion, but the keyword is "tunneled" anything that is tunneled in regards to SSH is encrypted, so that it cannot be read "on the wire."

> **duduntu said:**
> 
Meanwhile password logins to ordinary computers (not for bank transfers) 
are safe enough provided you adjusted properly your /etc/host... files.

By the way in these things with it is not all good /etc/host... with Ubuntu.
But I do nto have more time to discuss this.

What are you referring to, exactly?

---

### Post by duduntu on 2010-11-19
> **hggdh said:**
> 
You have to login to the site, in the same way you logged in when you opened the bug. You should have an userId and password to do that. And yes, I was waiting for your answer there.


Yes, consider please these posts as answers.
I tried there two times, but twice had my text lost and the screen full of some red diagniostics.

Still please don't forget about RSAAuthentication option.
I still do not understand whether it needs and for what it needs, although I already spend a lot of time for this reading and discussions. You are against making comments more clear?

---

### Post by duduntu on 2010-11-19
> **CharlesA said:**
> 



What are you referring to, exactly?

/etc/host.allow, /etc/host.deny

---

### Post by CharlesA on 2010-11-19
> **duduntu said:**
> /etc/host.allow, /etc/host.deny

That's part of [TCPwrappers]("http://linuxhelp.blogspot.com/2005/10/using-tcp-wrappers-to-secure-linux.html"), which isn't configured by default.

What are you using them for?

---

### Post by duduntu on 2010-11-19
> **CharlesA said:**
> That's part of [TCPwrappers]("http://linuxhelp.blogspot.com/2005/10/using-tcp-wrappers-to-secure-linux.html"), which isn't configured by default.

What are you using them for?
Obviously, to deny access to my computer from everywhere except may be from somewhere,
if I expect ever login from another computer to this.

---

### Post by CharlesA on 2010-11-19
> **duduntu said:**
> Obviously, to deny access to my computer from everywhere except may be from somewhere,
if I expect ever login from another computer to this.

Did you read the link on how to configure them?

The part that has me confused was what you said in the OP:

> Meanwhile password logins to ordinary computers (not for bank transfers)
are safe enough provided you adjusted properly your /etc/host... files.

By the way in these things with it is not all good /etc/host... with Ubuntu.
But I do nto have more time to discuss this.

You use tcpwrappers to secure services that are running on your machine, such as SSH. It's not used for normal web browsing.

---

### Post by duduntu on 2010-11-19
> **CharlesA said:**
> Did you read the link on how to configure them?

The part that has me confused was what you said in the OP:



You use tcpwrappers to secure services that are running on your machine, such as SSH. It's not used for normal web browsing.

I know how to configure them.
But what about web browsing? Looks like different subject.

---

### Post by CharlesA on 2010-11-19
> **duduntu said:**
> I know how to configure them.
But what about web browsing? Looks like different subject.

You said something about bank transfers. *shrugs*

---

### Post by duduntu on 2010-11-19
> **CharlesA said:**
> You said something about bank transfers. *shrugs*
I see what might be the confusion.
I meant that the passwords authentication plus a good hosts.allow/deny is enough for secure incoming connections to PC's which is controlled by you and used by you. 
Bank transfers needs higher security, assume mobility of a customers, plus 
banks usually want judicial proofs of identity.
(Customers would want prrofs of operations or their absence too, but  they are  denyed. )  :)
.. And all banks make interface through web browsers, yes (almost all).

---

### Post by CharlesA on 2010-11-19
> **duduntu said:**
> I see what might be the confusion.
I meant that the passwords authentication plus a good hosts.allow/deny is enough for secure incoming connections to PC's which is controlled by you and used by you. 
Bank transfers needs higher security, assume mobility of a customers, plus 
banks usually want judicial proofs of identity.
(Customers would want prrofs of operations or their absence too, but  they are  denyed. )  :)

That makes sense now.

I just use iptables to filter connections instead of relying on tcpwrappers, but either of them work.

---

### Post by matt_symes on 2010-11-19
Hi

@OP. Keys are safe as long a you keep your private key safe. If anybody could get their hands on your computer then they could hack your PC and communications. That is life.

The onus is on you to take some basic precautions with security. Keys are _not_ nonsense and more secure than passwords. _Always_ use keys.

Kind regards.

---

### Post by duduntu on 2010-11-19
> **matt_symes said:**
> Hi

@OP. Keys are safe as long a you keep your private key safe. If anybody could get their hands on your computer then they could hack your PC and communications. That is life.

The onus is on you to take some basic precautions with security. Keys are _not_ nonsense and more secure than passwords. _Always_ use keys.

Kind regards.

What means "@OP"?
Declarations without explanations are not welcome.
With explanations (brief) they are welcome.
Kind regards.

---

### Post by CharlesA on 2010-11-19
@OP means it's directed to the Original Poster.

Basically matt_symes, is saying that keys are secure as long as you keep your private key safe. If someone has physical access to the machine, it's game over.

Keys cannot be bruteforced since you need to have ***both*** the private key and know the passphrase on the private key.

---

### Post by duduntu on 2010-11-19
> **CharlesA said:**
> @OP means it's directed to the Original Poster.

Basically matt_symes, is saying that keys are secure as long as you keep your private key safe. If someone has physical access to the machine, it's game over.

Keys cannot be bruteforced since you need to have ***both*** the private key and know the passphrase on the private key.
Thank you for "@OP".
Keys are encripted with passphrase?
I met this. 
Then possibly there are some signatures in the key, which could allow to 
guess passphrase by brute force (by checking all more or less long passwords at fast computer or even at a farm?)
Then as soon as somebody have your flash disk or something with the key, after some excersises
he could login at your remote computer(s)?, from own his computer?
And this is not the case when dealing with password autentication. Impossible to scan all passwrods and
you can deny access for any hosts.

---

### Post by CharlesA on 2010-11-19
You can have a passphrase on your private key, yes.

The thing is that you cannot brute force the private key in the same way you bruteforce a password. You can run a dictionary attack on it, but since you need to authenticate to a machine with the public key you'd know someone has yer private key.

If your private key is compromised, you recreate the keypair, and remote the old public key from the authorized_keys file. That makes the compromised private key useless, since they can't connect with it.

---

### Post by matt_symes on 2010-11-19
Hi

duduntu my apologises, i did not mean to offend. I just guess i am used to typing a certain way.

As CharlesA pointed out, i was speaking to you (@OP you posted the first post). All i am trying to to do i teach you the best way to do things using SSH. Believe me, i want you to be safe online as well.

But keys are the safest way to do things. That is why i posted you the link for the ssh server.

Your in safe hands with these guys

Kind regards

---

### Post by duduntu on 2010-11-19
> **CharlesA said:**
> You can have a passphrase on your private key, yes.

The thing is that you cannot brute force the private key in the same way you bruteforce a password. You can run a dictionary attack on it, but since you need to authenticate to a machine with the public key you'd know someone has yer private key.

If your private key is compromised, you recreate the keypair, and remote the old public key from the authorized_keys file. That makes the compromised private key useless, since they can't connect with it.

For the last - if you know that it is compromised.
Have you ever happened to loss your flash disk and then tried to remember what was there?
Some one can also copy the key and return the flash on the place.

But the first sentence I don't understand. This is certainly misprint. I don't get the sence.
I am affraid attacker don't need to connect to the victims machine for bruteforcing password.
There might be some signatures. But this is just guess. If you  input passphrase incorrectly,
which mashine discovers it, the local or remote?

---

### Post by duduntu on 2010-11-19
> **matt_symes said:**
> Hi

duduntu my apologises, i did not mean to offend. 
Kind regards

No problem, no offenses. I simply asked what this means, since obviously it looked like having some sense, not a simple misprint. So now I now.
Regards. 
I might write unclear myself.
I mentioned declarations about the subject we are discussing, since you have issued some statements without explanations.

---

### Post by CharlesA on 2010-11-19
> **duduntu said:**
> For the last - if you know that it is compromised.
Have you ever happened to loss your flash disk and then tried to remember what was there?
Some one can also copy the key and return the flash on the place.

But the first sentence I don't understand. This is certainly misprint. I don't get the sence.
I am affraid attacker don't need to connect to the victims machine for bruteforcing password.
There might be some signatures. But this is just guess. If you  input passphrase incorrectly,
which mashine discovers it, the local or remote?

If I lose a flash drive and I am not sure if my private key is on it or not, I recreate the keypair just to be safe.

As for brute forcing, once the keypair is recreated, it's pointless to bruteforce the passphraes on the old key, since even with the passphrase, you wouldn't be able to connect with the old key.

---

### Post by duduntu on 2010-11-19
> **CharlesA said:**
> If I lose a flash drive and I am not sure if my private key is on it or not, I recreate the keypair just to be safe.

As for brute forcing, once the keypair is recreated, it's pointless to bruteforce the passphraes on the old key, since even with the passphrase, you wouldn't be able to connect with the old key.

Still you don't consider unnoticed copying or loss and bruteforcing.

---

### Post by CharlesA on 2010-11-19
> **duduntu said:**
> Still you don't consider unnoticed copying or loss and bruteforcing.

That's why you use a secure passphrase on yer private key. To bruteforce a non dictionary passphrase that is 10-15 (or more) characters long would take a long time. It doesn't work the same way as bruteforcing a password.

There is always risk involved with having remote access.

EDIT: The thing you need to know is that you need to connect to the machine the private key is for otherwise you don't get prompted for the passphrase. I would think someone would notice a ton of connection attempts from the same IP in the logs.

---

