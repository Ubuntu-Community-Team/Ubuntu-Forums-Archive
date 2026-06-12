---
title: "12Voip; PROBLEMS WITH WINE"
date: 2011-05-05
forum: Wine
---

### Post by bros on 2011-05-05
Hello!
I just finished to install 12Voip on Ubuntu 11.04 with WINE, everything ok till a try to open the application while I was connect to Internet and this is the message that I got:

**Program Error**

**The program 12Voip.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience.**

It doesn't matter how many times I tried, I'm getting the same message every time.

Can somebody help me? THANK YOU IN ADVANCE!

---

### Post by cogadh on 2011-05-05
Run the application from the terminal to get Wine's error output, that might tell us what is happening.

---

### Post by bros on 2011-05-05
> **cogadh said:**
> Run the application from the terminal to get Wine's error output, that might tell us what is happening.

Sounds a good idea... the only problem is that I'm pretty new with Ubuntu (in general), can you please tell me how to run it with the terminal? THANK YOU!

---

### Post by cogadh on 2011-05-05
Open a terminal (Applications menu > Accessories > Terminal), change directories to where the application is installed, then "wine" the executable:
```
cd ~/.wine/drive_c/<application installation path>
wine <executable name>.exe
```
Make sure to replace that "<application installation path>" and "<executable name>" with the correct information for your application.

---

### Post by bros on 2011-05-06
> **cogadh said:**
> Open a terminal (Applications menu > Accessories > Terminal), change directories to where the application is installed, then "wine" the executable:
```
cd ~/.wine/drive_c/<application installation path>
wine <executable name>.exe
```
Make sure to replace that "<application installation path>" and "<executable name>" with the correct information for your application.

I tried to use the two codes and the terminal says that I do not have such file or directory... but I do have it. Something that I'm doing wrong? THANK YOU!

---

### Post by cogadh on 2011-05-06
Let me guess, the app is installed somewhere in "Program Files", right? Terminal commands will have a problem with the space between "Program" and "Files", it won't be recognized. To get around it, you need to run the command like this:
```
cd ~/.wine/drive_c/Program\ Files/<app installation directory>
```
The "\" in the middles of "Program Files" will allow the terminal to "see" the space.

---

### Post by bros on 2011-05-06
> **cogadh said:**
> Let me guess, the app is installed somewhere in "Program Files", right? Terminal commands will have a problem with the space between "Program" and "Files", it won't be recognized. To get around it, you need to run the command like this:
```
cd ~/.wine/drive_c/Program\ Files/<app installation directory>
```
The "\" in the middles of "Program Files" will allow the terminal to "see" the space.

Your guess was right...I'll never stop learning! However I did what you said and I copied here below what I got from the Terminal so you can have more information:

**err:ntdll:RtlpWaitForCriticalSection section 0xd9bfa0 "?" wait timed out in thread 0047, blocked by 0028, retrying (60 sec)**

---

### Post by cogadh on 2011-05-06
There should have been much more than just that one error, we need the entire output to effectively analyze this. When you do post the full output, use the forum [code] tags, it will preserve the output format and layout. The [code] tags work just like the [quote] tags.

---

### Post by bros on 2011-05-06
[https://dl-web.dropbox.com/get/Error.pdf?w=a3bf3b92&dl=1]("https://dl-web.dropbox.com/get/Error.pdf?w=a3bf3b92&dl=1")

Here you have the whole text, thanks again for your help!

---

### Post by cogadh on 2011-05-06
That site requires a login to view the file.

---

### Post by bros on 2011-05-06
> **cogadh said:**
> That site requires a login to view the file.

Sorry, try with this one:

[http://dl.dropbox.com/u/12931707/Error.pdf](http://dl.dropbox.com/u/12931707/Error.pdf)

---

### Post by cogadh on 2011-05-06
Crap. Most of the errors in that are due to Wine lacking the functionality 12Voip needs. I don't think it is going to work...

And after checking Wine's Application Database (something we probably should have done at the very start), it's definitely not:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=12888](http://appdb.winehq.org/objectManager.php?sClass=application&iId=12888)

Your only option is going to be to wait until Wine is further developed.

---

### Post by bros on 2011-05-06
> **cogadh said:**
> Crap. Most of the errors in that are due to Wine lacking the functionality 12Voip needs. I don't think it is going to work...

And after checking Wine's Application Database (something we probably should have done at the very start), it's definitely not:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=12888](http://appdb.winehq.org/objectManager.php?sClass=application&iId=12888)

Your only option is going to be to wait until Wine is further developed.

That's not good... thank you however for your help!

---

