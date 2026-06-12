---
title: "Ssh client pass phrase window has gone"
date: 2011-04-11
forum: Security
---

### Post by mikeym on 2011-04-11
Hi,

I'm using ssh key based authentication and I was pleased to find that when I set it up out of the box when I connected to my ssh server it prompted me with a password window rather than typing into the terminal and it remembered the pass phrase from one connection to the next. 

For some reason it's stopped showing me the window, instead I'm logging in through the terminal, and it's stopped remembering my pass phrase between connections. 

since I don't know what the program was called that gave me the login box it's rather hard to search for. Could anyone give me some clues as to what I should be doing?

---

### Post by bodhi.zazen on 2011-04-11
seahorse ?

---

### Post by mikeym on 2011-04-12
I don't think so?? I literally typed *ssh myhost* and instead of typing in the pass-phrase to the terminal I'd type it into a gtk style box. And the next time I ran *ssh* it would have remembered it. Stopping me having to type it in 20 times.

---

### Post by bodhi.zazen on 2011-04-12
Well personally I use ssh-agent, which is command line.

seahorse is (was) the default for Ubuntu.

I am not aware of another graphical application, kde may have one (kde wallet ?)

Could be gnome-keyring, keychain, ksshaskpass ?

---

### Post by mikeym on 2011-04-14
bodhi.zazen,

thanks! It appears that it was *gnome-keyring* I was seeing but for some reason it's started failing to work some time after it is started. A log out and log back in has restored it. I'll have to try and track down where it's failing and report a bug.

---

