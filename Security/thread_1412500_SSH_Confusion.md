---
title: "SSH Confusion"
date: 2010-02-21
forum: Security
---

### Post by mr-woof on 2010-02-21
Hi all,

I'm sure there is a really easy answer to this, but i'm new to SSH. I've got Ubuntu server 9.10 installed with openSSH in a virtual machine and ubuntu 9.04 desktop in another virtual machine, they can both ping each other fine. 

I can login with a password via SSH to the server, so using the guide in the sticky, i've completed the following steps:

change PasswordAuthentication to no
change loginGraceTime 120 to LoginGraceTime 20
PermitRootLogin to no
change log level from INFO to VERBOSE
Generating SSH Keys
mkdir ~/.ssh
chmod 700 ~/.ssh
ssh-keygen -t rsa -b 4096

it's now i'm stuck, It's obviously using the keys I've created. When I try and login to the server using ssh 192.168.31.167 i'm getting permission denied (publickey).

Do I need to copy a key onto the machine that will be accessing the server? If yes, how the heck do I do it?

---

### Post by x33a on 2010-02-21
Yes you need to have the key on the other computer. To do that you must either have physical access to the machine or be able to access it with a password.

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by mr-woof on 2010-02-21
So if i'm connected to the server using password ssh, what command do I need to enter to get the key onto that machine?

---

### Post by x33a on 2010-02-21
You can simply copy it to the remote server using scp, take a look here:

[http://wiki.archlinux.org/index.php/Using_SSH_Keys](http://wiki.archlinux.org/index.php/Using_SSH_Keys)

---

### Post by 2hot6ft2 on 2010-02-21
[http://help.ubuntu.com/community/SSH/OpenSSH/Keys](http://help.ubuntu.com/community/SSH/OpenSSH/Keys)

> Saving Keys on Remote Computers

If you can log in to a computer over SSH using a password, you can transfer your RSA key by doing the following from your own computer:

ssh-copy-id <username>@<host>

Where <username> and <host> should be replaced by your username and the name of the computer you're transferring your key to.

You can make sure this worked by doing:

ssh <username>@<host>

You should be prompted for the passphrase for your key:

Enter passphrase for key '/home/<user>/.ssh/id_rsa':

Enter your passphrase, and provided host is configured to allow key-based logins, you should then be logged in as usual.



---

### Post by bodhi.zazen on 2010-02-21
> **2hot6ft2 said:**
> [http://help.ubuntu.com/community/SSH/OpenSSH/Keys](http://help.ubuntu.com/community/SSH/OpenSSH/Keys)

+1

From the client use ssh-copy-id , then test the key works, then disable the password.

I would also point out, with Virtual Machines on your LAN, there is less a need for keys. If you forward port 22 from your router to the Server, in addition to keys, you may want to consider denyhosts, fail2ban, or a few rules for iptables.

---

### Post by mr-woof on 2010-02-21
I tried that command

ssh-copy-id <username>@<host>

I got an error message back saying couldnt get to port 22

Do you run that command when connected to the server via password ssh?

Bodhi, this is a just a learning exercise on how to get ssh up and running using keys. I'll then install denyhost and fail2ban. Once i'm happy that's running ok, i'll install it all on the actual server i'm going to be using :)

---

### Post by FuturePilot on 2010-02-21
> **mr-woof said:**
> I tried that command

ssh-copy-id <username>@<host>

I got an error message back saying couldnt get to port 22

Do you run that command when connected to the server via password ssh?

No, you run that on the client.

---

### Post by mr-woof on 2010-02-21
Hmm, ran the command on the client machine. 

I'm now getting Error: no identities found

---

### Post by bodhi.zazen on 2010-02-21
> **mr-woof said:**
> Bodhi, this is a just a learning exercise on how to get ssh up and running using keys. I'll then install denyhost and fail2ban. Once i'm happy that's running ok, i'll install it all on the actual server i'm going to be using :)

You do not need both , one or the other.

If you have the time learn iptables. It is a steep learning curve, but a few rules for iptables will block ssh cracking attempts, and once you learn that you do not need to install additional applications or services.

In the time it takes to install and configure UFW, denyhost/failtoban , etc etc you can learn one tool (iptables) and do most anything you need.

---

### Post by mr-woof on 2010-02-21
Bodhi, thanks for the advice. I'm just trying bits out at the moment, once i've got it up and running i'll have a look for some iptables tutorials.

---

### Post by bodhi.zazen on 2010-02-21
I understand , I am just trying to save you some time, and as you seem interested in learning, trying to point you in what the "right direction" rather then installing a service, such as fail2ban, and not understanding what you are doing with your firewall.

With that said, fail2ban is a sophisticated application and does have some features iptables lacks ;)

My point, I guess, it is a very good first step to understand network protocols and iptables, at least a little, if you are interested in learning to run servers.

---

### Post by mr-woof on 2010-02-21
Bodhi, I really do appreciate any advice that you can give me. I'm trying my best to learn about Linux servers, ssh etc. I totally agree about network protocols/Ip tables etc

Now, If i can just get the key on the client I'll be up and running with the ssh server :)

edit: this looks a decent tutorial
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by x33a on 2010-02-21
To make your setup more secure, change the default port. Also, you can use ssh-agent or keychain to remember the passphrases.

---

