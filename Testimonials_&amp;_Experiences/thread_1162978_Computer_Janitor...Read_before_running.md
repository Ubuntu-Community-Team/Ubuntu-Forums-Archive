---
title: "Computer Janitor...Read before running"
date: 2009-05-18
forum: Testimonials &amp; Experiences
---

### Post by gdonwallace on 2009-05-18
Up until last Friday, my Ubuntu experience has been good.  No show stopping production stand still issues.

It had been almost 2 weeks since I updated to 9.04 and I had installed / uninstalled several programs, so I wanted to make sure that my computer was running at top speed.  That nothing was left hanging that should not be there, and decided to run the Computer Janitor, that was a mistake.

One of the programs that popped up on the Janitor to be removed was OpenOffice.  Having removed OOo that was installed so I could update to the newly released 3.1, I didn't think anything of it, as I was thinking the Janitor had found some left over files from the previous install.  So I went ahead and ran the removal.

BIG...HUGE mistake.  What I later found out was, since OOo 3.1 is not in the repo's, the Janitor assumed that it was incorrectly installed, and therefore removed it.  

It would seem that anything that is not in the repo's is to be marked for deletion from your system.  

I would advise NOT running the Computer Janitor if you have ANY SOFTWARE that is not in any of the "Official" repos.  Otherwise You may end up with the problem I have this morning, having to download and reinstall OOo, before I can actually get some work done....Hence why I am on this message board and not working.

---

### Post by juancarlospaco on 2009-05-18
Is the response to newbiews looking for a GUI to "* sudo apt-get clean ; sudo apt-get autoremove "*

So it works for others...

---

### Post by mkvnmtr on 2009-05-18
I don't want to use the terminal to auto clean and remove. I guess I think slowly and need time to study what I am going to do. Thus I use the package manager. It lists it all and I can see what depends on what. It takes me longer but I haven't made any mistakes. That being said I don't like computer janitor and have removed it completely from my installs. I am sure somebody worked hard on it but it is not for me.

---

### Post by NCLI on 2009-05-20
It warns you when it removes files you may need ;)

---

### Post by Gausian on 2009-05-20
not to be mean, but it seems that you made a mistake and you're blaming it on the janitor.  it did what it was designed to do.  you can easily uncheck any package that it picks up and it will leave it alone.

it also specifies the version numbers of packages that it recommends for removal, so again you manually removed the OO 3.1 package, not the janitor.

---

### Post by lukjad on 2009-05-20
I think this is more of a vent/warning than anything else. :)

---

