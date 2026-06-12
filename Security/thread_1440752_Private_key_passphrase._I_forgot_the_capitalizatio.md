---
title: "Private key passphrase. I forgot the capitalization"
date: 2010-03-27
forum: Security
---

### Post by Vistro on 2010-03-27
My passphrase is two sentences. Here's what I know (I'm changing the phrase once I figure it out.) Here it is in a basic form.

REMOVED

Problem is, I don't remember

1. What I capitalized
2. If I put a comma in there
3. If I put that last period there

Is there software that will brute force it with all the possiblites of the permutations I put on it? 

I did it on paper, and it's some 98 possible combos.

---

### Post by Vistro on 2010-03-27
It was 128 possibilities. I wrote a Python script to create a text file with all the possible combos. Amazingly, while the coding took 5 minutes, the script did it's job in less than a second. 

Is there a gpg terminal command that would let me try to access a key, and the passphrase would be a part of that command? I have an idea to have python take each possibility, load it into a variable, and then keep running the terminal command with each possibility until it got a positive response.

---

### Post by Agent ME on 2010-03-27
gpg's --passphrase command line option might be useful to you. Check gpg's man page for information.

---

### Post by Vistro on 2010-03-27
> **Agent ME said:**
> gpg's --passphrase command line option might be useful to you. Check gpg's man page for information.

Hmm... but how do I deal with spaces? It doesn't seem to like " signs.

EDIT: I've searched Google, and it looks like I'm the first person in the world to want to use a passphrase with a space with the terminal. Because 15 pages of results doesen't have anything.

---

### Post by Agent ME on 2010-03-28
If there are spaces in a string that is meant to be passed as a single argument in a shell, you need to quote the string or escape the spaces.

If your passphrase is **a b c**, then any of these will work:
gpg --passphrase "a b c"
gpg --passphrase 'a b c'
gpg --passphrase a\ b\ c

EDIT:
If you have a text file that has each possible passphrase on its own line, here's a shell script to try them all until one works to decrypt a file:
```
#!/bin/sh

while read line
do
	if gpg --passphrase-fd 0 --decrypt "$1" << EOF
$line
EOF
	then
		echo "Decryption succeeded with passphrase $line" >&2
		exit 0
	fi
done
echo "No passphrase worked." >&2
exit 1
```
Save that to a file such as "test.sh", set it as executable, and run it as "./test.sh file.gpg <passphrase-list.txt >output". "file.gpg" should be some file encrypted with your public key that needs your passphrase to be decrypted. If the script worked, it will say what passphrase it used, and the file "output" will have the decrypted content. If the script failed, it will report that it failed and "output" will be an empty file.

---

### Post by Vistro on 2010-03-28
Well using a controlled environment with a key I know the passphrase to I was able to crack the sucker open. 

But it's not working on my main key. I suppose I'll try my Ubuntu password but this is starting to worry me.

---

### Post by Vistro on 2010-03-28
And wouldn't you know it. After 5 hours of trying to crack a password, it was my Ubuntu logon. 

Wow. If any of you are from 4chan, you will understand me when I say

FFFFFFFFFFFFFFFFFFFFFFFFFUUUUUUUUUUUUUUUUUUUUUUUUUUUUUU!

EDIT: Thanks for all of the help anyways, guys! I learned some things about a function I hope to use in the future with my little thought I had... an encrypted direct pc to pc IM system. The only thing standing in my way are the routers bound to be present at both parties.

---

### Post by Agent ME on 2010-03-28
> **Vistro said:**
> EDIT: Thanks for all of the help anyways, guys! I learned some things about a function I hope to use in the future with my little thought I had... an encrypted direct pc to pc IM system. The only thing standing in my way are the routers bound to be present at both parties.
It would be easier not to invent your own IM system, but to create a plugin for an existing program such as Pidgin. However, Pidgin already has a plugin for encrypted chats.

---

