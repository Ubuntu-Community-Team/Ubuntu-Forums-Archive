---
title: "Trouble with ssh"
date: 2010-05-20
forum: Security
---

### Post by holocene on 2010-05-20
I am having trouble getting ssh working between my two pc's
 

 Both boxes are running Lucid
 Both boxes have a user with same name.
 

 My reason for this is, besides just logging in to my boxes, I want to explore using ssh with rsync.  
 

 What I have done so far:
 
[LIST]
[*]Installed on each box openssh by 	running >sudo apt-get install openssh
[*]verified that I can connect from 	each one to the other by running >ssh username@<other box ip>
[*]on each box, edited /etc/ssh/sshd_config to 	turn off passwords making the line equal to > 	PasswordAuthentication no
[*]on each box, restarted sshd by 	>sudo /etc/init.d/ssh restart
[*]on each box, using the same 	userid, supplying diff passphrase, ran >ssh-keygen -t rsa
[*]from each box, attempt to copy 	public key to the other box by >ssh-copy-id username@<other 	box ip>. **This fails on each box with msg: Permission denied 	(publickey). **
[/LIST]
 

 The result is that I can not ssh from either box to the other box. 



Also, I have repeated these steps and I may need to reset files back to default. Is this necessary? 

 

 What do I need to do to be able to ssh from one to the other and vice versa?  
 

 Is there a special consideration about using the same or different userid's on the boxes?
 

 Any help greatly appreciated.
 Steve.

---

### Post by 2hot6ft2 on 2010-05-20
Copy the keys manually using a usb flash drive/floppy/cd. All done.
Or re-enable password login and transfer them THEN disable it. You disabled it before transferring the keys.
and
no, depending on how you want to do it and what you changed.
transfer the keys
and
no
:popcorn:

---

### Post by holocene on 2010-05-20
> **2hot6ft2 said:**
> Copy the keys manually using a usb flash drive/floppy/cd. All done.
Or re-enable password login and transfer them THEN disable it. You disabled it before transferring the keys.
and
no, depending on how you want to do it and what you changed.
transfer the keys
and
no
:popcorn:

Ok. Kinda got it to work. 

I set up a fresh user on each box, then repeated the steps above IN THE RIGHT ORDER this time. And it worked flawlessly. 

I just have to figure out what is wrong with my initial pair of users. I could not get it to work in the same way. 

How do I start over on them? 

thanks much
steve.

---

### Post by cariboo on 2010-05-20
You should be able to start over again by removing the authorized_keys file in the ~/.ssh directory in each users home directory.

---

### Post by holocene on 2010-05-20
Solved.

Not sure exactly why it is working now, but I set the files in ~/.ssh to zero bytes, then repeated all steps, restarting the server. Did not work at this point. Then I rebooted and tried again to ssh (without password as it should work). i was able to connect from either.

Thanks to all for hints.
Steve.

---

