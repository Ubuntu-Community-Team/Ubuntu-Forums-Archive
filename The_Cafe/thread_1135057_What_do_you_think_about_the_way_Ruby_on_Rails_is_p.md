---
title: "What do you think about the way Ruby on Rails is packaged?"
date: 2009-04-24
forum: The Cafe
---

### Post by rapha on 2009-04-24
Hi all,

so I just installed Jaunty (which rocks) and now took a look at what Rails version is in the repos ... it's 2.1.0 (which doesn't quite rock that much).

Which means that nothing really changes; the Rails version in the repositories is still not much use to me (and probably any other serious Rails developer either) and I'll end up installing it through RubyGems again. If I should decide to use Ubuntu's own rubygems, I'll have to alter my path to include /var/lib/gems/.../bin afterwards which isn't exactly "Ubuntuian" either, having to edit paths by hand and so on.

My question is: am I the only one who thinks getting up and with Ruby on Rails under Ubuntu is a bit of a pain in the neck? Shouldn't at least the binaries installed by RubyGems be in the path by default? Or the police on the frequency of updating the Rails package be changed? Or something?

What do you think?

Cheers,
Raphael

---

### Post by Tibuda on 2009-04-24
So that's why I'm not able to get Rails working with the repository RubyGems! It only works for me if I install RubyGems from source (in both Intrepid and Jaunty).

I agree with you. The installed gems should be in the path, and the rails package should be updated.

---

### Post by rapha on 2009-04-24
Good to hear I'm not the only one - me, I'm installing gems locally for the time being and have added $HOME/.gem/ruby/1.8/bin to my own $PATH. But all that stuff not what you'd call "easily discoverable"... :roll:

---

