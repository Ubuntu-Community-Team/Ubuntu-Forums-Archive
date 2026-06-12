---
title: "SSH Keys Issues - continual request for passphrase"
date: 2012-01-26
forum: Server Platforms
---

### Post by np123 on 2012-01-26
Hi there,
 
I am having a few issues on a new server install of 11.10 server edition. As I connect to it from a windows box, I have to use Putty to do so. 
 
Initially, I tried to create a directory .ssh for the keys, and copy the putty key to authorized_keys, but it wouldnt find the key.
 
So then I created a pair of keys on the server which set up my directory and permissions etc, and after doing so copied my unrelated putty key to the authorized_keys file using copy and paste with vim.
 
Now, the key is recognized, but I am asked for my passphrase every time. I changed permissions on the authorized_keys file to 600, so its rw only. Although it reads something like:
 
rw-----  me me 712 authorized keys
 
I thought it would say 600 where it says 712 (or something like). I set the key to me owned by user and group of user (I hadnt set up the user group beforehand though, does this matter?)
 
Does anyone have any idea why it is still asking for my passphrase. It sees the key, accepts it, but asks for the passphrase for the key. Its doing my nut! :-)
 
Many thanks

---

### Post by Lars Noodén on 2012-01-26
600 is the 'rw-----' part of the line.  The 712 is the size of the file in bytes.  

Does it ask you for the key once per connection or more than once per connection?

---

### Post by np123 on 2012-01-26
Hi there, thankyou for the reply. Good, so im not going mad about the file then. It asks me for the key once at login time.
 
I struggled with this on my previous install. I had it working and then after some updates it asked me for passphrase each time.
 
I did wonder if it was something very trivial, like I typed sudo mkdir .ssh/ setting up the .ssh directory as root owner in my home rather than me as the owner? Maybe this doesnt matter.
 
I also wondered if having the additional unused keys was causing the issue, but then if it sees the key in the authorized_keys file I assumed it would accept the passphrase automatically.

---

### Post by kevdog on 2012-01-26
Do a ssh -vvv to get very verbose output and see if the error is produced.  Openssh (the type of ssh ran on ubuntu), and putty keys are different.  From my experience in the past I needed to convert the open-ssh key into a putty key.

The .ssh directory and all its contents should be owned by the user and not root.

---

### Post by np123 on 2012-01-26
Cheers, I'll do this when i get back tonight and post the output here.
 
Thanks for taking the time to respond

---

### Post by np123 on 2012-01-26
As im using putty and a putty generated key i used the event log from that, here is what it said:


2012-01-26 18:58:52	Offered public key
2012-01-26 18:58:52	Offer of public key accepted
2012-01-26 18:59:05	Sent public key signature
2012-01-26 18:59:05	Access granted
2012-01-26 18:59:05	Opened channel for session
2012-01-26 18:59:05	Allocated pty (ospeed 38400bps, ispeed 38400bps)
2012-01-26 18:59:05	Started a shell/command

---

### Post by np123 on 2012-01-26
I deleted the saved putty sessions and re-entered all the info and guess what, it now works. Not sure why, but not too worried.

Thanks for your help

---

