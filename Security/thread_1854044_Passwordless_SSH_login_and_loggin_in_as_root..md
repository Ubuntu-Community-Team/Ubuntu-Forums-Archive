---
title: "Passwordless SSH login and loggin in as root."
date: 2011-10-03
forum: Security
---

### Post by rs2k on 2011-10-03
I use a passwordless SSH login using a shared RSA key on my VM linux installs. Assuming my home desktop is 100% secure, is there any risk to using this to remotely connect to a server with a public IP?


When I connect and need to run commands as root I generally just use "sudo su -l" instead of typing sudo before everything I do. If a person knows my password they can effectively become a root user by typing that command, so what's the difference between actually logging in as root and a user that has root equivalent permissions?

---

### Post by collisionystm on 2011-10-03
I guess the big difference is just the fact that 'root' is disabled. Everyone on the planet knows the account name root for hacking, but they do not know a personalized username. Thus it is much harder to attempt a break into your system.

---

### Post by rs2k on 2011-10-03
That's the only thing I could think of. Instead of knowing the username I'd have to know the account name of the user that has access to run as root.


I understand the risks of using root. If I'm not careful I could blow something up. I'm not worried about user error, it's security risks I'm worried about.

---

### Post by rs2k on 2011-10-03
What is the difference between using

sudo -i
and
sudo su -l

?

---

### Post by Dangertux on 2011-10-03
> **rs2k said:**
> I use a passwordless SSH login using a shared RSA key on my VM linux installs. Assuming my home desktop is 100% secure, is there any risk to using this to remotely connect to a server with a public IP?


When I connect and need to run commands as root I generally just use "sudo su -l" instead of typing sudo before everything I do. If a person knows my password they can effectively become a root user by typing that command, so what's the difference between actually logging in as root and a user that has root equivalent permissions?


Well the first assumption is a pretty big one.

I won't say there is no risk there are always risks. SSH keys can be sniffed, man in the middle attack, etc. So yes there is a risk. How much of a risk, well who do you have mad at you? :-P

As far as the usage of sudo su vs sudo, that's debatable and is more of a physical security feature. In terms of an ssh compromise a compromise against a sudoer is just as effective as a compromise against the root user. If that makes sense. In any case it's a far cry from best practices but probably a sustainable risk for your purposes.

---

### Post by Jonathan L on 2011-10-04
> **rs2k said:**
> I use a passwordless SSH login using a shared RSA key on my VM linux installs. Assuming my home desktop is 100% secure, is there any risk to using this to remotely connect to a server with a public IP?


When I connect and need to run commands as root I generally just use "sudo su -l" instead of typing sudo before everything I do. If a person knows my password they can effectively become a root user by typing that command, so what's the difference between actually logging in as root and a user that has root equivalent permissions?

Hi rs2k

It's worth noting that shared-key ssh login is pretty widespread, for example at Amazon Web Services, where most Ubuntu images give you passwordless login as user 'ubuntu', with sudo privileges.  And as these are on known blocks of IP addresses, they are routinely under attack.  I don't know whether they get cracked very often, but it's a good question, probably mostly related to the size of keys chosen.  I'd be very interested to hear other views on this topic.

One of the differences between sudo su -l and sudo is where any shell history might be recorded, where "oops it went to my home directory" aims, and so on.  Personally I'm not dogmatic on the difference, and think the simplicity of a big sharp axe sometimes makes one more careful than when one has some processes as root and some without.

Just some thoughts.

Kind regards,
Jonathan.

---

### Post by CharlesA on 2011-10-04
Find more info about sudo -i vs sudo su (I use sudo -i) [here]("https://help.ubuntu.com/community/RootSudo").

Is there a reason you are using a passprase-less key?

I use one for doing automated backups.

---

### Post by rs2k on 2011-10-04
Thanks for all the info.

The reason I'm doing it is for automated backups using rsync through SSH from my hosted dedicated server to my home computer.

---

### Post by CharlesA on 2011-10-04
Ah ok. You should be ok as long as you keep the private key secure.

EDIT: Also if you are only connecting from one IP, you can set the firewall to only allow that IP to help prevent bruteforce attempts (which would fail, but could clog your log files)

---

### Post by rs2k on 2011-10-04
My home desktop would be the largest problem. Anyone who has access to it would have access to everything. I think that's secure enough for a hosted dedicated server hosting a few small eCommerce sites though.

---

### Post by Dangertux on 2011-10-04
EDIT : Nevermind I reread and it makes more sense now.

Honestly passphrase-less keys are probably more secure unless your pass-phrase is ridiculous, generated key will be much stronger. Since most pass phrases don't have enough entropy to really take full advantage of the encryption and key generation method.

---

### Post by CharlesA on 2011-10-04
> **rs2k said:**
> My home desktop would be the largest problem. Anyone who has access to it would have access to everything. I think that's secure enough for a hosted dedicated server hosting a few small eCommerce sites though.

That's the main problem - physical access = root access anyway.

+1 to dangertux.

---

### Post by rs2k on 2011-10-04
My eCommerce sites don't handle customer money exchanges. I let other sites like paypal do that for me. I've used authorize/net in the past, but I didn't feel comfortable with it. My sites merely hold the products and allow customers to check order status/history.


I obviously can't control physical access to the server itself, but physical access to my home computer is as secure as it can be. I'm the only one who ever touches it. Unfortunately, I'm using windows because I can't figure out how to make 4 monitors work the way I want them to on any linux gui.

---

### Post by CharlesA on 2011-10-04
> **rs2k said:**
> My eCommerce sites don't handle customer money exchanges. I let other sites like paypal do that for me. I've used authorize/net in the past, but I didn't feel comfortable with it. My sites merely hold the products and allow customers to check order status/history.


I obviously can't control physical access to the server itself, but physical access to my home computer is as secure as it can be. I'm the only one who ever touches it. Unfortunately, I'm using windows because I can't figure out how to make 4 monitors work the way I want them to on any linux gui.

Should be fine then. If the machine at home was an actual "server" you could put it behind a locked door or something to help restrict physical access.

---

