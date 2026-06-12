---
title: "Please help me understand GNU GPL moment..."
date: 2010-07-02
forum: The Cafe
---

### Post by Istrebitel on 2010-07-02
Greetings!

Since i got interested in Open Source philosophy and linux, i've read about GPL and studied it alot. I made a conclusion that one of the points is:

- if a program/library/piece of code is released under GPL, then any program/library/piece of code that uses it, should also be released under GPL. 

That way, it promotes Open source as you cannot use something someone released as GPL, build on top of it and claim it as yourself (proprietary licence)

How come do stuff like this exists then: "LZMA compression algorithm is very suitable for embedded applications. LZMA is released under the terms of the GNU LGPL. LZMA is also available under a proprietary license for those who can not use the GNU LGPL in their code."

How can the same code exist as GPL and as proprietary license?

Analogues exist everywhere - Open Office/Star Office for example. What is this? Does this mean you actually CAN take GPL code and release it under proprietary license?

Explain this to me please. I am confused here.

Thanks in advance!

---

### Post by DoubleClicker on 2010-07-02
> **Istrebitel said:**
> Greetings!

Since i got interested in Open Source philosophy and linux, i've read about GPL and studied it alot. I made a conclusion that one of the points is:

- if a program/library/piece of code is released under GPL, then any program/library/piece of code that uses it, should also be released under GPL. 

That way, it promotes Open source as you cannot use something someone released as GPL, build on top of it and claim it as yourself (proprietary licence)

How come do stuff like this exists then: "LZMA compression algorithm is very suitable for embedded applications. LZMA is released under the terms of the GNU LGPL. LZMA is also available under a proprietary license for those who can not use the GNU LGPL in their code."

How can the same code exist as GPL and as proprietary license?

Analogues exist everywhere - Open Office/Star Office for example. What is this? Does this mean you actually CAN take GPL code and release it under proprietary license?

Explain this to me please. I am confused here.

Thanks in advance!

The original author of the code can license it under multiple licenses, as long as he doesn't include someone else's GPL code.  If you use the open sources code  that's under GPL you must abide by all the terms of the GPL. However if you license the code (usually for a fee) from the original author under a proprietary license, you can use the code without distributing the source.

The original author owns the code and can do whatever he wants with it.

---

### Post by Istrebitel on 2010-07-02
Thanks. But still, how does OpenOffice gets released under proprietary license if it inherits works of peope who contributed to the project? Or is the whole Open-Office made by Sun Microsystems?

---

### Post by mickie.kext on 2010-07-02
> **Istrebitel said:**
> Greetings!

Since i got interested in Open Source philosophy and linux, i've read about GPL and studied it alot. I made a conclusion that one of the points is:

- if a program/library/piece of code is released under GPL, then any program/library/piece of code that uses it, should also be released under GPL. 

That way, it promotes Open source as you cannot use something someone released as GPL, build on top of it and claim it as yourself (proprietary licence)

How come do stuff like this exists then: "LZMA compression algorithm is very suitable for embedded applications. LZMA is released under the terms of the GNU LGPL. LZMA is also available under a proprietary license for those who can not use the GNU LGPL in their code."

How can the same code exist as GPL and as proprietary license?

Analogues exist everywhere - Open Office/Star Office for example. What is this? Does this mean you actually CAN take GPL code and release it under proprietary license?

Explain this to me please. I am confused here.

Thanks in advance!

No, you can't release other's people GPL code under anything other than GPL. But you can re-release your code under any license you want. That is because of copyright law, not GPL. 

For example, you write a program and release it under GPL. Then GPL apply to other people, but you can still take the code and put it in proprietary program, because it is your "property". You can't "steal" from yourself. You would have to sue yourself to enforce GPL in that case, because copyright holder is only one that can enforce GPL.

But when other people contribute to your program, then parts they wrote are not yours. You no longer can re-license whole program, only parts you wrote. However, you can set a policy that says that outside developers must sign contributor agreement which says that original developer is allowed to re-license code. Again, that is feat of copyright law, not GPL. 

In case of OpenOffice, Sun bought company called StarDivision which produced proprietary StarOffice program. Sun released it under LGPL and from later on asked every contributor to sign copyright assignment. So they still can re-license at will. But such a policy [turned down some contributors]("http://www.h-online.com/open/features/OpenOffice-at-the-crossroads-1023702.html"), because FLOSS people like transparency and don't trust for-profit companies. 

On other hand, Linux kernel is a mess in that regard, everyone and their mother owns copyrights. So to change license, you have to ask all those people. That's why it couldn't switch to GPLv3. 

GNU project for example has very interesting copyright assignment policy. Every contributor must sign contributor agreement to assign copyrights to FSF. But FSF then signs that they can't re-license code, and they effectively just can sue violators but they don't own re-licensing rights. They can just re-license to newer version of GPL. 

I hope I helped.

---

### Post by Istrebitel on 2010-07-02
Thank you you have been very hepful.

so, in simple human terms, every contributor to OpenOffice signs a contract that he allows Sun Microsystems to release his code as a private property?

---

### Post by mickie.kext on 2010-07-02
> **Istrebitel said:**
> Thank you you have been very hepful.

so, in simple human terms, every contributor to OpenOffice signs a contract that he allows Sun Microsystems to release his code as a private property?

Well, sort of. They can't cut of community from code community write. Contributor remains owner of the code, but they assign right to re-license it to Sun. So Sun must make that code available under LGPL (or else contributor will do it himself) and can integrate it in OpenOffice. But Sun can also integrate that code in proprietary StarOffice, and can sub-license that code to other party such is IBM, to integrate in their proprietary Lotus Symphony. Which they did. And that caused some ill will in OpenOffice community, because Sun didn't want to disclose terms under which they sub-licensed code to IBM.

Here is little something about dual licensing:
[http://en.wikipedia.org/wiki/Multi-licensing](http://en.wikipedia.org/wiki/Multi-licensing)

Dual-licensing is not necessarily evil, but it should be done transparently and contributors should know upfront where their code might also end up and under which terms.

---

### Post by Istrebitel on 2010-07-02
Thats it. I get it now, thanks!

---

### Post by forrestcupp on 2010-07-02
One thing that may be confusing is that Oracle changed the name of StarOffice to OpenOffice.  OpenOffice is a completely different program than OpenOffice.org, which is Free Software.  The new OpenOffice is just a renaming of Star Office, which has the same roots as OpenOffice.org.  But I suspect that the code base for Star Office isn't very close to the current OO.o anymore.

Also, OO.o is licensed under the LGPL license, which allows people to create software that links to the LGPL licensed software without being forced to release their own software under a free license.

---

