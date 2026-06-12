---
title: "Firefox 3.0 beta 1 released..."
date: 2007-11-20
forum: The Cafe
---

### Post by Colro on 2007-11-20
> The Mozilla Corporation today released Firefox 3 Beta 1, which is now available for download in a variety of languages. The beta includes updates to the default theme, the new places site management features, improved security architecture, and Gecko 1.9. Release notes with a more complete list of features, are also available.

[http://www.mozillazine.org/talkback.html?article=22714](http://www.mozillazine.org/talkback.html?article=22714)

3.0 seems to render pages significantly faster for me. I can't wait for it to be released :)

---

### Post by herbster on 2007-11-20
I downloaded it but how do I get it to run? I have extracted the tar to my desktop and am running the "firefox" within it, but it just keeps running 2.0.0.8. :confused:

---

### Post by Retrograde77 on 2007-11-20
also is there a way it can be installed and run on its own, not screwing up the current fox config?

---

### Post by -grubby on 2007-11-20
the alpha is in the repos if anyone wants to try it

---

### Post by x0as on 2007-11-20
I've been trying it today, even with a fresh profile it doesn't feel any quicker than firefox 2.  I'll be sticking with 2.

---

### Post by oliviacond on 2007-11-20
> **herbster said:**
> I downloaded it but how do I get it to run? I have extracted the tar to my desktop and am running the "firefox" within it, but it just keeps running 2.0.0.8. :confused:
[http://www.debianadmin.com/install-firefox30a1-in-ubuntu-and-list-of-addons.html]("http://www.debianadmin.com/install-firefox30a1-in-ubuntu-and-list-of-addons.html")

---

### Post by mrgnash on 2007-11-20
> **herbster said:**
> I downloaded it but how do I get it to run? I have extracted the tar to my desktop and am running the "firefox" within it, but it just keeps running 2.0.0.8. :confused:

Are you executing the full path? If you simply type 'firefox' in the terminal, regardless of where you are in the directory structure, you will invoke Firefox 2.0.0.8 You need to type something like ./firefox instead.

---

### Post by oliviacond on 2007-11-20
> **Colro said:**
> [http://www.mozillazine.org/talkback.html?article=22714](http://www.mozillazine.org/talkback.html?article=22714)

3.0 seems to render pages significantly faster for me. I can't wait for it to be released :)

less memory usage too:)

---

### Post by mthei on 2007-11-20
> **nathangrubb said:**
> the alpha is in the repos if anyone wants to try it

I never even bothered to check. But if the betas, and the final, are as good as the alpha in the repos, it may be enough to get me to crawl back to Firefox as my full time browser. Far more responsive and lighter than 2.

---

### Post by herbster on 2007-11-20
I did ./firefox from the directory at terminal, still runs v2. Also did sh /home/user/Desktop/firefox/firefox, same thing. I can't run this thing?!

---

### Post by tristan on 2007-11-20
> **herbster said:**
> I did ./firefox from the directory at terminal, still runs v2. Also did sh /home/user/Desktop/firefox/firefox, same thing. I can't run this thing?!

I had the same problem until I realised I had a minimised FF2 window somewhere which just maximised when I called FF3. Not trying to insult your intelligence, but have you made sure you have no other instances of FF running?

---

### Post by crimesaucer on 2007-11-20
I would get this warning when running ./firefox: (gecko:7670): Pango-WARNING


It would still work, the warning would list some fonts and tell me that it would be displayed ugly.


My pages looked the same, but there was a slight "flutter" of weirdness that would show when a page like Google loaded. Then my menus were very buggy and never dropped down smooth like it does regularly. 


Plus, certain pages would not complete the loading process (like digg), and it would load to about 99% and then keep using my cpu without finishing. 


Other than that, the native gtk widgets were really nice, and it did feel as fast as my Swiftfox.


* I wouldn't even worry about it yet, it's not near finished. When it does finish, I'm sure it will be really good.

---

### Post by ~LoKe on 2007-11-20
Fonts are larger.

HOWEVER!  It follows the gtk theme (holy crap finally).

---

### Post by dasunst3r on 2007-11-20
To get my Firefox 3b1 fix, I did the following.  If you need any clarifications on what commands to issue, ask:[LIST=1]
[*]Download the .tar.gz
[*]Extract it
[*]Move the resulting directory to /opt
[*]Make a copy of ~/.mozilla/firefox for backup's sake
[*]Change my default browser to Firefox 3 under System -> Preferences -> Preferred Applications[/LIST]Besides a few rendering quirks, it runs pretty fast.  I'm confident that the folks of Mozilla will do some more bug-quashing before releasing.

---

### Post by Colro on 2007-11-20
Has anyone managed to get a userContent.css file to work for dark themes yet? Working with GTK themes is nice until you get black text in black textboxes =(

---

### Post by ilh on 2007-11-21
Argh! 1 of the things I loved about older FF versions over IE was that it didn't screw up the ordering of sites i've visited in the address bar drop down by putting the most recently visited at the top. Now FF3 beta does just that. I hate not knowing where what is because it's been sorted on the fly.

Is there any way to change this so it doesn't reorder them?

---

### Post by herbster on 2007-11-21
> **Colro said:**
> Has anyone managed to get a userContent.css file to work for dark themes yet? Working with GTK themes is nice until you get black text in black textboxes =(

Easy fix, go to gnome-look.org, search for the Neutronium theme and download it, there's a fix where you change something in the config as well as a custom forms.css you put into firefox. I use it everytime I install Ubuntu and import my home folder to get FF just fine and dandy.

And tristan, you were on the money! I had 3 FF windows running, lol ;) I just ran FF3 and honestly can't say there's that big of a difference. It felt a tiny bit smoother in switching tabs and opening new ones, but nothing tremendous.

---

### Post by Saya on 2007-12-17
Mispost.

---

