---
title: "ssh keys can't be found"
date: 2010-09-29
forum: Security
---

### Post by badnaam on 2010-09-29
Scenario 1. I am doing this from /home/deploy directory
  I am trying to set up ssh with github for capistrano deployment. this has been an absolute nightmare.
  when I do ssh [EMAIL="git@github.com"]git@github.com[/EMAIL] as the deploy account I get
  Permission denied (publickey).
  so may be the key is not being found, so If I do a 
  ssh-add /home/deploy/.ssh/id_rsa
  Could not open a connection to your authentication agent.
  (i did verify that the ssh-agent was running) If I do exec ssh-agent bash and then repeat the ssh-add then the key does get added and I can ssh into github.
  Now I exit from the ssh connection to my server and ssh back in and I can't ssh into github anymore!
  Scenario 2
  if I login to my remote server and then cd into my .ssh directory and ssh into github then it all works fine
  I guess there is a problem with locating the key and for some reason the agent isn't funcitoning correctly.
  Any ideas?

---

### Post by bodhi.zazen on 2010-09-30
Not sure what you are wanting exactly.

ssh agent (ssh-add) should be running already, are you running X ? If you are not running X, then yes you need to start a shell as you have. You could do this with screen  ;)

In terms of ssh, you specify a key

ssh -i ~/.ssh/key_name user@server

HTH

---

### Post by badnaam on 2010-09-30
Thanks for the reply. Please look at this pastie it has all the details (permission, .bashrc etc).

[http://pastie.org/pastes/1190557/](http://pastie.org/pastes/1190557/)

I do start the ssh agent, but it doesn't really work the way its expected. I am having to do a ssh-add key in every session for this to work, the ssh-add key does not persist across sessions. 

Does that explain my problem?

---

