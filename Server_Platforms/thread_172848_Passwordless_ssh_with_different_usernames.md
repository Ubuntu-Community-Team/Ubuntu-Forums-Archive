---
title: "Passwordless ssh with different usernames"
date: 2006-05-09
forum: Server Platforms
---

### Post by dakebusi on 2006-05-09
Hello,

I'm trying to ssh from one machine to another and I don't want to type the password every time. I know that I can use the public keys method, but as far as my knowledge goes (which is not that far) that works only if the username is the same in the local and remote machine. 

How should I set up so that I can ssh directly without being asked for a password?

Thanks a lot!

---

### Post by cgjones on 2006-05-09
Have you tried using authorized_keys with different user names? I've never tried it, but it might work.

---

### Post by harisund on 2006-05-09
First of, let me tell you, SSH is totally awesome. You can do just about anything with it, except perhaps clean the kitchen sink (and that's only because the kitchen sink can't run a SSH server ...) 

So, assuming you have setup your keys properly (if you don't post back, and I will walk you through it) here is what I suggest you do . 

On your local machine, create a file called 'config' in the '.ssh' directory of your $HOME. The syntax you will need for the file creation is as follows

Host ConnectionName
HostName remote.machine.name
User username_on_remote_machine
Port port_to_connect_on_remote_machine

Here is the description: 
In the file, what comes after 'HostName' is the name of the machine. This could be an ip address (68.122.45.234) or a dns name (computer.example.com). 
What comes after the 'UserName' directive is the username to be used on the remote machine (it could be the same as yours, or it could be different). 
The port is pretty obvious, and the 'Host' directive is a convenient name you wish to give it. For example, here is my ~/.ssh/config file 
```

Host Home
User whyDoYouWantToKnow
Port 8322
HostName harisund.com

Host Office
User UberConfidential
Port 22
HostName machine.whereIwork.com

```

Then using my laptop if I want to connect to my home machine all I need to do is ```
ssh Home
``` and it automatically connects me to [email]whyDoYouWantToKnow@harisund.com[/email] on port 8322. The beauty is you can use it through scp as well. As in ```
scp Home:~/.bashrc .
``` automatically copies the required file from my home machine using the parameters set in the config file. 

If you have keys you can have passwordless access (which I do a real lot .. how else do you think I can get on irc from my school machines?)

---

### Post by dakebusi on 2006-05-10
Thanks to both of you, cgjones and harisund.

Now it works and I can ssh without having to type the password. 

I think yesterday i messed the authorized_keys files and that was the reason I couldn't ssh as a different user without being asked for the password.

Anyway, the config file is very useful as well, so I don't have to type all the information every time I want to ssh.

---

