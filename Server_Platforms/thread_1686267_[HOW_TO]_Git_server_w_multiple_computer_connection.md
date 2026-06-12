---
title: "[HOW TO] Git server /w multiple computer connections"
date: 2011-02-12
forum: Server Platforms
---

### Post by max_power on 2011-02-12
FYI I use gitosis here which is no longer recommended because it is no longer supported. But this works great for me so give it a shot. 

Here we go:

First get all the needed packages and then install gitosis
```

sudo apt-get install git-core python-setuptools
cd ~
mkdir ~/src
cd ~/src
git clone git://eagain.net/gitosis.git
cd gitosis
sudo python setup.py install

```

Now create our git user
```

sudo adduser \
  --system \
  --shell /bin/sh \
  --gecos 'git version control' \
  --group \
  --disabled-password \
  --home /home/git \
  git

```

[COLOR="Green"][SIZE="4"]This is where we stray from the rest of the tutorials out there[/SIZE][/COLOR]

[SIZE="3"]**On each of your client computers:**[/SIZE]
[COLOR="Orange"]If your client is a windows computer you will need the gitbash program to generate your public key[/COLOR]

if you don't have a public ssh key already do the following. Otherwise skip this part

The -C command means comment. put the name of the computer here. Use something like "work" or "home" of "windowsLaptop" etc...
```

ssh-keygen -t rsa -C "computerName"

```
save the key in the default location.
enter a passphrase. DO NOT LEAVE IT BLANK!

Now that you have a public ssh key, lets copy it to our server. Use the same name that you used in your ssh key comment (-C "computerName")
```

scp ~/.ssh/id_rsa.pub user@myserver.com:computerName.pub

```

--------------------- back to the server now

**This next step is very important and is the "key" (no pun intended) to our setup.**

on the server create a public ssh key (if there is not one already)
```

ssh-keygen -t rsa -C "myserver"

```
save the key in the default location.
enter a passphrase. DO NOT LEAVE IT BLANK!

now copy that key to /tmp
```

cp ~/.ssh/id_rsa.pub /tmp

```

Now do this
```

sudo -H -u git gitosis-init < /tmp/id_rsa.pub
sudo chmod 755 /home/git/repositories/gitosis-admin.git/hooks/post-update

```

Now that we have our gitosis-admin repo setup, we can check it out and make changes to the config file.

FROM THE SERVER we are going to check out the gitosis-admin repo. I suggest checking it out in a spot you will remember. I will put it in our home folder.

```

cd ~
git clone git@YOUR_SERVER:gitosis-admin.git

```

if everything went well you can now cd into the new folder
```

cd gitosis-admin

```

next we are going to copy the public keys we generated from our client machines into the gitosis-admin/keydir file.
do this for each public key you copied to the server
```

cp ~/computerName.pub keydir

```

Now we will setup our permissions and repos!
```

nano gitosis.config

```
[COLOR="Red"][SIZE="3"]Warning: this part is crucial. If you mess this up you might have to delete the git user and his home folder and then create him again.[/SIZE][/COLOR]

Edit the config file as such:
```

[gitosis]

[group gitosis-admin]
writable = gitosis-admin
members = myserver

[group all-repos]
writable = project1 put all of your repos here separated by spaces
members = myserver computerName computer2 computer3


```

notice in [group all-repos] you put each repo you want to host on the writable line and the members line the computers who can access those projects.

once your done, exit nano and save the config file

Now, we are going to commit and push the new settings to gitosis
```

git commit -a -m "added repos and users"
git push

```

if everything went ok you are now done with the server setup!! Any time you want to add more repos or users you just check out the gitosis-admin repo and edit the config file.

Notice how gitosis-admin members is only the server. This is awesome because only the server can make changes to the gitosis. the benefit of this is one could SSH into the server from ANY computer and edit the config file. Other tutorials have you check out gitosis-admin on the client computer which to me seems like a bad idea if you operate from multiple computers (home, work, laptop etc...)

---------------------- End server config. time to init some repos

You've made it this far! congrats. Now lets make some repos and push them to the server

On one of your client computers navigate to the folder you want to put under source control and do the following:
```

cd project1
git init
git remote add origin git@myserver.com:project1.git
git add .
git commit -a -m "initial import"
git push origin master:refs/heads/master

```

if all went well you can now try to clone that project from another computer (that you created a ssh key and put in keydir. remember that?)

so, on another computer do this:
```

git clone git@myserver.com:project1.git

```
the project should now be downloaded.

DONE :D

---

