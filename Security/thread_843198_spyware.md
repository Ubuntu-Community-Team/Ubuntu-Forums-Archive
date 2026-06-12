---
title: "spyware"
date: 2008-06-28
forum: Security
---

### Post by irishy on 2008-06-28
Help please I am now 3 days into hardy heron and while asking the question do I need antivirus in various places on the internet I have finished up with (antvrsinstall.exe) trying to install itself on the pc and there is no apparent way of getting rid of it so I have shut the pc down and come to this pc to find out what the problem is searching for the same came up with several websites that would if anyone can believe them would show how to get rid of it as it was a very serious problem I think that clicking on one of these links would put this pc in the same predicament
can anyone help please

---

### Post by cpetercarter on 2008-06-28
Antvrsinstall certainly looks like bad news, if you have Windows on your pc. But I am not clear from your question - is it on a Windows pc,or on a pc running Linux? If the former, you will need to use a Windows anti-spyware programme to get rid of it (google "antvrsinstall.exe" for suggestions) or run Microsoft's own on-line anti-virus scan. An ".exe" file is a Windows file and it can't "install itself" on a Linux computer. It might, just, be possible to install it using Wine, but I doubt that it would work.

---

### Post by forger on 2008-06-28
You have wine installed? You should remove it and all it's configuration.
If you agree and want to purge it:
> sudo apt-get purge wine
rm -rf $HOME/.wine/

That's it, but if you don't agree, you should do a complete format and keep the files you need as a backup.

And don't install wine :)

---

### Post by irishy on 2008-06-28
I thank you for your advice I was really worried about this
Irishy

---

