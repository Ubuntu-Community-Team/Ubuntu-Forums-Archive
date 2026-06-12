---
title: "Syncing multiple folders between multiple computers"
date: 2013-06-27
forum: The Cafe
---

### Post by thnewguy on 2013-06-27
I've been working on a project lately which allows the user to sync multiple folders between multiple computers. It's coming nicely and I feel it's finally really for beta testing. The program is called Fish-Sync and it is designed to make syncing files as straight forward (and secure) as possible. 

How it works is the user tells Fish-Sync the name of remote computers with which we want to share files. We provide our username on the remote machine(s) and the files we want to share. We can also specify as to whether we want to sync folders or only push/pull files to/from another computer. Only one of the machines under our control needs to have Fish-Sync installed, all of the others need only to have OpenSSH server running.

Fish-Sync creates a unique security key and copies it to the remote machines. It then syncs the folders we specify and continues to perform regular synchronizations periodically. (We can specific the frequency of synchronizations.) Fish-Sync is designed to be a "set and forget" application and requires no special access rights.

If you are interested in trying Fish-Sync you can download a copy on the website [http://fishsync.sf.net](http://fishsync.sf.net) There is accompanying documentation and installation on Ubuntu is as simple as running:
```

sudo make get-ubuntu-deps
make
sudo make install
sudo make installgui          (optional)

```

I created this app because I feel rsync and backup scripts tend to be intimidating to new users (and inconvenient for experienced users). Fish-Sync is open source, free to use and hasn't eaten any of my data throughout my tests.

---

