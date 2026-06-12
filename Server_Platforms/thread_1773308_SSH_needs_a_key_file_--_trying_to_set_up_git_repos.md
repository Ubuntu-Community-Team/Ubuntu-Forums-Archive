---
title: "SSH needs a key file -- trying to set up git repos"
date: 2011-06-01
forum: Server Platforms
---

### Post by sneakyimp on 2011-06-01
I've got an Amazon EC2 compute instance with Ubuntu 11.04 running on it.  I've managed to get my root key (the "ubuntu" user actually) set up so that I can SSH in from both my windows machine and my Ubuntu desktop.

The issue I'm having is that I'm trying to set up a git repository on this server to be accessed via SSH by a team of developers.  I've created the first user, "jason" but jason cannot log using the password I created for him because SSH on the server is set up to require a key file.  I believe that's due to this setting in **/etc/ssh/sshd_config**:
```

# Change to no to disable tunnelled clear text passwords
PasswordAuthentication no
```

I've got a few questions:
1) Can I allow users to login by setting that to "yes" and restarting ssh?  Is this safe?  Will passwords be transmitted as cleartext?  What about root/ubuntu who (afaik) don't have any password yet -- are those accounts safe?

2) If it's not safe, what steps are required to allow "jason" to login with a certificate?  Obviously I need a key file but I tried using the key file that I created for the ubuntu/root user (when I created the compute instance) and it apparently doesn't work for "jason" -- it only works for "ubuntu".  What are the steps?  Where does the file go? Does it need to be stored on both the client and the server?  Or does the server have a public key and the client have a private key?

3) How hard is it to set up my devs (using Windows, OSX, and linux) each with keys so that their various git clients (git-gui, gitk, git, TortoiseGit, eGit, etc) can interact with the repository via ssh?  Do the clients need to know where the key file lives or do they just use ssh and ssh needs to know where the key file is?

Any help would  be much appreciated.

---

### Post by brettg on 2011-06-01
Setting PasswordAuthentication to yes will work. You just need to restart your sshd service to make it take effect. Passwords are NOT transmitted as cleartext.

It all depends on how paranoid you are as to whether this is safe or not.

If you trust your users and they have sufficiently complex passwords then you should be fine. If none of them can escalate themselves to root privileges (sudo) then even better.

If you do prefer your users to use keys [this guide]("http://tuxnetworks.blogspot.com/2009/08/ssh-using-public-key.html") will help.

However using keys is only secure to the degree that the users private key is kept secure. Should the private key be leaked somehow then miscreants can use it to gain access to your machine just as if they had the password.

---

### Post by sneakyimp on 2011-06-01
thank you for your response.  i have managed to get my Ubuntu desktop to connect to the remote server using keys.  [This page](http://www.ece.uci.edu/~chou/ssh-key.html) worked perfectly.

However, I must repeat those steps for each developer on my team -- and, more importantly, they have to be able to use their various git clients (TortoiseGIT, git-gui, eGit, etc.) to use ssh to interact with my central git repository.  I'm wondering how tough it will be to generate a cert file for each dev, distribute them all, and configure all those clients. :(

---

### Post by ehammond on 2011-06-06
gitolite is a great framework for managing multiple users' access to central Git repositories without having to create individual user accounts on the server.

I'm working to make it easy to fire off a Git/gitolite server on EC2:

  [http://alestic.com/alestic-git/](http://alestic.com/alestic-git/)

--
Eric Hammond

---

### Post by sneakyimp on 2011-06-06
Nice! Alestic is very impressive and I admire your work. You obviously have a masterful command of EC2 techniques. I've heard of gitolite but instead managed to add my dev users, add them all to a dev group and get the permissions just so, etc. I was lucky enough to find a guy who knew how to set things up that way so I have it working.  I'll probably create a tutorial when I get a moment -- although your work at alestic will probably obviate the need for this tutorial.  There's just so much to read about git and so little in the way of succinct documentation about how to host a core git repository on your own server.

In the meantime, I've become concerned about backing up my server.  Any chance I could cajole you into contributing to [my question on aws forums](https://forums.aws.amazon.com/thread.jspa?messageID=252811&tstart=0) about backing up my EC2 instance?

---

