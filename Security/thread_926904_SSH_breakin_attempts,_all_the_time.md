---
title: "SSH breakin attempts, all the time"
date: 2008-09-22
forum: Security
---

### Post by CaptSaltyJack on 2008-09-22
I've got a couple computers on my home LAN, and pretty much the only ports that are open (ssh, smtp, http) go to my Ubuntu box which is locked down tight.  I get login attempts all the time, almost every day, e.g.:

```

Sep 20 15:07:57 myhost sshd[11358]: Failed password for invalid user adam from 211.157.110.226 port 48927 ssh2
Sep 20 15:07:59 myhost sshd[11360]: Invalid user admin from 211.157.110.226
Sep 20 15:08:01 myhost sshd[11360]: Failed password for invalid user admin from 211.157.110.226 port 49671 ssh2
Sep 20 15:08:04 myhost sshd[11362]: Invalid user admin from 211.157.110.226
Sep 20 15:08:06 myhost sshd[11362]: Failed password for invalid user admin from 211.157.110.226 port 50435 ssh2
Sep 20 15:08:08 myhost sshd[11364]: Invalid user admin from 211.157.110.226
Sep 20 15:08:10 myhost sshd[11364]: Failed password for invalid user admin from 211.157.110.226 port 51227 ssh2
Sep 20 15:08:12 myhost sshd[11366]: Invalid user admin from 211.157.110.226
Sep 20 15:08:14 myhost sshd[11366]: Failed password for invalid user admin from 211.157.110.226 port 51968 ssh2
Sep 20 15:08:17 myhost sshd[11368]: Invalid user admin from 211.157.110.226
Sep 20 15:08:19 myhost sshd[11368]: Failed password for invalid user admin from 211.157.110.226 port 52726 ssh2
Sep 22 08:37:40 myhost sshd[29260]: Failed password for invalid user root from 151.13.82.194 port 48500 ssh2
Sep 22 08:37:43 myhost sshd[29262]: Failed password for invalid user root from 151.13.82.194 port 49083 ssh2
Sep 22 08:37:46 myhost sshd[29264]: Failed password for invalid user root from 151.13.82.194 port 49614 ssh2

```

I get all kinds of strange usernames too: fluffy, adam, marine, condor.  My question is, how are these people getting my hostname/IP address if it's not publicized anywhere?  And secondly, are these attack bots?  Or are they real people trying to log in?

---

### Post by aurelieng on 2008-09-22
Hello,

Everyone can reach you through your IP address, which is public, even if their is no "directory of IP address". Your login attempts might be both real people mistyping the IP of the computer they want to ssh to, or real bots scanning the network, looking for a server listening, port 22, then trying to guess username/passwords combinations.

The quickest way to solve this problem is to have SSH listening to a non-standard port. You can also use fail2ban for instance, if several login attempts comes from the same IP address.

Good luck :)

---

### Post by CaptSaltyJack on 2008-09-22
I use denyhosts and like it quite a bit.

I know my IP is public but how do they find it?  How does one issue a command like "show me all public IPs"?

---

### Post by qstraza on 2008-09-22
Well every ISP has range of ips dedicated to them, they must be publicly known, so if someone scans your isps range, you are in there too ;>

---

### Post by .nedberg on 2008-09-22
Probably someone trying to get into your server.

Things you can do:
[LIST=1]
[*]Move ssh to a different port
[*]Install fail2ban and set it up with ssh
[*]Configure portknocking
[/LIST]

On my ssh servers I use 1 and 2 if I can, or only 2.

---

### Post by AusIV4 on 2008-09-22
So long as you have a solid password, this is nothing to be concerned about. I changed the ssh port on my system and it stopped entirely, but that's no substitute for a strong password.

---

### Post by .nedberg on 2008-09-22
Of course, a strong password is obligatory! And prevent root log in while you are at it.

---

### Post by qstraza on 2008-09-22
I have iptables rules, to limit login rate. Moved port on very high, higher than 65000 and i use key for auth, password is disabled, and AllowUser me, and no one else.

You should use keys for auth too;>

---

### Post by CaptSaltyJack on 2008-09-22
I'm pretty locked down.  I have zero concern of any of these fools actually getting in. :)  I definitely use AllowUsers to limit it to just me.  And I have denyhosts installed which will automatically throw abusers into /etc/hosts.deny.

Key auth is cool, I use it at home and on my laptop to connect to my Linux box.  But I dunno if I want to put keys on my machine at work or not.  I guess there's no harm in it, I'm only generating private/public keys for my actual work computer, and if I ever quit my job, I can just remove the pub key from my Linux machine's authorized_keys file.

EDIT: How do I make sshd accept ONLY keys and not username/password based logins?

---

### Post by qstraza on 2008-09-22
> **CaptSaltyJack said:**
> I'm pretty locked down.  I have zero concern of any of these fools actually getting in. :)  I definitely use AllowUsers to limit it to just me.  And I have denyhosts installed which will automatically throw abusers into /etc/hosts.deny.

Key auth is cool, I use it at home and on my laptop to connect to my Linux box.  But I dunno if I want to put keys on my machine at work or not.  I guess there's no harm in it, I'm only generating private/public keys for my actual work computer, and if I ever quit my job, I can just remove the pub key from my Linux machine's authorized_keys file.

EDIT: How do I make sshd accept ONLY keys and not username/password based logins?
you can put key on USB...


sshd_config:
PasswordAuthentication no
UsePAM no

---

### Post by CaptSaltyJack on 2008-09-22
Ahh, key on USB, good idea!  I'd have to have both the private and public key on there, right?

Actually, I was thinking of using a passwordless key on my work machine, that's why I was hesitant.  But I just generated a RSA2 key with a passphrase, and I use Pageant (Windows) so I only have to load up the key into memory once.  Then PuTTY will grab the auth from Pageant and automatically log me in.  This works pretty well for me, as anyone who grabs my work machine's private/public key will still need a pass phrase to do anything with them.

---

### Post by qstraza on 2008-09-22
u need just a private key, public is on the server side.
after login as:
ssh -p port user@host -i /path/to/key

---

### Post by HermanAB on 2008-09-22
These dumb attacks always run on port 22.  So a really simple solution is to change the SSH listen port to something else, eg. 2222.

There are an infinite number of complicated solutions to the problem, but none simpler than this.

---

### Post by CaptSaltyJack on 2008-09-22
Problem is, my workplace blocks all outgoing ports except ports 22, 25, 80, 443, maybe 8000 and 8080, and maybe a couple others I'm not aware of.  So I can't just pick something like port 67000, because I won't be able to get to my machine from work. :)

---

### Post by qstraza on 2008-09-22
well 67000 does not exist anyway :p, it goes up to 65535

---

### Post by CaptSaltyJack on 2008-09-22
No, that's the idea.. port 67000, then NO one can log in, not even me. ;)  Ultimate security!

---

### Post by qstraza on 2008-09-22
lol:p dont run sshd :p thats the ultimate sec;>

---

### Post by hyper_ch on 2008-09-22
moving ssh port to something else adds nothing for security...

automated script-kiddy attacks are nothing you need to be afraid of if you use denyhosts or fail2ban...

---

### Post by qstraza on 2008-09-22
it makes your reading of logs alot easier

---

### Post by hyper_ch on 2008-09-22
> **qstraza said:**
> it makes your reading of logs alot easier

that's true and it's a good reason to change port number... however I prefer have it on 22 as it's standard... however changing ports does not make ssh any safer.

---

### Post by qstraza on 2008-09-22
> **hyper_ch said:**
> that's true and it's a good reason to change port number... however I prefer have it on 22 as it's standard... however changing ports does not make ssh any safer.
well in theory it does not, but i doubt that anyone will wait 10h to scan one host from 1 to 65535. Alot of scanners dont scan high ports by default... So i think it is safer from that point of view.

---

### Post by hyper_ch on 2008-09-22
qstraza: against automatic script kiddy attacks you don't have to worry... those you have to worry about are not the automatic ones and they will find the port where ssh is running... nmap works really great for that ;)

---

### Post by qstraza on 2008-09-22
well scan host with nmap from 1 to 65535 ;)
it will keep you busy for a while.
Anyway, i agree that script kiddies are not a thread, but still, i dont like to get brute forced. No one does.

---

### Post by hyper_ch on 2008-09-22
it does not take that long and it doesn't keep me busy as I don't have to do anything ;)

---

### Post by qstraza on 2008-09-22
im done arguing

---

### Post by vagena on 2008-09-24
Real human hair is in limited supply, so [lace wigs](http://www.cosprops.com/lacewigs.html) are much more expensive; typically they several hundred dollars. [full lace wigs](http://www.cosprops.com) look and feel very natural. However, it is important to know that the quality of your [cosplay wig](http://www.cosprops.com/cosplay-wigs-c-5.html) depends on the origin of the hair used. The cheapest hair comes from Asian countries, but their texture is different from the hair of European women. The best [lace human hair wig](http://www.cosprops.com/lace-human-hair-wigs-c-10.html) is made from European hair but, unfortunately, they cost a small fortune.

---

### Post by qstraza on 2008-09-24
ok what just happend?

---

### Post by CaptSaltyJack on 2008-09-24
Spammer.. I just reported it.

---

### Post by beniji on 2008-09-27
AllowUsers is essential for piece of mind!

---

