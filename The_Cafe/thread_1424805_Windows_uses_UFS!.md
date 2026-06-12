---
title: "Windows uses UFS?!"
date: 2010-03-08
forum: The Cafe
---

### Post by makaki on 2010-03-08
I was fixing a PC that runs XP. Then suddenly I removed a usb flash memory. Then I got this message (in the attachment).

Notice: \Harddisk\DR4

It looks like Windows uses UFS(Unix File System), but sure it uses '\' instead of '/'. If this is true, isn't it violating open source license? i.e shouldn't be free or open source. I don't know about the license behind UFS.

---

### Post by Dayofswords on 2010-03-08
"\" are used for local files in windows

the \Device\blah is normal most OS i think

plus it like it (internally) but not the same code


[SIZE="1"]random ramblings. I may be wrong, in fact, theres a good chance of it[/SIZE]

---

### Post by Grifulkin on 2010-03-08
Wow, that is all I have to say is wow.  And most likely it wouldn't be against the copyright of UFS.

---

### Post by Bachstelze on 2010-03-08
How on earth did you come to the conclusion that Windows uses UFS just by seeing that?

---

### Post by tcoffeep on 2010-03-08
> **Bachstelze said:**
> How on earth did you come to the conclusion that Windows uses UFS just by seeing that?

If someone wants to see something, they usually do.

---

### Post by mickie.kext on 2010-03-08
> **makaki said:**
> 
It looks like Windows uses UFS(Unix File System), but sure it uses '\' instead of '/'. If this is true, isn't it violating open source license? i.e shouldn't be free or open source. I don't know about the license behind UFS.

UFS is distributed under Modified BSD who do not forbid making proprietary versions. So they could do it but... how did you come to conclusion that Windows use UFS? It do not uses UFS.

It uses NTFS. "New Techlogy File System" which is developed by IBM and Microsoft in early 90es. It is not open source.

---

### Post by Bachstelze on 2010-03-08
> **mickie.kext said:**
> UFS is distributed under Modified BSD licence who permits lockdown of previously open source code.

Could you please stop spreading that FUD?

---

### Post by mickie.kext on 2010-03-08
> **Bachstelze said:**
> Could you please stop spreading that FUD?

Fixed wording. Are you satisfied?

---

### Post by madhi19 on 2010-03-08
> **mickie.kext said:**
> UFS is distributed under Modified BSD who do not forbid making proprietary versions. So they could do it but... how did you come to conclusion that Windows use UFS? It do not uses UFS.

It uses NTFS. "New Techlogy File System" which is developed by IBM and Microsoft in early 90es. It is not open source.

I think it time they rename NTFS after all it not New anymore! :p

---

### Post by makaki on 2010-03-08
I said it uses UFS because it's starts with '\' which something like root folder, then 'Device' which also exists in the root folder...etc

---

### Post by chriswyatt on 2010-03-08
And there is a Device folder in the root of C: then?

---

### Post by jrothwell97 on 2010-03-08
> **makaki said:**
> I said it uses UFS because it's starts with '\' which something like root folder, then 'Device' which also exists in the root folder...etc

That's not UFS, that's simply a low-level naming convention.

It's no secret: just take a look at boot.ini or try using the Windows recovery console without seeing the internal device naming system.

The naming convention is *not* the same as the file system.

---

### Post by kk0sse54 on 2010-03-08
> **makaki said:**
> I said it uses UFS because it's starts with '\' which something like root folder, then 'Device' which also exists in the root folder...etc

First off, do you even know what UFS is?

---

### Post by whiskeylover on 2010-03-08
> **C!oud said:**
> First off, do you even know what UFS is?

Why don't you explain it to him then? Why are you rude for no reason?

---

### Post by Barrucadu on 2010-03-08
> **whiskeylover said:**
> Why don't you explain it to him then? Why are you rude for no reason?

It's not rude, it's a simple question.

---

### Post by tcoffeep on 2010-03-08
If you look for a rude tone in that question, it's quite possible to see it... if you look for it.

---

### Post by chriswyatt on 2010-03-08
> **tcoffeep said:**
> If you look for a rude tone in that question, it's quite possible to see it... if you look for it.

I sometimes do that on the internet actually, read something in a rude or sarcastic tone and forget that the tone of voice actually came from my head and not the person on the forum.  I've occasionally been a little defensive when I probably shouldn't have been.

---

### Post by kk0sse54 on 2010-03-08
> **whiskeylover said:**
> Why don't you explain it to him then? Why are you rude for no reason?

Like Barrucadu said, it was but a simple question whose answer is key to refuting your original statement. I apologize if you took it to be rude, but quite to the contrary it was meant to provoke a search for the answer which could have been easily accomplished with a simple google or wikipedia search rather than being unnecessarily spoon fed as so often happens on these forums.

---

### Post by whiskeylover on 2010-03-08
In that case, I apologize for my statement.

---

### Post by Dayofswords on 2010-03-10
i was working on a lab in my operating systems II: Windows class

i did find this
[IMG]http://dayofswords.com/picsforanything/Capture.JPG[/IMG]


its just an internally naming thing really

---

### Post by forrestcupp on 2010-03-10
> **Bachstelze said:**
> Could you please stop spreading that FUD?

Where was the FUD?  The modified BSD license *does* allow source code that was previously open to be locked down and distributed in a proprietary format, as long as the requirements are met.  

I don't see any fear, uncertainty, or doubt in that statement.

---

