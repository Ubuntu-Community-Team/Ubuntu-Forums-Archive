---
title: "Man in the Middle Attack"
date: 2014-12-05
forum: Windows
---

### Post by ooboontwo on 2014-12-05
Hello,

I recently received the following warning message when attempting to connect to one of my servers via ssh:

[ATTACH=CONFIG]258409[/ATTACH]

I wrote down the rsa key (edit: 'fingerprint') it gave me, hit cancel and checked it against the server's public key (locally). The keys DO NOT MATCH, which seems to indicate a 'Man in the Middle Attack.' However, now that I know someone is 'doing something nasty,' how do I bypass them so that I am able to connect to my server using ssh?

Thank you for your help!

---

### Post by seabird22 on 2014-12-05
> **ooboontwo said:**
> Hello,

I recently received the following warning message when attempting to connect to one of my servers via ssh:

[ATTACH=CONFIG]258409[/ATTACH]

I wrote down the rsa key (edit: 'fingerprint') it gave me, hit cancel and checked it against the server's public key (locally). The keys DO NOT MATCH, which seems to indicate a 'Man in the Middle Attack.' However, now that I know someone is 'doing something nasty,' how do I bypass them so that I am able to connect to my server using ssh?

Thank you for your help!

For how long were you connecting with no error, using the same computer and software, from the same client connection, before you received the warning message? 

Are you trying to connect to your ssh server from your workplace or a public wifi hot spot? try using a different ISP and see if you get the same result.

---

### Post by ooboontwo on 2014-12-08
> **seabird22 said:**
> For how long were you connecting with no error, using the same computer and software, from the same client connection, before you received the warning message?

Over a year.

> Are you trying to connect to your ssh server from your workplace or a public wifi hot spot? try using a different ISP and see if you get the same result.

I am connecting from an office complex. I will try connecting from my house and report back.

---

### Post by ooboontwo on 2014-12-09
I tried connecting from another ISP and received the same fraudulent host fingerprint. Obviously, I didn't get the security breach message because it was the first time I was trying to connect from that machine but the host key was the same (and it is NOT the real host key of my server).

Also, I connect to the server through DynDNS, and I tried changing the hostname there but received the same fraudulent host key, which seems to indicate that this attacker has my external IP and is connecting straight from there.

So, back to my original question: How do I kick this guy out? Is there some way to blacklist his rsa key and get around him to my actual server? The server is not located in an area that is easy to work on, that is why I normally do everything through SSH.

Any thoughts are appreciated.

Blessings,
Cody

---

### Post by kpatz on 2014-12-09
You said you connect through DynDNS.  What happens if you connect directly to the server's IP?  Maybe your DNS record got compromised, and is sending you someplace other than your server.

Can you put your private key on another machine and connect from there, to see if it's something on your machine that's redirecting your connection?

---

### Post by ooboontwo on 2014-12-09
I have tried the IP as well as the DNS, it does the same thing. Currently, I am logged in to my server through SSH (via DNS). There was no security warning this time and I verified the fingerprint using: 'ssh-keygen -l -f /etc/ssh/ssh_host_rsa_key.pub' once inside.

But this is what happens, it works for a little bit and then it seems the attacker gets in the middle again and I receive the security warning box and hit 'Cancel,' not wanting to compromise my credentials. So, sometimes I receive the warning and other times I do not.

As far as putting the key on another machine, I don't know how to do that (as I've never had to before). Instructions or a link would be awesome if you think I should try this next.

Blessings,
Cody

---

### Post by Lars Noodén on 2014-12-09
You could probably use agent forwarding ([-A](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh.1.html)) to avoid needing to copy your private key from your client to an intermediate machine.  

I'm not up on networking at all but you might see if the output from [traceroute](http://linux.die.net/man/8/traceroute) is ok.  What kind of network is the destination machine on?

---

### Post by kpatz on 2014-12-09
> **ooboontwo said:**
> I have tried the IP as well as the DNS, it does the same thing. Currently, I am logged in to my server through SSH (via DNS). There was no security warning this time and I verified the fingerprint using: 'ssh-keygen -l -f /etc/ssh/ssh_host_rsa_key.pub' once inside.

But this is what happens, it works for a little bit and then it seems the attacker gets in the middle again and I receive the security warning box and hit 'Cancel,' not wanting to compromise my credentials. So, sometimes I receive the warning and other times I do not.Do you use the same key to connect to other servers, or just this one?

Also, note that MITM attacks are a bigger issue if you're using password authentication rather than public keys.  If your private key has a good passphrase, and/or you don't keep it on the server, it's unlikely to be compromised even via a MITM attack.  If you don't use this key anywhere else (or in just a few places where you can change it easily), try logging in when you get the "wrong" fingerprint (click No so you don't update PuTTY's fingerprint cache) and then poke around to see if you're on a different box.  Check the ssh_host_rsa_key.pub to see if it's different.  You can always generate a new key and delete the old one when you're on the "correct" server.  Just don't type any sensitive information like passwords or passphrases while in the suspicious session (i.e. don't use sudo and type in your password).

> As far as putting the key on another machine, I don't know how to do that (as I've never had to before). Instructions or a link would be awesome if you think I should try this next.

Blessings,
CodyCopy putty.exe and the .ppk (private key) file you're using onto another Windows PC, set up the session and try logging in from that machine.  Ideally from a different network/ISP.  See if you get the same host key discrepancy.

Can you give more details on the server?  Is it hosted, dedicated, virtual, or your own box?  One possibility, if it's hosted, is maybe there's more than one server behind a load balancer, and sometimes you connect to one or the other.

When you get the "wrong" fingerprint, is it always the same "wrong" fingerprint each time, or does it change?

---

### Post by bapoumba on 2014-12-09
*Thread moved to **Windows**.*

---

### Post by ooboontwo on 2014-12-09
> **Lars Noodén said:**
> You could probably use agent forwarding ([-A]("http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh.1.html")) to avoid needing to copy your private key from your client to an intermediate machine.  

I'm not up on networking at all but you might see if the output from [traceroute]("http://linux.die.net/man/8/traceroute") is ok.  What kind of network is the destination machine on?

The destination machine is a desktop connected to a router which has IP passthrough enabled to it as the default server from the external IP address.

---

### Post by ooboontwo on 2014-12-09
> **bapoumba said:**
> *Thread moved to **Windows**.*

Alright... moving this thread to Windows from Security seems off to me. The problem isn't just on Windows. I can't connect via SSH on my iPhone either, or through any other Linux box. In fact, I don't think my problem has anything to do with Windows at all. The fact that I'm connecting via Putty on a Windows system seems irrelevant.

EDIT: I don't mean to sound rude, I just want my thread noticed by the right people.

---

### Post by bapoumba on 2014-12-09
> **ooboontwo said:**
> Alright... moving this thread to Windows from Security seems off to me. The problem isn't just on Windows. I can't connect via SSH on my iPhone either, or through any other Linux box. In fact, I don't think my problem has anything to do with Windows at all. The fact that I'm connecting via Putty on a Windows system seems irrelevant.

EDIT: I don't mean to sound rude, I just want my thread noticed by the right people.
Well, the screenshot in OP is from windows, such are some .exe app install recommendations. Fits to the Windows area to me.

---

### Post by Lars Noodén on 2014-12-09
> **ooboontwo said:**
> The destination machine is a desktop connected to a router which has IP passthrough enabled to it as the default server from the external IP address.

Can another machine on your LAN be ARP spoofing?  Do you get the same intermittent problem while on the same LAN or is it only ever via the router?

---

### Post by ooboontwo on 2014-12-10
> **kpatz said:**
> Do you use the same key to connect to other servers, or just this one?

I just used whatever key was generated when SSH was installed during the Ubuntu Server installation. My understanding was that it generates a random key, yes? In other words, I don't ever specify a particular key when I build a new server box.

> Also, note that MITM attacks are a bigger issue if you're using password  authentication rather than public keys.  If your private key has a good  passphrase, and/or you don't keep it on the server, it's unlikely to be  compromised even via a MITM attack.  If you don't use this key anywhere  else (or in just a few places where you can change it easily), try  logging in when you get the "wrong" fingerprint (click No so you don't  update PuTTY's fingerprint cache) and then poke around to see if you're  on a different box.  Check the ssh_host_rsa_key.pub to see if it's  different.  You can always generate a new key and delete the old one  when you're on the "correct" server.  Just don't type any sensitive  information like passwords or passphrases while in the suspicious  session (i.e. don't use sudo and type in your password).

I guess I'm using password authentication. I hate to sound so amateur but I'm certainly no expert when it comes to SSH. When I follow your instructions and select "No," the SSH terminal just prints, "login as:"

Normally, I would log in with my credentials but if I'm not connected to my actual server isn't that dangerous? I guess I'm not sure how to poke around without giving the fraud-box my credentials.

> Can you give more details on the server?  Is it hosted, dedicated, virtual, or your own box?  One possibility, if it's hosted, is maybe there's more than one server behind a load balancer, and sometimes you connect to one or the other.

The server is a custom-built desktop that I installed Ubuntu server on myself.

> When you get the "wrong" fingerprint, is it always the same "wrong" fingerprint each time, or does it change?

The 'wrong' fingerprint is always the same.

> **Lars Noodén said:**
> Can another machine on your LAN be ARP  spoofing?  Do you get the same intermittent problem while on the same  LAN or is it only ever via the router?

I have never encountered this error while connecting to the server on the LAN.

---

### Post by kpatz on 2014-12-10
> **ooboontwo said:**
> I just used whatever key was generated when SSH was installed during the Ubuntu Server installation. My understanding was that it generates a random key, yes? In other words, I don't ever specify a particular key when I build a new server box.Ok, you and I are talking about different keys then.  There's a key generated when the OpenSSH server is installed, which is what generates the fingerprint that your client checks to detect that you're connecting to the correct box.  The key I was talking about is a key you would have set up to use as authentication when logging into the server via ssh, instead of using a password.> I guess I'm using password authentication. I hate to sound so amateur but I'm certainly no expert when it comes to SSH. When I follow your instructions and select "No," the SSH terminal just prints, "login as:"And after that it asks for a password, or a passphrase?  If it asks for a password, and it's the same password you'd use for sudo, then you're using password, not key-based authentication.> Normally, I would log in with my credentials but if I'm not connected to my actual server isn't that dangerous? I guess I'm not sure how to poke around without giving the fraud-box my credentials.Yes, that's the reason for the server key in the first place, to warn you that you're about to give your password to a box you don't want to trust.

So, to rephrase my prior question, do you use those credentials (password) anywhere else?  Or do you use a specific password to log into that box and you don't use the same password anywhere else?

Next time you connect and get the wrong key, try logging in with random credentials, or your username but the wrong password.  Does it let you in?  If it does, you know you have an imposter set up to intercept your password.  Even if it doesn't, if they intercepted your credentials, you gave them the wrong password so they won't be able to do much with it.> The server is a custom-built desktop that I installed Ubuntu server on myself.Maybe you should check to see if it was hacked and anything installed on it that doesn't belong.

You may also want to create a private/public key in PuTTY (use puttygen) and set that up so you can log in without using your password.  When you run puttygen, click Generate, follow the prompts, give it a passphrase and a comment and then save the private key and it will create a private key in a .ppk file that you tell PuTTY to use when logging into the box (in the SSH Auth section of Putty's settings).  The public key will appear in a box that you can copy and paste ("Public key for pasting into OpenSSH authorized_keys file").  Create a file on the server called ~/.ssh/authorized_keys (that's a directory called .ssh in your home directory, create it with 700 permissions) and paste the public key into that.  If the file already exists, add the new key to the end.  After doing this, you should be able to log in without having to use your password.  You'll be asked for your key's passphrase if you gave it one, but that info never touches the server.

[ATTACH=CONFIG]258485[/ATTACH]

Add the private key to your setup in PuTTY:

[ATTACH=CONFIG]258486[/ATTACH]

Once you do this, and next time you connect to the "wrong" box, you'll know right away if it's a different box since your key based login won't work, unless the hacker clones your .ssh folder into the imposter box.

---

### Post by ooboontwo on 2014-12-10
OK, thank you for clarifying. Yes, I am using password-based authentication. I tried logging into the presumed 'fraud-box' with a random username and password. It returned an Access Denied message.

To answer your question about the login credentials being unique: I am not using this username/password combo anywhere else, to log in to anything else.

At this time, I don't really want to switch over to key-based authentication either. I just want to be able to access my server as I have for over a year. I know the fingerprint on my server-box does not match the one that Putty is warning me about when attempting to connect. I know I don't trust that fingerprint and don't believe I'm actually connected to my server. Obviously, I don't know what to do next besides simply wait for the MITM to give up. I'd rather take a proactive step in resolving this issue though. Of course, having limited experience in this area I don't know what my options are, really.

Would key-based authentication get me around this MITM? If so, I'd be happy to set it up, but if it is just going to give me the same kind of error, why bother?

Thank you for taking all this time to help me out. I really appreciate it. I am bringing the server to my office so that I can work on it there. Let me know what you think I should try next.

Blessings,
Cody

---

### Post by Lars Noodén on 2014-12-10
Ok, that's a good sign that you don't get the fake server when connecting on your LAN.  Don't log into the fake server with any real credentials, you won't get in, but the attacker will then be able to get into your real server using them.  (If you try logging in with made-up credentials you might then check /var/log/auth.log when you get home to see if anyone has been trying to get in with the made-up credentials and what ip address/network they are coming from. ) 

Since you mention that you still get the fake server when trying to connect from other networks but not on your LAN, that puts the problem closer to your server than to your client, so possibly it is at your ISP.  This may be something for your ISP's network administrator(s) to take care of, because it shouldn't be happening.

---

### Post by ooboontwo on 2014-12-10
> **Lars Noodén said:**
> Ok, that's a good sign that you don't get the fake server when connecting on your LAN.  Don't log into the fake server with any real credentials, you won't get in, but the attacker will then be able to get into your real server using them.  (If you try logging in with made-up credentials you might then check /var/log/auth.log when you get home to see if anyone has been trying to get in with the made-up credentials and what ip address/network they are coming from. ) 

Since you mention that you still get the fake server when trying to connect from other networks but not on your LAN, that puts the problem closer to your server than to your client, so possibly it is at your ISP.  This may be something for your ISP's network administrator(s) to take care of, because it shouldn't be happening.

OK. /var/log/auth.log confirms that someone is definitely 'doing something nasty.' The log shows that a rotation of unknown IPs have been trying to get in to the server over the course of the past few days. We're talking about multiple login attempts every second, continuously for the last few days.

Here is a snippet of the output:

> Dec 8 00:49:34 mazhome12 sshd[10679]: Failed password for root from 103.41.124.38 port 33354 ssh2
Dec 8 00:49:34 mazhome12 sshd[10679]: pam_winbind(sshd:auth): getting password (0x00000388)
Dec 8 00:49:34 mazhome12 sshd[10679]: pam_winbind(sshd:auth): pam_get_item returned a password
Dec 8 00:49:34 mazhome12 sshd[10679]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (1), MTSTATUS: MT_STATUS_NO_SUCH_USER, Error message was: No such user

This kind of output repeats over and over again with a rotating port number. Then, the IP changes and the ports continue to rotate for awhile and then it changes again.

And a video showing just how many entries there are when using 'cat /var/log/auth.log' to view the contents...

[video=youtube;v-RUJ4jENys]https://www.youtube.com/watch?v=v-RUJ4jENys&amp;feature=youtu.be[/video]

That video is mainly just for fun (poor quality, so text is unreadable). I felt a little sick when I saw the output though. It really looks like someone is trying to force their way into my system.

EDIT: Also, I forgot to mention it but as you can see, someone is trying to get in as 'root' user. Yikes!

---

### Post by Lars Noodén on 2014-12-10
The more one looks the more break-in attempts one can spot.  It's the nature of being on the net.  But there are more things that can be done to mitigate the probes and attacks.  

It is considered good practice to have [PermitRootLogin no](http://manpages.ubuntu.com/manpages/trusty/en/man5/sshd_config.5.html) on your server to eliminate even the chance of someone getting in that  way, if you haven't set that yet.  Eventually, unless your situation is unusual, you can turn off password authentication and allow only keys.  That stops password guessers completely.  

Also, iptables can do rate limiting to lock out attempts coming in faster than x per second or y per minute.  UFW has a primitive for that, which is "sudo ufw limit ssh" which defaults to 6 per 30 seconds per ip address.  

Also, fail2ban gets mentioned a lot but you might look at sshguard first.  That scans the logs and then uses iptables to block persistent failed attempts.  But as you notice, they rotate ip addresses and that makes the attack harder to block.  

Are any of the ip addresses coming from your same ISP?  You can use [whois](http://manpages.ubuntu.com/manpages/trusty/en/man1/whois.1.html) to look up which ISP is responsible for a given ip, if any look close but you are not sure.

---

### Post by kpatz on 2014-12-10
> **ooboontwo said:**
> OK, thank you for clarifying. Yes, I am using password-based authentication. I tried logging into the presumed 'fraud-box' with a random username and password. It returned an Access Denied message.

To answer your question about the login credentials being unique: I am not using this username/password combo anywhere else, to log in to anything else.Did you take note of what the random username you used was?  Check your server's auth.log to see if any attempts were made to log in using that same username.  Maybe try it again this time with a different username that you would recognize if you see it in your logs afterward.

Attempts on the root account are common on servers that have their ssh service open to the internet.  This is why Ubuntu in particular disables root logins by default.> Would key-based authentication get me around this MITM? If so, I'd be happy to set it up, but if it is just going to give me the same kind of error, why bother?It won't stop the MITM attempts or the errors, but it will prevent the attacker from getting usable credentials.  The way key authentication works in ssh is the private key stays on your client (machine running PuTTY) and your public key is on the server you're logging in to.  The two keys are related in that anything encrypted with one can only be decrypted with the other, but it's nearly impossible given one of the two keys to extrapolate the other.  So, even if a MITM occurs and you attempt to log in to an attacker's box, they won't get anything useful that they can log in with.  And if they manage to get into your server, all they can get is your public key, which can't be used to gain any access to anything--only the private key will.

The only thing passed between the client and the server when logging on using keys is an encrypted token.  Your client (PuTTY) encrypts this token with your private key and then sends it to the server, which then attempts to decrypt it using the public keys stored in the authorized_keys file.  If it is able to, it lets you log in.  This token is useless outside the transaction, and nothing of the private key gets sent over the wire.

Also, if you set up the key credentials on your PuTTY and server, and you connect to the MITM server, you can try logging in and see if it works.  If it does, you're either on your server or they copied your public key from your server to the attack server.  If you get to a shell, you can do some looking around.  But chances are the MITM box won't recognize your key and it'll revert to a regular password login prompt (don't be fooled and enter your password if this happens!)

---

### Post by ooboontwo on 2014-12-11
> **Lars Noodén said:**
> The more one looks the more break-in attempts one can spot.  It's the nature of being on the net.  But there are more things that can be done to mitigate the probes and attacks.  

It is considered good practice to have [PermitRootLogin no]("http://manpages.ubuntu.com/manpages/trusty/en/man5/sshd_config.5.html") on your server to eliminate even the chance of someone getting in that  way, if you haven't set that yet.  Eventually, unless your situation is unusual, you can turn off password authentication and allow only keys.  That stops password guessers completely.

I have now set PermitRootLogin to 'no.'

I will also work on setting up key-based authentication today.

> Also, iptables can do rate limiting to lock out attempts coming in faster than x per second or y per minute.  UFW has a primitive for that, which is "sudo ufw limit ssh" which defaults to 6 per 30 seconds per ip address.

I ran 'sudo ufw limit ssh' in the terminal and received a confirmation message. Is that all I need to do?

> Also, fail2ban gets mentioned a lot but you might look at sshguard first.  That scans the logs and then uses iptables to block persistent failed attempts.  But as you notice, they rotate ip addresses and that makes the attack harder to block.

I also installed sshguard. Now that it is installed do I need to make special configurations or should the default config work OK for me?

> Are any of the ip addresses coming from your same ISP?  You can use [whois]("http://manpages.ubuntu.com/manpages/trusty/en/man1/whois.1.html") to look up which ISP is responsible for a given ip, if any look close but you are not sure.

All the IP addresses are coming from China/Hong Kong, so none are with my ISP (AT&T).

Thanks for all your help. I will continue to Google and research the things you've talked about. I don't want to waste your time when there is so much information on the net, or using 'man sshguard' etc.

Blessings,
Cody

---

### Post by ooboontwo on 2014-12-11
> **kpatz said:**
> Did you take note of what the random username you used was?  Check your server's auth.log to see if any attempts were made to log in using that same username.  Maybe try it again this time with a different username that you would recognize if you see it in your logs afterward.

I do remember the username I tried but I haven't seen it in the log, probably because I physically removed the computer from its usual location and brought it to my office. Still, I will keep an eye on the log and see if this fake username comes up ever again.

> Attempts on the root account are common on servers that have their ssh service open to the internet.  This is why Ubuntu in particular disables root logins by default. It won't stop the MITM attempts or the errors, but it will prevent the attacker from getting usable credentials.  The way key authentication works in ssh is the private key stays on your client (machine running PuTTY) and your public key is on the server you're logging in to.  The two keys are related in that anything encrypted with one can only be decrypted with the other, but it's nearly impossible given one of the two keys to extrapolate the other.  So, even if a MITM occurs and you attempt to log in to an attacker's box, they won't get anything useful that they can log in with.  And if they manage to get into your server, all they can get is your public key, which can't be used to gain any access to anything--only the private key will.

The only thing passed between the client and the server when logging on using keys is an encrypted token.  Your client (PuTTY) encrypts this token with your private key and then sends it to the server, which then attempts to decrypt it using the public keys stored in the authorized_keys file.  If it is able to, it lets you log in.  This token is useless outside the transaction, and nothing of the private key gets sent over the wire.

Also, if you set up the key credentials on your PuTTY and server, and you connect to the MITM server, you can try logging in and see if it works.  If it does, you're either on your server or they copied your public key from your server to the attack server.  If you get to a shell, you can do some looking around.  But chances are the MITM box won't recognize your key and it'll revert to a regular password login prompt (don't be fooled and enter your password if this happens!)

This sounds much better than the way I've been doing it (password  authentication). I will work on setting this up today. Thank you!

---

### Post by kpatz on 2014-12-11
Now that you physically moved the server, what happens if you try to connect to the server's original IP (assuming the server is on a different IP now)?  Or if you use the DNS name, if you didn't re-point it?  It might still route you to the false server.

Also, at the server's original location, you said it's behind a router with the port forwarded, right?  Are there any other machines at that location, also behind the router?  Does the router have wireless, and is it properly secured? (i.e. WPA2 and a good passphrase?)

It's possible the MITM is being done at the router, especially if it wasn't properly secured.

Once you get the keys set up, I think you'll like it better.  If your PuTTY machine is secure (i.e. at home with no one else that has access to it) you could even get away without using a passphrase, and then you can log in without having to enter a password or passphrase.  If you do use a passphrase, you can use an SSH agent (such as Pageant for PuTTY) to cache your key, so you only have to enter the passphrase once, and then you can log into any/all boxes that have that key set up on it without entering it again, until you turn off Pageant or reboot your PC.  You can use the same key to access multiple servers, or multiple user accounts on the same server.  Or you could use separate keys, your choice.  I prefer to have a separate key for each client machine, and put it on all the servers I log in to.  That way I can use Pageant or ssh-agent to cache the key and I can log in to server after server without re-entering my passphrase every time.  And if one of my client machines gets compromised (i.e. someone steals my laptop), I can just delete the laptop's public key from the server(s)' authorized_keys file and then it can no longer be used, but I can still log in using the keys on my other clients.

---

### Post by Lars Noodén on 2014-12-11
> **kpatz said:**
> It's possible the MITM is being done at the router, especially if it wasn't properly secured.

That's what I considered at first but there is apparently no spoofing on the LAN itself.  So if it is a router, it is one further out.  It might be the ISP's.

---

### Post by kpatz on 2014-12-11
> **Lars Noodén said:**
> That's what I considered at first but there is apparently no spoofing on the LAN itself.  So if it is a router, it is one further out.  It might be the ISP's.When on the LAN, you aren't going through the router at all, but are connecting directly to the server.  When outside the LAN, you're going through the router.  So it could still be the router.  Are there other machines on the LAN connected to the router?  Is there wireless on the router?

---

### Post by Lars Noodén on 2014-12-12
> **ooboontwo said:**
> 
I ran 'sudo ufw limit ssh' in the terminal and received a confirmation message. Is that all I need to do?

I also installed sshguard. Now that it is installed do I need to make special configurations or should the default config work OK for me?

All the IP addresses are coming from China/Hong Kong, so none are with my ISP (AT&T).


You can double-check UFW with [iptables-save](http://manpages.ubuntu.com/manpages/trusty/en/man8/iptables-save.8.html) and see what it has set for ssh.

```

sudo iptables-save | less

```

There will be a lot of extraneous rules but the ones to focus on will be in the INPUT chain and pertain to port 22.

Looking at sshguard in Ubuntu, it looks like the defaults should work.  But check iptables to be sure that attacks are getting blocked, if you are still getting probed.  

Sometimes it helps to lookup the netblock owner for misbehaving hosts and fire off a polite e-mail to the contact person with a few sample log entries.

---

### Post by Lars Noodén on 2014-12-12
> **kpatz said:**
> When on the LAN, you aren't going through the router at all, but are connecting directly to the server.  When outside the LAN, you're going through the router.  So it could still be the router.  Are there other machines on the LAN connected to the router?  Is there wireless on the router?

The LAN has its own router, but that one seems not to be involved.  If there is a problem with the router, it is likely with the next layer out or more likely it is another host on that layer because it looks like the external address is getting spoofed.  Perhaps in the networking subforum someone would know what the best action is.

---

