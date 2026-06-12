---
title: "connecting  atom/ on linux with GIT and github"
date: 2018-12-09
forum: The Cafe
---

### Post by dilbert_one on 2018-12-09
dear Ubuntu-.experts good day 

today i have a question regarding the usage of atom-editor with git and github. 
i am on linux. 

the question is : how to run the atom-gitub-connectoion with ssh-keys the right way?



See here; heard that this would be but very simple from the command line and linux...

Set your email: [https://help.github.com/articles/setting-your-commit-email-address-in-git/](https://help.github.com/articles/setting-your-commit-email-address-in-git/)

After uploading keys, test your ssh connection: [https://help.github.com/articles/testing-your-ssh-connection/](https://help.github.com/articles/testing-your-ssh-connection/)

Switch repo to use ssh rather than https: [https://help.github.com/articles/changing-a-remote-s-url/#switching-remote-urls-from-https-to-ssh](https://help.github.com/articles/changing-a-remote-s-url/#switching-remote-urls-from-https-to-ssh)


but if i look at my atom editor i have the options of 

- connect with GIT 
- connect with GITHub 


well whats the difference here betweeen git and github!? 

why cannot add some commmits while i see the git with create detached commend - nothing happens here

---

### Post by TheFu on 2018-12-10
Git is the tool.  It is available on the local system without any networking.
If you add networking and ssh connectivity, then any approved git client that supports ssh connections can be used.
ssh connections and tools can be by passwords, ssh-keys or ssh-certificate authentication. The "right way" is debateable, but I have a personla rule that doesn't allow passwords for authentication to any services I manage over the internet.  ssh configuration can force this.

Any ssh-based tool will use ssh-keys if they are configured.  This is definitely more secure than passwords and almost always 10,000x more secure.  ssh, scp, sftp, rsync, rdiff-backup, sshfs, duplicity, stunnel, are some tools off the top of my head which honor ssh-keys.  git is one too.

Github is a service, owned by Microsoft, which makes git repositories available on a cloudy service. There are others.  You can deploy your own, if you like, using something like gitlab.

I don't know anything about atom integration.  Never touched it, but I suspect any git integration would be using just the most popular capabilities and system() calls to a git command.  Basically, GUI tools provide 80% of the features, by supporting 20% of the most popular options for the normal CLI tool.

There is a free PDF book called ProGIT which explains git very well.

---

