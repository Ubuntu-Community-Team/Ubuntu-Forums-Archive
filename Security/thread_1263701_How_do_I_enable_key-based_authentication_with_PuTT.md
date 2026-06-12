---
title: "How do I enable key-based authentication with PuTTY on XP?"
date: 2009-09-11
forum: Security
---

### Post by mrcoulson on 2009-09-11
I am trying to set up SSH key-based authentication.  I use PuTTY on my XP machine to get to my Ubuntu server.  I have found a few tutorials around the web, but many seem to tell me different steps.  My excellent Official Ubuntu Server Book tells me how to do it from an Ubuntu client, but not from Windows.  So, what I really need is a simple set of directions written for the lowest possible level of intelligence because that's me.

And if I ever meet you in real life, I'll buy you a drink or some cake or wings.

Jeremy

---

### Post by i.r.id10t on 2009-09-11
The keys used in Putty are different from your Linux key.

Or rather, after providing a windows user a copy of my linux key it wouldn't work.

Have to create a key using the putty tools (look on the putty download site).

Once you've got your key, create a profile in putty and look in the window on the elft - under SSH there is an Auth section, you can browse for your key there.

---

### Post by Bachstelze on 2009-09-11
> **i.r.id10t said:**
> 
Have to create a key using the putty tools (look on the putty download site).

You can also convert your OpenSSH key in the putty format.

---

### Post by cariboo on 2009-09-11
I just happened to do what you are asking a couple of hours ago. If you downloaded the putty installer you should have a program called Pageant, run that to generate the key, then copy it to ~/.ssh/authorized_keys on the remote computer you are setting ssh up on.

---

### Post by Bachstelze on 2009-09-11
> **cariboo907 said:**
> I just happened to do what you are asking a couple of hours ago. If you downloaded the putty installer you should have a program called Pageant, run that to generate the key, then copy it to ~/.ssh/authorized_keys on the remote computer you are setting ssh up on.

The program used to generate keypairs is puttygen, not pageant.

---

### Post by cariboo on 2009-09-12
Oops, you're right. I generated the key last week, and got it working today.

---

### Post by bodhi.zazen on 2009-09-13
> **Bachstelze said:**
> You can also convert your OpenSSH key in the putty format.

using puttygen

[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

[http://rnc.lbl.gov/~jhthomas/public/sshtricks.html](http://rnc.lbl.gov/~jhthomas/public/sshtricks.html)

[http://quark.humbug.org.au/publications/notes/bofh/msg00059.html](http://quark.humbug.org.au/publications/notes/bofh/msg00059.html)

---

### Post by mrcoulson on 2009-09-14
> **cariboo907 said:**
>  ~/.ssh/authorized_keys
Where is this directory?  I don't see it.  Should I just make one?  Does it go in /home/me ?

Jeremy

---

### Post by mrcoulson on 2009-09-14
And do I somehow have to enable this?  I've saved my key, but I'm still asked for a password when opening the connection on my iPhone.  Do I need to tell the server somehow not to ask for passwords for SSH and only allow users with keys?

Sorry if my questions are retarded.  It's all very new to me.

Jeremy

---

### Post by mrcoulson on 2009-09-14
Okay, it's now not asking for a password on my iPhone because I disabled passwords in the config file for sshd.

Now in iSSH on my iPhone, I connect and it asks for my login.  I enter that.  Then I'm told "Connection Failed: Server unexpectedly closed network connection."  

Do I need to specify something else?  I can connect with the key internally on the network here, but outside it doesn't appear to be working.

Frustration level: high.

Jeremy

---

### Post by mrcoulson on 2009-09-14
Also, if I try 

sudo service sshd reload

I get

sshd: unrecognized service

Jeremy

---

### Post by bodhi.zazen on 2009-09-14
I can not tell from your posts what you have done and what you have not.

I suggest you read this :

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

In order to use keys you :

1. Generalt a key pair.

2. Transfer the public key to your server. You save the public key on the server in /home/hour_user/.ssh

You can do this manually or use 

ssh-copy-id -i ~/.ssh/your_key_name you@server

which will do it automatically.

Once keys are working, disable password login.

[SSH/OpenSSH/Configuring - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring") 

3. Import the key to putty.

Not sure where you are on those steps or what you have done.

```
sudo /etc/init.d/ssh restart
```

Use tab completion =)

---

### Post by mrcoulson on 2009-09-14
Well, I actually created DSA keys.  This was the only way I could get it to work with the app on iPhone.  Now I can't get on with PuTTY.  It keeps saying "Server refused our key."

I'm thinking I'm barking up the wrong tree and should just go back to Windows severs.

Jeremy

---

### Post by bodhi.zazen on 2009-09-14
So the key is working from a Linux client ?

You need to import the key to putty, as outlined in the links I gave you.

---

### Post by mrcoulson on 2009-09-14
Dear God!  I think I have it!  A long time ago, I added the keys to my authorized_keys file with a line between each one, like this:

here's a key

here's another key

Then I changed it so they were all on the same line, like this:

here's a key here's another key

Now I've just put them on different lines with nothing between, like this:

here's a key
here's another key

THAT works.  iPhone logs in.  PuTTY logs in.  Sweet.

Now, let's see what happens when I take away password logins...

Jeremy

---

### Post by mrcoulson on 2009-09-14
Okay!  Here's the other problem.  When I do this, my FTP stops working.  I use SFTP.  Is there something I need to change?  I don't see a place for putting a key in FileZilla.

Jeremy

---

### Post by bodhi.zazen on 2009-09-14
> **mrcoulson said:**
> Okay!  Here's the other problem.  When I do this, my FTP stops working.  I use SFTP.  Is there something I need to change?  I don't see a place for putting a key in FileZilla.

Jeremy

Use Winscp , it will use your putty keys and has a graphical interface.

[http://winscp.net/eng/download.php](http://winscp.net/eng/download.php)

---

### Post by mrcoulson on 2009-09-15
I got it with PuTTY's Pageant program.  It also saves my keys for my PuTTY sessions so I don't have to enter a passphrase.  Neato.

Thanks for the assistance.  If I ever am in Montana, I'll buy you lunch.

Jeremy

---

