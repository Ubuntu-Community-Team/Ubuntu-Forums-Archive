---
title: "A question about Viruses."
date: 2010-10-19
forum: Security
---

### Post by Sanzoku on 2010-10-19
Hey Im Sanzo and just out of nowhere I decided yesterday to try an OS different from windows. I installed Ubuntu through Wubi while I was using windows and it created a dual-boot of sorts. I have been told that Ubuntu like OSX is unaffected by normal viruses made for windows. I was wondering though if I entered a virus filled alley of the internet or something while on ubuntu is it possible for the things that are harmless to ubuntu still latch onto my windows partition while im using only ubuntu? 

Thanks in advance also sorry if that was worded in a really weird way. 


Ps. A very unrelated question but are there equivilants to the crtl+ c, v, and x shortcuts on ubuntu?

---

### Post by Grenage on 2010-10-19
Yes and no.

Linux won't execute the code and infect anything, but you could download an infected file and then later run it from Windows.

> **Sanzoku said:**
> Ps. A very unrelated question but are there equivilants to the crtl+ c, v, and x shortcuts on ubuntu?

Yup, same keys.

---

### Post by Sanzoku on 2010-10-19
Oh I see. Thank you very much for the quick answer.

So they are the same keys then. I tried them but does Terminal maybe not allow copy paste cut?

---

### Post by Fableflame on 2010-10-19
> **Sanzoku said:**
> Oh I see. Thank you very much for the quick answer.

So they are the same keys then. I tried them but does Terminal maybe not allow copy paste cut?

In the terminal you'll actually have to right click and click copy, or right click and click paste.

---

### Post by Sanzoku on 2010-10-19
ah. Thanks a lot. 
Ill get the hang of it yet.

---

### Post by kleskjr on 2010-10-19
in terminal you can use crtl + shift + c, v for copy/paste

---

### Post by pqwoerituytrueiwoq on 2010-10-19
if you are feeling lazy you can highlight the text and them click with your mouse wheel
Warning it will be a little annoying when you go to use that on windows out of habit and it do nothing

---

### Post by Sanzoku on 2010-10-19
> **kleskjr said:**
> in terminal you can use crtl + shift + c, v for copy/paste

oh awesome thank you.

just for the heck of it is there any reason shift is added? does ctrl+ c, v or x have another function within Terminal?

> if you are feeling lazy you can highlight the text and them click with your mouse wheel
Warning it will be a little annoying when you go to use that on windows out of habit and it do nothing

That is just amazing. simply the best copy shortcut I have ever heard of

---

### Post by TBABill on 2010-10-19
If you had a true dual boot you would not be affected by Windows viruses directly. You could still download the malicious file and pass it on to others (on Windows machines), but it would not be harmful on your machine. Under Wubi you are more susceptible to those because it is installed within your Windows partition. If your goal is to run the machine without the same vulnerability, booting directly into Ubuntu on a separate partition is the safer way to do so. And booting and running from the LiveCD is the safest way because you are not using an OS from the hard drive.

---

### Post by nlsthzn on 2010-10-19
> **pqwoerituytrueiwoq said:**
> if you are feeling lazy you can highlight the text and them click with your mouse wheel
Warning it will be a little annoying when you go to use that on windows out of habit and it do nothing

Just read this and I am like no way... tried it and was like "Way!" Awesome!

---

### Post by Sanzoku on 2010-10-19
So by using wubi it is not a true dual-boot?
hmm. If my Ubuntu is a part of windows then why cant I access my windows files?
I tried to follow a guide to mount it but to no avail.

---

### Post by SeijiSensei on 2010-10-19
You can also usually cut a line in the Terminal with Ctrl-k and retrieve it with Ctrl-y.  (These commands also work in emacs and clones like jed.)

Ctrl-k cuts from the cursor position to the end of the line.  If you want to extract a substring from a line, you'll need to use the right-clicking techniques.

---

### Post by Sanzoku on 2010-10-19
Oh I see. I have a lot of new shortcuts to memorize. Thanks a lot

---

### Post by TBABill on 2010-10-19
In Wubi you are on a virtual partition, which is like a partition dedicated to Ubuntu within your Windows partition. In a true dual boot you have a partition for each OS. 
 
More here: [https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi) or [http://en.wikipedia.org/wiki/Wubi_(Ubuntu](http://en.wikipedia.org/wiki/Wubi_(Ubuntu))[]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer")

---

### Post by Sanzoku on 2010-10-19
I see. So as a virtual partition is there a difference in performance?

---

### Post by The Cog on 2010-10-19
> just for the heck of it is there any reason shift is added? does ctrl+ c, v or x have another function within Terminal?Yes, these keys have their own meanings in terminal. Especially Ctrl-C which will usually terminate whatever command is running.
> So as a virtual partition is there a difference in performance?I hear there is a small performance loss but not much. 

You should be able to access your windows files, whether you use WUBI or not. Open your home folder and then in the file explorer (called nautilus) go to the Computer icon. You should see the other partitions there. You may have difficulty if windows did not shut down cleanly though - use windows to chkdisk them in that case.

---

### Post by Sanzoku on 2010-10-19
Oh. awesome.
would windows preparing for updates the next time it boots count as an unclean shutdown perhaps? if so that was the case. if not ill have to do more research.
Thanks

---

### Post by PhilGil on 2010-10-19
If nothing has changed since I used WUBI, your Windows drive is available in the /host directory of the File System (Places > Computer > File System > [I]host)

[/I]Enjoy your new Ubuntu Install[I].
[/I]

---

### Post by Sanzoku on 2010-10-20
Oh yea! my windows stuff wasnt automatically there and I totally failed at using terminal to do it but I found an app thing that helped me mount it correctly. Thanks a lot guys. I even got my arcade emulator working in wine xD

---

### Post by ronnielsen1 on 2010-10-20
> I even got my arcade emulator working in wine xD
Which emulator? There's probably a native linux version

---

### Post by Sanzoku on 2010-10-20
Its a Cps3 cabinet emulator. 
I use it to play Street Fighter: Third Strike

I tried to use wine to play Street Fighter IV and BlazBlue CS but I guess theyre too heavy to be emulated by wine.

My boss told me about something called Cedega. any chance of that running heavier games?


(also am i breaking any rules if im talking about this stuff in a thread that i used to ask about viruses? I come here while im at work so I have to be quick and havent really had time to look for the rules. Sorry bout that)

---

### Post by bodhi.zazen on 2010-10-20
> **TBABill said:**
> In Wubi you are on a virtual partition, which is like a partition dedicated to Ubuntu within your Windows partition. In a true dual boot you have a partition for each OS. 
 
More here: [https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi) or [http://en.wikipedia.org/wiki/Wubi_(Ubuntu](http://en.wikipedia.org/wiki/Wubi_(Ubuntu))[]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer")

That is an extremely narrow definition of Dual Booting. You are splitting hairs from an old definition what was written before wubi or similar technology was in existence. You are splitting hairs on the definition of a partition (ie a physical partition vs the method used by wubi, loop mounting a file).

Most people consider wubi to be dual booting.

---

