---
title: "PasswordAuthentication no still allows passwords"
date: 2012-02-09
forum: Server Platforms
---

### Post by thefarelkid on 2012-02-09
I've been getting familiar with Ubuntu Server Edition on a Virtual Box install and getting a lot of my questions solved by tutorials and forums, but I've run into a problem that I can't find an answer to anywhere.  After setting up OpenSSH and generating a rsa key, i turned PasswordAuthentication to no using sudo nano /etc/ssh/sshd_config, I attempt to login through Cygwin on a Win7 machine, and it still asks for a password after seeing that I don't have the key.  I put it in and I'm logged in as if passwords are allowed.  I tried apt-get purge and then installed again, but no luck.  Any ideas?

I forgot to mention, I did restart SSH after updating sshd_config

---

### Post by thefarelkid on 2012-02-11
Bump

---

### Post by azmyth on 2012-02-11
Are you sure it's the login password it's asking for or is it asking for the key passphrase. The key passphrase it should ask for.

---

### Post by thefarelkid on 2012-02-12
The tutorials I was reading told me to leave the key passphrase blank to automate Unison. Thanks for the reply.

---

### Post by azmyth on 2012-02-12
Okay, if you don't set a passphrase it shouldn't prompt you for one. 

Run ssh in debug mode and post the output.

sudo service ssh stop
sudo /usr/sbin/ssh -d

---

### Post by thefarelkid on 2012-02-13
So this is strange.  The first command returns: "ssh stop/waiting" And the second command returns: "sudo: /usr/sbin/ssh: command not found"

I was also looking at the tutorials again for how to turn off password authentication in SSH and I found that they use "sudo nano /etc/ssh**d**/sshd_config" while I was using "sudo nano /etc/ssh/sshd_config".  If I add the d I open a new file in the nano editor.  Without the d, I find the expected file.  Not sure why my install of OpenSSH has this small change.

Again, thanks for the help.

---

### Post by azmyth on 2012-02-13
My bad.

Wrong command forgot the d

sudo /usr/sbin/sshd -d

Your're editing the correct file

---

### Post by gsgleason on 2012-02-13
Are you sure it's using password authentication and not keyboard-interactive?

An easier thing might be to do a verbose connection from the client.

ssh -v user@host

Also, try disabling PAM support in your sshd_config file.  That fixed a user's issue on a mailing list I found while googling: [http://linuxmafia.com/pipermail/conspire/2006-August/002230.html](http://linuxmafia.com/pipermail/conspire/2006-August/002230.html)

---

### Post by thefarelkid on 2012-02-14
azmyth- I am still trying to figure out how to get that output into a text file so I can post it here.  My first time without a GUI to help me.  I've tried "sudo /usr/sbin/sshd -d > log.txt" and "sudo /usr/sbin/sshd -d | tee log.txt", and variations on that.  no dice.

gsgleason- Running -v on client shows what authentications are valid, "Authentications that can continue: publickey,password" So after looking for the private keys that match the public one offered by the server and not finding it, it goes to the next authentication method and upon me entering the password for that user, I get in, which I don't want.  Also I tried turning PAM to no and still doesn't work.

---

### Post by azmyth on 2012-02-14
You can disregard my commands.

The post gsgleason made will give you the info you need. Does it say it's reading in proper ssh_config file with gsgleason command. Second line.

You should have

PasswordAuthentication no

Please note, if there's a # infront you must remove

For example, you see

#PasswordAuthentication no

You must change to

PasswordAuthentication no

---

### Post by thefarelkid on 2012-02-15
Well that was amazingly simple. Turns out you need to remove the #. I should have known that.  Thank you both for your help.

---

