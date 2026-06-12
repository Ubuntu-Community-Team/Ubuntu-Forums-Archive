---
title: "ssh for that pesky windows installation of yours"
date: 2010-11-18
forum: The Cafe
---

### Post by azzid on 2010-11-18
At work I have to use windows for this and that reason and the other day I started to think about the fact that I don't have the command 'ssh' there.

Sure, I have putty and with it the cmd-compatible plink, but they don't respond when I call for 'ssh'.

As it turns out it is fairly simple to fix this little annoyance, and by doing so, calling home to your beloved ubuntu machine will feel a little bit more natural. ;)

Firstly, there are aliases in windows. You'll have to fiddle about a little bit in the registry, but if you add the key:
```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\App Paths\ssh.exe
```
And set the default string to your path to putty:
```
"C:\Program Files\PuTTY\putty.exe"
```
You'll be able to put 'ssh' into the run-dialog and have it start putty. Putty will also take an address as an argument, so putting 'ssh host' into the run dialog will work as expected! =D

**That takes care of the gui, but what if you're in cmd and want to do the same?**

In cmd there is a little command called 'doskey', using that you can make the alias 'ssh' run plink like so:
```
doskey ssh="C:\Program Files\PuTTY\plink.exe" $*
```
After running the code above the command 'ssh host' will work as expected. You still got the problem however that you'll have to run this command every time you start a new cmd...

For this to I found a fix!

In the following registry key:
```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Command Processor
```
If you create the string 'AutoRun' in it and assign it the value '%USERPROFILE%\alias.cmd' that file will be run every time cmd starts.

After that all you'll have to do is create the file (%USERPROFILE%\alias.cmd) and put the command (doskey ssh="C:\Program Files\PuTTY\plink.exe" $*) in it!

I've attached a file with exports from my registry and also my 'alias.cmd'.

Not the most ubuntu-like topic here, but as it fell within my taste I hope it will also please some of the other ubuntuforum readers.

---

