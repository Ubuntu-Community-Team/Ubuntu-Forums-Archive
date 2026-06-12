---
title: "Make it easier to explain how to do things"
date: 2008-02-22
forum: Ubuntu Brainstorm
---

### Post by dumbo on 2008-02-22
Currently if someone wants to install something, or add a component the instructions they will be given are typically of the format:

- open a console, type 'sudo apt-get install X' then 'sudo apt-get install Y'.

It's short, to the point, you know that someone will achieve the correct results, but it also puts them into contact with the command line completely unnecessarily...
- does a new user know how to copy/paste in ubuntu yet? 
- are they going to learn anything by typing 'random gibberish' into a black box? 
- or will this just enforce the "it's too hard for me"/it's for geeks mentality?

You could suggest:
- use synaptic.  The instructions on how to do 'sudo apt-get install X' would be rather long, and involve a search.  It's a good program, but this isn't it's forte.
- use add/remove programs.  That only seems to cover some programs, and is also 'search' based.

This should NOT involve 'search', the point is to install precisely what the user wants - not to leave them with a list of packages with the term in it's name/description. (try installing 'firefox' - I get 1.5 pages of options to select from via 'add/remove programs' - even more in synaptic).

I'm not really sure how this could be done 'easily' - random ideas:
- have a tiny 'install application' window that just gives a prompt and takes the name(s) of the application.
- add a protocol handler to firefox that "simply" calls synaptic to install the given package(s) from the official ubuntu repository.  Along with a 'are you sure?' button.

---

It just seems that for a new user, the only reason they'll need the console is to type in the 'arcane' apt-get commands this forum/ubuntu documentation offers as solutions...

---

### Post by ryanhaigh on 2008-02-22
Already implemented but underused, try [apt://firefox]("apt://firefox") , while its obviously very simple it doesn't teach the user anything wheras pointing to synaptic/addremove or even apt-get makes things very clear and is universal accross all the *buntu's. Perhaps the apt:// handler could be improved so that the package is installed but alsp a website shown that explains what just happended and how to install software using add/remove synaptic and the terminal in that order.

---

