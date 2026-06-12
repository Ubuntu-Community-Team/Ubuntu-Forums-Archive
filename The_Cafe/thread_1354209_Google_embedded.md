---
title: "Google embedded"
date: 2009-12-13
forum: The Cafe
---

### Post by Marvin666 on 2009-12-13
Is google embedded into ubuntu to the point, were you can't remove all traces of it? one time on a win install I tried to remove IE, google, and all registry (heh, registry...) keys pointing to those two. Needles to say, I failed miserably. Is anything wedged this deep into ubuntu, that it can't be pried out?

---

### Post by joey-elijah on 2009-12-13
"Google" isn't embedded into Ubuntu at all!

The only thing comparable to IE in Ubuntu is Evolution whereby you can't remove *every *last part of it because the GNOME/ubuntu desktop relies on parts of it.

(Well from my experience, I've never been able to remove evolution-server-common without removing Ubuntu-Desktop)

I also don't understand how you had "google" in your windows registry. Am i missing something?

---

### Post by pwnst*r on 2009-12-13
> **Marvin666 said:**
> Is google embedded into ubuntu to the point, were you can't remove all traces of it? one time on a win install I tried to remove IE, google, and all registry (heh, registry...) keys pointing to those two. Needles to say, I failed miserably. Is anything wedged this deep into ubuntu, that it can't be pried out?

what the hell is the matter with you people?

---

### Post by nmccrina on 2009-12-13
> **pwnst*r said:**
> what the hell is the matter with you people?

Yeah, I don't know, the last like week everyone's been running around screaming "ZOMG!!! TEH GOOGLEZ!" and switching to Bing and stuff. It's like the tech version of the swine flu fiasco. I almost went along with it, but then I was like, wait a minute, what? I don't care if everybody sees everything I do with a computer, it's not that interesting.

I counted yesterday, and at least 6 of the 20 threads on the front page of the cafe had Google in their title. [-(

---

### Post by ceramicm on 2009-12-13
[QUOTE=joey-elijah](Well from my experience, I've never been able to remove evolution-server-common without removing Ubuntu-Desktop)[/QUOTE]

ubuntu-desktop is just a metapackage, and is perfectly safe to remove. Your Ubuntu will still work without it.

Installing ubuntu-desktop pulls in all the software that it a part of the default Ubuntu install, but none of that software needs ubuntu-desktop to function properly.

Here's one use of it: Ubuntu 10.04 will include a video editor by default. Since this program is now part of the default install, it will be installed automatically when ubuntu-desktop is updated from the 9.10 version. The installation of ubuntu-desktop eases transitions between versions, but again, it is perfectly safe to remove.

It is difficult to remove Evolution completely, but I personally appreciate its integration with GNOME. I think I read somewhere that the devs are working on making it easier to remove, don't remember a source.

---

### Post by Marvin666 on 2009-12-13
If you look through the keys carefully, you'll see google in numerous places. Various web browsers have google links in their keys. Many commercial programs also point to google in their keys.
I've had a very long vendetta against google.... It goes back further than my dislike of microsoft even.

---

