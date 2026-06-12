---
title: "is it possible to recover an encrypted home folder in these circumstances?"
date: 2011-08-01
forum: Security
---

### Post by eveg on 2011-08-01
one item before i ask my question. i've noticed a lot of bad links in posts concerning .ICEauthority problems. anyone with questions similar to mine, please don't click on any links from anyone dubious that may begin to infest this thread too. and if your problem is simpler than mine the answer to it may well already've been posted by bodhi.zazen who is a forum admin here and whose links, fortunately, are very useful indeed. the solved thread 'changing the name of my home directory' in security discussions may be what you're looking for.
 
honestly, the answer to my problem may be there too, but if so i don't understand it yet.
 
unfortunately, i've deleted the .ICEauthiority file in my home directory. fortunately it's on an old computer that's only for playing with, doesn't even go online, and only has unimportant personal files on it. 
 
what happened is that i'd enabled root [NEVER do this. there are excellent reasons not to. it's a bad security risk among other things. i was reading a little book called sopmething like linux in easy steps, and it gives clear uinstructions how to with ony a little note in the margin to say not to. if you have enabled root, your best bet is to go offline, make a backup of all your files, and wipe and reinstall your operating system. then have a look at your files, in detail, and hope you catch anything that shouldn't be ion them before you reinstall.], and to complicate matters, i forgot my user password, but remembered my root password. 
 
so i logged into bios in recovery mode and unwisely using a book i didn't understand well enough tried to change my user password. using sudo when evidently i should've used gksudo.

---

### Post by eveg on 2011-08-05
i have the original (32 digit/letter) passphrase that the computer gave me when i originally installed ubuntu, but when i've tried to enter it from the command line, either i was doing something wrong or it didn't work. i changed the password as root, sortof. logged in as root from bios, i perfaced the password change with sudo, when i should've used gksudo. finding that i'd messed that up i deleted the .ICEauthority file, but couldn't get it to take a gksudo password change. so i logged into gnome as root, set my user not to need a password to log in, but i still get the .ICEauthority error, and gconfig sanity check failed. 
is there any way to fix this?

if not, it's not the end of the world. there's just one file i'd like to recover before i erase everything and reinstall with root disabled and password required and all as it should be. needless to say, the computer is never going online in the shape it's in. probably never anyway. it's an old one to play with so far.

---

### Post by eveg on 2011-08-12
hi again.
wondering if i should just give up on this system and reinstall. 
it's only one encrypted file i'd lose if i did so, and it's only a personal file, but i kind of wanted to recover it if possible.
i changed my password as root. does that make recovery impossible?
 
i had enabled a root account, which i obviously shouldn't've done. i have the correct root password. 
i forgot my user password. i logged in as root from the bios in recovery mode and tried to change the password. i was aware that working as root could really mess things up so i prefaced the change password command with sudo. obviously what i should've done is used the passphrase, which i had bothered to write down. but i didn't know how to and none of the books i had explained it. 
 
the next book i found (ubuntu bible dec 2010, p972) told me (as neither of the others had) that it could seriously mess up a system to use sudo where you should've used gksudo. and reccommended deleting the .ICEauthority file in your home directory and then doing with gksudo whatever you'd mistakenly done w/ sudo. i managed to delete the .ICEauthority file ( i think. a search for it in my home folder shows no such file). however, simply trying to change the password as root prefacing the command w/ gksudo did nothing. 
logged into the gui as root, went to users and groups and tried to give myself a nopassword login, just so i could recover the encrypted file and then erase the whole system and reinstall, leaving root disabled. all nogo.
 
every time i try to log in as anything other than root, i get first a box saying:
 
error could not update .ICEauthority file /home/username/.ICEauthority
 
 
 
then after i clear that off the screen another box saying, if i recall (i'll check and correct this if i'm a little off):
 
there is a problem with the configuration server(usr/lib/libgconfig2-4/gconfg-sanity-check2 exited with status 256)
 
is there something obvious i'm missing? i've tried command line options from books and they ask for the passphrase and if i use the one i wrote down from system install it's wrong. in fact when i was changing the password the wrong way, it directed me to a similar screen a couple of times and when i clicked on it to write down the passphrase, it didn't give it to me just returned me to a previous screen.
do i need to do something with encryptfs-unwrap-passphrase , and if so what and how?
 
do i need to create another user with system admin privelages other than my original user and root? 
 
is the kirkland solution, encryptfs-recover-private , live cd of 11.04, going to be any use in this case? and if so, to have access to my encrypted home folder, should i do gksudo rather than sudo, or is that differant in 11.04?
 
is it because i made the mistake of enabling root, which is quite reasonably frowned on, that no one's answering any of my questions about this? i'm not telling anyone how to enable root. i stumbled across it, in print, not online, from an author who in my opinion should've known better. it was a supposed 'easy' book and it goes thru instructions telling a person not only how to enable root, but telling them specifically to do so, only mentioning in a margin note that you shouldn't enable root unless you have a good reason to, and not mentioning that root is disabled in ubuntu deliberately and should be left so as a security feature, much less saying anything about the differance between sudo and gksudo, so far as i recall.
 
well, if anyone has a definitive answer, thanx much.
 
only, please, unless you're staff or a moderator, please do not post a link to suggested solutions. i won't click on it and i strongly advise no one else does either. if there's a solution elsewhere you consider reliable give directions to it and people can decide for themselcves if it looks like a good idea.
bodhi.zazen's link to the dustinkirkland blog is one i've already tried, and it looks like a good idea, i'm just not sure it would work for what i'm trying to recover. i'll probably try it eventually, i'm just not sure how, sudo ? gksudo? etc.

---

