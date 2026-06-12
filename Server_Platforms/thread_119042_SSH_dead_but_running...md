---
title: "SSH dead but running.."
date: 2006-01-18
forum: Server Platforms
---

### Post by CrustyDOD on 2006-01-18
Hey

I have server running on 5.04 and everything runs just fine but SSH stopped working somehow...

Problem is that connection with putty to server over ssh, results in connection timed out. But it worked just fine untill now!

The weird part about this is that ssh is running and firewall is not blocking it!
http, ftp,... is running normally...

It just denies me to connect..

I know i had this problems already and to fix it i had to do apt-get install ssh stuff again... Don't want to do that each time :(

Also rebooted server, not working, can't connect to SSH...

Any ideas?
Oh btw, getting logs to post here will kinda be hard cause well, i don't know how to post them using console... heh

---

### Post by Glut on 2006-01-18
I would like to see your sshd_config which  is in /etc/ssh. Access to logs would also be nice, copy them to your user directory and chown them to your username. Then post from the web browser. 

if you telnet to your server on port 22, do you get a connection?

---

### Post by CrustyDOD on 2006-01-21
Voila, my config file for ssh.. Always the same, worked with this so far, well untill now that is...

What log file do i need to check for SSH stuff? Got lots of them in /var/log and don't really have time to go over all 1 by 1...


```
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 600
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to no to disable s/key passwords
#ChallengeResponseAuthentication yes

# Change to yes to enable tunnelled clear text passwords
PasswordAuthentication no


# To change Kerberos options
#KerberosAuthentication no
#KerberosOrLocalPasswd yes
#AFSTokenPassing no
#KerberosTicketCleanup no

# Kerberos TGT Passing does only work with the AFS kaserver
#KerberosTgtPassing yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
KeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem	sftp	/usr/lib/sftp-server

UsePAM yes

```

---

### Post by MJN on 2006-01-22
You mentioned Putty, that's a Windows SSH client right? If so, it's always best to test things locally when you're having problems then you more easily determine where your problems lie...

Can you SSH from the machine to itself?

Mathew

---

### Post by CrustyDOD on 2006-01-24
Well it does connect locally but it refuses local connection or something like that...

Tried from linux desktop to server also and i also can't connect...

It's really weird as i haven't changed a thing...

---

### Post by alamba on 2006-01-24
Can you run the following command: nmap localhost
Is ssh listening on port 22?

Akshay

---

### Post by CrustyDOD on 2006-01-24
bash - nmap command doesn't exists... error i get (text not really the same as i didn't remember it word by word ;) )

Yes, SSH is running on 22 port, firewall open, all worked fine all up untill 1 day... heh

I know that if i simply do a apt-get install ssh again that it will work as this isn't the first time this happened for no reason at all but i would really like to find out what is going on... It's kinda annoying doing this all the time especially since server is not like near me...

---

### Post by MJN on 2006-01-24
I think you're going to have to give us more clues here...
 
Copy-and-paste the output of **ssh 127.0.0.1** whilst sat on the server, word for word, so we can see what's happening...

---

### Post by CrustyDOD on 2006-01-24
> Copy-and-paste the output of ssh 127.0.0.1
Hardly! Server, console only in my basement, small screen can hardly see anything...

I tried "ssh 127..." and the output was:
**The authenticity of host '127.0.0.1 (127.0.0.1)' can't be established.**
RSA key fingerprint bla bla...

I'll try ssh with -v command for more details but i need to get digital camera first as i don't know any other way of showing you what respondes i get in console...

---

### Post by MJN on 2006-01-24
I'm using Konsole in Kubuntu however the similar app in Ubuntu must surely have the ability to highlight a block of text, copy it to the clipboard and then you can paste it here?

It'd be worth finding out how, now only for other purposes but I think it's our only chance of getting you up and running on this one!

For what it's worth, the bits you remembered were starting to look promising... but it's the rest that's still of interest!

Mathew

P.S. -v won't be necessary (not yet anyway!) as it usually spews out enough when things go wrong to be able to determine what's up.

---

### Post by CrustyDOD on 2006-01-25
[QUOTE=MJN]I'm using Konsole in Kubuntu however the similar app in Ubuntu must surely have the ability to highlight a block of text, copy it to the clipboard and then you can paste it here?
[/QUOTE]
Don't think that you understand what i'm saying :) Or maybe i don't..

It's a server with console only, NO X system on it, no mouse, no icons, no KDE, GNOME or others... just console! 
I never heard of a browser that works in console... so that's the problem i have with copy and paste this stuff to you here...

I'll get a digital camera tommorow and make pics of it heh, the only way i know to show you what i get in console..

[QUOTE=MJN]
For what it's worth, the bits you remembered were starting to look promising... but it's the rest that's still of interest!
[/QUOTE]
The rest is just about that RSA key fingerprint and if i say Yes, it accepts it and then goes back to console. When i type logout, it says that it was successfully disconnected from SSH and then i type logout again and i logout normally.

More info tommorow when i get camera and you'll see the pics..

---

### Post by MJN on 2006-01-25
[quote=CrustyDOD]Don't think that you understand what i'm saying :) Or maybe i don't..[/quote]
 
It's me that's getting the wrong end of the stick... I'd made the wrong assumption that you were browsing/posting here on the machine you're talking about.
 
> The rest is just about that RSA key fingerprint and if i say Yes, it accepts it and then goes back to console. When i type logout, it says that it was successfully disconnected from SSH and then i type logout again and i logout normally.
 
Right, so that's working properly yes? You mentioned '..and then goes back to console'... this has me worried that you're not realising you've SSH'd back to your own machine and thus have succesfully achieved a connection? Particularly given that you earlier said:
 
> Well it does connect locally but it refuses local connection or something like that...
 
...what did that mean?
 
Mathew

---

### Post by CrustyDOD on 2006-01-25
>  Well it does connect locally but it refuses local connection or something like that...
Ignore this line, my bad i mixed up something...

This is the deal, from start so that we don't have any confusion anymore ;)

I type: **ssh 127.0.0.1**

and the respond i get is:

**The authenticity of host '127.0.0.1 (127.0.0.1)' can't be established.**
RSA key fingerprint...

It does create RSA key fingerprint even tho that the connection can't be established and if i say Yes to creating RSA key fingerprint, it successfully creates one. Then it simply goes back to bash line or whatever you call that.

Now if i type "logout" i get message saying that i was successfully disconnected from SSH.

I'll attach pics tommorow so that you'll see excatly what happens!

---

### Post by MJN on 2006-01-25
Believe it or not it's working, and you're logging in via an SSH tunnel, but simply back into your own machine!!!

The first line is not saying the connection can't be established, it's merely saying that the *authenticity* of the host cannot be established i.e. it is claiming to be a particular machine and is providing an RSA key but your client has no way of validating it - it is thus asking you whether to accept it and carry on. By saying 'yes' your client is taking a signature of the server and should not ask you again...

Then, once you've given your password you're logged in! Whilst you think you're 'back to the bash prompt' you're actually seeing the prompt on the machine through the SSH tunnel!

Don't believe me? Try the following (forgive me detailing everything, but then we know where we stand):

1) Starting from scratch, move to your home directory (**cd ~**)
2) Create a directory (**mkdir test**)
3) Move into that directory (**cd test**) - your prompt should indicate you being 'sat' in that directory (e.g. **mathew@rugrat:~test$**)
4) SSH to your machine (**ssh 127.0.0.1**) and login

What does the prompt say? No doubt something like **mathew@rugrat:~$**

Note how it doesn't include **test**? That's because you've SSH'd into your machine and its dropped you in your home directory (as it's configured to do)!! When you type **logout** you're closing the SSH tunnel and now you're back where you left off... with the **mathew@rugrat:~test$ **prompt!

The confusion is likely coming from the fact that you're SSHing into your own machine hence the machine names in the prompt aren't changing making it look like you've not gone anywhere... But the above test shows you have!

Normally, you'd SSH from another machine so the dialogue would go something like this:

mathew@rugrat:~$ [B]ssh somemachine
[/B]mathew@somemachine's password:[B]<password>
[/B]No mail
Last login blah blah blah
mathew@somemachine:~$     <at this point you're in 'somemachine' via the SSH tunnel - the prompt shows this>
mathew@somemachine:~$ **...**
mathew@somemachine:~$ **<lots of commands and messing around>**
mathew@somemachine:~$ **...**
mathew@somemachine:~$ **logout**
Connection to somemachine closed.
mathew@rugrat:~$     <now you're back in rugrat>

Does this make sense?

Mathew

P.S. Of course, all this has nothing to do with why connections from Putty and other machines aren't working, however lets at least establish a local connection (which I think you can, I just need to convince you of that!) before moving on...
P.P.S. Next time you're down in the basement change **LOGLEVEL** in /etc/ssh/sshd_config to **VERBOSE**, try the above and even attempts from other machines, and then grab a copy of /var/log/auth.log as we'll be needing that next... ;)

---

### Post by CrustyDOD on 2006-01-26
So true, stupid me!
Was so concentrating on "can't be established" that i didn't really see the word "The authenticity of host"...

Yes, local connection works just fine!

And i just solved the problem! Stupid me changed hardware in between and somehow my TCP/IP manual configuration was deleted and router assigned local IP to my PC. This local IP was not the one i'm using and as such it was blocked from server by firewall cause i'm allowing only my local IP to have access over SSH to server.

I checked the AUTH logs and i saw no attempts from this PC to server so i checked local IP..

All i can say: OMG!:rolleyes:

Now that TCP/IP is configured manually, everything works!

Thanks for help!!

---

### Post by MJN on 2006-01-26
Ah bonza - glad to hear you're working!
 
Also glad to have helped you see the light at the end of the (SSH) tunnel... [/cheese] ;) 
 
Mathew
 
P.S. As for the underlying problem being a change of hardware and a firewall why oh why did you not mention this in your first post? This information could not have been more relevant!! :mad:

---

### Post by CrustyDOD on 2006-01-26
heh i didn't change server hardware but PC's (desktop) hardware. Didn't hit me that settings were changed...

Oh well, we are all just human heh

Thanks again!

---

