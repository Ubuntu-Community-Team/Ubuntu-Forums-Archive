---
title: "Beginners Guide to Bazaar"
date: 2008-09-10
forum: Server Platforms
---

### Post by Dr Small on 2008-09-10
[center][SIZE="4"]A Beginner's Guide to Bazaar[/SIZE]
[SIZE="7"]&#9617;&#9618;&#9619;»§«&#9619;&#9618;&#9617;[/SIZE][/center]


[SIZE="4"]_Introduction_[/SIZE]

*Bazaar  (or  bzr)  is  a project of Canonical to develop an open source distributed version control system  that  is powerful,  friendly,  and scalable. * ... It is used by Launchpad for managing revisions with packages. If you have never created a Launchpad project because bzr scared you, fear no more!

To get started, you should install the bzr application by running:
```
sudo apt-get install bzr
```

Bazaar relies on SSH keys to transfer files to your Launchpad account. If you don't have a SSH key, you can follow the next steps to get your SSH key on Launchpad. If you already have your SSH key on Launchpad, you can skip this section to "Using Bazaar".

[SIZE="4"]_Launchpad / SSH Key_[/SIZE]

To create your SSH key, open a terminal and run:
```
ssh-keygen -t dsa
```

Leave the first prompt (for the key location) at default, by pressing Enter, then enter a passphrase for your private SSH key. When complete, run:
```
cat ~/.ssh/id_dsa.pub
```

Copy your public key, from the previous command, then go to Launchpad to edit your SSH key:
[https://launchpad.net/~username/+editsshkeys](https://launchpad.net/~username/+editsshkeys)

Paste the key into "Add an SSH key" then click "Import Public Key". You should be all set now!


[SIZE="4"]_Using Bazaar_[/SIZE]

Suppose you found a project on Launchpad, that you wanted to help out with, or wanted to download their project source to tweak it to your own likings. I'll give my perlbot project as a quick example. If you go to:
[https://code.launchpad.net/~drsmall/perlbot/trunk](https://code.launchpad.net/~drsmall/perlbot/trunk)

You can view the trunk, and revisions for that project. If you wanted to download a copy of this trunk to your local system, you would issue this command:
```
bzr pull lp:perlbot
```

This would then download the source files of perlbot to ~/perlbot on your system. You can then execute, run, or send the revisions back to the trunk (with proper permission).

Ok. So let's say you want to start your own branch, where you can host your own edited version of some software, or it could be something you created by yourself that you want to be worked on by a team. Gather up all of the files you want to placed in your launchpad branch, and place them in one directory. cd to this directory, and then run:
```
bzr init
```

This makes the directory into a version branch. If you take the time to notice, there is now a hidden directory called .bzr in here. This is where all the revisions, and files are stored to be used by bzr. Now, add all of the files to the branch:
```
bzr add *
```

It is a good idea to get in the habit of running the next command for checking the difference between your last revision and the current one. You shouldn't have to do this on your first time around, though.
```
bzr diff
```

With this next step, we are committing our edits into the current revision. It is a good idea to label your revisions with meaningful comments.
```
bzr commit -m "Revision 1 Comment"
```

You may now upload your revision to your Launchpad branch. If the branch does not exist, it will be created. You can have multiple branches, so name them accordingly. This command may take a few minutes, but it is creating the branch, uploading your files, creating revisions and alot of other things.
```
bzr push lp:~user/projectname/branchname
```


[SIZE="4"]_Commands_[/SIZE]

Make directory a bzr branch:
```
bzr init
```

Download a branch:
```
bzr pull <location>
```

Update a branch:
```
bzr push <location>
```

Add files to branch:
```
bzr add <filename>
```

Check the difference between revisions:
```
bzr diff
```

Commit the revision:
```
bzr commit -m "Revision Comment"
```

(These are just the basic commands. You can find the complete list of commands by running 'man bzr' in your terminal.)




**Additional Links:**
[Bzr - Ubuntu Wiki]("https://wiki.ubuntu.com/Bzr")
[Bazaar Official Website]("http://bazaar-vcs.org/")
[Launchpad.net]("http://launchpad.net")

Dr Small

---

### Post by -grubby on 2008-09-14
Thank you.. this guide is very helpful

---

### Post by Flimm on 2008-09-27
I've got a question, what exactly is the difference between bzr pull and bzr branch?

---

### Post by Dr Small on 2008-09-27
> **Flimm said:**
> I've got a question, what exactly is the difference between bzr pull and bzr branch?
I think that 'bzr branch location' will create the current directory into a branch and download the branch, whereas 'bzr pull location' will only pull the branch to the directory, without setting up a local branch.

Dr Small

---

### Post by mdgrech on 2009-04-08
wow great work here doc

---

### Post by cunhapri on 2012-03-25
Hi, I'm very new to Baazar, and I was invited to an existing project in Launchpad.net. Do you know if there is a way to import a branch (for an existing project that has its own account in Baazar) without installing Baazar on my computer, just using the existing host?

 I'm not a fluent speaker of English, so let me know if there is something wrong with my question and I'll clarify it.

---

