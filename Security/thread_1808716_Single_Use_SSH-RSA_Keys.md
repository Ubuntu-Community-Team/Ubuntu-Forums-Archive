---
title: "Single Use SSH-RSA Keys"
date: 2011-07-20
forum: Security
---

### Post by thegodfaza on 2011-07-20
My primary Ubuntu server has SSH exposed to the internet so I can remotely access it. I have configured OpenSSH to use only RSA key authentication. Each computer I use has a separate RSA key unique to it. I also have a unique RSA key on a USB thumb-drive I carry with me. The purpose of the USB key is for emergencies if I have to access the server from some remote system. The problem is that I may not trust the remote machine (university/public library computer for example). What I would like to do is have a set of one-time use RSA keys that, after I log in to SSH with them, are removed from the authorized_keys file. This would hopefully keep my system safe even if the remote machine I was using was compromised and had copied my private key and key-logged the password I used to decrypt it. I would like to have these keys be separate from the keys I have for my trusted computers.

---

### Post by bodhi.zazen on 2011-07-20
Look at your private key, at the very end you will see your user name 

something like user@hostname where user is the user name you used to make the key and hostname is the box you made the key on.

change that to something like

untrusted@crisis

Then before you log out simply

```
sed -i -e '/untrusted/d' ~/.ssh/authorized_keys
```

The key is no longer valid

You can of course script this if you prefer .

---

### Post by thegodfaza on 2011-07-21
Was hoping for some automated system but I guess I can just write a bash script. Thanks for the help.

---

### Post by bodhi.zazen on 2011-07-21
> **thegodfaza said:**
> Was hoping for some automated system but I guess I can just write a bash script. Thanks for the help.

Probably not sufficient demand for one to be coded, and if it were it would probably be a script.

---

### Post by Enoch247 on 2012-11-30
I know this is old, but I am looking to create a similar setup to yours and ran across this.

I know that you can tie certain commands to be executed with ssh keys on a per key basis. What I was planning to do was: upon using a one-time-key, have it setup to execute a script that removes itself from the authorized key file and then starts bash. you could even have one-time-use keys that start restricted shells along side your normal one-time-use keys for times when you just need to grab a file, etc.

---

### Post by thnewguy on 2012-11-30
If you want to automate the process of removing keys, just put the command Bodhi provided above in your .bashrc file. That will rmeove your untrusted key as soon as you login. That way you don't have to remember it.

of courwe if you do this you will be effectively blocking your access to the box, so make sure you don't make any mistakes, get disconnected, etc.

---

### Post by chmac on 2013-01-21
The disconnected warning is perhaps the most important I reckon. For example, today I had an emergency, had to log into our production machine over SSH from a (very) untrusted internet cafe! I've since cycled passwords and so on, but if I had only one key with me, and that key was automatically removed from the system on login, then I'd be screwed if I was disconnected.

Carrying the key on a USB stick is an interesting idea though. I may well look into that if I can figure out how to encrypt it in such a way that it can be decrypted on multiple platforms. Would be a shame to be carrying a "blank" key to the server around... :-)

---

