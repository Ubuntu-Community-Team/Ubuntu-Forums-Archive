---
title: "Using pass (password manager), please help with git repo"
date: 2016-02-26
forum: Security
---

### Post by CaptainMark on 2016-02-26
I'm just looking into setting myself up using pass, the password manager.
I've generated my GPG key and started using pass locally, but I understand it can use git repos. I think this means you can kind of sync your passwords with other pc's, have I understood this correctly? I don't know the first thing about what git is and what you can do with it.

I have pass working on my pc (desktop) and I'd like to be able to get passwords on my server (raspberry) I have a ssh connection between the two machines and LAN traffic can bypass the firewall freely between them.

Can anyone provide any help, the guides and man pages tell me how to initialize a git pass store but assume you already know what that is and how to use it.

Many Thanks&#65279;
Mark

---

### Post by thatotherguy2 on 2016-09-03
Looks like this is a little old but it's about all that comes up when searching on using Pass with gnome-keyring. 

As for learning git if you haven't already by now, this may help. [http://rogerdudler.github.io/git-guide/](http://rogerdudler.github.io/git-guide/)

Also there are lots of helpful guides and even a waltkthrough type tutorial when you sign up at Github.



I've also been looking into setting this up. So far I have successfully migrated my keepass2 database to Pass and I'm using QTpass as a GUI on Ubuntu 16. I have the Pass recommended firefox extension installed and it works great, besides missing the ability to generate new passwords in the browser.

What I'd like to know is how to best integrate Pass with the default gnome-keyring. Will they play nice together? And, are they only playing nice at the moment because I don't have GPG and git enabled in the settings yet?

Like the OP, I'd like to turn this on to allow me to sync my passwords across devices.

---

