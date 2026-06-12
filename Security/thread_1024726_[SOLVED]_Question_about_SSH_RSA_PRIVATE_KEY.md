---
title: "[SOLVED] Question about SSH RSA PRIVATE KEY"
date: 2008-12-29
forum: Security
---

### Post by Kissell on 2008-12-29
How important is it to keep the private key private?

I understand that if you use an unencrypted private key (with no passphrase) that it's very important to protect the key, because anyone who gets the key has access to all systems with the correstponding public key...  

But what if you used a passphrase on your private key...  and then your private key was leaked on the internet...  is it really a concern?

I'm just not really sure how things work...  if the passphrase decrypts the key and then the decryption is sent to the server as the private key, then if they guess the passphrase wrong it would be an unsuccessful login attempt at the server, and the server would stop talking to them after a few attempts as long as your using something like "fail2ban".  

So, if you can throw unlimited passphrases at a private key, and try to brute force hack it, so what...  cause you never know if you successfully decrypted it without using it to login to the server, which only allows a few attempts.

Now, if on the other hand, the private key can be brute force hacked, and it be known that the passphrase was entered successfully without any connection to the server, then yes, the security of the private key is extremely important.  

Anyone know which of these two ways the passphrase on the private key works?

---

### Post by insane_alien on 2008-12-29
well, the easy way around bruteforcing is by selecting a suitable password length with plenty of randomness and nonalphanumerics.

if its long enough it'll take longer than the age of the universe to bruteforce it.

---

### Post by Kissell on 2008-12-29
Yeah, I just got some free time, so I've been obsessed with this project of making a server as secure as possible, while still being reasonably usable.  An eight or twelve character mixed passphrase isn't too bad...  but a 100 character one is impractical to type in.

My idea was that I wouldn't have to worry about securing the client PCs, just the server, so long as they don't cache the passphrase...  but it looks like this isn't true...  if the clients are not secured then their compromised keys can become huge holes in my security if the passphrases can be hacked...  I want to make it secure enought hat a super computer would take at least a year to sequentially brute force it...

I did find this great site/table:
[http://www.lockdown.co.uk/?pg=combi](http://www.lockdown.co.uk/?pg=combi)

It also appears that private ssh keys are crackable with brute force without needing to authenticate to the server to verify the crack was successful, at least, i found a program to do that to Putty generated private keys...  so it looks like securing the private key would be ideal, although probably impossible.  So yeah, a large passphrase is looking like the best option...  still, crackable though...

---

### Post by bodhi.zazen on 2008-12-29
May I suggest you take a look at port knocking ?

here is an overview :

[http://www.linuxjournal.com/article/6811](http://www.linuxjournal.com/article/6811)

---

### Post by Dr Small on 2008-12-30
> **bodhi.zazen said:**
> May I suggest you take a look at port knocking ?

here is an overview :

[http://www.linuxjournal.com/article/6811](http://www.linuxjournal.com/article/6811)
There is always kevdog's guide on portknocking also :)
[http://ubuntuforums.org/showthread.php?t=812573](http://ubuntuforums.org/showthread.php?t=812573)

---

### Post by kevdog on 2008-12-30
Not sure if port knocking is applicable to this thread, however if basically opens up a temporary hole in the firewall (using an iptables interface) to allow an incoming connection.  Its usually thought of opening a temporary hole to unmask a listening daemon such as an ssh daemon. The firewall is altered to allow incoming connections from the computer issuing the port knocking request for a specified number of minutes or seconds (this parameter can be set).  The actual port knocker daemon is a listening process, but not in the conventional sense.  Port Knockers can be set up to examine attempted incoming connection requests via examination of log files or it can sniffs all incoming packets "off the wire" using libpcap, not requiring examination of log files.  The actual packet sniffing process takes advantage of a "combination sent" between client and server.  In the traditional sense this used to be a "knock" sequence where the client would try to connect on 3 specific port numbers such as 110, 250, 399 -- Hence the name port knocker.  Modern port knocker implementations such as fwknop actual do the authentication via a single packet.  The packet is encrypted using either AES symmetric encryption of asymmetrically encrypted using GPG.  This makes the actual commands to open the firewall port virtually unaccessible to a rogue third party also capturing packets.  Based on other studies, the presence of this outgoing packet is also very hard to detect compared to random noise.  This identification of a specific port knocking packet -- not the content of the packet -- but the presence of packet being sent by the client -- is an area of ongoing research.  Its the goal to make the presence of this packet indistinguishable from random noise.  

Although port knocking is a great theoretical concept, its acceptance is not widespread.  Many continue to consider this another security via obscurity measure. A debian package is now available for the fwknop port knocking utility.  Client software is available for all platforms. [http://cipherdyne.org/fwknop/](http://cipherdyne.org/fwknop/)

---

### Post by euler_fan on 2008-12-31
> **Kissell said:**
> Yeah, I just got some free time, so I've been obsessed with this project of making a server as secure as possible, while still being reasonably usable.  An eight or twelve character mixed passphrase isn't too bad...  but a 100 character one is impractical to type in.

My idea was that I wouldn't have to worry about securing the client PCs, just the server, so long as they don't cache the passphrase...  but it looks like this isn't true...  if the clients are not secured then their compromised keys can become huge holes in my security if the passphrases can be hacked...  I want to make it secure enought hat a super computer would take at least a year to sequentially brute force it...

I did find this great site/table:
[http://www.lockdown.co.uk/?pg=combi](http://www.lockdown.co.uk/?pg=combi)

It also appears that private ssh keys are crackable with brute force without needing to authenticate to the server to verify the crack was successful, at least, i found a program to do that to Putty generated private keys...  so it looks like securing the private key would be ideal, although probably impossible.  So yeah, a large passphrase is looking like the best option...  still, crackable though...

If there's a problem with Putty's implementation, then perchance Putty is a tool you should stay away from . . . 

The website you link to is all well and good, if they have your private key and it's password protected and they decide it's worth more than a couple of weeks on a really good machine (or set of them) *and your password is ridiculously short relative to the value of what it protects.* And of course, you happen to think there's any value in those estimates anyway.

A more useful estimate would compute the required password length given an alphabet of n characters, a probability p of guessing correctly in a given period of time T (in seconds), and an upper bound on the number of guesses per second B. From there it's a matter of computing the log base n of [(T*B)/p]. I suggest making p < 0.001, B > 100 billion/sec, and T > 31.8 million sec (somewhat larger than a year). Assuming of course, you use pseudo-random passwords and change the password at least once per year.

Note the passwords he computes for are at most eight characters--if you suppose the encrypted version of your private key where to hit the internet, then would you really trust an eight character password? Even a couple extra characters add exponentially to the security of a password without much added complexity (going from eight to ten characters) in any of the scenarios. Lesson: longer is better, pseudo-random is better (within limits).

You're never going to be secure if the client isn't secure . . . period. At some point the data has to exist in RAM or pass through a keyboard and that's the end of it.

---

### Post by Kissell on 2008-12-31
Originally I didn't realize (or it hadn't sunk in) that I could use spaces in a passphrase...  so using a sentence like "Question about SSH RSA PRIVATE KEY!" is actually easy to remember and becomes a very long password in terms of characters...  becomes almost impossible to hack via sequential brute force on characters, although not so difficult with a dictionary attack that creates sentences and assumes spaces and randomizes case...  taking into consideration likelihood of special characters like "!" appearing at the end of a sentence instead of throughout it...  anyway, I was originally thinking of the passphrase more like a password, in which it would need to be something more like "sEEE8#@l!LONGbott0m" which I could never remember, versus something like "? aBoUt SSH RSA Private Key$" which would be a lot easier for me to remember.

But I'm still unhappy about the nature of security...  I want to be able to have total security by only securing the server side...  I know there are big huge holes in my security because my clients aren't securing their PCs...  and I can't do anything about it, and it pisses me off...  all the work I've done to secure things on my end, and it's got huge holes because the clients don't want to be hassled with the inconvenience of security!  argh!

---

### Post by chrestomanci on 2008-12-31
> **Kissell said:**
> I'm just not really sure how things work...  if the passphrase decrypts the key and then the decryption is sent to the server as the private key, then if they guess the passphrase wrong it would be an unsuccessful login attempt at the server, and the server would stop talking to them after a few attempts as long as your using something like "fail2ban".  

So, if you can throw unlimited passphrases at a private key, and try to brute force hack it, so what...  cause you never know if you successfully decrypted it without using it to login to the server, which only allows a few attempts.

Now, if on the other hand, the private key can be brute force hacked, and it be known that the passphrase was entered successfully without any connection to the server, then yes, the security of the private key is extremely important.  

Anyone know which of these two ways the passphrase on the private key works?
The private key is decrypted off line, and then used to connect to the server, so if someone gets hold of your private key protected with a weak password (such as a word in a dictonary), they could use a fast PC to try thousands of possible passwords every second until they find the one that decrypts the key, and then use it once for a successful login to the remote system. In this situation fail2ban would have no effect.

As others have said, you can make your private key more secure, by choosing a better passphrase (such as a longer one, or one that is not just a dictionary word), or by keeping it more secure. Depending on your situation, it may be more secure to chose a really strong passphrase and then write it down, and keep that written note somewhere safe such as in a safe.

Something like:
```
head -c 12 /dev/random | base64
```
Will give you a totally random 16 byte passphrase that will be unguessable by an attacker other than by brute force exhausting the keyspace.

---

### Post by bodhi.zazen on 2009-01-01
> **Kissell said:**
> But I'm still unhappy about the nature of security...  I want to be able to have total security by only securing the server side...  I know there are big huge holes in my security because my clients aren't securing their PCs...  and I can't do anything about it, and it pisses me off...  all the work I've done to secure things on my end, and it's got huge holes because the clients don't want to be hassled with the inconvenience of security!  argh!

EXACTLY !!!

This is why I cringe when I see posts from people wanting to dismantle security because they are "the only one using the computer" as they post on the Ubuntu forums. Or people who think they can "protect" windows by installing antivirus on Linux.

If we have learned nothing from windows, lax security effects all of us.

---

