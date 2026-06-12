---
title: "so where IS my Thunderbird executable ?"
date: 2006-03-08
forum: The Cafe
---

### Post by rfruth on 2006-03-08
Okay breezy is treating me fine so just out of curiosity, where IS my stock Firefox 1.0.7 executable (not the profile) there is a /etc/mozilla-firefox but that's not it... I can't find it, help me out :-k

---

### Post by Mustard on 2006-03-08
Hmmm..I wonder which is which?

```
mustard@slave:/usr/bin$ ls /usr/bin/ | grep firefox
firefox
firefox.ubuntu
mozilla-firefox

```

I've got Firefox 1.5 installed , which I think is the 'firefox' reference.  I would think the 1.0.7 version is the mozilla-firefox.  I have no idea what firefox.ubuntu is. :)

---

### Post by kaamos on 2006-03-08
/usr/bin/mozilla-firefox

Almost all executable files are under different bin directories. You can check your directories with  "echo $PATH"

---

### Post by rfruth on 2006-03-08
I have a /usr/bin/mozillla-firefox but its labeled link to shell script, guess I need to try & decipher that  ...

[ATTACH]6853[/ATTACH]

---

### Post by cdhotfire on 2006-03-08
[QUOTE=Mustard]Hmmm..I wonder which is which?

```
mustard@slave:/usr/bin$ ls /usr/bin/ | grep firefox
firefox
firefox.ubuntu
mozilla-firefox

```

I've got Firefox 1.5 installed , which I think is the 'firefox' reference.  I would think the 1.0.7 version is the mozilla-firefox.  I have no idea what firefox.ubuntu is. :)[/QUOTE]

firefox.ubuntu is 1.0.7 automatix renames it that, I think.  mozilla-firefox must be 1.0.7 as well. :|

Firefox is /usr/bin/firefox, this is because when you type in "firefox" in terminal, it means /usr/bin/firefox, or /usr/sbin/, it checks them both.  So if you type "firefox.ubuntu" it will boot up 1.0.7.  When you type a single word expresion it looks in either /usr/bin/ or /usr/sbin/.

---

### Post by aysiu on 2006-03-08
Why is the subject Thunderbird when everything in the thread is about Firefox? Just curious.

---

### Post by rfruth on 2006-03-08
I should have named this Firefox not Thunderbird ...

---

### Post by poofyhairguy on 2006-03-09
[QUOTE=rfruth]I should have named this Firefox not Thunderbird ...[/QUOTE]


sigh

---

### Post by Kvark on 2006-03-09
In the future when you wonder where other executables are. Use the "which program-name" command to find them. In this case "which firefox" returns "/usr/bin/firefox" which means thats the executable that is used to launch firefox.

If "which..." doesn't work because you are unsure on the exact name of the program (for example in this case it is unclear if it is firefox or mozilla-firefox that is used) then right click on it's icon in the panel, desktop or menu editor (the editor cause it doesn't work in the menu itself) and select properties. The field labelled "command" contains the exact name possibly followed by some arguments.

If you are unsure of which version an executable is then they usually tell you if you use the "--version" argument. In this case "firefox --version", "mozilla-firefox --version" and  "firefox.ubuntu --version" would tell you which version each of the executables are.

---

