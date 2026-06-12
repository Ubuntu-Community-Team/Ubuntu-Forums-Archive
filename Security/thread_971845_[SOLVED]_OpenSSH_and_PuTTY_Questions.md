---
title: "[SOLVED] OpenSSH and PuTTY Questions"
date: 2008-11-05
forum: Security
---

### Post by scribbles on 2008-11-05
I've been following this [SSH Howto]("https://help.ubuntu.com/community/SSHHowto") and have some questions. I've gotten as far as generating the public/private keys and can see them in ~/.ssh. I chose to use a password for the key to be stored locally. Now what I've done is created a new user for a friend that I want to be able to use PuTTY from his Windows box to login. 

There are public/private keys in my home directory, those are specifically for me, correct?

Do I log in under the new user I created for him and follow the same key generation process (and for each user that needs external access via ssh) and use a password of his choice to lock the private key?

OR, does he just need the public key generated in my home directory to allow him to log into the user I created for him?

I'm confused as to where to go from here... THANKS!

---

### Post by Sarmacid on 2008-11-05
> The private key is kept on the computer you log in from, while the public key is stored on the .ssh/authorized_keys file on all the computers you want to log in to.
You should have him generate his own key pair, and send you only his public key.

---

### Post by scribbles on 2008-11-05
Ahhh, I don't know why I assumed the keys had to come from my machine. 

This is something he'd do with PuTTYgen right? Then I would store the public key he sends me in ~/.ssh?

I know if I want to use the key generated here on another machine with PuTTY I have to convert it to .PPK, would I have to convert the keys he makes back into the form I'm using locally?

---

### Post by scribbles on 2008-11-05
Woops

---

### Post by scribbles on 2008-11-05
I converted the key per [this document]("http://linux-sxs.org/networking/openssh.putty.html"). Whenever I go to login to my machine it asks for my login then tells me "Server refused our key" and goes on to ask for my regular password and lets me log in as usual...?

---

### Post by Sarmacid on 2008-11-06
I used [this guide]("http://sial.org/howto/openssh/publickey-auth/") and the putty manual to set up public key authentication from windows to Ubuntu, however, I wasn't using passwords. Maybe you should try without passwords first and see if it works, then add them.

---

### Post by kevdog on 2008-11-06
You need to append the putty key to the ~/.ssh/authorized_keys file -- just an FYI.  

Actually an explanation
1. Openssh keys and Putty keys are not interchangeable.
2. I would generate openssh keys
Append the openssh public key to the authorized_keys file
3. Import the openssh private key into puttykeygen and convert it to a putty private key
4. Then use the putty private key

I think this is the way to do this.  I haven't done it in a while.

---

### Post by scribbles on 2008-11-06
From reading around, looks like the authorized_keys file has to be made, that's the part I was missing, cat the .pub and convert the private key through puttygen and it should work....

---

### Post by scribbles on 2008-11-06
So here's my steps thus far:
[LIST]
[*]Pub/Priv keys were generated and the pub was added to authorized_keys file which I generated in ~/.ssh
[*]Keys were copied to my windows laptop and the private was converted into a PPK and loaded into Pageant. I even made sure that the key comment matched authorized_keys. 
[*]Connect and enter my login and PuTTY tells me "Disconnected: No supported authentication methods available". I did turn off password auth in sshd_config.
[*]I generated brand new keys in PuTTY and added the generated pub to authorized_keys, loaded the new private into Pageant and attempted login with the exact same result...
[/LIST]

I can't figure out whats roadblocking me here?

---

### Post by kevdog on 2008-11-07
I retrieved this from the Putty documentation:

8.2.12 Dealing with private keys in other formats

Most SSH-1 clients use a standard format for storing private keys on disk. PuTTY uses this format as well; so if you have generated an SSH-1 private key using OpenSSH or ssh.com's client, you can use it with PuTTY, and vice versa.

However, SSH-2 private keys have no standard format. OpenSSH and ssh.com have different formats, and PuTTY's is different again. So a key generated with one client cannot immediately be used with another.

Using the ‘Import’ command from the ‘Conversions’ menu, PuTTYgen can load SSH-2 private keys in OpenSSH's format and ssh.com's format. Once you have loaded one of these key types, you can then save it back out as a PuTTY-format key (*.PPK) so that you can use it with the PuTTY suite. The passphrase will be unchanged by this process (unless you deliberately change it). You may want to change the key comment before you save the key, since OpenSSH's SSH-2 key format contains no space for a comment and ssh.com's default comment format is long and verbose.

PuTTYgen can also export private keys in OpenSSH format and in ssh.com format. To do so, select one of the ‘Export’ options from the ‘Conversions’ menu. Exporting a key works exactly like saving it (see section 8.2.8) - you need to have typed your passphrase in beforehand, and you will be warned if you are about to save a key without a passphrase.

Note that since only SSH-2 keys come in different formats, the export options are not available if you have generated an SSH-1 key.

---

### Post by scribbles on 2008-11-07
That's basically the process I've been following. One of the cool features in PuTTYgen is that when you load a private key it automatically shows you the public key output specifically for posting in an OpenSSH authorized_keys file yet still nothing.

---

### Post by scribbles on 2008-11-07
IT WORKS!

A friend had me grep the logs to see what was going on and there was a permissions error accessing authorized_keys. chmod'd the file and restarted ssh and it works!

---

