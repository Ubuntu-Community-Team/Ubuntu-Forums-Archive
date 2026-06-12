---
title: "vi commands"
date: 2011-10-26
forum: Server Platforms
---

### Post by packetsmacker on 2011-10-26
i am running server 11. When i created a text file with vi i found some issues. It looks like a keyboard mapping problem but I can figure it out. 


form the terminal i can run vi filename to open the file. next if i hit i for insert I can start typing. the issue is if i need to back space to delete the character i just typed i just get the cursor to go back but doesn't delete the character. Also if I use the arrow keys i get strange things like up arrow gives me a capital A. 

I have also sshed in to the server from my mac and have the same issues. I changed my terminal type on the mac to vt100 didn't help

I have used vi in other distos and on the mac and it is not working the same on Ubuntu. 

What can i do?

---

### Post by Reddoug on 2011-10-26
Google vi. A lot of info out there. I use vim.

[http://www.cs.colostate.edu/helpdocs/vi.html](http://www.cs.colostate.edu/helpdocs/vi.html)

Doug

---

### Post by cortman on 2011-10-26
use emacs

---

### Post by PaulW2U on 2011-10-26
> **packetsmacker said:**
> form the terminal i can run vi filename to open the file. next if i hit i for insert I can start typing. the issue is if i need to back space to delete the character i just typed i just get the cursor to go back but doesn't delete the character.

Are you really running vi? I suspect you're actually running vim. Type **:ver** in the command line to check.

There are hundreds of web pages that you can refer for help if you enter "vim backspace" into Google.

Here's one such page to start you off - [http://vim.wikia.com/wiki/Backspace_and_delete_problems](http://vim.wikia.com/wiki/Backspace_and_delete_problems)

---

### Post by packetsmacker on 2011-10-26
:ver gives me version 7.3 

but i still dont' understand why the sames commands work differently in ubuntu then say centos. i check my centos server and its the same version of vim.

---

### Post by haqking on 2011-10-26
> **packetsmacker said:**
> :ver gives me version 7.3 

but i still dont' understand why the sames commands work differently in ubuntu then say centos. i check my centos server and its the same version of vim.

[http://vim.wikia.com/wiki/Backspace_and_delete_problems](http://vim.wikia.com/wiki/Backspace_and_delete_problems)

there is plenty of more information relating to keymappings and term types on the vim wiki also

edit: ahh i see post 4 gave same link

---

### Post by PaulW2U on 2011-10-26
> **packetsmacker said:**
> :ver gives me version 7.3 

but i still dont' understand why the sames commands work differently in ubuntu then say centos. i check my centos server and its the same version of vim.

Right so you are using vim. You might have a hidden settings file called .vimrc. I really can't remember whether a default file is installed or if you need to create one yourself. If the .vimrc on your Centos server contains different settings than the one on your Ubuntu server then vim will behave differently.

In my .vimrc I have **set backspace=2** to make vim's backspace behave how I want it to.

---

### Post by bab1 on 2011-10-26
> **packetsmacker said:**
> i am running server 11. When i created a text file with vi i found some issues. It looks like a keyboard mapping problem but I can figure it out. 


form the terminal i can run vi filename to open the file. next if i hit i for insert I can start typing. the issue is if i need to back space to delete the character i just typed i just get the cursor to go back but doesn't delete the character. Also if I use the arrow keys i get strange things like up arrow gives me a capital A. 

I have also sshed in to the server from my mac and have the same issues. I changed my terminal type on the mac to vt100 didn't help

I have used vi in other distos and on the mac and it is not working the same on Ubuntu. 

What can i do?

You are most probably running the default minimal version of vim (vim-tiny).  You need to install the complete package.  ```
sudo apt-get install vim
```

---

### Post by ksudbury on 2012-02-18
Check out this guide for [Vi commands]("http://techspotting.org/vi-commands") should get you going, IME the hardest thing to get used to is the navigation in Vi :)

---

