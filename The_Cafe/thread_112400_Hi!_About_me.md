---
title: "Hi! About me"
date: 2006-01-04
forum: The Cafe
---

### Post by David Olivier on 2006-01-04
Hi to all. A message at the top of the page tells me that since I am new to the forum I should say hello here so this is it! Otherwise I wouldn't have dared! :razz: 

I'm new to Ubuntu too, which I started installing Monday and still have a lot to learn about. And I'm not very sure how and where to ask the questions, it's difficult not to be confused!

I'm actually and old-time Unix user (and somewhat administrator), and developer (C, Java...), but this is practically my first contact with Linux at the GUI level. For desktop type work (mail, word processing, etc.) I have been using Macintoshes for over 15 years, but now I'm fed up with paying the price, and don't feel there is anything so "special" about Apple anymore, so I have chosen to move on to Linux.

One of my problems is understanding what I should do with "raw" comand-line tools and what I should do with GUI tools. One of the first things I botched up was Monday after my first installation; I decided I wanted to set my unix account number to the value I usually give it, so I manually edited /etc/passwd and did chown on my homedir and whatever was in it... But that wasn't a good idea, I never managed to log back in! I had to redo the installation...

So now I'm more cautious and try to use the tools. But even with that it's difficult understanding if they are all compatible...

I suppose these are too general questions for anyone to answer, I was just giving my impressions.

But maybe there is a question I can ask. Am I the only one in this situation: having experience with Unix at the command-line and development levels, but none at all at the GUI desktop user interface level, and feeling confused about that?

David

---

### Post by imrumpf on 2006-01-04
no don't worry. I switched over recently from windows, never used *nix before and I am doing a lot better now. It just takes a litte bit of time to get used to things. I have a couple of examples, such as commands like "sudo dpkg -i *.deb" i used to always have to look in the forums for that code. I gave it time and now i know how to do that off by heart. Of course there will be a lot of things I'll never learn but thats where this awesome forum comes into place. A simple search has almost always fixed my problem.

Now I am still new, but the account number is defaultly 1000 is it not? Then after every user it goes up by 1 right? if that's the case you could edit that in the gui from the "users and groups" option under administration.

---

### Post by David Olivier on 2006-01-04
[QUOTE=imrumpf]Now I am still new, but the account number is defaultly 1000 is it not? Then after every user it goes up by 1 right? if that's the case you could edit that in the gui from the "users and groups" option under administration.[/QUOTE]

Yes, my initial account number was 1000. That was the initial account that was created at the end of the installation process, which didn't let me choose another value (I feel it should have!).

It doesn't seem possible with the "users and groups" tool to change the account number of a user once it is created. Actually, I hadn't thought of trying that; I just went and changed it in the /etc/passwd file, which is normally the file that links user ids to user numbers, from 1000 to the value I wanted. And then I changed the ownership of my home directory and all files in it to be owned by the "new" myself. Normally that should have been enough!

Probably there were other files that contained the old account number or that were owned by my old account number and were outside my home directory, because then all went wrong.

What I did, after reinstalling Ubuntu from scratch, is create an initial user with another name; and then, with the "users and groups" tool, I created the user I wanted, with the account number I wanted. (The "users and groups" tool does allow that.) And then I logged out and logged back in as this new user, and erased the initial account.

By the way: the reason I want to have the same account ids is that I have the impression that makes things easier when I move tar files around, which contain the account number rather than the textual id. But maybe I am wrong about that.

---

