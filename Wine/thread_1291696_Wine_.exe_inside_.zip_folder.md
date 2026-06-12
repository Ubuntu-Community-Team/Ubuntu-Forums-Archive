---
title: "Wine .exe inside .zip folder?"
date: 2009-10-15
forum: Wine
---

### Post by Drasticly on 2009-10-15
Ok so I had a friend send a program through an email and it is inside a .zip folder.  Once I extracted the folder, i cded into the folder and wanted to wine installer.exe.  Well nothing happened...  Also, the .exe isn't even green...

Iniuria CSS Release A.exe      - that is what I need to wine.

Thanks for any help! :)

---

### Post by lisati on 2009-10-15
You will need to unzip the file first. You can then check the .exe file for viruses and, once satisfied that it's safe, you can run it.

---

### Post by Drasticly on 2009-10-15
So I extracted the contents inside the .zip folder back to my desktop.  Then I cded into the folder and typed:
```
wine Iniuria\ CSS\ Release\ A.exe 
```

I was also warned to run the .exe before I unzip it, would this be possible?

---

### Post by BenAshton24 on 2009-10-15
An Aimbot! Really? I think I speak for lots of people when I say.. "we don't need your type around here!" 

Unless, of course you're just testing it in order to truly appreciate the awesomeness of DLL Injection, which I shall presume you are doing :P

Anyways, I wouldn't get your hopes up, a general rule is:

Aimbots + Games in Wine = Failure

But if you really want to try to get it working then we're going to need more information on what exactly "nothing happened" means. Did the program hang, or did it just stop and give you a prompt again? Any error message?

When you say that the executable wasn't even green I presume that you are talking about when you run "ls." To rectify this you can run:
```
chmod +x "Iniuria CSS Release A.exe"
```
Although that won't actually do anything since your using "wine" to execute it therefore it does not need to be executable in order to start.

Also, from my very limited knowledge about aimbots, don't they usually have to be in the same folder as your game executable?

Hope this helps,
Ben.

---

### Post by Drasticly on 2009-10-15
I only use my powers for good! Never evil!  I just simply want to be able to counteract a hacker in Counter Strike Source since each server these days seems to have hackers who think "hacking is fun."

The first time I ran the .exe, I got an error saying it experienced a critical error and needed to close.  The second time, the terminal just went to the next line and hung there forever.

I ran the chmod code listed above and got:
```
chmod +x "Iniuria\ CSS\ Release\ A.exe"
chmod: cannot access `Iniuria\\ CSS\\ Release\\ A.exe': No such file or directory

```

Thanks for the help!
Drastic

---

### Post by BenAshton24 on 2009-10-15
```
chmod +x "Iniuria CSS Release A.exe"
```
You don't need to escape the spaces since it is contained in speech marks. The reason it is saying that there is no such file or directory is because it is treating your backslashes literally, hence the double backslashes in the error :P

Anyway, this doesn't get you any closer to solving the problem since the way you were running it should have been fine with or without executable permissions on the file.

Without knowledge of how the hack works I can't really help you, maybe it was hanging on the next line because it was running and was waiting to get a hook on CSS when you started it? 

As I said before I doubt that you will be able to get this to work, unfortunately, hacks like these tend to be heavily reliant on 100% windows :(

Good luck though!
Ben.

---

### Post by hikaricore on 2009-10-15
> **BenAshton24 said:**
> As I said before I doubt that you will be able to get this to work, **fortunately** hacks like these tend to be heavily reliant on 100% windows :(

fixed

---

### Post by beastrace91 on 2009-10-15
You do not need to chmod +x a .exe you are going to be running through Wine... You only need to wine <file name>.exe

That being said - outside programs like this most often times will not run through wine as has been stated. chmod +x is only needed when you are running native Linux files - .sh, .run, .bin ect.

~Jeff

---

