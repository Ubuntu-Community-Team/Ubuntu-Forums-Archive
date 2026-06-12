---
title: "How to reverse-engineer My Ubuntu Package"
date: 2013-06-25
forum: Ubuntu Dev Link Forum
---

### Post by Bresser on 2013-06-25
Ok, So like a month ago I made the program, "GibberEng". Just a simple program that encrypts a string. But while, it is simple it took very long to code, since its GUI and has its own unique encryption method. But last week my harddrive broke. All my data is lost and I didn't have a back-up (won't make that mistake again). Is there any way I can like decompile it and get its source?

---

### Post by MG&amp;TL on 2013-06-26
> **Bresser said:**
> Ok, So like a month ago I made the program, "GibberEng". Just a simple program that encrypts a string. But while, it is simple it took very long to code, since its GUI and has its own unique encryption method. But last week my harddrive broke. All my data is lost and I didn't have a back-up (won't make that mistake again). Is there any way I can like decompile it and get its source?

What langauge is it written in, and have you got a copy of the binary somewhere?

---

### Post by Bresser on 2013-06-26
No thats why I'm worried. All i have is the package from Ubuntu Software Center.  And it is written in C++ with some qt GUI libraries.

---

### Post by MG&amp;TL on 2013-06-27
> **Bresser said:**
> No thats why I'm worried. All i have is the package from Ubuntu Software Center.  And it is written in C++ with some qt GUI libraries.

Well, the package from USC is just a debian package, which is itself just a compressed folder with some install scripts. Extract (drop it into Archive Manager) a copy of the package somewhere, and see what's in there.

If you haven't got any source at all, I don't hold much hope, but you can never tell. C++ isn't easy to decompile.

---

