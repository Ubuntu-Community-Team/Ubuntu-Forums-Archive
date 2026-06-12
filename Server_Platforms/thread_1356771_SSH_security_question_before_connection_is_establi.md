---
title: "SSH security question before connection is established"
date: 2009-12-16
forum: Server Platforms
---

### Post by kewlrichie on 2009-12-16
Hey guys I am sure someone could answer this pretty quickly I was wondering when I access my work server from home and i ssh to the ip and port is the first initial username and password sent over clear text until the ssh connection is made? or is it encrypted from the very first connect even before successful login?

because i was wondering if i log into my account which is a able to be a sudoer if it is being sent in plain text they would be able to man in the middle me and have full access to the server. If this is true I would probably make limited account (not able to sudo) log into that first then change user to the account I am able to sudo from then have full access from there.

---

### Post by cdenley on 2009-12-16
The username and password are NOT sent in plaintext.

---

### Post by Dark_Stang on 2009-12-16
The only thing sent in plain text (IIRC) is the encryption Key that you will be using when you first establish the connection.

---

### Post by craigp84 on 2009-12-16
Unfortunately the attack you describe is technically possible with SSH.

While it's true that no details are sent plaintext, so a casual snooper / packet sniffer wont be able to uncover your password from just viewing the traffic, by implementing a man-in-the-middle attack they would gain access to your details.

This is why, when you first login to a host, SSH prompts you and says, hey the fingerprint of the remote key is xxx:xxx:xxx:xxx:xxxx are you sure this is right / do you wish to continue.

You're supposed to verify this fingerprint against the remote host -- via another channel, say physically logging onto the console of the host to read the fingerprint of the keypair and writing it down, then compare against this when you first try to ssh in.

SSH will store the fingerprint in ~/.ssh/known_hosts by default, so for all future connections it knows you trust the remote host's key. This also protects you against me breaking into your isp's routers and setting up a MITM attack against you, because next time you connect, my key's fingerprint *will be different* from the one you have stored already. SSH will scream blue murder in this case and even refuse to allow you to continue.

You can see the behaviour by editing the known hosts file and just change 1 character on the line for your chosen remote host, now try to SSH in.

Hope it helps

p.s. this is a very difficult attack to implement generally and by verifying your fingerprints you can mitigate the risk of this attack.

---

### Post by osjak on 2009-12-17
[Set up the key authentication to SSH]("http://www.ibm.com/developerworks/library/l-keyc.html") and turn off password logins. This will prevent any chance of brute forcing the login. This measure will also prevent you from giving your password to the man-in-the-middle, even if you ignore the warning that Craig described above.

See here for more information:
[http://docstore.mik.ua/orelly/networking_2ndEd/ssh/ch03_10.htm](http://docstore.mik.ua/orelly/networking_2ndEd/ssh/ch03_10.htm)

---

