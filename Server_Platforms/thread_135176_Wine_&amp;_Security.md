---
title: "Wine &amp; Security"
date: 2006-02-23
forum: Server Platforms
---

### Post by turker on 2006-02-23
One of the most important reasons I use Ubuntu Linux is security. Yet, it's sometimes good to run windows applications under Linux.

Is using wine as secure as not using it? 

When I open an infected *.exe file through wine, may it pose a security issue for my Ubuntu 5.10?

---

### Post by echo $USER on 2006-02-23
Good question, I have been wondering the same.  And what if you run IE through Wine; could that infect your machine with malware?

---

### Post by earobinson on 2006-02-23
wine is designed to have all the same bugs as windows, this is somehting the wine guys brag about.

That being said wine could deleat any files it has axcess to, however wine will never be able to infect ubuntu (unless some one wrote a wine linux virus, that would be fairly complacated).

so to sum things up wine wont be able to install ad ware or anything else on ubuntu but it could deleat files it has axcess to.

SPELLING ERROR deleat = delete

---

### Post by turker on 2006-02-23
Sorry, but what do you mean  "deleat" ?

Only a misspelling of "delete" or any other word that i don't know?

---

### Post by shof2k on 2006-02-23
Wine does aim for a 'bug for bug' compatibility.  That's why it has the SVG metafile flaw...but I recall a study where someone tried to get 10 infamous windows viruses to run via wine.  Only 1 did and that couldn't do anything.

Overall I think wine is safer than native windows

---

### Post by earobinson on 2006-02-23
[QUOTE=shof2k]Wine does aim for a 'bug for bug' compatibility.  That's why it has the SVG metafile flaw...but I recall a study where someone tried to get 10 infamous windows viruses to run via wine.  Only 1 did and that couldn't do anything.

Overall I think wine is safer than native windows[/QUOTE]
SPELLING ERROR deleat = delete

---

### Post by jpkotta on 2006-02-24
You can manipulate files from Wine.  I have / mounted as Z: in wine, and I can't remember doing anything to specifically mount it.  I usually would do something like create a directory for Wine in $HOME and copy any files it needed there.  So I think it was mounted by default (but am not sure).

It's not that big a deal, though.  I don't have write access to most files in /, and most files in $HOME have permission 600.  It appears that Wine acts like its own user, because I could manipulate 777 but not 600 files. If you're paranoid like me, add ```
umask 0077
``` to your ~/.bashrc.

---

### Post by earobinson on 2006-02-24
[QUOTE=jpkotta]You can manipulate files from Wine.  I have / mounted as Z: in wine, and I can't remember doing anything to specifically mount it.  I usually would do something like create a directory for Wine in $HOME and copy any files it needed there.  So I think it was mounted by default (but am not sure).

It's not that big a deal, though.  I don't have write access to most files in /, and most files in $HOME have permission 600.  It appears that Wine acts like its own user, because I could manipulate 777 but not 600 files. If you're paranoid like me, add ```
umask 0077
``` to your ~/.bashrc.[/QUOTE]
true my only point was if you ran a program(virus) that would deleat any .doc files it could find, wine would deleat all the .doc files that it had the correct permissions to deleat.

---

### Post by tzembi on 2007-09-05
I was asking myself the same question.

Here is what i found so far:

[http://ubuntuforums.org/showthread.php?t=543419](http://ubuntuforums.org/showthread.php?t=543419)

Sorry didnt see your post.

Regards,
TZembi

---

