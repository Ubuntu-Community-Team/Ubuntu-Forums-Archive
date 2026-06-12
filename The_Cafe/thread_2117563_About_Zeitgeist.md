---
title: "About Zeitgeist"
date: 2013-02-18
forum: The Cafe
---

### Post by G_khan on 2013-02-18
Hello,

In searching for all kinds of ways to do away with Zeitgeist, which for me is an unnecessary program, and many will agree with me, is borderline big brother, I have found a nice solution on hindering zeitgeist.  There are solutions such as making it so that the program does not write to the splite file, or removing it completely and losing many important programs.  I tried the latter at first, and found that I couldn't view my files, which was annoying.  And so I persisted and found a nice solution: break the dependencies of the program.

Using aptitude (which is pretty sweet, so if you don't have it, install it), run the command *aptitude keep-all*.  This essentially breaks dependencies by basically telling your computer you have installed every single program in your computer.  That way, you can run the command *sudo apt-get remove --purge zeitgeist*, you get to keep all those programs you'd otherwise lose.

Insofar as I know, this did the trick for me.  I basically removed anything with the word zeitgeist in it, except for libzeitgeist and a few others.  With the above command, I think I've succeeded in hindering this shady program.  Of course, I might be wrong, and so this is the reason why I am posting this message.

---

### Post by tgalati4 on 2013-02-18
Linux Mint 14 Mate does not have zeitgeist installed.  What is the advantage of having zeitgeist?

---

### Post by cariboo on 2013-02-18
@G_khan, Lucid Desktop support ends in two months (April), when you upgrade to the next LTS version, you can turn off what zeitgeist records in System Settings->Privacy

---

### Post by s1baker on 2013-02-19
here are a bunch of links. the first one is the best


[http://ubuntuforums.org/showthread.php?t=2000108&highlight=zeitgeist]("http://ubuntuforums.org/showthread.php?t=2000108&highlight=zeitgeist")

[http://insanitybit.wordpress.com/2012/07/17/removing-zeitgeist-sped-up-unity-2/]("http://insanitybit.wordpress.com/2012/07/17/removing-zeitgeist-sped-up-unity-2/")

[http://linuxaria.com/howto/how-to-remove-zeitgeist-in-ubuntu-and-why?lang=en]("http://linuxaria.com/howto/how-to-remove-zeitgeist-in-ubuntu-and-why?lang=en")

[http://ubuntuforums.org/showthread.php?t=2062843]("http://ubuntuforums.org/showthread.php?t=2062843")

[http://catlingmindswipe.blogspot.com/2012/05/how-to-enhance-privacy-with-zeitgeist.html]("http://catlingmindswipe.blogspot.com/2012/05/how-to-enhance-privacy-with-zeitgeist.html")

[http://www.iloveubuntu.net/activity-log-manager-08-handy-gui-blacklisting-zeitgeists-activity-released-ppa]("http://www.iloveubuntu.net/activity-log-manager-08-handy-gui-blacklisting-zeitgeists-activity-released-ppa")

---

### Post by Paqman on 2013-02-19
> **tgalati4 said:**
> What is the advantage of having zeitgeist?

Basically it's to make your machine learn what you want to do with it.

It's a service which can provide apps with lots of useful information about what the user is up to. The apps can use that to tailor the user's experience to their habits and usage patterns. It can also provide really fine-grained and smart search.

---

### Post by diesch on 2013-02-19
You can just switch off Zeitgeist logging in Privacy settings or use [Privacy Indicator](http://www.florian-diesch.de/software/indicator-privacy/)

Remove  *~/.local/share/zeitgeist/* to delete everything Zeitgeist logged so far

---

### Post by G_khan on 2013-02-19
@cariboo907: I actually don't have lucid installed any more.  I would change that about my profile, but there is a minimum number of posts that we need to post before we can change things in our profile.  But given the cool icons under your name, I don't think I needed to say all that to you.  I have Ubuntu Gnome Remix installed and I didn't find the Privacy option in System Settings.  Plus I thought it was cool to break dependencies (although I don't think it broke all dependencies).  

@s1baker:  Thanks for the links.  The first one is good.

@diesch: That folder is now empty after purging zeitgeist, but thanks for the suggestion.

---

