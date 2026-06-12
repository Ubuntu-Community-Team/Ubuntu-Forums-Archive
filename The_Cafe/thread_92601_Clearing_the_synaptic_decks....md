---
title: "Clearing the synaptic decks..."
date: 2005-11-19
forum: The Cafe
---

### Post by adam.tropics on 2005-11-19
So I'm sure most people here have installed and tweaked away until they are happy with their setup of Ubuntu.......more than once!

After it's all done and dusted, I'm pretty sure there must normally be a whole load of junk, as in non-required packages or files that may have been dependancies at one time but now are just space fillers. I know synaptic does a terrific job and all, but is there a way to check it!!??

It could be just me, but i hate the idea of keeping stuff for no reason....

---

### Post by Haegin on 2005-11-20
Also is there a way of saving a list of what you have installed so you can enter one command or click a few buttons and synaptic will churn through and bring you back to where you were before? (Just with regards to installed programs - not a backup, just a list of installed programs)

---

### Post by Jussi Kukkonen on 2005-11-20
Try deborphan:
[I] deborphan finds "orphaned" packages on your system.
 It determines which packages have no other packages
 depending on their installation, and shows you a list of
 these packages. It is most useful when finding libraries,
 but it can be used on packages in all sections.
[/I]

---

### Post by marksi on 2005-11-21
You could also try *sudo apt-get auto-clean* which clears out the local repository of re&#8208;trieved package files.

---

