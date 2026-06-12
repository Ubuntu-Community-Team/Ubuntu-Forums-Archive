---
title: "SSH port suggestion"
date: 2006-09-15
forum: Server Platforms
---

### Post by the_0ne on 2006-09-15
I'd like some advise on changing my ssh access port.  I was hacked last week.  I really am not sure how the hacker got in, but it looked like a script kiddie.  They logged in and installed some port scanners and basicly didn't touch anything else.

I know, I know, you can never trust that you found everything, so yes, I did wipe and re-install.  I'm on a fresh copy now.  :)

Now to my question.  Is using another port for ssh a good thing to do?  Of course I would have to open it through my router and of course have to remember what the port is to use the ssh client.  I'm just wondering if it's a good idea, as sort of a security measure?

Also, is there a site I can check out with a list of ports I could use?  I could try at random, but don't want to block a port that is being used for something else.

Thanks again for the help everybody...

---

### Post by kidders on 2006-09-15
Hi there,

Avoiding conventional ports *might* throw off a few idiots, but in general, any open port will attract attention ... particularly since you'll probably only have one or two.

How did you get hacked? (Did someone guess your password?!)

My Linux box gets a **very** large number of login attempts most weeks. A while ago I implemented a crude (but suprisingly effective) way of blocking naughty users, by monitoring my SSH logs for login failures and automatically adding an iptables rule to drop incoming packets from any computer that caused more than one error. I found that, after a while, I could identify particular IP ranges SSH login attempts tend to come from, and manually block all traffic from them.

One other thing worth mentioning is that if you generate hashes for all your critical system files, you can use cron to periodically check for intrusions, by running a comparison for you. There are several apps that do this sort of thing, if you don't have the time to write it yourself.

Hope this helps.

---

### Post by mitch.c on 2006-09-15
> **the_0ne said:**
> Is using another port for ssh a good thing to do?  Of course I would have to open it through my router and of course have to remember what the port is to use the ssh client.  I'm just wondering if it's a good idea, as sort of a security measure?

Using another port is a great idea, but as mentioned earlier the most you can hope for is to slow people down.

You didn't mention what ssh authentication you used, but I would suggest disabling password authentication in favor of public key authentication.

If you don't know how, read this: [https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

> **the_0ne said:**
> Also, is there a site I can check out with a list of ports I could use?  I could try at random, but don't want to block a port that is being used for something else.

Generally your safe to use a port above 1024. But here's the authoratative reference: [http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers)

---

### Post by the_0ne on 2006-09-16
Thanks for the replies.  

*How did you get hacked? (Did someone guess your password?!)*

That's a good question.  I am no linux newbie, but when it comes to security, I'm more a programmer than a sysadmin.  I'll tell you this, I made a dumb mistake.  I had a user (my kid) that has the same username as the pwd.  I had this machine for myself (and my kids) to mess around at first, I never kept it on other than when they were messing with it.  Then I brought it to my office and kept it as more of a server (and you guessed it) forgot to remove the user account.

My problem is this, I did a dumb thing by having a uname and pwd the same, but how did the hacker even find out a username???  I am almost positive the user got in through ssh.

*You didn't mention what ssh authentication you used, but I would suggest disabling password authentication in favor of public key authentication.*

I'll have to look into that, thanks for the link.

Thanks again for the replies...

---

### Post by kidders on 2006-09-16
Oh no! So someone literally walked in the front door?!! ](*,) Nasty!

> how did the hacker even find out a username?

If I let my SSH server sit online unguarded, I will tend to get people that run through half the alphabet looking for a suitable username/password combination. Such break-in attempts might last over 30 minutes! Accordingly, I tend to try to avoid "obvious" usernames.

mitch.c is right on the money with his password authentication comment, by the way :-)

If it were *my* linux box, and I were worried about brute force attacks and other unauthorised access over SSH, I'd strongly suggest at least the following:

[LIST=1]
[*]Continue using port 22 ... after all, it's convenient! There's no particular reason why using another is a bad idea though (as long as it's big number!).
[*]Write a script to monitor your SSH daemon logs for things like "Invalid user guest from 203.129.200.125" or "authentication failure; logname= uid=0". It should extract the IP addresses from such lines and do an "iptables -I INPUT ... -j DROP" for persistent offenders.
[*]Steer clear of usernames that are peoples' first names or dictionary words.
[*]Never ever ever allow dictionary word passwords.
[*]Disable authentication by password altogether ... key-based authentication is infinitely more convenient anyhow!
[*]Give yourself added peace of mind by examining critical system files for unauthorised changes on occasion. If someone knowledgeable breaks into your system, they will invariably do something to allow them in easier the next time, maybe with escalated privileges.
[/LIST]

Security is pretty close to the heart of any Linux user ... after all, it's part of the reason most of us chose the platform! Feel free to post back if you need any more specific advice :-)

**Edit:** Have a quick read about SSH's features ... you can, for instance, only allow remote access by certain users, if you want.

---

### Post by the_0ne on 2006-09-16
> **kidders said:**
> Oh no! So someone literally walked in the front door?!! ](*,) Nasty!

If I let my SSH server sit online unguarded, I will tend to get people that run through half the alphabet looking for a suitable username/password combination. Such break-in attempts might last over 30 minutes! Accordingly, I tend to try to avoid "obvious" usernames.

I guess that must be the only explanation and the username was very easy to figure out.  If the cracker dude had some kind of script that goes through common names, it would have been a cakewalk.  :( 

> 
mitch.c is right on the money with his password authentication comment, by the way :-)


Yeah, I'm going to look into that as soon as I have some time.

And I'll take all yours suggestions to heart, believe me.

As to specific help, I can imagine I'll need it, so I'll probably be posting back.

Thanks again all...

---

### Post by the_0ne on 2006-09-16
> **kidders said:**
> Oh no! So someone literally walked in the front door?!! ](*,) Nasty!

If I let my SSH server sit online unguarded, I will tend to get people that run through half the alphabet looking for a suitable username/password combination. Such break-in attempts might last over 30 minutes! Accordingly, I tend to try to avoid "obvious" usernames.


I'm looking over the openssh documentation and it's bringing up a question.  By what I described, does it really sound like all the person that broke into my machine had to do was run some kind of brute-force program that generates logins.  Once he found a valid username, then all he had to do was figure out the pwd, which was the same as the username, real hard one there...  :(

Does that sound like what happened?  I'm thinking he had some kind of magical way to break in, did I really leave it that easy for them???

---

### Post by mitch.c on 2006-09-16
> **the_0ne said:**
> I'm looking over the openssh documentation and it's bringing up a question.  By what I described, does it really sound like all the person that broke into my machine had to do was run some kind of brute-force program that generates logins.  Once he found a valid username, then all he had to do was figure out the pwd, which was the same as the username, real hard one there...  :(

Does that sound like what happened?  I'm thinking he had some kind of magical way to break in, did I really leave it that easy for them???

umm. yup. ;)

Especially easy when the username is a first name, and/or the password is the same as the username. Big no-no.

---

### Post by the_0ne on 2006-09-16
> **mitch.c said:**
> You didn't mention what ssh authentication you used, but I would suggest disabling password authentication in favor of public key authentication.

If you don't know how, read this: [https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)


> **kidders said:**
> mitch.c is right on the money with his password authentication comment, by the way

Ok, I was able to get rsa key-based authentication through ssh working now instead of just plain old password.  I even disabled plain old password authentication in the sshd_config file.  The documentation was great for showing me how to do it.  (In fact I had to do it twice because I didn't like my first passphrase.)  However, the documentation doesn't explain what happens now when I try to ssh from somewhere that I did not copy the key to.

I think this is how it works.  If I try to ssh from a machine that does not have the key, I immediately am denied. (Good thing.) However, if I ssh from my laptop (where the key was already copied.) then the key check succeeds, but then I still need to type in the passphrase?  So, it's sort of a double layer of protection.

Is there anything I'm missing on how this works?

---

### Post by mitch.c on 2006-09-16
> **the_0ne said:**
> However, the documentation doesn't explain what happens now when I try to ssh from somewhere that I did not copy the key to.
If you disabled password authentication then you will not be able to login from any machine that does not have a copy of your private key.

> **the_0ne said:**
> 
I think this is how it works.  If I try to ssh from a machine that does not have the key, I immediately am denied. (Good thing.) However, if I ssh from my laptop (where the key was already copied.) then the key check succeeds, but then I still need to type in the passphrase?  So, it's sort of a double layer of protection.

Is there anything I'm missing on how this works?
Basically your right. When you access the the remote machine via ssh:

1. You enter your passphrase, and a signature is generated using your private key.
2. The encrypted signature is sent to the remote machine. Your passphrase is *never* sent across the wire.
3. The remote machine receives the encrypted signature, and checks to see if the supplied key is acceptable (authorized_keys).
4. The remote machine checks whether the signature is correct (using your public key).
5. If 3 and 4 are true, then you are authenticated.

So you see why it's more secure? No password or passphrase is ever sent accross the wire. Data used for authentication is encrypted first and then sent over an encrypted channel. Both a private key and public key are requrired and are at separate ends of the communication channel.

Someone jump in if I missed anything.

---

### Post by the_0ne on 2006-09-16
> **kidders said:**
> My Linux box gets a **very** large number of login attempts most weeks. A while ago I implemented a crude (but suprisingly effective) way of blocking naughty users, by monitoring my SSH logs for login failures and automatically adding an iptables rule to drop incoming packets from any computer that caused more than one error. I found that, after a while, I could identify particular IP ranges SSH login attempts tend to come from, and manually block all traffic from them.

Where do the ssh logs reside?  I have nothing in /var/log and I've tailed /var/log/messages and /var/log/syslogs and see nothing when I ssh in.  Is there something I need to change in the ssh config.  I've checked sshd_config and see nothing there about a log path.

---

### Post by mitch.c on 2006-09-16
> **the_0ne said:**
> Where do the ssh logs reside?  I have nothing in /var/log and I've tailed /var/log/messages and /var/log/syslogs and see nothing when I ssh in.  Is there something I need to change in the ssh config.  I've checked sshd_config and see nothing there about a log path.
sshd info is logged to /var/log/auth.log

Logging is controlled by:
```
# /etc/ssh/sshd_config
SyslogFacility AUTH #default
LogLevel INFO #default... try VERBOSE (see man sshd_config)
```

You can get a look at what's in there now:
```
cat /var/log/auth.log | grep sshd
```

---

### Post by the_0ne on 2006-09-17
> **mitch.c said:**
> sshd info is logged to /var/log/auth.log

Logging is controlled by:
```
# /etc/ssh/sshd_config
SyslogFacility AUTH #default
LogLevel INFO #default... try VERBOSE (see man sshd_config)
```

You can get a look at what's in there now:
```
cat /var/log/auth.log | grep sshd
```

Thanks for the info.  Oh yeah, I'm getting hit a lot from the same ip address.  How do I find out info on this ip address?  I can tell they are using some kind of program to brute force their way in because the username attempts are in alphabetical order and each attempt is within 3 seconds of each other.  All the same ip.  It's 210.187.84.14.  How do I find info on this and report them?

Thanks again for all the help everybody.

---

### Post by mitch.c on 2006-09-17
> **the_0ne said:**
> 210.187.84.14.  How do I find info on this and report them?

There are lots of whois lookups on the web, or if you want a pretty gnome GUI, you could try:
System -> Administration -> Network Tools -> Lookup

---

### Post by kidders on 2006-09-18
Hi there,

I just thought I might mention this:

```
$ whois 210.187.84.14
% [whois.apnic.net node-2]
% Whois data copyright terms    http://www.apnic.net/db/dbcopyright.html

**inetnum:      210.187.84.0 - 210.187.84.127**
netname:      PENGURUSANLEBUHRAYA-TMNET
country:      MY
descr:        PENGURUSAN LEBUHRAYA SDN BHD
descr:        KUALA LUMPUR
admin-c:      RM218-AP
...
...
```

Seems to be a Malaysian SP. Say you were using an iptables-based firewall. You could wave bye-bye to domestic DSL customers from this entire ISP with **iptables -I INPUT -p tcp -m iprange --src-range 210.187.84.1-210.187.84.127 -j DROP**, or by using their netmask.

In terms of what they are running, here is a service list:

```
$ nmap !$
nmap 210.187.84.14

Starting Nmap 4.03 ( http://www.insecure.org/nmap/ ) at 2006-09-18 09:20 IST
Interesting ports on 210.187.84.14:
(The 1667 ports scanned but not shown below are in state: filtered)
PORT      STATE SERVICE
21/tcp    open  ftp
22/tcp    open  ssh
25/tcp    open  smtp
80/tcp    open  http
110/tcp   open  pop3
443/tcp   open  https
10000/tcp open  snet-sensor-mgmt     [Webmin]
```

Quite often, reporting this kind of abuse is not terrible helpful :-( Service providers that receive a lot of complaints often respond with something like "Heh, well, it's probably just some poor soul with a virus. Live with it!".

---

### Post by the_0ne on 2006-09-18
> **kidders said:**
> Quite often, reporting this kind of abuse is not terrible helpful :-( Service providers that receive a lot of complaints often respond with something like "Heh, well, it's probably just some poor soul with a virus. Live with it!".

Thanks for the info.  I had a feeling it wouldn't amount to much, so I'll let it go.  Very useful commands to use, thanks.

I brought the laptop today to work to mess with getting my work machines to connect to it using the rsa keys.  I can see why people opt out of going the extra mile and using rsa key-based authentication, it really is a PIA having to get all the machines to generate the key and then copy it over.

BUT, I'd rather sit at home and watch the **failed** attempts in auth.log than find another pscan2 process taking up 100% of my cpu because I didn't take the extra steps.  ;)

Hats off to you and mitch.c for the help!

---

### Post by mitch.c on 2006-09-18
> **the_0ne said:**
> I can see why people opt out of going the extra mile and using rsa key-based authentication, it really is a PIA having to get all the machines to generate the key and then copy it over.

You really only need *one* key-pair per user. The public key gets copied to the ssh server once. Copy the private key to each machine you want to login from.

For maximum security, keep the private key on an encrypted usb driver (there's a wiki page on that somewhere). You might also want to check out ssh-agent type programs as well.

---

### Post by the_0ne on 2006-09-18
> **mitch.c said:**
> You really only need *one* key-pair per user. The public key gets copied to the ssh server once. Copy the private key to each machine you want to login from.

For maximum security, keep the private key on an encrypted usb driver (there's a wiki page on that somewhere). You might also want to check out ssh-agent type programs as well.

Sorry mitch.c, I'm not understanding what you mean.  I *think* I tried what you said and it's not working.  I'll give you an example...

My laptop, that is the machine that I now have rsa key-based authentication working.  No password authentication at all, it's turned off.

Under my .ssh directory, I have the files authorized_keys, id_rsa and id_rsa.pub (and of course known_hosts).  If I scp the id_rsa (which is the private key) to the machine I want to connect FROM and put it in my the remote machine's .ssh directory.  I do get a passphrase prompt now, which I wasn't getting before, but then I get this...

Permission denied (publickey).

What did work for me, but I had mentioned was a PIA, was I ran the ssh-keygen program on the remote machine (the one I want to connect from to my laptop).  Then I run a ssh-copy-id from the remote machine to the laptop and that enters a line in the authorized_keys file, which then allows me to connect with a passphrase.

Am I taking extra steps that are not needed?

---

### Post by kidders on 2006-09-18
I hope mitch.c doesn't mind me cutting across him, but I just happened to notice your post.

Public/private keypairs are generated on a per-user basis ... effectively, the key *is* your password. What machine you use to generate your keypair is irrelevant. Once you've made one, you can copy it into your home directory on any PC you have an account on.

Once that's ready, you can log in passwordlessly (is that even a word?!) to any machine that is aware of your public key, which you will have copied into your authorized_keys file on that machine.

Does that make any sense?

---

### Post by the_0ne on 2006-09-18
> **kidders said:**
> I hope mitch.c doesn't mind me cutting across him, but I just happened to notice your post.

Public/private keypairs are generated on a per-user basis ... effectively, the key *is* your password. What machine you use to generate your keypair is irrelevant. Once you've made one, you can copy it into your home directory on any PC you have an account on.

Once that's ready, you can log in passwordlessly (is that even a word?!) to any machine that is aware of your public key, which you will have copied into your authorized_keys file on that machine.

Does that make any sense?

It does make sense, I understand more that the key is generated per user (which is something mitch.c mentioned also) however, I'm not sure what I am doing wrong in my case.

machine one is the rsa key-based authentication ssh server.  I have a .ssh/ directory with authorized_keys, id_rsa, id_rsa.pub and known_hosts.

The remote machine I want to ssh FROM, I copied over my id_rsa private key file and mv'd it to .ssh/ (from the ssh server).  But I am still getting the...

Permission denied (publickey).

...error when I try to ssh in from the remote machine to the ssh server.  I think I am missing the part of copying my key to the authorized_keys file on the actual ssh server?  How do I go about that.

btw, the user you are speaking of, I have this same user account on multiple machine, so key should be valid for all.

---

### Post by mitch.c on 2006-09-18
> **the_0ne said:**
> My laptop, that is the machine that I now have rsa key-based authentication working.  No password authentication at all, it's turned off.

Under my .ssh directory, I have the files authorized_keys, id_rsa and id_rsa.pub (and of course known_hosts).  If I scp the id_rsa (which is the private key) to the machine I want to connect FROM and put it in my the remote machine's .ssh directory.

Am I taking extra steps that are not needed?

id_rsa.pub is your public key. This file goes in the .ssh directory you want to login TO (the ssh server).

id_rsa is your identity (private key). This file goes in the .ssh directory on the machine you want to login FROM.

> **the_0ne said:**
> I do get a passphrase prompt now, which I wasn't getting before, but then I get this...

Permission denied (publickey).
What OS are you running on the machine you are trying to access FROM (not the ssh server)?

---

### Post by mitch.c on 2006-09-18
> **the_0ne said:**
> I think I am missing the part of copying my key to the authorized_keys file on the actual ssh server?  How do I go about that.

```

cd .ssh
cat id_rsa.pub >> authorized_keys
```

---

### Post by Dirren on 2008-02-18
I realize I'm late to the discussion but, the_One, did you ever get the certificate-authentication in place for the other machines? 
I'm sort of interested, 'cause I just got hacked in a similar manner as you (forgot to raise the security bar when exposing the machine to the bad guys out there!).

For anyone else out there I can relay a hint to a tool that may come in handy in this context: chkrootkit (just google that and you'll find it).

---

