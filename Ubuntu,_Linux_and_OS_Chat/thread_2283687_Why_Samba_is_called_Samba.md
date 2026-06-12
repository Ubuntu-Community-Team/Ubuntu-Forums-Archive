---
title: "Why Samba is called Samba?"
date: 2015-06-23
forum: Ubuntu, Linux and OS Chat
---

### Post by papakota on 2015-06-23
Hello!

Samba is a Brazilian carnival dance name. So why does Linux protocol called the same?
I didn't understand the Wikipedia explanation, frankly...

---

### Post by sudodus on 2015-06-23
See this link:

[https://www.samba.org/samba/docs/SambaIntro.html](https://www.samba.org/samba/docs/SambaIntro.html)

> 
Andrew Tridgell, who is both tall and Australian, had a bit of a problem.  He needed to mount disk space from a Unix server on his DOS PC.  Actually, this wasn't the problem at all because he had an NFS (***N**etwork **F**ile **S**ystem*) client for DOS and it worked just fine.  Unfortunately, he also had an application that required the NetBIOS interface.  Anyone who has ever tried to run multiple protocols under DOS knows that it can be...er...quirky.   

So Andrew chose the obvious solution.  He wrote a packet sniffer, reverse engineered the SMB protocol, and implemented it on the Unix box.  Thus, he made the Unix system appear to be a PC file server, which allowed him to mount shared filesystems from the Unix server while concurrently running NetBIOS applications.  Andrew published his code in early 1992.  There was a quick, but short succession of bug-fix releases, and then he put the project aside.  Occasionally he would get E'mail about it, but he otherwise ignored it.  Then one day, almost two years later, he decided to link his wife's Windows PC with his own Linux system.  Lacking any better options, he used his own server code. He was actually surprised when it worked.   
Through his E'mail contacts, Andrew discovered that NetBIOS and SMB were actually (though nominally) documented.  With this new information at his fingertips he set to work again, but soon ran into another problem.  He was contacted by a company claiming trademark on the name that he had chosen for his server software.  Rather than cause a fuss, [COLOR=#ff0000]Andrew did a quick scan against a spell-checker dictionary, looking for words containing the letters "smb".  "Samba" was in the list[/COLOR].  Curiously, that same word is not in the dictionary file that he uses today.  (Perhaps they know it's been taken.)   


---

### Post by grahammechanical on 2015-06-23
And there was me thinking that the name was chosen because it did something similar to Rumba.

I used to work for a high street chain and sales assistants could use Windows computers to connect to the warehouse computers and order garments as a customer request. The system would show if the garment was in stock or not. The sale assistant would switch from the usual Windows desktop into Rumba.

When I installed Ubuntu on my personal computer and heard about Samba and I made a connection in my mind to Rumba because FOSS developers often make a play on words in the names they choose.

Now, I know differently.

Regards.

---

### Post by wildmanne39 on 2015-06-23
I learn something new every day!:)

---

### Post by QIII on 2015-06-24
They wanted to call it "Chuck", but that was taken...

:)

---

### Post by Bucky Ball on 2015-06-24
> **QIII said:**
> They wanted to call it "Chuck", but that was taken...

:)

Mate, the guy was an Australian. He wanted to call it Mate, mate, but cos he didn't, now that's been taken, mate!

To Andrew the Australalian, chuck is something you do with a cricket ball or a 'stubby' of beer to a mate, mate, or you chuck snags on a barbie(q), mate. :)

(I am Australian and, while wittily written [debatable], the previous sentence is, in fact, true!)

---

### Post by papakota on 2015-06-24
I see now... Thank you all for your replies!

---

