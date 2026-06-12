---
title: "SSH ssh-add: Could not open a connection to your authentication agent."
date: 2011-03-08
forum: Security
---

### Post by seth1010 on 2011-03-08
As the title says, whenever I try to use the ssh-add command I always get the same error. (exact console copies for your convenience)

 > ty@ubuntu:~$ sudo ssh-add
[sudo] password for ty: 
Could not open a connection to your authentication agent.
ty@ubuntu:~$ 


After looking pretty much everywhere on the internet, I found a lot of people had the same problem, but their solutions didn't work for me.
> 
ty@ubuntu:~$ exec ssh-agent bash
ty@ubuntu:~$ sudo ssh-add
Could not open a connection to your authentication agent.


Am I missing something basic?

---

### Post by seth1010 on 2011-03-09
Alright, I figured out my problem, but in order to keep from being one of *those* guys, I figured that I will let anyone that is having similar problems how to fix it. 

What I should have noticed is that I needed to use sudo in order to ssh-add.  This is a big red flag.  What happened in my case was I had given root ownership of the .ssh folder.  From what I can figure, I did this by opening gedit with sudo while trying to open a file in that directory.  More info [here]("https://help.ubuntu.com/community/RootSudo"). 

What I did to solve the problem was delete the .ssh folder entirely and start again.  There is probably a much more elegant way to do this, but being a linux newbie, this worked just fine.

Comments from more experienced members would be amazing, I'm still trying to wrap my head around this.

---

### Post by cariboo on 2011-03-09
Personally, I would have just changed ownership and permission on the ~/.ssh driectory, you could have done it using the following commands:

```
sudo chown -R user:user ~/.shh
```

where user:user = your user name and group name, then set the directory permission to 700:

```
chown 700 ~/.ssh
```

then cd in to the directory and give the correct file permissions to the files inside:

```
cd .ssh
```

and

```
chmod 600 *
```

---

### Post by VentoLTU on 2012-05-07
cariboo, I think you meant
```
$ chmod 700 ~/.ssh
```

---

