---
title: "ssh key issues"
date: 2010-09-30
forum: Server Platforms
---

### Post by badnaam on 2010-09-30
Scenario 1. I am doing this from /home/deploy directory
  I am trying to set up ssh with github for capistrano deployment. this has been an absolute nightmare.
  when I do ssh [EMAIL="git@github.com"]git@github.com[/EMAIL] as the deploy account I get
  Permission denied (publickey).
  so may be the key is not being found, so If I do a
  ssh-add /home/deploy/.ssh/id_rsa
  Could not open a connection to your authentication agent.
  (i did verify that the ssh-agent was running) If I do exec ssh-agent  bash and then repeat the ssh-add then the key does get added and I can  ssh into github.
  Now I exit from the ssh connection to my server and ssh back in and I can't ssh into github anymore!
  Scenario 2
  if I login to my remote server and then cd into my .ssh directory and ssh into github then it all works fine
  I guess there is a problem with locating the key and for some reason the agent isn't funcitoning correctly.
  Any ideas?


Here is the pastie with my .bashrc and other info.


[http://pastie.org/pastes/1190557/](http://pastie.org/pastes/1190557/)

---

### Post by a9k3d on 2010-10-02
Three machines involved:
[LIST=1]
[*]Development machine you are typing on.
[*]Server that you telling via capistrano and ssh to get files from github
[*]Github server
[/LIST]

I found I had to change the name of id_rsa or id_dsa to keep straight what ID I was wanting. I have one id_dsa to get on my server called a9k_id and another for repositories call git_id.

I run ssh-agent at startup but there is only ONE process running. You show TEN. That could be a problem, how is a poor ssh to know which one you want to use.

When I type  ssh-add -l I get both id's listed.

Smells like you are getting too many ssh-agents going. Note my cap deploy isn't starting any ssh-add or ssh-agent since ssh-agent is always on on my machine.

ssh-agent -s should show something like *echo Agent pid 18538;* which will tell you which of those ten ssh-agent you really are using.

The good news is you can get from the server to the repository - that is half the battle won.

---

