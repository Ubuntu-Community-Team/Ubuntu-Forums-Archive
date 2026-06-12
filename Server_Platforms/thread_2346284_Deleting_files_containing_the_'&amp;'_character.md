---
title: "Deleting files containing the '&amp;' character"
date: 2016-12-13
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2016-12-13
Hi all

In thread [Locating space consuming files]("https://ubuntuforums.org/showthread.php?t=2346186"), a large number of files named similarly to```
/root/update?host=@&domain=mydomain.com&password=e12345678987654321.999
```were found.

As they are redundant and contain the '&' character, how can they be deleted, please?

TIA

---

### Post by kpatz on 2016-12-13
Enclose the file name in single quotes, such as```
rm '/root/update?host=@&domain=mydomain.com&password=e12345678987654321.999'
```

Or if you have a bunch of them that all start the same way, ```
rm /root/update?host=*
``` In this case, omit the quotes.

---

### Post by SeijiSensei on 2016-12-13
Single quotes is usually the easiest.  You can also "escape" the ampersand by placing a backslash ahead of it:

```
rm /root/update?host=@\&domain=mydomain.com\&password=e12345678987654321.999
```

That tells the shell to treat the character as a literal ampersand rather than interpreting it as the "put this process in the background" character.

Often if you use "[tab completion]("http://www.howtogeek.com/195207/use-tab-completion-to-type-commands-faster-on-any-operating-system/")" the appropriate backslashes will be added automatically.

---

### Post by ChrisRChamberlain on 2016-12-13
kpatz, SeijiSensei - thanks for your replies.

Tried all three variants with similar error messages. 
> rm: cannot remove ‘/root/update?host=*’: No such file or directoryNo quotes were used, kpatz suggestion.
> rm: cannot remove ‘/root/update?host=www&domain=mysite.com’: No such file or directoryNo quotes were used, SeijiSensei suggestion.

The filename was derived from ```
sudo du -ah --max-depth=1 /root
```appended to a file.

---

### Post by kpatz on 2016-12-13
Can you post a screenshot or a copy/paste of a few of the filenames (from ls -1 or ls -l) ?

---

### Post by ChrisRChamberlain on 2016-12-13
```
4.0K	/root/update?host=www&domain=remindamail.co.uk&password=b7b514179ec9472199a0f3babd18c34d.232
4.0K	/root/update?host=www&domain=motrac.co.uk&password=c766702f3d274fcfaf2edfd1df69321f.7
4.0K	/root/update?host=www&domain=salysis.co.uk&password=753da405e0674b598ddf1e41c4ad1ee0.113
4.0K	/root/update?host=@&domain=invoicebilda.com&password=1784ac0074524172a432f5f360a2aeec.180
```

---

### Post by Graham_Willis on 2016-12-13
You should be extra careful when using wildcards - applying **-- **is a minimal safety measure. Otherwise a file containing a dash may be interpreted as an argument with possibly pretty scary consequences. It's possible that 99% of the time not using **--** will work, but I really doubt that you'd like to ever find yourself in the remaining 1%. Try this:

[B]cd /root
rm -- update?host=*[/B]

The fact that I recommend you to **cd** into the appropriate directory first isn't accidental - in this way you minimize the chance and consequences of executing rm with mistakingly introduced space (like in [COLOR=#ff0000]rm -rf -- /root /update?host=* [/COLOR]- in fact, if you mistakingly introduced spaces in [COLOR=#ff0000]rm -- /root /update?host=* [/COLOR]no much harm'd be done as it doesn't work recursively. But **cd**ing first is a good practice anyway).
If it doesn't work, the following comand probably will - but I'd recommend that earlier you check if you aren't about to remove some files that you need:

[B]cd /root
rm -- update*[/B]

If it doesn't work, run mc (midnight commander) and try to delete these files from there.

Write back in case of problems.

---

### Post by kpatz on 2016-12-13
Since they're in /root, try removing them from a root shell:
```
sudo -i
```
then
```
rm -- /root/update\?host=*
```
Then use **exit** or Ctrl-D to exit from the root shell.

The reason that **sudo rm -- /root/update\?host=*** doesn't work is because the wildcard expansion is occurring in your current shell which doesn't have access to /root.  Running a shell with root privileges and then running the command will allow it to work.

---

### Post by ChrisRChamberlain on 2016-12-13
Graham_Willis - thanks for your reply.

kpatz - your suggestion resolved the issue, many thanks.

> Since they're in /root, try removing them from a root shell:
```
sudo -i
```
then```
rm -- /root/update\?host=*
```

---

