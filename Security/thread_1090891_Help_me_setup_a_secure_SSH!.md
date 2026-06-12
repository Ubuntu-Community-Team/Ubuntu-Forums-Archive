---
title: "Help me setup a secure SSH!"
date: 2009-03-08
forum: Security
---

### Post by Depressed Man on 2009-03-08
I already have SSH setup, however it's insecure since I never did figure out how to correctly setup the keys. Right now it's just password protected but I would like to have the keys setup as well with my n800 as the server and my laptop or desktop as the client. I'm guessing the instructions below have that as a similar setup.

scp ~/.ssh/id_dsa.pub [email]user@10.0.0.30:/home/user/.ssh[/email]/authorized_keys2

The problem here is I changed my port number. Normally if I were to just ssh connect I would specify -p 80 (say if I choose 80). But I can't seem to find an option for that. -P is the option for scp but I can't seem to figure out where to place it. 

[http://cleardefinition.com/page/Sync_Evolution_and_GPE_on_N800/](http://cleardefinition.com/page/Sync_Evolution_and_GPE_on_N800/)

The instructions here are..

```
Set up passwordless logon to N800 SSH
1.
On your desktop, run ssh-keygen -t and accept the default options. This will create a certificate on your computer that allows it to authenticate without a password. Do not enter a passphrase when asked, or you're basically making this step meaningless. (In theory, you should be able to use an SSH agent or something to let you do this, for better security. I wasn't that picky.)
2.
Now, let's transfer the public certificate to the N800 and authorize it for access. From your PC, scp ~/.ssh/id_dsa.pub user@10.0.0.30:/home/user/.ssh/authorized_keys2 (for OpenSSH aka SSH - if you use dropbear, the file is called authorized_keys - thanks to Chris McNally for the tip!) where 10.0.0.30 is again your N800/Nokia 770 IP address. Use the user password you created before to authorize the transfer.
3.
Let's test to make sure this works. Run ssh user@10.0.0.30 - it should log you on and give you a busybox prompt without asking for a password. If this worked, you're golden, move on. If not, well, I'm not sure what the deal is. Make sure /home/user/.ssh/ exists on the n800/Nokia 770, maybe.

```

The reason why is I want to get GPE ToDo syncing working between my tablet and my desktop. I've also read..

[http://sial.org/howto/openssh/publickey-auth/](http://sial.org/howto/openssh/publickey-auth/)

Can someone help me setup the agent (I would like to have the password security as well). Also what if I already generated a key on the server? 

[https://www.opensync.org/browser/plugins/gpe/README](https://www.opensync.org/browser/plugins/gpe/README)

---

### Post by bodhi.zazen on 2009-03-09
I find the -P needs to be the first argument.

```
scp -P 80 ~/.ssh/id_dsa.pub [EMAIL="user@10.0.0.30:/home/user/.ssh"]user@10.0.0.30:/home/user/.ssh[/EMAIL]/authorized_keys2
```

The directory ~/.ssh must exist on the server (sometimes best to copy it to your $HOME , then ssh in and move the key to authorized_keys ).

Obviously , kame sure the key works before you disable passwords.

---

### Post by hyper_ch on 2009-03-09
setting up ssh key login is this:

client --> computer that you use
server --> computer that you want to login to
user --> the username you want to add it to on the server

(1) generate the key on the client
```

ssh-keygen -t dsa

```

(2) copy and add it on the server
```

cat ~/.ssh/id_dsa.pub | ssh -l user server 'cat && ~/.ssh/authorized_keys'

```

(3) login
```

ssh user@server

```
or add -p NUMBER for an alternate port

---

### Post by Depressed Man on 2009-03-09
Thanks, I managed to get it copied over. But I can't login without the password. After I do..

ssh user@192.168.1.102

it asks me for user@192.168.1.102's password still. I didn't specify a password in the keys generation either..

---

### Post by apmcd47 on 2009-03-09
1) Check that $HOME/.ssh on both machines is readable only by the owner.
2) Are you using authorized_keys or authorized_keys2? Your original posting showed you intended to use the latter but hyper_ch said the former. I **think **it is the latter (using Windoze here so can't check), but don't be afraid to experiment with both until it's working.
3) Check the man page for ssh_config. You should be able to put the port number into your config file:
```
Host Fred
  Name 192.168.1.102
  User me
  Port 80
  ...

```
The above is example code - the man page will tell you the real settings.
Andrew

---

### Post by Depressed Man on 2009-03-09
$HOME/.ssh being /home/user/.ssh (or home/username/.ssh) right? If so, only the user (and root of course) should be able to access those directories. But I'll chmod them again. 

I am using authorized_keys2 since I am running OpenSSH on both the client (laptop) and server (n800 tablet). 

And yeah, I figured out the port thing. -P port number works for scp if it's directly after scp. 

I had configured something on the tablet beforehand,  but I decided to start with a clean slate by reinstalling openssh server as well as rm * the /etc/ssh/ files. I don't need to setup anything else on the server do I?

---

### Post by bodhi.zazen on 2009-03-09
See : [https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

---

### Post by hyper_ch on 2009-03-09
well, if you're using authorized_keys2 then you'll have to alter the command given above accordingly.

---

### Post by Depressed Man on 2009-03-09
> **hyper_ch said:**
> well, if you're using authorized_keys2 then you'll have to alter the command given above accordingly.

I did, though I was bodhi.zazen's instructions. I'm going try your instructions now. Ideally though I want to be able to use a passphrase as well for additional security. Though it doesn't seem to work with opensync then without the use of the ssh-agent.

Edit: Currently going to try...
[http://www.debian-administration.org/articles/152](http://www.debian-administration.org/articles/152)

Edit: Got it to work! Except still haven't figured out how to use ssh-agent but that'll be for another day. 

Now to get GPE sync to work..

---

### Post by apmcd47 on 2009-03-10
> **Depressed Man said:**
> 
Edit: Got it to work! Except still haven't figured out how to use ssh-agent but that'll be for another day. 


Good man! Ubuntu runs ssh-agent through the desktop environment. That is, when you login through gdm/kdm, the login script runs gnome/kde/xfce under ssh-agent, so you should already be running it. To check this, open a terminal window and pipe **env **or **set **through **grep SSH**. You should see the environment variables set by ssh-agent. If that is the case, just run **ssh-add** to load your key. If you logon to a terminal you probably have to put something like **exec ssh-agent $SHELL** at the end of your .bash_profile (assuming bash), but I've never done that so I don't really know.

Andrew

---

### Post by bodhi.zazen on 2009-03-10
ssh-agent is easy, it is a command line tool, and you have to be running X, lol

```
ssh-add ~/.ssh/key_to_add
```

You enter the password for the key and it is stored in memory (until you log out of X).

Then you can simply

ssh user@server

and you will connect w/o specifying the path to the key or password.

---

### Post by samiux on 2009-07-08
> **Depressed Man said:**
> I already have SSH setup, however it's insecure since I never did figure out how to correctly setup the keys. Right now it's just password protected but I would like to have the keys setup as well with my n800 as the server and my laptop or desktop as the client. I'm guessing the instructions below have that as a similar setup.

scp ~/.ssh/id_dsa.pub [email]user@10.0.0.30:/home/user/.ssh[/email]/authorized_keys2

The problem here is I changed my port number. Normally if I were to just ssh connect I would specify -p 80 (say if I choose 80). But I can't seem to find an option for that. -P is the option for scp but I can't seem to figure out where to place it. 

[http://cleardefinition.com/page/Sync_Evolution_and_GPE_on_N800/](http://cleardefinition.com/page/Sync_Evolution_and_GPE_on_N800/)

The instructions here are..

```
Set up passwordless logon to N800 SSH
1.
On your desktop, run ssh-keygen -t and accept the default options. This will create a certificate on your computer that allows it to authenticate without a password. Do not enter a passphrase when asked, or you're basically making this step meaningless. (In theory, you should be able to use an SSH agent or something to let you do this, for better security. I wasn't that picky.)
2.
Now, let's transfer the public certificate to the N800 and authorize it for access. From your PC, scp ~/.ssh/id_dsa.pub user@10.0.0.30:/home/user/.ssh/authorized_keys2 (for OpenSSH aka SSH - if you use dropbear, the file is called authorized_keys - thanks to Chris McNally for the tip!) where 10.0.0.30 is again your N800/Nokia 770 IP address. Use the user password you created before to authorize the transfer.
3.
Let's test to make sure this works. Run ssh user@10.0.0.30 - it should log you on and give you a busybox prompt without asking for a password. If this worked, you're golden, move on. If not, well, I'm not sure what the deal is. Make sure /home/user/.ssh/ exists on the n800/Nokia 770, maybe.

```

The reason why is I want to get GPE ToDo syncing working between my tablet and my desktop. I've also read..

[http://sial.org/howto/openssh/publickey-auth/](http://sial.org/howto/openssh/publickey-auth/)

Can someone help me setup the agent (I would like to have the password security as well). Also what if I already generated a key on the server? 

[https://www.opensync.org/browser/plugins/gpe/README](https://www.opensync.org/browser/plugins/gpe/README)

My setup is here :
[http://samiux.wordpress.com/2009/06/15/ssh-to-use-rsa-key-for-login/]("http://samiux.wordpress.com/2009/06/15/ssh-to-use-rsa-key-for-login/")

---

